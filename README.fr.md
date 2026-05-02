**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  NestJS <img src="./assets/nestjs.svg" width="40" height="40" alt="NestJS logo"/>
</h1>

<h2>Les questions et réponses d'entretien NestJS les plus populaires</h2>

<details>
<summary>1. Qu'est-ce que NestJS et quels problèmes résout-il ?</summary>

#### NestJS

NestJS est un framework Node.js progressif pour créer des applications backend.
Il est conçu avec TypeScript par défaut et reprend des idées architecturales
familières d’Angular (modules, injection de dépendances, décorateurs), tout en
fonctionnant sur des adaptateurs HTTP comme Express ou Fastify.

#### Ce que NestJS résout

1. **Manque de structure dans les applications Node.js qui grandissent**
   NestJS impose des frontières modulaires claires (`@Module`), ce qui facilite
   la scalabilité et la maintenance des grandes bases de code.

2. **Dépendances difficiles à gérer**
   L’**injection de dépendances (DI)** intégrée réduit le couplage fort entre les
   classes et améliore la testabilité.

3. **Boilerplate sur les préoccupations transverses**
   Guards, Pipes, Interceptors, Filters et Middleware fournissent des patterns
   cohérents pour l’authentification, la validation, la transformation, le
   logging et la gestion d’erreurs.

4. **Architecture incohérente entre équipes**
   NestJS fournit des conventions opinionated, ce qui permet aux équipes de
   construire avec le même modèle mental et une structure de projet prévisible.

5. **Mise en place de tests complexe**
   Les outils de test (`@nestjs/testing`) et la conception orientée DI
   simplifient les tests unitaires, d’intégration et e2e.

6. **Besoin de supporter plusieurs transports backend**
   NestJS prend en charge HTTP REST, GraphQL, WebSockets et les microservices
   (TCP, Redis, NATS, Kafka, gRPC, etc.) avec un modèle de programmation unifié.

#### En bref

NestJS vous aide à passer d’un « code Node.js qui fonctionne » à une
**architecture backend bien structurée, prête pour l’entreprise**, avec une forte
maintenabilité, testabilité et scalabilité d’équipe.

</details>

<details>
<summary>2. Quelle est la différence entre NestJS, Express et Fastify ?</summary>

#### NestJS

NestJS, Express et Fastify sont liés, mais opèrent à des niveaux d’abstraction
différents.

#### Différence principale

1. **Express / Fastify** sont des frameworks de serveur HTTP.
2. **NestJS** est un framework d’application qui peut fonctionner au-dessus
   d’Express ou de Fastify via des adaptateurs.

#### Architecture et modèle de développement

1. **Express**
   Minimaliste et peu prescriptif. Vous définissez manuellement la structure,
   les patterns de DI, la validation et les conventions.

2. **Fastify**
   Également plutôt bas niveau, mais optimisé pour la performance avec un
   écosystème de plugins et une approche schema-first.

3. **NestJS**
   Architecture opinionated prête à l’emploi : modules, providers,
   controllers, injection de dépendances, lifecycle hooks et pipeline de
   requêtes standardisé.

#### Perspective performance

1. **Fastify** est généralement plus rapide qu’Express en débit HTTP brut.
2. **NestJS avec l’adaptateur Fastify** offre en général de meilleures
   performances que NestJS sur Express.
3. Dans la plupart des systèmes métier, l’architecture, la maintenabilité et
   la vélocité d’équipe sont souvent plus importantes que les micro-benchmarks.

#### Comparaison des fonctionnalités en pratique

1. **Injection de dépendances**
   Native dans NestJS ; manuelle ou via des solutions tierces dans
   Express/Fastify.

2. **Ergonomie de test**
   NestJS propose des patterns de modules de test intégrés ; les frameworks bas
   niveau demandent plus de setup personnalisé.

3. **Scalabilité de la base de code**
   Les conventions NestJS réduisent le chaos dans les grandes équipes/projets.

4. **Portée de l’écosystème**
   NestJS unifie REST, GraphQL, WebSockets et microservices sous un même modèle
   mental.

#### Quand choisir quoi

1. Choisissez **Express** pour des services très petits/simples ou la
   compatibilité legacy.
2. Choisissez **Fastify** quand le débit maximal et un faible overhead sont
   prioritaires.
3. Choisissez **NestJS** si vous avez besoin de maintenabilité long terme,
   d’une architecture claire et d’une approche backend standardisée pour
   l’entreprise.

</details>

<details>
<summary>3. Quels sont les principaux blocs de construction de NestJS ?</summary>

#### NestJS

NestJS est composé de plusieurs blocs de construction fondamentaux qui
définissent l’architecture de l’application, son comportement à l’exécution et
le flux des requêtes.

#### Blocs de construction principaux

1. **Modules (`@Module`)**
   Unité d’organisation de plus haut niveau. Un module regroupe des
   controllers et providers liés, et contrôle la visibilité via `imports` /
   `exports`.

2. **Controllers (`@Controller`)**
   Gèrent les requêtes entrantes et renvoient les réponses. Les décorateurs de
   route comme `@Get()`, `@Post()`, `@Patch()` mappent les handlers aux
   endpoints.

3. **Providers (`@Injectable`)**
   Classes gérées par le conteneur DI de Nest (services, repositories,
   factories, helpers). Elles encapsulent la logique métier et peuvent être
   injectées dans d’autres classes.

4. **Conteneur d’Injection de Dépendances (DI)**
   Résout les dépendances des providers via des tokens, scopes et frontières
   de modules. C’est la base d’une conception découplée dans NestJS.

#### Composants du cycle de vie d’une requête

1. **Middleware**
   S’exécute avant les handlers de route. Utile pour le prétraitement bas niveau
   des requêtes (ex. logging, headers, initialisation du contexte de requête).

2. **Guards (`CanActivate`)**
   Décident si une requête est autorisée à continuer (barrière auth/authz).

3. **Pipes (`PipeTransform`)**
   Transforment et valident les données entrantes (validation DTO, parsing,
   normalisation).

4. **Interceptors (`NestInterceptor`)**
   Encapsulent l’exécution des handlers pour les préoccupations transverses
   (mapping de réponse, timing, cache, tracing, logique de retry).

5. **Exception Filters (`ExceptionFilter`)**
   Gestion centralisée des erreurs et formatage des réponses pour les exceptions
   levées.

#### Blocs plateforme et transport

1. **Adaptateurs HTTP**
   Intégration Express ou Fastify via des adaptateurs de plateforme.

2. **Couche de transport microservices**
   TCP, Redis, NATS, Kafka, gRPC, RMQ et autres via l’API microservices de Nest.

3. **Modules WebSockets / GraphQL**
   Modèles d’interaction alternatifs, fondés sur les mêmes principes DI/module.

#### Modèle mental pratique

Utilisez les **Modules** pour structurer les domaines, les **Controllers** comme
points d’entrée API, et les **Providers** pour la logique métier. Ensuite,
composez le comportement avec Middleware, Guards, Pipes, Interceptors et Filters
pour construire des services de production robustes.

</details>

<details>
<summary>4. Quel est le rôle de TypeScript dans NestJS et pourquoi le mode strict est-il important ?</summary>

#### NestJS

TypeScript est un pilier de conception central de NestJS, pas simplement un
ajout optionnel. Nest utilise des classes, des décorateurs, des interfaces et
des patterns de DI pilotés par métadonnées, qui sont bien plus efficaces avec
un typage fort.

#### Rôle de TypeScript dans NestJS

1. **Architecture sûre au niveau des types**
   Controllers, services, DTOs et repositories sont implémentés comme des
   classes et contrats typés, ce qui réduit les surprises à l’exécution.

2. **Meilleure expérience d’Injection de Dépendances**
   Les types des constructeurs rendent explicites les dépendances des providers
   et facilitent le raisonnement pendant le refactoring.

3. **Frontières d’API guidées par les DTO**
   Les formes des requêtes/réponses deviennent explicites via des classes DTO et
   des mapped types, ce qui améliore la maintenabilité et la cohérence des API.

4. **Outils et productivité**
   Un IntelliSense solide, des auto-refactors sûrs et le feedback à la
   compilation accélèrent le développement d’équipe.

5. **Gouvernance d’une base de code scalable**
   Les contrats de types servent de documentation exécutable dans les grands
   systèmes.

#### Pourquoi le mode strict est important

1. **Détection précoce des bugs**
   `strictNullChecks`, `noImplicitAny` et les vérifications associées évitent
   des erreurs courantes avant la production.

2. **Refactoring plus sûr**
   Dans les grands projets NestJS, le mode strict réduit les régressions cachées
   lors des déplacements de logique entre modules/services.

3. **Logique métier plus fiable**
   L’optionalité explicite et les unions précises obligent à traiter les cas
   limites de manière volontaire.

4. **Meilleure cohérence d’équipe**
   Les règles strictes du compilateur créent des standards qualité partagés
   entre les contributeurs.

#### Réglages strict à fort impact pour NestJS

1. `strict: true`
2. `noImplicitAny: true`
3. `strictNullChecks: true`
4. `noUncheckedIndexedAccess: true` (recommandé pour des accès objet/tableau plus sûrs)
5. `noFallthroughCasesInSwitch: true`

#### Recommandation pratique

Utilisez TypeScript comme un outil de conception, pas uniquement comme un sucre
syntaxique. Dans NestJS, le mode strict apporte vite des gains en correction,
lisibilité et maintenabilité long terme des services backend.

</details>

<details>
<summary>5. Que sont les décorateurs dans NestJS ? Donnez des exemples.</summary>

#### NestJS

Les décorateurs dans NestJS sont des annotations TypeScript qui attachent des
métadonnées aux classes, méthodes, paramètres et propriétés. Nest lit ces
métadonnées à l’exécution pour configurer le routing, l’injection de
dépendances, la validation, l’autorisation et d’autres fonctionnalités du
framework.

#### Pourquoi les décorateurs sont importants dans NestJS

1. **Configuration déclarative**
   Vous décrivez le comportement au plus près du code, au lieu de maintenir de
   gros fichiers de configuration externes.

2. **Runtime piloté par métadonnées**
   Nest exploite les métadonnées des décorateurs pour construire les modules,
   résoudre les providers et créer le pipeline de requêtes.

3. **Architecture cohérente**
   Les équipes suivent des patterns prévisibles entre controllers, services et
   guards.

#### Catégories courantes de décorateurs

1. **Décorateurs de classe**
   `@Module()`, `@Controller()`, `@Injectable()`

2. **Décorateurs de méthode**
   `@Get()`, `@Post()`, `@UseGuards()`, `@UseInterceptors()`

3. **Décorateurs de paramètre**
   `@Param()`, `@Body()`, `@Query()`, `@Headers()`, `@Req()`

4. **Décorateurs d’injection de propriété/constructeur**
   `@Inject(TOKEN)` (quand on utilise des tokens de provider personnalisés)

#### Exemples

```ts
import { Module, Controller, Get, Post, Body, Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  create(dto: { email: string }) {
    return { id: 1, ...dto };
  }

  findAll() {
    return [{ id: 1, email: 'user@example.com' }];
  }
}

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  getUsers() {
    return this.usersService.findAll();
  }

  @Post()
  createUser(@Body() body: { email: string }) {
    return this.usersService.create(body);
  }
}

@Module({
  controllers: [UsersController],
  providers: [UsersService],
})
export class UsersModule {}
```

#### À retenir

Les décorateurs sont l’une des raisons centrales pour lesquelles NestJS paraît
structuré : ils rendent le comportement du framework explicite, composable et
facile à faire évoluer à grande échelle.

</details>

<details>
<summary>6. Qu’est-ce que Reflect.metadata et comment NestJS l’utilise-t-il en interne ?</summary>

#### NestJS

`Reflect.metadata` fait partie du mécanisme de réflexion des métadonnées utilisé
avec les décorateurs TypeScript (via le polyfill `reflect-metadata`). Il permet
d’attacher des métadonnées structurées aux classes, méthodes et paramètres afin
que les frameworks puissent les inspecter à l’exécution.

En pratique, NestJS est fortement piloté par les métadonnées : les décorateurs
écrivent des métadonnées, et Nest les lit pour construire les graphes de
dépendances, les maps de routing, les chaînes guards/pipes/interceptors et la
logique de résolution des paramètres.

#### Concept en une ligne

1. Un décorateur écrit des métadonnées.
2. Nest lit ces métadonnées via les API `Reflector` / `Reflect`.
3. Le comportement runtime est assemblé automatiquement.

#### Où NestJS utilise les métadonnées

1. **Injection de Dépendances**
   Les types des paramètres de constructeur et les tokens d’injection explicites
   sont lus pour résoudre les providers depuis le conteneur IoC.

2. **Routing**
   `@Controller()` et `@Get()/@Post()` stockent des métadonnées de chemin et de
   méthode utilisées pour enregistrer les handlers de route.

3. **Guards, Pipes, Interceptors, Filters**
   Les métadonnées au niveau méthode/classe contrôlent quels composants
   transverses s’appliquent.

4. **Annotations d’autorisation personnalisées**
   Des décorateurs comme `@Roles('admin')` stockent des métadonnées personnalisées
   relues ensuite par les Guards.

#### Exemple minimal (métadonnées personnalisées + lecture)

```ts
import 'reflect-metadata';

const ROLES_KEY = 'roles';

function Roles(...roles: string[]) {
  return Reflect.metadata(ROLES_KEY, roles);
}

@Roles('admin')
class UsersController {}

const roles = Reflect.getMetadata(ROLES_KEY, UsersController);
// ['admin']
```

#### Note spécifique à Nest

Dans une vraie application NestJS, on utilise généralement :
1. `SetMetadata()` pour écrire les métadonnées.
2. Le service `Reflector` dans les Guards/Interceptors pour lire les métadonnées de façon sûre.

Cette abstraction garde votre code aligné avec le framework et plus simple à
tester que des appels manuels `Reflect.getMetadata(...)` partout.

</details>

<details>
<summary>7. Comment créer un décorateur personnalisé dans NestJS ? (`createParamDecorator`, `SetMetadata`)</summary>

#### NestJS

Dans NestJS, les décorateurs personnalisés se créent généralement de deux
façons :
1. **`SetMetadata()`** pour attacher des métadonnées personnalisées aux
   routes/classes.
2. **`createParamDecorator()`** pour extraire des valeurs personnalisées depuis
   le contexte de requête.

Ces deux patterns couvrent la plupart des cas réels : marqueurs
d’autorisation et paramètres dérivés de la requête.

#### 1) Décorateur de métadonnées personnalisé avec `SetMetadata`

À utiliser quand vous voulez annoter des handlers/classes avec des données que
les Guards ou Interceptors liront ensuite.

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Utilisation :

```ts
@Controller('users')
export class UsersController {
  @Get()
  @Roles('admin', 'manager')
  findAll() {
    return [];
  }
}
```

Le Guard lit les métadonnées via `Reflector` :

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(),
      context.getClass(),
    ]);
    if (!requiredRoles) return true;

    const request = context.switchToHttp().getRequest();
    const userRoles: string[] = request.user?.roles ?? [];
    return requiredRoles.some(role => userRoles.includes(role));
  }
}
```

#### 2) Décorateur de paramètre personnalisé avec `createParamDecorator`

À utiliser quand vous voulez des signatures de controllers propres et un parsing
réutilisable de la requête.

```ts
import { createParamDecorator, ExecutionContext } from '@nestjs/common';

export const CurrentUser = createParamDecorator(
  (field: string | undefined, ctx: ExecutionContext) => {
    const request = ctx.switchToHttp().getRequest();
    const user = request.user;
    return field ? user?.[field] : user;
  },
);
```

Utilisation :

```ts
@Get('me')
getProfile(@CurrentUser() user: { id: string; email: string }) {
  return user;
}

@Get('my-email')
getEmail(@CurrentUser('email') email: string) {
  return { email };
}
```

#### Bonnes pratiques

1. Gardez les décorateurs légers ; mettez la logique métier dans les
   Guards/Services.
2. Utilisez des constantes pour les clés de métadonnées (évitez les magic strings).
3. Préférez `Reflector.getAllAndOverride()` pour fusionner les métadonnées classe + méthode.
4. Typez la sortie du décorateur de paramètre pour garder des contrats explicites
   côté controller.

</details>

<details>
<summary>8. Que fait `@Injectable()` et pourquoi est-il nécessaire ?</summary>

#### NestJS

`@Injectable()` marque une classe comme provider pouvant participer à
l’Injection de Dépendances (DI) de NestJS. Autrement dit, cela indique à Nest
que cette classe est gérée par le conteneur IoC et peut recevoir des
dépendances injectées dans son constructeur.

#### Ce que fait `@Injectable()`

1. **Enregistre les métadonnées DI**
   Cela permet à Nest de traiter la classe comme un provider injectable.

2. **Permet l’injection par constructeur**
   Nest peut résoudre et injecter les dépendances déclarées dans le constructeur.

3. **S’intègre au scope/cycle de vie des providers**
   La classe peut être scoped en `DEFAULT`, `REQUEST` ou `TRANSIENT` selon la
   configuration.

4. **Améliore la testabilité**
   Les services injectables sont faciles à remplacer/mocker dans les modules de
   test.

#### Pourquoi c’est nécessaire

1. **Découplage**
   Les controllers dépendent d’abstractions/services au lieu de créer
   manuellement leurs dépendances.

2. **Responsabilité unique**
   La logique métier vit dans les services, pas dans les controllers.

3. **Création d’objets centralisée**
   Le conteneur Nest contrôle l’instanciation, le partage et le comportement de
   cycle de vie.

4. **Architecture scalable**
   Les patterns DI restent maintenables à mesure que la taille de l’app et de
   l’équipe augmente.

#### Exemple

```ts
import { Injectable, Controller, Get } from '@nestjs/common';

@Injectable()
export class UsersService {
  findAll() {
    return [{ id: 1, email: 'user@example.com' }];
  }
}

