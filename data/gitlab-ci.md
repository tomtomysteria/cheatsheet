# 📦 GitLab CI/CD

## Introduction

GitLab CI/CD est le moteur d’intégration continue et de déploiement continu intégré à GitLab. Il exécute des **pipelines** composés de **jobs** (tâches) regroupés par **stages** (étapes), dans des runners (agents d’exécution).

Objectifs typiques :

- Compiler/tester (Java, Angular…)
- Publier des artefacts (JAR, rapports…)
- Builder et pousser des images Docker
- Déployer (Kubernetes/Helm, VM via Ansible, etc.)

---

## Concepts clés

### Pipeline / stage / job

- **pipeline** : l’ensemble des jobs pour un commit/merge request.
- **stage** : une étape logique (ex: `build`, `test`, `deploy`). Les stages s’exécutent dans l’ordre.
- **job** : un bloc de commandes (`script:`) qui tourne dans un runner. Les jobs d’un même stage peuvent tourner en parallèle.

### Runner

Un **runner** est la machine (ou pod) qui exécute les jobs.

- exécution dans une image Docker (`image:`)
- ou via un runner “shell” (sur VM)

### Variables et secrets

- Variables GitLab (UI) : `Settings → CI/CD → Variables`.
- Variables masquées/protégées pour les secrets.
- ⚠️ Éviter d’écrire des secrets en clair dans le repo.

Exemple :

```yaml
variables:
  MAVEN_OPTS: "-Dmaven.repo.local=$CI_PROJECT_DIR/.m2/repository"
```

### Cache vs artifacts

- **cache** : accélère les builds (ex: `.m2`, `node_modules`). Peut être réutilisé entre pipelines.
- **artifacts** : fichiers produits par un job, téléchargeables et passés aux jobs suivants.

### `dependencies` / `needs`

- `dependencies:` contrôle quels artifacts sont téléchargés.
- `needs:` permet de lancer un job plus tôt (DAG) et de réduire la durée totale.

---

## Structure minimale d’un `.gitlab-ci.yml`

```yaml
image: alpine:3.20

stages:
  - build
  - test

build_job:
  stage: build
  script:
    - echo "build"

test_job:
  stage: test
  script:
    - echo "test"
```

---

## Exemples utiles (Java / Maven / Spring Boot)

### Build + tests Maven

```yaml
image: maven:3.9.9-eclipse-temurin-21

stages:
  - build
  - test

cache:
  key: maven
  paths:
    - .m2/repository

build:
  stage: build
  script:
    - mvn -B -DskipTests package
  artifacts:
    when: always
    paths:
      - target/*.jar

unit_tests:
  stage: test
  script:
    - mvn -B test
  artifacts:
    when: always
    reports:
      junit:
        - target/surefire-reports/TEST-*.xml
```

### Secrets : fichier `application-secrets.properties`

Plutôt que de committer le fichier, on peut le générer au runtime depuis une variable GitLab :

```yaml
before_script:
  - echo "$APP_SECRETS" > src/main/resources/application-secrets.properties
```

Bonnes pratiques :

- variable `APP_SECRETS` marquée **masked**
- si multi-jobs : regénérer dans chaque job qui en a besoin

---

## Exemples utiles (Angular)

```yaml
image: node:20

stages:
  - install
  - test
  - build

cache:
  key: node
  paths:
    - node_modules/

install:
  stage: install
  script:
    - npm ci
  artifacts:
    paths:
      - node_modules/

unit_tests:
  stage: test
  script:
    - npm test -- --watch=false

build:
  stage: build
  script:
    - npm run build
  artifacts:
    paths:
      - dist/
```

---

## Docker dans GitLab CI

### Build + push d’une image

```yaml
image: docker:27
services:
  - docker:27-dind

variables:
  DOCKER_HOST: tcp://docker:2375
  DOCKER_TLS_CERTDIR: ""

stages:
  - build

build_image:
  stage: build
  script:
    - echo "$CI_REGISTRY_PASSWORD" | docker login -u "$CI_REGISTRY_USER" --password-stdin "$CI_REGISTRY"
    - docker build -t "$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA" .
    - docker push "$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA"
```

---

## Déployer sur Kubernetes avec Helm (exemple)

Prérequis typiques :

- un runner qui peut contacter le cluster
- un `kubeconfig` fourni via variable CI (souvent encodé en base64)

Exemple minimal : build image → deploy Helm.

```yaml
stages:
  - build
  - deploy

build_image:
  stage: build
  image: docker:27
  services:
    - docker:27-dind
  variables:
    DOCKER_HOST: tcp://docker:2375
    DOCKER_TLS_CERTDIR: ""
  script:
    - echo "$CI_REGISTRY_PASSWORD" | docker login -u "$CI_REGISTRY_USER" --password-stdin "$CI_REGISTRY"
    - docker build -t "$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA" .
    - docker push "$CI_REGISTRY_IMAGE:$CI_COMMIT_SHA"

deploy_prod:
  stage: deploy
  image:
    name: alpine/helm:3.16.2
    entrypoint: [""]
  rules:
    - if: $CI_COMMIT_BRANCH == "main"
  environment:
    name: production
  script:
    - mkdir -p "$CI_PROJECT_DIR/.kube"
    - echo "$KUBECONFIG_B64" | base64 -d > "$CI_PROJECT_DIR/.kube/config"
    - export KUBECONFIG="$CI_PROJECT_DIR/.kube/config"
    - helm upgrade --install my-app ./helm/my-app -n my-namespace --create-namespace \
        --set image.repository="$CI_REGISTRY_IMAGE" \
        --set image.tag="$CI_COMMIT_SHA"
```

  Variante fréquente : values par environnement (ex: prod) : ajouter `-f ./helm/my-app/values-prod.yaml`.

Bonnes pratiques :

- mettre `KUBECONFIG_B64` en variable **protected** et **masked**
- utiliser un tag d’image immuable (SHA)

Voir aussi :

- Helm : `data/helm.md`

---

## Déclenchement et conditions

### `rules:` (recommandé)

```yaml
unit_tests:
  stage: test
  rules:
    - if: $CI_PIPELINE_SOURCE == "merge_request_event"
    - if: $CI_COMMIT_BRANCH == "main"
  script:
    - mvn test
```

---

## Bonnes pratiques

1. **Isoler les responsabilités** : un job = un objectif clair.
2. **Rendre les pipelines reproductibles** : `mvn -B`, `npm ci`, versions figées.
3. **Cache intelligent** : `.m2/repository`, `node_modules` si pertinent.
4. **Artifacts utiles** : JUnit, JAR, coverage.
5. **Secrets uniquement via variables** : jamais en clair.
6. **Optimiser avec `needs:`** quand le pipeline grossit.

---

## Liens utiles

- [Documentation GitLab CI/CD](https://docs.gitlab.com/ee/ci/)
- [`.gitlab-ci.yml` reference](https://docs.gitlab.com/ee/ci/yaml/)
