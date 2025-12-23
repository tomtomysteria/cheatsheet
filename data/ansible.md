# 📦 Ansible

## Introduction

Ansible est un outil d’automatisation (Infra as Code) basé sur des **playbooks YAML**. Il est **agentless** : il se connecte (souvent en SSH) et applique des changements via des modules.

Atouts :

- Idempotence (réappliquer sans casser)
- Inventaires (groupes de machines)
- Rôles réutilisables

---

## Concepts clés

### Inventory

Liste des hôtes (fichier `inventory.ini` ou dynamique) :

```ini
[web]
web1 ansible_host=10.0.0.10
web2 ansible_host=10.0.0.11

[db]
db1 ansible_host=10.0.0.20
```

### Playbook

Un playbook décrit :

- sur quels hôtes
- avec quel user
- quelles tâches (tasks)

Structure minimale (un play) :

```yaml
- name: Exemple de play
  hosts: web
  become: true
  tasks:
    - name: Ping
      ansible.builtin.ping:
```

Rappels YAML utiles :

- l’indentation est **significative** (espaces, pas de tabulations)
- `-` introduit un élément de liste
- `clé: valeur` définit un mapping (objet)

### Rôles

Un rôle structure les tasks/templates/vars de manière réutilisable.

### Secrets

- `ansible-vault` chiffre des variables/fichiers.

---

## Commandes essentielles

```bash
ansible --version
ansible all -i inventory.ini -m ping

ansible-playbook -i inventory.ini playbook.yml
ansible-playbook -i inventory.ini playbook.yml --check
ansible-playbook -i inventory.ini playbook.yml --diff
```

Chiffrement :

```bash
ansible-vault create secrets.yml
ansible-vault edit secrets.yml
ansible-vault encrypt vars.yml
ansible-vault decrypt vars.yml
```

---

## Exemple : installer Docker (Ubuntu)

```yaml
- name: Installer Docker
  hosts: web
  become: true
  tasks:
    - name: Installer dépendances
      ansible.builtin.apt:
        name:
          - ca-certificates
          - curl
        update_cache: true

    - name: Installer docker.io
      ansible.builtin.apt:
        name: docker.io
        state: present

    - name: Démarrer Docker
      ansible.builtin.service:
        name: docker
        state: started
        enabled: true
```

---

## Exemple : déployer une application (fichier + service)

Cas typique : copier un `.jar` et redémarrer un service systemd.

```yaml
- name: Déployer une app Spring Boot
  hosts: web
  become: true

  vars:
    app_name: my-app
    jar_path: /opt/my-app/app.jar

  tasks:
    - name: Copier le jar
      ansible.builtin.copy:
        src: target/my-app.jar
        dest: "{{ jar_path }}"
        mode: '0644'

    - name: Redémarrer le service
      ansible.builtin.service:
        name: "{{ app_name }}"
        state: restarted
```

---

## Bonnes pratiques

## À connaître en entreprise

### Rôles (structure)

Structure type :

```text
roles/
  my-role/
    tasks/main.yml
    handlers/main.yml
    templates/
    defaults/main.yml
    vars/main.yml
```

### Handlers

Utiles pour redémarrer un service uniquement si un fichier a changé.

### Templates (Jinja)

Rendu de fichiers de config paramétrés via `ansible.builtin.template`.

1. **Toujours idempotent** : préférer des modules (`apt`, `template`) à `shell`.
2. **Rôles** : factoriser les playbooks.
3. **Vault** : secrets chiffrés.
4. **Mode `--check`** : valider avant d’appliquer.
5. **Inventaires par environnement** : dev / preprod / prod.

---

## Liens utiles

- [Ansible docs](https://docs.ansible.com/)
- [Best practices](https://docs.ansible.com/ansible/latest/tips_tricks/ansible_tips_tricks.html)
