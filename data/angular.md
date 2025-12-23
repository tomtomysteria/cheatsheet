# Angular

## Introduction

Angular est un framework JavaScript développé par Google pour créer des applications web dynamiques. Il utilise TypeScript comme langage principal et offre une architecture basée sur les composants. Angular est particulièrement adapté pour les applications complexes nécessitant une gestion avancée des états et des interactions utilisateur.

## Concepts clés

### Composants

Les composants sont les blocs de construction de base d'une application Angular. Chaque composant est constitué de :

- Un fichier TypeScript (`.ts`) définissant la logique.
- Un fichier HTML (`.html`) pour la structure.
- Un fichier CSS ou SCSS (`.css` ou `.scss`) pour le style.

Exemple de composant :

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-example',
  template: '<h1>Hello Angular</h1>',
  styles: ['h1 { color: blue; }']
})
export class ExampleComponent {}
```

### Modules

Les modules permettent de structurer une application en regroupant des fonctionnalités connexes. Le module racine est généralement `AppModule`.

Exemple de module :

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

### Services

Les services sont utilisés pour partager des données ou des fonctionnalités entre différents composants. Ils sont souvent injectés via le système d'injection de dépendances.

Exemple de service :

```typescript
import { Injectable } from '@angular/core';

@Injectable({ providedIn: 'root' })
export class DataService {
  getData() {
    return ['Angular', 'React', 'Vue'];
  }
}
```

### Directives

Les directives permettent de manipuler le DOM. Il existe trois types de directives :

- Structurelles (ex : `*ngIf`, `*ngFor`).
- Attributs (ex : `[ngClass]`, `[ngStyle]`).
- Composants (qui sont des directives avec un template).

Exemple de directive structurelle :

```html
<div *ngIf="isVisible">Ce contenu est visible</div>
```

### Routage

Angular inclut un système de routage puissant pour gérer la navigation entre les pages.

Exemple de configuration de routage :

```typescript
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about', component: AboutComponent }
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule {}
```

### Tests

Angular supporte les tests unitaires et end-to-end via des outils comme Jasmine et Protractor.

Exemple de test unitaire :

```typescript
import { TestBed } from '@angular/core/testing';
import { AppComponent } from './app.component';

describe('AppComponent', () => {
  beforeEach(() => {
    TestBed.configureTestingModule({
      declarations: [AppComponent]
    });
  });

  it('should create the app', () => {
    const fixture = TestBed.createComponent(AppComponent);
    const app = fixture.componentInstance;
    expect(app).toBeTruthy();
  });
});
```

### Modèles

Les modèles définissent la structure des données utilisées dans l'application. Ils sont souvent représentés par des classes TypeScript.

Exemple de modèle :

```typescript
export class Product {
  constructor(
    public id: number,
    public name: string,
    public price: number
  ) {}
}
```

### Contrôleurs

⚠️ Angular (moderne) est centré sur les **composants**. La notion de “controller” est surtout associée à **AngularJS** (ancienne génération).

### Logs

Angular propose des outils pour la gestion des logs, comme le service `Logger` ou des bibliothèques externes comme `ngx-logger`.

Exemple de configuration de logs :

```typescript
import { Injectable } from '@angular/core';
import { NGXLogger } from 'ngx-logger';

@Injectable({ providedIn: 'root' })
export class LoggerService {
  constructor(private logger: NGXLogger) {}

  logInfo(message: string) {
    this.logger.info(message);
  }
}
```

## Installation

Pour installer Angular, utilisez la commande suivante :

```bash
npm install -g @angular/cli
```

## Commandes principales

- `ng new <nom-du-projet>` : Crée un nouveau projet Angular.
- `ng serve` : Démarre le serveur de développement.
- `ng build` : Compile le projet pour la production.
- `ng generate <type> <nom>` : Génère des composants, services, etc.
- `ng test` : Exécute les tests unitaires.
- `ng e2e` : Exécute les tests end-to-end.
- `ng lint` : Analyse le code pour détecter les erreurs de style.
- `ng add <package>` : Ajoute des fonctionnalités à un projet existant.
- `ng update` : Met à jour les dépendances Angular.
- `ng config` : Configure les paramètres Angular CLI.
- `ng analytics` : Gère les paramètres d'analyse.

## Structure du projet

- `src/app` : Contient les composants principaux de l'application.
- `src/assets` : Contient les fichiers statiques comme les images.
- `src/environments` : Contient les configurations d'environnement.
- `src/styles.css` : Contient les styles globaux.
- `src/main.ts` : Point d'entrée de l'application.
- `src/models` : Contient les modèles de données.
- `src/services` : Contient les services partagés.
- `src/logs` : Contient les fichiers de logs (si configuré).

## Bonnes pratiques

- Utilisez des modules pour organiser votre code.
- Écrivez des tests pour chaque composant et service.
- Suivez les conventions de nommage Angular.
- Optimisez les performances en utilisant le lazy loading pour les modules.
- Utilisez des outils de gestion des logs pour surveiller les erreurs et les performances.

## À connaître en poste (essentiel)

### HttpClient + Interceptors (auth / erreurs)

On utilise `HttpClient` (Observables) et des **interceptors** pour :

- ajouter un token (Authorization)
- centraliser la gestion d’erreurs

Exemple d’interceptor (simplifié) :

```typescript
import { Injectable } from '@angular/core';
import { HttpInterceptor, HttpRequest, HttpHandler } from '@angular/common/http';

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  intercept(req: HttpRequest<unknown>, next: HttpHandler) {
    const token = localStorage.getItem('token');
    if (!token) return next.handle(req);

    return next.handle(
      req.clone({ setHeaders: { Authorization: `Bearer ${token}` } })
    );
  }
}
```

### RxJS (indispensable)

Opérateurs très fréquents : `map`, `tap`, `switchMap`, `catchError`, `finalize`, `debounceTime`.

### Forms

- **Reactive Forms** (souvent préféré) : validations, formulaires complexes.

### Routing avancé

- **Guards** (auth)
- **Lazy loading** (performance)

### Perf

- `ChangeDetectionStrategy.OnPush`
- `trackBy` sur les `*ngFor`

---

## Mini exemple end-to-end (Angular → Spring Boot)

### Service Angular qui appelle une API Spring

```typescript
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';
import { Observable } from 'rxjs';

export interface UserDto {
  id: number;
  email: string;
}

@Injectable({ providedIn: 'root' })
export class UsersApi {
  constructor(private http: HttpClient) {}

  list(): Observable<UserDto[]> {
    return this.http.get<UserDto[]>('/api/users');
  }
}
```

Note : en dev, tu peux configurer un proxy (`proxy.conf.json`) pour éviter CORS.

## Documentation officielle

[Angular Documentation](https://angular.io/docs)