@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  getUsers() {
    return this.usersService.findAll();
  }
}
```

#### Nuance pratique

`@Injectable()` seul ne suffit pas ; le provider doit aussi être enregistré dans
un module (tableau `providers`) ou exporté/importé via les frontières de modules
pour que Nest puisse le résoudre là où il est nécessaire.

</details>

<details>
<summary>9. Quelle est la différence entre `@Controller` et les décorateurs `@Get()`/`@Post()` ?</summary>

#### NestJS

`@Controller` et les décorateurs de méthode de route (`@Get`, `@Post`, etc.)
fonctionnent ensemble, mais couvrent des niveaux de routing différents.

#### Différence principale

1. **`@Controller()`**
   Déclare une classe comme controller et définit un **préfixe de route de
   base** pour tous les handlers de cette classe.

2. **`@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`**
   Associent une méthode de classe spécifique à une méthode HTTP + un chemin de
   route.

#### Modèle mental

1. `@Controller('users')` signifie : « Tous les endpoints de cette classe
   commencent par `/users`. »
2. `@Get(':id')` signifie : « Cette méthode gère `GET /users/:id`. »

#### Exemple

```ts
import { Body, Controller, Get, Param, Post } from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get()
  findAll() {
    return [{ id: 1, email: 'a@example.com' }];
  }

  @Get(':id')
  findOne(@Param('id') id: string) {
    return { id, email: 'a@example.com' };
  }

  @Post()
  create(@Body() dto: { email: string }) {
    return { id: 2, ...dto };
  }
}
```

Routes résolues :
1. `GET /users`
2. `GET /users/:id`
3. `POST /users`

#### Pourquoi cette séparation est utile

1. **Structure API claire**
   La classe regroupe les endpoints liés par domaine/ressource.

2. **Configuration réutilisable au niveau controller**
   Guards, interceptors, versioning et préfixes peuvent être appliqués au niveau
   de la classe.

3. **Couche de routing lisible**
   Les décorateurs de méthode rendent l’intention de chaque endpoint explicite et
   facile à parcourir.

</details>

<details>
<summary>10. Comment NestJS traite-t-il les requêtes HTTP et détermine-t-il quel controller appeler ?</summary>

#### NestJS

NestJS détermine le controller et le handler cibles à partir des métadonnées
collectées par les décorateurs lors du bootstrap de l’application, puis exécute
la requête via un pipeline défini.

#### Comment le routing est construit au démarrage

1. **Scan des modules**
   Nest scanne les modules importés et découvre les controllers/providers
   enregistrés.

2. **Collecte des métadonnées de route**
   `@Controller()` fournit le chemin de base ; `@Get/@Post/...` fournissent la
   méthode HTTP et le sous-chemin.

3. **Enregistrement des routes dans l’adaptateur**
   Nest combine les métadonnées en routes concrètes et les enregistre dans le
   routeur Express ou Fastify.

#### Ce qui se passe pour chaque requête entrante

1. La requête entre dans l’adaptateur HTTP sous-jacent (Express/Fastify).
2. Le routeur associe la méthode + l’URL à une méthode de controller.
3. Nest crée un `ExecutionContext` pour ce handler.
4. Le pipeline de requête s’exécute dans l’ordre :
   1. Middleware (si configuré)
   2. Guards (décision d’autorisation)
   3. Interceptors (avant le handler)
   4. Pipes (parsing/validation des paramètres)
   5. Exécution de la méthode du controller
   6. Interceptors (après handler, mapping de réponse)
   7. Exception filters (si des erreurs sont levées)
5. La réponse finale est renvoyée par l’adaptateur.

#### Comment Nest choisit la méthode exacte du controller

1. Matching par méthode HTTP (`GET`, `POST`, etc.).
2. Matching par chemin complet normalisé :
   `globalPrefix + controllerPath + handlerPath`.
3. Si le versioning est activé, les contraintes de version sont évaluées.
4. S’il y a des paramètres de route (`:id`), le pattern matching des paramètres
   est appliqué.

#### Exemple de mapping

```ts
@Controller('users')
export class UsersController {
  @Get(':id')
  findOne() {}
}
```

Si le préfixe global est `api`, la requête `GET /api/users/42` est mappée vers
`UsersController.findOne`.

#### À retenir

NestJS ne « recherche pas dynamiquement les controllers » à chaque requête. Il
pré-calcule la table de routing au bootstrap, puis exécute un cycle de requête
prévisible autour du handler correspondant.

</details>

<details>
<summary>11. Comment NestJS utilise-t-il les décorateurs pour construire la couche de routing ?</summary>

#### NestJS

Le routing de NestJS est piloté par les métadonnées. Les décorateurs annotent
les classes et les méthodes, puis Nest lit ces métadonnées au bootstrap pour
créer une map de routes concrète dans l’adaptateur HTTP sous-jacent.

#### Sources des métadonnées de routing

1. **`@Controller(path)`**
   Déclare un préfixe au niveau controller (namespace de ressource).

2. **Décorateurs de méthode**
   `@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`, `@Options()`,
   `@Head()`, `@All()` définissent la méthode HTTP + le chemin du handler.

3. **Décorateurs de paramètre**
   `@Param()`, `@Query()`, `@Body()`, `@Headers()`, `@Req()`, `@Res()`
   définissent comment les données de requête sont injectées dans les arguments
   du handler.

4. **Décorateurs transverses**
   `@UseGuards()`, `@UsePipes()`, `@UseInterceptors()`, `@UseFilters()`
   attachent le comportement d’exécution à la route/la classe.

#### Comment Nest construit les routes

1. Scanne les modules et découvre les controllers.
2. Lit les métadonnées controller + méthode via réflexion.
3. Compose le chemin complet :
   `globalPrefix + controllerPath + methodPath`.
4. Enregistre les handlers compilés dans le routeur Express/Fastify.
5. Enveloppe les handlers avec le pipeline guard/pipe/interceptor/filter.

#### Exemple

```ts
import { Body, Controller, Get, Param, Post, UseGuards } from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get(':id')
  getById(@Param('id') id: string) {
    return { id };
  }

  @Post()
  @UseGuards(AuthGuard)
  create(@Body() dto: { email: string }) {
    return { id: 'u_1', ...dto };
  }
}
```

Intention de routing résolue :
1. `GET /users/:id` -> `getById`
2. `POST /users` -> `create` (protégé par guard)

#### Pourquoi cette conception est puissante

1. **Déclarative et locale**
   Les règles de routing vivent près du code du handler.

2. **Composable**
   Les décorateurs de niveau classe et méthode se combinent naturellement.

3. **Cohérence du framework**
   Le même pattern s’applique à REST, aux resolvers GraphQL et aux handlers de
   messages microservices (avec des décorateurs spécifiques au transport).

</details>

<details>
<summary>12. Quelle est la différence entre `imports`, `exports`, `providers` et `declarations` dans `@Module` ?</summary>

#### NestJS

Dans les modules NestJS, `imports`, `providers` et `exports` définissent les
frontières essentielles de visibilité et de dépendances. `declarations` n’est
**pas** un champ de module NestJS (c’est un concept Angular), donc l’utiliser
dans `@Module()` est incorrect.

#### Champs de module corrects

1. **`providers`**
   Classes/factories/values créés dans le contexte DI de ce module.
   Ils sont disponibles à l’intérieur du même module par défaut.

2. **`imports`**
   Autres modules dont vous voulez utiliser les **providers exportés** dans ce
   module.
   Importer un module n’expose pas tous ses providers, uniquement ceux exportés.

3. **`exports`**
   Sous-ensemble des providers de ce module (ou modules ré-exportés) qui doivent
   être visibles pour les modules qui importent ce module.

4. **`controllers`**
   Handlers de routes appartenant à ce module (couche HTTP). Ils ne sont pas
   exportés comme providers injectables par défaut.

#### À propos de `declarations`

1. `declarations` est utilisé dans les NgModules Angular pour
   components/directives/pipes.
2. `@Module()` de NestJS ne supporte **pas** `declarations`.
3. Les équivalents NestJS sont surtout `controllers` + `providers`, selon le rôle.

#### Exemple

```ts
import { Module } from '@nestjs/common';

@Module({
  providers: [UsersService],     // créé dans le contexte UsersModule
  exports: [UsersService],       // rendu disponible aux modules importateurs
})
export class UsersModule {}

@Module({
  imports: [UsersModule],        // peut maintenant injecter UsersService exporté
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Règle pratique

1. Mettez les classes service/repository/factory dans `providers`.
2. Mettez les handlers de route dans `controllers`.
3. Mettez les modules externes nécessaires dans `imports`.
4. Mettez seulement la surface API réutilisable dans `exports`
   (évitez la sur-exportation).

</details>

<details>
<summary>13. Quelle est la différence entre `@Module imports` et `@Module providers` ?</summary>

#### NestJS

`imports` et `providers` dans `@Module()` répondent à des besoins DI différents :
1. `imports` relie les modules.
2. `providers` définit ce que ce module crée dans son propre scope DI.

#### `providers` : définitions locales

1. Déclare des services/factories/values instanciés dans le contexte de ce
   module.
2. Disponibles pour l’injection à l’intérieur de ce module.
3. Non visibles par les autres modules, sauf export explicite.

Exemple :

```ts
@Module({
  providers: [UsersService],
})
export class UsersModule {}
```

#### `imports` : dépendances externes

1. Importe d’autres modules pour consommer leurs **providers exportés**.
2. Ne copie pas tous les éléments internes du module importé.
3. Crée un graphe de dépendances explicite entre modules.

Exemple :

```ts
@Module({
  imports: [UsersModule], // peut injecter uniquement ce que UsersModule exporte
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Exemple combiné avec exports

```ts
@Module({
  providers: [UsersService],
  exports: [UsersService],
})
export class UsersModule {}

@Module({
  imports: [UsersModule],
  providers: [OrdersService],
})
export class OrdersModule {
  constructor(private readonly usersService: UsersService) {}
}
```

#### Distinction pratique

1. Ajoutez dans `providers` quand vous **possédez et créez** la dépendance ici.
2. Ajoutez dans `imports` quand la dépendance est **possédée par un autre
   module** et exportée.
3. Si l’injection échoue, vérifiez :
   1. Le provider est enregistré dans `providers` du module source.
   2. Le module source l’exporte dans `exports`.
   3. Le module consommateur inclut le module source dans `imports`.

</details>

<details>
<summary>14. Que sont les modules dynamiques et quand faut-il les utiliser ?</summary>

#### NestJS

Les modules dynamiques sont des modules dont la configuration est produite à
l’exécution via des méthodes factory statiques (souvent `forRoot`,
`forRootAsync`, `register`, `registerAsync`). Ils permettent de créer des
modules réutilisables, configurables différemment selon les applications/
environnements.

#### Pourquoi les modules dynamiques existent

1. **Configuration runtime**
   Passer des options (URLs, clés API, feature flags, choix de stratégie) lors
   de l’import du module.

2. **Modules de bibliothèque réutilisables**
   Emballer un module unique pouvant être consommé par plusieurs applications
   avec des paramètres différents.

3. **Initialisation asynchrone**
   Résoudre la configuration depuis `ConfigService`, un gestionnaire de secrets
   ou des sources distantes.

4. **Providers conditionnels**
   Créer des providers selon les options (ex. Redis vs cache en mémoire).

#### Patterns d’API typiques

1. `forRoot(options)` pour une configuration singleton à l’échelle de l’app.
2. `forRootAsync({...})` quand la config dépend de factories asynchrones/
   dépendances injectées.
3. `register(options)` pour une configuration scoped à une feature/par import.

#### Exemple

```ts
import { DynamicModule, Module } from '@nestjs/common';

export interface MailModuleOptions {
  host: string;
  apiKey: string;
}

export const MAIL_OPTIONS = Symbol('MAIL_OPTIONS');

@Module({})
export class MailModule {
  static forRoot(options: MailModuleOptions): DynamicModule {
    return {
      module: MailModule,
      providers: [
        { provide: MAIL_OPTIONS, useValue: options },
        MailService,
      ],
      exports: [MailService],
    };
  }
}
```

Utilisation :

```ts
@Module({
  imports: [
    MailModule.forRoot({
      host: 'smtp.example.com',
      apiKey: process.env.MAIL_API_KEY!,
    }),
  ],
})
export class AppModule {}
```

#### Quand utiliser des modules dynamiques

1. Pour construire des modules d’infrastructure partagés (DB, mail, cache,
   queue, clients d’auth).
2. Quand vous avez besoin d’un setup spécifique à l’environnement ou au tenant.
3. Quand vous avez besoin d’un bootstrap asynchrone avec `ConfigModule` et des
   factories injectées.

#### Quand ce n’est pas nécessaire

1. Si la configuration est statique et locale à l’app, des modules réguliers
   sont plus simples.
2. Si un seul provider doit varier, un provider factory peut suffire.

</details>

<details>
<summary>15. Quelle est la différence entre les types de providers dans NestJS ? (`useClass`, `useValue`, `useFactory`)</summary>

#### NestJS

Les providers NestJS peuvent être enregistrés avec différentes stratégies selon
la façon dont une instance/valeur doit être créée. Les plus courantes sont
`useClass`, `useValue` et `useFactory`.

#### 1) `useClass`

Crée une instance d’une classe via la DI de Nest.

1. Idéal pour les implémentations de service standard.
2. Supporte automatiquement l’injection par constructeur.
3. Utile pour changer d’implémentation selon l’environnement.

```ts
{
  provide: PaymentPort,
  useClass: StripePaymentService,
}
```

#### 2) `useValue`

Associe un token à une valeur/objet/constante déjà prête.

1. Aucune instanciation par Nest.
2. Très pratique pour les objets de config, singletons SDK, mocks de test.
3. Rapide et simple, mais sans cycle de vie DI pour cette valeur.

```ts
{
  provide: 'APP_CONFIG',
  useValue: { region: 'eu', retries: 3 },
}
```

#### 3) `useFactory`

Crée la valeur du provider via une fonction factory.

1. Permet de construire dynamiquement un objet.
2. Permet d’injecter d’autres providers dans la factory (tableau `inject`).
3. Fonctionne pour l’initialisation sync et async.

```ts
{
  provide: DbClient,
  useFactory: async (config: ConfigService) => {
    const client = new DbClient(config.get<string>('DB_URL')!);
    await client.connect();
    return client;
  },
  inject: [ConfigService],
}
```

#### Comparaison rapide

1. **`useClass`** : « Instancier cette classe avec la DI. »
2. **`useValue`** : « Utiliser exactement cette valeur telle quelle. »
3. **`useFactory`** : « Construire la valeur avec une logique personnalisée
   (et des dépendances injectées optionnelles). »

#### Quand choisir quoi

1. Choisissez `useClass` pour les services applicatifs normaux et les
   implémentations polymorphes.
2. Choisissez `useValue` pour les constantes, instances tierces et doubles de test.
3. Choisissez `useFactory` pour la construction conditionnelle/asynchrone et les
   setups complexes.

#### Note pratique

Les trois stratégies sont résolues par **token** (`provide`). Un bon design de
tokens (token de classe, symbole ou constante string) est essentiel pour une DI
maintenable.

</details>

<details>
<summary>16. Qu’est-ce que le scope d’un provider ? (`DEFAULT`, `REQUEST`, `TRANSIENT`)</summary>

#### NestJS

Le scope d’un provider dans NestJS définit **la durée de vie des instances** et
**la fréquence de création de nouvelles instances** par le conteneur DI.

#### Types de scope

1. **`DEFAULT` (singleton)**
   Une instance partagée pour tout le cycle de vie de l’application.

2. **`REQUEST`**
   Nouvelle instance par requête entrante (contexte HTTP/RPC/message).

3. **`TRANSIENT`**
   Nouvelle instance à chaque injection/résolution du provider.

#### 1) Scope `DEFAULT`

1. Le plus performant et le plus courant.
2. Idéal pour les services stateless (logique métier, repositories, mappers).
3. L’état partagé dans ce service est global au processus de l’application.

```ts
@Injectable()
export class UsersService {}
```

#### 2) Scope `REQUEST`

1. À utiliser quand le service doit être sensible à la requête (tenant,
   correlation ID, cache par requête, contexte utilisateur).
2. Augmente le coût de création d’objets.
3. Si un singleton dépend d’un provider request-scoped, le graphe de dépendances
   peut nécessiter des ajustements de propagation de scope.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.REQUEST })
export class RequestContextService {}
```

#### 3) Scope `TRANSIENT`

1. Instance fraîche à chaque point d’injection.
2. Utile pour des helpers légers et stateful où une instance partagée n’est pas
   souhaitable.
3. Peut être coûteux s’il est surutilisé dans des graphes d’objets profonds.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.TRANSIENT })
export class AuditBuilder {}
```

#### Guide pratique de décision

1. Commencez avec `DEFAULT`.
2. Passez à `REQUEST` seulement pour de vrais besoins d’état par requête.
3. Utilisez `TRANSIENT` pour des objets helper mutables et à portée étroite.

#### Note performance et architecture

Le scope est à la fois un choix de correction et de performance. Surutiliser des
scopes non-singleton peut augmenter la latence et le churn mémoire ; appliquez
ces scopes de manière intentionnelle.

</details>

<details>
<summary>17. Comment gérez-vous les dépendances circulaires (`forwardRef`) dans les grands systèmes ?</summary>

#### NestJS

Les dépendances circulaires apparaissent lorsque deux providers/modules
dépendent l’un de l’autre directement ou via une chaîne. Dans NestJS, la
solution de premier niveau est le découplage architectural ; `forwardRef()` est
un outil tactique quand le refactoring n’est pas immédiatement possible.

#### Pourquoi les dépendances circulaires sont risquées

1. Couplage fort entre domaines.
2. Tests et refactoring plus difficiles.
3. Frontières de responsabilité peu claires.
4. Complexité du bootstrap/de la résolution DI.

#### Stratégie préférée : supprimer le cycle

1. **Extraire la logique partagée**
   Déplacer le comportement commun vers un troisième service/module
   (`SharedDomainService`).

2. **Dépendre de tokens d’abstraction**
   Remplacer la dépendance directe à une classe par un token type interface +
   adaptateur.

3. **Domain events / messagerie asynchrone**
   Publier un événement depuis A, traité dans B, au lieu d’une chaîne d’appels
   directe.

4. **Redécouper les frontières de modules**
   Réorganiser par use-case/domaine pour préserver une direction de dépendance
   unique.

#### `forwardRef()` pour les cas inévitables

Utilisez `forwardRef()` quand deux providers/modules doivent se référencer
mutuellement pendant la résolution DI.

Exemple au niveau provider :

```ts
import { Inject, Injectable, forwardRef } from '@nestjs/common';

@Injectable()
export class UsersService {
  constructor(
    @Inject(forwardRef(() => AuthService))
    private readonly authService: AuthService,
  ) {}
}
```

```ts
import { Inject, Injectable, forwardRef } from '@nestjs/common';

@Injectable()
export class AuthService {
  constructor(
    @Inject(forwardRef(() => UsersService))
    private readonly usersService: UsersService,
  ) {}
}
```

Exemple au niveau module :

```ts
@Module({
  imports: [forwardRef(() => AuthModule)],
  providers: [UsersService],
  exports: [UsersService],
})
export class UsersModule {}

@Module({
  imports: [forwardRef(() => UsersModule)],
  providers: [AuthService],
  exports: [AuthService],
})
export class AuthModule {}
```

#### Recommandations pour les grands systèmes

1. Traitez `forwardRef()` comme temporaire/cas limite, pas comme design par
   défaut.
2. Suivez les dépendances circulaires dans les revues d’architecture et
   supprimez-les progressivement.
3. Ajoutez des tests autour des flux critiques liés au cycle avant refactoring.
4. Préférez des graphes de dépendances unidirectionnels entre bounded contexts.

</details>

<details>
<summary>18. Comment structurer une application NestJS scalable ?</summary>

#### NestJS

Une application NestJS scalable est structurée autour de frontières de domaine
claires, d’une direction de dépendances maîtrisée et de patterns transverses
prévisibles.

#### Principes structurels fondamentaux

1. **Modularité par domaine (bounded contexts)**
   Découper par capacités métier (`Users`, `Billing`, `Orders`), pas uniquement
   par couches techniques.

2. **Responsabilités en couches dans chaque module**
   Garder les controllers légers, les services orientés orchestration, et les
   adaptateurs d’infrastructure isolés.

3. **Règle de dépendance**
   La logique métier de plus haut niveau ne doit pas dépendre directement des
   détails framework/infrastructure.

4. **Contrats explicites**
   Utiliser DTOs, schémas de validation et interfaces/tokens pour les
   frontières.

#### Layout de module pratique (exemple)

```text
src/
  modules/
    users/
      application/
        users.service.ts
        commands/
        queries/
      domain/
        entities/
        value-objects/
        ports/
      infrastructure/
        persistence/
        http/
      users.controller.ts
      users.module.ts
  common/
    guards/
    interceptors/
    filters/
    pipes/
    decorators/
  config/
  main.ts
```

#### Patterns architecturaux qui passent à l’échelle

1. **Feature modules + shared kernel**
   Garder les utilitaires partagés minimaux pour éviter un « god common module ».

2. **Ports et adaptateurs**
   La couche métier dépend d’abstractions ; les adaptateurs implémentent les
   détails DB/API/message-bus.

3. **CQRS quand la complexité le justifie**
   Séparer modèles write/read pour les domaines complexes, pas partout par
   défaut.

4. **Frontières asynchrones**
   Utiliser événements/queues pour les workflows inter-modules et l’eventual
   consistency.

#### Enjeux de scalabilité opérationnelle

1. **Gestion de configuration**
   Configuration centralisée et typée, avec validation d’environnement.

2. **Observability**
   Structured logging, tracing, metrics et correlation IDs.

3. **Stratégie d’erreurs**
   Exception filters globaux + mapping d’erreurs spécifique au domaine.

4. **Performance**
   Caching, pagination, backpressure, indexation DB et éviter l’abus du
   request-scope.

#### Pratiques de scalabilité d’équipe

1. Imposer des gates lint/format/type/tests en CI.
2. Garder une ownership des modules claire (codeowners ou carte d’ownership de
   service).
3. Revoir les décisions d’architecture (ADRs) pour les nouvelles dépendances
   cross-domain.
4. Préférer un refactoring incrémental aux réécritures big-bang.

#### En résumé

La scalabilité dans NestJS est surtout une discipline d’architecture : modules
orientés domaine, dépendances contrôlées et préoccupations plateforme
standardisées autour de ces modules.

</details>

<details>
<summary>19. Comment concevoir une API REST avec une bonne séparation des responsabilités ?</summary>

#### NestJS

Une bonne séparation des responsabilités dans une API REST NestJS signifie que
chaque couche a une responsabilité unique et claire, et que les dépendances
circulent dans un seul sens.

#### Répartition recommandée des responsabilités

1. **Couche Controller (transport)**
   Ne gère que les préoccupations HTTP : routing, status codes,
   mapping requête/réponse, décorateurs d’auth et binding des entrées.

2. **Couche Application/Service (use cases)**
   Orchestre les workflows métier et les transactions ; sans logique spécifique
   à HTTP.

3. **Couche Domaine (règles métier)**
   Encapsule les règles centrales, invariants, entities/value objects et domain
   services.

4. **Couche Infrastructure**
   Implémente la persistance, les API externes, les queues et autres adaptateurs.

#### Ce qu’il ne faut PAS mélanger

1. Requêtes base de données dans les controllers.
2. Objets HTTP (`Request`, `Response`) dans la logique domaine.
3. Validation/invariants métier dispersés sur plusieurs couches.
4. Détails de SDK externes qui fuient dans les contrats des use cases.

#### Flux pratique

1. Le controller reçoit un DTO (`@Body`, `@Query`, `@Param`).
2. Un pipe valide/transforme le DTO.
3. Le controller appelle une méthode du service d’application.
4. Le service utilise repositories/ports et règles de domaine.
5. Le service renvoie un modèle de résultat.
6. Le controller mappe le résultat vers un DTO de réponse/view model.

#### Squelette d’exemple

```ts
// controller
@Post()
create(@Body() dto: CreateOrderDto): Promise<OrderView> {
  return this.ordersAppService.createOrder(dto);
}

