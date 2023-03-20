# Angular Interceptors

Ce projet vise à illustrer l'utilisation des interceptors Angular pour effectuer diverses tâches, telles que la gestion des erreurs, l'ajout de tokens d'authentification et la journalisation des requêtes HTTP.

## Table des matières

- Introduction
- Installation
- Exemples d'interceptors
- Gestion des erreurs
- Ajout de tokens d'authentification
- Journalisation des requêtes HTTP
- Enregistrement des interceptors
- Conclusion

### Introduction

Les interceptors Angular sont une fonctionnalité puissante qui permet de modifier les requêtes HTTP avant qu'elles ne soient envoyées au serveur et de traiter les réponses avant qu'elles ne soient renvoyées à l'application. Ils sont particulièrement utiles pour centraliser la gestion des erreurs, l'authentification et la journalisation des requêtes HTTP.

### Installation

Assurez-vous d'avoir installé Node.js et Angular CLI sur votre machine. Clonez ce dépôt et naviguez jusqu'au dossier du projet :
```bash
git clone https://github.com/ThomasBernardDiiage/TosInterceptor
cd angular-interceptors
```

Installez les dépendances du projet :

```bash
npm install
```

Lancez l'application Angular en mode développement :
```bash
ng serve
```

Ouvrez votre navigateur et accédez à `http://localhost:4200/` pour voir l'application en action.

### Exemples d'interceptors

Dans ce projet, nous présentons trois exemples d'interceptors Angular pour illustrer leur utilisation.

### Gestion des erreurs

Un interceptor qui gère globalement les erreurs HTTP en détectant les erreurs et en affichant un message d'erreur approprié à l'utilisateur, par exemple via une notification ou une alerte.
Fichier : src/app/interceptors/error.interceptor.ts

### Ajout de tokens d'authentification

Un interceptor qui ajoute un token d'authentification à chaque requête HTTP sortante, en l'insérant dans le header Authorization.
Fichier : src/app/interceptors/auth.interceptor.ts

### Journalisation des requêtes HTTP

Un interceptor qui enregistre le temps d'exécution et le statut de chaque requête HTTP, permettant ainsi de surveiller et d'optimiser les performances de l'application.

Fichier : src/app/interceptors/logging.interceptor.ts


### Enregistrement des interceptors

Pour utiliser ces interceptors, il faut les enregistrer dans le module de l'application. Dans ce projet, nous les avons enregistrés dans le fichier `src/app/app.module.ts`. Voici comment procéder pour enregistrer un interceptor :

Importez l'interceptor dans le fichier app.module.ts :

```typescript
import { ErrorInterceptor } from './interceptors/error.interceptor';
import { AuthInterceptor } from './interceptors/auth.interceptor';
import { LoggingInterceptor } from './interceptors/logging.interceptor';

Ajoutez l'interceptor à la liste des providers en utilisant HTTP_INTERCEPTORS et useClass :
```typescript

import { HttpClientModule, HTTP_INTERCEPTORS } from '@angular/common/http';

@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [
    BrowserModule,
    HttpClientModule
  ],
  providers: [
    { provide: HTTP_INTERCEPTORS, useClass: ErrorInterceptor, multi: true },
    { provide: HTTP_INTERCEPTORS, useClass: AuthInterceptor, multi: true },
    { provide: HTTP_INTERCEPTORS, useClass: LoggingInterceptor, multi: true }
  ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Notez l'utilisation de multi: true, qui permet d'ajouter plusieurs interceptors à la liste des interceptors existants.

### Conclusion

Ce projet démontre l'utilisation des interceptors Angular pour gérer les erreurs, ajouter des tokens d'authentification et journaliser les requêtes HTTP. Les interceptors sont un outil puissant pour améliorer et centraliser la gestion des communications HTTP dans les applications Angular.N'hésitez pas à explorer davantage ce projet et à ajouter d'autres interceptors pour répondre à des besoins spécifiques. Les interceptors Angular offrent de nombreuses possibilités pour optimiser et personnaliser le comportement des requêtes HTTP.

### Contribuer

Les contributions à ce projet sont les bienvenues. Si vous souhaitez ajouter de nouveaux exemples d'interceptors ou améliorer ceux existants, n'hésitez pas à soumettre une pull request.

### Licence

Ce projet est sous licence MIT. Consultez le fichier LICENSE pour plus d'informations.