// application service
async createOrder(dto: CreateOrderDto): Promise<OrderView> {
  const order = Order.create(dto.customerId, dto.items); // règle de domaine
  await this.ordersRepo.save(order);                     // port infrastructure
  return OrderView.from(order);                          // mapping de sortie
}
```

#### Techniques de conception utiles

1. **DTOs pour les contrats API**
   Séparer les contrats d’entrée/sortie des entités internes.

2. **Interfaces repository/port**
   Dépendre d’abstractions, pas directement des clients ORM dans la couche
   métier.

3. **Composants transverses globaux**
   Utiliser guards/pipes/interceptors/filters pour auth, validation, logging,
   erreurs.

4. **Versioning et idempotence**
   Appliquer une stratégie de versioning API et des clés d’idempotence pour les
   opérations non sûres.

5. **Modèle d’erreur cohérent**
   Mapper les erreurs domaine/infrastructure vers des réponses HTTP stables de
   type problem.

#### Résultat

Avec cette séparation, votre API est plus facile à tester, refactorer et faire
évoluer : les changements de transport ne cassent pas la logique domaine, et
l’infrastructure peut évoluer indépendamment.

</details>

<details>
<summary>20. Quel est le cycle de vie complet d’une requête dans NestJS ?</summary>

#### NestJS

Le cycle de vie d’une requête NestJS est un pipeline déterministe autour d’un
handler de route correspondant. Comprendre cet ordre est essentiel pour debugger
l’auth, la validation et le façonnage des réponses.

#### Séquence de haut niveau

1. La requête entrante atteint l’adaptateur de plateforme (Express/Fastify).
2. La route est mappée à une méthode de controller.
3. Nest exécute les composants du pipeline framework dans un ordre défini.
4. La réponse est renvoyée (ou l’exception est gérée par les filters).

#### Ordre détaillé du cycle de vie

1. **Middleware**
   S’exécute avant les guards ; utilisé pour le prétraitement bas niveau de la
   requête (logging, correlation ID, manipulation brute des headers, etc.).

2. **Guards**
   Décident si l’exécution est autorisée (`canActivate`).
   Si un guard retourne `false`/lève une exception, la requête s’arrête ici.

3. **Interceptors (avant handler)**
   Enveloppent l’exécution ; peuvent démarrer des timers, attacher un contexte,
   ou court-circuiter un comportement.

4. **Pipes**
   S’exécutent sur les arguments de route pour transformer/valider les données
   entrantes (`@Body`, `@Param`, `@Query`, params personnalisés).

5. **Controller handler**
   Le use case métier est invoqué (souvent en déléguant à la couche service).

6. **Interceptors (après handler)**
   Peuvent mapper/stream/cacher les réponses et finaliser la logique
   d’observability.

7. **Exception filters**
   Capturent les exceptions non gérées et les convertissent en réponses HTTP.

#### Modèle visuel d’exécution

1. Middleware -> Guards -> Interceptors (pre) -> Pipes -> Handler ->
   Interceptors (post) -> Response
2. Toute erreur levée dans le pipeline/handler -> Exception Filters

#### Notes sur le scope et la précédence

1. La plupart des composants de pipeline peuvent être appliqués au niveau :
   1. Global
   2. Controller
   3. Route-handler
2. Nest fusionne ces niveaux ; la config route-level est en général la plus spécifique.

#### Conseils pratiques de debugging

Si le comportement est inattendu :
1. Vérifiez d’abord si la requête est bloquée par un guard.
2. Vérifiez la transformation/validation par pipe sur les paramètres.
3. Inspectez la chaîne d’interceptors pour les changements de mapping de réponse.
4. Confirmez le formatage des erreurs par les exception filters.

Connaître cet ordre évite les hypothèses « magiques » et accélère fortement le
diagnostic des incidents de production.

</details>

<details>
<summary>21. Quelle est la différence entre Middleware, Guards, Pipes et Interceptors ?</summary>

#### NestJS

Ces quatre composants NestJS participent tous au traitement des requêtes, mais
ils ont des responsabilités différentes et s’exécutent à des étapes différentes
du cycle de vie.

#### Comparaison rapide des rôles

1. **Middleware**
   Prétraitement HTTP avant routing/avant handler.

2. **Guards**
   Barrière d’autorisation : décide si la requête peut continuer.

3. **Pipes**
   Transforment et valident les arguments du handler.

4. **Interceptors**
   Enveloppent l’exécution du handler avant/après, pour la logique de réponse
   transverse.

#### Différences plus profondes par responsabilité

1. **Middleware**
   Idéal pour le travail générique de niveau transport : logging de requête,
   correlation IDs, headers, parsing de cookies, mutation brute de la requête.

2. **Guards**
   Idéal pour les décisions auth/authz : présence JWT, vérifications de rôles,
   checks de policy.
   Retourne `true/false` (ou lève une exception) pour autoriser/refuser
   l’exécution de la route.

3. **Pipes**
   Idéal pour la qualité des entrées : parsing (`string -> number`), validation
   (règles DTO), sanitization/normalization au niveau paramètre.

4. **Interceptors**
   Idéal pour l’enveloppement d’exécution : mapping de réponse, caching,
   timing de métriques, tracing, wrappers timeout/retry, gestion de flux.

#### Position dans le cycle de vie

1. Middleware
2. Guards
3. Interceptors (avant)
4. Pipes
5. Handler
6. Interceptors (après)
7. Exception filters (chemin d’erreur)

#### Exemples typiques

1. Middleware : attacher `requestId`.
2. Guard : rejeter la requête si le token est invalide.
3. Pipe : valider `CreateUserDto`.
4. Interceptor : transformer l’enveloppe de réponse `{ data, meta }`.

#### Règle de sélection pratique

1. Besoin de décider **qui peut accéder** ? -> Guard.
2. Besoin de garantir la **forme/le type des entrées** ? -> Pipe.
3. Besoin d’un **enveloppement avant/après handler** ? -> Interceptor.
4. Besoin de prétraitement HTTP bas niveau hors sémantique de route ? -> Middleware.

</details>

<details>
<summary>22. Comment appliquer un Middleware globalement vs sur une route spécifique ?</summary>

#### NestJS

Dans NestJS, le middleware peut être appliqué globalement (sur beaucoup/toutes
les routes) ou sélectivement (controllers/routes spécifiques). Le mécanisme
diffère de guards et interceptors, car le middleware se configure via l’API du
module consumer ou au bootstrap de l’app.

#### 1) Appliquer un middleware globalement

À utiliser quand le comportement est nécessaire pour presque chaque requête
(request IDs, logging commun, bootstrap de security headers, etc.).

Configuration globale au niveau module :

```ts
import { MiddlewareConsumer, Module, NestModule } from '@nestjs/common';

@Module({})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer.apply(LoggerMiddleware).forRoutes('*');
  }
}
```

Vous pouvez aussi cibler tous les controllers via des patterns basés sur des
classes dans `forRoutes(...)`.

#### 2) Appliquer un middleware à des routes/controllers spécifiques

À utiliser uniquement pour des préoccupations spécifiques à une feature.

```ts
import {
  MiddlewareConsumer,
  Module,
  NestModule,
  RequestMethod,
} from '@nestjs/common';
import { UsersController } from './users.controller';

@Module({})
export class UsersModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer
      .apply(AuthAuditMiddleware)
      .forRoutes(
        UsersController, // toutes les routes du controller
        { path: 'users/:id', method: RequestMethod.PATCH }, // route exacte
      );
  }
}
```

#### Exclure des routes

Vous pouvez attacher un middleware large et exclure des endpoints sensibles/publics :

```ts
consumer
  .apply(AuthMiddleware)
  .exclude(
    { path: 'health', method: RequestMethod.GET },
    { path: 'auth/login', method: RequestMethod.POST },
  )
  .forRoutes('*');
```

#### Recommandations pratiques

1. Préférez le middleware global uniquement pour les préoccupations vraiment
   transverses.
2. Gardez le middleware léger ; la logique authz lourde appartient aux Guards.
3. Utilisez un middleware spécifique à la route pour les comportements bornés à
   une feature.
4. Si vous avez besoin de vérifications métier fortement liées à la DI,
   déplacez la logique du middleware vers des Guards ou Interceptors.

</details>

<details>
<summary>23. Qu’est-ce que `ExecutionContext` et comment est-il utilisé ?</summary>

#### NestJS

`ExecutionContext` est une abstraction NestJS qui décrit l’environnement
courant d’exécution d’un handler. Elle étend `ArgumentsHost` et fournit aux
composants du framework (Guards, Interceptors, Filters, décorateurs
personnalisés) une manière unifiée d’accéder aux données spécifiques à la
requête, quel que soit le transport.

#### Pourquoi `ExecutionContext` existe

1. **Accès agnostique au transport**
   Le même pattern d’API fonctionne pour HTTP, WebSockets et microservices.

2. **Introspection handler/classe**
   Vous pouvez inspecter la classe controller et la méthode en cours
   d’exécution.

3. **Cohérence des composants transverses**
   Guards/interceptors/filters peuvent fonctionner avec un seul modèle de
   contexte.

#### APIs clés

1. `context.getType()`
   Retourne le type d’exécution (`http`, `ws`, `rpc`).

2. `context.switchToHttp()`
   Donne accès à `getRequest()`, `getResponse()`, `getNext()`.

3. `context.switchToWs()` / `context.switchToRpc()`
   Donne accès aux données spécifiques websocket/microservice.

4. `context.getClass()` et `context.getHandler()`
   Retourne la classe controller courante et la référence de méthode.

#### Usage courant dans un Guard

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';

@Injectable()
export class JwtGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const req = context.switchToHttp().getRequest();
    const authHeader = req.headers.authorization;
    return Boolean(authHeader);
  }
}
```

#### Usage courant avec métadonnées + Reflector

```ts
const isPublic = this.reflector.getAllAndOverride<boolean>('isPublic', [
  context.getHandler(),
  context.getClass(),
]);
```

Ce pattern lit les métadonnées route/classe (ex. `@Public()`, `@Roles(...)`) et
est largement utilisé dans les guards d’autorisation.

#### À retenir

Pensez à `ExecutionContext` comme à l’enveloppe runtime du framework pour l’appel
courant d’un endpoint : il vous dit **où vous êtes**
(handler/classe/transport) et vous permet d’accéder proprement aux données de
requête spécifiques au transport.

</details>

<details>
<summary>24. Qu’est-ce qu’un Guard et en quoi diffère-t-il d’un Middleware ?</summary>

#### NestJS

Un **Guard** dans NestJS est une classe qui implémente `CanActivate` et décide
si la requête courante est autorisée à atteindre un route handler.

#### Ce que fait un Guard

1. S’exécute avant l’exécution du handler.
2. Retourne `true` pour autoriser, `false` (ou lève une exception) pour refuser.
3. A accès à `ExecutionContext` (handler, controller, transport, requête).
4. Est couramment utilisé pour l’authentification et l’autorisation.

#### Différences entre Guard et Middleware

1. **Finalité de décision**
   Le Guard est une barrière d’autorisation explicite.
   Le Middleware est un prétraitement générique de requête.

2. **Connaissance du framework**
   Le Guard connaît la classe/le handler cible via `ExecutionContext`.
   Le Middleware n’a généralement pas le contexte des métadonnées de
   route-handler.

3. **Position dans le cycle de vie**
   Le Middleware s’exécute plus tôt.
   Le Guard s’exécute après le middleware, avant pipes/interceptors/handler.

4. **Cas d’usage typiques**
   Guard : JWT/rôles/policies.
   Middleware : logging, request IDs, normalisation des headers, mutation brute
   de requête.

#### Exemple de Guard

```ts
import { CanActivate, ExecutionContext, Injectable, UnauthorizedException } from '@nestjs/common';

@Injectable()
export class AuthGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const req = context.switchToHttp().getRequest();
    const token = req.headers.authorization;
    if (!token) throw new UnauthorizedException('Missing token');
    return true;
  }
}
```

#### Règle pratique

1. Besoin de décider « cet utilisateur peut-il accéder à cette route ? » -> **Guard**.
2. Besoin de prétraitement HTTP bas niveau avant handler, indépendamment de la
   sémantique de route -> **Middleware**.

</details>

<details>
<summary>25. Comment les Guards s’intègrent-ils à l’autorisation ?</summary>

#### NestJS

Les Guards sont la barrière d’autorisation principale dans NestJS. Ils évaluent
si le principal authentifié courant peut accéder à une route spécifique,
généralement en combinant l’identité de requête avec les métadonnées de route
(rôles, policies, permissions).

#### Flux d’autorisation typique avec Guards

1. **Étape d’authentification**
   Un guard en amont (ou une stratégie Passport) valide le token/la session et
   attache `request.user`.

2. **Déclaration de métadonnées sur la route**
   La route est annotée avec des exigences, par ex. `@Roles('admin')` ou des clés
   de policy.

3. **Évaluation du guard d’autorisation**
   Le guard lit les métadonnées via `Reflector` + lit `request.user` et décide de
   l’accès.

4. **Autoriser ou refuser**
   Retourner `true` pour continuer ; sinon retourner `false` ou lever
   `ForbiddenException`.

#### Exemple basé rôles (RBAC)

Décorateur Roles :

```ts
import { SetMetadata } from '@nestjs/common';
export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Guard :

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const required = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(),
      context.getClass(),
    ]);
    if (!required) return true;

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];
    return required.some(role => userRoles.includes(role));
  }
}
```

Utilisation :

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Patterns d’intégration dans les systèmes réels

1. **Stacked guards**
   `JwtAuthGuard` (identité) + `Roles/PoliciesGuard` (logique d’autorisation).

2. **ABAC/policy engine**
   Le guard délègue la décision à un service de policy
   (subject, action, resource).

3. **Contrôles contextuels**
   Le guard lit les paramètres de route/le propriétaire de ressource et impose
   des règles de ownership.

#### Bonnes pratiques

1. Gardez les guards légers ; déplacez la logique lourde vers des services
   d’autorisation dédiés.
2. Utilisez des décorateurs de métadonnées pour des règles d’accès déclaratives
   et auditables.
3. Distinguez les échecs d’authentification (`401`) des échecs d’autorisation
   (`403`).
4. Testez les guards avec des scénarios de permissions positifs et négatifs.

</details>

<details>
<summary>26. Qu’est-ce que `@SetMetadata()` et comment fonctionne-t-il avec les Guards via `Reflector` ?</summary>

#### NestJS

`@SetMetadata()` est un décorateur helper NestJS utilisé pour attacher des
métadonnées personnalisées à une classe ou une méthode. Les Guards peuvent
ensuite lire ces métadonnées via `Reflector` et appliquer l’autorisation ou
un autre comportement spécifique à la route.

#### Idée centrale

1. `@SetMetadata(key, value)` écrit des métadonnées sur la route/la classe.
2. Le Guard utilise `Reflector` pour lire les métadonnées à l’exécution.
3. Le Guard décide si la requête est autorisée.

#### Pourquoi ce pattern est important

1. **Règles d’accès déclaratives**
   Les permissions sont visibles directement sur les endpoints.

2. **Séparation des responsabilités**
   Les controllers déclarent l’intention ; les guards implémentent la logique
   d’application.

3. **Réutilisabilité**
   Un guard peut gérer de nombreuses routes avec des valeurs de métadonnées
   différentes.

#### Exemple : métadonnées de rôles

Décorateur :

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Utilisation sur un endpoint :

```ts
@Controller('users')
export class UsersController {
  @Get()
  @Roles('admin', 'manager')
  findAll() {
    return [];
  }
}
```

Guard lisant les métadonnées :

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(), // metadata de méthode
      context.getClass(),   // metadata de controller
    ]);

    if (!requiredRoles) return true;

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];
    return requiredRoles.some(role => userRoles.includes(role));
  }
}
```

#### Méthodes `Reflector` les plus utilisées

1. `get(key, target)` -> lit les métadonnées d’une cible spécifique.
2. `getAllAndOverride(key, [handler, class])` -> la metadata de méthode
   surcharge celle de classe.
3. `getAllAndMerge(key, [handler, class])` -> combine les valeurs des deux
   niveaux.

#### À retenir

`@SetMetadata()` + `Reflector` est le mécanisme standard NestJS pour construire
une autorisation et des règles de comportement de route propres, scalables et
pilotées par métadonnées.

</details>

<details>
<summary>27. Comment implémenter l’authentification JWT via un Guard ?</summary>

#### NestJS

L’authentification JWT dans NestJS est généralement implémentée avec un Guard
qui valide le token et attache l’identité utilisateur au contexte de requête.

#### Architecture standard

1. **AuthService**
   Signe et vérifie les JWT.

2. **Stratégie/guard JWT**
   Extrait le bearer token, le valide, puis définit `request.user`.

3. **Routes protégées**
   Utilisent `@UseGuards(...)` pour exiger l’authentification.

Vous pouvez l’implémenter avec Passport (`@nestjs/passport`) ou avec un guard
personnalisé.

#### Guard JWT personnalisé minimal (sans Passport)

```ts
import {
  CanActivate,
  ExecutionContext,
  Injectable,
  UnauthorizedException,
} from '@nestjs/common';
import { JwtService } from '@nestjs/jwt';

@Injectable()
export class JwtAuthGuard implements CanActivate {
  constructor(private readonly jwtService: JwtService) {}

  async canActivate(context: ExecutionContext): Promise<boolean> {
    const req = context.switchToHttp().getRequest();
    const auth = req.headers.authorization as string | undefined;

    if (!auth?.startsWith('Bearer ')) {
      throw new UnauthorizedException('Missing bearer token');
    }

    const token = auth.slice(7);

    try {
      const payload = await this.jwtService.verifyAsync(token);
      req.user = payload; // attache l’identité pour les handlers/guards suivants
      return true;
    } catch {
      throw new UnauthorizedException('Invalid or expired token');
    }
  }
}
```

#### Protéger des routes

```ts
import { Controller, Get, Req, UseGuards } from '@nestjs/common';

@Controller('profile')
export class ProfileController {
  @Get('me')
  @UseGuards(JwtAuthGuard)
  me(@Req() req: any) {
    return req.user;
  }
}
```

#### Configuration `JwtModule`

```ts
JwtModule.register({
  secret: process.env.JWT_ACCESS_SECRET,
  signOptions: { expiresIn: '15m' },
});
```

#### Bonnes pratiques en production

1. Utiliser des secrets séparés pour access et refresh tokens.
2. Garder les access tokens de courte durée.
3. Valider explicitement issuer/audience/algorithm.
4. Préférer `401 Unauthorized` pour les erreurs de token.
5. Combiner avec un guard d’autorisation (rôles/policies) pour les permissions.
6. Ajouter une stratégie de révocation de token si nécessaire
   (blacklist/versioning/rotation).

#### Note pratique

Dans les grandes applications, `AuthGuard('jwt')` de Passport + `JwtStrategy`
est souvent plus propre pour la réutilisation et l’intégration à l’écosystème,
mais le principe de base reste le même : extraire -> vérifier -> attacher
l’utilisateur -> autoriser/refuser.

</details>

<details>
<summary>28. Comment implémenter RBAC et ABAC dans NestJS, et quand chaque approche est-elle préférable ?</summary>

#### NestJS

RBAC et ABAC sont deux modèles d’autorisation qui peuvent tous deux être
implémentés dans NestJS avec Guards + métadonnées + services d’autorisation.

#### RBAC vs ABAC

1. **RBAC (Role-Based Access Control)**
   L’accès est accordé selon les rôles utilisateur (ex. `admin`, `editor`,
   `viewer`).

2. **ABAC (Attribute-Based Access Control)**
   L’accès est accordé en évaluant des attributs (utilisateur, ressource,
   action, contexte) : ownership, département, région, statut, fenêtre
   temporelle, etc.

#### Quand chaque modèle est le meilleur

1. Choisissez **RBAC** quand :
   1. Le modèle de permissions est simple et stable.
   2. La hiérarchie des rôles est claire.
   3. Une implémentation rapide et un audit facile sont prioritaires.

2. Choisissez **ABAC** quand :
   1. Les règles dépendent des données de ressource et du contexte.
   2. Vous avez besoin de décisions fines et dynamiques.
   3. La complexité des policies multi-tenant/enterprise est élevée.

3. Utilisez un **hybride RBAC + ABAC** dans la plupart des systèmes réels :
   RBAC pour l’accès grossier, ABAC pour les opérations sensibles.

#### Pattern d’implémentation RBAC dans NestJS

1. Décorateur `@Roles(...)` via `SetMetadata`.
2. `RolesGuard` lit les métadonnées avec `Reflector`.
3. Le guard compare les rôles requis avec `request.user.roles`.

```ts
export const Roles = (...roles: string[]) => SetMetadata('roles', roles);
```

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Pattern d’implémentation ABAC dans NestJS

1. Définir un service de policy/ability (`can(user, action, resource)`).
2. Dans le guard, charger la ressource cible (ou assez d’attributs).
3. Évaluer la policy et autoriser/refuser.

```ts
@Injectable()
export class PoliciesGuard implements CanActivate {
  constructor(private readonly policy: PolicyService) {}

  async canActivate(ctx: ExecutionContext): Promise<boolean> {
    const req = ctx.switchToHttp().getRequest();
    const user = req.user;
    const order = await req.orderLoader.load(req.params.id); // exemple
    return this.policy.can(user, 'update', order);
  }
}
```

#### Bonnes pratiques de conception

1. Gardez le guard léger ; déléguez la logique de règles à un service de policy
   dédié.
2. Évitez de coder en dur les règles dans les controllers.
3. Mettez en cache les lookups liés aux policies quand c’est sûr.
4. Retournez `403 Forbidden` pour les refus d’autorisation (pas `401`).
5. Journalisez le contexte de décision pour l’auditabilité dans les domaines
   critiques.

#### Recommandation pratique

Commencez avec RBAC pour la vitesse de base, puis introduisez ABAC dans les flux
à haut risque/forte variabilité (ownership checks, sensibilité des données,
frontières de tenant, actions conditionnelles).

</details>

<details>
<summary>29. Comment implémenter la rotation des refresh tokens et pourquoi est-ce important ?</summary>

#### NestJS

La rotation des refresh tokens consiste à émettre un **nouveau refresh token à
chaque requête de refresh** et à invalider le précédent. Cela réduit le risque
de replay si un refresh token est volé.

#### Pourquoi c’est important

1. Limite l’impact d’une fuite de refresh token.
2. Détecte les attaques de réutilisation de token (ancien token volé réutilisé).
3. Permet des sessions longues sécurisées sans access tokens longue durée.
4. Améliore le contrôle de session entre appareils.

#### Modèle de token recommandé

1. **Access token** : TTL court (ex. 5-15 min), JWT stateless.
2. **Refresh token** : TTL plus long (jours/semaines), roté à chaque usage.
3. Stocker uniquement le **hash du refresh token** (ou des métadonnées de famille de token) en DB.
4. Suivre la famille/session de token (`sessionId`, `jti`, `rotatedFrom`, `revokedAt`).

#### Flux de rotation dans NestJS

1. L’utilisateur se connecte -> émettre access + refresh token (RT1), persister
   le hash RT1 + métadonnées.
2. Le client appelle `/auth/refresh` avec RT1.
3. Le serveur vérifie signature/expiration et compare le hash avec le token actif
   stocké.
4. Si valide :
   1. Révoquer RT1.
   2. Émettre AT2 + RT2.
   3. Persister le hash RT2 comme token actif pour cette session.
5. Si l’ancien RT1 est réutilisé plus tard :
   1. Marquer comme réutilisation suspecte.
   2. Révoquer toute la session/famille de token.
   3. Forcer une ré-authentification.

#### Sketch minimal au niveau service

```ts
async rotateRefreshToken(userId: string, presentedRt: string, sessionId: string) {
  const session = await this.sessionsRepo.findById(sessionId);
  if (!session || session.revokedAt) throw new UnauthorizedException();

  const matches = await this.hash.compare(presentedRt, session.refreshTokenHash);
  if (!matches) {
    await this.sessionsRepo.revokeFamily(session.familyId); // réponse à la détection de réutilisation
    throw new UnauthorizedException('Refresh token reuse detected');
  }

  const newAccessToken = this.jwt.sign({ sub: userId }, { expiresIn: '15m' });
  const newRefreshToken = this.jwt.sign(
    { sub: userId, sid: sessionId, jti: randomUUID() },
    { expiresIn: '7d', secret: this.refreshSecret },
  );

  await this.sessionsRepo.updateRefreshHash(sessionId, await this.hash.make(newRefreshToken));
  return { accessToken: newAccessToken, refreshToken: newRefreshToken };
}
```

#### Notes d’implémentation NestJS

1. Utiliser une config/des secrets `JwtModule` dédiés pour access vs refresh tokens.
2. Protéger l’endpoint refresh avec un guard/une stratégie refresh-token.
3. Garder le refresh token dans un cookie httpOnly sécurisé quand possible.
4. Ajouter une table device/session pour logout multi-device et révocation.

#### Bonnes pratiques de sécurité

1. Hasher les refresh tokens au repos.
2. Lier le refresh token aux métadonnées de session/appareil.
3. Faire la rotation à chaque requête refresh, sans exception.
4. Révoquer la famille de tokens en cas de réutilisation détectée.
5. Logger les événements de rotation/réutilisation pour le monitoring d’incident.

</details>

<details>
<summary>30. Qu’est-ce qu’un Pipe dans NestJS et quand faut-il l’utiliser ?</summary>

#### NestJS

Un Pipe dans NestJS est une classe qui implémente `PipeTransform` et s’exécute
avant un route handler pour **transformer** et/ou **valider** les données
entrantes.

#### Ce que font les Pipes

1. **Transformation**
   Convertir des valeurs transport brutes vers les types attendus (ex. string ->
   number, string -> objet UUID, trimming/normalisation).

2. **Validation**
   Appliquer des règles DTO/schema et rejeter tôt les entrées invalides.

3. **Comportement fail-fast**
   Lever une exception (généralement `BadRequestException`) avant l’exécution de
   la logique métier.

#### Où les Pipes s’insèrent dans le cycle de vie

1. Middleware
2. Guards
3. Interceptors (pre)
4. **Pipes**
5. Handler
6. Interceptors (post)
7. Exception filters

#### Exemples de pipes intégrés

1. `ValidationPipe`
2. `ParseIntPipe`
3. `ParseBoolPipe`
4. `ParseUUIDPipe`
5. `DefaultValuePipe`
6. `ParseArrayPipe`

#### Exemples d’utilisation

Niveau paramètre :

```ts
@Get(':id')
findOne(@Param('id', ParseIntPipe) id: number) {
  return this.usersService.findOne(id);
}
```

Validation globale :

```ts
app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
    forbidNonWhitelisted: true,
    transform: true,
  }),
);
```

#### Exemple de Pipe personnalisé

```ts
import { BadRequestException, Injectable, PipeTransform } from '@nestjs/common';

@Injectable()
export class TrimToLowerPipe implements PipeTransform<string, string> {
  transform(value: string): string {
    if (typeof value !== 'string') {
      throw new BadRequestException('Expected string');
    }
    return value.trim().toLowerCase();
  }
}
```

#### Quand utiliser les Pipes

1. Valider les DTO de requête et les payloads query/param.
2. Parser les paramètres primitifs de route/query vers des valeurs typées.
3. Centraliser les règles de normalisation d’entrée.
4. Garder controllers/services sans code répétitif de validation/parsing.

#### Règle pratique

Utilisez les Pipes pour la **correction des entrées**, les Guards pour le
**contrôle d’accès**, les Interceptors pour l’**enveloppement d’exécution**, et
le Middleware pour le **prétraitement de requête bas niveau**.

</details>

<details>
<summary>31. Qu’est-ce qu’un DTO ?</summary>

#### NestJS

Un DTO (Data Transfer Object) est une forme d’objet utilisée pour transférer des
données entre des frontières applicatives, le plus souvent entre le client et
votre couche API.

Dans NestJS, les DTO sont généralement implémentés en **classes** pour
supporter la validation et la transformation à l’exécution avec
`class-validator` et `class-transformer`.

#### Pourquoi les DTO sont importants

1. **Contrats API explicites**
   Définissent exactement quels champs d’entrée/sortie sont autorisés.

2. **Frontière de validation**
   Rejettent les payloads mal formés ou dangereux avant l’exécution de la
   logique métier.

3. **Découplage**
   Évitent l’exposition directe des entités domaine/modèles ORM aux clients
   externes.

4. **Maintenabilité**
   Des schémas de requête/réponse clairs rendent le refactoring plus sûr et la
   documentation plus simple.

#### Types de DTO typiques dans NestJS

1. **DTO de requête**
   `CreateUserDto`, `UpdateUserDto`, DTO de query/filter.

2. **DTO de réponse/vue**
   Forme de sortie contrôlée (masquer les champs internes comme mots de passe,
   tokens, flags).

3. **DTO de type commande**
   Entrées pour des use cases spécifiques (surtout dans les modules de style
   CQRS).

#### Exemple de DTO de requête

```ts
import { IsEmail, IsString, MinLength } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;

  @IsString()
  @MinLength(8)
  password: string;
}
```

Utilisation dans un controller :

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Règles pratiques

1. N’utilisez jamais de payload `any` brut dans les controllers.
2. Gardez les DTO orientés transport (pas des entités domaine complètes).
3. Séparez les DTO d’entrée des DTO de sortie.
4. Combinez les DTO avec un `ValidationPipe` global pour une application
   cohérente des règles.

</details>

<details>
<summary>32. Quelle est la différence entre interface et classe pour typer les DTO — et pourquoi la classe est-elle préférée dans NestJS ?</summary>

#### NestJS

Les interfaces et les classes peuvent toutes deux décrire des formes TypeScript,
mais dans NestJS les DTO sont généralement implémentés en **classes**, car la
validation/transformation Nest fonctionne à l’exécution, pas seulement à la
compilation.

#### Différence clé

1. **Interface**
   Existe uniquement au moment de la compilation TypeScript ; supprimée à
   l’exécution.

2. **Classe**
   Existe à l’exécution comme véritable objet constructeur/fonction ; peut porter
   les métadonnées de décorateurs utilisées par les pipes et l’outillage Nest.

#### Pourquoi la classe est préférée pour les DTO dans NestJS

1. **Support de validation runtime**
   Les décorateurs `class-validator` (`@IsEmail`, `@IsString`, etc.) sont
   attachés aux propriétés de classe et utilisés par `ValidationPipe`.

2. **Support de transformation**
   `class-transformer` peut instancier/transformer des payloads bruts en
   instances de classe (`transform: true` dans `ValidationPipe`).

3. **Intégration OpenAPI/Swagger**
   Les classes DTO fournissent les métadonnées pour la génération de schémas
   `@nestjs/swagger`.

4. **Support des mapped types**
   `PartialType`, `PickType`, `OmitType`, `IntersectionType` opèrent sur des
   classes.

#### Exemple pratique

Interface (type-only, pas de métadonnées runtime) :

```ts
interface CreateUserDto {
  email: string;
}
```

Classe DTO (runtime + décorateurs) :

```ts
import { IsEmail } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;
}
```

Avec validation globale :

```ts
app.useGlobalPipes(new ValidationPipe({ whitelist: true, transform: true }));
```

Seul le DTO basé sur une classe peut être validé/transformé via les métadonnées
de décorateurs.

#### Quand les interfaces restent utiles

1. Contrats internes de service qui ne nécessitent pas de réflexion runtime.
2. Typage utilitaire générique et abstractions de domaine.
3. Frontières compile-time en lecture seule, quand la validation est gérée
   ailleurs.

#### Règle pratique

Utilisez des **classes pour les DTO d’API externes** (contrats d’entrée/sortie
controller). Utilisez des interfaces pour les contrats internes compile-time
quand les métadonnées runtime ne sont pas nécessaires.

</details>

<details>
<summary>33. Que sont les mapped types dans NestJS ? (`PartialType`, `OmitType`, `PickType`, `IntersectionType`)</summary>

#### NestJS

Les mapped types dans NestJS sont des utilitaires qui génèrent de nouvelles
classes DTO à partir de DTO existants, afin de réduire la duplication tout en
préservant les métadonnées de validation/Swagger.

Ils sont généralement importés depuis :
1. `@nestjs/mapped-types` (usage agnostique du framework)
2. `@nestjs/swagger` (quand Swagger et les décorateurs de schéma sont utilisés)

#### Pourquoi les mapped types sont utiles

1. Évitent les définitions DTO répétitives.
2. Gardent les DTO create/update cohérents.
3. Préservent les métadonnées de décorateurs pour validation/docs.
4. Rendent l’évolution des contrats API plus sûre.

#### Principaux mapped types

1. **`PartialType(BaseDto)`**
   Rend toutes les propriétés optionnelles.
   Usage typique : `UpdateDto` à partir de `CreateDto`.

2. **`PickType(BaseDto, ['a', 'b'])`**
   Conserve uniquement les propriétés sélectionnées.
   Usage typique : entrée allégée pour un endpoint ciblé.

3. **`OmitType(BaseDto, ['x'])`**
   Exclut certaines propriétés.
   Usage typique : masquer des champs d’entrée interdits comme `role`, `id`.

4. **`IntersectionType(A, B)`**
   Combine les propriétés de deux classes DTO.
   Usage typique : DTO composés de filter/pagination/query.

#### Exemple

```ts
import { IsEmail, IsOptional, IsString, MinLength } from 'class-validator';
import { OmitType, PartialType, PickType, IntersectionType } from '@nestjs/mapped-types';

export class CreateUserDto {
  @IsEmail()
  email: string;

  @IsString()
  @MinLength(8)
  password: string;

  @IsString()
  role: string;
}

export class UpdateUserDto extends PartialType(CreateUserDto) {}

export class PublicUserInputDto extends OmitType(CreateUserDto, ['role'] as const) {}

export class CredentialsDto extends PickType(CreateUserDto, ['email', 'password'] as const) {}

class PaginationDto {
  @IsOptional()
  page?: number;
}

class SearchDto {
  @IsOptional()
  @IsString()
  q?: string;
}

export class UserQueryDto extends IntersectionType(PaginationDto, SearchDto) {}
```

#### Précautions pratiques

1. Les mapped types opèrent sur les métadonnées de classe ; le DTO de base doit
   être une classe.
2. Gardez l’héritage DTO lisible ; évitez les chaînes profondes et confuses.
3. Revoyez le schéma OpenAPI généré après des intersections complexes.

#### Règle pratique

Utilisez les mapped types pour la réutilisation des contrats, surtout pour le
flux `Create` -> `Update`, tout en gardant une hiérarchie DTO simple et
explicite.

</details>

<details>
<summary>34. Comment implémenter la validation avec `class-validator` et les pipes ?</summary>

#### NestJS

Dans NestJS, la validation est généralement implémentée avec :
1. Des classes DTO annotées avec des décorateurs `class-validator`.
2. `ValidationPipe` (global ou au niveau route) pour appliquer les règles à
   l’exécution.

#### Étape 1 : définir un DTO avec des décorateurs de validation

```ts
import { IsEmail, IsInt, IsOptional, IsString, Max, Min, MinLength } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;

  @IsString()
  @MinLength(8)
  password: string;

  @IsOptional()
  @IsInt()
  @Min(18)
  @Max(120)
  age?: number;
}
```

#### Étape 2 : activer `ValidationPipe`

Configuration globale (recommandée) :

```ts
import { ValidationPipe } from '@nestjs/common';

app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
    forbidNonWhitelisted: true,
    transform: true,
    transformOptions: { enableImplicitConversion: true },
  }),
);
```

#### Ce que font ces options

1. `whitelist: true`
   Supprime les propriétés non définies dans le DTO.

2. `forbidNonWhitelisted: true`
   Lève une erreur quand des propriétés inconnues sont présentes.

3. `transform: true`
   Convertit le payload en instance DTO et applique la transformation de type.

4. `enableImplicitConversion: true`
   Autorise une conversion sûre des types primitifs selon les types de
   propriétés du DTO.

#### Étape 3 : utiliser le DTO dans le controller

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Validation au niveau route (si nécessaire)

```ts
@Post('strict')
@UsePipes(new ValidationPipe({ whitelist: true, forbidNonWhitelisted: true }))
createStrict(@Body() dto: CreateUserDto) {}
```

#### Réponse d’erreur de validation typique

1. HTTP `400 Bad Request`
2. Tableau de messages avec les contraintes échouées
3. Diagnostics clairs au niveau champ pour les développeurs client

#### Bonnes pratiques

1. Garder les DTO ciblés par endpoint/use case.
2. Séparer les DTO Create/Update (souvent via `PartialType`).
3. Ne pas compter uniquement sur la validation dans les services si les
   controllers acceptent des données externes.
4. Personnaliser `exceptionFactory` de `ValidationPipe` pour une forme d’erreur
   API cohérente.

</details>

<details>
<summary>35. Comment implémenter un Exception Filter global et des erreurs HTTP personnalisées ?</summary>

#### NestJS

Dans NestJS, un Exception Filter global centralise le mapping erreur -> réponse,
afin que toutes les exceptions non gérées produisent un format API cohérent.

Les erreurs HTTP personnalisées sont généralement créées en étendant
`HttpException` ou en utilisant les exceptions intégrées
(`BadRequestException`, `NotFoundException`, etc.).

#### 1) Créer un exception filter global

```ts
import {
  ArgumentsHost,
  Catch,
  ExceptionFilter,
  HttpException,
  HttpStatus,
} from '@nestjs/common';
import { Request, Response } from 'express';

@Catch()
export class GlobalExceptionFilter implements ExceptionFilter {
  catch(exception: unknown, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const res = ctx.getResponse<Response>();
    const req = ctx.getRequest<Request>();

    const isHttp = exception instanceof HttpException;
    const status = isHttp
      ? exception.getStatus()
      : HttpStatus.INTERNAL_SERVER_ERROR;

    const raw = isHttp ? exception.getResponse() : 'Internal server error';
    const message =
      typeof raw === 'string'
        ? raw
        : (raw as any).message ?? 'Unexpected error';

    res.status(status).json({
      success: false,
      statusCode: status,
      timestamp: new Date().toISOString(),
      path: req.url,
      message,
    });
  }
}
```

#### 2) Enregistrer le filter globalement

Dans `main.ts` :

```ts
app.useGlobalFilters(new GlobalExceptionFilter());
```

#### 3) Créer une exception HTTP personnalisée

```ts
import { HttpException, HttpStatus } from '@nestjs/common';

export class BusinessRuleViolationException extends HttpException {
  constructor(message: string, code = 'BUSINESS_RULE_VIOLATION') {
    super(
      {
        message,
        code,
      },
      HttpStatus.UNPROCESSABLE_ENTITY,
    );
  }
}
```

Utilisation :

```ts
if (!canCloseOrder) {
  throw new BusinessRuleViolationException('Order cannot be closed in current state');
}
```

#### Pourquoi cette approche est bonne

1. Format de réponse cohérent sur toute l’API.
2. Controllers/services plus propres (pas de try/catch répétitifs pour formatter).
3. Hooks d’observability centralisés (logging, correlation IDs, codes d’erreur).
4. Mapping facile des erreurs domaine/infrastructure vers des sémantiques HTTP pertinentes.

#### Bonnes pratiques

1. Évitez d’exposer des stack traces internes dans les réponses de production.
2. Incluez des codes d’erreur lisibles par machine pour les clients.
3. Conservez les stack traces dans les logs (pas forcément dans le body HTTP).
4. Mappez les erreurs métier attendues en 4xx ; les échecs inattendus en 5xx.

</details>

<details>
<summary>36. Comment bien gérer les erreurs et renvoyer une structure de réponse cohérente ?</summary>

#### NestJS

Une bonne gestion des erreurs dans NestJS consiste à séparer :
1. où les erreurs sont créées (domaine/application/infrastructure),
2. où elles sont traduites en HTTP (filters),
3. et comment les réponses sont standardisées (contrat global).

#### Stratégie recommandée

1. **Lever des exceptions significatives dans le flux métier**
   Utiliser des exceptions spécifiques au domaine ou des sous-classes
   appropriées de `HttpException`.

2. **Centraliser le formatage des réponses HTTP**
   Utiliser un exception filter global pour imposer un schéma d’erreur unique.

3. **Standardiser aussi les réponses de succès**
   Optionnellement, utiliser un interceptor pour une enveloppe de succès
   uniforme.

4. **Préserver l’observability**
   Logger le contexte d’erreur (requestId, path, userId, stack) à un seul
   endroit.

#### Exemple de forme de réponse d’erreur cohérente

```json
{
  "success": false,
  "statusCode": 403,
  "code": "INSUFFICIENT_PERMISSIONS",
  "message": "You do not have access to this resource",
  "timestamp": "2026-04-30T12:00:00.000Z",
  "path": "/api/users/42"
}
```

#### Composants d’implémentation

1. **Global Exception Filter**
   Mappe toutes les exceptions vers la même structure de réponse.

2. **Classes d’exception personnalisées**
   Encapsulent code/message/statut d’erreur domaine/métier.

3. **Response interceptor optionnel**
   Enveloppe les réponses réussies :
   `{ success: true, data, meta }`.

#### Guide de catégorisation des erreurs

1. **Erreurs de validation/saisie client** -> `400`.
2. **Erreurs d’authentification** -> `401`.
3. **Erreurs d’autorisation** -> `403`.
4. **Ressources manquantes** -> `404`.
5. **Conflits de règle métier** -> `409` ou `422`.
6. **Pannes système inattendues** -> `500`.

#### Ce qu’il faut éviter

1. Renvoyer des formats d’erreur ad hoc selon les controllers.
2. Avaler les exceptions et renvoyer `200` avec `"error"` dans le body.
3. Exposer stack traces internes/erreurs SQL dans les réponses de production.
4. Mélanger la logique de formatage transport directement dans les services.

#### Bonnes pratiques concrètes

1. Définir un catalogue de codes d’erreur (`USER_NOT_FOUND`, `TOKEN_EXPIRED`, etc.).
2. Ajouter un correlation/request ID à chaque réponse d’erreur et entrée de log.
3. S’assurer que le filter global gère les erreurs connues (`HttpException`) et
   inconnues.
4. Couvrir les chemins d’erreur avec des tests e2e pour figer le contrat d’erreur API.

</details>

<details>
<summary>37. Comment logger correctement les erreurs sans perdre la stack trace en production ?</summary>

#### NestJS

Pour logger correctement les erreurs en production, vous avez besoin de deux
sorties parallèles :
1. **réponse client sûre** (sans informations internes sensibles),
2. **log serveur structuré complet** (incluant stack trace et contexte).

#### Principe central

Ne jamais exposer les stack traces aux clients API, mais toujours les conserver
dans les logs pour le debugging et la réponse à incident.

#### Approche recommandée dans NestJS

1. Capturer les erreurs de manière centralisée dans un exception filter global.
2. Logger avec un logger structuré (Pino/Winston/adaptateur Nest Logger).
3. Inclure stack, code d’erreur, métadonnées de requête, correlation ID et
   contexte utilisateur.
4. Retourner un payload d’erreur assaini depuis le filter.

#### Exemple (global filter qui log la stack)

```ts
import {
  ArgumentsHost,
  Catch,
  ExceptionFilter,
  HttpException,
  HttpStatus,
  Inject,
} from '@nestjs/common';
import { Request, Response } from 'express';

@Catch()
export class GlobalExceptionFilter implements ExceptionFilter {
  constructor(@Inject('LOGGER') private readonly logger: any) {}

  catch(exception: unknown, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const req = ctx.getRequest<Request>();
    const res = ctx.getResponse<Response>();

    const status =
      exception instanceof HttpException
        ? exception.getStatus()
        : HttpStatus.INTERNAL_SERVER_ERROR;

    const message =
      exception instanceof HttpException
        ? exception.message
        : 'Internal server error';

    const err = exception as Error;

    this.logger.error({
      msg: 'Unhandled exception',
      statusCode: status,
      path: req.url,
      method: req.method,
      requestId: (req as any).requestId,
      userId: (req as any).user?.id,
      errorName: err?.name,
      errorMessage: err?.message,
      stack: err?.stack, // conserver la stack complète dans les logs
    });

    res.status(status).json({
      success: false,
      statusCode: status,
      message,
      requestId: (req as any).requestId,
    });
  }
}
```

#### Que logger pour un diagnostic production-grade

1. Timestamp, niveau, nom du service, environnement.
2. Request ID / trace ID.
3. Route, méthode, status code, latence.
4. Contexte auth (userId/tenantId quand disponible).
5. Stack complète + chaîne de causes racines.

#### Erreurs fréquentes

1. Logger uniquement `error.message` (perte de stack et de chaîne de causes).
2. Logs concaténés en string au lieu de logs JSON structurés.
3. Logging dupliqué à plusieurs couches (bruit).
4. Retourner des objets d’exception bruts aux clients.

#### Bonnes pratiques concrètes

1. Utiliser un logger structuré unique sur toute l’application.
2. Ajouter un middleware/interceptor de correlation ID tôt dans le cycle de requête.
3. Redacter les secrets/PII avant émission des logs.
4. Envoyer les logs vers une stack d’observability centralisée
   (ELK, Datadog, Grafana Loki).
5. Tester les chemins d’erreur pour vérifier que la stack est bien conservée
   dans les logs après déploiement.

</details>

<details>
<summary>38. Qu’est-ce que ConfigModule et pourquoi l’utiliser à la place de `process.env` ?</summary>

#### NestJS

`ConfigModule` est le système de configuration de NestJS (`@nestjs/config`) qui
charge, valide et fournit les valeurs d’environnement/configuration via la DI.

Utiliser `ConfigModule` est préférable à l’accès direct à `process.env`, car il
centralise la logique de config, améliore la sûreté de typage et rend les tests/
la maintenance beaucoup plus propres.

#### Pourquoi `process.env` seul ne suffit pas

1. Lectures d’environnement dispersées dans toute la base de code.
2. Pas de validation centralisée des variables requises.
3. Valeurs uniquement en string sans parsing typé.
4. Tests/mocks plus difficiles et découverte des variables moins bonne.

#### Ce que `ConfigModule` apporte

1. **Chargement de config centralisé**
   Un seul endroit pour définir les fichiers env et les config factories.

2. **Validation au démarrage**
   Échec immédiat si des variables requises sont absentes/invalides.

3. **Accès typé via `ConfigService`**
   Meilleurs contrats et moins de surprises runtime.

4. **Intégration DI**
   Tout provider peut injecter la config proprement.

5. **Composition spécifique à l’environnement**
   Découpage facile dev/staging/prod.

#### Setup de base

```ts
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';

@Module({
  imports: [
    ConfigModule.forRoot({
      isGlobal: true,
      envFilePath: ['.env.local', '.env'],
      cache: true,
    }),
  ],
})
export class AppModule {}
```

Utilisation :

```ts
import { Injectable } from '@nestjs/common';
import { ConfigService } from '@nestjs/config';

@Injectable()
export class JwtConfigService {
  constructor(private readonly config: ConfigService) {}

  get accessSecret(): string {
    return this.config.getOrThrow<string>('JWT_ACCESS_SECRET');
  }
}
```

#### Exemple de validation (recommandé)

Utilisez `validationSchema` (Joi) ou une fonction de validation personnalisée :
1. Exiger les variables obligatoires.
2. Valider formats/plages.
3. Bloquer le bootstrap de l’app si la config est invalide.

#### Recommandation pratique

Utilisez `process.env` uniquement dans les config factories/les frontières de
bootstrap. Partout ailleurs, consommez la config via `ConfigService` ou des
providers de config typés pour assurer cohérence, testabilité et comportement
plus sûr en production.

</details>

<details>
<summary>39. Comment organiser correctement les fichiers `.env` pour différents environnements (dev, staging, prod) ?</summary>

#### NestJS

Une bonne organisation des fichiers `.env` doit fournir une configuration
prévisible par environnement, éviter les fuites de secrets et garder le
développement local pratique.

#### Stratégie d’environnement recommandée

1. Garder un fichier **de base** pour les valeurs par défaut partagées.
2. Ajouter des fichiers **spécifiques à l’environnement** pour les overrides.
3. Garder les secrets hors git et les injecter via la plateforme de déploiement/
   le secret store.

Layout typique :
1. `.env` (valeurs locales partagées)
2. `.env.development`
3. `.env.staging`
4. `.env.production`
5. `.env.test`
6. `.env.local` (overrides machine développeur, ignoré par git)

#### Avec `ConfigModule` de NestJS

```ts
ConfigModule.forRoot({
  isGlobal: true,
  envFilePath: [
    `.env.${process.env.NODE_ENV ?? 'development'}`,
    '.env',
  ],
  cache: true,
});
```

L’ordre de chargement est important : les fichiers lus en premier ont
généralement la priorité dans ce pattern.

#### Ce qui doit être commit vs ignoré

1. Commit :
   1. `.env.example` (documenter toutes les clés requises sans vrais secrets)
   2. Valeurs par défaut non sensibles si votre politique l’autorise

2. Ne pas commit :
   1. Vrais secrets/tokens/clés privées
   2. `.env.local` et overrides spécifiques machine

#### Validation et fail-fast

Validez toujours la config au démarrage (Joi ou validateur custom) :
1. Les clés requises existent.
2. Les types/plages sont valides (`PORT`, timeouts, feature flags).
3. Le format des URLs et des credentials est correct.

#### Bonnes pratiques production/staging

1. Préférez les secret managers de plateforme
   (AWS SSM/Secrets Manager, Vault, Doppler, etc.) aux fichiers plats.
2. Faites tourner les secrets régulièrement.
3. Séparez strictement les credentials staging/prod.
4. Gardez `NODE_ENV` explicite dans la configuration de déploiement.
5. N’intégrez jamais les secrets dans les images Docker/le code source.

#### Workflow d’équipe pratique

1. Maintenir `.env.example` comme contrat.
2. Ajouter un script/check d’onboarding qui vérifie les variables env manquantes.
3. Utiliser des wrappers de config typés pour que le code app ne lise jamais des
   clés env aléatoires directement.
4. Documenter l’ownership des variables critiques (DB, JWT, API externes).

</details>

<details>
<summary>40. Comment utiliser Joi ou Zod pour valider la configuration au démarrage de l’application ?</summary>

#### NestJS

Validez la configuration au démarrage pour que l’application échoue immédiatement
si des variables d’environnement sont manquantes ou invalides, au lieu de planter
plus tard à l’exécution.

Dans NestJS, cela se fait généralement avec `ConfigModule.forRoot(...)` et soit :
1. `validationSchema` (Joi), soit
2. une fonction `validate` (logique personnalisée, souvent avec Zod).

#### Option A : Joi avec `validationSchema`

```ts
import * as Joi from 'joi';
import { ConfigModule } from '@nestjs/config';

ConfigModule.forRoot({
  isGlobal: true,
  validationSchema: Joi.object({
    NODE_ENV: Joi.string().valid('development', 'test', 'staging', 'production').required(),
    PORT: Joi.number().port().default(3000),
    DATABASE_URL: Joi.string().uri().required(),
    JWT_ACCESS_SECRET: Joi.string().min(32).required(),
  }),
});
```

Fonctionnement :
1. Les variables d’environnement sont chargées.
2. Joi valide la structure et les contraintes.
3. Le bootstrap de l’application échoue immédiatement si la configuration est invalide.

#### Option B : Zod avec fonction `validate`

```ts
import { z } from 'zod';
import { ConfigModule } from '@nestjs/config';

const envSchema = z.object({
  NODE_ENV: z.enum(['development', 'test', 'staging', 'production']),
  PORT: z.coerce.number().int().positive().default(3000),
  DATABASE_URL: z.string().url(),
  JWT_ACCESS_SECRET: z.string().min(32),
});

ConfigModule.forRoot({
  isGlobal: true,
  validate: (config: Record<string, unknown>) => envSchema.parse(config),
});
```

Pourquoi les équipes apprécient Zod :
1. Inférence TypeScript solide à partir du schéma.
2. Schémas composables pour une config modulaire.
3. Erreurs de parsing claires et support des transformations.

#### Bonnes pratiques

1. Valider tous les secrets/URL/ports requis au démarrage.
2. Convertir explicitement les types primitifs (`PORT`, booléens, timeouts).
3. Garder un schéma unique comme source de vérité.
4. Exposer une config typée via des wrappers/services, pas via `process.env` brut.
5. Utiliser des fichiers d’environnement par contexte, mais un contrat de validation unique.

#### Joi vs Zod en bref

1. **Joi** : mature, simple à intégrer avec `validationSchema`.
2. **Zod** : orienté TypeScript et composable ; excellent pour des pipelines de config typés.

Les deux sont valides en production ; choisissez-en un et appliquez-le de manière cohérente.

</details>

<details>
<summary>41. Comment implémenter des feature flags dans NestJS ?</summary>

#### NestJS

Dans NestJS, les feature flags sont généralement implémentés via un service dédié
qui évalue si une fonctionnalité est activée pour un contexte donné (environnement,
utilisateur, tenant, pourcentage de déploiement, etc.).

#### Pourquoi les feature flags sont importants

1. Déploiement progressif et sûr.
2. Kill-switch rapide pour les fonctionnalités problématiques.
3. Expérimentation A/B.
4. Découplage entre déploiement et mise en production réelle.

#### Architecture courante

1. **FeatureFlagService**
   Point d’entrée unique : `isEnabled(flag, context)`.

2. **Source des flags**
   Configuration d’environnement, table DB ou fournisseur externe.

3. **Contexte d’évaluation**
   ID utilisateur, ID tenant, plan, région, version de l’app, métadonnées de requête.

4. **Points d’usage**
   Guards, services, contrôleurs, intercepteurs, adaptation de la réponse UI.

#### Implémentation simple dans l’app (basée sur config)

```ts
import { Injectable } from '@nestjs/common';
import { ConfigService } from '@nestjs/config';

type FlagContext = { userId?: string; tenantId?: string };

@Injectable()
export class FeatureFlagService {
  constructor(private readonly config: ConfigService) {}

  isEnabled(flag: string, _ctx?: FlagContext): boolean {
    return this.config.get<string>(`FEATURE_${flag.toUpperCase()}`) === 'true';
  }
}
```

Utilisation dans un service :

```ts
if (this.flags.isEnabled('new_checkout', { userId, tenantId })) {
  return this.newCheckoutFlow();
}
return this.legacyCheckoutFlow();
```

#### Contrôle au niveau route via Guard (optionnel)

1. Créer un décorateur de métadonnées `@Feature('new_checkout')`.
2. Le Guard lit les métadonnées via `Reflector`.
3. Le Guard appelle `FeatureFlagService.isEnabled(...)`.
4. Refuser ou rediriger le comportement si la feature est désactivée.

#### Pratiques prêtes pour la production

1. Prendre en charge des stratégies de rollout :
   1. Activation/désactivation globale
   2. Déploiement en pourcentage
   3. Allowlists utilisateur/tenant
   4. Activation sur plage temporelle

2. Ajouter un cache local avec TTL pour les fournisseurs externes.
3. Garder des valeurs par défaut explicites (fail-closed vs fail-open selon le flag).
4. Journaliser les décisions de flags pour faciliter le débogage.
5. Supprimer rapidement les flags obsolètes pour limiter la complexité.

#### Build vs buy

1. Construire en interne pour des besoins simples et une faible charge opérationnelle.
2. Utiliser des solutions gérées (LaunchDarkly, Unleash, ConfigCat, etc.) pour le ciblage avancé, l’analytique et la gouvernance.

#### Règle pratique

Traitez les flags comme des contrôles de release à durée de vie courte,
pas comme des branches permanentes de logique métier. Définissez un responsable
et une date de suppression pour chaque flag.

</details>

<details>
<summary>42. Comment intégrer des bases de données ? (TypeORM, Prisma, Drizzle, Mongoose)</summary>

#### NestJS

Dans NestJS, l’intégration de la base de données doit passer par des modules/providers
infrastructure dédiés, et non directement par les contrôleurs. Le choix dépend du
modèle de données, des préférences de l’équipe et de la complexité des requêtes.

#### Options courantes

1. **TypeORM**
   ORM complet avec décorateurs, repositories, migrations et forte intégration
   aux modules Nest.

2. **Prisma**
   ORM/client schema-first avec excellente DX, requêtes typées et migrations
   prévisibles.

3. **Drizzle**
   Toolkit SQL typé/ORM léger avec une approche explicite orientée SQL.

4. **Mongoose**
   ODM pour MongoDB avec modélisation de schémas et workflows orientés documents.

#### Patterns d’intégration par outil

1. **TypeORM**
   Utiliser `TypeOrmModule.forRoot(...)` dans le module racine, `forFeature([Entity])`
   dans les modules métier, injecter les repositories via `@InjectRepository`.

2. **Prisma**
   Créer un `PrismaService` (hérite de `PrismaClient`) et le fournir dans un module.
   Injecter ce service dans les repositories/services applicatifs.

3. **Drizzle**
   Créer un provider DB (`drizzle(...)`) avec pool de connexions (`pg`, `mysql2`).
   Injecter l’instance DB typée via un token personnalisé.

4. **Mongoose**
   Utiliser `MongooseModule.forRoot(...)` + `forFeature([{ name, schema }])`,
   injecter le modèle via `@InjectModel`.

#### Exemples minimaux

TypeORM :

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

Service Prisma :

```ts
@Injectable()
export class PrismaService extends PrismaClient implements OnModuleInit {
  async onModuleInit() {
    await this.$connect();
  }
}
```

Mongoose :

```ts
MongooseModule.forRoot(process.env.MONGO_URI!);
```

#### Guide de décision

1. Choisir **TypeORM** si vous voulez le style Nest classique avec décorateurs/repositories.
2. Choisir **Prisma** pour un client fortement typé et un workflow moderne de migrations.
3. Choisir **Drizzle** si vous préférez une approche SQL-first explicite avec sûreté de types.
4. Choisir **Mongoose** quand le modèle document MongoDB est le plus adapté.

#### Bonnes pratiques production (quel que soit l’outil)

1. Garder l’accès DB dans des repositories/adapters, pas dans les contrôleurs.
2. Utiliser des migrations ; éviter l’auto-sync de schéma en production.
3. Configurer pooling de connexions et timeouts.
4. Ajouter health checks et fail-fast au démarrage.
5. Instrumenter la latence des requêtes et les taux d’erreur.
6. Encapsuler les transactions au niveau des frontières de services applicatifs.

</details>

<details>
<summary>43. Quelle est la différence entre TypeOrmModule.forRoot() et forFeature() ?</summary>

#### NestJS

`TypeOrmModule.forRoot()` et `TypeOrmModule.forFeature()` servent des portées
différentes dans l’intégration TypeORM de NestJS.

#### `forRoot()` — configuration de la connexion DB au niveau application

À utiliser dans le module racine (généralement `AppModule`) pour configurer
la DataSource/connexion.

Il définit :
1. Le driver/type DB (`postgres`, `mysql`, etc.)
2. Les identifiants de connexion / l’URL
3. Les options globales TypeORM (chargement des entités, logs, migrations, `synchronize`)

Exemple :

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

#### `forFeature()` — enregistrement des repositories dans un module métier

À utiliser dans les modules domaine/feature pour enregistrer des entités précises
et rendre leurs repositories injectables dans ce contexte de module.

Exemple :

```ts
@Module({
  imports: [TypeOrmModule.forFeature([UserEntity])],
  providers: [UsersService],
})
export class UsersModule {}
```

Injection du repository :

```ts
constructor(
  @InjectRepository(UserEntity)
  private readonly usersRepo: Repository<UserEntity>,
) {}
```

#### Résumé pratique de la différence

1. `forRoot()`:
   1. Crée/configure la connexion DB une seule fois (ou des connexions nommées).
   2. Préoccupation d’infrastructure globale.

2. `forFeature()`:
   1. Expose les repositories des entités sélectionnées dans la portée du module.
   2. Préoccupation métier/feature.

#### Erreur fréquente

Utiliser `forFeature()` sans `forRoot()` (ou sans DataSource initialisée)
provoque des erreurs DI/runtime, car les repositories n’ont aucune connexion active.

#### Règle pratique

1. Configurer la connexion une seule fois avec `forRoot` sur le chemin de bootstrap.
2. Enregistrer les entités par module avec `forFeature` là où les repositories sont nécessaires.
3. Garder `synchronize: false` en production et utiliser des migrations.

</details>

<details>
<summary>44. Qu’est-ce que le pattern Repository dans NestJS + TypeORM ?</summary>

#### NestJS

Le pattern Repository abstrait l’accès aux données derrière une interface/service
dédié, afin que la logique métier ne dépende pas directement des détails de l’ORM.

Dans NestJS + TypeORM, cela signifie généralement envelopper `Repository<Entity>`
dans votre propre contrat repository orienté domaine, avec son implémentation.

#### Pourquoi utiliser le pattern Repository

1. Découple la logique applicative/domaine de l’API TypeORM.
2. Améliore la testabilité (mock facile des interfaces de repository).
3. Centralise la logique de requêtes et de mapping.
4. Rend le remplacement/refactor de l’ORM moins douloureux.

#### Structure typique

1. **Contrat domaine (port)**
   Interface `UsersRepository` avec des méthodes orientées métier.

2. **Implémentation infrastructure**
   `TypeOrmUsersRepository` qui utilise `Repository<UserEntity>`.

3. **Couche service/application**
   Dépend d’un token d’interface, pas d’une classe TypeORM concrète.

#### Exemple

Contrat repository :

```ts
export interface UsersRepository {
  findByEmail(email: string): Promise<UserEntity | null>;
  save(user: UserEntity): Promise<UserEntity>;
}
```

Implémentation TypeORM :

```ts
@Injectable()
export class TypeOrmUsersRepository implements UsersRepository {
  constructor(
    @InjectRepository(UserEntity)
    private readonly repo: Repository<UserEntity>,
  ) {}

  findByEmail(email: string) {
    return this.repo.findOne({ where: { email } });
  }

  save(user: UserEntity) {
    return this.repo.save(user);
  }
}
```

Binding provider :

```ts
{
  provide: 'USERS_REPOSITORY',
  useClass: TypeOrmUsersRepository,
}
```

Le service dépend de l’abstraction :

```ts
constructor(
  @Inject('USERS_REPOSITORY')
  private readonly usersRepo: UsersRepository,
) {}
```

#### Ce qui relève du repository vs du service

1. Repository :
   requêtes de persistance, chargement/sauvegarde d’agrégats, filtrage spécifique DB.

2. Service/use-case :
   orchestration, règles métier, coordination des frontières transactionnelles.

#### Anti-pattern courant

Injecter directement les repositories TypeORM dans de nombreux services/contrôleurs
et dupliquer partout des fragments de requêtes. Cela augmente le couplage
et l’incohérence.

#### Conclusion pratique

Utilisez le repository TypeORM en interne, mais exposez votre propre interface
repository au niveau domaine pour garder une architecture modulaire et testable.

</details>

<details>
<summary>45. Quelle est la différence entre le pattern Repository et Active Record, et quand choisir chacun ?</summary>

#### NestJS

Le pattern Repository et Active Record sont deux approches différentes pour
organiser la logique de persistance.

#### Différence centrale

1. **Pattern Repository**
   La couche domaine/métier travaille avec des abstractions de repository ;
   la logique de persistance est séparée dans des classes dédiées.

2. **Active Record**
   Les objets entité/modèle contiennent eux-mêmes les méthodes de persistance
   (`save`, `remove`, finders statiques), mélangeant données + comportement de persistance.

#### Caractéristiques du pattern Repository

1. Meilleure séparation des responsabilités.
2. Tests unitaires plus simples via mocks d’interfaces.
3. Meilleure évolutivité pour des domaines complexes/microservices.
4. Favorise un design orienté domaine et des frontières claires.

#### Caractéristiques d’Active Record

1. Démarrage plus rapide pour des applis petites/simples.
2. Moins de boilerplate pour du CRUD direct.
3. Peut devenir fortement couplé à l’ORM avec le temps.
4. Plus difficile d’isoler la logique métier quand la complexité augmente.

#### Quand choisir chaque approche

1. Choisir **Repository pattern** quand :
   1. Le projet est moyen/grand ou voué à grandir.
   2. L’équipe a besoin d’une architecture stricte et testable.
   3. La logique domaine est non triviale.
   4. Le remplacement futur de l’ORM est une préoccupation possible.

2. Choisir **Active Record** quand :
   1. L’application est petite, orientée CRUD et peu complexe.
   2. La vitesse de développement initial est prioritaire.
   3. L’équipe accepte le compromis d’un couplage ORM plus fort.

#### En pratique dans NestJS

1. L’architecture NestJS (modules/providers/DI) s’aligne naturellement
   avec le pattern Repository.
2. Même avec TypeORM, beaucoup d’équipes production préfèrent un style
   Data Mapper/repository à Active Record pour garder des services propres.

#### Tableau comparatif rapide

1. **Couplage**
   Repository : plus faible
   Active Record : plus fort

2. **Testabilité**
   Repository : élevée
   Active Record : moyenne/faible (plus couplé à la DB)

3. **Boilerplate**
   Repository : plus
   Active Record : moins

4. **Maintenabilité long terme**
   Repository : meilleure pour les systèmes complexes
   Active Record : acceptable pour des applis simples

#### Recommandation pratique

Pour une architecture NestJS de niveau entretien/production, privilégiez par
défaut le pattern Repository. Utilisez Active Record seulement si le domaine
est volontairement simple et le coût de cycle de vie faible.

</details>

<details>
<summary>46. Que sont les migrations dans TypeORM/Prisma et pourquoi `synchronize: true` est dangereux en production ?</summary>

#### NestJS

Les migrations sont des scripts versionnés et explicites de changement de schéma de
base de données. Elles permettent aux équipes de faire évoluer le schéma de manière
sûre et prévisible entre les environnements.

Dans TypeORM/Prisma, les migrations sont la méthode sûre pour appliquer des
changements de schéma en production.

#### Ce que sont les migrations

1. **Historique ordonné du schéma**
   Chaque migration est une étape suivie (up/down) de l’évolution du schéma.

2. **Déploiements reproductibles**
   Les mêmes changements de schéma s’exécutent de façon cohérente en dev/staging/prod.

3. **Lot de changements révisable**
   L’intention SQL/DDL est visible en code review et CI.

4. **Stratégie de rollback**
   Vous pouvez revenir sur des changements problématiques (avec contraintes).

#### Modèle de migration : TypeORM vs Prisma

1. **TypeORM**
   Les migrations sont des fichiers TS/JS (ou SQL), générés/écrits puis exécutés via CLI.

2. **Prisma**
   Les changements sont définis dans `schema.prisma` ; les fichiers de migration
   sont générés et appliqués avec Prisma Migrate.

Les deux approches créent des artefacts de migration auditables.

#### Pourquoi `synchronize: true` est dangereux en production

1. **Changements destructifs implicites**
   L’ORM peut modifier/supprimer automatiquement des colonnes/index sans revue contrôlée.

2. **Comportement non déterministe**
   Le diff de schéma peut varier selon la dérive des entités et l’état runtime.

3. **Absence d’historique de migration fiable**
   Difficile d’auditer quoi a changé et quand.

4. **Couplage risqué au démarrage**
   Le bootstrap de l’app peut muter le schéma production de manière inattendue.

5. **Faible sécurité multi-instances**
   Des démarrages concurrents peuvent entrer en course sur les mises à jour de schéma.

#### Workflow sûr pour la production

1. Mettre `synchronize: false` en production.
2. Générer une migration pour chaque changement de schéma.
3. Revoir le SQL de migration dans la PR.
4. Exécuter les migrations dans le pipeline de déploiement avant/avec le rollout app.
5. Monitorer l’exécution des migrations et faire échouer le déploiement en cas d’erreur.

#### Exemples pratiques

Configuration production TypeORM :

```ts
TypeOrmModule.forRoot({
  // ...
  synchronize: false,
  migrationsRun: false,
});
```

Approche de déploiement Prisma :
1. Commit les fichiers de migration.
2. Exécuter `prisma migrate deploy` pendant la release.

#### Règle pratique

Utilisez `synchronize: true` uniquement pour du prototypage local rapide.
Pour tout environnement sérieux, les migrations sont obligatoires pour la sécurité,
la traçabilité et une évolution contrôlée du schéma.

</details>

<details>
<summary>47. Comment implémenter le soft delete dans TypeORM ?</summary>

#### NestJS

Le soft delete signifie que les enregistrements sont marqués comme supprimés au
lieu d’être physiquement retirés de la base. Dans TypeORM, cela se fait
habituellement avec `@DeleteDateColumn`.

#### Pourquoi utiliser le soft delete

1. Récupérer des données supprimées par erreur.
2. Conserver le contexte d’audit/historique.
3. Préserver les relations de clés étrangères et la traçabilité métier.
4. Prendre en charge des workflows de type « corbeille/restauration ».

#### Étape 1 : Ajouter une colonne timestamp de suppression

```ts
import { Column, DeleteDateColumn, Entity, PrimaryGeneratedColumn } from 'typeorm';

@Entity('users')
export class UserEntity {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ unique: true })
  email: string;

  @DeleteDateColumn({ name: 'deleted_at', nullable: true })
  deletedAt?: Date | null;
}
```

#### Étape 2 : Utiliser les méthodes repository de soft delete

```ts
// marquer comme supprimé (renseigne deletedAt)
await this.usersRepo.softDelete(userId);

// restaurer la ligne soft-deletée
await this.usersRepo.restore(userId);
```

Vous pouvez aussi utiliser :
1. `softRemove(entity)` pour supprimer une instance d’entité.
2. `recover(entity)` pour restaurer une instance.

#### Comportement des requêtes

1. Par défaut, TypeORM exclut les lignes soft-deletées dans les requêtes `find*`.
2. Pour inclure les lignes supprimées, utilisez `withDeleted: true`.

```ts
const allRows = await this.usersRepo.find({ withDeleted: true });
```

Uniquement les lignes supprimées :

```ts
const deletedOnly = await this.usersRepo.find({
  withDeleted: true,
  where: { deletedAt: Not(IsNull()) },
});
```

#### Exemple au niveau service

```ts
async removeUser(id: number) {
  const result = await this.usersRepo.softDelete(id);
  if (!result.affected) throw new NotFoundException('User not found');
}

async restoreUser(id: number) {
  const result = await this.usersRepo.restore(id);
  if (!result.affected) throw new NotFoundException('User not found');
}
```

#### Considérations production

1. Ajouter des index sur les champs souvent filtrés (`deleted_at`, clés tenant).
2. Vérifier que les contraintes d’unicité tiennent compte des lignes soft-deletées
   (index uniques partiels si supportés).
3. Définir une politique de rétention pour un nettoyage hard delete ultérieur.
4. Inclure les événements de suppression/restauration dans les logs d’audit.

#### Règle pratique

Utilisez le soft delete pour les données utilisateur/métier qui peuvent nécessiter
récupération ou audit. Utilisez le hard delete seulement si des règles de
conformité, de stockage ou du domaine exigent une suppression permanente.

</details>

<details>
<summary>48. Comment implémenter des transactions dans TypeORM avec NestJS ?</summary>

#### NestJS

Les transactions garantissent qu’un groupe d’opérations de base de données réussit
en totalité ou est annulé en totalité. Dans NestJS + TypeORM, utilisez-les pour
les écritures en plusieurs étapes qui doivent rester cohérentes.

#### Quand les transactions sont nécessaires

1. Création/mise à jour de plusieurs tables liées dans un même use case.
2. Modifications de solde/argent/stock.
3. Opérations où un succès partiel corromprait l’état métier.

#### Principales approches dans TypeORM

1. **`DataSource.transaction(...)`** (recommandé par défaut)
2. **`QueryRunner`** (contrôle manuel pour des flux avancés)

#### Approche 1 : `DataSource.transaction` (propre et sûre)

```ts
import { Injectable } from '@nestjs/common';
import { DataSource } from 'typeorm';

@Injectable()
export class OrdersService {
  constructor(private readonly dataSource: DataSource) {}

  async createOrder(input: { userId: number; items: Array<{ sku: string; qty: number }> }) {
    return this.dataSource.transaction(async manager => {
      const order = manager.create(OrderEntity, { userId: input.userId });
      await manager.save(order);

      for (const item of input.items) {
        const row = manager.create(OrderItemEntity, {
          orderId: order.id,
          sku: item.sku,
          qty: item.qty,
        });
        await manager.save(row);
      }

      return order;
    });
  }
}
```

Important : dans le callback transactionnel, utilisez le `manager` transactionnel,
pas les repositories globaux injectés.

#### Approche 2 : `QueryRunner` (contrôle fin)

```ts
const qr = dataSource.createQueryRunner();
await qr.connect();
await qr.startTransaction();
try {
  // utiliser qr.manager pour toutes les requêtes
  await qr.manager.save(entityA);
  await qr.manager.save(entityB);
  await qr.commitTransaction();
} catch (e) {
  await qr.rollbackTransaction();
  throw e;
} finally {
  await qr.release();
}
```

#### Bonnes pratiques

1. Garder une portée transactionnelle courte et ciblée.
2. Éviter les appels HTTP externes dans une transaction DB.
3. Utiliser un niveau d’isolation approprié pour les flux sensibles à la concurrence.
4. Prévoir une stratégie deadlock/retry pour les opérations très contentionnées.
5. Émettre les événements domaine après commit réussi (ou utiliser l’outbox pattern).

#### Erreurs fréquentes

1. Mélanger repositories transactionnels et non transactionnels dans le même flux.
2. Transactions longues provoquant de la contention de verrous.
3. Avaler les erreurs et valider un état incohérent.

#### Règle pratique

Encapsulez un use case métier dans une seule frontière transactionnelle lorsque la
cohérence entre plusieurs écritures est non négociable.

</details>

<details>
<summary>49. Qu’est-ce que le problème N+1 et comment le résoudre dans NestJS ?</summary>

#### NestJS

Le problème N+1 se produit lorsque votre application exécute :
1. une requête pour charger une liste d’enregistrements parents,
2. puis une requête supplémentaire par parent pour charger les données liées.

Cela provoque `1 + N` requêtes, une latence élevée et une charge DB inutile.

#### Exemple de N+1

1. Requête des utilisateurs (`N` utilisateurs retournés).
2. Pour chaque utilisateur, requête séparée des posts.
3. Total des requêtes : `1 + N`.

Avec 100 utilisateurs, cela fait 101 allers-retours DB.

#### Où cela apparaît dans les applis NestJS

1. Accès aux relations lazy TypeORM dans des boucles.
2. Résolveurs GraphQL qui résolvent des champs imbriqués entité par entité.
3. Méthodes service qui font des appels repository répétés par élément.

#### Comment le résoudre

1. **Chargement eager avec joins**
   Utiliser des joins query builder pour récupérer les relations en une requête
   (ou un petit nombre contrôlé).

2. **Chargement par lot (batch loading)**
   Utiliser un batching style DataLoader (surtout en GraphQL).

3. **Requêtes IN**
   Récupérer les lignes liées pour tous les IDs parents d’un coup,
   puis mapper en mémoire.

4. **Optimisation de projection**
   Sélectionner seulement les colonnes nécessaires pour réduire le payload.

#### Exemple TypeORM avec join

```ts
const users = await this.usersRepo
  .createQueryBuilder('u')
  .leftJoinAndSelect('u.posts', 'p')
  .getMany();
```

#### Exemple de pattern batch loading

```ts
const users = await this.usersRepo.find();
const userIds = users.map(u => u.id);

const posts = await this.postsRepo.find({
  where: { userId: In(userIds) },
});

const byUser = new Map<number, PostEntity[]>();
for (const post of posts) {
  const arr = byUser.get(post.userId) ?? [];
  arr.push(post);
  byUser.set(post.userId, arr);
}
```

#### Signaux de détection

1. Croissance soudaine du nombre de requêtes avec des jeux de résultats plus grands.
2. Latence endpoint qui croît linéairement avec le nombre de lignes parentes.
3. Requêtes SQL similaires répétées dans les logs/monitoring.

#### Stratégie pratique de prévention

1. Activer les logs SQL/requêtes en tests de performance hors prod.
2. Ajouter des assertions de nombre de requêtes pour les endpoints critiques.
3. Préférer des méthodes repository conçues pour des lectures d’agrégats.
4. Revoir les résolveurs GraphQL pour éviter les appels DB par champ.

#### Règle pratique

Si un endpoint charge des collections avec relations, concevez l’accès aux données
dès le départ pour le batching/joins. N’utilisez jamais des boucles de fetch lazy
par élément sur des chemins de production.

</details>

<details>
<summary>50. Qu’est-ce que le connection pooling et comment le configurer correctement pour une base de données ?</summary>

#### NestJS

Le connection pooling est un ensemble géré de connexions DB réutilisables,
partagées entre les requêtes. Au lieu d’ouvrir une nouvelle connexion pour
chaque requête, l’application emprunte une connexion du pool puis la rend.

#### Pourquoi le pooling est important

1. Réduit le coût d’établissement des connexions.
2. Améliore le débit et la latence sous charge.
3. Évite la surcharge DB due aux pics de connexions non contrôlés.
4. Stabilise le comportement avec des requêtes concurrentes.

#### Paramètres clés du pool

1. **taille max du pool**
   Nombre maximal de connexions DB simultanées par instance d’app.

2. **taille min du pool** (selon driver)
   Nombre minimal de connexions idle conservées ouvertes.

3. **acquire timeout**
   Durée d’attente d’une connexion libre.

4. **idle timeout**
   Durée de conservation des connexions inutilisées avant fermeture.

5. **durée de vie max**
   Âge maximal d’une connexion avant recyclage.

#### Stratégie de dimensionnement (pratique)

1. Partir de la limite DB et du nombre de réplicas d’app :
   `pool_max_per_instance * replica_count < db_connection_limit - safety_margin`.

2. Garder de la marge pour :
   1. migrations/outils admin
   2. workers de fond
   3. pics de trafic inattendus

3. Faire des tests de charge et ajuster selon :
   1. temps d’attente d’acquisition de connexion
   2. CPU DB
   3. contention de verrous
   4. latence p95/p99

#### Exemple TypeORM/NestJS (Postgres)

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  synchronize: false,
  extra: {
    max: 20,                  // connexions max du pool
    connectionTimeoutMillis: 5000,
    idleTimeoutMillis: 30000,
  },
});
```

#### Bonnes pratiques opérationnelles

1. Utiliser une seule DataSource globale par process app (éviter plusieurs pools).
2. Définir des query timeouts et statement timeouts.
3. Surveiller les métriques du pool : actives, idle, en attente.
4. Ajuster selon la charge réelle, pas selon les valeurs par défaut.
5. En serverless/forte élasticité, envisager PgBouncer ou un pooling managé.

#### Erreurs fréquentes

1. Pool trop grand -> thrashing DB / pression de verrous.
2. Pool trop petit -> file d’attente des requêtes / timeouts.
3. Ignorer le multiplicateur de scaling horizontal entre réplicas.
4. Ouvrir manuellement de nouveaux clients dans les handlers de requêtes.

#### Règle pratique

La taille du pool de connexions est une décision de capacité système,
pas seulement une configuration ORM. Ajustez-la avec une charge proche
production et les limites réelles de la base.

</details>

<details>
<summary>51. Comment se protéger contre l’injection SQL dans TypeORM/Prisma ?</summary>

#### NestJS

La protection contre l’injection SQL dans NestJS avec TypeORM/Prisma repose sur
un principe clé : **ne jamais construire du SQL par concaténation de chaînes avec
une entrée non fiable**.

Utilisez des requêtes paramétrées et des API ORM qui bindent les valeurs en sécurité.

#### Défauts sûrs (safe defaults)

1. **Repository/query builder TypeORM avec paramètres**
2. **Méthodes client Prisma avec filtres typés**
3. **Validation DTO + parsing avant la couche de persistance**

#### Patterns sûrs TypeORM

API repository :

```ts
await usersRepo.findOne({ where: { email: input.email } });
```

QueryBuilder avec paramètres liés :

```ts
await usersRepo
  .createQueryBuilder('u')
  .where('u.email = :email', { email: input.email })
  .andWhere('u.status = :status', { status: 'active' })
  .getMany();
```

#### Patterns sûrs Prisma

```ts
await prisma.user.findMany({
  where: {
    email: input.email,
    status: 'active',
  },
});
```

Prisma génère des requêtes paramétrées en interne pour les méthodes client standard.

#### Anti-patterns dangereux

1. SQL brut avec interpolation de chaîne :

```ts
// BAD
await dataSource.query(`SELECT * FROM users WHERE email = '${input.email}'`);
```

2. ORDER BY / noms de colonnes dynamiques non sûrs issus de l’entrée utilisateur.
3. Passage de fragments non validés aux fonctions SQL brutes.

#### Si le SQL brut est inévitable

1. Utiliser des placeholders de paramètres :

```ts
await dataSource.query('SELECT * FROM users WHERE email = $1', [input.email]);
```

2. Whitelister explicitement les identifiants dynamiques (colonnes/tri) :
   mapper l’entrée vers un token SQL sûr connu.

#### Défense en profondeur

1. Valider et assainir les entrées via DTO + `ValidationPipe`.
2. Utiliser des comptes DB au moindre privilège.
3. Désactiver les permissions DB dangereuses (drop/alter si non requis).
4. Logger les patterns de requêtes suspects et les échecs d’authentification.
5. Ajouter des tests de sécurité avec payloads d’injection sur endpoints critiques.

#### Règle pratique

Restez sur les API ORM pour 95 % des requêtes. Pour le SQL brut restant,
paramétrez toujours les valeurs et whitelistez toute structure SQL dynamique.

</details>

<details>
<summary>52. Comment organiser correctement la pagination dans une API REST ? (offset vs cursor-based)</summary>

#### NestJS

Une bonne conception de pagination REST doit être stable, performante et prévisible
pour les clients. Les deux principaux modèles sont la pagination par offset
et la pagination par curseur.

#### Offset vs curseur : différence clé

1. **Pagination offset**
   Utilise `limit` + `offset` (ou page/pageSize).
   Exemple : `GET /users?limit=20&offset=40`.

2. **Pagination par curseur**
   Utilise un pointeur vers le dernier enregistrement vu dans un flux trié.
   Exemple : `GET /users?limit=20&cursor=eyJpZCI6MTIzfQ==`.

#### Quand utiliser la pagination offset

1. Jeux de données petits/moyens.
2. Besoin de sauts de page aléatoires (`page=7`).
3. Dashboards admin/backoffice plus simples.

Compromis :
1. Plus lente sur de grands offsets.
2. Pages incohérentes en cas d’insertions/suppressions concurrentes.

#### Quand utiliser la pagination par curseur

1. Grands jeux de données qui changent fréquemment.
2. Infinite scroll / feeds mobiles.
3. APIs sensibles à la performance.

Avantages :
1. Meilleure performance DB à grande échelle.
2. Ordonnancement plus stable sous écritures concurrentes.

Compromis :
1. Pas de saut de page aléatoire naturel.

#### Règles de conception essentielles (deux modèles)

1. Définir toujours un ordre de tri déterministe :
   ex. `ORDER BY created_at DESC, id DESC`.

2. Imposer une taille de page maximale côté serveur.

3. Retourner des métadonnées de pagination :
   `hasNext`, `nextCursor` (modèle curseur) ou `total` (modèle offset si nécessaire).

4. Valider les paramètres de pagination via DTO + pipes.

#### Exemples de format de réponse

Offset :

```json
{
  "data": [...],
  "meta": { "limit": 20, "offset": 40, "total": 312, "hasNext": true }
}
```

Curseur :

```json
{
  "data": [...],
  "meta": { "limit": 20, "nextCursor": "eyJjcmVhdGVkQXQiOiIyMDI2LTA0LTMwVDEwOjAwOjAwWiIsImlkIjoxMjN9", "hasNext": true }
}
```

#### Notes d’implémentation NestJS

1. Créer des DTO dédiés : `OffsetPaginationDto`, `CursorPaginationDto`.
2. Garder la logique de pagination dans la couche repository/requête, pas dans le contrôleur.
3. Encoder le curseur comme token opaque (base64/json + signature optionnelle).
4. Vérifier que les index DB correspondent aux clés tri/filtre (`created_at`, `id`, champs tenant).

#### Recommandation pratique

1. Utiliser **offset** pour des endpoints internes simples.
2. Utiliser **curseur** pour des feeds publics/fort volume.
3. En cas de doute, commencer par curseur pour des timelines à forte écriture,
   afin d’éviter des problèmes futurs de performance et de cohérence.

</details>

<details>
<summary>53. Comment versionner une API dans NestJS ? (URI, Header, versioning par type média)</summary>

#### NestJS

Le versioning d’API dans NestJS permet de faire évoluer les endpoints sans casser
les clients existants. Nest prend en charge les stratégies URI, en-tête personnalisé
et type média.

#### Stratégies de versioning

1. **Versioning URI**
   Version dans le chemin : `/v1/users`, `/v2/users`.

2. **Versioning par header**
   Version dans un en-tête personnalisé (ex. `X-API-Version: 2`).

3. **Versioning par type média**
   Version dans le type média de l’en-tête `Accept`
   (ex. `application/vnd.myapp.v2+json`).

#### Activer le versioning dans NestJS

```ts
import { NestFactory, VersioningType } from '@nestjs/core';

const app = await NestFactory.create(AppModule);

app.enableVersioning({
  type: VersioningType.URI, // ou HEADER / MEDIA_TYPE
  defaultVersion: '1',
});
```

#### Déclarer les versions sur contrôleurs/routes

Niveau contrôleur :

```ts
@Controller({ path: 'users', version: '1' })
export class UsersV1Controller {}
```

Niveau route :

```ts
@Get()
@Version('2')
findAllV2() {}
```

Versions multiples sur un même handler :

```ts
@Version(['1', '2'])
```

#### Choisir la stratégie

1. **Versioning URI** (le plus courant)
   1. Facile à déboguer et à mettre en cache.
   2. Clair dans les logs et la documentation.
   3. Meilleur choix par défaut pour les APIs REST publiques.

2. **Versioning par header**
   1. Garde des URLs propres.
   2. Utile avec des clients entreprise contrôlés.
   3. Plus difficile à tester manuellement et à mettre en cache par défaut.

3. **Versioning par type média**
   1. Style orienté standards de négociation de contenu.
   2. Le plus complexe côté clients/outillage.

#### Bonnes pratiques

1. Introduire le versioning avant le premier changement cassant.
2. Maintenir une fenêtre de rétrocompatibilité et une politique de dépréciation.
3. Versionner seulement les changements de contrat cassants.
4. Documenter les calendriers de fin de support des anciennes versions.
5. Garder la logique métier partagée dans les services ; versionner surtout la couche transport.

#### Règle pratique

Pour la plupart des équipes, commencez par le **versioning URI** : explicite et
simple à opérer. Utilisez header/type média seulement si des exigences plateforme
claires l’imposent.

</details>

<details>
<summary>54. Comment implémenter la documentation Swagger dans NestJS via @nestjs/swagger ?</summary>

#### NestJS

Swagger dans NestJS s’implémente avec `@nestjs/swagger` pour générer
automatiquement une documentation OpenAPI à partir des contrôleurs, DTO et décorateurs.

#### Étape 1 : installer les paquets

1. `@nestjs/swagger`
2. `swagger-ui-express`

#### Étape 2 : configurer Swagger dans `main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  const config = new DocumentBuilder()
    .setTitle('NestJS Interview API')
    .setDescription('API documentation')
    .setVersion('1.0.0')
    .addBearerAuth()
    .build();

  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('docs', app, document);

  await app.listen(3000);
}
bootstrap();
```

L’URL de la documentation sera `/docs`.

#### Étape 3 : annoter les contrôleurs et DTO

Annotations de contrôleur :

```ts
import { ApiBearerAuth, ApiOperation, ApiResponse, ApiTags } from '@nestjs/swagger';

@ApiTags('users')
@ApiBearerAuth()
@Controller('users')
export class UsersController {
  @Get(':id')
  @ApiOperation({ summary: 'Get user by id' })
  @ApiResponse({ status: 200, description: 'User found' })
  @ApiResponse({ status: 404, description: 'User not found' })
  findOne() {}
}
```

Annotations DTO :

```ts
import { ApiProperty } from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({ example: 'john@example.com' })
  email: string;

  @ApiProperty({ minLength: 8 })
  password: string;
}
```

#### Étape 4 : garder les schémas exacts

1. Utiliser des DTO basés sur des classes (pas des interfaces) pour les métadonnées runtime.
2. Combiner avec `ValidationPipe` pour que la doc reflète les vraies contraintes.
3. Documenter explicitement auth, pagination et modèles d’erreur.

#### Pratiques avancées en production

1. Générer une doc par version d’API si le versioning est activé.
2. Masquer les endpoints internes/admin si nécessaire.
3. Utiliser `operationIdFactory` pour une génération SDK stable.
4. Exporter le JSON OpenAPI en CI pour les vérifications de contrat/codegen client.
5. Protéger l’endpoint de doc en production si l’API est privée.

#### Conclusion pratique

Considérez Swagger comme un artefact de contrat, pas seulement une UI.
Mettez à jour décorateurs et DTO en même temps que les changements d’endpoints
pour éviter la dérive de documentation.

</details>

<details>
<summary>55. Comment implémenter CORS dans NestJS et quand des paramètres personnalisés sont-ils nécessaires ?</summary>

#### NestJS

CORS (Cross-Origin Resource Sharing) contrôle quelles origines navigateur peuvent
accéder à votre API. Dans NestJS, cela se configure au niveau du bootstrap
application.

#### Activation CORS basique

```ts
const app = await NestFactory.create(AppModule);
app.enableCors();
```

C’est acceptable en développement local, mais trop permissif pour la production.

#### Configuration CORS style production

```ts
app.enableCors({
  origin: ['https://app.example.com', 'https://admin.example.com'],
  methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE', 'OPTIONS'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true,
  maxAge: 86400,
});
```

#### Quand des paramètres CORS personnalisés sont nécessaires

1. **Plusieurs domaines frontend**
   Besoin d’une allowlist explicite par environnement.

2. **Auth basée sur cookies (`credentials: true`)**
   Exige une origine spécifique (pas `*`) et une politique de cookies sécurisée.

3. **Headers/tokens personnalisés**
   Ajouter les en-têtes requis à `allowedHeaders`.

4. **Méthodes complexes/preflight**
   Configurer `methods` et s’assurer que `OPTIONS` fonctionne correctement.

5. **Règles d’origine dynamiques ou par tenant**
   Utiliser un resolver d’origine basé sur une fonction.

#### Exemple d’origine dynamique

```ts
app.enableCors({
  origin: (origin, callback) => {
    const allowlist = new Set([
      'https://app.example.com',
      'https://staging.example.com',
    ]);

    if (!origin || allowlist.has(origin)) {
      return callback(null, true);
    }
    return callback(new Error('Not allowed by CORS'));
  },
  credentials: true,
});
```

#### Erreurs fréquentes

1. Utiliser `origin: '*'` avec `credentials: true` (invalide/non sûr pour cookies).
2. Oublier la gestion preflight (`OPTIONS`) dans les proxies/gateways.
3. Coder en dur une seule origine pour tous les environnements.
4. Traiter CORS comme frontière de sécurité pour des clients non navigateur.

#### Recommandations pratiques

1. Conserver une allowlist d’origines stricte en production.
2. Séparer la config CORS par environnement via `ConfigService`.
3. Logger les origines bloquées pour le débogage.
4. Combiner CORS avec vraie auth/authz, rate limiting et stratégie CSRF si pertinent.

</details>

<details>
<summary>56. Qu’est-ce que l’idempotence dans le contexte d’une API REST et comment la garantir ?</summary>

#### NestJS

L’idempotence signifie que répéter plusieurs fois la même requête produit le même
état final du système que si elle était exécutée une seule fois.

Dans les APIs REST, c’est critique pour la fiabilité face aux retries,
timeouts réseau et soumissions dupliquées côté client.

#### Sémantique HTTP et idempotence

1. **Généralement idempotentes par conception**
   `GET`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`.

2. **Non idempotente par défaut**
   `POST` (crée souvent une nouvelle ressource à chaque appel).

#### Pourquoi l’idempotence est importante

1. Retries client sûrs après timeout.
2. Protection contre les actions dupliquées (double paiement/commande).
3. Meilleure résilience en systèmes distribués et flux at-least-once.

#### Comment garantir l’idempotence en pratique

1. **Pattern de clé d’idempotence (pour POST)**
   Le client envoie une clé unique (ex. header `Idempotency-Key`).
   Le serveur stocke clé + empreinte de requête + réponse.
   Un même retry avec la même clé renvoie le résultat initial, sans réexécuter l’action.

2. **Contraintes base de données**
   Imposer l’unicité sur les identifiants métier
   (`externalPaymentId`, `orderReference`, etc.).

3. **Patterns upsert/compare-and-set**
   Utiliser des écritures déterministes quand c’est possible.

4. **Traitement transactionnel**
   Protéger les écritures en plusieurs étapes contre les duplications partielles.

#### Schéma d’implémentation NestJS

1. Un interceptor/guard vérifie `Idempotency-Key`.
2. Calculer l’empreinte (route + utilisateur + hash payload).
3. Rechercher l’enregistrement d’idempotence :
   1. Si terminé -> renvoyer la réponse stockée.
   2. Si en cours -> renvoyer conflit/politique retry-later.
   3. Si absent -> réserver la clé et exécuter le handler.
4. Stocker la réponse finale de manière atomique et la renvoyer.

#### Flux conceptuel minimal

```text
Request -> middleware/interceptor d'idempotence
        -> clé existe avec réponse terminée ? renvoyer réponse en cache
        -> sinon exécuter le use case
        -> persister le résultat par clé
        -> renvoyer la réponse
```

#### Pièges fréquents

1. Réutiliser une clé pour un payload différent (il faut détecter et rejeter).
2. Stocker les clés sans TTL/cleanup.
3. Ne pas scoper la clé par tenant/utilisateur si nécessaire.
4. Renvoyer une réponse différente lors d’un retry avec la même clé.

#### Recommandation pratique

Pour tous les endpoints paiement/commande/abonnement, imposez des clés
idempotentes + des contraintes d’unicité DB. Cela apporte une protection
contre les doublons à la fois au niveau applicatif et persistance.

</details>

<details>
<summary>57. Comment implémenter le rate limiting dans NestJS ? (@nestjs/throttler)</summary>

#### NestJS

Le rate limiting contrôle combien de requêtes un client peut faire dans une
fenêtre de temps. Dans NestJS, la solution standard est `@nestjs/throttler`.

#### Pourquoi le rate limiting est nécessaire

1. Protège l’API contre les abus et tentatives de brute force.
2. Réduit la surcharge accidentelle causée par des clients bruyants.
3. Améliore l’équité entre utilisateurs/tenants.
4. Ajoute de la résilience avant d’atteindre des dépendances coûteuses.

#### Étape 1 : installer et configurer le module

```ts
import { Module } from '@nestjs/common';
import { ThrottlerModule } from '@nestjs/throttler';

@Module({
  imports: [
    ThrottlerModule.forRoot([
      {
        ttl: 60_000, // 60 secondes
        limit: 100,  // 100 requêtes par fenêtre
      },
    ]),
  ],
})
export class AppModule {}
```

#### Étape 2 : appliquer un guard global

```ts
import { ThrottlerGuard } from '@nestjs/throttler';
import { APP_GUARD } from '@nestjs/core';

providers: [
  {
    provide: APP_GUARD,
    useClass: ThrottlerGuard,
  },
];
```

Toutes les routes sont alors limitées par défaut.

#### Étape 3 : personnaliser par route/contrôleur

Limite plus stricte :

```ts
@Throttle({ default: { limit: 5, ttl: 60_000 } })
@Post('login')
login() {}
```

Ignorer la limite pour un endpoint de santé :

```ts
@SkipThrottle()
@Get('health')
health() {}
```

#### Stratégie de clé (qui est limité)

Par défaut, c’est souvent l’IP client. En réel, vous pouvez avoir besoin de :
1. limite par ID utilisateur (après auth),
2. limite par tenant/clé API,
3. politiques spécifiques par groupe de routes.

Vous pouvez étendre la logique guard/tracker pour des clés personnalisées.

#### Note déploiement distribué

En environnement multi-instances, le stockage en mémoire n’est pas suffisant pour
des limites globales strictes. Utilisez un stockage partagé (ex. Redis) pour garder
la cohérence des limites entre réplicas.

#### Bonnes pratiques

1. Mettre des limites plus strictes sur auth/reset/token.
2. Retourner des réponses `429 Too Many Requests` claires.
3. Exposer des métadonnées de retry (`Retry-After`) quand possible.
4. Monitorer les hits de throttling par route/client pour ajuster.
5. Combiner avec rate limiting WAF/reverse proxy pour une défense multicouche.

</details>

<details>
<summary>58. Comment implémenter le request tracing (ajout d’un requestId à chaque requête) ?</summary>

#### NestJS

Le request tracing consiste à attacher un `requestId` unique à chaque requête
entrante et à le propager dans les logs, les réponses et les appels downstream.

C’est essentiel pour déboguer les systèmes distribués et corréler les événements
entre services.

#### Objectifs du request tracing

1. Corréler tous les logs d’une même requête.
2. Suivre les échecs à travers middleware/guards/services/DB/APIs externes.
3. Renvoyer un identifiant de requête aux clients/équipes support.

#### Pattern d’implémentation courant

1. Un middleware lit le header existant (`x-request-id`) ou génère un nouvel UUID.
2. Stocker l’ID sur l’objet requête.
3. Ajouter l’ID dans les en-têtes de réponse.
4. Le logger inclut automatiquement `requestId` dans chaque entrée.

#### Exemple de middleware

```ts
import { Injectable, NestMiddleware } from '@nestjs/common';
import { randomUUID } from 'crypto';
import { Request, Response, NextFunction } from 'express';

@Injectable()
export class RequestIdMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: NextFunction) {
    const incoming = req.header('x-request-id');
    const requestId = incoming && incoming.trim() ? incoming : randomUUID();

    (req as any).requestId = requestId;
    res.setHeader('x-request-id', requestId);

    next();
  }
}
```

Appliquer le middleware globalement dans `AppModule.configure(...)`.

#### Intégration logging

1. Inclure `requestId` dans les logs structurés depuis interceptors/services.
2. Préférer une abstraction de logger centralisée pour embarquer les champs de corrélation sur chaque log.

Exemple d’interceptor (timing + requestId) :

```ts
const req = context.switchToHttp().getRequest();
const requestId = req.requestId;
this.logger.log({ msg: 'request.start', requestId, path: req.url });
```

#### Propagation de contexte async (avancé)

Pour des couches de service profondes/chaînes async, utiliser `AsyncLocalStorage`
(ou module CLS) afin d’accéder à `requestId` sans le passer manuellement partout.

#### Propagation downstream

1. Forward `x-request-id` dans les appels HTTP sortants.
2. Inclure le request ID dans les métadonnées des messages queues/events.
3. Mapper vers trace/span IDs si vous utilisez OpenTelemetry.

#### Bonnes pratiques

1. Accepter l’ID de requête amont depuis des gateways de confiance.
2. Générer l’ID côté serveur s’il manque.
3. Retourner l’ID dans chaque réponse d’erreur pour le diagnostic support.
4. Garder un nom de header cohérent entre tous les services.
5. Traiter `requestId` comme métadonnée de corrélation, pas comme token de sécurité.

</details>

<details>
<summary>59. Comment gérer multipart/form-data et les uploads de fichiers dans NestJS ?</summary>

#### NestJS

Dans NestJS (plateforme Express), les uploads de fichiers sont généralement gérés
avec Multer via les interceptors `@nestjs/platform-express`.

`multipart/form-data` est utilisé lorsque les requêtes incluent des fichiers
(et éventuellement des champs supplémentaires).

#### Blocs de base

1. `FileInterceptor()` pour un fichier unique.
2. `FilesInterceptor()` pour plusieurs fichiers (même champ).
3. `FileFieldsInterceptor()` pour plusieurs champs nommés.
4. `@UploadedFile()` / `@UploadedFiles()` pour accéder aux fichiers parsés.

#### Exemple d’upload fichier unique

```ts
import {
  BadRequestException,
  Controller,
  Post,
  UploadedFile,
  UseInterceptors,
} from '@nestjs/common';
import { FileInterceptor } from '@nestjs/platform-express';
import { diskStorage } from 'multer';
import { extname } from 'path';

@Controller('files')
export class FilesController {
  @Post('avatar')
  @UseInterceptors(
    FileInterceptor('file', {
      storage: diskStorage({
        destination: './uploads',
        filename: (_req, file, cb) => {
          const unique = `${Date.now()}-${Math.round(Math.random() * 1e9)}`;
          cb(null, `${unique}${extname(file.originalname)}`);
        },
      }),
      limits: { fileSize: 5 * 1024 * 1024 }, // 5MB
      fileFilter: (_req, file, cb) => {
        const allowed = ['image/jpeg', 'image/png', 'image/webp'];
        if (!allowed.includes(file.mimetype)) {
          return cb(new BadRequestException('Invalid file type') as any, false);
        }
        cb(null, true);
      },
    }),
  )
  uploadAvatar(@UploadedFile() file: Express.Multer.File) {
    return { filename: file.filename, size: file.size };
  }
}
```

#### Gestion de plusieurs fichiers

1. Même champ :
   `@UseInterceptors(FilesInterceptor('files', 10))`

2. Champs nommés :
   `@UseInterceptors(FileFieldsInterceptor([{ name: 'avatar', maxCount: 1 }, ...]))`

#### Exigences de validation et sécurité

1. Imposer des limites de taille max.
2. Valider le type MIME et (idéalement) la signature réelle du fichier.
3. Assainir les noms de fichiers et ne pas faire confiance aux noms fournis par le client.
4. Stocker hors des chemins sensibles/exécutables/statiques.
5. Exécuter un scan malware pour les domaines à haut risque.

#### Stratégies de stockage

1. Disque local (simple pour dev/petits déploiements).
2. Stockage objet (S3/GCS/MinIO) pour une production scalable.
3. Stockage DB seulement pour des cas spéciaux (souvent non idéal pour gros binaires).

#### Bonnes pratiques production

1. Préférer des uploads directs vers stockage objet pour les gros fichiers.
2. Garder les métadonnées en DB (owner, key, mime, size, checksum).
3. Utiliser des URLs signées pour contrôler l’accès upload/download.
4. Appliquer auth + rate limits sur les endpoints d’upload.
5. Ajouter des politiques de rétention/cleanup.

</details>

<details>
<summary>60. Comment implémenter la compression (gzip/brotli) dans NestJS ?</summary>

#### NestJS

La compression réduit la taille des réponses et améliore les performances réseau,
surtout pour les APIs riches en JSON/texte.

Dans NestJS (adapter Express), gzip/brotli s’active généralement via un middleware
de compression.

#### Configuration de base (Express)

1. Installer `compression`.
2. Enregistrer le middleware dans `main.ts`.

```ts
import { NestFactory } from '@nestjs/core';
import compression from 'compression';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    compression({
      threshold: 1024, // compresser les réponses > 1KB
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

Le header client `Accept-Encoding` détermine la négociation d’algorithme
(`br`, `gzip`, etc., selon le runtime/proxy).

#### Où le brotli est généralement appliqué

1. Couche application (middleware Node/support runtime).
2. Reverse proxy/CDN (Nginx, Cloudflare, Vercel, etc.).

Dans beaucoup de setups production, le proxy/CDN compresse plus efficacement
que le process applicatif.

#### Ce qu’il faut compresser

1. Réponses JSON
2. Texte/HTML/CSS/JS
3. Réponses GraphQL

#### Ce qu’il ne faut pas compresser

1. Assets déjà compressés (`.zip`, `.jpg`, `.png`, `.mp4`, `.pdf`)
2. Payloads très petits (le coût de compression peut dépasser le gain)

#### Bonnes pratiques opérationnelles

1. Utiliser un threshold pour ignorer les réponses minuscules.
2. Vérifier que cache/proxy respecte `Vary: Accept-Encoding`.
3. Mesurer le coût CPU vs gain de bande passante.
4. Préférer la compression proxy/CDN sur des charges à fort trafic.
5. Garder en tête les risques TLS + compression pour des contextes sensibles
   (risque moderne rare, mais suivre les recommandations plateforme).

#### Note Fastify

Si vous utilisez l’adapter Fastify, utilisez le plugin de compression Fastify
correspondant au lieu du middleware Express.

#### Recommandation pratique

Activez la compression par défaut pour les réponses API, puis ajustez le threshold
et l’emplacement (app vs edge/proxy) selon le trafic réel et le profil CPU.

</details>

<details>
<summary>61. Comment implémenter helmet et quels en-têtes HTTP définit-il ?</summary>

#### NestJS

Helmet est un middleware de sécurité qui définit des en-têtes HTTP de protection
pour réduire la surface d’attaque web courante (XSS, clickjacking, MIME sniffing,
fuite de données via referrer, etc.).

Dans NestJS (adapter Express), intégrez-le globalement dans `main.ts`.

#### Configuration de base

1. Installer `helmet`.
2. L’enregistrer comme middleware.

```ts
import { NestFactory } from '@nestjs/core';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    helmet({
      // Configurer CSP/HSTS/etc. selon les besoins d'environnement
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

#### En-têtes courants définis par Helmet (selon version/config)

1. `Content-Security-Policy` (CSP)
2. `Cross-Origin-Opener-Policy`
3. `Cross-Origin-Resource-Policy`
4. `Origin-Agent-Cluster`
5. `Referrer-Policy`
6. `Strict-Transport-Security` (HSTS, quand le contexte HTTPS convient)
7. `X-Content-Type-Options: nosniff`
8. `X-DNS-Prefetch-Control`
9. `X-Download-Options` (protection legacy IE)
10. `X-Frame-Options` (protection clickjacking)
11. `X-Permitted-Cross-Domain-Policies`
12. Comportement `X-XSS-Protection` (legacy ; les navigateurs modernes s’appuient sur CSP)

Les valeurs par défaut exactes peuvent varier selon la version de Helmet et l’environnement runtime.

#### Notes de configuration pratiques

1. **Le tuning CSP est critique**
   Une CSP stricte améliore la sécurité, mais peut casser scripts/styles si mal configurée.

2. **HSTS uniquement en HTTPS**
   À activer avec prudence sur les domaines production ; éviter un lock-in involontaire en local/dev.

3. **CORS + Helmet**
   Ils répondent à des préoccupations différentes ; configurez les deux explicitement.

4. **Conscience du reverse proxy**
   Vérifier la config trusted proxy/termination HTTPS pour un comportement HSTS/sécurité correct.

#### Pattern de production typique

1. Activer Helmet globalement.
2. Personnaliser les directives CSP selon le comportement frontend/API.
3. Garder des profils de config séparés dev vs production.
4. Vérifier les en-têtes via tests d’intégration et scans de sécurité.

#### Règle pratique

Helmet donne un bon socle de durcissement, mais ce n’est pas une sécurité complète.
Combinez-le avec auth, validation, rate limits, cookies sécurisés et hygiène des dépendances.

</details>

<details>
<summary>62. Quelles sont les principales vulnérabilités OWASP et comment s’en protéger ?</summary>

#### NestJS

Les principaux risques OWASP sont des classes courantes de défaillances de sécurité web.
Dans NestJS, la mitigation se fait par des contrôles en couches : validation, auth,
configurations sûres, monitoring et durcissement de l’infrastructure.

#### Principaux risques OWASP et protections orientées NestJS

1. **Contrôle d’accès cassé (Broken Access Control)**
   1. Utiliser des Guards pour l’autorisation (`RolesGuard`, guards policy/ABAC).
   2. Imposer des vérifications de propriété sur l’accès aux ressources.
   3. Refuser par défaut ; éviter les accès implicites.

2. **Défaillances cryptographiques (Cryptographic Failures)**
   1. Utiliser HTTPS partout.
   2. Hasher les mots de passe avec des algorithmes robustes (argon2/bcrypt avec coût adapté).
   3. Stocker les secrets dans un secret manager, pas dans le code source.
   4. Chiffrer les données sensibles au repos si nécessaire.

3. **Injection (SQL/NoSQL/Commande)**
   1. Utiliser des requêtes ORM paramétrées (TypeORM/Prisma).
   2. Valider/whitelister les entrées via DTO + `ValidationPipe`.
   3. Éviter les requêtes brutes construites en chaîne et les commandes shell avec entrée utilisateur.

4. **Conception non sûre (Insecure Design)**
   1. Faire du threat modeling sur les flux critiques (auth, paiements, admin).
   2. Ajouter dès la conception idempotence, rate limits et contrôles anti-abus.
   3. Appliquer le moindre privilège aux frontières d’architecture.

5. **Mauvaise configuration de sécurité (Security Misconfiguration)**
   1. Activer Helmet et un CORS strict.
   2. Désactiver les options debug par défaut en production.
   3. Garder les environnements de production séparés et verrouillés.

6. **Composants vulnérables/obsolètes (Vulnerable and Outdated Components)**
   1. Mettre à jour régulièrement les dépendances.
   2. Faire des scans SCA en CI (`npm audit`, Snyk, Dependabot, etc.).
   3. Supprimer les packages inutilisés.

7. **Défaillances d’identification/authentification**
   1. Access tokens courte durée + rotation des refresh tokens.
   2. MFA pour les comptes à haut risque.
   3. Gestion sécurisée cookie/token, lockout/rate-limit sur endpoints de login.

8. **Défaillances d’intégrité logicielle et des données**
   1. Artifacts signés, pipeline CI/CD de confiance.
   2. Vérifier les sources tierces et pinner les versions.
   3. Contrôler les changements de configuration et les validations de release.

9. **Défaillances de logs/monitoring sécurité**
   1. Logs structurés avec requestId/userId/action/résultat.
   2. Alerting sur anomalies d’auth et pics d’erreurs.
   3. Conserver les stack traces dans les logs, pas dans les réponses.

10. **SSRF (Server-Side Request Forgery)**
   1. Restreindre les destinations réseau sortantes.
   2. Valider et whitelister les URLs externes.
   3. Bloquer les plages IP de métadonnées internes.

#### Checklist baseline NestJS

1. `ValidationPipe` global (`whitelist`, `forbidNonWhitelisted`, `transform`).
2. Exception filter global avec réponses d’erreur sûres.
3. Guards auth + autorisation sur routes protégées.
4. Rate limiting (`@nestjs/throttler`) sur endpoints sensibles.
5. Helmet + config CORS stricte.
6. Configuration sécurisée avec validation au démarrage (Joi/Zod).
7. Scans sécurité/dépendances en CI.

#### Conclusion pratique

La sécurité n’est pas un package unique. Dans NestJS, une posture solide vient
d’une défense en profondeur cohérente sur le code, la config, l’infrastructure
et les opérations.

</details>

<details>
<summary>63. Comment utiliser HttpModule (axios) dans NestJS pour les requêtes API externes ?</summary>

#### NestJS

Dans NestJS, les appels HTTP externes se font souvent via `HttpModule` de
`@nestjs/axios`, qui encapsule Axios et s’intègre à l’injection de dépendances.

#### Pourquoi utiliser `HttpModule`

1. Client HTTP partagé, compatible DI.
2. Configuration centralisée (base URL, timeout, headers).
3. Testabilité/mock simplifiés.
4. Intégration RxJS native (réponses `Observable`).

#### Étape 1 : enregistrer `HttpModule`

```ts
import { Module } from '@nestjs/common';
import { HttpModule } from '@nestjs/axios';

@Module({
  imports: [
    HttpModule.register({
      baseURL: 'https://api.example.com',
      timeout: 5000,
      maxRedirects: 3,
    }),
  ],
})
export class ExternalApiModule {}
```

Variante async :
`HttpModule.registerAsync(...)` avec `ConfigService`.

#### Étape 2 : injecter `HttpService` dans un provider

```ts
import { Injectable } from '@nestjs/common';
import { HttpService } from '@nestjs/axios';
import { firstValueFrom } from 'rxjs';

@Injectable()
export class ExternalUsersClient {
  constructor(private readonly http: HttpService) {}

  async getUser(id: string) {
    const response = await firstValueFrom(
      this.http.get(`/users/${id}`, {
        headers: { 'x-service': 'nestjs-app' },
      }),
    );
    return response.data;
  }
}
```

#### Pattern de gestion d’erreurs

1. Capturer les erreurs Axios et les mapper vers des exceptions domaine/app.
2. Éviter d’exposer brut les erreurs upstream aux clients API.

```ts
try {
  const res = await firstValueFrom(this.http.get('/health'));
  return res.data;
} catch (e: any) {
  const status = e?.response?.status;
  throw new BadGatewayException(`Upstream error: ${status ?? 'unknown'}`);
}
```

#### Bonnes pratiques production

1. Définir des timeouts stricts pour tous les appels sortants.
2. Ajouter retries/circuit breaker pour les dépendances instables.
3. Propager les IDs de requête/corrélation dans les headers.
4. Utiliser des DTO/adapters de réponse typés pour les contrats externes.
5. Instrumenter latence, échecs et status codes upstream.

#### Stratégie de tests

1. Mocker `HttpService` en tests unitaires.
2. En tests d’intégration, utiliser des serveurs mock (ex. nock/wiremock).
3. Valider explicitement les chemins timeout/retry/mapping d’erreurs.

#### Conclusion pratique

Traitez le HTTP externe comme un I/O non fiable : configurez `HttpModule`
centralement, encapsulez-le dans des services clients dédiés, et imposez des
politiques robustes de timeout/retry/erreurs.

</details>

<details>
<summary>64. Comment ajouter des interceptors globaux à axios dans NestJS ? (ajout de headers, logging)</summary>

#### NestJS

Dans NestJS, les interceptors Axios se configurent sur l’instance `axiosRef`
exposée par `HttpService` (`@nestjs/axios`). Cela permet d’appliquer un comportement
global aux requêtes sortantes : headers, logs, timing, tokens d’auth et
normalisation des erreurs.

#### Pourquoi utiliser les interceptors Axios

1. Centraliser le comportement HTTP sortant.
2. Éviter de répéter la logique headers/auth à chaque appel.
3. Ajouter des logs et métriques cohérents request/response.
4. Normaliser les erreurs upstream en un seul endroit.

#### Pattern d’implémentation typique

1. Créer un provider/service qui reçoit `HttpService`.
2. Dans le cycle de vie d’initialisation du module, enregistrer une fois
   les interceptors request/response.
3. Garder une logique d’interceptor légère et déterministe.

#### Exemple : headers sortants globaux + logging

```ts
import { Injectable, Logger, OnModuleInit } from '@nestjs/common';
import { HttpService } from '@nestjs/axios';

@Injectable()
export class HttpClientInterceptorSetup implements OnModuleInit {
  private readonly logger = new Logger(HttpClientInterceptorSetup.name);

  constructor(private readonly http: HttpService) {}

  onModuleInit() {
    const axios = this.http.axiosRef;

    axios.interceptors.request.use((config) => {
      const startedAt = Date.now();
      (config as any).metadata = { startedAt };

      config.headers = config.headers ?? {};
      config.headers['x-service-name'] = 'nestjs-api';
      config.headers['x-request-id'] = config.headers['x-request-id'] ?? 'generated-or-propagated-id';

      this.logger.debug(`HTTP -> ${config.method?.toUpperCase()} ${config.url}`);
      return config;
    });

    axios.interceptors.response.use(
      (response) => {
        const startedAt = (response.config as any).metadata?.startedAt ?? Date.now();
        const duration = Date.now() - startedAt;
        this.logger.debug(
          `HTTP <- ${response.status} ${response.config.method?.toUpperCase()} ${response.config.url} (${duration}ms)`,
        );
        return response;
      },
      (error) => {
        const cfg = error.config ?? {};
        const status = error.response?.status;
        this.logger.warn(
          `HTTP !! ${cfg.method?.toUpperCase()} ${cfg.url} status=${status ?? 'NO_RESPONSE'}`,
        );
        return Promise.reject(error);
      },
    );
  }
}
```

Enregistrez ce provider dans un module qui importe `HttpModule`.

#### Notes importantes pour la production

1. Vérifier que les interceptors sont enregistrés une seule fois (éviter les doublons au hot reload/re-init module).
2. Propager les IDs de requête/corrélation depuis le contexte des requêtes entrantes.
3. Masquer les secrets (`Authorization`, clés API) dans les logs.
4. Garder explicite la stratégie timeout/retry/circuit-breaker (les interceptors ne remplacent pas une couche complète de résilience).

#### Cas d’usage courants

1. Injection de tokens d’auth depuis `ConfigService` ou un provider de tokens.
2. Ajout de headers tenant/contexte pour les services downstream.
3. Standardisation des objets d’erreur avant rethrow.
4. Émission de métriques/traces pour les systèmes d’observabilité.

#### Conclusion pratique

Utilisez les interceptors Axios comme l’équivalent sortant d’un middleware Nest :
un point unique pour la politique HTTP transversale sur tous les appels API externes.

</details>

<details>
<summary>65. Comment typer correctement les réponses d’API externes en TypeScript ?</summary>

#### NestJS

Bien typer les réponses d’API externes signifie traiter les données distantes comme
**non fiables** tant qu’elles ne sont pas validées, tout en utilisant les types
TypeScript pour le confort développeur.

#### Principe clé

1. Les types de compilation (`interface`/`type`) améliorent la DX.
2. La validation runtime (Zod/class-validator/guards custom) garantit la sécurité.
3. Utiliser les deux, pas l’un sans l’autre.

#### Pattern recommandé

1. Définir un DTO/type de réponse attendu.
2. Récupérer les données via un appel client HTTP typé.
3. Valider/parser à la frontière.
4. Mapper vers le modèle domaine interne avant la logique métier.

#### Exemple avec `HttpService` + Zod

```ts
import { Injectable, BadGatewayException } from '@nestjs/common';
import { HttpService } from '@nestjs/axios';
import { firstValueFrom } from 'rxjs';
import { z } from 'zod';

const ExternalUserSchema = z.object({
  id: z.string(),
  email: z.string().email(),
  status: z.enum(['active', 'blocked']),
});

type ExternalUser = z.infer<typeof ExternalUserSchema>;

@Injectable()
export class ExternalUsersClient {
  constructor(private readonly http: HttpService) {}

  async getUser(id: string): Promise<ExternalUser> {
    const res = await firstValueFrom(this.http.get<unknown>(`/users/${id}`));
    const parsed = ExternalUserSchema.safeParse(res.data);

    if (!parsed.success) {
      throw new BadGatewayException('Invalid upstream payload');
    }

    return parsed.data;
  }
}
```

#### Pourquoi ne pas se reposer uniquement sur les génériques

```ts
this.http.get<MyType>(...)
```

Cela indique seulement à TypeScript ce que vous *attendez* ; cela ne vérifie pas
la charge utile runtime réelle du service amont.

#### Stratégies pratiques de typage

1. Utiliser des modules client dédiés par API amont.
2. Séparer les DTO amont des entités domaine internes.
3. Normaliser/transformer les enums et noms de champs externes à la frontière.
4. Gérer explicitement nullable/optional (`null` en amont est fréquent).

#### Bonnes pratiques de gestion d’erreurs

1. Distinguer erreurs de transport (timeout, 5xx) et erreurs de schéma.
2. Mapper les deux vers des exceptions internes stables.
3. Logger les métadonnées de réponse amont pour le diagnostic (sans fuite de secrets).

#### Règle pratique

Typez les réponses externes en deux couches :
1. type statique pour l’intelligence de code,
2. validation de schéma runtime pour la correction et la sécurité.

</details>

<details>
<summary>66. Comment implémenter une logique de retry pour des requêtes HTTP externes dans NestJS ?</summary>

#### NestJS

La logique de retry aide à gérer les pannes transitoires (timeouts, 5xx temporaires,
brefs incidents réseau) lors d’appels API externes.

Dans NestJS, les retries s’implémentent souvent avec des opérateurs RxJS sur
`HttpService` ou avec des librairies de résilience à la frontière client.

#### Quand les retries sont appropriés

1. Erreurs timeout/réseau.
2. 5xx amont temporaires.
3. Réponses rate-limit quand le serveur fournit des indices de retry (`429` avec `Retry-After`).

#### Quand les retries sont dangereux

1. Opérations non idempotentes sans clé d’idempotence.
2. Erreurs permanentes (`400`, `401`, `403`, échecs de validation).
3. Tempêtes de retries massives pendant une panne amont.

#### Retry de base avec RxJS

```ts
import { Injectable, BadGatewayException } from '@nestjs/common';
import { HttpService } from '@nestjs/axios';
import { firstValueFrom, throwError, timer } from 'rxjs';
import { mergeMap, retryWhen } from 'rxjs/operators';

@Injectable()
export class ExternalApiClient {
  constructor(private readonly http: HttpService) {}

  async getData() {
    const request$ = this.http.get('/resource').pipe(
      retryWhen(errors =>
        errors.pipe(
          mergeMap((error, attempt) => {
            const status = error?.response?.status;
            const retryable = !status || status >= 500 || status === 429;
            const maxRetries = 3;

            if (!retryable || attempt >= maxRetries) {
              return throwError(() => error);
            }

            const backoffMs = 200 * Math.pow(2, attempt); // 200, 400, 800
            return timer(backoffMs);
          }),
        ),
      ),
    );

    try {
      const res = await firstValueFrom(request$);
      return res.data;
    } catch {
      throw new BadGatewayException('Upstream service unavailable');
    }
  }
}
```

#### Politique de retry recommandée

1. Utiliser un backoff exponentiel.
2. Ajouter du jitter pour éviter des pics de retries synchronisés.
3. Limiter strictement le nombre maximal de tentatives.
4. Retry seulement les opérations idempotentes ou protégées par idempotence.

#### Associer les retries à des garde-fous

1. Timeout global par requête.
2. Circuit breaker en cas d’échec prolongé.
3. Rate limiting et bulkheads sur les clients sortants.
4. Métriques centralisées : nombre de retries, taux d’échec final, impact latence.

#### Règle pratique

Les retries doivent améliorer la fiabilité, pas masquer les pannes.
Gardez-les sélectifs, bornés et observables.

</details>

<details>
<summary>67. Qu’est-ce que le pattern Circuit Breaker et quand en avez-vous besoin ?</summary>

#### NestJS

Le Circuit Breaker est un pattern de résilience qui empêche les appels répétés
vers une dépendance en échec. Au lieu de retry sans fin un service amont cassé,
il « ouvre le circuit » et échoue rapidement pendant un certain temps.

#### Pourquoi le circuit breaker est nécessaire

1. Évite les pannes en cascade entre services.
2. Réduit l’épuisement des ressources (threads/connexions/pression event-loop).
3. Améliore la latence pendant les incidents en échouant vite.
4. Laisse du temps à la dépendance instable pour se rétablir.

#### États du circuit

1. **Closed**
   Fonctionnement normal, les requêtes passent.

2. **Open**
   La dépendance est jugée non saine ; les appels sont bloqués immédiatement.

3. **Half-open**
   Un nombre limité de requêtes test est autorisé pour vérifier la reprise.
   Si succès -> closed ; si échec -> reopen.

#### Quand l’utiliser

1. Appels vers APIs externes/fournisseurs de paiement/services d’identité.
2. Dépendance avec taux de panne non négligeable ou pics de latence.
3. Service à fort trafic où les retries seuls amplifient les incidents.
4. Le métier peut tolérer un comportement de fallback quand l’amont est indisponible.

#### Intégration typique dans NestJS

1. Envelopper l’appel client externe dans une policy breaker.
2. Combiner avec timeout + retry (borné) + fallback.
3. Émettre des métriques/événements sur les changements d’état.

Flux conceptuel :

```text
request -> vérification timeout -> circuit breaker -> appel sortant
        -> succès: réponse normale
        -> seuil d’échec dépassé: circuit OPEN
        -> OPEN: fail fast / fallback
```

#### Options d’implémentation pratiques

1. Utiliser des librairies de résilience (ex. opossum) autour des appels `HttpService`.
2. Construire un breaker léger custom pour des cas limités.
3. Externaliser la config breaker via `ConfigService`.

#### Paramètres clés de tuning

1. Seuil d’échec (% ou nombre).
2. Taille de fenêtre glissante.
3. Durée de cooldown en état open.
4. Nombre de probes en half-open.
5. Timeout par appel.

#### Erreurs fréquentes

1. Utiliser un breaker sans observabilité (pas de métriques/logs d’état).
2. Seuils trop agressifs causant de faux open.
3. Absence de stratégie fallback en état open.
4. Combiner retries infinis avec breaker (annule l’intérêt).

#### Règle pratique

Si la panne d’un service amont peut dégrader tout votre service, ajoutez un
circuit breaker à cette frontière et surveillez ses transitions d’état comme
signaux SRE de premier plan.

</details>

<details>
<summary>68. Comment implémenter le caching (in-memory, Redis), et quand utiliser chaque approche ?</summary>

#### NestJS

Le caching stocke des données pré-calculées/fréquemment demandées pour réduire la
latence et la charge backend. Dans NestJS, les choix courants sont le cache
in-memory et le cache Redis.

#### In-memory vs Redis

1. **Cache in-memory**
   Stocké dans la mémoire d’un seul process applicatif.

2. **Cache Redis**
   Service de cache externe partagé, accessible par toutes les instances.

#### Quand utiliser le cache in-memory

1. Applications mono-instance ou développement local.
2. Valeurs cachées petites et de courte durée.
3. Lectures locales à très faible latence.

Limites :
1. Non partagé entre réplicas.
2. Perdu au redémarrage/déploiement du process.
3. La pression mémoire impacte le process applicatif.

#### Quand utiliser le cache Redis

1. Déploiements multi-instances/distribués.
2. Cache partagé entre services.
3. Besoin d’un comportement TTL/invalidation centralisé.
4. Exigences plus élevées de fiabilité et d’observabilité.

Compromis :
1. Un saut réseau ajoute une petite latence.

#### Options d’implémentation NestJS

1. `CacheModule` + adapters cache manager.
2. Client Redis manuel pour des patterns avancés.
3. `CacheInterceptor` pour le caching de réponse sur endpoints sélectionnés.

#### Setup conceptuel `CacheModule`

In-memory :

```ts
CacheModule.register({
  ttl: 30_000,
  max: 500,
});
```

Redis (config dépendante de l’adapter) :

```ts
CacheModule.registerAsync({
  useFactory: () => ({
    store: /* redis store adapter */,
    url: process.env.REDIS_URL,
    ttl: 60_000,
  }),
});
```

#### Quoi mettre en cache

1. Données de référence lues souvent et peu modifiées.
2. Agrégats coûteux à calculer.
3. Réponses d’API externes avec tolérance claire à l’obsolescence.

#### Ce qu’il ne faut pas cacher aveuglément

1. Données très volatiles sans plan d’invalidation.
2. Données sensibles par utilisateur sans clés scoppées.
3. Chemins critiques d’écriture où des lectures obsolètes sont inacceptables.

#### Pratiques clés de conception

1. Utiliser un nommage explicite des clés (`user:{id}`, `catalog:v2:{region}`).
2. Définir un TTL intentionnel par type de donnée.
3. Ajouter le pattern cache-aside :
   read -> miss -> load source -> set cache -> return.
4. Planifier l’invalidation sur écritures/événements.
5. Surveiller hit ratio, évictions et impact des lectures obsolètes.

#### Règle pratique

Commencez avec in-memory seulement pour les cas simples/mono-nœud.
Pour la production avec plusieurs instances ou besoin d’état partagé,
passez à un cache adossé à Redis.

</details>

<details>
<summary>69. Qu’est-ce que l’invalidation du cache et comment l’implémenter correctement ?</summary>

#### NestJS

L’invalidation du cache est le processus de suppression/mise à jour des données
cachées quand les données source changent, afin que les clients ne reçoivent pas
de réponses obsolètes.

C’est souvent la partie la plus difficile du caching, car la justesse dépend des
règles de cohérence des données, pas seulement de la vitesse.

#### Pourquoi l’invalidation est importante

1. Évite des données visibles utilisateur obsolètes ou incohérentes.
2. Maintient l’alignement du cache avec les écritures.
3. Évite des bugs subtils dans des flux métier critiques.

#### Stratégies courantes d’invalidation

1. **Expiration basée TTL**
   Les clés expirent automatiquement après un délai fixe.

2. **Invalidation pilotée par événements/écritures**
   Après une écriture réussie, supprimer/mettre à jour explicitement les clés liées.

3. **Clés versionnées**
   Inclure une version/tag dans la clé pour basculer naturellement les lectures vers un nouvel espace de clés.

4. **Invalidation par tag/groupe** (si supportée par l’outillage)
   Invalider plusieurs entrées liées via un groupe logique.

#### Patterns pratiques d’implémentation

1. **Cache-aside avec delete-on-write**
   1. Read : cache miss -> DB -> set cache.
   2. Write : update DB -> delete des clés de cache pertinentes.

2. **Write-through**
   Mettre à jour cache et DB dans le même flux (attention à la gestion des échecs).

3. **Invalidation événementielle**
   Publier un événement domaine (`user.updated`) et invalider côté subscribers/workers.

#### Règles clés de conception

1. Utiliser un schéma de clé prévisible :
   `user:{id}`, `users:list:{filterHash}`, `product:{id}:v{n}`.

2. Garder explicite le mapping écriture -> clés :
   quelles mutations invalident quelles clés de lecture.

3. Préférer TTL court + invalidation explicite pour les hot keys critiques.

4. En systèmes multi-instances, utiliser un cache partagé (Redis), pas seulement la mémoire locale.

#### Exemple de flux d’invalidation

```text
PATCH /users/42
 -> update DB
 -> del user:42
 -> del users:list:*
 -> return updated response
```

(L’invalidation des listes peut être sélective si vous suivez les ensembles de clés filtre/index.)

#### Erreurs fréquentes

1. Mettre en cache des endpoints liste sans invalider ensemble les clés détail/liste liées.
2. Se reposer uniquement sur un TTL long pour des données fréquemment mises à jour.
3. Ne pas gérer les écritures concurrentes/race conditions.
4. Oublier le scope tenant/utilisateur dans les clés.

#### Recommandation pratique

Commencez simple :
1. cache-aside,
2. TTL courts,
3. delete-on-write explicite.

Puis évoluez vers une invalidation événementielle/par tags quand la complexité
métier augmente.

</details>
