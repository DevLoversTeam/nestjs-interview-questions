**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  NestJS <img src="./assets/nestjs.svg" width="40" height="40" alt="NestJS logo"/>
</h1>

<h2>Die beliebtesten NestJS-Interviewfragen und Antworten</h2>

<details>
<summary>1. Was ist NestJS und welche Probleme löst es?</summary>

#### NestJS

NestJS ist ein progressives Node.js-Framework für die Entwicklung von
Serveranwendungen. Es ist standardmäßig auf TypeScript ausgelegt und verwendet
vertraute Architekturideen aus Angular (Module, Dependency Injection,
Dekoratoren), während es auf HTTP-Adaptern wie Express oder Fastify läuft.

#### Welche Probleme NestJS löst

1. **Mangel an Struktur in wachsenden Node.js-Anwendungen**
   NestJS erzwingt klare modulare Grenzen (`@Module`) und macht große Codebasen
   leichter skalierbar und wartbar.

2. **Schwer zu verwaltende Abhängigkeiten**
   Die integrierte **Dependency Injection (DI)** reduziert enge Kopplung zwischen
   Klassen und verbessert die Testbarkeit.

3. **Boilerplate bei querschnittlichen Anforderungen**
   Guards, Pipes, Interceptors, Filters und Middleware bieten konsistente Muster
   für Authentifizierung, Validierung, Transformation, Logging und Fehlerbehandlung.

4. **Inkonsistente Architektur in Teams**
   NestJS liefert opinionated Konventionen, damit Teams mit demselben mentalen
   Modell und einer vorhersagbaren Projektstruktur arbeiten können.

5. **Komplexes Test-Setup**
   Testwerkzeuge (`@nestjs/testing`) und DI-freundliches Design vereinfachen
   Unit-, Integrations- und E2E-Tests.

6. **Bedarf an mehreren Backend-Transporten**
   NestJS unterstützt HTTP REST, GraphQL, WebSockets und Microservices (TCP,
   Redis, NATS, Kafka, gRPC usw.) mit einem einheitlichen Programmiermodell.

#### Kurz gesagt

NestJS hilft beim Übergang von „einfach funktionierendem Node.js-Code“ zu einer
**gut strukturierten, enterprise-tauglichen Backend-Architektur** mit hoher
Wartbarkeit, Testbarkeit und Team-Skalierbarkeit.

</details>

<details>
<summary>2. Worin unterscheidet sich NestJS von Express und Fastify?</summary>

#### NestJS

NestJS, Express und Fastify sind miteinander verwandt, bedienen aber
unterschiedliche Abstraktionsebenen.

#### Kerndifferenz

1. **Express / Fastify** sind HTTP-Server-Frameworks.
2. **NestJS** ist ein Application-Framework, das über Adapter auf Express oder
   Fastify laufen kann.

#### Architektur und Entwicklungsmodell

1. **Express**
   Minimalistisch und unopinionated. Struktur, DI-Patterns, Validierung und
   Konventionen werden manuell festgelegt.

2. **Fastify**
   Ebenfalls relativ low-level, aber auf Performance optimiert, mit
   Plugin-Ökosystem und schema-first Ansatz.

3. **NestJS**
   Opinionated Architektur „out of the box“: Module, Provider, Controller,
   Dependency Injection, Lifecycle Hooks und standardisierte Request-Pipeline.

#### Performance-Perspektive

1. **Fastify** ist bei rohem HTTP-Durchsatz in der Regel schneller als Express.
2. **NestJS mit Fastify-Adapter** liefert meist bessere Performance als NestJS
   mit Express.
3. In den meisten Business-Systemen sind Architektur, Wartbarkeit und Team-Tempo
   wichtiger als Micro-Benchmark-Unterschiede.

#### Feature-Vergleich in der Praxis

1. **Dependency Injection**
   In NestJS nativ; bei Express/Fastify manuell oder über Drittanbieter.

2. **Test-Ergonomie**
   NestJS bietet eingebaute Testing-Module-Patterns; bei low-level Frameworks
   ist mehr eigenes Setup nötig.

3. **Skalierbarkeit der Codebasis**
   NestJS-Konventionen reduzieren Chaos in großen Teams/Projekten.

4. **Umfang des Ökosystems**
   NestJS vereint REST, GraphQL, WebSockets und Microservices in einem
   einheitlichen mentalen Modell.

#### Wann was wählen

1. Wähle **Express** für sehr kleine/einfache Services oder Legacy-Kompatibilität.
2. Wähle **Fastify**, wenn maximaler Durchsatz und geringe Overhead-Kosten
   oberste Priorität haben.
3. Wähle **NestJS**, wenn langfristige Wartbarkeit, klare Architektur und ein
   standardisierter Enterprise-Backend-Ansatz benötigt werden.

</details>

<details>
<summary>3. Was sind die wichtigsten Bausteine von NestJS?</summary>

#### NestJS

NestJS besteht aus mehreren zentralen Bausteinen, die die Anwendungsarchitektur,
das Laufzeitverhalten und den Request-Flow bestimmen.

#### Zentrale Bausteine

1. **Module (`@Module`)**
   Die oberste organisatorische Einheit. Ein Modul gruppiert zusammengehörige
   Controller und Provider und steuert Sichtbarkeit über `imports` / `exports`.

2. **Controller (`@Controller`)**
   Verarbeiten eingehende Requests und liefern Responses zurück.
   Routen-Dekoratoren wie `@Get()`, `@Post()`, `@Patch()` ordnen Handler
   Endpunkten zu.

3. **Provider (`@Injectable`)**
   Klassen, die vom DI-Container von Nest verwaltet werden (Services,
   Repositories, Factories, Hilfsklassen). Sie kapseln Business-Logik und können
   in andere Klassen injiziert werden.

4. **Dependency-Injection-Container (DI)**
   Löst Provider-Abhängigkeiten über Tokens, Scopes und Modulgrenzen auf.
   Das ist die Grundlage für entkoppeltes Design in NestJS.

#### Komponenten des Request-Lifecycle

1. **Middleware**
   Läuft vor Route-Handlern. Geeignet für low-level Request-Vorverarbeitung
   (z. B. Logging, Header, Initialisierung des Request-Kontexts).

2. **Guards (`CanActivate`)**
   Entscheiden, ob ein Request weiterverarbeitet werden darf
   (Auth/Authz-Gate).

3. **Pipes (`PipeTransform`)**
   Transformieren und validieren eingehende Daten
   (DTO-Validierung, Parsing, Normalisierung).

4. **Interceptors (`NestInterceptor`)**
   Umhüllen die Handler-Ausführung für querschnittliche Anforderungen
   (Response-Mapping, Timing, Caching, Tracing, Retry-Logik).

5. **Exception Filters (`ExceptionFilter`)**
   Zentrale Fehlerbehandlung und Response-Formung für geworfene Exceptions.

#### Plattform- und Transport-Bausteine

1. **HTTP-Adapter**
   Express- oder Fastify-Integration über Plattform-Adapter.

2. **Microservice-Transport-Layer**
   TCP, Redis, NATS, Kafka, gRPC, RMQ und weitere über die Nest-Microservices-API.

3. **WebSockets / GraphQL-Module**
   Alternative Interaktionsmodelle mit denselben DI-/Modulprinzipien.

#### Praktisches mentales Modell

Nutze **Module** zur Strukturierung von Domänen, **Controller** als API-Einstieg
und **Provider** für Business-Logik. Kombiniere das Verhalten anschließend über
Middleware, Guards, Pipes, Interceptors und Filters, um robuste
Production-Services zu bauen.

</details>

<details>
<summary>4. Welche Rolle spielt TypeScript in NestJS und warum ist der Strict Mode wichtig?</summary>

#### NestJS

TypeScript ist ein zentraler Designpfeiler von NestJS, nicht nur ein optionales
Add-on. Nest verwendet Klassen, Dekoratoren, Interfaces und metadata-getriebene
DI-Patterns, die mit starker Typisierung am effektivsten funktionieren.

#### Rolle von TypeScript in NestJS

1. **Type-safe Architektur**
   Controller, Services, DTOs und Repositories werden als typisierte Klassen und
   Verträge implementiert, was Runtime-Überraschungen reduziert.

2. **Bessere Dependency-Injection-Erfahrung**
   Konstruktor-Typen machen Provider-Abhängigkeiten explizit und erleichtern das
   Refactoring.

3. **DTO-getriebene API-Grenzen**
   Request-/Response-Formen werden über DTO-Klassen und Mapped Types explizit,
   was Wartbarkeit und API-Konsistenz verbessert.

4. **Tooling und Produktivität**
   Starkes IntelliSense, sichere Auto-Refactors und Compile-time-Feedback
   beschleunigen die Team-Entwicklung.

5. **Skalierbare Codebase-Governance**
   Typverträge dienen in großen Systemen als ausführbare Dokumentation.

#### Warum der Strict Mode wichtig ist

1. **Findet Fehler früh**
   `strictNullChecks`, `noImplicitAny` und verwandte Checks verhindern häufige
   Fehler vor der Produktion.

2. **Sichereres Refactoring**
   In großen NestJS-Projekten reduziert Strict Mode versteckte Brüche beim
   Verschieben von Logik zwischen Modulen/Services.

3. **Zuverlässigere Domänenlogik**
   Explizite Optionalität und präzise Union-Typen erzwingen den bewussten Umgang
   mit Edge Cases.

4. **Bessere Team-Konsistenz**
   Strenge Compiler-Regeln schaffen gemeinsame Qualitätsstandards über alle
   Contributors hinweg.

#### Hochwirksame Strict-Einstellungen für NestJS

1. `strict: true`
2. `noImplicitAny: true`
3. `strictNullChecks: true`
4. `noUncheckedIndexedAccess: true` (empfohlen für sichereren Objekt-/Arrayzugriff)
5. `noFallthroughCasesInSwitch: true`

#### Praktische Empfehlung

Nutze TypeScript als Design-Tool, nicht nur als Syntax-Zucker. In NestJS zahlt
sich Strict Mode schnell aus, weil er Korrektheit, Lesbarkeit und langfristige
Wartbarkeit von Backend-Services verbessert.

</details>

<details>
<summary>5. Was sind Decorators in NestJS? Gib Beispiele.</summary>

#### NestJS

Decorators in NestJS sind TypeScript-Annotationen, die Metadaten an Klassen,
Methoden, Parameter und Properties anhängen. Nest liest diese Metadaten zur
Laufzeit aus, um Routing, Dependency Injection, Validierung, Autorisierung und
weitere Framework-Mechanismen zu verdrahten.

#### Warum Decorators in NestJS wichtig sind

1. **Deklarative Konfiguration**
   Verhalten wird nah am Code beschrieben, statt große externe Konfigurationsdateien
   zu pflegen.

2. **Metadatengetriebene Laufzeit**
   Nest nutzt Decorator-Metadaten, um Module aufzubauen, Provider aufzulösen und
   die Request-Pipeline zu erzeugen.

3. **Konsistente Architektur**
   Teams folgen vorhersehbaren Patterns über Controller, Services und Guards hinweg.

#### Gängige Decorator-Kategorien

1. **Klassen-Decorators**
   `@Module()`, `@Controller()`, `@Injectable()`

2. **Methoden-Decorators**
   `@Get()`, `@Post()`, `@UseGuards()`, `@UseInterceptors()`

3. **Parameter-Decorators**
   `@Param()`, `@Body()`, `@Query()`, `@Headers()`, `@Req()`

4. **Property-/Konstruktor-Injection-Decorators**
   `@Inject(TOKEN)` (bei benutzerdefinierten Provider-Tokens)

#### Beispiele

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

#### Praktisches Fazit

Decorators sind ein zentraler Grund, warum NestJS strukturiert wirkt: Sie machen
Framework-Verhalten explizit, kombinierbar und in großen Services gut skalierbar.

</details>

<details>
<summary>6. Was ist Reflect.metadata und wie nutzt NestJS es intern?</summary>

#### NestJS

`Reflect.metadata` ist Teil des Metadaten-Reflection-Mechanismus, der mit
TypeScript-Decorators verwendet wird (über das `reflect-metadata` Polyfill). Es
ermöglicht, strukturierte Metadaten an Klassen, Methoden und Parametern zu
hinterlegen, damit Frameworks diese Informationen zur Laufzeit auslesen können.

In der Praxis ist NestJS stark metadatengesteuert: Decorators schreiben
Metadaten, und Nest liest sie, um Abhängigkeitsgraphen, Routing-Maps,
Guard-/Pipe-/Interceptor-Ketten und Parameterauflösung aufzubauen.

#### Konzept in einer Zeile

1. Decorator schreibt Metadaten.
2. Nest liest Metadaten über `Reflector` / `Reflect` APIs.
3. Das Laufzeitverhalten wird automatisch zusammengesetzt.

#### Wo NestJS Metadaten nutzt

1. **Dependency Injection**
   Konstruktor-Parametertypen und explizite Injection-Tokens werden ausgelesen,
   um Provider aus dem IoC-Container aufzulösen.

2. **Routing**
   `@Controller()` und `@Get()/@Post()` speichern Pfad- und Methodenmetadaten,
   die zur Registrierung von Route-Handlern genutzt werden.

3. **Guards, Pipes, Interceptors, Filters**
   Metadaten auf Methoden-/Klassenebene steuern, welche
   Querschnittskomponenten angewendet werden.

4. **Benutzerdefinierte Autorisierungsannotation**
   Decorators wie `@Roles('admin')` speichern Metadaten, die später von Guards
   ausgelesen werden.

#### Minimales Beispiel (Custom Metadata + Read)

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

#### Nest-spezifischer Hinweis

In realen NestJS-Apps nutzt man üblicherweise:
1. `SetMetadata()` zum Schreiben von Metadaten.
2. Den `Reflector`-Service in Guards/Interceptors zum sicheren Auslesen.

Diese Abstraktion hält den Code framework-konform und testbarer als direkte,
manuelle `Reflect.getMetadata(...)`-Aufrufe an vielen Stellen.

</details>

<details>
<summary>7. Wie erstellt man einen benutzerdefinierten Decorator in NestJS? (createParamDecorator, SetMetadata)</summary>

#### NestJS

In NestJS werden benutzerdefinierte Decorators meist auf zwei Arten erstellt:
1. **`SetMetadata()`** zum Anhängen eigener Metadaten an Routen/Klassen.
2. **`createParamDecorator()`** zum Extrahieren eigener Werte aus dem Request-Kontext.

Diese beiden Patterns decken die meisten Praxisfälle ab: Autorisierungsmarker und
requestbasierte Parameter.

#### 1) Custom-Metadata-Decorator mit `SetMetadata`

Nutze dies, wenn du Handler/Klassen mit Daten annotieren willst, die Guards oder
Interceptors später auslesen.

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Verwendung:

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

Guard liest Metadaten über `Reflector`:

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

#### 2) Benutzerdefinierter Parameter-Decorator mit `createParamDecorator`

Nutze dies für saubere Controller-Signaturen und wiederverwendbares Request-Parsen.

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

Verwendung:

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

#### Best Practices

1. Decorators schlank halten; Business-Logik in Guards/Services platzieren.
2. Konstanten für Metadaten-Keys verwenden (keine Magic Strings).
3. `Reflector.getAllAndOverride()` für Merging von Klassen- und Methodenmetadaten
   bevorzugen.
4. Ausgabe des Parameter-Decorators typisieren, um Controller-Verträge explizit
   zu halten.

</details>

<details>
<summary>8. Was macht @Injectable() und warum wird es benötigt?</summary>

#### NestJS

`@Injectable()` markiert eine Klasse als Provider, der an der NestJS
Dependency Injection (DI) teilnehmen kann. Mit anderen Worten: Es sagt Nest, dass
diese Klasse vom IoC-Container verwaltet wird und Abhängigkeiten über den
Konstruktor injiziert bekommen kann.

#### Was `@Injectable()` macht

1. **Registriert DI-Metadaten**
   Es ermöglicht Nest, die Klasse als injizierbaren Provider zu behandeln.

2. **Erlaubt Konstruktor-Injection**
   Nest kann die im Konstruktor deklarierten Abhängigkeiten auflösen und
   injizieren.

3. **Integriert Scope/Lifecycle von Providern**
   Die Klasse kann bei Konfiguration `DEFAULT`, `REQUEST` oder `TRANSIENT`
   gescoped sein.

4. **Verbessert Testbarkeit**
   Injektierbare Services lassen sich in Testing-Modulen leicht ersetzen/mocken.

#### Warum es benötigt wird

1. **Entkopplung**
   Controller hängen von Abstraktionen/Services ab, statt Abhängigkeiten manuell
   zu instanziieren.

2. **Single Responsibility**
   Business-Logik liegt in Services, nicht in Controllern.

3. **Zentrale Objekterstellung**
   Der Nest-Container steuert Instanziierung, Sharing und Lifecycle-Verhalten.

4. **Skalierbare Architektur**
   DI-Patterns bleiben wartbar, wenn App- und Teamgröße wachsen.

#### Beispiel

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

#### Praktische Nuance

`@Injectable()` allein reicht nicht; der Provider muss zusätzlich in einem Modul
registriert sein (`providers`-Array) oder über Modulgrenzen exportiert/importiert
werden, damit Nest ihn dort auflösen kann, wo er benötigt wird.

</details>

<details>
<summary>9. Was ist der Unterschied zwischen @Controller und @Get()/@Post()-Decorators?</summary>

#### NestJS

`@Controller` und Methoden-Decorators für Routen (`@Get`, `@Post` usw.) arbeiten
zusammen, lösen aber unterschiedliche Routing-Ebenen.

#### Hauptunterschied

1. **`@Controller()`**
   Deklariert eine Klasse als Controller und definiert ein
   **Basisrouten-Präfix** für alle Handler in dieser Klasse.

2. **`@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`**
   Mappen eine konkrete Klassenmethode auf HTTP-Methode + Routenpfad.

#### Mentales Modell

1. `@Controller('users')` bedeutet: „Alle Endpunkte in dieser Klasse beginnen
   mit `/users`.“
2. `@Get(':id')` bedeutet: „Diese Methode behandelt `GET /users/:id`.“

#### Beispiel

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

Aufgelöste Routen:
1. `GET /users`
2. `GET /users/:id`
3. `POST /users`

#### Warum diese Trennung nützlich ist

1. **Klare API-Struktur**
   Die Klasse gruppiert verwandte Endpunkte nach Domäne/Ressource.

2. **Wiederverwendbare Controller-Level-Konfiguration**
   Guards, Interceptors, Versionierung und Präfixe lassen sich auf Klassenebene
   anwenden.

3. **Lesbare Routing-Schicht**
   Methoden-Decorators machen die Endpunkt-Intention explizit und schnell
   erfassbar.

</details>

<details>
<summary>10. Wie verarbeitet NestJS HTTP-Requests und wie bestimmt es, welcher Controller aufgerufen wird?</summary>

#### NestJS

NestJS bestimmt den Ziel-Controller und Handler über Metadaten, die beim
Application-Bootstrap aus Decorators gesammelt werden, und führt den Request dann
durch eine definierte Pipeline aus.

#### Wie Routing beim Start aufgebaut wird

1. **Modul-Scan**
   Nest scannt importierte Module und entdeckt registrierte Controller/Provider.

2. **Sammeln von Routen-Metadaten**
   `@Controller()` liefert den Basispfad; `@Get/@Post/...` liefern HTTP-Methode
   und Subpfad.

3. **Routenregistrierung im Adapter**
   Nest kombiniert Metadaten zu konkreten Routen und registriert sie im
   Express- oder Fastify-Router.

#### Was pro eingehendem Request passiert

1. Request gelangt in den zugrunde liegenden HTTP-Adapter (Express/Fastify).
2. Der Router matched Methode + URL-Pfad auf eine Controller-Methode.
3. Nest erstellt ein `ExecutionContext` für diesen Handler.
4. Die Request-Pipeline läuft in folgender Reihenfolge:
   1. Middleware (falls konfiguriert)
   2. Guards (Autorisierungsentscheidung)
   3. Interceptors (vor dem Handler)
   4. Pipes (Parameter-Parsing/Validierung)
   5. Ausführung der Controller-Methode
   6. Interceptors (nach dem Handler, Response-Mapping)
   7. Exception Filters (falls Fehler geworfen werden)
5. Die finale Response wird vom Adapter zurückgegeben.

#### Wie Nest die exakte Controller-Methode auswählt

1. Match nach HTTP-Methode (`GET`, `POST` usw.).
2. Match nach normalisiertem vollständigem Routenpfad:
   `globalPrefix + controllerPath + handlerPath`.
3. Falls Versionierung aktiv ist, werden Versions-Constraints ausgewertet.
4. Falls Routenparameter existieren (`:id`), wird Param-Pattern-Matching angewendet.

#### Beispiel-Mapping

```ts
@Controller('users')
export class UsersController {
  @Get(':id')
  findOne() {}
}
```

Wenn das globale Präfix `api` ist, wird `GET /api/users/42` auf
`UsersController.findOne` gemappt.

#### Praktisches Fazit

NestJS „sucht Controller nicht dynamisch“ bei jedem Request. Es berechnet die
Routing-Map beim Bootstrap vor und führt danach einen vorhersehbaren
Request-Lifecycle um den gematchten Handler aus.

</details>

<details>
<summary>11. Wie verwendet NestJS Decorators zum Aufbau der Routing-Schicht?</summary>

#### NestJS

Das Routing in NestJS ist metadatengesteuert. Decorators annotieren Klassen und
Methoden, und Nest liest diese Metadaten beim Bootstrap aus, um im zugrunde
liegenden HTTP-Adapter eine konkrete Routing-Map zu erzeugen.

#### Quellen der Routing-Metadaten

1. **`@Controller(path)`**
   Definiert ein Prefix auf Controller-Ebene (Resource-Namespace).

2. **Methoden-Decorators**
   `@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`, `@Options()`,
   `@Head()`, `@All()` definieren HTTP-Methode + Handler-Pfad.

3. **Parameter-Decorators**
   `@Param()`, `@Query()`, `@Body()`, `@Headers()`, `@Req()`, `@Res()` legen
   fest, wie Request-Daten in Handler-Argumente injiziert werden.

4. **Querschnitts-Decorators**
   `@UseGuards()`, `@UsePipes()`, `@UseInterceptors()`, `@UseFilters()` hängen
   Ausführungsverhalten an Route/Klasse.

#### Wie Nest Routen aufbaut

1. Module scannen und Controller entdecken.
2. Controller- und Methoden-Metadaten per Reflection auslesen.
3. Vollständigen Pfad zusammensetzen:
   `globalPrefix + controllerPath + methodPath`.
4. Kompilierte Handler im Express/Fastify-Router registrieren.
5. Handler mit Guard-/Pipe-/Interceptor-/Filter-Pipeline umhüllen.

#### Beispiel

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

Aufgelöste Routing-Intention:
1. `GET /users/:id` -> `getById`
2. `POST /users` -> `create` (guard-protected)

#### Warum dieses Design stark ist

1. **Deklarativ und lokal**
   Routing-Regeln liegen nahe am Handler-Code.

2. **Kombinierbar**
   Decorators auf Klassen- und Methodenebene lassen sich natürlich kombinieren.

3. **Framework-Konsistenz**
   Dasselbe Pattern gilt für REST, GraphQL-Resolver und Microservice-Handler
   (mit transportspezifischen Decorators).

</details>

<details>
<summary>12. Was ist der Unterschied zwischen imports, exports, providers und declarations in @Module?</summary>

#### NestJS

In NestJS-Modulen sind `imports`, `providers` und `exports` die zentralen
Sichtbarkeits- und Abhängigkeitsgrenzen. `declarations` ist **kein** Feld von
NestJS-Modulen (es ist ein Angular-Konzept), daher ist die Nutzung in
`@Module()` falsch.

#### Korrekte Modul-Felder

1. **`providers`**
   Klassen/Factories/Values, die im DI-Kontext dieses Moduls erzeugt werden.
   Sie sind standardmäßig innerhalb desselben Moduls verfügbar.

2. **`imports`**
   Andere Module, deren **exportierte Provider** du in diesem Modul verwenden
   möchtest. Beim Import werden nicht alle internen Provider sichtbar, sondern
   nur die exportierten.

3. **`exports`**
   Teilmenge der Provider dieses Moduls (oder re-exportierte Module), die für
   importierende Module sichtbar sein sollen.

4. **`controllers`**
   Route-Handler, die diesem Modul gehören (HTTP-Schicht). Sie werden
   standardmäßig nicht als injizierbare Provider exportiert.

#### Zu `declarations`

1. `declarations` wird in Angular NgModules für Components/Directives/Pipes
   verwendet.
2. NestJS `@Module()` unterstützt `declarations` **nicht**.
3. NestJS-Äquivalente sind meist `controllers` + `providers`, je nach Rolle.

#### Beispiel

```ts
import { Module } from '@nestjs/common';

@Module({
  providers: [UsersService],     // im Kontext von UsersModule erstellt
  exports: [UsersService],       // für importierende Module verfügbar gemacht
})
export class UsersModule {}

@Module({
  imports: [UsersModule],        // kann nun exportierten UsersService injizieren
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Praktische Faustregel

1. Service-/Repository-/Factory-Klassen in `providers`.
2. Route-Handler in `controllers`.
3. Benötigte externe Module in `imports`.
4. In `exports` nur wiederverwendbare API-Oberfläche aufnehmen
   (Over-Exporting vermeiden).

</details>

<details>
<summary>13. Was ist der Unterschied zwischen @Module imports und @Module providers?</summary>

#### NestJS

`imports` und `providers` in `@Module()` lösen unterschiedliche DI-Aufgaben:
1. `imports` verbindet Module.
2. `providers` definiert, was dieses Modul in seinem eigenen DI-Scope erzeugt.

#### `providers`: lokale Definitionen

1. Deklariert Services/Factories/Values, die im Kontext dieses Moduls instanziiert werden.
2. Innerhalb dieses Moduls für Injection verfügbar.
3. Für andere Module nicht sichtbar, außer sie werden explizit exportiert.

Beispiel:

```ts
@Module({
  providers: [UsersService],
})
export class UsersModule {}
```

#### `imports`: externe Abhängigkeiten

1. Bindet andere Module ein, um deren **exportierte** Provider zu nutzen.
2. Kopiert nicht alle internen Bestandteile des importierten Moduls.
3. Erstellt einen expliziten Modul-Abhängigkeitsgraphen.

Beispiel:

```ts
@Module({
  imports: [UsersModule], // kann nur exportiertes aus UsersModule injizieren
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Kombiniertes Beispiel mit exports

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

#### Praktische Unterscheidung

1. Zu `providers` hinzufügen, wenn du die Abhängigkeit hier **besitzt und erzeugst**.
2. Zu `imports` hinzufügen, wenn die Abhängigkeit **einem anderen Modul gehört**
   und exportiert wird.
3. Falls Injection fehlschlägt, prüfen:
   1. Provider ist im Quellmodul in `providers` registriert.
   2. Quellmodul exportiert ihn in `exports`.
   3. Konsumentenmodul enthält das Quellmodul in `imports`.

</details>

<details>
<summary>14. Was sind dynamische Module und wann sollte man sie verwenden?</summary>

#### NestJS

Dynamische Module sind Module, deren Konfiguration zur Laufzeit über statische
Factory-Methoden erzeugt wird (typisch `forRoot`, `forRootAsync`, `register`,
`registerAsync`). Damit lassen sich wiederverwendbare Module bauen, die je nach
App/Umgebung unterschiedlich konfiguriert werden können.

#### Warum es dynamische Module gibt

1. **Runtime-Konfiguration**
   Optionen (URLs, API-Keys, Feature-Flags, Strategie-Auswahl) beim Import eines
   Moduls übergeben.

2. **Wiederverwendbare Bibliotheksmodule**
   Ein Modul paketieren, das von vielen Apps mit unterschiedlichen Einstellungen
   genutzt werden kann.

3. **Asynchrone Initialisierung**
   Konfiguration aus `ConfigService`, Secret-Managern oder Remote-Quellen auflösen.

4. **Bedingte Provider**
   Provider anhand von Optionen erzeugen (z. B. Redis vs In-Memory-Cache).

#### Typische API-Patterns

1. `forRoot(options)` für app-weite Singleton-Konfiguration.
2. `forRootAsync({...})`, wenn Konfiguration von asynchronen Factories/injizierten
   Abhängigkeiten abhängt.
3. `register(options)` für feature-scoped/per-import Konfiguration.

#### Beispiel

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

Verwendung:

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

#### Wann du dynamische Module verwenden solltest

1. Beim Bau geteilter Infrastruktur-Module (DB, Mail, Cache, Queue, Auth-Clients).
2. Wenn umgebungs- oder mandantenspezifisches Setup benötigt wird.
3. Wenn asynchrones Bootstrapping mit `ConfigModule` und injizierten Factories nötig ist.

#### Wann sie nicht nötig sind

1. Bei statischer, app-lokaler Konfiguration sind normale Module einfacher.
2. Wenn nur ein einzelner Provider variabel sein muss, reicht oft ein
   Factory-Provider.

</details>

<details>
<summary>15. Was ist der Unterschied zwischen Provider-Typen in NestJS? (useClass, useValue, useFactory)</summary>

#### NestJS

Provider in NestJS können mit unterschiedlichen Strategien registriert werden –
abhängig davon, wie eine Instanz/ein Wert erzeugt werden soll. Die häufigsten
Varianten sind `useClass`, `useValue` und `useFactory`.

#### 1) `useClass`

Erzeugt eine Instanz einer Klasse über Nest DI.

1. Gut für Standard-Service-Implementierungen.
2. Unterstützt Konstruktor-Injection automatisch.
3. Nützlich, um Implementierungen je nach Umgebung auszutauschen.

```ts
{
  provide: PaymentPort,
  useClass: StripePaymentService,
}
```

#### 2) `useValue`

Bindet ein Token an einen bereits vorhandenen Value/Objekt/Konstante.

1. Keine Instanziierung durch Nest.
2. Gut für Konfigurationsobjekte, SDK-Singletons, Mocks in Tests.
3. Schnell und einfach, aber ohne DI-Lifecycle für diesen Wert.

```ts
{
  provide: 'APP_CONFIG',
  useValue: { region: 'eu', retries: 3 },
}
```

#### 3) `useFactory`

Erzeugt den Provider-Wert über eine Factory-Funktion.

1. Kann Objekt dynamisch berechnen.
2. Kann andere Provider in die Factory injizieren (`inject`-Array).
3. Funktioniert für synchrone und asynchrone Initialisierung.

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

#### Schneller Vergleich

1. **`useClass`**: „Instanziiere diese Klasse per DI.“
2. **`useValue`**: „Nutze genau diesen Wert unverändert.“
3. **`useFactory`**: „Baue den Wert mit eigener Logik (und optional injizierten Dependencies).“

#### Wann welche Variante wählen

1. `useClass` für normale App-Services und polymorphe Implementierungen.
2. `useValue` für Konstanten, Third-Party-Instanzen und Test-Doubles.
3. `useFactory` für bedingte/asynchrone Erzeugung und komplexes Setup.

#### Praktischer Hinweis

Alle drei Strategien werden über ein **Token** (`provide`) aufgelöst. Gutes
Token-Design (Klassen-Token, Symbol oder String-Konstante) ist entscheidend für
wartbares DI.

</details>

<details>
<summary>16. Was ist der Provider-Scope? (DEFAULT, REQUEST, TRANSIENT)</summary>

#### NestJS

Der Provider-Scope in NestJS definiert, **wie lange Provider-Instanzen leben**
und **wie oft neue Instanzen** durch den DI-Container erzeugt werden.

#### Scope-Typen

1. **`DEFAULT` (Singleton)**
   Eine gemeinsame Instanz für den gesamten Lebenszyklus der Anwendung.

2. **`REQUEST`**
   Neue Instanz pro eingehendem Request (HTTP/RPC/Message-Kontext).

3. **`TRANSIENT`**
   Neue Instanz jedes Mal, wenn der Provider injiziert/aufgelöst wird.

#### 1) `DEFAULT`-Scope

1. Am performantesten und am häufigsten verwendet.
2. Ideal für zustandslose Services (Business-Logik, Repositories, Mapper).
3. Gemeinsamer Zustand in so einem Service ist pro App-Prozess global.

```ts
@Injectable()
export class UsersService {}
```

#### 2) `REQUEST`-Scope

1. Verwenden, wenn der Service request-aware sein muss
   (Tenant, Correlation ID, per-request Cache, User-Kontext).
2. Erhöht den Overhead bei der Objekterzeugung.
3. Wenn ein Singleton von einem request-scoped Provider abhängt, kann der
   Abhängigkeitsgraph Scope-Propagation-Anpassungen benötigen.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.REQUEST })
export class RequestContextService {}
```

#### 3) `TRANSIENT`-Scope

1. Frische Instanz an jedem Injection-Point.
2. Nützlich für leichte, zustandsbehaftete Helper, bei denen eine geteilte
   Instanz unerwünscht ist.
3. Kann teuer werden, wenn in tiefen Objektgraphen übermäßig genutzt.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.TRANSIENT })
export class AuditBuilder {}
```

#### Praktischer Entscheidungsleitfaden

1. Mit `DEFAULT` starten.
2. Zu `REQUEST` nur wechseln, wenn echter per-request Zustand nötig ist.
3. `TRANSIENT` für eng begrenzte, mutable Helper-Objekte verwenden.

#### Performance- und Architekturhinweis

Scope ist sowohl eine Korrektheits- als auch eine Performance-Entscheidung.
Übermäßiger Einsatz nicht-Singleton Scopes kann Latenz und Memory-Churn erhöhen,
daher bewusst einsetzen.

</details>

<details>
<summary>17. Wie geht man in großen Systemen mit zirkulären Abhängigkeiten (forwardRef) um?</summary>

#### NestJS

Zirkuläre Abhängigkeiten entstehen, wenn zwei Provider/Module direkt oder über
eine Kette voneinander abhängen. In NestJS ist der erste Lösungsansatz
architektonische Entkopplung; `forwardRef()` ist ein taktisches Mittel, wenn ein
Refactoring nicht sofort möglich ist.

#### Warum zirkuläre Abhängigkeiten riskant sind

1. Enge Kopplung zwischen Domänen.
2. Erschwertes Testen und Refactoring.
3. Unklare Ownership-Grenzen.
4. Komplexität beim Bootstrapping/bei DI-Auflösung.

#### Bevorzugte Strategie: den Zyklus entfernen

1. **Gemeinsame Logik extrahieren**
   Gemeinsames Verhalten in einen dritten Service/ein drittes Modul auslagern
   (`SharedDomainService`).

2. **Von Abstraktions-Tokens abhängen**
   Direkte Klassenabhängigkeit durch Interface-ähnliches Token + Adapter ersetzen.

3. **Domain Events / asynchrones Messaging**
   Event aus A publizieren, in B verarbeiten – statt direkter Aufrufkette.

4. **Modulgrenzen neu schneiden**
   Nach Use-Case/Domäne reorganisieren, sodass eine eindeutige
   Abhängigkeitsrichtung erhalten bleibt.

#### `forwardRef()` für unvermeidbare Fälle

`forwardRef()` verwenden, wenn zwei Provider/Module sich bei der DI-Auflösung
gegenseitig referenzieren müssen.

Beispiel auf Provider-Ebene:

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

Beispiel auf Modul-Ebene:

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

#### Hinweise für große Systeme

1. `forwardRef()` als temporäre Edge-Case-Lösung behandeln, nicht als Standarddesign.
2. Zirkuläre Dependencies im Architektur-Review nachverfolgen und schrittweise entfernen.
3. Vor Refactoring Tests um zykluskritische Flows ergänzen.
4. Bevorzugt unidirektionale Abhängigkeitsgraphen zwischen Bounded Contexts.

</details>

<details>
<summary>18. Wie strukturiert man eine skalierbare NestJS-Anwendung?</summary>

#### NestJS

Eine skalierbare NestJS-Anwendung wird um klare Domänengrenzen,
Abhängigkeitsrichtungen und vorhersehbare Querschnittsmuster herum aufgebaut.

#### Zentrale Strukturprinzipien

1. **Modular nach Domäne (Bounded Contexts)**
   Nach Business-Fähigkeiten aufteilen (`Users`, `Billing`, `Orders`), nicht nur
   nach technischen Schichten.

2. **Geschichtete Verantwortlichkeiten innerhalb jedes Moduls**
   Controller schlank halten, Services auf Orchestrierung fokussieren und
   Infrastruktur-Adapter isolieren.

3. **Abhängigkeitsregel**
   Höherstufige Business-Logik darf nicht direkt von
   Framework-/Infrastrukturdetails abhängen.

4. **Explizite Verträge**
   DTOs, Validierungsschemas und Interfaces/Tokens für klare Grenzen verwenden.

#### Praktisches Modul-Layout (Beispiel)

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

#### Architektur-Patterns, die skalieren

1. **Feature-Module + Shared Kernel**
   Gemeinsame Utilities minimal halten, um ein „God Common Module“ zu vermeiden.

2. **Ports and Adapters**
   Die Business-Schicht hängt von Abstraktionen ab; Adapter implementieren
   DB/API/Message-Bus-Details.

3. **CQRS dort, wo die Komplexität es rechtfertigt**
   Write-/Read-Modelle für komplexe Domänen trennen, nicht pauschal überall.

4. **Asynchrone Grenzen**
   Events/Queues für modulübergreifende Workflows und eventual consistency nutzen.

#### Operative Skalierungsaspekte

1. **Konfigurationsmanagement**
   Zentralisierte typisierte Konfiguration mit Environment-Validierung.

2. **Observability**
   Strukturiertes Logging, Tracing, Metriken und Correlation IDs.

3. **Fehlerstrategie**
   Globale Exception Filters + domänenspezifisches Error-Mapping.

4. **Performance**
   Caching, Pagination, Backpressure, DB-Indizierung und sparsamer Einsatz von
   Request Scope.

#### Team-Skalierungspraktiken

1. Lint/Format/Type/Test-Gates in CI erzwingen.
2. Modulverantwortung klar halten (Codeowners oder Service-Ownership-Map).
3. Architekturentscheidungen (ADRs) bei neuen domänenübergreifenden
   Abhängigkeiten reviewen.
4. Inkrementelles Refactoring statt Big-Bang-Umbauten bevorzugen.

#### Fazit

Skalierbarkeit in NestJS ist vor allem Architekturdiziplin: domänenorientierte
Module, kontrollierte Abhängigkeiten und standardisierte Plattform-Bausteine.

</details>

<details>
<summary>19. Wie entwirft man eine REST-API mit sauberer Trennung der Verantwortlichkeiten?</summary>

#### NestJS

Saubere Separation of Concerns in einer NestJS-REST-API bedeutet: Jede Schicht
hat eine einzelne, klare Verantwortung, und Abhängigkeiten fließen in eine
Richtung.

#### Empfohlene Verantwortungsaufteilung

1. **Controller-Schicht (Transport)**
   Kümmert sich nur um HTTP-Themen: Routing, Status-Codes,
   Request-/Response-Mapping, Auth-Decorators und Input-Binding.

2. **Application-/Service-Schicht (Use Cases)**
   Orchestriert Business-Workflows und Transaktionen; keine HTTP-spezifische
   Logik.

3. **Domain-Schicht (Business-Regeln)**
   Kapselt Kernregeln, Invarianten, Entities/Value Objects, Domain-Services.

4. **Infrastruktur-Schicht**
   Implementiert Persistence, externe APIs, Queues und andere Adapter.

#### Was NICHT vermischt werden sollte

1. Datenbankabfragen in Controllern.
2. HTTP-Objekte (`Request`, `Response`) in der Domain-Logik.
3. Validierung/Business-Invarianten, die über mehrere Schichten verstreut sind.
4. Externe SDK-Details, die in Use-Case-Verträge hineinleaken.

#### Praktischer Flow

1. Controller empfängt DTO (`@Body`, `@Query`, `@Param`).
2. Pipe validiert/transformiert DTO.
3. Controller ruft Methode des Application-Services auf.
4. Service verwendet Repositories/Ports und Domain-Regeln.
5. Service gibt Ergebnis-Modell zurück.
6. Controller mappt Ergebnis auf Response-DTO/View-Model.

#### Beispiel-Skelett

```ts
// controller
@Post()
create(@Body() dto: CreateOrderDto): Promise<OrderView> {
  return this.ordersAppService.createOrder(dto);
}

// application service
async createOrder(dto: CreateOrderDto): Promise<OrderView> {
  const order = Order.create(dto.customerId, dto.items); // domain rule
  await this.ordersRepo.save(order);                     // infrastructure port
  return OrderView.from(order);                          // output mapping
}
```

#### Design-Techniken, die helfen

1. **DTOs für API-Verträge**
   Input-/Output-Verträge von internen Entities trennen.

2. **Repository-/Port-Interfaces**
   Von Abstraktionen abhängen, nicht direkt von ORM-Clients in der
   Business-Schicht.

3. **Globale Querschnittskomponenten**
   Guards/Pipes/Interceptors/Filters für Auth, Validierung, Logging, Fehler nutzen.

4. **Versionierung und Idempotenz**
   API-Versionierungsstrategie und Idempotency Keys für unsichere Operationen anwenden.

5. **Konsistentes Fehlermodell**
   Domain-/Infrastrukturfehler auf stabile HTTP-Problem-Responses mappen.

#### Ergebnis

Mit dieser Trennung ist die API leichter zu testen, zu refactoren und zu
skalieren: Transportänderungen brechen die Domain-Logik nicht, und die
Infrastruktur kann sich unabhängig weiterentwickeln.

</details>

<details>
<summary>20. Wie sieht der vollständige Request-Lifecycle in NestJS aus?</summary>

#### NestJS

Der NestJS Request-Lifecycle ist eine deterministische Pipeline um einen
gematchten Route-Handler. Diese Reihenfolge zu verstehen ist entscheidend für das
Debugging von Authentifizierung, Validierung und Response-Shaping.

#### High-Level-Sequenz

1. Eingehender Request erreicht den Plattform-Adapter (Express/Fastify).
2. Die Route wird auf eine Controller-Methode gematcht.
3. Nest führt Framework-Pipeline-Komponenten in definierter Reihenfolge aus.
4. Response wird zurückgegeben (oder Exception wird durch Filters behandelt).

#### Detaillierte Lifecycle-Reihenfolge

1. **Middleware**
   Läuft vor Guards; für low-level Request-Vorverarbeitung
   (Logging, Correlation ID, Raw-Header-Manipulation usw.).

2. **Guards**
   Entscheiden, ob die Ausführung erlaubt ist (`canActivate`).
   Gibt ein Guard `false` zurück/throwt, endet der Request hier.

3. **Interceptors (vor dem Handler)**
   Umhüllen die Ausführung; können Timer starten, Kontext anhängen oder
   Verhalten kurzschließen.

4. **Pipes**
   Laufen auf Route-Argumenten zur Transformation/Validierung eingehender Daten
   (`@Body`, `@Param`, `@Query`, Custom-Params).

5. **Controller-Handler**
   Der Business-Use-Case wird ausgeführt (meist Delegation an die Service-Schicht).

6. **Interceptors (nach dem Handler)**
   Können Responses mappen/streamen/cachen und Observability-Logik finalisieren.

7. **Exception Filters**
   Fangen unbehandelte Exceptions und wandeln sie in HTTP-Responses um.

#### Visuelles Ausführungsmodell

1. Middleware -> Guards -> Interceptors (pre) -> Pipes -> Handler ->
   Interceptors (post) -> Response
2. Jeder geworfene Fehler in Pipeline/Handler -> Exception Filters

#### Hinweise zu Scope und Priorität

1. Die meisten Pipeline-Komponenten können auf folgenden Ebenen angewendet werden:
   1. Global
   2. Controller-Ebene
   3. Route-Handler-Ebene
2. Nest merged diese Ebenen; route-spezifische Konfiguration ist meist am
   spezifischsten.

#### Praktisches Debugging-Fazit

Wenn Verhalten unerwartet ist:
1. Prüfen, ob der Request zuerst vom Guard blockiert wird.
2. Pipe-Transformation/Validierung der Parameter verifizieren.
3. Interceptor-Kette auf Response-Mapping-Änderungen prüfen.
4. Exception-Filter-Formatierung für geworfene Fehler bestätigen.

Diese Reihenfolge zu kennen verhindert „magische“ Annahmen und beschleunigt die
Diagnose von Production-Incidents deutlich.

</details>

<details>
<summary>21. Was ist der Unterschied zwischen Middleware, Guards, Pipes und Interceptors?</summary>

#### NestJS

Diese vier NestJS-Komponenten nehmen alle an der Request-Verarbeitung teil,
haben aber unterschiedliche Verantwortlichkeiten und laufen in verschiedenen
Lifecycle-Phasen.

#### Schneller Rollenvergleich

1. **Middleware**
   HTTP-Vorverarbeitung vor Routing/Handler.

2. **Guards**
   Autorisierungs-Gate: entscheiden, ob der Request fortgesetzt werden darf.

3. **Pipes**
   Transformieren und validieren Handler-Argumente.

4. **Interceptors**
   Umhüllen die Handler-Ausführung vor/nachher und ermöglichen
   querschnittliche Response-Logik.

#### Tiefere Unterschiede nach Verantwortung

1. **Middleware**
   Am besten für generische Transport-Level-Aufgaben: Request-Logging,
   Correlation IDs, Header, Cookie-Parsing, Raw-Request-Mutation.

2. **Guards**
   Am besten für Auth/Authz-Entscheidungen: JWT-Prüfung, Rollenchecks,
   Policy-Checks.
   Geben `true/false` zurück (oder throwen), um Routen-Ausführung zu erlauben/zu
   verweigern.

3. **Pipes**
   Am besten für Input-Korrektheit: Parsing (`string -> number`), Validierung
   (DTO-Regeln), Sanitizing/Normalisierung auf Parameter-Ebene.

4. **Interceptors**
   Am besten für Execution-Wrapping: Response-Mapping, Caching, Timing-Metriken,
   Tracing, Timeout-/Retry-Wrapper, Stream-Handling.

#### Position im Lifecycle

1. Middleware
2. Guards
3. Interceptors (before)
4. Pipes
5. Handler
6. Interceptors (after)
7. Exception Filters (Error-Path)

#### Typische Beispiele

1. Middleware: `requestId` anhängen.
2. Guard: Request bei ungültigem Token ablehnen.
3. Pipe: `CreateUserDto` validieren.
4. Interceptor: Response-Envelope `{ data, meta }` transformieren.

#### Auswahl-Faustregel

1. Muss entschieden werden, **wer zugreifen darf**? -> Guard.
2. Muss **Input-Form/Typ** sichergestellt werden? -> Pipe.
3. Wird **Wrapping vor/nach dem Handler** benötigt? -> Interceptor.
4. Wird low-level HTTP-Vorverarbeitung außerhalb der Routen-Semantik benötigt? -> Middleware.

</details>

<details>
<summary>22. Wie wendet man Middleware global vs. für eine bestimmte Route an?</summary>

#### NestJS

In NestJS kann Middleware entweder global (für viele/alle Routen) oder selektiv
(bestimmte Controller/Routen) angewendet werden. Der Mechanismus unterscheidet
sich von Guards und Interceptors, weil Middleware über die Module-Consumer-API
oder den App-Bootstrap konfiguriert wird.

#### 1) Middleware global anwenden

Verwende dies, wenn Verhalten für fast jeden Request benötigt wird
(Request IDs, gemeinsames Logging, Bootstrap von Security-Headern usw.).

Globale Konfiguration auf Modul-Ebene:

```ts
import { MiddlewareConsumer, Module, NestModule } from '@nestjs/common';

@Module({})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer.apply(LoggerMiddleware).forRoutes('*');
  }
}
```

Du kannst auch alle Controller über klassenbasierte Patterns in
`forRoutes(...)` targeten.

#### 2) Middleware auf bestimmte Routen/Controller anwenden

Verwende dies nur für feature-spezifische Anforderungen.

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
        UsersController, // alle Routen im Controller
        { path: 'users/:id', method: RequestMethod.PATCH }, // exakte Route
      );
  }
}
```

#### Routen ausschließen

Du kannst breite Middleware anhängen und sensible/öffentliche Endpunkte
ausschließen:

```ts
consumer
  .apply(AuthMiddleware)
  .exclude(
    { path: 'health', method: RequestMethod.GET },
    { path: 'auth/login', method: RequestMethod.POST },
  )
  .forRoutes('*');
```

#### Praktische Hinweise

1. Globale Middleware nur für wirklich querschnittliche Anforderungen verwenden.
2. Middleware leichtgewichtig halten; schwere Authz-Logik gehört in Guards.
3. Routen-spezifische Middleware für klar abgegrenztes Feature-Verhalten nutzen.
4. Wenn DI-lastige Business-Prüfungen nötig sind, Logik von Middleware in Guards
   oder Interceptors verschieben.

</details>

<details>
<summary>23. Was ist `ExecutionContext` und wie wird er verwendet?</summary>

#### NestJS

`ExecutionContext` ist eine NestJS-Abstraktion, die die aktuelle
Handler-Ausführungsumgebung beschreibt. Sie erweitert `ArgumentsHost` und gibt
Framework-Komponenten (Guards, Interceptors, Filters, Custom Decorators) einen
einheitlichen Weg, auf request-spezifische Daten über unterschiedliche
Transporte hinweg zuzugreifen.

#### Warum `ExecutionContext` existiert

1. **Transport-agnostischer Zugriff**
   Dasselbe API-Muster funktioniert für HTTP, WebSockets und Microservices.

2. **Handler-/Klassen-Introspektion**
   Du kannst prüfen, welche Controller-Klasse und Methode ausgeführt werden.

3. **Konsistenz für Querschnittskomponenten**
   Guards/Interceptors/Filters können mit einem gemeinsamen Kontextmodell arbeiten.

#### Wichtige APIs

1. `context.getType()`
   Gibt den Ausführungstyp zurück (`http`, `ws`, `rpc`).

2. `context.switchToHttp()`
   Bietet Zugriff auf `getRequest()`, `getResponse()`, `getNext()`.

3. `context.switchToWs()` / `context.switchToRpc()`
   Zugriff auf protokollspezifische Daten für WebSockets/Microservices.

4. `context.getClass()` und `context.getHandler()`
   Liefert aktuelle Controller-Klasse und Methoden-Referenz.

#### Häufige Verwendung in einem Guard

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

#### Häufige Verwendung mit Metadaten + Reflector

```ts
const isPublic = this.reflector.getAllAndOverride<boolean>('isPublic', [
  context.getHandler(),
  context.getClass(),
]);
```

Dieses Muster liest Routen-/Klassen-Metadaten (z. B. `@Public()`, `@Roles(...)`)
und wird häufig in Autorisierungs-Guards genutzt.

#### Praktischer Kernpunkt

Sieh `ExecutionContext` als Runtime-Umschlag des Frameworks für den aktuellen
Endpoint-Aufruf: Er zeigt dir **wo du bist** (Handler/Klasse/Transport) und
ermöglicht sicheren Zugriff auf transportspezifische Request-Daten.

</details>

<details>
<summary>24. Was ist ein Guard und wie unterscheidet er sich von Middleware?</summary>

#### NestJS

Ein **Guard** in NestJS ist eine Klasse, die `CanActivate` implementiert und
entscheidet, ob die aktuelle Anfrage einen Route-Handler erreichen darf.

#### Was ein Guard macht

1. Läuft vor der Handler-Ausführung.
2. Gibt `true` zurück, um zu erlauben, `false` (oder wirft) zum Ablehnen.
3. Hat Zugriff auf `ExecutionContext` (Handler, Controller, Transport, Request).
4. Wird häufig für Authentifizierung und Autorisierung verwendet.

#### Unterschied Guard vs. Middleware

1. **Zweck der Entscheidung**
   Guard ist ein explizites Autorisierungs-Gate.
   Middleware ist generische Request-Vorverarbeitung.

2. **Framework-Bewusstsein**
   Guard kennt den Ziel-Handler/die Klasse über `ExecutionContext`.
   Middleware hat meist keinen Zugriff auf Route-Handler-Metadaten.

3. **Position im Lifecycle**
   Middleware läuft früher.
   Guard läuft nach Middleware, vor Pipes/Interceptors/Handler.

4. **Typische Anwendungsfälle**
   Guard: JWT/Rollen/Policies.
   Middleware: Logging, Request-IDs, Header-Normalisierung, rohe Request-Mutation.

#### Beispiel-Guard

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

#### Faustregel

1. Es muss entschieden werden: „Darf dieser User auf diese Route zugreifen?“ -> **Guard**.
2. Es wird low-level HTTP-Preprocessing unabhängig von Routen-Semantik benötigt -> **Middleware**.

</details>

<details>
<summary>25. Wie integrieren sich Guards in die Autorisierung?</summary>

#### NestJS

Guards sind in NestJS das zentrale Autorisierungs-Gate. Sie prüfen, ob der
aktuell authentifizierte Principal auf eine bestimmte Route zugreifen darf –
meist durch Kombination aus Request-Identität und Route-Metadaten (Rollen,
Policies, Berechtigungen).

#### Typischer Autorisierungsablauf mit Guards

1. **Authentifizierungsschritt**
   Ein vorgelagerter Guard (oder eine Passport-Strategie) validiert Token/Session
   und hängt `request.user` an.

2. **Metadaten-Deklaration an der Route**
   Die Route erhält Anforderungen, z. B. `@Roles('admin')` oder Policy-Keys.

3. **Auswertung durch Autorisierungs-Guard**
   Der Guard liest Metadaten über `Reflector`, liest `request.user` und trifft
   die Zugriffsentscheidung.

4. **Erlauben oder verweigern**
   Rückgabe `true` zum Fortfahren, sonst `false` oder `ForbiddenException`.

#### Rollenbasiertes Beispiel (RBAC)

Roles-Decorator:

```ts
import { SetMetadata } from '@nestjs/common';
export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Guard:

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

Verwendung:

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Integrationsmuster in realen Systemen

1. **Gestapelte Guards**
   `JwtAuthGuard` (Identität) + `Roles/PoliciesGuard` (Autorisierungslogik).

2. **ABAC/Policy-Engine**
   Der Guard delegiert Entscheidungen an einen Policy-Service
   (Subject, Action, Resource).

3. **Kontextabhängige Prüfungen**
   Guard liest Route-Parameter/Ressourcen-Eigentümer und erzwingt
   Ownership-Regeln.

#### Best Practices

1. Guards schlank halten; schwere Logik in dedizierte Autorisierungs-Services
   auslagern.
2. Metadaten-Decorator für deklarative, auditierbare Zugriffsregeln nutzen.
3. Authentifizierungsfehler (`401`) klar von Autorisierungsfehlern (`403`) trennen.
4. Guards mit positiven und negativen Berechtigungsszenarien testen.

</details>
<details>
<summary>26. Was ist `@SetMetadata()` und wie arbeitet es mit Guards über `Reflector`?</summary>

#### NestJS

`@SetMetadata()` ist ein NestJS-Helper-Decorator, mit dem benutzerdefinierte
Metadaten an eine Klasse oder Methode angehängt werden. Guards können diese
Metadaten dann über `Reflector` lesen und Autorisierung oder anderes
routenspezifisches Verhalten durchsetzen.

#### Kernidee

1. `@SetMetadata(key, value)` schreibt Metadaten auf Route/Klasse.
2. Guard liest Metadaten zur Laufzeit per `Reflector`.
3. Guard entscheidet, ob die Anfrage erlaubt ist.

#### Warum dieses Muster wichtig ist

1. **Deklarative Zugriffsregeln**
   Berechtigungen sind direkt an Endpunkten sichtbar.

2. **Trennung der Verantwortlichkeiten**
   Controller deklarieren Absicht; Guards implementieren die Durchsetzung.

3. **Wiederverwendbarkeit**
   Ein Guard kann viele Routen mit unterschiedlichen Metadatenwerten behandeln.

#### Beispiel: Rollen-Metadaten

Decorator:

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Verwendung am Endpoint:

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

Guard, der Metadaten liest:

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(), // Methoden-Metadaten
      context.getClass(),   // Controller-Metadaten
    ]);

    if (!requiredRoles) return true;

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];
    return requiredRoles.some(role => userRoles.includes(role));
  }
}
```

#### `Reflector`-Methoden, die am häufigsten genutzt werden

1. `get(key, target)` -> liest Metadaten von einem spezifischen Ziel.
2. `getAllAndOverride(key, [handler, class])` -> Methoden-Metadaten überschreiben Klassen-Metadaten.
3. `getAllAndMerge(key, [handler, class])` -> kombiniert Werte aus beiden Ebenen.

#### Praktischer Kernpunkt

`@SetMetadata()` + `Reflector` ist der Standardmechanismus in NestJS, um
saubere, skalierbare, metadatengetriebene Autorisierung und Route-Verhalten
aufzubauen.

</details>

<details>
<summary>27. Wie implementiert man JWT-Authentifizierung über einen Guard?</summary>

#### NestJS

JWT-Authentifizierung in NestJS wird häufig mit einem Guard umgesetzt, der das
Token validiert und die User-Identität in den Request-Kontext schreibt.

#### Standard-Architektur

1. **AuthService**
   Signiert und verifiziert JWTs.

2. **JWT-Strategie/Guard**
   Extrahiert das Bearer-Token, validiert es und setzt `request.user`.

3. **Geschützte Routen**
   Verwenden `@UseGuards(...)`, um Authentifizierung zu erzwingen.

Du kannst das mit Passport (`@nestjs/passport`) oder mit einem Custom Guard
implementieren.

#### Minimaler Custom JWT Guard (ohne Passport)

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
      req.user = payload; // Identität für nachgelagerte Handler/Guards anhängen
      return true;
    } catch {
      throw new UnauthorizedException('Invalid or expired token');
    }
  }
}
```

#### Routen schützen

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

#### `JwtModule`-Setup

```ts
JwtModule.register({
  secret: process.env.JWT_ACCESS_SECRET,
  signOptions: { expiresIn: '15m' },
});
```

#### Best Practices für Production

1. Separate Secrets für Access- und Refresh-Token verwenden.
2. Access-Tokens kurzlebig halten.
3. Issuer/Audience/Algorithmus explizit validieren.
4. Bei Token-Fehlern `401 Unauthorized` verwenden.
5. Mit einem Autorisierungs-Guard (Rollen/Policies) für Berechtigungen kombinieren.
6. Falls nötig, Token-Revocation-Strategie ergänzen (Blacklist/Versionierung/Rotation).

#### Praktische Notiz

In größeren Anwendungen ist `AuthGuard('jwt')` mit Passport + `JwtStrategy`
häufig sauberer für Wiederverwendung und Ökosystem-Integration. Das Kernprinzip
bleibt gleich: extrahieren -> verifizieren -> User anhängen -> erlauben/ablehnen.

</details>
<details>
<summary>28. Wie implementiert man RBAC und ABAC in NestJS, und wann ist welcher Ansatz besser?</summary>

#### NestJS

RBAC und ABAC sind zwei Autorisierungsmodelle, die beide in NestJS mit Guards +
Metadaten + Autorisierungs-Services umgesetzt werden können.

#### RBAC vs ABAC

1. **RBAC (Role-Based Access Control)**
   Zugriff wird über User-Rollen vergeben (z. B. `admin`, `editor`, `viewer`).

2. **ABAC (Attribute-Based Access Control)**
   Zugriff wird durch Auswertung von Attributen entschieden (User, Resource,
   Action, Kontext): Ownership, Abteilung, Region, Status, Zeitfenster usw.

#### Wann welcher Ansatz besser ist

1. **RBAC** wählen, wenn:
   1. Das Berechtigungsmodell einfach und stabil ist.
   2. Die Rollen-Hierarchie klar ist.
   3. Schnelle Umsetzung und einfaches Auditing Priorität haben.

2. **ABAC** wählen, wenn:
   1. Regeln von Resource-Daten und Kontext abhängen.
   2. Feingranulare, dynamische Entscheidungen nötig sind.
   3. Multi-Tenant- oder Enterprise-Policy-Komplexität hoch ist.

3. In den meisten realen Systemen ein **hybrides RBAC + ABAC** nutzen:
   RBAC für groben Zugriff, ABAC für sensitive Operationen.

#### RBAC-Implementierungsmuster in NestJS

1. `@Roles(...)`-Decorator über `SetMetadata`.
2. `RolesGuard` liest Metadaten mit `Reflector`.
3. Guard vergleicht erforderliche Rollen mit `request.user.roles`.

```ts
export const Roles = (...roles: string[]) => SetMetadata('roles', roles);
```

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### ABAC-Implementierungsmuster in NestJS

1. Policy-Ability-Service definieren (`can(user, action, resource)`).
2. Im Guard Ziel-Resource (oder relevante Attribute) laden.
3. Policy auswerten und erlauben/ablehnen.

```ts
@Injectable()
export class PoliciesGuard implements CanActivate {
  constructor(private readonly policy: PolicyService) {}

  async canActivate(ctx: ExecutionContext): Promise<boolean> {
    const req = ctx.switchToHttp().getRequest();
    const user = req.user;
    const order = await req.orderLoader.load(req.params.id); // Beispiel
    return this.policy.can(user, 'update', order);
  }
}
```

#### Design-Best-Practices

1. Guard schlank halten; Regel-Logik in dedizierten Policy-Service auslagern.
2. Regeln nicht in Controllern hardcoden.
3. Policy-relevante Lookups, wenn sicher, cachen.
4. Für Autorisierungs-Ablehnungen `403 Forbidden` zurückgeben (nicht `401`).
5. Entscheidungs-Kontext für Auditierbarkeit in kritischen Domänen loggen.

#### Praktische Empfehlung

Mit RBAC für Baseline-Geschwindigkeit starten, dann ABAC in
High-Risk-/High-Variance-Flows ergänzen (Ownership-Checks, Datensensitivität,
Tenant-Grenzen, konditionale Aktionen).

</details>

<details>
<summary>29. Wie implementiert man Refresh-Token-Rotation und warum ist sie wichtig?</summary>

#### NestJS

Refresh-Token-Rotation bedeutet, bei jeder Refresh-Anfrage **ein neues
Refresh-Token auszustellen** und das vorherige zu invalidieren. Das reduziert
Replay-Risiken, falls ein Refresh-Token gestohlen wird.

#### Warum das wichtig ist

1. Begrenzt den Schaden durch geleakte Refresh-Tokens.
2. Erkennt Token-Reuse-Angriffe (gestohlenes altes Token wird erneut genutzt).
3. Ermöglicht sichere langlebige Sessions ohne langlebige Access-Tokens.
4. Verbessert Session-Kontrolle über mehrere Geräte.

#### Empfohlenes Token-Modell

1. **Access-Token**: kurze TTL (z. B. 5-15 Min), zustandsloses JWT.
2. **Refresh-Token**: längere TTL (Tage/Wochen), bei jeder Nutzung rotiert.
3. In der DB nur **gehashtes Refresh-Token** (oder Token-Family-Metadaten) speichern.
4. Token-Family/Session tracken (`sessionId`, `jti`, `rotatedFrom`, `revokedAt`).

#### Rotationsablauf in NestJS

1. User loggt sich ein -> Access + Refresh-Token (RT1) ausstellen, RT1-Hash + Metadaten speichern.
2. Client ruft `/auth/refresh` mit RT1 auf.
3. Server validiert Signatur/Ablauf und vergleicht Hash mit aktiv gespeichertem Token.
4. Wenn gültig:
   1. RT1 widerrufen.
   2. AT2 + RT2 ausstellen.
   3. RT2-Hash als aktives Token für diese Session speichern.
5. Wenn altes RT1 später erneut verwendet wird:
   1. Als verdächtigen Reuse markieren.
   2. Ganze Session/Token-Family widerrufen.
   3. Re-Authentifizierung erzwingen.

#### Minimales Service-Sketch

```ts
async rotateRefreshToken(userId: string, presentedRt: string, sessionId: string) {
  const session = await this.sessionsRepo.findById(sessionId);
  if (!session || session.revokedAt) throw new UnauthorizedException();

  const matches = await this.hash.compare(presentedRt, session.refreshTokenHash);
  if (!matches) {
    await this.sessionsRepo.revokeFamily(session.familyId); // Reuse-Detection-Reaktion
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

#### Hinweise zur NestJS-Implementierung

1. Eigene `JwtModule`-Config/Secrets für Access- vs Refresh-Token verwenden.
2. Refresh-Endpoint mit Refresh-Token-Guard/Strategie schützen.
3. Refresh-Token nach Möglichkeit in sicherem httpOnly-Cookie halten.
4. Device-/Session-Tabelle für Multi-Device-Logout und Widerruf ergänzen.

#### Security-Best-Practices

1. Refresh-Tokens im Ruhezustand hashen.
2. Refresh-Token an Session-/Geräte-Metadaten binden.
3. Bei jeder Refresh-Anfrage rotieren, ohne Ausnahmen.
4. Token-Family bei erkanntem Reuse widerrufen.
5. Rotations-/Reuse-Events für Incident-Monitoring loggen.

</details>

<details>
<summary>30. Was ist eine Pipe in NestJS und wann sollte man sie verwenden?</summary>

#### NestJS

Eine Pipe in NestJS ist eine Klasse, die `PipeTransform` implementiert und vor
 einem Route-Handler läuft, um eingehende Daten zu **transformieren** und/oder
 zu **validieren**.

#### Was Pipes machen

1. **Transformation**
   Rohwerte aus dem Transport in erwartete Typen umwandeln (z. B. String -> Zahl,
   String -> UUID-Objekt, Trimming/Normalisierung).

2. **Validierung**
   DTO-/Schema-Regeln durchsetzen und ungültige Eingaben früh ablehnen.

3. **Fail-fast-Verhalten**
   Eine Exception werfen (typisch `BadRequestException`), bevor Business-Logik läuft.

#### Wo Pipes im Lifecycle stehen

1. Middleware
2. Guards
3. Interceptors (pre)
4. **Pipes**
5. Handler
6. Interceptors (post)
7. Exception Filters

#### Beispiele für eingebaute Pipes

1. `ValidationPipe`
2. `ParseIntPipe`
3. `ParseBoolPipe`
4. `ParseUUIDPipe`
5. `DefaultValuePipe`
6. `ParseArrayPipe`

#### Verwendungsbeispiele

Auf Parameter-Ebene:

```ts
@Get(':id')
findOne(@Param('id', ParseIntPipe) id: number) {
  return this.usersService.findOne(id);
}
```

Globale Validierung:

```ts
app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
    forbidNonWhitelisted: true,
    transform: true,
  }),
);
```

#### Beispiel für eine Custom Pipe

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

#### Wann man Pipes verwenden sollte

1. Request-DTOs und Query-/Param-Payloads validieren.
2. Primitive Route-/Query-Parameter in typisierte Werte parsen.
3. Eingabe-Normalisierungsregeln zentralisieren.
4. Controller/Services von wiederholtem Validierungs-/Parsing-Code freihalten.

#### Faustregel

Pipes für **Input-Korrektheit**, Guards für **Zugriffskontrolle**, Interceptors
für **Execution-Wrapping** und Middleware für **low-level Request-Preprocessing** nutzen.

</details>

<details>
<summary>31. Was ist ein DTO?</summary>

#### NestJS

Ein DTO (Data Transfer Object) ist eine Objektstruktur zum Datentransfer über
Anwendungsgrenzen hinweg, meist zwischen Client und API-Layer.

In NestJS werden DTOs typischerweise als **Klassen** implementiert, um
Runtime-Validierung und -Transformation mit `class-validator` und
`class-transformer` zu unterstützen.

#### Warum DTOs wichtig sind

1. **Explizite API-Verträge**
   Definieren genau, welche Eingabe-/Ausgabefelder erlaubt sind.

2. **Validierungsgrenze**
   Lehnt fehlerhafte oder unsichere Payloads ab, bevor Business-Logik ausgeführt wird.

3. **Entkopplung**
   Verhindert, dass Domain-Entities/ORM-Modelle direkt nach außen exponiert werden.

4. **Wartbarkeit**
   Klare Request-/Response-Schemas machen Refactoring sicherer und Dokumentation einfacher.

#### Typische DTO-Typen in NestJS

1. **Request-DTOs**
   `CreateUserDto`, `UpdateUserDto`, Query-/Filter-DTOs.

2. **Response-/View-DTOs**
   Kontrollierte Output-Form (interne Felder wie Passwörter, Tokens, Flags ausblenden).

3. **Command-Style-DTOs**
   Inputs für spezifische Use-Cases (besonders in CQRS-orientierten Modulen).

#### Beispiel für ein Request-DTO

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

Verwendung im Controller:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Praktische Regeln

1. In Controllern niemals rohe `any`-Payloads verwenden.
2. DTOs transportfokussiert halten (nicht als vollständige Domain-Entities).
3. Input-DTOs von Output-DTOs trennen.
4. DTOs mit globaler `ValidationPipe` kombinieren für konsistente Durchsetzung.

</details>

<details>
<summary>32. Was ist der Unterschied zwischen Interface und Klasse für DTO-Typisierung — und warum wird in NestJS die Klasse bevorzugt?</summary>

#### NestJS

Sowohl Interfaces als auch Klassen können TypeScript-Strukturen beschreiben,
in NestJS werden DTOs jedoch meist als **Klassen** implementiert, weil
Nest-Validierung/-Transformation zur Laufzeit arbeitet, nicht nur zur Compile-Zeit.

#### Kerndifferenz

1. **Interface**
   Existiert nur zur TypeScript-Compile-Zeit; wird zur Laufzeit entfernt.

2. **Klasse**
   Existiert zur Laufzeit als reales Konstruktor-/Funktionsobjekt und kann
   Decorator-Metadaten tragen, die von Nest-Pipes und Tooling genutzt werden.

#### Warum in NestJS Klassen für DTOs bevorzugt werden

1. **Runtime-Validierungsunterstützung**
   `class-validator`-Decorators (`@IsEmail`, `@IsString` usw.) werden an
   Klassen-Properties gebunden und von `ValidationPipe` verwendet.

2. **Transformationsunterstützung**
   `class-transformer` kann rohe Payloads in Klasseninstanzen
   instanziieren/transformieren (`transform: true` in `ValidationPipe`).

3. **OpenAPI/Swagger-Integration**
   DTO-Klassen liefern Metadaten für Schema-Generierung mit `@nestjs/swagger`.

4. **Mapped-Types-Unterstützung**
   `PartialType`, `PickType`, `OmitType`, `IntersectionType` arbeiten auf Klassen.

#### Praktisches Beispiel

Interface (nur Typ, keine Runtime-Metadaten):

```ts
interface CreateUserDto {
  email: string;
}
```

Klassen-DTO (Runtime + Decorators):

```ts
import { IsEmail } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;
}
```

Mit globaler Validierung:

```ts
app.useGlobalPipes(new ValidationPipe({ whitelist: true, transform: true }));
```

Nur das klassenbasierte DTO kann über Decorator-Metadaten validiert und transformiert werden.

#### Wann Interfaces trotzdem nützlich sind

1. Interne Service-Verträge ohne Bedarf an Runtime-Reflection.
2. Generische Utility-Typisierung und Domain-Abstraktionen.
3. Read-only Compile-Time-Grenzen, wenn Validierung anderswo erfolgt.

#### Faustregel

**Klassen für externe API-DTOs** verwenden (Controller-Input-/Output-Verträge).
Interfaces für interne Compile-Time-Verträge nutzen, bei denen keine
Runtime-Metadaten benötigt werden.

</details>

<details>
<summary>33. Was sind Mapped Types in NestJS? (`PartialType`, `OmitType`, `PickType`, `IntersectionType`)</summary>

#### NestJS

Mapped Types in NestJS sind Utilities, die aus bestehenden DTO-Klassen neue
DTO-Klassen erzeugen. So wird Duplikation reduziert, während
Validierungs-/Swagger-Metadaten erhalten bleiben.

Sie werden typischerweise importiert aus:
1. `@nestjs/mapped-types` (framework-agnostische Nutzung)
2. `@nestjs/swagger` (bei Swagger- und Schema-Decorators)

#### Warum Mapped Types nützlich sind

1. Wiederholte DTO-Definitionen vermeiden.
2. `Create`-/`Update`-DTOs konsistent halten.
3. Decorator-Metadaten für Validierung/Doku erhalten.
4. API-Vertragsentwicklung sicherer machen.

#### Zentrale Mapped Types

1. **`PartialType(BaseDto)`**
   Macht alle Properties optional.
   Typischer Use-Case: `UpdateDto` aus `CreateDto`.

2. **`PickType(BaseDto, ['a', 'b'])`**
   Behält nur ausgewählte Properties.
   Typischer Use-Case: schlanker Input für einen fokussierten Endpoint.

3. **`OmitType(BaseDto, ['x'])`**
   Schließt ausgewählte Properties aus.
   Typischer Use-Case: verbotene Input-Felder wie `role`, `id` ausblenden.

4. **`IntersectionType(A, B)`**
   Kombiniert Properties aus zwei DTO-Klassen.
   Typischer Use-Case: zusammengesetzte Filter-/Pagination-/Query-DTOs.

#### Beispiel

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

#### Praktische Hinweise

1. Mapped Types arbeiten auf Klassen-Metadaten; das Basis-DTO sollte eine Klasse sein.
2. DTO-Vererbung lesbar halten; tiefe, verwirrende Ketten vermeiden.
3. Bei komplexen Intersections das generierte OpenAPI-Schema prüfen.

#### Faustregel

Mapped Types für Vertrags-Wiederverwendung nutzen, besonders `Create` -> `Update`,
dabei die DTO-Hierarchie einfach und explizit halten.

</details>

<details>
<summary>34. Wie implementiert man Validierung mit `class-validator` und Pipes?</summary>

#### NestJS

In NestJS wird Validierung meist so umgesetzt:
1. DTO-Klassen mit `class-validator`-Decorators.
2. `ValidationPipe` (global oder route-spezifisch), um Regeln zur Laufzeit durchzusetzen.

#### Schritt 1: DTO mit Validierungs-Decorators definieren

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

#### Schritt 2: `ValidationPipe` aktivieren

Globales Setup (empfohlen):

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

#### Was diese Optionen machen

1. `whitelist: true`
   Entfernt Properties, die nicht im DTO definiert sind.

2. `forbidNonWhitelisted: true`
   Wirft Fehler, wenn unbekannte Properties vorhanden sind.

3. `transform: true`
   Konvertiert Payload in DTO-Instanz und wendet Typtransformation an.

4. `enableImplicitConversion: true`
   Erlaubt sichere Primitive-Konvertierung anhand der DTO-Property-Typen.

#### Schritt 3: DTO im Controller verwenden

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Routen-spezifische Validierung (wenn nötig)

```ts
@Post('strict')
@UsePipes(new ValidationPipe({ whitelist: true, forbidNonWhitelisted: true }))
createStrict(@Body() dto: CreateUserDto) {}
```

#### Typische Validierungsfehler-Response

1. HTTP `400 Bad Request`
2. Message-Array mit fehlgeschlagenen Constraints
3. Klare Felddiagnostik für Client-Entwickler

#### Best Practices

1. DTOs pro Endpoint/Use-Case fokussiert halten.
2. `Create`-/`Update`-DTOs trennen (oft via `PartialType`).
3. Nicht nur auf Service-Validierung vertrauen, wenn Controller externe Daten annehmen.
4. `exceptionFactory` in `ValidationPipe` anpassen für konsistente API-Fehlerform.

</details>

<details>
<summary>35. Wie implementiert man einen globalen Exception Filter und eigene HTTP-Fehler?</summary>

#### NestJS

In NestJS zentralisiert ein globaler Exception Filter das Mapping von Fehlern zu
Responses, sodass alle unbehandelten Exceptions ein konsistentes API-Format
liefern.

Eigene HTTP-Fehler werden typischerweise durch Erweiterung von `HttpException`
oder durch eingebaute Exceptions (`BadRequestException`, `NotFoundException` usw.) erstellt.

#### 1) Globalen Exception Filter erstellen

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

#### 2) Filter global registrieren

In `main.ts`:

```ts
app.useGlobalFilters(new GlobalExceptionFilter());
```

#### 3) Eigene HTTP-Exception erstellen

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

Verwendung:

```ts
if (!canCloseOrder) {
  throw new BusinessRuleViolationException('Order cannot be closed in current state');
}
```

#### Warum dieser Ansatz gut ist

1. Konsistentes Response-Format über die gesamte API.
2. Sauberere Controller/Services (kein repetitives Try/Catch nur fürs Formatting).
3. Zentrale Observability-Hooks (Logging, Correlation IDs, Error Codes).
4. Domain-/Infrastrukturfehler lassen sich klar auf sinnvolle HTTP-Semantik mappen.

#### Best Practices

1. In Production keine internen Stacktraces in Responses leaken.
2. Maschinenlesbare Error Codes für Clients mitgeben.
3. Stacktraces in Logs erhalten (nicht zwingend im HTTP-Body).
4. Erwartete Business-Fehler auf 4xx, unerwartete Ausfälle auf 5xx mappen.

</details>

<details>
<summary>36. Wie behandelt man Fehler korrekt und liefert eine konsistente Response-Struktur zurück?</summary>

#### NestJS

Korrekte Fehlerbehandlung in NestJS bedeutet, klar zu trennen:
1. wo Fehler entstehen (Domain/Application/Infrastruktur),
2. wo Fehler nach HTTP übersetzt werden (Filter),
3. und wie Responses standardisiert werden (globaler Vertrag).

#### Empfohlene Strategie

1. **Aussagekräftige Exceptions im Business-Flow werfen**
   Domain-spezifische Exceptions oder passende `HttpException`-Subklassen nutzen.

2. **HTTP-Response-Formatting zentralisieren**
   Einen globalen Exception Filter verwenden, der ein einheitliches Fehler-Schema erzwingt.

3. **Auch Success-Responses standardisieren**
   Optional einen Interceptor für ein einheitliches Success-Envelope einsetzen.

4. **Observability erhalten**
   Fehlerkontext (requestId, path, userId, stack) zentral loggen.

#### Beispiel für eine konsistente Fehler-Response

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

#### Implementierungsbausteine

1. **Globaler Exception Filter**
   Mappt alle Exceptions auf dieselbe Response-Struktur.

2. **Eigene Exception-Klassen**
   Kapseln Domain-/Business-Error-Code + Message + Status.

3. **Optionaler Response-Interceptor**
   Wrappt erfolgreiche Responses:
   `{ success: true, data, meta }`.

#### Leitlinie zur Fehlerkategorisierung

1. **Validierungs-/Client-Input-Fehler** -> `400`.
2. **Authentifizierungsfehler** -> `401`.
3. **Autorisierungsfehler** -> `403`.
4. **Fehlende Ressourcen** -> `404`.
5. **Business-Rule-Konflikte** -> `409` oder `422`.
6. **Unerwartete Systemfehler** -> `500`.

#### Was man vermeiden sollte

1. Ad-hoc-Fehlerformate aus unterschiedlichen Controllern zurückzugeben.
2. Exceptions zu schlucken und `200` mit `"error"` im Body zurückzugeben.
3. Interne Stacktraces/SQL-Fehler in Production-Responses offenzulegen.
4. Transport-Formatting-Logik direkt in Services zu mischen.

#### Praktische Best Practices

1. Einen Error-Code-Katalog definieren (`USER_NOT_FOUND`, `TOKEN_EXPIRED` usw.).
2. Correlation-/Request-ID in jede Fehler-Response und jeden Log-Eintrag aufnehmen.
3. Sicherstellen, dass der globale Filter bekannte (`HttpException`) und unbekannte Fehler behandelt.
4. Fehlerpfade mit E2E-Tests absichern, um den API-Error-Contract zu stabilisieren.

</details>

<details>
<summary>37. Wie loggt man Fehler in Production korrekt, ohne den Stack Trace zu verlieren?</summary>

#### NestJS

Um Fehler in Production korrekt zu loggen, brauchst du zwei parallele Ausgaben:
1. **sichere Client-Response** (keine sensiblen Interna),
2. **vollständiges strukturiertes Server-Log** (inkl. Stack Trace und Kontext).

#### Kernprinzip

Stack Traces niemals an API-Clients ausgeben, aber immer in Logs erhalten – für
Debugging und Incident Response.

#### Empfohlener Ansatz in NestJS

1. Fehler zentral in einem globalen Exception Filter abfangen.
2. Mit strukturiertem Logger loggen (Pino/Winston/Nest-Logger-Adapter).
3. Stack, Error Code, Request-Metadaten, Correlation ID und User-Kontext loggen.
4. Aus dem Filter eine bereinigte Error-Payload zurückgeben.

#### Beispiel (globaler Filter loggt Stack)

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
      stack: err?.stack, // vollständigen Stack in Logs behalten
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

#### Was für production-taugliche Diagnostik geloggt werden sollte

1. Timestamp, Level, Service-Name, Environment.
2. Request ID / Trace ID.
3. Route, Methode, Status Code, Latenz.
4. Auth-Kontext (userId/tenantId, wenn verfügbar).
5. Vollständiger Stack + Root-Cause-Kette.

#### Häufige Fehler

1. Nur `error.message` loggen (Stack und Cause-Chain gehen verloren).
2. String-konkatenierte Logs statt strukturierter JSON-Logs.
3. Doppelte Logs auf mehreren Schichten (Rauschen).
4. Rohe Exception-Objekte an Clients zurückgeben.

#### Praktische Best Practices

1. Einen einzigen strukturierten Logger app-weit verwenden.
2. Correlation-ID-Middleware/-Interceptor früh im Request-Lifecycle einbauen.
3. Secrets/PII vor Log-Ausgabe redaktieren.
4. Logs an zentralen Observability-Stack weiterleiten (ELK, Datadog, Grafana Loki).
5. Fehlerpfade testen, damit der Stack nach Deploy weiterhin in Logs erhalten bleibt.

</details>

<details>
<summary>38. Was ist `ConfigModule` und warum sollte man es statt `process.env` verwenden?</summary>

#### NestJS

`ConfigModule` ist das Konfigurationssystem von NestJS (`@nestjs/config`), das
Umgebungs-/Konfigurationswerte lädt, validiert und über DI bereitstellt.

`ConfigModule` ist direktem Zugriff auf `process.env` vorzuziehen, weil es
Konfigurationslogik zentralisiert, die Typsicherheit verbessert und
Tests/Wartung deutlich sauberer macht.

#### Warum `process.env` allein nicht ausreicht

1. Verstreute Environment-Reads über die gesamte Codebase.
2. Keine zentrale Validierung obligatorischer Variablen.
3. Nur String-Werte ohne typisierte Konvertierung.
4. Schwerer testbar/mockbar und schlechter auffindbar.

#### Was dir `ConfigModule` gibt

1. **Zentrales Config-Loading**
   Ein Ort für Env-Dateien und Config-Factories.

2. **Validierung beim Startup**
   Fail-fast, wenn Pflichtvariablen fehlen/ungültig sind.

3. **Typisierter Zugriff über `ConfigService`**
   Bessere Verträge und weniger Runtime-Überraschungen.

4. **DI-Integration**
   Jeder Provider kann Config sauber injizieren.

5. **Environment-spezifische Komposition**
   Einfache Trennung für dev/staging/prod.

#### Basis-Setup

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

Verwendung:

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

#### Validierungsbeispiel (empfohlen)

`validationSchema` (Joi) oder eine eigene Validierungsfunktion verwenden:
1. Pflichtvariablen erzwingen.
2. Formate/Bereiche validieren.
3. App-Bootstrap bei ungültiger Config stoppen.

#### Praktische Empfehlung

`process.env` nur in Config-Factories/Bootstrap-Grenzen verwenden. Überall sonst
Config über `ConfigService` oder typisierte Config-Provider beziehen – für
Konsistenz, Testbarkeit und sichereres Verhalten in Production.

</details>

<details>
<summary>39. Wie organisiert man `.env`-Dateien korrekt für verschiedene Umgebungen (dev, staging, prod)?</summary>

#### NestJS

Eine saubere `.env`-Organisation sollte pro Umgebung vorhersehbare Konfiguration
liefern, Secret-Leaks verhindern und lokale Entwicklung bequem halten.

#### Empfohlene Environment-Strategie

1. Eine **Basisdatei** für gemeinsame Defaults behalten.
2. **Umgebungsspezifische** Dateien für Overrides ergänzen.
3. Secrets aus Git fernhalten und über Deployment-Plattform/Secret-Store injizieren.

Typisches Layout:
1. `.env` (gemeinsame lokale Defaults)
2. `.env.development`
3. `.env.staging`
4. `.env.production`
5. `.env.test`
6. `.env.local` (dev-spezifische Overrides, per gitignore)

#### Mit NestJS `ConfigModule`

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

Die Lade-Reihenfolge ist wichtig: frühere Dateien haben in diesem Muster meist höhere Priorität.

#### Was committed vs ignoriert werden sollte

1. Committen:
   1. `.env.example` (alle benötigten Keys dokumentieren, ohne echte Secrets)
   2. Nicht-sensitive Defaults, falls eure Policy das erlaubt

2. Nicht committen:
   1. Echte Secrets/Tokens/private Keys
   2. `.env.local` und maschinenspezifische Overrides

#### Validierung und Fail-fast

Config beim Startup immer validieren (Joi oder Custom Validator):
1. Pflicht-Keys vorhanden.
2. Typen/Bereiche korrekt (`PORT`, Timeouts, Feature Flags).
3. URLs und Credentials-Format gültig.

#### Best Practices für Production/Staging

1. Plattform-Secret-Manager (AWS SSM/Secrets Manager, Vault, Doppler usw.)
   statt Klartextdateien bevorzugen.
2. Secrets regelmäßig rotieren.
3. Staging-/Prod-Credentials strikt trennen.
4. `NODE_ENV` in Deployment-Config explizit setzen.
5. Secrets nie in Docker-Images/Source-Code einbacken.

#### Praktischer Team-Workflow

1. `.env.example` als Vertragsquelle pflegen.
2. Onboarding-Script/Check hinzufügen, der fehlende Env-Variablen erkennt.
3. Typisierte Config-Wrapper nutzen, damit App-Code keine zufälligen Env-Keys direkt liest.
4. Ownership für kritische Variablen dokumentieren (DB, JWT, externe APIs).

</details>

<details>
<summary>40. Wie verwendet man Joi oder Zod, um Konfiguration beim App-Startup zu validieren?</summary>

#### NestJS

Konfiguration beim Startup validieren, damit die App bei fehlenden/ungültigen
Env-Werten sofort fehlschlägt, statt später zur Laufzeit zu crashen.

In NestJS passiert das typischerweise mit `ConfigModule.forRoot(...)` plus
entweder:
1. `validationSchema` (Joi), oder
2. `validate`-Funktion (eigene Logik, oft mit Zod).

#### Option A: Joi mit `validationSchema`

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

So funktioniert es:
1. Env wird geladen.
2. Joi validiert Struktur und Constraints.
3. App-Bootstrap schlägt sofort fehl, wenn Config ungültig ist.

#### Option B: Zod mit `validate`-Funktion

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

Warum Teams Zod mögen:
1. Starke TS-Typinferenz aus dem Schema.
2. Komponierbare Schemas für modulare Konfiguration.
3. Klare Parse-Fehler und gute Transformationsunterstützung.

#### Praktische Best Practices

1. Alle Pflicht-Secrets/URLs/Ports beim Startup validieren.
2. Primitive Typen explizit coercen (`PORT`, Booleans, Timeouts).
3. Ein Schema als Single Source of Truth halten.
4. Typisierte Config über Wrapper/Services bereitstellen, nicht über rohes `process.env`.
5. Unterschiedliche Env-Dateien pro Umgebung nutzen, aber einen Validierungsvertrag.

#### Joi vs Zod kurz

1. **Joi**: reif, direkt nutzbar mit eingebautem `validationSchema`.
2. **Zod**: TS-first Typisierung und Komponierbarkeit; stark für typisierte Config-Pipelines.

Beide sind production-tauglich; wichtig ist, eines konsistent durchzusetzen.

</details>

<details>
<summary>41. Wie implementiert man Feature Flags in NestJS?</summary>

#### NestJS

Feature Flags in NestJS werden typischerweise als dedizierter Service
implementiert, der bewertet, ob ein Feature für einen gegebenen Kontext aktiv
ist (Umgebung, User, Tenant, Prozent-Rollout usw.).

#### Warum Feature Flags wichtig sind

1. Sicheres, schrittweises Rollout.
2. Schneller Kill-Switch für problematische Features.
3. A/B-Experimente.
4. Entkopplung von Deployment und Release.

#### Häufige Architektur

1. **FeatureFlagService**
   Single Entry Point: `isEnabled(flag, context)`.

2. **Flag-Quelle**
   Env-Konfiguration, DB-Tabelle oder externer Flag-Provider.

3. **Evaluationskontext**
   User ID, Tenant ID, Plan, Region, App-Version, Request-Metadaten.

4. **Verwendungspunkte**
   Guards, Services, Controller, Interceptors, UI-Response-Shaping.

#### Einfache In-App-Implementierung (config-basiert)

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

Verwendung im Service:

```ts
if (this.flags.isEnabled('new_checkout', { userId, tenantId })) {
  return this.newCheckoutFlow();
}
return this.legacyCheckoutFlow();
```

#### Route-Level-Durchsetzung via Guard (optional)

1. `@Feature('new_checkout')`-Metadata-Decorator erstellen.
2. Guard liest Metadaten mit `Reflector`.
3. Guard ruft `FeatureFlagService.isEnabled(...)` auf.
4. Bei deaktiviertem Flag verweigern oder Verhalten umleiten.

#### Production-taugliche Praktiken

1. Rollout-Strategien unterstützen:
   1. Global on/off
   2. Prozent-Rollout
   3. User-/Tenant-Allowlisten
   4. Zeitfenster-Aktivierung

2. Lokalen Cache mit TTL für externe Flag-Provider hinzufügen.
3. Default-Werte explizit halten (fail-closed vs fail-open pro Flag).
4. Flag-Entscheidungen für Debugging loggen/nachweisbar machen.
5. Veraltete Flags schnell entfernen, um Langzeit-Komplexität zu vermeiden.

#### Build vs Buy

1. In-App bauen für einfache Anforderungen und geringe operative Last.
2. Managed Provider (LaunchDarkly, Unleash, ConfigCat usw.) für erweitertes
   Targeting, Analytics und Governance nutzen.

#### Faustregel

Flags als kurzlebige Release-Kontrollen behandeln, nicht als dauerhafte
Business-Logik-Branches. Für jedes Flag Ownership und Sunset-Datum festlegen.

</details>

<details>
<summary>42. Wie integriert man Datenbanken? (TypeORM, Prisma, Drizzle, Mongoose)</summary>

#### NestJS

In NestJS sollte die Datenbankintegration über dedizierte
Infrastruktur-Module/Provider erfolgen, nicht direkt in Controllern. Die Wahl
hängt vom Datenmodell, Team-Präferenzen und der Query-Komplexität ab.

#### Häufige Optionen

1. **TypeORM**
   Vollwertiges ORM mit Decorators, Repositories, Migrations und starker
   Nest-Modulintegration.

2. **Prisma**
   Schema-first ORM/Client mit sehr guter DX, typisierten Queries und
   vorhersehbaren Migrations.

3. **Drizzle**
   Leichtgewichtiges typisiertes SQL-Toolkit/ORM mit explizitem SQL-orientiertem Ansatz.

4. **Mongoose**
   ODM für MongoDB mit Schema-Modellierung und dokumentenorientierten Workflows.

#### Integrationsmuster je Tool

1. **TypeORM**
   `TypeOrmModule.forRoot(...)` im Root-Modul, `forFeature([Entity])` in
   Feature-Modulen, Repositories via `@InjectRepository` injizieren.

2. **Prisma**
   `PrismaService` erstellen (erbt von `PrismaClient`) und in einem Modul
   bereitstellen. Service in Repositories/Application-Services injizieren.

3. **Drizzle**
   DB-Provider (`drizzle(...)`) über Connection-Pool (`pg`, `mysql2`) bauen.
   Typisierte DB-Instanz über Custom Token injizieren.

4. **Mongoose**
   `MongooseModule.forRoot(...)` + `forFeature([{ name, schema }])` verwenden,
   Model via `@InjectModel` injizieren.

#### Minimale Beispiele

TypeORM:

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

Prisma-Service:

```ts
@Injectable()
export class PrismaService extends PrismaClient implements OnModuleInit {
  async onModuleInit() {
    await this.$connect();
  }
}
```

Mongoose:

```ts
MongooseModule.forRoot(process.env.MONGO_URI!);
```

#### Entscheidungsleitfaden

1. **TypeORM** wählen, wenn du klassischen Nest-Stil mit Decorators/Repositories möchtest.
2. **Prisma** wählen für stark typisierten Client und modernen Migrations-Workflow.
3. **Drizzle** wählen, wenn du SQL-first-Explizitheit mit Typsicherheit bevorzugst.
4. **Mongoose** wählen, wenn das MongoDB-Dokumentmodell natürlich passt.

#### Production-Best-Practices (unabhängig vom Tool)

1. DB-Zugriff in Repositories/Adaptern halten, nicht in Controllern.
2. Migrations nutzen; Schema-Auto-Sync in Production vermeiden.
3. Connection Pooling und Timeouts konfigurieren.
4. Health Checks und Startup-Fail-fast-Verhalten ergänzen.
5. Query-Latenz und Error-Raten instrumentieren.
6. Transaktionen in Application-Service-Grenzen kapseln.

</details>

<details>
<summary>43. Was ist der Unterschied zwischen `TypeOrmModule.forRoot()` und `forFeature()`?</summary>

#### NestJS

`TypeOrmModule.forRoot()` und `TypeOrmModule.forFeature()` bedienen in der
TypeORM-Integration von NestJS unterschiedliche Scopes.

#### `forRoot()` — DB-Connection-Setup auf Anwendungsebene

Im Root-Modul (meist `AppModule`) verwenden, um DataSource/Connection zu
konfigurieren.

Es definiert:
1. DB-Treiber/-Typ (`postgres`, `mysql` usw.)
2. Connection-Credentials/URL
3. Globale TypeORM-Optionen (Entity-Loading, Logging, Migrations, `synchronize`)

Beispiel:

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

#### `forFeature()` — Repository-Registrierung im Feature-Modul

In Domänen-/Feature-Modulen verwenden, um spezifische Entities zu registrieren
und deren Repositories im Modulkontext injizierbar zu machen.

Beispiel:

```ts
@Module({
  imports: [TypeOrmModule.forFeature([UserEntity])],
  providers: [UsersService],
})
export class UsersModule {}
```

Repository injizieren:

```ts
constructor(
  @InjectRepository(UserEntity)
  private readonly usersRepo: Repository<UserEntity>,
) {}
```

#### Praktische Zusammenfassung

1. `forRoot()`:
   1. Erstellt/konfiguriert die DB-Connection einmal (oder benannte Connections).
   2. Globales Infrastruktur-Thema.

2. `forFeature()`:
   1. Exponiert Repositories für ausgewählte Entities im Modul-Scope.
   2. Feature-/Business-Thema.

#### Häufiger Fehler

`forFeature()` ohne `forRoot()` (oder ohne initialisierte DataSource) führt zu
DI-/Runtime-Fehlern, weil Repositories keine aktive Connection im Hintergrund
haben.

#### Faustregel

1. Connection einmal mit `forRoot` im App-Bootstrap-Pfad konfigurieren.
2. Pro Modul Entities mit `forFeature` registrieren, wo Repositories benötigt werden.
3. `synchronize: false` in Production halten und Migrations verwenden.

</details>

<details>
<summary>44. Was ist das Repository-Pattern in NestJS + TypeORM?</summary>

#### NestJS

Das Repository-Pattern abstrahiert Datenzugriff hinter einer dedizierten
Schnittstelle/einem dedizierten Service, sodass Business-Logik nicht direkt von
ORM-Details abhängt.

In NestJS + TypeORM bedeutet das meist, `Repository<Entity>` mit einem eigenen
domänenorientierten Repository-Vertrag und dessen Implementierung zu kapseln.

#### Warum das Repository-Pattern nutzen

1. Entkoppelt Application-/Domain-Logik von der TypeORM-API.
2. Verbessert Testbarkeit (Interfaces einfach mockbar).
3. Zentralisiert Query-Logik und Mapping.
4. Macht ORM-Wechsel/Refactoring weniger schmerzhaft.

#### Typische Struktur

1. **Domain-Vertrag (Port)**
   `UsersRepository`-Interface mit business-orientierten Methoden.

2. **Infrastruktur-Implementierung**
   `TypeOrmUsersRepository`, das `Repository<UserEntity>` nutzt.

3. **Service-/Application-Layer**
   Hängt vom Interface-Token ab, nicht von konkreter TypeORM-Klasse.

#### Beispiel

Repository-Vertrag:

```ts
export interface UsersRepository {
  findByEmail(email: string): Promise<UserEntity | null>;
  save(user: UserEntity): Promise<UserEntity>;
}
```

TypeORM-Implementierung:

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

Provider-Bindung:

```ts
{
  provide: 'USERS_REPOSITORY',
  useClass: TypeOrmUsersRepository,
}
```

Service hängt von Abstraktion ab:

```ts
constructor(
  @Inject('USERS_REPOSITORY')
  private readonly usersRepo: UsersRepository,
) {}
```

#### Was in Repository vs Service gehört

1. Repository:
   Persistenz-Queries, Aggregate laden/speichern, DB-spezifisches Filtering.

2. Service/Use-Case:
   Orchestrierung, Business-Regeln, Transaktionsgrenzen koordinieren.

#### Häufiges Anti-Pattern

TypeORM-Repositories direkt in viele Services/Controller injizieren und
Query-Fragmente überall duplizieren. Das erhöht Kopplung und Inkonsistenz.

#### Praktischer Kernpunkt

TypeORM-Repository intern nutzen, aber nach außen ein eigenes
Domain-Repository-Interface exponieren, um die Architektur modular und
testfreundlich zu halten.

</details>

<details>
<summary>45. Was ist der Unterschied zwischen Repository-Pattern und Active Record — und wann sollte man welches wählen?</summary>

#### NestJS

Repository-Pattern und Active Record sind zwei unterschiedliche Ansätze zur
Organisation von Persistenzlogik.

#### Kerndifferenz

1. **Repository-Pattern**
   Domain-/Business-Layer arbeitet mit Repository-Abstraktionen; Persistenzlogik
   ist in Repository-Klassen getrennt.

2. **Active Record**
   Entity-/Model-Objekte enthalten Persistenzmethoden selbst (`save`, `remove`,
   statische Finder) und mischen Daten + Persistenzverhalten.

#### Eigenschaften des Repository-Patterns

1. Bessere Trennung der Verantwortlichkeiten.
2. Leichtere Unit-Tests über Interface-Mocks.
3. Skaliert besser in komplexen Domänen/Microservices.
4. Fördert domain-zentriertes Design und saubere Grenzen.

#### Eigenschaften von Active Record

1. Schnellerer Start bei kleinen/einfachen Apps.
2. Weniger Boilerplate für geradliniges CRUD.
3. Kann mit der Zeit eng an das ORM gekoppelt werden.
4. Mit wachsender Komplexität wird es schwerer, Business-Logik isoliert zu halten.

#### Wann welches wählen

1. **Repository-Pattern** wählen, wenn:
   1. Das Projekt mittel/groß ist oder voraussichtlich wächst.
   2. Das Team strikte Architektur/Testbarkeit braucht.
   3. Die Domain-Logik nicht trivial ist.
   4. Ein möglicher zukünftiger ORM-Wechsel ein Thema ist.

2. **Active Record** wählen, wenn:
   1. Die App klein, CRUD-lastig und wenig komplex ist.
   2. Geschwindigkeit der initialen Entwicklung Priorität hat.
   3. Das Team den Trade-off engerer ORM-Kopplung akzeptiert.

#### In der NestJS-Praxis

1. Die NestJS-Architektur (Module/Provider/DI) passt natürlich zum Repository-Pattern.
2. Selbst mit TypeORM bevorzugen viele Production-Teams Data-Mapper-/Repository-Stil,
   um Services sauber zu halten.

#### Kurzer Vergleich

1. **Kopplung**
   Repository: geringer
   Active Record: höher

2. **Testbarkeit**
   Repository: hoch
   Active Record: mittel/niedrig (stärker DB-gekoppelt)

3. **Boilerplate**
   Repository: mehr
   Active Record: weniger

4. **Langfristige Wartbarkeit**
   Repository: besser für komplexe Systeme
   Active Record: okay für einfache Apps

#### Praktische Empfehlung

Für interview-taugliche und production-reife NestJS-Architektur standardmäßig
Repository-Pattern verwenden. Active Record nur einsetzen, wenn die Domäne
bewusst einfach und die Lifecycle-Kosten niedrig sind.

</details>

<details>
<summary>46. Was sind Migrations in TypeORM/Prisma und warum ist `synchronize: true` in Production gefährlich?</summary>

#### NestJS

Migrations sind versionierte, explizite Scripts für Datenbankschema-Änderungen.
Sie ermöglichen Teams, Schemata sicher und vorhersehbar über Umgebungen hinweg
weiterzuentwickeln.

In TypeORM/Prisma sind Migrations der production-sichere Weg, Schemaänderungen
anzuwenden.

#### Was Migrations sind

1. **Geordnete Schema-Historie**
   Jede Migration ist ein nachvollziehbarer Schritt (up/down) der Schema-Evolution.

2. **Reproduzierbare Deployments**
   Dieselben Schemaänderungen laufen konsistent in dev/staging/prod.

3. **Reviewbares Change-Set**
   SQL/DDL-Intention ist im Code-Review und in CI sichtbar.

4. **Rollback-Strategie**
   Problematische Änderungen können (mit Einschränkungen) zurückgenommen werden.

#### TypeORM vs Prisma Migrationsmodell

1. **TypeORM**
   Migrations sind TS/JS-Dateien (oder SQL), die per CLI erzeugt/geschrieben und ausgeführt werden.

2. **Prisma**
   Schemaänderungen werden in `schema.prisma` definiert; Migration-Dateien werden
   generiert und mit Prisma Migrate angewendet.

Beide Ansätze erzeugen auditierbare Migrations-Artefakte.

#### Warum `synchronize: true` in Production gefährlich ist

1. **Implizit destruktive Änderungen**
   Das ORM kann Spalten/Indizes automatisch ändern/löschen, ohne kontrolliertes Review.

2. **Nicht-deterministisches Verhalten**
   Schema-Diff-Verhalten kann je nach Entity-Drift und Runtime-Zustand variieren.

3. **Keine saubere Migrationshistorie**
   Schwer nachvollziehbar, was wann geändert wurde.

4. **Riskante Startup-Kopplung**
   App-Start kann Produktionsschema unerwartet mutieren.

5. **Schwache Multi-Instance-Sicherheit**
   Gleichzeitige App-Starts können bei Schema-Updates race conditions erzeugen.

#### Production-sicherer Workflow

1. `synchronize: false` in Production setzen.
2. Für jede Schemaänderung eine Migration erzeugen.
3. Migration-SQL im PR reviewen.
4. Migrations in der Deployment-Pipeline vor/mit App-Rollout ausführen.
5. Migration-Ausführung überwachen und Deployment bei Fehlern stoppen.

#### Praktische Beispiele

TypeORM-Production-Konfiguration:

```ts
TypeOrmModule.forRoot({
  // ...
  synchronize: false,
  migrationsRun: false,
});
```

Prisma-Deployment-Ansatz:
1. Migration-Dateien committen.
2. `prisma migrate deploy` beim Release ausführen.

#### Faustregel

` synchronize: true` nur für schnelles lokales Prototyping verwenden. Für jede
ernsthafte Umgebung sind Migrations Pflicht für Sicherheit, Nachvollziehbarkeit
und kontrollierte Schema-Evolution.

</details>

<details>
<summary>47. Wie implementiert man Soft Delete in TypeORM?</summary>

#### NestJS

Soft Delete bedeutet, dass Datensätze als gelöscht markiert werden, statt sie
physisch aus der Datenbank zu entfernen. In TypeORM geschieht das typischerweise
mit `@DeleteDateColumn`.

#### Warum Soft Delete nutzen

1. Versehentlich gelöschte Daten wiederherstellen.
2. Audit-/Historienkontext erhalten.
3. Foreign-Key-Beziehungen und Business-Traceability bewahren.
4. „Papierkorb/Wiederherstellen“-Workflows unterstützen.

#### Schritt 1: Delete-Timestamp-Spalte hinzufügen

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

#### Schritt 2: Soft-Delete-Repository-Methoden verwenden

```ts
// als gelöscht markieren (setzt deletedAt)
await this.usersRepo.softDelete(userId);

// soft-gelöschte Zeile wiederherstellen
await this.usersRepo.restore(userId);
```

Du kannst auch nutzen:
1. `softRemove(entity)` für Löschung auf Entity-Instanzebene.
2. `recover(entity)` für Restore auf Instanzebene.

#### Query-Verhalten

1. Standardmäßig schließt TypeORM soft-gelöschte Zeilen bei `find*` aus.
2. Um gelöschte Zeilen einzubeziehen, `withDeleted: true` setzen.

```ts
const allRows = await this.usersRepo.find({ withDeleted: true });
```

Nur gelöschte Zeilen:

```ts
const deletedOnly = await this.usersRepo.find({
  withDeleted: true,
  where: { deletedAt: Not(IsNull()) },
});
```

#### Beispiel auf Service-Ebene

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

#### Production-Hinweise

1. Indizes für häufig gefilterte Felder setzen (`deleted_at`, Tenant-Keys).
2. Sicherstellen, dass Unique Constraints Soft-Deletes berücksichtigen (partielle Unique Indizes, wenn unterstützt).
3. Retention-Policy für spätere Hard-Cleanup-Läufe definieren.
4. Delete-/Restore-Events in Audit-Logs aufnehmen.

#### Faustregel

Soft Delete für User-/Business-Daten nutzen, bei denen Recovery oder Audit nötig
sein kann. Hard Delete nur verwenden, wenn Compliance-/Storage-Vorgaben oder
Domänenregeln dauerhafte Löschung verlangen.

</details>

<details>
<summary>48. Wie implementiert man Transaktionen in TypeORM mit NestJS?</summary>

#### NestJS

Transaktionen stellen sicher, dass eine Gruppe von DB-Operationen entweder
vollständig erfolgreich ist oder komplett zurückgerollt wird. In NestJS +
TypeORM solltest du Transaktionen für mehrstufige Writes nutzen, die konsistent
bleiben müssen.

#### Wann Transaktionen erforderlich sind

1. Beim Erstellen/Aktualisieren mehrerer zusammenhängender Tabellen in einem Use-Case.
2. Bei Balance-/Geld-/Bestandsänderungen.
3. Bei Operationen, bei denen Teilerfolg den Business-Status korrumpieren würde.

#### Hauptansätze in TypeORM

1. **`DataSource.transaction(...)`** (empfohlener Default)
2. **`QueryRunner`** (manuelle Kontrolle für fortgeschrittene Flows)

#### Ansatz 1: `DataSource.transaction` (sauber und sicher)

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

Wichtig: Im Transaktions-Callback mit `manager`-Repositories/Entities arbeiten,
nicht mit global injizierten Repositories.

#### Ansatz 2: `QueryRunner` (feingranulare Kontrolle)

```ts
const qr = dataSource.createQueryRunner();
await qr.connect();
await qr.startTransaction();
try {
  // qr.manager für alle Queries verwenden
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

#### Best Practices

1. Transaktions-Scope kurz und fokussiert halten.
2. Externe HTTP-Calls innerhalb einer DB-Transaktion vermeiden.
3. Bei concurrency-sensitiven Flows passende Isolation Levels nutzen.
4. Deadlock-/Retry-Strategien für High-Contention-Operationen umsetzen.
5. Domain-Events erst nach erfolgreichem Commit emitten (oder Outbox-Pattern verwenden).

#### Häufige Fehler

1. Transaktionale und nicht-transaktionale Repositories im selben Flow mischen.
2. Lang laufende Transaktionen, die Lock-Contention verursachen.
3. Fehler schlucken und inkonsistenten Zustand committen.

#### Praktische Regel

Einen Business-Use-Case in eine Transaktionsgrenze packen, wenn Konsistenz
zwischen mehreren Writes nicht verhandelbar ist.

</details>

<details>
<summary>49. Was ist das N+1-Problem und wie löst man es in NestJS?</summary>

#### NestJS

Das N+1-Problem entsteht, wenn deine App:
1. eine Query lädt, um eine Liste von Parent-Datensätzen zu holen,
2. und dann pro Parent eine zusätzliche Query für Relationen ausführt.

Das erzeugt `1 + N` Queries, hohe Latenz und unnötige DB-Last.

#### Beispiel für N+1

1. Users laden (`N` Users werden zurückgegeben).
2. Für jeden User Posts separat laden.
3. Gesamtzahl Queries: `1 + N`.

Bei 100 Usern sind das 101 DB-Roundtrips.

#### Wo es in NestJS-Apps auftritt

1. TypeORM Lazy-Relations in Schleifen.
2. GraphQL-Resolver, die Nested Fields pro Entity auflösen.
3. Service-Methoden mit wiederholten Repository-Calls pro Item.

#### Wie man es löst

1. **Eager Loading mit Joins**
   Query-Builder-Joins verwenden, um Relationen in einer Query (oder wenigen kontrollierten Queries) zu laden.

2. **Batch Loading**
   DataLoader-artiges Batching nutzen (besonders in GraphQL).

3. **IN-Queries**
   Related Rows für alle Parent-IDs auf einmal laden und im Speicher mappen.

4. **Projektionsoptimierung**
   Nur benötigte Spalten selektieren, um Payload zu reduzieren.

#### TypeORM-Join-Beispiel

```ts
const users = await this.usersRepo
  .createQueryBuilder('u')
  .leftJoinAndSelect('u.posts', 'p')
  .getMany();
```

#### Beispiel für Batch-Loading-Pattern

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

#### Erkennungssignale

1. Plötzlicher Query-Count-Anstieg bei größeren Result-Sets.
2. Endpoint-Latenz skaliert linear mit der Anzahl Parent-Zeilen.
3. Wiederholte ähnliche SQL-Statements in Logs/Monitoring.

#### Praktische Präventionsstrategie

1. SQL-/Query-Logging in non-prod Performance-Tests aktivieren.
2. Query-Count-Assertions für kritische Endpoints ergänzen.
3. Repository-Methoden bevorzugen, die auf Aggregate-Reads ausgelegt sind.
4. GraphQL-Resolver auf per-field DB-Calls prüfen.

#### Faustregel

Wenn ein Endpoint Collections mit Relationen lädt, Data Access von Anfang an für
Batching/Joins entwerfen. In Production-Pfaden nie auf per-item Lazy-Fetch-Loops
verlassen.

</details>

<details>
<summary>50. Was ist Connection Pooling und wie konfiguriert man es korrekt für eine Datenbank?</summary>

#### NestJS

Connection Pooling ist eine verwaltete Menge wiederverwendbarer
Datenbankverbindungen, die von Requests gemeinsam genutzt wird. Statt für jede
Query eine neue Verbindung aufzubauen, leiht sich die App eine Verbindung aus
dem Pool und gibt sie danach zurück.

#### Warum Pooling wichtig ist

1. Reduziert Overhead beim Verbindungsaufbau.
2. Verbessert Durchsatz/Latenz unter Last.
3. Verhindert DB-Überlastung durch unkontrollierte Connection-Spitzen.
4. Stabilisiert das Verhalten bei parallelen Requests.

#### Wichtige Pool-Parameter

1. **max pool size**
   Maximale Anzahl gleichzeitiger DB-Verbindungen pro App-Instanz.

2. **min pool size** (treiberspezifisch)
   Minimale Anzahl offener Idle-Verbindungen.

3. **acquire timeout**
   Wie lange auf eine freie Connection gewartet wird.

4. **idle timeout**
   Wie lange ungenutzte Connections vor dem Schließen gehalten werden.

5. **max lifetime**
   Maximales Alter einer Connection vor Recycle.

#### Sizing-Strategie (praxisnah)

1. Vom DB-Limit und der Anzahl App-Replikas ausgehen:
   `pool_max_per_instance * replica_count < db_connection_limit - safety_margin`.

2. Headroom lassen für:
   1. Migrations/Admin-Tools
   2. Background-Worker
   3. Unerwartete Traffic-Spitzen

3. Per Load-Test tunen anhand von:
   1. Wartezeit auf Connection-Akquise
   2. DB-CPU
   3. Lock-Contention
   4. p95/p99-Latenz

#### TypeORM/NestJS-Beispiel (Postgres)

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  synchronize: false,
  extra: {
    max: 20,                  // pool max connections
    connectionTimeoutMillis: 5000,
    idleTimeoutMillis: 30000,
  },
});
```

#### Operative Best Practices

1. Eine globale DataSource pro App-Prozess verwenden (nicht viele Pools erzeugen).
2. Query-Timeouts und Statement-Timeouts setzen.
3. Pool-Metriken monitoren: active, idle, waiting.
4. Mit realer Last tunen, nicht mit Defaults.
5. Bei serverless/stark elastisch ggf. PgBouncer oder providerverwaltetes Pooling nutzen.

#### Häufige Fehler

1. Pool zu groß -> DB-Thrashing/Lock-Druck.
2. Pool zu klein -> Request-Queuing/Timeouts.
3. Horizontalen Skalierungsfaktor über Replikas ignorieren.
4. Neue Clients manuell in Request-Handlern öffnen.

#### Faustregel

Die Connection-Pool-Größe ist eine System-Kapazitätsentscheidung, nicht nur
ORM-Konfiguration. Mit produktionsnaher Last und DB-Limits tunen.

</details>

<details>
<summary>51. Wie schützt man sich in TypeORM/Prisma vor SQL-Injection?</summary>

#### NestJS

SQL-Injection-Schutz in NestJS mit TypeORM/Prisma basiert auf einem Prinzip:
**SQL niemals per String-Konkatenation mit untrusted Input bauen**.

Parameterisierte Queries und ORM-Query-APIs verwenden, die Werte sicher binden.

#### Sichere Defaults

1. **TypeORM Repository/Query Builder mit Parametern**
2. **Prisma-Client-Methoden mit typisierten Filtern**
3. **DTO-Validierung + Parsing, bevor Daten die Persistenzschicht erreichen**

#### Sichere TypeORM-Patterns

Repository-API:

```ts
await usersRepo.findOne({ where: { email: input.email } });
```

QueryBuilder mit gebundenen Parametern:

```ts
await usersRepo
  .createQueryBuilder('u')
  .where('u.email = :email', { email: input.email })
  .andWhere('u.status = :status', { status: 'active' })
  .getMany();
```

#### Sichere Prisma-Patterns

```ts
await prisma.user.findMany({
  where: {
    email: input.email,
    status: 'active',
  },
});
```

Prisma erzeugt unter der Haube für Standard-Client-Methoden parameterisierte Queries.

#### Gefährliche Anti-Patterns

1. Raw SQL mit String-Interpolation:

```ts
// BAD
await dataSource.query(`SELECT * FROM users WHERE email = '${input.email}'`);
```

2. Unsichere dynamische ORDER-BY-/Spaltennamen aus User-Input.
3. Unvalidierte Fragmente in Raw-Query-Funktionen übergeben.

#### Falls Raw SQL unvermeidbar ist

1. Parameter-Placeholder verwenden:

```ts
await dataSource.query('SELECT * FROM users WHERE email = $1', [input.email]);
```

2. Dynamische Identifiers (Spalten-/Sortierfelder) strikt whitelisten:
   Input -> bekannter sicherer SQL-Token.

#### Defense in Depth

1. Input per DTO + `ValidationPipe` validieren und bereinigen.
2. DB-Accounts mit Least-Privilege nutzen.
3. Gefährliche DB-Rechte deaktivieren (drop/alter, wenn nicht nötig).
4. Auffällige Query-Patterns und fehlgeschlagene Auth-Versuche loggen.
5. Security-Tests mit Injection-Payloads für kritische Endpoints ergänzen.

#### Praktische Regel

Bei 95% der Queries auf ORM-APIs bleiben. Für verbleibende Raw-SQL-Fälle immer
Parameter binden und jede dynamische SQL-Struktur whitelisten.

</details>

<details>
<summary>52. Wie organisiert man Pagination in einer REST-API korrekt? (Offset vs Cursor-basiert)</summary>

#### NestJS

Gutes Pagination-Design in einer REST-API sollte stabil, performant und für
Clients vorhersehbar sein. Die zwei Hauptmodelle sind offset-basierte und
cursor-basierte Pagination.

#### Offset vs Cursor: Kerndifferenz

1. **Offset-Pagination**
   Nutzt `limit` + `offset` (oder page/pageSize).
   Beispiel: `GET /users?limit=20&offset=40`.

2. **Cursor-Pagination**
   Nutzt einen Zeiger auf den zuletzt gesehenen Datensatz in einem sortierten Strom.
   Beispiel: `GET /users?limit=20&cursor=eyJpZCI6MTIzfQ==`.

#### Wann man Offset-Pagination nutzen sollte

1. Kleine/mittlere Datensätze.
2. Bedarf an zufälligen Seitensprüngen (`page=7`).
3. Einfachere Admin-Dashboards/Backoffice-Tools.

Trade-offs:
1. Langsamer bei großen Offsets.
2. Inkonsistente Seiten bei gleichzeitigen Inserts/Deletes.

#### Wann man Cursor-Pagination nutzen sollte

1. Große, häufig veränderte Datensätze.
2. Infinite Scroll/mobile Feeds.
3. Performance-sensitive APIs.

Vorteile:
1. Bessere DB-Performance bei Skalierung.
2. Stabilere Reihenfolge bei parallelen Writes.

Trade-off:
1. Kein natürlicher zufälliger Seitensprung.

#### Essenzielle Designregeln (beide Modelle)

1. Immer deterministische Sortierung definieren:
   z. B. `ORDER BY created_at DESC, id DESC`.

2. Max Page Size serverseitig erzwingen.

3. Pagination-Metadaten zurückgeben:
   `hasNext`, `nextCursor` (Cursor-Modell) oder `total` (Offset-Modell bei Bedarf).

4. Pagination-Parameter via DTO + Pipes validieren.

#### Response-Shape-Beispiele

Offset:

```json
{
  "data": [...],
  "meta": { "limit": 20, "offset": 40, "total": 312, "hasNext": true }
}
```

Cursor:

```json
{
  "data": [...],
  "meta": { "limit": 20, "nextCursor": "eyJjcmVhdGVkQXQiOiIyMDI2LTA0LTMwVDEwOjAwOjAwWiIsImlkIjoxMjN9", "hasNext": true }
}
```

#### Hinweise zur NestJS-Implementierung

1. Dedizierte DTOs erstellen: `OffsetPaginationDto`, `CursorPaginationDto`.
2. Pagination-Logik in Repository-/Query-Layer halten, nicht im Controller.
3. Cursor als opaken Token kodieren (base64/json + optionale Signatur).
4. Sicherstellen, dass DB-Indizes zu Sort-/Filter-Keys passen (`created_at`, `id`, Tenant-Felder).

#### Praktische Empfehlung

1. **Offset** für einfache interne Endpoints nutzen.
2. **Cursor** für öffentliche/high-volume Feeds nutzen.
3. Bei Unsicherheit bei Cursor starten, besonders für write-heavy Timelines, um
   spätere Performance- und Konsistenzprobleme zu vermeiden.

</details>

<details>
<summary>53. Wie versioniert man eine API in NestJS? (URI-, Header-, Media-Type-Versionierung)</summary>

#### NestJS

API-Versionierung in NestJS ermöglicht es, Endpoints weiterzuentwickeln, ohne
bestehende Clients zu brechen. Nest unterstützt URI-, Custom-Header- und
Media-Type-Versionierungsstrategien.

#### Versionierungsstrategien

1. **URI-Versionierung**
   Version im Pfad: `/v1/users`, `/v2/users`.

2. **Header-Versionierung**
   Version im Custom Header (z. B. `X-API-Version: 2`).

3. **Media-Type-Versionierung**
   Version im `Accept`-Header-Media-Type
   (z. B. `application/vnd.myapp.v2+json`).

#### Versionierung in NestJS aktivieren

```ts
import { NestFactory, VersioningType } from '@nestjs/core';

const app = await NestFactory.create(AppModule);

app.enableVersioning({
  type: VersioningType.URI, // oder HEADER / MEDIA_TYPE
  defaultVersion: '1',
});
```

#### Versionen an Controller/Routes deklarieren

Controller-Level:

```ts
@Controller({ path: 'users', version: '1' })
export class UsersV1Controller {}
```

Route-Level:

```ts
@Get()
@Version('2')
findAllV2() {}
```

Mehrere Versionen auf einem Handler:

```ts
@Version(['1', '2'])
```

#### Auswahl der Strategie

1. **URI-Versionierung** (am häufigsten)
   1. Einfach zu debuggen und zu cachen.
   2. Klar in Logs und Doku sichtbar.
   3. Bester Default für öffentliche REST-APIs.

2. **Header-Versionierung**
   1. Hält URLs sauber.
   2. Nützlich in kontrollierten Enterprise-Clients.
   3. Schwerer manuell zu testen und standardmäßig schwieriger zu cachen.

3. **Media-Type-Versionierung**
   1. Standards-orientierter Content-Negotiation-Stil.
   2. Für Clients/Tooling am komplexesten.

#### Praktische Best Practices

1. Versionierung vor dem ersten Breaking Change einführen.
2. Backward-Compatibility-Fenster und Deprecation-Policy definieren.
3. Nur versionieren, wenn Contract-Änderungen breaking sind.
4. Sunset-Timelines für alte Versionen dokumentieren.
5. Gemeinsame Business-Logik in Services halten; primär die Transport-Schicht versionieren.

#### Faustregel

Für die meisten Teams mit **URI-Versionierung** starten, weil sie explizit und
operativ einfach ist. Header-/Media-Type-Versionierung nur bei klaren
Plattformanforderungen einsetzen.

</details>

<details>
<summary>54. Wie implementiert man Swagger-Dokumentation in NestJS via `@nestjs/swagger`?</summary>

#### NestJS

Swagger in NestJS wird mit `@nestjs/swagger` implementiert, um OpenAPI-Dokumentation
automatisch aus Controllern, DTOs und Decorators zu generieren.

#### Schritt 1: Pakete installieren

1. `@nestjs/swagger`
2. `swagger-ui-express`

#### Schritt 2: Swagger in `main.ts` konfigurieren

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

Die Doku-URL ist dann `/docs`.

#### Schritt 3: Controller und DTOs annotieren

Controller-Annotationen:

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

DTO-Annotationen:

```ts
import { ApiProperty } from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({ example: 'john@example.com' })
  email: string;

  @ApiProperty({ minLength: 8 })
  password: string;
}
```

#### Schritt 4: Schemas korrekt halten

1. Klassenbasierte DTOs (keine Interfaces) für Runtime-Metadaten verwenden.
2. Mit `ValidationPipe` kombinieren, damit Doku und echte Constraints übereinstimmen.
3. Auth, Pagination und Error-Modelle explizit dokumentieren.

#### Fortgeschrittene Production-Praktiken

1. Pro API-Version eigene Doku erzeugen, wenn Versionierung aktiv ist.
2. Interne/Admin-Endpoints bei Bedarf ausblenden.
3. `operationIdFactory` für stabile SDK-Generierung nutzen.
4. OpenAPI-JSON in CI exportieren für Contract-Checks/Client-Codegen.
5. Docs-Endpoint in Production schützen, wenn die API privat ist.

#### Praktischer Kernpunkt

Swagger als Contract-Artefakt behandeln, nicht nur als UI. Decorators und DTOs
parallel zu Endpoint-Änderungen pflegen, um Doc-Drift zu vermeiden.

</details>

<details>
<summary>55. Wie implementiert man CORS in NestJS und wann sind Custom-Einstellungen nötig?</summary>

#### NestJS

CORS (Cross-Origin Resource Sharing) steuert, welche Browser-Origins auf deine
API zugreifen dürfen. In NestJS wird es auf Bootstrap-Ebene der Anwendung
konfiguriert.

#### Basisaktivierung von CORS

```ts
const app = await NestFactory.create(AppModule);
app.enableCors();
```

Das ist für lokale Entwicklung okay, für Production aber meist zu permissiv.

#### CORS-Konfiguration im Production-Stil

```ts
app.enableCors({
  origin: ['https://app.example.com', 'https://admin.example.com'],
  methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE', 'OPTIONS'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true,
  maxAge: 86400,
});
```

#### Wann Custom-CORS-Einstellungen nötig sind

1. **Mehrere Frontend-Domains**
   Explizite Allowlist je Umgebung erforderlich.

2. **Cookie-basierte Auth (`credentials: true`)**
   Erfordert spezifische Origin (nicht `*`) und sichere Cookie-Policy.

3. **Custom Header/Tokens**
   Benötigte Header in `allowedHeaders` ergänzen.

4. **Komplexe Methoden/Preflight**
   `methods` konfigurieren und sicherstellen, dass `OPTIONS` korrekt funktioniert.

5. **Pro-Tenant- oder dynamische Origin-Regeln**
   Funktionsbasierten Origin-Resolver verwenden.

#### Beispiel für dynamische Origin

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

#### Häufige Fehler

1. `origin: '*'` mit `credentials: true` verwenden (für Cookies ungültig/unsicher).
2. Preflight-Handling (`OPTIONS`) in Proxies/Gateways vergessen.
3. Eine Origin für alle Umgebungen hardcoden.
4. CORS als Security-Grenze für Nicht-Browser-Clients behandeln.

#### Praktische Empfehlungen

1. In Production eine strikte Origin-Allowlist verwenden.
2. CORS-Config je Umgebung via `ConfigService` trennen.
3. Geblockte Origins für Debugging loggen.
4. CORS mit echter Auth/Authz, Rate Limiting und ggf. CSRF-Strategie kombinieren.

</details>

<details>
<summary>56. Was ist Idempotenz im Kontext einer REST-API und wie stellt man sie sicher?</summary>

#### NestJS

Idempotenz bedeutet, dass das wiederholte Senden derselben Anfrage mehrfach
zum selben finalen Systemzustand führt wie eine einmalige Ausführung.

In REST-APIs ist das kritisch für Zuverlässigkeit bei Retries,
Netzwerk-Timeouts und doppelten Client-Submissions.

#### HTTP-Semantik und Idempotenz

1. **Meist per Design idempotent**
   `GET`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`.

2. **Nicht standardmäßig idempotent**
   `POST` (erzeugt oft bei jedem Call neue Ressourcen).

#### Warum Idempotenz wichtig ist

1. Sichere Client-Retries nach Timeout.
2. Schutz vor doppelten Aktionen (Double Charge/Order).
3. Höhere Resilienz in verteilten Systemen und at-least-once Delivery-Flows.

#### Wie man Idempotenz in der Praxis sicherstellt

1. **Idempotency-Key-Pattern (für POST)**
   Client sendet eindeutigen Key (z. B. `Idempotency-Key`-Header).
   Server speichert Key + Request-Fingerprint + Response.
   Wiederholter identischer Key liefert Originalergebnis statt erneuter Ausführung.

2. **Datenbank-Constraints**
   Eindeutigkeit auf Business-Identifiern erzwingen
   (`externalPaymentId`, `orderReference` usw.).

3. **Upsert-/Compare-and-Set-Patterns**
   Deterministische Write-Operationen nutzen, wo möglich.

4. **Transaktionale Verarbeitung**
   Mehrstufige Writes vor partieller Duplikation schützen.

#### NestJS-Implementierungs-Skizze

1. Interceptor/Guard prüft `Idempotency-Key`.
2. Fingerprint berechnen (Route + User + Payload-Hash).
3. Idempotency-Record nachschlagen:
   1. Wenn completed -> gespeicherte Response zurückgeben.
   2. Wenn in-progress -> Conflict-/Retry-later-Policy zurückgeben.
   3. Wenn nicht vorhanden -> Key reservieren und Handler ausführen.
4. Finale Response atomar speichern und zurückgeben.

#### Minimaler konzeptioneller Flow

```text
Request -> Idempotency middleware/interceptor
        -> key exists with completed response? return cached response
        -> else execute use case
        -> persist outcome by key
        -> return response
```

#### Häufige Stolperfallen

1. Gleichen Key für verschiedene Payloads wiederverwenden (muss erkannt und abgelehnt werden).
2. Keys ohne TTL/Cleanup speichern.
3. Key nicht nach Tenant/User scopen, wo nötig.
4. Bei Retry für denselben Key unterschiedliche Responses liefern.

#### Praktische Empfehlung

Für alle Money-/Order-/Subscription-Endpoints Idempotency-Keys + eindeutige
DB-Constraints erzwingen. Das bietet Schutz gegen Duplikate auf
Anwendungsebene und Persistenzebene.

</details>

<details>
<summary>57. Wie implementiert man Rate Limiting in NestJS? (`@nestjs/throttler`)</summary>

#### NestJS

Rate Limiting steuert, wie viele Requests ein Client in einem Zeitfenster senden
kann. In NestJS ist die Standardlösung `@nestjs/throttler`.

#### Warum Rate Limiting nötig ist

1. Schützt die API vor Missbrauch und Brute-Force-Versuchen.
2. Reduziert unbeabsichtigte Überlast durch „laute“ Clients.
3. Verbessert Fairness zwischen Usern/Tenants.
4. Erhöht Resilienz, bevor Traffic teure Abhängigkeiten erreicht.

#### Schritt 1: Modul installieren und konfigurieren

```ts
import { Module } from '@nestjs/common';
import { ThrottlerModule } from '@nestjs/throttler';

@Module({
  imports: [
    ThrottlerModule.forRoot([
      {
        ttl: 60_000, // 60 Sekunden
        limit: 100,  // 100 Requests pro Fenster
      },
    ]),
  ],
})
export class AppModule {}
```

#### Schritt 2: Globalen Guard anwenden

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

Damit sind alle Routen standardmäßig rate-limitiert.

#### Schritt 3: Pro Route/Controller anpassen

Strengeres Limit:

```ts
@Throttle({ default: { limit: 5, ttl: 60_000 } })
@Post('login')
login() {}
```

Limit für Health-Endpoint überspringen:

```ts
@SkipThrottle()
@Get('health')
health() {}
```

#### Keying-Strategie (wer limitiert wird)

Default ist meist Client-IP. In realen Systemen oft nötig:
1. userId-basiertes Limit (nach Auth),
2. tenant-/API-key-basiertes Limit,
3. route-gruppenspezifische Policies.

Guard-/Tracker-Logik kann für Custom Keys erweitert werden.

#### Hinweis für verteilte Deployments

In Multi-Instance-Umgebungen reicht In-Memory-Storage nicht für strikte globale
Limits. Shared Storage Adapter (z. B. Redis-basiert) verwenden, damit Limits
über Replikas konsistent bleiben.

#### Praktische Best Practices

1. Strengere Limits auf Auth-/Reset-/Token-Endpunkten setzen.
2. Klare `429 Too Many Requests`-Responses zurückgeben.
3. Retry-Metadaten (`Retry-After`) bereitstellen, wo möglich.
4. Throttle-Hits pro Route/Client monitoren, um Limits zu tunen.
5. Mit WAF/Reverse-Proxy-Rate-Limiting für mehrschichtige Defense kombinieren.

</details>

<details>
<summary>58. Wie implementiert man Request Tracing (requestId zu jedem Request hinzufügen)?</summary>

#### NestJS

Request Tracing bedeutet, jedem eingehenden Request eine eindeutige
`requestId` zuzuweisen und diese durch Logs, Responses und Downstream-Calls
weiterzureichen.

Das ist essenziell für Debugging in verteilten Systemen und zur Korrelation von
Events über Services hinweg.

#### Ziele von Request Tracing

1. Alle Logs für einen Request korrelieren.
2. Fehler über Middleware/Guards/Services/DB/externe APIs hinweg verfolgen.
3. Request-Identifier an Clients/Support-Teams zurückgeben.

#### Häufiges Implementierungsmuster

1. Middleware liest vorhandenen Header (`x-request-id`) oder erzeugt neue UUID.
2. ID am Request-Objekt speichern.
3. ID in Response-Header schreiben.
4. Logger fügt `requestId` automatisch in jede Log-Zeile ein.

#### Middleware-Beispiel

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

Middleware global in `AppModule.configure(...)` anwenden.

#### Logging-Integration

1. `requestId` in strukturierte Logs aus Interceptors/Services aufnehmen.
2. Zentrale Logger-Abstraktion bevorzugen, damit jede Log-Zeile Correlation-Felder trägt.

Interceptor-Beispiel (Timing + requestId):

```ts
const req = context.switchToHttp().getRequest();
const requestId = req.requestId;
this.logger.log({ msg: 'request.start', requestId, path: req.url });
```

#### Async-Context-Propagation (fortgeschritten)

Für tiefe Service-Layer/Background-Async-Chains `AsyncLocalStorage` (oder CLS-Modul)
verwenden, um `requestId` ohne manuelles Durchreichen durch jede Methode zu lesen.

#### Downstream-Propagation

1. `x-request-id` in ausgehenden HTTP-Calls weiterreichen.
2. Request-ID in Message-Metadaten für Queues/Events aufnehmen.
3. Auf Trace-/Span-IDs mappen, wenn OpenTelemetry genutzt wird.

#### Best Practices

1. Upstream-Request-ID von vertrauenswürdigen Gateways akzeptieren.
2. ID serverseitig generieren, wenn sie fehlt.
3. ID in jeder Error-Response zurückgeben für Support-Diagnostik.
4. Header-Naming über alle Services konsistent halten.
5. `requestId` als Correlation-Metadatum behandeln, nicht als Security-Token.

</details>

<details>
<summary>59. Wie geht man in NestJS mit `multipart/form-data` und Datei-Uploads um?</summary>

#### NestJS

In NestJS (Express-Plattform) werden Datei-Uploads typischerweise mit Multer
über Interceptors aus `@nestjs/platform-express` umgesetzt.

`multipart/form-data` wird verwendet, wenn Requests Dateien (und optionale
Form-Felder) enthalten.

#### Zentrale Bausteine

1. `FileInterceptor()` für einzelne Datei.
2. `FilesInterceptor()` für mehrere Dateien (gleiches Feld).
3. `FileFieldsInterceptor()` für mehrere benannte Datei-Felder.
4. `@UploadedFile()` / `@UploadedFiles()` für Zugriff auf geparste Dateien.

#### Beispiel: Single-File-Upload

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

#### Mehrere Dateien verarbeiten

1. Gleiches Feld:
   `@UseInterceptors(FilesInterceptor('files', 10))`

2. Benannte Felder:
   `@UseInterceptors(FileFieldsInterceptor([{ name: 'avatar', maxCount: 1 }, ...]))`

#### Validierungs- und Sicherheitsanforderungen

1. Maximale Dateigröße erzwingen.
2. MIME-Type und idealerweise reale Dateisignatur prüfen.
3. Dateinamen bereinigen und clientseitige Namen nicht vertrauen.
4. Außerhalb ausführbarer/statischer sensibler Pfade speichern.
5. Malware-Scanning für High-Risk-Domänen durchführen.

#### Storage-Strategien

1. Lokale Disk (einfach für dev/kleinere Deployments).
2. Object Storage (S3/GCS/MinIO) für skalierbare Production.
3. DB-Storage nur für Spezialfälle (für große Binärdateien meist ungeeignet).

#### Production-Best-Practices

1. Für große Dateien direct-to-object-storage Uploads bevorzugen.
2. Metadaten in DB halten (owner, key, mime, size, checksum).
3. Signed URLs für Download/Upload-Zugriffskontrolle nutzen.
4. Auth + Rate Limits auf Upload-Endpunkte anwenden.
5. Retention-/Cleanup-Policies ergänzen.

</details>

<details>
<summary>60. Wie implementiert man Komprimierung (gzip/brotli) in NestJS?</summary>

#### NestJS

Komprimierung reduziert die Response-Payload-Größe und verbessert die
Netzwerk-Performance, besonders bei JSON-/textlastigen APIs.

In NestJS (Express-Adapter) wird gzip/brotli typischerweise über
Compression-Middleware aktiviert.

#### Basis-Setup (Express)

1. `compression` installieren.
2. Middleware in `main.ts` registrieren.

```ts
import { NestFactory } from '@nestjs/core';
import compression from 'compression';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    compression({
      threshold: 1024, // responses > 1KB komprimieren
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

Der `Accept-Encoding`-Header des Clients steuert die Algorithmus-Aushandlung
(`br`, `gzip` usw., abhängig von Runtime/Proxy-Support).

#### Wo brotli typischerweise passiert

1. Anwendungsebene (Node-Middleware/Runtime-Support).
2. Reverse Proxy/CDN (Nginx, Cloudflare, Vercel usw.).

In vielen Production-Setups übernimmt Proxy/CDN die Komprimierung effizienter
als der App-Prozess.

#### Was komprimiert werden sollte

1. JSON-Responses
2. Text/HTML/CSS/JS
3. GraphQL-Responses

#### Was nicht komprimiert werden sollte

1. Bereits komprimierte Assets (`.zip`, `.jpg`, `.png`, `.mp4`, `.pdf`)
2. Sehr kleine Payloads (Komprimierungs-Overhead kann höher sein als der Nutzen)

#### Operative Best Practices

1. Threshold nutzen, um winzige Responses zu überspringen.
2. Sicherstellen, dass Cache/Proxy `Vary: Accept-Encoding` respektiert.
3. CPU-Overhead vs Bandbreitenersparnis messen.
4. Bei High-Traffic Workloads Proxy/CDN-Komprimierung bevorzugen.
5. TLS + Komprimierungsrisiken in sensitiven Kontexten beachten (modern selten,
   aber Plattform-Guidance befolgen).

#### Fastify-Hinweis

Beim Fastify-Adapter das entsprechende Fastify-Compression-Plugin statt
Express-Middleware verwenden.

#### Praktische Empfehlung

Komprimierung standardmäßig für API-Responses aktivieren und anschließend
Threshold sowie Platzierung (App vs Edge/Proxy) anhand realen Traffics und
CPU-Profils tunen.

</details>

<details>
<summary>61. Wie implementiert man Helmet und welche HTTP-Header setzt es?</summary>

#### NestJS

Helmet ist eine Security-Middleware, die schützende HTTP-Header setzt, um die
Angriffsfläche typischer Webangriffe zu reduzieren (XSS, Clickjacking,
MIME-Sniffing, Datenlecks via Referrer usw.).

In NestJS (Express-Adapter) wird es global in `main.ts` integriert.

#### Basis-Setup

1. `helmet` installieren.
2. Als Middleware registrieren.

```ts
import { NestFactory } from '@nestjs/core';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    helmet({
      // CSP/HSTS/etc. je nach Umgebungsanforderungen konfigurieren
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

#### Häufige Header, die Helmet setzt (versions-/config-abhängig)

1. `Content-Security-Policy` (CSP)
2. `Cross-Origin-Opener-Policy`
3. `Cross-Origin-Resource-Policy`
4. `Origin-Agent-Cluster`
5. `Referrer-Policy`
6. `Strict-Transport-Security` (HSTS, wenn HTTPS-Kontext passend ist)
7. `X-Content-Type-Options: nosniff`
8. `X-DNS-Prefetch-Control`
9. `X-Download-Options` (Legacy-IE-Schutz)
10. `X-Frame-Options` (Clickjacking-Schutz)
11. `X-Permitted-Cross-Domain-Policies`
12. Verhalten rund um `X-XSS-Protection` (legacy; moderne Browser verlassen sich auf CSP)

Exakte Defaults können je nach Helmet-Version und Runtime-Umgebung variieren.

#### Praktische Konfigurationshinweise

1. **CSP-Tuning ist kritisch**
   Striktes CSP erhöht Sicherheit, kann aber Scripts/Styles brechen, wenn es nicht korrekt konfiguriert ist.

2. **HSTS nur auf HTTPS**
   In Production-Domains mit Bedacht aktivieren; versehentliches Lock-in auf lokal/dev vermeiden.

3. **CORS + Helmet**
   Lösen unterschiedliche Probleme; beide explizit konfigurieren.

4. **Reverse-Proxy-Bewusstsein**
   Trusted Proxy-/HTTPS-Termination-Konfiguration muss für korrektes HSTS/Security-Verhalten stimmen.

#### Typisches Production-Muster

1. Helmet global aktivieren.
2. CSP-Directives für Frontend/API-Verhalten anpassen.
3. Getrennte Config-Profile für dev vs production pflegen.
4. Header über Integrationstests und Security-Scans verifizieren.

#### Faustregel

Helmet liefert gute Baseline-Härtung, ist aber nicht die ganze Security.
Kombinieren mit Auth, Validierung, Rate Limits, sicheren Cookies und
Dependency-Hygiene.

</details>

<details>
<summary>62. Was sind die wichtigsten OWASP-Schwachstellen und wie schützt man sich dagegen?</summary>

#### NestJS

OWASP-Top-Risiken sind häufige Klassen von Web-Sicherheitsfehlern. In NestJS
erfolgt die Mitigation über mehrschichtige Controls: Validierung, Auth,
sichere Defaults, Monitoring und Infrastruktur-Härtung.

#### Wichtige OWASP-Risiken und NestJS-orientierte Schutzmaßnahmen

1. **Broken Access Control**
   1. Guards für Authz nutzen (`RolesGuard`, Policy-/ABAC-Guards).
   2. Ownership-Checks beim Ressourcenzugriff erzwingen.
   3. Default deny; impliziten Zugriff vermeiden.

2. **Cryptographic Failures**
   1. HTTPS überall nutzen.
   2. Passwörter mit starken Algorithmen hashen (argon2/bcrypt mit passendem Cost).
   3. Secrets im Secret Manager halten, nicht im Source Code.
   4. Sensible Daten at rest verschlüsseln, wo erforderlich.

3. **Injection (SQL/NoSQL/Command)**
   1. Parameterisierte ORM-Queries (TypeORM/Prisma) verwenden.
   2. Input via DTO + `ValidationPipe` validieren/whitelisten.
   3. String-gebastelte Raw-Queries und Shell-Commands mit User-Input vermeiden.

4. **Insecure Design**
   1. Threat Modeling für kritische Flows (Auth, Payments, Admin) anwenden.
   2. Idempotenz, Rate Limits und Abuse-Controls by design ergänzen.
   3. Least Privilege in Architekturgrenzen umsetzen.

5. **Security Misconfiguration**
   1. Helmet und striktes CORS aktivieren.
   2. Debug-Defaults in Production deaktivieren.
   3. Production-Umgebung getrennt und gehärtet halten.

6. **Vulnerable and Outdated Components**
   1. Dependencies regelmäßig aktualisieren.
   2. SCA-Scans in CI nutzen (`npm audit`, Snyk, Dependabot usw.).
   3. Unbenutzte Pakete entfernen.

7. **Identification and Authentication Failures**
   1. Kurzlebige Access-Tokens + Refresh-Rotation.
   2. MFA für High-Risk-Accounts.
   3. Sichere Cookie/Token-Handhabung, Lockout/Rate-Limit für Login-Endpunkte.

8. **Software and Data Integrity Failures**
   1. Signierte Artefakte, vertrauenswürdige CI/CD-Pipeline.
   2. Third-Party-Quellen verifizieren und Versionen pinnen.
   3. Config-Änderungen und Release-Freigaben kontrollieren.

9. **Security Logging and Monitoring Failures**
   1. Strukturierte Logs mit requestId/userId/action/outcome.
   2. Alerting auf Auth-Anomalien und Error-Spitzen.
   3. Stack Traces in Logs erhalten, nicht in Responses.

10. **Server-Side Request Forgery (SSRF)**
   1. Outbound-Netzwerkziele einschränken.
   2. Externe URLs validieren und whitelisten.
   3. Interne Metadata-IP-Ranges blockieren.

#### NestJS-Baseline-Checkliste

1. Globale `ValidationPipe` (`whitelist`, `forbidNonWhitelisted`, `transform`).
2. Globaler Exception Filter mit sicheren Fehler-Responses.
3. Auth + Authorization Guards auf geschützten Routen.
4. Rate Limiting (`@nestjs/throttler`) auf sensitiven Endpunkten.
5. Helmet + strikte CORS-Konfiguration.
6. Sichere Config mit Startup-Validierung (Joi/Zod).
7. Dependency-/Security-Scans in CI.

#### Praktischer Kernpunkt

Security ist kein einzelnes Paket. In NestJS entsteht eine starke
Sicherheitsposition durch konsistente Defense-in-Depth über Code, Config,
Infrastruktur und Betrieb.

</details>

<details>
<summary>63. Wie verwendet man `HttpModule` (axios) in NestJS für externe API-Requests?</summary>

#### NestJS

In NestJS werden externe HTTP-Calls typischerweise über `HttpModule` aus
`@nestjs/axios` gemacht. Es kapselt Axios und integriert es in DI.

#### Warum `HttpModule` nutzen

1. DI-freundlicher gemeinsamer HTTP-Client.
2. Zentrale Konfiguration (base URL, timeout, headers).
3. Einfaches Testen/Mocking.
4. Eingebaute RxJS-Integration (`Observable`-Responses).

#### Schritt 1: `HttpModule` registrieren

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

Asynchrone Config-Variante:
`HttpModule.registerAsync(...)` mit `ConfigService`.

#### Schritt 2: `HttpService` in Provider injizieren

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

#### Error-Handling-Pattern

1. Axios-Fehler abfangen und in Domain-/App-Exceptions mappen.
2. Rohe Upstream-Fehler nicht direkt an API-Clients leaken.

```ts
try {
  const res = await firstValueFrom(this.http.get('/health'));
  return res.data;
} catch (e: any) {
  const status = e?.response?.status;
  throw new BadGatewayException(`Upstream error: ${status ?? 'unknown'}`);
}
```

#### Production-Best-Practices

1. Strikte Timeouts für alle Outbound-Calls setzen.
2. Retries/Circuit Breaker für instabile Abhängigkeiten ergänzen.
3. Request-/Correlation-IDs in Headern propagieren.
4. Typisierte Response-DTOs/Adapter für externe Contracts nutzen.
5. Latenz, Fehler und Upstream-Statuscodes instrumentieren.

#### Teststrategie

1. `HttpService` in Unit-Tests mocken.
2. Für Integrationstests Mock-Server verwenden (z. B. nock/wiremock).
3. Timeout-/Retry-/Error-Mapping-Pfade explizit validieren.

#### Praktischer Kernpunkt

Externe HTTP-Calls als unzuverlässiges I/O behandeln: `HttpModule` zentral
konfigurieren, in dedizierte Client-Services kapseln und robuste
Timeout-/Retry-/Error-Policies durchsetzen.

</details>

<details>
<summary>64. Wie fügt man globale Interceptors zu axios in NestJS hinzu? (Header hinzufügen, Logging)</summary>

#### NestJS

In NestJS werden Axios-Interceptors auf der `axiosRef`-Instanz konfiguriert,
die `HttpService` (`@nestjs/axios`) bereitstellt. So lassen sich globale
Verhaltensweisen für Outbound-Requests anwenden: Header, Logging, Timing,
Auth-Tokens und Error-Normalisierung.

#### Warum Axios-Interceptors nutzen

1. Outbound-HTTP-Verhalten zentralisieren.
2. Wiederholte Header-/Auth-Logik in jedem Call vermeiden.
3. Konsistentes Request-/Response-Logging und Metriken ergänzen.
4. Upstream-Fehler an einer Stelle normalisieren.

#### Typisches Implementierungsmuster

1. Provider/Service erstellen, der `HttpService` erhält.
2. Im Modul-Init-Lifecycle Request-/Response-Interceptors einmal registrieren.
3. Interceptor-Logik leichtgewichtig und deterministisch halten.

#### Beispiel: globale Outbound-Header + Logging

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

Diesen Provider in einem Modul registrieren, das `HttpModule` importiert.

#### Wichtige Production-Hinweise

1. Sicherstellen, dass Interceptors nur einmal registriert werden (keine Duplikate bei Hot Reload/Module-Reinit).
2. Correlation-/Request-IDs aus dem Inbound-Request-Kontext propagieren.
3. Secrets (Authorization, API Keys) in Logs redaktieren.
4. Timeout-/Retry-/Circuit-Breaker-Strategie explizit halten (Interceptors sind keine vollständige Resilience-Schicht).

#### Häufige Use Cases

1. Auth-Tokens aus `ConfigService` oder Token-Providern injizieren.
2. Tenant-/Kontext-Header für Downstream-Services hinzufügen.
3. Error-Objekte vor dem Rethrow standardisieren.
4. Metriken/Traces für Observability-Systeme emittieren.

#### Praktischer Kernpunkt

Axios-Interceptors als Outbound-Äquivalent zu Nest-Middleware nutzen: ein
zentraler Ort für cross-cutting HTTP-Client-Policies über alle externen
API-Calls.

</details>

<details>
<summary>65. Wie typisiert man externe API-Responses in TypeScript korrekt?</summary>

#### NestJS

Korrekte Typisierung externer API-Responses bedeutet, Remote-Daten bis zur
Validierung als **untrusted** zu behandeln und gleichzeitig TypeScript-Typen für
Developer-Ergonomie zu nutzen.

#### Kernprinzip

1. Compile-Time-Typen (`interface`/`type`) verbessern DX.
2. Runtime-Validierung (Zod/class-validator/custom guards) stellt Sicherheit her.
3. Beides verwenden, nicht nur eines.

#### Empfohlenes Muster

1. Response-DTO/-Typ für erwartete Struktur definieren.
2. Daten über typisierten HTTP-Client-Call laden.
3. An der Boundary validieren/parsen.
4. Vor Business-Logik auf internes Domänenmodell mappen.

#### Beispiel mit `HttpService` + Zod

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

#### Warum Generics allein nicht reichen

```ts
this.http.get<MyType>(...)
```

Das sagt TypeScript nur, was du *erwartest*; es verifiziert nicht die echte
Runtime-Payload vom Upstream-Service.

#### Praktische Typisierungsstrategien

1. Dedizierte Client-Module pro Upstream-API nutzen.
2. Upstream-DTOs getrennt von internen Domain-Entities halten.
3. Externe Enums/Feldnamen an der Boundary normalisieren/transformieren.
4. Nullable-/Optional-Handling explizit abbilden (`null` vom Upstream ist häufig).

#### Best Practices für Error Handling

1. Transportfehler (timeout, 5xx) von Schemafehlern unterscheiden.
2. Beide auf stabile interne Exceptions mappen.
3. Upstream-Response-Metadaten zur Diagnostik loggen (ohne Secrets zu leaken).

#### Faustregel

Externe Responses doppelt typisieren:
1. statischer Typ für Code-Intelligence,
2. Runtime-Schema-Validierung für Korrektheit und Sicherheit.

</details>

<details>
<summary>66. Wie implementiert man Retry-Logik für externe HTTP-Requests in NestJS?</summary>

#### NestJS

Retry-Logik hilft bei transienten Fehlern (Timeouts, temporäre 5xx,
kurze Netzwerkstörungen) beim Aufruf externer APIs.

In NestJS werden Retries häufig mit RxJS-Operatoren auf `HttpService` oder mit
Resilience-Libraries an der Client-Boundary umgesetzt.

#### Wann Retries sinnvoll sind

1. Timeout-/Netzwerkfehler.
2. Temporäre Upstream-5xx.
3. Rate-Limit-Responses mit Retry-Hinweisen (`429` mit `Retry-After`).

#### Wann Retries gefährlich sind

1. Nicht-idempotente Operationen ohne Idempotency Keys.
2. Permanente Fehler (`400`, `401`, `403`, Validierungsfehler).
3. Große Retry-Stürme bei Upstream-Outages.

#### Basis-Retry mit RxJS

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

#### Empfohlene Retry-Policy

1. Exponential Backoff verwenden.
2. Jitter hinzufügen, um synchronisierte Retry-Spitzen zu vermeiden.
3. Maximalversuche strikt begrenzen.
4. Nur idempotente Operationen oder idempotency-geschützte Writes retrien.

#### Retries mit Schutzmechanismen kombinieren

1. Globalen Timeout pro Request setzen.
2. Circuit Breaker bei andauernden Fehlern einsetzen.
3. Rate Limiting und Bulkheads auf Outbound-Clients anwenden.
4. Zentrale Metriken: Retry-Anzahl, finale Fehlerquote, Latenzeffekt.

#### Praktische Regel

Retries sollen Zuverlässigkeit verbessern, nicht Outages verstecken. Selektiv,
begrenzt und beobachtbar halten.

</details>

<details>
<summary>67. Was ist das Circuit-Breaker-Pattern und wann braucht man es?</summary>

#### NestJS

Der Circuit Breaker ist ein Resilience-Pattern, das wiederholte Calls zu einer
fehlerhaften Abhängigkeit verhindert. Statt endlos einen kaputten Upstream zu
retrien, „öffnet“ er den Circuit und schlägt für eine Zeit schnell fehl.

#### Warum ein Circuit Breaker nötig ist

1. Verhindert kaskadierende Fehler über Services hinweg.
2. Reduziert Ressourcenerschöpfung (Threads/Connections/Event-Loop-Druck).
3. Verbessert Latenz in Outages durch Fast-Fail.
4. Gibt instabilen Abhängigkeiten Zeit zur Erholung.

#### Circuit-Zustände

1. **Closed**
   Normalbetrieb, Requests werden durchgelassen.

2. **Open**
   Abhängigkeit gilt als ungesund; Calls werden sofort blockiert.

3. **Half-open**
   Begrenzte Probe-Requests testen die Erholung.
   Bei Erfolg -> schließen; bei Fehler -> wieder öffnen.

#### Wann man ihn einsetzen sollte

1. Bei Calls zu externen APIs/Payment-Providern/Identity-Services.
2. Wenn die Abhängigkeit spürbare Fehlerraten oder Latenzspitzen hat.
3. Wenn der Service high-traffic ist und Retries Incidents verstärken können.
4. Wenn das Business Fallback-Verhalten bei Upstream-Ausfall toleriert.

#### Typische NestJS-Integration

1. Externen Client-Call in eine Breaker-Policy kapseln.
2. Mit Timeout + Retry (begrenzt) + Fallback kombinieren.
3. Metriken/Events für Breaker-State-Changes emittieren.

Konzeptioneller Flow:

```text
request -> timeout check -> circuit breaker -> outbound call
        -> success: normal response
        -> failure threshold exceeded: circuit OPEN
        -> OPEN: fail fast / fallback
```

#### Praktische Implementierungsoptionen

1. Resilience-Libraries (z. B. opossum) um `HttpService`-Calls verwenden.
2. Für begrenzte Use Cases eigenen leichten Breaker bauen.
3. Breaker-Config über `ConfigService` externalisieren.

#### Wichtige Tuning-Parameter

1. Failure Threshold (% oder Count).
2. Rolling-Window-Größe.
3. Open-State-Cooldown-Dauer.
4. Half-open-Probe-Count.
5. Timeout pro Call.

#### Häufige Fehler

1. Breaker ohne Observability verwenden (keine State-Metriken/Logs).
2. Zu aggressive Thresholds, die False-Opens verursachen.
3. Fehlende Fallback-Strategie für Open-State.
4. Unendliche Retries mit Breaker kombinieren (hebt den Zweck auf).

#### Faustregel

Wenn ein Upstream-Fehler deinen gesamten Service degradieren kann, einen
Circuit Breaker an dieser Boundary ergänzen und State-Transitions als
First-Class-SRE-Signale monitoren.

</details>

<details>
<summary>68. Wie implementiert man Caching (In-Memory, Redis) und wann sollte man welchen Ansatz nutzen?</summary>

#### NestJS

Caching speichert vorab berechnete/häufig angefragte Daten, um Latenz und
Backend-Last zu reduzieren. In NestJS sind gängige Optionen In-Memory-Cache und
Redis-Cache.

#### In-Memory vs Redis

1. **In-Memory-Cache**
   Wird im Speicher eines einzelnen App-Prozesses gehalten.

2. **Redis-Cache**
   Externer geteilter Cache-Service, auf den alle App-Instanzen zugreifen.

#### Wann In-Memory-Cache sinnvoll ist

1. Single-Instance-Apps oder lokale Entwicklung.
2. Kleine, kurzlebige Cache-Werte.
3. Ultra-niedrige lokale Read-Latenz.

Einschränkungen:
1. Nicht über Replikas geteilt.
2. Bei Prozess-Neustart/Deploy verloren.
3. Memory-Druck beeinflusst den App-Prozess.

#### Wann Redis-Cache sinnvoll ist

1. Multi-Instance-/verteilte Deployments.
2. Serviceübergreifend geteilter Cache.
3. Bedarf an zentralem TTL-/Invalidierungsverhalten.
4. Höhere Anforderungen an Zuverlässigkeit und Observability.

Trade-off:
1. Network-Hop fügt kleine Latenz hinzu.

#### NestJS-Implementierungsoptionen

1. `CacheModule` + cache-manager-Adapter.
2. Manueller Redis-Client für fortgeschrittene Patterns.
3. `CacheInterceptor` für response-level Caching auf ausgewählten Endpoints.

#### Konzeptionelles `CacheModule`-Setup

In-Memory:

```ts
CacheModule.register({
  ttl: 30_000,
  max: 500,
});
```

Redis (adapter-spezifische Config):

```ts
CacheModule.registerAsync({
  useFactory: () => ({
    store: /* redis store adapter */,
    url: process.env.REDIS_URL,
    ttl: 60_000,
  }),
});
```

#### Was gecacht werden sollte

1. Read-heavy, selten veränderte Referenzdaten.
2. Teure berechnete Aggregate.
3. Externe API-Responses mit klarer Staleness-Toleranz.

#### Was man nicht blind cachen sollte

1. Stark volatile Daten ohne Invalidierungsplan.
2. Security-sensitive per-user Daten ohne scoped Keys.
3. Write-kritische Pfade, bei denen stale Reads inakzeptabel sind.

#### Wichtige Design-Praktiken

1. Explizite Key-Namen nutzen (`user:{id}`, `catalog:v2:{region}`).
2. TTL bewusst je Datentyp setzen.
3. Cache-aside-Pattern ergänzen:
   read -> miss -> source laden -> cache setzen -> return.
4. Invalidierung bei Writes/Events planen.
5. Hit-Rate, Evictions und Stale-Read-Auswirkung monitoren.

#### Faustregel

In-Memory nur für einfache/single-node Fälle starten. Für Production mit
mehreren Instanzen oder Shared-State-Anforderungen auf Redis-basiertes Caching
wechseln.

</details>

<details>
<summary>69. Was ist Cache-Invalidierung und wie implementiert man sie korrekt?</summary>

#### NestJS

Cache-Invalidierung ist der Prozess, gecachte Daten zu entfernen/aktualisieren,
wenn sich Quelldaten ändern, damit Clients keine veralteten Responses erhalten.

Sie ist oft der schwierigste Teil des Cachings, weil Korrektheit von
Konsistenzregeln abhängt, nicht nur von Geschwindigkeit.

#### Warum Invalidierung wichtig ist

1. Verhindert veraltete oder inkonsistente, für Nutzer sichtbare Daten.
2. Hält den Cache mit Writes synchron.
3. Vermeidet subtile Bugs in business-kritischen Flows.

#### Gängige Invalidierungsstrategien

1. **TTL-basierte Expiration**
   Cache-Keys laufen nach fester Zeit automatisch ab.

2. **Event-/Write-getriebene Invalidierung**
   Nach erfolgreichem Write verwandte Cache-Keys explizit löschen/aktualisieren.

3. **Versionierte Keys**
   Version/Tag im Key aufnehmen, sodass neue Writes Reads natürlich in neuen Keyspace lenken.

4. **Tag-/Gruppen-Invalidierung** (wenn vom Tooling unterstützt)
   Mehrere verwandte Einträge per logischer Gruppe invalidieren.

#### Praktische Implementierungsmuster

1. **Cache-aside mit delete-on-write**
   1. Read: cache miss -> DB -> cache setzen.
   2. Write: DB updaten -> relevante cache keys löschen.

2. **Write-through**
   Cache und DB in einem Flow updaten (Vorsicht bei Fehlerhandling).

3. **Event-driven Invalidierung**
   Domain-Event (`user.updated`) publizieren und in Subscribers/Workern invalidieren.

#### Wichtige Designregeln

1. Vorhersagbares Key-Schema nutzen:
   `user:{id}`, `users:list:{filterHash}`, `product:{id}:v{n}`.

2. Write-to-key-Mapping explizit halten:
   welche Mutationen welche Read-Keys invalidieren.

3. Für kritische Hot Keys kurze TTL + explizite Invalidierung bevorzugen.

4. In Multi-Instance-Systemen Shared Cache (Redis) statt nur lokalen Speicher verwenden.

#### Beispiel-Invalidierungsfluss

```text
PATCH /users/42
 -> update DB
 -> del user:42
 -> del users:list:*
 -> return updated response
```

(List-Invalidierung kann selektiv sein, wenn Filter-/Index-Key-Sets getrackt werden.)

#### Häufige Fehler

1. List-Endpoints cachen, ohne zugehörige Detail-/List-Keys gemeinsam zu invalidieren.
2. Nur auf lange TTL bei häufig aktualisierten Daten setzen.
3. Gleichzeitige Writes/Race Conditions nicht behandeln.
4. Tenant-/User-Scoping in Keys vergessen.

#### Praktische Empfehlung

Einfach starten:
1. cache-aside,
2. kurze TTLs,
3. explizites delete-on-write.

Danach mit wachsender Domänenkomplexität zu event-driven/tag-basierter
Invalidierung weiterentwickeln.

</details>

<details>
<summary>70. Wann sollte man in NestJS Observables statt Promises verwenden?</summary>

#### NestJS

Observables in NestJS verwenden, wenn **Streams, Cancellation, Komposition
mehrerer asynchroner Events oder reaktive Operatoren** nötig sind. Für einfache
One-shot-Async-Operationen Promises nutzen.

#### Kerndifferenz

1. **Promise**
   Ein einzelner zukünftiger Wert (oder Fehler), löst genau einmal auf.

2. **Observable**
   Lazy Stream von 0..N Werten über Zeit, mit reichhaltigen RxJS-Operatoren und
   Cancellation.

#### Wann Observables besser passen

1. **Streaming-Use-Cases**
   Server-Sent Events, websocket-ähnliche Flows, chunked Responses.

2. **Komposition mehrerer Async-Quellen**
   Timer, HTTP-Calls, User-Events und Retries per Operatoren kombinieren.

3. **Fortgeschrittenes Retry/Backoff/Circuit-Verhalten**
   RxJS-Operatoren (`retryWhen`, `timeout`, `catchError`, `switchMap` usw.).

4. **Cancellation-aware Flows**
   Durch Unsubscribe Arbeit stoppen und Ressourcen freigeben.

5. **Nest-Ökosystem-Features**
   Interceptors und `HttpService` liefern natürlicherweise Observables.

#### Wann Promise vorzuziehen ist

1. One request -> one response DB/API-Call.
2. Geradlinige Service-Methodenlogik mit `async/await`.
3. Team nutzt reaktive Patterns nicht tief.

#### Praktische NestJS-Beispiele

1. `HttpService.get(...)` gibt `Observable<AxiosResponse<T>>` zurück.
2. SSE-Endpoints geben häufig `Observable<MessageEvent>` zurück.
3. Microservice-Message-Patterns können reaktive Streams nutzen.

#### Interop-Pattern

Wenn deine App `async/await` nutzt, aber ein Observable erhält:

```ts
const response = await firstValueFrom(this.http.get('/users'));
```

Wenn nur ein Wert aus dem Stream benötigt wird, bewusst konvertieren
(`firstValueFrom` oder `lastValueFrom`) und Boundaries klar halten.

#### Entscheidungs-Faustregel

1. Ein Wert einmal nötig -> Promise (`async/await`).
2. Stream/Retry-Komposition/Cancellation nötig -> Observable.

Pro Modul-Boundary möglichst einen Stil wählen, um gemischte Async-Komplexität
zu vermeiden.

</details>

<details>
<summary>71. Was ist der Unterschied zwischen async/await und RxJS für asynchrone Logik, und wann sollte man welchen Ansatz nutzen?</summary>

#### NestJS

`async/await` und RxJS lösen asynchrone Arbeit auf unterschiedlichen
Komplexitätsstufen. Keiner ist pauschal besser; die Wahl hängt vom
Ausführungsmodell ab.

#### Kerndifferenz

1. **`async/await` (Promises)**
   Am besten für Async-Tasks mit Einzelergebnis und linearem Control Flow.

2. **RxJS (Observables)**
   Am besten für Event-Streams, Multi-Value-Flows, Cancellation und
   fortgeschrittene Komposition über Zeit.

#### Stärken von `async/await`

1. Sehr lesbarer imperativer Code.
2. Einfaches Error Handling mit `try/catch`.
3. Ideal für Request-Response-Service-Methoden (DB/API einmal).
4. Niedrigere kognitive Last für die meisten Teams.

#### Stärken von RxJS

1. Komposition mehrerer Async-Streams (`mergeMap`, `switchMap`, `combineLatest`).
2. Leistungsstarke Retry-/Backoff-/Timeout-Operatoren.
3. Native Cancellation via Unsubscribe.
4. Stream-Processing-Patterns (SSE, Websockets, reaktive Pipelines).

#### Typischer NestJS-Usage-Split

1. **Services/Controller**
   Häufig `async/await` für Business-Use-Cases.

2. **`HttpService` / Interceptors / Streaming-Endpoints**
   Häufig Observables, optional zu Promise konvertiert, wenn nur ein Wert nötig ist.

#### Interoperabilität

Observable -> Promise:

```ts
const res = await firstValueFrom(this.http.get('/health'));
```

Promise -> Observable:

```ts
from(this.usersService.findById(id))
```

#### Wann `async/await` wählen

1. CRUD-artige Endpoints.
2. One-shot DB/API-Calls.
3. Team bevorzugt geradlinigen Control Flow.

#### Wann RxJS wählen

1. Kontinuierliche Streams oder Realtime-Pipelines.
2. Komplexe Orchestrierung mehrerer Async-Quellen.
3. Bedarf an cancellation-aware Verhalten und operatorbasierter Flow-Steuerung.

#### Häufige Fehler

1. RxJS für triviale one-off Operationen verwenden (Overengineering).
2. Promise-Stil in Streaming-Szenarien erzwingen (reaktive Vorteile gehen verloren).
3. Beide Stile chaotisch im selben Modul mischen.

#### Praktische Regel

Standardmäßig `async/await` für einfache Business-Logik nutzen; RxJS dort
introduzieren, wo Reaktivität/Stream-Komposition klaren operativen Nutzen bringt.

</details>

<details>
<summary>72. Wie vermeidet man das Blockieren des Event Loops in NestJS und hält die Performance stabil?</summary>

#### NestJS

NestJS läuft auf dem Node.js Event Loop. Wenn du diesen Loop mit CPU-intensiven
oder synchronen Operationen blockierst, bekommen alle parallelen Requests
Latenzspitzen.

#### Was den Event Loop blockiert

1. Schwere synchrone CPU-Tasks (Hashing großer Payloads, Bild-/Videoverarbeitung).
2. Große synchrone JSON-Parsing-/Stringify-Schleifen.
3. Synchrone Dateisystem-APIs (`fs.readFileSync` usw.) auf dem Request-Pfad.
4. Lange enge Loops ohne Yield.
5. Teure Regex-Backtracking-Fälle und ineffiziente Algorithmen.

#### Praktische Strategien zur Vermeidung von Blocking

1. **Async-I/O-APIs bevorzugen**
   Nicht-blockierende Filesystem-/Network-/DB-Operationen nutzen.

2. **CPU-schwere Arbeit vom Request-Thread auslagern**
   1. Worker Threads (`worker_threads`)
   2. Background Jobs/Queues (BullMQ, RabbitMQ usw.)
   3. Dedizierte Processing-Services

3. **Streaming für große Payloads verwenden**
   Große Dateien/Objekte nicht komplett im Speicher puffern.

4. **Arbeit paginieren und in Chunks verarbeiten**
   Große Datensätze in Batches statt in einer riesigen synchronen Operation bearbeiten.

5. **Teure Berechnungen cachen**
   Ergebnisse, wo möglich, wiederverwenden.

#### NestJS-Architektur-Patterns

1. Controller schlank halten; schwere Aufgaben an asynchrone Worker delegieren.
2. Queues für E-Mail/PDF/Report-Generierung/Media-Konvertierung nutzen.
3. Timeouts und Backpressure-Policies auf externe Calls setzen.
4. Rate Limiting auf teuren Endpunkten anwenden.

#### Monitoring-Signale für Event-Loop-Blocking

1. Steigende p95/p99-Latenz bei moderatem Traffic.
2. Niedrige CPU-Idle-Zeit bei dennoch schwachem Durchsatz.
3. Verzögerte Timer und langsame Health Checks.
4. Wachsende Event-Loop-Lag-Metriken.

#### Hilfreiche operative Tools

1. Event-Loop-Lag-Monitoring (`perf_hooks`, APM-Tools).
2. CPU-Profiling/Flamegraphs für Hot Paths.
3. Endpoint-Latenz- und Payload-Größen-Dashboards.

#### Häufige Fehler

1. Synchrone Crypto/Compression in Request-Handlern ausführen.
2. Große Reports inline während des HTTP-Requests erzeugen.
3. Riesige Dateien in den Speicher laden statt zu streamen.
4. Algorithmische Komplexität in Loops über große Arrays ignorieren.

#### Faustregel

Der Request-Thread soll orchestrieren, nicht schwer rechnen. Non-blocking halten
und teure Arbeit an asynchrone Infrastruktur delegieren.

</details>

<details>
<summary>73. Wie optimiert man Latenz (p95 / p99) und was beeinflusst diese Metriken?</summary>

#### NestJS

`p95` und `p99` sind Tail-Latenz-Perzentile: Sie zeigen, wie langsam die
schlechtesten 5% bzw. 1% der Requests sind. Production-Zuverlässigkeit hängt
stärker von diesen Tails als von Durchschnittslatenz ab.

#### Was p95/p99 am meisten beeinflusst

1. Ineffiziente DB-Queries (N+1, fehlende Indizes, Lock-Contention).
2. Langsame externe Abhängigkeiten (HTTP-APIs, Queues, Auth-Provider).
3. Event-Loop-Blocking (CPU-heavy Sync-Tasks).
4. Connection-Pool-Sättigung (DB/HTTP).
5. Payload-Größe und Serialisierungs-Overhead.
6. Cache-Miss-Raten und Cold Starts.
7. GC-Pausen und Memory-Druck.
8. Retry-Stürme/Timeout-Kaskaden bei Fehlern.

#### Optimierungsstrategie (höchster Impact zuerst)

1. **Zuerst messen**
   Endpoint-Level p50/p95/p99 Dashboards und Trace-Spans je Abhängigkeit ergänzen.

2. **Hot-DB-Pfade beheben**
   Kritische Filter indizieren, N+1 entfernen, Joins optimieren, korrekt paginieren.

3. **Externe Calls absichern**
   Strikte Timeouts, begrenzte Retries mit Jitter, Circuit Breaker, Fallbacks.

4. **Arbeit im Request-Pfad reduzieren**
   CPU-schwere Tasks in Worker/Queues auslagern; HTTP-Pfad leicht halten.

5. **Smart cachen**
   Read-heavy teure Daten cachen (Redis/In-Memory je nach Bedarf).

6. **Pools und Concurrency tunen**
   DB/HTTP-Pools richtig dimensionieren und Queue-Aufbau vermeiden.

7. **Payloads kontrollieren**
   Response-Felder begrenzen, Komprimierung nutzen, gigantische JSON-Objekte vermeiden.

#### NestJS-spezifische praktische Maßnahmen

1. Interceptor-basiertes Latenz-Logging mit requestId ergänzen.
2. Downstream-Calls (DB und HttpService) mit Timing und Status instrumentieren.
3. Globale Timeout-Policies für Upstream-Calls einsetzen.
4. Rate Limiting auf teuren Endpunkten anwenden.
5. Background Jobs für nicht-kritische synchrone Tasks nutzen.

#### Typische Tail-Latenz-Anti-Patterns

1. Endpoint macht mehrere sequenzielle externe Calls.
2. Lange DB-Transaktionen auf Read-Pfaden.
3. Per-Request-Cache-Warmups ohne Memoization.
4. Massive DTO-Transformationen in Hot Paths.

#### SLO-orientierter Ansatz

1. Latenz-SLOs pro Endpoint-Klasse definieren (read, write, auth).
2. Auf p95/p99-Verletzungen alerten (nicht nur auf Durchschnitt).
3. Lasttests mit produktionsnaher Traffic-Verteilung durchführen.
4. Regressionen pro Release via CI-Perf-Checks tracken, wo möglich.

#### Faustregel

Um p99 zu verbessern, Worst-Case-Pfade und Fehlerverhalten optimieren, nicht nur
Median-Codepfade. Tail-Latenz ist vor allem ein System- und Abhängigkeitsproblem.

</details>

<details>
<summary>74. Wie nutzt man den Cluster-Modus in Node.js zusammen mit NestJS zur Skalierung?</summary>

#### NestJS

Der Cluster-Modus startet mehrere Node.js-Worker-Prozesse auf einer Maschine,
sodass eine NestJS-App mehrere CPU-Kerne statt nur eines Event Loops nutzen kann.

#### Warum Cluster-Modus nutzen

1. Bessere CPU-Auslastung auf Multi-Core-Servern.
2. Höherer Durchsatz bei CPU-/Mixed-Workloads.
3. Prozess-Isolation (ein Worker-Crash killt nicht alle Worker).

#### Grundkonzept des Cluster-Setups

1. Primärprozess forkt `N` Worker (`N` oft = CPU-Kerne).
2. Jeder Worker startet die Nest-App auf demselben Port.
3. Node verteilt eingehende Verbindungen auf Worker.

#### Beispiel-Bootstrap (konzeptionell)

```ts
import cluster from 'cluster';
import { cpus } from 'os';
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrapWorker() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}

if (cluster.isPrimary) {
  const workerCount = cpus().length;
  for (let i = 0; i < workerCount; i++) cluster.fork();

  cluster.on('exit', () => {
    cluster.fork(); // naiver Auto-Restart
  });
} else {
  bootstrapWorker();
}
```

#### Wichtige Production-Aspekte

1. **Statelessness**
   In-Memory-State ist pro Worker getrennt und nicht geteilt.
   Redis/DB für gemeinsame Sessions/Cache/Locks verwenden.

2. **WebSockets**
   Sticky Sessions oder externer Pub/Sub-Adapter für Multi-Worker-Konsistenz nötig.

3. **Rate Limiting/Cache**
   In-Memory-Implementierungen werden über Worker inkonsistent.
   Redis-gestützte Stores bevorzugen.

4. **Graceful Shutdown**
   SIGTERM/SIGINT behandeln und Connections pro Worker sauber drainen.

5. **Observability**
   Worker-ID/Process-ID in Logs und Metriken aufnehmen.

#### Cluster vs Container/Orchestrierung

1. Cluster skaliert vertikal innerhalb eines Hosts.
2. Kubernetes/PM2/systemd-Replikate skalieren horizontal über Hosts.
3. Viele Teams skalieren zuerst horizontal und nutzen Cluster nur bei Bedarf.

#### Wann Cluster-Modus gut passt

1. Bare-Metal-/VM-Deployments mit Multi-Core-CPU.
2. Mehr Durchsatz nötig ohne sofortige Infrastrukturänderung.
3. App ist weitgehend stateless und bereit für Multi-Prozess-Verhalten.

#### Faustregel

Cluster kann Single-Host-Durchsatz steigern, ersetzt aber keine verteilte
Architektur. Mit externalisiertem State und solidem Prozessmanagement kombinieren.

</details>

<details>
<summary>75. Wie implementiert man Cron-Jobs in NestJS via `@nestjs/schedule`?</summary>

#### NestJS

In NestJS werden Cron-Jobs mit `@nestjs/schedule` umgesetzt. Das Paket bietet
deklarative Decorators für feste Intervalle, Timeouts und Cron-Expressions.

#### Schritt 1: ScheduleModule installieren und aktivieren

```ts
import { Module } from '@nestjs/common';
import { ScheduleModule } from '@nestjs/schedule';

@Module({
  imports: [ScheduleModule.forRoot()],
})
export class AppModule {}
```

#### Schritt 2: Scheduled Service erstellen

```ts
import { Injectable, Logger } from '@nestjs/common';
import { Cron, CronExpression, Interval, Timeout } from '@nestjs/schedule';

@Injectable()
export class JobsService {
  private readonly logger = new Logger(JobsService.name);

  @Cron(CronExpression.EVERY_DAY_AT_MIDNIGHT)
  handleDailyJob() {
    this.logger.log('Running daily job');
  }

  @Interval(60_000)
  handleEveryMinute() {
    this.logger.log('Running interval job');
  }

  @Timeout(10_000)
  handleStartupDelayedTask() {
    this.logger.log('Running one-time delayed task');
  }
}
```

#### Custom-Cron-Expression mit Zeitzone

```ts
@Cron('0 9 * * 1-5', { timeZone: 'Europe/Kyiv' })
runWeekdayAt9am() {}
```

#### Dynamische Cron-Jobs (runtime)

Für user-konfigurierbare Zeitpläne `SchedulerRegistry` nutzen, um Jobs zur
Laufzeit hinzuzufügen/zu entfernen statt statischer Decorators.

#### Production-Aspekte

1. **Multi-Instance-Duplikationsrisiko**
   In skalierten Deployments läuft Cron auf jeder Instanz, wenn nicht koordiniert.
   Distributed Locking (Redis/DB-Lock) nutzen oder Jobs in dediziertem Worker ausführen.

2. **Idempotenz**
   Job-Handler sollten bei Retries/Re-Runs sicher sein.

3. **Error Handling**
   Jobs mit try/catch und strukturierten Logs/Alerts kapseln.

4. **Timeouts und Backpressure**
   Überlappende lange Ausführungen vermeiden, außer wenn explizit gewünscht.

5. **Observability**
   Metriken emittieren: start/end/duration/success/failure.

#### Häufige Use Cases

1. Cleanup abgelaufener Sessions/Tokens.
2. Sync mit externen Systemen.
3. Geplante Reports/Benachrichtigungen.
4. Datenaggregation und Cache-Warmup.

#### Faustregel

`@nestjs/schedule` ist ideal für App-level Scheduling, aber in verteilten
Systemen ist Koordination nötig, um doppelte Ausführungen zu verhindern.

</details>

<details>
<summary>76. Was ist EventEmitter in NestJS und wie unterscheidet es sich von Queues (Bull)?</summary>

#### NestJS

`EventEmitter` in NestJS (`@nestjs/event-emitter`) ist ein In-Process-Pub/Sub-
Mechanismus für interne Modulkommunikation. Er ist schnell und einfach, aber
nicht dauerhaft über Prozess-Crashes/Restarts hinweg.

Bull/BullMQ-Queues sind persistente Job-Processing-Systeme (meist Redis-basiert)
für Background-Ausführung, Retries und Zuverlässigkeit.

#### Kerndifferenz

1. **EventEmitter**
   1. In-Memory, gleicher Prozess.
   2. Fire-and-forget Modul-Events.
   3. Standardmäßig keine durable Persistenz.

2. **Bull/BullMQ**
   1. Persistenter Queue-Storage (Redis).
   2. Background-Worker verarbeiten Jobs.
   3. Retries, Delays, Backoff, Concurrency und Monitoring-Support.

#### Wann EventEmitter nutzen

1. Interne Domain-Events innerhalb einer Service-Instanz.
2. Leichtgewichtige Side Effects (Audit-Log-Trigger, Cache-Invalidierungssignal).
3. Nicht-kritische async Entkopplung, bei der gelegentlicher Verlust akzeptabel ist.

#### Wann Bull/BullMQ nutzen

1. Kritische Tasks, die Restarts überleben müssen.
2. Lang laufende/schwere Jobs (E-Mails, Reports, Media-Processing).
3. Bedarf an Retry/Backoff und Dead-Letter-Handling.
4. Bedarf an Workload-Smoothing und kontrollierter Concurrency.

#### Vergleich des Zuverlässigkeitsmodells

1. **EventEmitter**
   Wenn die App nach dem Emit und vor Handler-Ausführung crasht, kann das Event verloren gehen.

2. **Queue**
   Job ist persistent; Worker kann später mit Retry-Policies fortsetzen.

#### Latenz- und Komplexitäts-Trade-off

1. EventEmitter:
   Niedrigere Latenz, geringere operative Komplexität.

2. Queue:
   Leicht höhere Latenz und Infrastruktur-Komplexität, dafür deutlich höhere Zuverlässigkeit.

#### Praktisches NestJS-Pattern

1. Lokale Domain-Events für unmittelbare nicht-kritische Reaktionen emittieren.
2. Durable Background-Jobs für wichtige/teure Arbeit enqueuen.
3. Für Cross-Service-Integration Message-Broker/Events nutzen, nicht nur In-Process-EventEmitter.

#### Faustregel

Wenn Event-Verlust nicht akzeptabel ist, Bull/BullMQ (oder brokerbasierte
Messaging-Lösung) verwenden, nicht reinen EventEmitter.

</details>

<details>
<summary>77. Wie implementiert man interne event-driven Kommunikation zwischen Modulen via EventEmitter2?</summary>

#### NestJS

Interne event-driven Kommunikation in NestJS mit EventEmitter2 entkoppelt Module:
Ein Modul emittiert ein Domain-Event, andere Module reagieren ohne direkte
Service-Calls.

#### Schritt 1: EventEmitterModule aktivieren

```ts
import { Module } from '@nestjs/common';
import { EventEmitterModule } from '@nestjs/event-emitter';

@Module({
  imports: [
    EventEmitterModule.forRoot({
      wildcard: true,
      delimiter: '.',
      maxListeners: 20,
    }),
  ],
})
export class AppModule {}
```

#### Schritt 2: Events aus dem Application-Flow emittieren

```ts
import { Injectable } from '@nestjs/common';
import { EventEmitter2 } from '@nestjs/event-emitter';

@Injectable()
export class OrdersService {
  constructor(private readonly events: EventEmitter2) {}

  async createOrder(input: { orderId: string; userId: string; total: number }) {
    // ...order persistieren
    this.events.emit('order.created', {
      orderId: input.orderId,
      userId: input.userId,
      total: input.total,
      occurredAt: new Date().toISOString(),
    });
  }
}
```

#### Schritt 3: In anderen Modulen mit `@OnEvent` subscriben

```ts
import { Injectable, Logger } from '@nestjs/common';
import { OnEvent } from '@nestjs/event-emitter';

@Injectable()
export class NotificationsListener {
  private readonly logger = new Logger(NotificationsListener.name);

  @OnEvent('order.created')
  async handleOrderCreated(event: { orderId: string; userId: string; total: number }) {
    this.logger.log(`Send confirmation for order ${event.orderId}`);
    // email / push / audit entry senden
  }
}
```

#### Naming- und Payload-Konventionen

1. Stabile Namen verwenden: `domain.action` (`order.created`, `user.deleted`).
2. Payload explizit und versionierbar halten.
3. Metadaten einbeziehen (`occurredAt`, `correlationId`, `source`).

#### Error-Handling-Aspekte

1. Event-Handler sollten eigene Fehler catchen/loggen.
2. Ein fehlschlagender Listener darf den Kern-Transaktionsflow nicht brechen.
3. Für kritische Side Effects durable Jobs enqueuen statt nur auf In-Memory-Event-Delivery zu setzen.

#### Modul-Architektur-Leitlinien

1. Events aus Application-Services nach erfolgreicher State-Änderung emittieren.
2. Listener in dedizierten Modulen halten (notifications, analytics, audit).
3. Circular Dependencies vermeiden, indem über Events statt direkte Service-Injection kommuniziert wird.

#### Faustregel

EventEmitter2 für interne Entkopplung in einem Service-Prozess nutzen. Für
Cross-Service oder garantierte Zustellung Queues/Message-Broker verwenden.

</details>

<details>
<summary>78. Wie implementiert man Hintergrundjobs mit Bull oder BullMQ?</summary>

#### NestJS

Hintergrundjobs in NestJS werden genutzt, um schwere oder nicht sofort nötige
Aufgaben aus dem Request/Response-Pfad auszulagern (E-Mails, Reports,
Medienverarbeitung, Synchronisationsaufgaben).

Bull/BullMQ stellen Redis-basierte, robuste Queues mit Retries, Delays und
Steuerung der Worker-Konkurrenz bereit.

#### Typische Architektur

1. API/Service stellt den Job schnell in die Queue.
2. Worker/Processor verarbeitet den Job asynchron.
3. Der Job-Status wird verfolgt (`waiting`, `active`, `completed`, `failed`).

#### Schritt 1: Queue-Modul registrieren

Bull-Setup im Modul:

```ts
import { Module } from '@nestjs/common';
import { BullModule } from '@nestjs/bull';

@Module({
  imports: [
    BullModule.forRoot({
      redis: { host: '127.0.0.1', port: 6379 },
    }),
    BullModule.registerQueue({ name: 'emails' }),
  ],
})
export class JobsModule {}
```

#### Schritt 2: Jobs erzeugen

```ts
import { InjectQueue } from '@nestjs/bull';
import { Injectable } from '@nestjs/common';
import { Queue } from 'bull';

@Injectable()
export class NotificationsService {
  constructor(@InjectQueue('emails') private readonly emailsQueue: Queue) {}

  async enqueueWelcomeEmail(userId: string, email: string) {
    await this.emailsQueue.add(
      'send-welcome-email',
      { userId, email },
      {
        attempts: 5,
        backoff: { type: 'exponential', delay: 1000 },
        removeOnComplete: true,
      },
    );
  }
}
```

#### Schritt 3: Jobs im Processor konsumieren

```ts
import { Process, Processor } from '@nestjs/bull';
import { Job } from 'bull';

@Processor('emails')
export class EmailsProcessor {
  @Process('send-welcome-email')
  async handleWelcome(job: Job<{ userId: string; email: string }>) {
    // provider aufrufen / E-Mail senden
  }
}
```

#### Hinweis zu BullMQ

BullMQ verwendet neuere APIs (`Queue`, `Worker`, `QueueEvents`) und wird für
moderne Setups empfohlen. Der Ablauf bleibt konzeptionell identisch:
Producer -> Redis-Queue -> Worker.

#### Best Practices für Produktion

1. Idempotente Job-Handler implementieren (Duplikate müssen sicher sein).
2. `attempts` + `backoff` sauber konfigurieren, um temporäre Fehler zu überstehen.
3. Dead-Letter-Strategie für dauerhaft fehlerhafte Jobs vorsehen.
4. Queue-Länge, Fehlerquote, Durchsatz und Latenz monitoren.
5. Job-Payload klein halten und nur referenzierende IDs speichern, wenn möglich.

#### Wann Bull/BullMQ einsetzen

1. Wenn Tasks länger dauern als eine typische HTTP-Timeout-Grenze.
2. Wenn Workloads geglättet oder wiederholbar verarbeitet werden müssen.
3. Wenn Zuverlässigkeit (Retry/Delay/Persistenz) erforderlich ist.

</details>

<details>
<summary>79. Wie entwirft man idempotente Jobs (Task Queues), um doppelte Ausführung zu vermeiden?</summary>

#### NestJS

Idempotentes Job-Design bedeutet, dass mehrfaches Ausführen desselben Jobs zum
selben Endzustand führt wie eine einmalige Ausführung.

In Queue-Systemen ist das Pflicht, weil Retries, Worker-Neustarts und
Delivery-Semantik zu doppelten Ausführungsversuchen führen können.

#### Warum Duplikate entstehen

1. Worker stürzt nach Side Effect, aber vor ACK ab.
2. Retry nach Timeout/Netzwerkpartition.
3. Manuelles Requeue/Replay.
4. Race Conditions bei mehreren Consumern.

#### Kernstrategien für Idempotenz

1. **Business-Idempotency-Key**
   Stabilen eindeutigen Schlüssel pro Operation verwenden (`paymentId`, `orderId:action`).

2. **Deduplication-Store**
   Verarbeitete Keys/Status in DB/Redis mit Unique-Constraint persistieren.

3. **Atomisches Check-and-Set**
   Sicherstellen, dass die „erste Ausführung gewinnt“ (Transaktion/Lock/Unique-Insert).

4. **Outbox-/Inbox-Pattern**
   Verarbeitete Message-IDs nachhalten, um wiederholte Side Effects zu verhindern.

5. **Idempotente Side-Effect-APIs**
   Externe Provider-Idempotency-Keys nutzen, wenn verfügbar.

#### Praktischer Job-Flow

1. Job startet mit `idempotencyKey`.
2. Key atomar reservieren:
   1. Bereits `completed` -> erfolgreich beenden (No-op).
   2. Gerade reserviert -> fortfahren.
3. Side Effects ausführen.
4. Key mit Ergebnis-Metadaten als `completed` markieren.
5. Bei Fehlern Retry-Policy beibehalten, aber Idempotenz-Semantik erhalten.

#### Beispiel für ein Key-Modell

1. `job_key` (unique)
2. `status` (`processing`, `completed`, `failed`)
3. `updated_at`
4. optional `result_hash` / `external_reference`

#### Queue-Level-Techniken

1. Deterministischen `jobId` beim Enqueue setzen (verhindert in vielen Engines doppelte Enqueues).
2. Begrenzte Retries + Backoff verwenden.
3. Gleiches Entity nicht parallel verarbeiten (Partitionierung/Locking).

#### Praktische Hinweise für NestJS/Bull

1. Idempotenz-Guard am Processor-Start setzen, nicht nur auf Producer-Seite.
2. Processor, wo möglich, transaktional halten.
3. Bei externen Calls Idempotency-Header/Key weitergeben.
4. Strukturierte Logs mit Key + Attempt + Outcome schreiben.

#### Häufige Fehler

1. Von „exactly-once delivery“ ausgehen.
2. Side Effects vor Idempotenz-Reservierung ausführen.
3. Pro Retry zufällige UUID als Key nutzen (bricht Deduplication).
4. Idempotenz-Records zu früh löschen.

#### Faustregel

Jeden Background-Job als at-least-once zugestellt betrachten. Idempotenz an der
Business-Grenze macht Retries erst sicher.

</details>

<details>
<summary>80. Wie implementiert man WebSockets in NestJS?</summary>

#### NestJS

WebSockets in NestJS werden über Gateways implementiert, typischerweise mit dem
Paket `@nestjs/websockets` und einem Socket.IO-Adapter (häufiges Standard-Setup).

#### Kernkonzepte

1. **Gateway**
   Einstiegspunkt für WebSockets (ähnliche Rolle wie Controller bei HTTP).

2. **Events/Nachrichten**
   Der Client sendet Event-Namen mit Payload; der Server verarbeitet und antwortet bzw. emittiert.

3. **Lifecycle Hooks**
   Verarbeitung von Connect/Disconnect und Server-Initialisierung.

#### Einfaches Gateway-Beispiel

```ts
import {
  ConnectedSocket,
  MessageBody,
  OnGatewayConnection,
  OnGatewayDisconnect,
  SubscribeMessage,
  WebSocketGateway,
  WebSocketServer,
} from '@nestjs/websockets';
import { Server, Socket } from 'socket.io';

@WebSocketGateway({
  cors: { origin: ['https://app.example.com'], credentials: true },
  namespace: '/chat',
})
export class ChatGateway implements OnGatewayConnection, OnGatewayDisconnect {
  @WebSocketServer()
  server: Server;

  handleConnection(client: Socket) {
    // Auth/Context-Prüfungen können hier stattfinden
  }

  handleDisconnect(client: Socket) {
    // Presence/Ressourcen bereinigen
  }

  @SubscribeMessage('chat.send')
  async onSend(
    @MessageBody() payload: { roomId: string; text: string },
    @ConnectedSocket() client: Socket,
  ) {
    this.server.to(payload.roomId).emit('chat.message', {
      userId: client.id,
      text: payload.text,
      sentAt: new Date().toISOString(),
    });
  }
}
```

#### Room- und Broadcast-Patterns

1. Room beitreten: `client.join(roomId)`.
2. In Room senden: `server.to(roomId).emit(...)`.
3. An alle senden: `server.emit(...)`.
4. Nur an Sender senden: `client.emit(...)`.

#### Validierung und Sicherheit

1. Message-Payload validieren (DTO/Pipes).
2. Verbindung authentifizieren (Token/Session im Handshake).
3. Room-Zugriff pro Event autorisieren.
4. Rate Limiting/Throttling für laute Events anwenden.

#### Produktionsaspekte

1. Multi-Instance-Skalierung braucht Adapter/Pub-Sub (z. B. Redis-Adapter) für nodeübergreifende Event-Propagation.
2. Sticky Sessions bzw. passende Load-Balancer-Strategie nutzen, falls vom Transport benötigt.
3. Verbindungsanzahl, Event-Durchsatz und Disconnect-Gründe monitoren.
4. Handler schlank halten; schwere Arbeit in Queues/Worker auslagern.

#### Faustregel

WebSockets für bidirektionale Low-Latency-Features nutzen (Chat, Live-Updates,
Presence). Protokollverträge explizit halten und wie jede öffentliche API absichern.

</details>

<details>
<summary>81. Wie implementiert man Authentifizierung in einem WebSocket-Gateway?</summary>

#### NestJS

WebSocket-Authentifizierung in NestJS erfolgt üblicherweise während der
Handshake-Phase und wird anschließend pro Event mit Guards/
Autorisierungsprüfungen durchgesetzt.

#### Typischer Authentifizierungsfluss

1. Client sendet Token (JWT/Session) im Handshake:
   `auth`, Header oder Query-Parameter (bevorzugt `auth`/Header).

2. Server verifiziert Token in Gateway-Middleware/Guard.

3. Authentifizierter User-Kontext wird am Socket gespeichert (`client.data.user`).

4. Nachfolgende Message-Handler nutzen diesen Kontext für Autorisierung.

#### Beispiel: bei Verbindung authentifizieren

```ts
import {
  ConnectedSocket,
  MessageBody,
  OnGatewayConnection,
  SubscribeMessage,
  WebSocketGateway,
} from '@nestjs/websockets';
import { UnauthorizedException, UseGuards } from '@nestjs/common';
import { Socket } from 'socket.io';

@WebSocketGateway({ namespace: '/chat', cors: { origin: ['https://app.example.com'] } })
export class ChatGateway implements OnGatewayConnection {
  constructor(private readonly authService: AuthService) {}

  async handleConnection(client: Socket) {
    const token =
      client.handshake.auth?.token ||
      (client.handshake.headers.authorization as string | undefined)?.replace('Bearer ', '');

    if (!token) throw new UnauthorizedException('Missing token');

    const user = await this.authService.verifyAccessToken(token); // wirft bei Ungültigkeit
    client.data.user = user;
  }

  @SubscribeMessage('chat.send')
  async onSend(
    @ConnectedSocket() client: Socket,
    @MessageBody() payload: { roomId: string; text: string },
  ) {
    const user = client.data.user;
    // Benutzerzugriff auf den Room hier autorisieren
    return { ok: true, userId: user.id, text: payload.text };
  }
}
```

#### Guard-basierte Event-Autorisierung

1. `WsGuard` verwenden, um Auth-Kontext pro Event zu validieren.
2. Mit Rollen-/Policy-Prüfungen kombinieren (Room-Mitgliedschaft, Tenant-Scope, Berechtigungen).

#### Security Best Practices

1. Kurzlebige Access-Tokens bevorzugen.
2. Autorisierung bei sensitiven Events erneut prüfen, nicht nur beim Connect.
3. Token-Ablauf/Widerruf behandeln (Disconnect oder Re-Auth erzwingen).
4. Niemals clientseitig gesendeten User-IDs in Payload vertrauen; Socket-Auth-Kontext nutzen.
5. Throttling/Rate Limits für auth-sensitive Events anwenden.

#### Hinweise zur Skalierung

1. In Multi-Instance-Setups gemeinsame Session-/Token-Verifizierungsstrategie nutzen.
2. Bei verteilter Presence/Rooms Redis-Adapter für nodeübergreifende State-Synchronisierung nutzen.

#### Faustregel

Einmal im Handshake authentifizieren (Effizienz), pro Event autorisieren
(Sicherheit). Für sichere Echtzeitsysteme sind beide Ebenen nötig.

</details>

<details>
<summary>82. Welche Ansätze werden zur Skalierung von Echtzeitsystemen verwendet?</summary>

#### NestJS

Die Skalierung von Echtzeitsystemen erfordert das gemeinsame Beherrschen von drei
Dimensionen:
1. Verbindungs-Skalierung,
2. Nachrichten-Durchsatz,
3. Zustandskonsistenz über mehrere Nodes.

#### Zentrale Skalierungsansätze

1. **Horizontale Skalierung von Gateway-Instanzen**
   Mehrere WebSocket-Gateway-Replikas hinter einem Load Balancer betreiben.

2. **Sticky Sessions (falls erforderlich)**
   Sicherstellen, dass derselbe Client auf derselben Node bleibt, wenn
   Transport-/Session-Modell Affinität verlangt.

3. **Pub/Sub-Adapter für nodeübergreifende Broadcasts**
   Redis-Adapter (oder Äquivalent) nutzen, damit Events von einer Node auch
   Clients auf anderen Nodes erreichen.

4. **Ausgelagerter gemeinsamer Zustand**
   Presence-/Room-/Session-Metadaten in Redis/DB speichern, nicht nur im
   Prozessspeicher.

5. **Backpressure und Rate Limiting**
   Laute Clients drosseln, Fan-out-Spitzen begrenzen und Downstream-Systeme schützen.

#### Architektur-Patterns

1. **Gateway-Tier + Worker-Tier**
   Gateways verwalten Verbindungen; schwere Verarbeitung wird in Queue-Worker verlagert.

2. **Channel-/Room-Partitionierung**
   Hochvolumige Streams nach Tenant/Region/Topic partitionieren.

3. **Event-driven Backbone**
   Broker (Redis Streams/Kafka/NATS) für dauerhafte oder sehr hohe Event-Last verwenden,
   wenn einfaches Pub/Sub nicht ausreicht.

4. **Fan-out-Optimierung**
   Empfänger-Mengen vorkalkulieren und teure DB-Lookups pro Nachricht vermeiden.

#### Performance- und Zuverlässigkeitstechniken

1. Kompakte Message-Payloads verwenden und übergroße Events vermeiden.
2. Heartbeats/Ping-Pong mit sinnvollen Timeouts einsetzen.
3. Reconnect- plus Replay-Strategie für verpasste kritische Nachrichten umsetzen.
4. Circuit Breaker/Timeouts für externe Abhängigkeiten ergänzen.
5. p95/p99-Latenz der Event-Zustellung und Drop-Raten monitoren.

#### Notwendige operative Observability

1. Aktive Verbindungen pro Node.
2. Nachrichten/Sekunde rein/raus.
3. Room-Größenverteilung und Hot Rooms.
4. Nodeübergreifender Pub/Sub-Lag.
5. Fehler-/Disconnect-Gründe und Reconnect-Erfolgsrate.

#### NestJS-spezifischer Implementierungs-Stack (typisch)

1. `@WebSocketGateway` für Echtzeit-Endpunkte.
2. Redis-Adapter für Multi-Instance-Event-Propagation.
3. Bull/BullMQ zum Auslagern schwerer asynchroner Aufgaben.
4. `@nestjs/throttler` oder eigene Guards zur Missbrauchskontrolle.

#### Faustregel

Echtzeit-Skalierung ist nicht nur „mehr Pods“. Horizontale Gateways,
gemeinsames Pub/Sub/State und strikte Flusskontrolle müssen kombiniert werden,
damit die Latenz vorhersagbar bleibt.

</details>

<details>
<summary>83. Welche Ansätze zur GraphQL-Integration in NestJS gibt es (Code-first vs. Schema-first), und worin liegt der Unterschied?</summary>

#### NestJS

NestJS unterstützt zwei Ansätze zur GraphQL-Integration:
1. **Code-first**
2. **Schema-first**

Beide sind produktionsgeeignet. Der Unterschied liegt darin, wo der API-Vertrag
zuerst definiert wird: in TypeScript-Klassen/Dekoratoren oder in `.graphql`-SDL-Dateien.

#### Code-first-Ansatz

GraphQL-Typen und Resolver werden in TypeScript mit Dekoratoren definiert, das
Schema wird automatisch generiert.

Beispielstil:
1. `@ObjectType()`, `@Field()`, `@InputType()`
2. `@Resolver()`, `@Query()`, `@Mutation()`

Vorteile:
1. Eine Sprache (TS) für App + Schema.
2. Starke Typisierung und Refactoring-Support in der IDE.
3. Weniger Duplizierung zwischen DTOs und Schema-Modell.

Nachteile:
1. Schema-Lesbarkeit für Nicht-TS-Stakeholder kann geringer sein.
2. Generiertes Schema muss dennoch sorgfältig reviewed/versioniert werden.

#### Schema-first-Ansatz

Das Schema wird in `.graphql`-Dateien (SDL) definiert, Resolver werden danach in TS implementiert.

Vorteile:
1. Contract-first-Workflow (gut für API-Governance).
2. SDL ist explizit und teamübergreifend leicht reviewbar.
3. Starker Fit, wenn das Schema sprach-/teamübergreifend geteilt wird.

Nachteile:
1. Potenzielle Duplizierung zwischen SDL und TS-Typen.
2. Erfordert Disziplin zur Synchronisierung, um Drift zu vermeiden.

#### NestJS-Setup-Beispiele (konzeptionell)

Code-first:

```ts
GraphQLModule.forRoot({
  autoSchemaFile: true,
});
```

Schema-first:

```ts
GraphQLModule.forRoot({
  typePaths: ['./**/*.graphql'],
});
```

#### Entscheidung zwischen beiden Ansätzen

1. **Code-first** wählen, wenn:
   1. Das Team TypeScript-zentriert ist.
   2. Iterationsgeschwindigkeit Priorität hat.
   3. Das Schema primär vom Backend-Team verantwortet wird.

2. **Schema-first** wählen, wenn:
   1. Der API-Vertrag breit geteilt/governed wird.
   2. Mehrere Implementierungen/Consumer vom SDL abhängen.
   3. Contract-Review und Versionierung zentraler Workflow sind.

#### Praktische Empfehlung

Für die meisten NestJS-Teams liefert Code-first die schnellste Entwicklung mit
starker Typisierung. Schema-first ist sinnvoll, wenn Contract-Governance und
teamübergreifende SDL-Verantwortung im Vordergrund stehen.

</details>

<details>
<summary>84. Was sind Resolver in GraphQL und wie unterscheiden sie sich von REST-Controllern?</summary>

#### NestJS

Resolver in GraphQL sind Funktionen, die Felder im GraphQL-Schema auflösen.
Sie bilden die Ausführungsschicht, die Daten für Queries, Mutations und
verschachtelte Objektfelder liefert.

In NestJS werden Resolver mit `@Resolver()` und Methodendekoratoren wie
`@Query()`, `@Mutation()` und `@ResolveField()` definiert.

#### Was Resolver tun

1. GraphQL-Operationen verarbeiten (`query`, `mutation`, ggf. subscriptions).
2. Verschachtelte Felder lazy auflösen (gemäß angefragtem Selection Set).
3. Kontext nutzen (auth user, Request-Metadaten, Loader).
4. Business-Logik an Services delegieren.

#### Wie Resolver sich von REST-Controllern unterscheiden

1. **API-Form**
   REST-Controller exponieren mehrere URL-Endpunkte.
   GraphQL-Resolver exponieren einen Endpunkt mit schema-gesteuerten Operationen.

2. **Datenauswahl**
   REST liefert pro Endpunkt eine feste Response.
   GraphQL liefert dynamisch client-selektierte Felder.

3. **Ausführungsmodell**
   REST-Controller bauen meist die komplette Response auf einmal.
   GraphQL-Resolver können als Resolver-Baum mehrere Feld-Resolver ausführen.

4. **Over-/Under-Fetching**
   REST erfordert oft Endpunkt-Kompromisse.
   GraphQL reduziert Over-/Under-Fetching über Selection Sets.

5. **Versionierungsstil**
   REST nutzt häufig explizite API-Versionen.
   GraphQL entwickelt das Schema typischerweise über Deprecations und additive Änderungen weiter.

#### NestJS-Resolver-Beispiel

```ts
import { Args, Mutation, Query, Resolver } from '@nestjs/graphql';

@Resolver(() => User)
export class UsersResolver {
  constructor(private readonly usersService: UsersService) {}

  @Query(() => User, { name: 'user' })
  findOne(@Args('id') id: string) {
    return this.usersService.findById(id);
  }

  @Mutation(() => User)
  createUser(@Args('input') input: CreateUserInput) {
    return this.usersService.create(input);
  }
}
```

#### Best Practices

1. Resolver schlank halten; Business-Logik in Services legen.
2. DataLoader/Batching nutzen, um N+1 bei verschachtelten Feldern zu vermeiden.
3. Args/Inputs validieren und AuthZ in Guards/Kontext erzwingen.
4. Schema-Typen an der Domänensprache ausrichten, nicht direkt an DB-Tabellen.

#### Faustregel

Resolver sind das GraphQL-Äquivalent zu Controllern, aber mit Feld-Level-
Ausführung und clientgetriebener Datenselektionssemantik.

</details>

<details>
<summary>85. Wie arbeitet man mit Context in GraphQL und implementiert Autorisierung darüber?</summary>

#### NestJS

In NestJS GraphQL ist `context` der Container pro Request, der Metadaten
(Benutzer, Header, requestId, Loader, Tenant-Infos) in Resolver und Guards trägt.

Autorisierung wird typischerweise so umgesetzt:
1. Benutzer in den Context authentifizieren,
2. Zugriffsregeln mit GraphQL-fähigen Guards/Policies erzwingen.

#### Schritt 1: GraphQL-Context befüllen

Bei der Konfiguration von `GraphQLModule` Request-Daten im Context verfügbar machen:

```ts
GraphQLModule.forRoot({
  autoSchemaFile: true,
  context: ({ req, res }) => ({ req, res, requestId: req.headers['x-request-id'] }),
});
```

Wenn JWT-Middleware/-Strategie `req.user` setzt, ist dies im GraphQL-Context verfügbar.

#### Schritt 2: Context im Resolver verwenden

```ts
import { Context, Query, Resolver } from '@nestjs/graphql';

@Resolver()
export class ProfileResolver {
  @Query(() => String)
  me(@Context() ctx: any) {
    return ctx.req.user?.id;
  }
}
```

#### Schritt 3: mit GraphQL-Guard autorisieren

`GqlExecutionContext` nutzen, um in Guards auf `req.user` zuzugreifen:

```ts
import { CanActivate, ExecutionContext, Injectable, UnauthorizedException } from '@nestjs/common';
import { GqlExecutionContext } from '@nestjs/graphql';

@Injectable()
export class GqlAuthGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const gqlCtx = GqlExecutionContext.create(context);
    const req = gqlCtx.getContext().req;
    if (!req.user) throw new UnauthorizedException();
    return true;
  }
}
```

Anwenden:

```ts
@UseGuards(GqlAuthGuard)
@Query(() => User)
me(@Context() ctx: any) {
  return ctx.req.user;
}
```

#### Feingranulare Autorisierung

1. Rollenbasierte Checks via Metadata + Guard (`@Roles(...)`).
2. Policy-/ABAC-Checks über Subject-Action-Resource-Service.
3. Feld-Level-Autorisierung in `@ResolveField()` bei Bedarf.

#### Best Practices

1. Context minimal, aber ausreichend halten (user, requestId, loader, tenant).
2. Authentifizierung einmal pro Request, Autorisierung pro Operation/Feld.
3. DataLoader im Context für N+1-Vermeidung nutzen.
4. Niemals clientseitigen User-IDs vertrauen; nur authentifizierten Context nutzen.

#### Faustregel

GraphQL-Context ist der vertrauenswürdige Request-Umschlag. Identität dort
ablegen und Autorisierung über darauf aufbauende Guards/Policies erzwingen.

</details>

<details>
<summary>86. Welche Transportprotokolle und Message Broker werden unterstützt (Kafka, Redis, gRPC, NATS) und was sind ihre Unterschiede?</summary>

#### NestJS

NestJS-Microservices unterstützen mehrere Transports, darunter Kafka, Redis,
gRPC und NATS. Jeder hat unterschiedliche Delivery-Semantik,
Performance-Profile und Einsatzfälle.

#### Vergleich auf hoher Ebene

1. **Kafka**
   Verteilter Commit-Log-Broker mit hohem Durchsatz, dauerhafter Retention,
   Consumer-Gruppen und Replay-Fähigkeit.

2. **Redis-Transport (Pub/Sub oder Streams-basierte Muster)**
   Sehr schnelle, einfache, latenzarme Nachrichtenübertragung; Haltbarkeit/
   Ordering hängen vom gewählten Redis-Muster und Setup ab.

3. **gRPC**
   RPC-Protokoll über HTTP/2 mit Protobuf-Verträgen; sehr gut für streng
   typisierte, synchrone Service-zu-Service-Aufrufe.

4. **NATS**
   Leichtgewichtiges, hochperformantes Messaging-System; stark für latenzarmes
   Pub/Sub und Request/Reply, optional mit Persistenz via JetStream.

#### Wann welchen wählen

1. **Kafka**
   1. Event Streaming und Audit Trails.
   2. Asynchrone Pipelines mit hohem Durchsatz.
   3. Bedarf an Replay/History und starker Consumer-Skalierung.

2. **Redis**
   1. Einfaches, leichtgewichtiges Event-Fan-out.
   2. Cache-nahe Messaging-Muster.
   3. Niedriger operativer Overhead für kleinere Systeme.

3. **gRPC**
   1. Latenzarme interne RPCs mit strikten Verträgen.
   2. Polyglotte Microservices mit generierten Clients/Stubs.
   3. Bidirektionale Streaming-RPC-Anwendungsfälle.

4. **NATS**
   1. Schnelles cloud-natives Messaging.
   2. Request/Reply und Pub/Sub mit kleinem Footprint.
   3. JetStream, wenn Haltbarkeit/ACK/Replay nötig sind.

#### Wichtige semantische Unterschiede

1. **Kommunikationsstil**
   Kafka/NATS/Redis: asynchrone event-/nachrichtengesteuerte Muster.
   gRPC: direkte RPC-Request/Response (synchron orientiert).

2. **Haltbarkeit/Replay**
   Kafka: starker dauerhafter Log und Replay by design.
   NATS Core: ephemer, außer JetStream ist aktiviert.
   Redis Pub/Sub: standardmäßig ephemer.
   gRPC: keine Broker-Persistenzschicht (RPC-Semantik).

3. **Contract-Modell**
   gRPC nutzt Protobuf-first mit strikten Schemata.
   Broker-basierte Transports nutzen häufig Message-Schema-Konventionen
   (Avro/JSON/Protobuf), die durch Team/Tooling erzwungen werden.

#### Praktische NestJS-Designhinweise

1. **gRPC** für synchrone interne APIs mit strikter Typisierung nutzen.
2. **Kafka/NATS/Redis** für asynchrone entkoppelte Workflows nutzen.
3. Für kritische Business-Events mit Replay/Audit **Kafka** oder persistentes
   **NATS JetStream** bevorzugen.
4. Message-Envelopes standardisieren (`eventName`, `version`, `correlationId`, `payload`).
5. Observability für Lag, Retry, DLQ und Consumer-Health hinzufügen.

#### Faustregel

Transport zuerst nach Fehlermodell und Delivery-Garantien wählen, nicht nur nach
rohem Durchsatz.

</details>

<details>
<summary>87. Wie entwirft man eine Event-driven Architecture korrekt und was sind die Kernprinzipien?</summary>

#### NestJS

Event-driven Architecture (EDA) organisiert Systeme um Events herum: Fakten,
dass etwas passiert ist (`order.created`, `payment.failed` usw.). Producer
publizieren Events, Consumer reagieren asynchron.

#### Kernprinzipien

1. **Loose Coupling**
   Producer hängen nicht von internen Details der Consumer ab.

2. **Asynchrone Kommunikation**
   Services koordinieren sich über Events statt wo möglich über blockierendes RPC.

3. **Single Source of Truth pro Domäne**
   Jeder Service besitzt seine Daten und publiziert Domain-Events nach
   Zustandsänderungen.

4. **Event-Contract-Governance**
   Events sind versionierte Verträge mit stabilem Schema und klarer Semantik.

5. **Idempotente Consumer**
   Handler müssen doppelte Zustellungen sicher verarbeiten können.

6. **Observability und Traceability**
   Correlation IDs, Event-Metadaten und Processing-Metriken sind Pflicht.

#### Richtlinien für Event-Design

1. Events als Fakten in Vergangenheitsform benennen: `invoice.paid`, `user.email_changed`.
2. Metadaten aufnehmen:
   `eventId`, `eventType`, `occurredAt`, `version`, `correlationId`, `source`.
3. Payload auf Business-Bedeutung fokussieren, nicht auf interne DB-Struktur.
4. Additive Schema-Evolution bevorzugen; Breaking Changes vermeiden.

#### Delivery- und Konsistenzmodell

1. In den meisten Broker-Systemen von at-least-once delivery ausgehen.
2. Eventual Consistency über Service-Grenzen akzeptieren.
3. Retries + DLQ für fehlgeschlagene Verarbeitung nutzen.
4. Outbox-Pattern einsetzen, um Lücken „DB-Write erfolgreich, Event-Publish fehlgeschlagen“ zu verhindern.

#### NestJS-Implementierungsbausteine

1. Interne Modul-Events: `@nestjs/event-emitter` (in-process).
2. Dauerhafte asynchrone Verarbeitung: Bull/BullMQ-Queues.
3. Service-übergreifendes Messaging: Kafka/NATS/Redis-Transport-Adapter.
4. Consumer-Handler mit Validierung + Idempotenz-Checks.

#### Anti-Patterns, die vermieden werden sollten

1. Event-Payloads mit riesigen, mutierbaren Objektsnapshots.
2. Versteckte synchrone Kopplung, als Events getarnt.
3. Keine Schema-Versionierungsstrategie.
4. Kein Replay-/Recovery-Plan bei Consumer-Ausfällen.
5. Events als Commands behandeln (außer explizit so modelliert).

#### Praktischer Architektur-Flow

1. Ein Command aktualisiert den Domänenzustand im Owner-Service.
2. Der Owner emittiert ein Domain-Event (transaktional via Outbox).
3. Broker liefert an interessierte Consumer.
4. Consumer aktualisieren eigene Read Models/Side Effects.
5. Monitoring verfolgt Lag, Fehler und DLQ.

#### Faustregel

Events als dauerhafte Business-Fakten entwerfen, nicht als
Implementierungsdetails. Zuverlässigkeit entsteht durch Idempotenz,
Contract-Disziplin und operative Observability.

</details>

<details>
<summary>88. Wie behandelt man verteilte Transaktionen in Microservices? (Saga-Pattern, Eventual Consistency)</summary>

#### NestJS

In Microservices sind klassische ACID-Transaktionen über mehrere Services/
Datenbanken meist unpraktisch. Stattdessen nutzt man **Eventual Consistency**
und Koordinationsmuster wie **Saga**.

#### Warum verteilte Transaktionen schwierig sind

1. Services besitzen getrennte Datenbanken.
2. Netzwerkfehler und Teilerfolge sind normal.
3. 2PC-artige globale Transaktionen reduzieren Verfügbarkeit und erhöhen Komplexität.

#### Bevorzugter Ansatz: Saga-Pattern

Eine Saga ist eine Sequenz lokaler Transaktionen über Services hinweg, gesteuert
über Erfolgs-/Fehlerpfade.

Zwei Varianten:
1. **Choreography**
   Services reagieren auf Events ohne zentralen Koordinator.
2. **Orchestration**
   Ein dedizierter Orchestrator steuert Schrittfolge und Kompensationen.

#### Kernkonzepte

1. **Lokale Transaktion pro Service**
   Jeder Service committed nur eigene DB-Änderungen.

2. **Kompensierende Aktionen**
   Falls ein späterer Schritt fehlschlägt, werden zuvor erfolgreiche Schritte
   kompensiert (`reserve -> release`, `charge -> refund`).

3. **Idempotenz**
   Alle Handler/Kompensationen müssen doppelte Zustellung tolerieren.

4. **Eventual Consistency**
   Temporäre Inkonsistenzen sind akzeptiert, bis die Saga konvergiert.

#### Beispiel-Flow (Order Checkout)

1. Order-Service erstellt Order mit Status `PENDING`.
2. Payment-Service belastet den Kunden.
3. Inventory-Service reserviert Bestand.
4. Wenn alles erfolgreich ist -> Order wird `CONFIRMED`.
5. Falls Inventory nach Payment fehlschlägt -> Kompensation ausführen (`payment.refund`) und Order auf `CANCELLED` setzen.

#### NestJS-Implementierungsbausteine

1. Message-Transport/Broker (Kafka, NATS, Redis usw.).
2. Dauerhafte Job-/Event-Verarbeitung mit Retries und DLQ.
3. Outbox-Pattern für zuverlässiges Event-Publishing nach lokalem Commit.
4. Saga-State-Tracking (DB-Tabelle/Workflow-Store).
5. Strukturierte Logs mit `correlationId`/`sagaId`.

#### Trade-off Choreography vs Orchestration

1. **Choreography**
   + Einfacher Start, weniger zentrale Abhängigkeit
   - Schwierigere globale Sicht/Kontrolle bei wachsendem Flow

2. **Orchestration**
   + Klare Flow-Ownership, einfacheres Debugging und Policy-Kontrolle
   - Zusätzliche Komponente und Koordinationslogik

#### Praktische Schutzmaßnahmen

1. Timeouts pro Saga-Schritt ergänzen.
2. Retry mit Backoff für transiente Fehler implementieren.
3. Für jeden nicht-idempotenten Side Effect Kompensation definieren.
4. Saga-Schritte klein und explizit halten.
5. Hängende/unvollständige Sagas monitoren.

#### Faustregel

In Microservices nicht globalem ACID nachjagen. Business-Workflows als Sagas
modellieren: mit idempotenten Handlern, Kompensationen und starker Observability.

</details>

<details>
<summary>89. Was ist CQRS und wie implementiert man es in NestJS mit @nestjs/cqrs?</summary>

#### NestJS

CQRS (Command Query Responsibility Segregation) trennt Schreiboperationen
(Commands) von Leseoperationen (Queries), oft mit unterschiedlichen Modellen und
Optimierungsstrategien auf beiden Seiten.

#### Warum CQRS verwendet wird

1. Klare Trennung von Business-Mutationen und Leseanforderungen.
2. Bessere Skalierbarkeit für leseintensive Systeme.
3. Einfachere Modellierung komplexer Domänen-Workflows.
4. Sauberere Integration mit Events und Eventual Consistency.

#### Kernkomponenten von CQRS

1. **Command**
   Absicht, Zustand zu ändern (`CreateOrderCommand`).

2. **CommandHandler**
   Führt Business-Logik aus und schreibt Zustand.

3. **Query**
   Datenabfrage ohne Side Effects (`GetOrderByIdQuery`).

4. **QueryHandler**
   Liefert Read Model/Datenprojektion zurück.

5. **Events** (optional, aber häufig)
   Fakten, die nach erfolgreichen Zustandsänderungen emittiert werden.

#### NestJS-Implementierung mit `@nestjs/cqrs`

Schritt 1: `CqrsModule` installieren und importieren.

```ts
@Module({
  imports: [CqrsModule],
  providers: [CreateOrderHandler, GetOrderByIdHandler],
})
export class OrdersModule {}
```

Schritt 2: Command + Handler definieren.

```ts
export class CreateOrderCommand {
  constructor(
    public readonly userId: string,
    public readonly items: Array<{ sku: string; qty: number }>,
  ) {}
}

@CommandHandler(CreateOrderCommand)
export class CreateOrderHandler implements ICommandHandler<CreateOrderCommand> {
  constructor(private readonly ordersService: OrdersService) {}

  async execute(command: CreateOrderCommand) {
    return this.ordersService.create(command.userId, command.items);
  }
}
```

Schritt 3: Query + Handler definieren.

```ts
export class GetOrderByIdQuery {
  constructor(public readonly orderId: string) {}
}

@QueryHandler(GetOrderByIdQuery)
export class GetOrderByIdHandler implements IQueryHandler<GetOrderByIdQuery> {
  constructor(private readonly readRepo: OrdersReadRepository) {}

  async execute(query: GetOrderByIdQuery) {
    return this.readRepo.findById(query.orderId);
  }
}
```

Schritt 4: Buses im Controller/Service verwenden.

```ts
constructor(
  private readonly commandBus: CommandBus,
  private readonly queryBus: QueryBus,
) {}

await this.commandBus.execute(new CreateOrderCommand(userId, items));
return this.queryBus.execute(new GetOrderByIdQuery(orderId));
```

#### Wann sich CQRS lohnt

1. Komplexe Domänenregeln und Workflows.
2. Unterschiedliche Skalierungsanforderungen für Reads vs. Writes.
3. Bedarf an eventgetriebenen Projektionen/Read Models.

#### Wann man CQRS nicht übernutzen sollte

1. Kleine CRUD-Apps mit einfacher Logik.
2. Teams, die für zusätzliche Architekturkomplexität noch nicht bereit sind.

#### Faustregel

CQRS dort einsetzen, wo Business-Komplexität oder Skalierungsbedarf es
rechtfertigen. Sonst ein einfacheres Service/Repository-Modell beibehalten und
inkrementell weiterentwickeln.

</details>

<details>
<summary>90. Was ist Domain-Driven Design und wie werden seine Prinzipien in NestJS angewendet?</summary>

#### NestJS

Domain-Driven Design (DDD) ist ein Ansatz, der Software um zentrale
Business-Domänen und deren Sprache modelliert, statt nur um technische Schichten.

In NestJS wird DDD angewendet, indem Module und Code-Grenzen an
Business-Fähigkeiten und Domänenregeln ausgerichtet werden.

#### Zentrale DDD-Prinzipien

1. **Ubiquitous Language**
   Geteiltes Business-Vokabular in Code, Doku und Gesprächen.

2. **Bounded Contexts**
   Klare Grenzen, in denen ein Modell eine spezifische Bedeutung hat.

3. **Entities / Value Objects / Aggregates**
   Domänenobjekte mit expliziten Invarianten und Konsistenzregeln.

4. **Domain Services**
   Zustandslose Business-Operationen, die nicht zu einer einzelnen Entity gehören.

5. **Repositories**
   Abstraktionen zum Laden/Speichern von Aggregates.

6. **Domain Events**
   Business-Fakten, die bei bedeutenden Zustandsänderungen emittiert werden.

#### Mapping auf NestJS

1. **Feature-Module als Bounded Contexts**
   `OrdersModule`, `BillingModule`, `InventoryModule`.

2. **Application-Layer-Services**
   Orchestrieren Use Cases, Transaktionen und Integrationen.

3. **Domain-Layer**
   Reines Business-Modell (Entities/Value Objects/Policies), framework-agnostisch.

4. **Infrastructure-Adapter**
   DB, Messaging, externe APIs, HTTP-Controller.

#### Typische Ordnerstruktur (Beispiel)

```text
orders/
  application/
    commands/
    queries/
    orders.application-service.ts
  domain/
    entities/
    value-objects/
    events/
    repositories/
  infrastructure/
    persistence/
    messaging/
    http/
  orders.module.ts
```

#### Praktische DDD-Vorteile in NestJS

1. Besserer Fit für komplexe Business-Logik.
2. Weniger versehentliche Kopplung zwischen Domänen.
3. Testbarere Core-Logik unabhängig von Framework/Infrastruktur.
4. Einfachere Architektur-Weiterentwicklung mit wachsendem System.

#### Häufige Fallstricke

1. Beliebigen Layer-Code ohne echte Domänentiefe als „DDD“ bezeichnen.
2. ORM-Entities direkt in die Domänenlogik durchreichen.
3. Technische Sprache und Business-Konzepte inkonsistent mischen.
4. DDD für triviale CRUD-Services überengineeren.

#### Wann DDD am wertvollsten ist

1. Reichhaltige, sich ändernde Business-Regeln.
2. Mehrere Teams/Domänen auf einer Plattform.
3. Bedarf an langfristiger Modellklarheit und Bounded-Context-Autonomie.

#### Faustregel

DDD inkrementell anwenden: mit klaren Bounded Contexts und Ubiquitous Language
starten, dann tiefere taktische Muster dort ausbauen, wo die Domänenkomplexität
es rechtfertigt.

</details>

<details>
<summary>91. Was ist Hexagonale Architektur (Ports & Adapters) und wie implementiert man sie in NestJS?</summary>

#### NestJS

Hexagonale Architektur (Ports & Adapters) strukturiert eine Anwendung so, dass
Business-Logik von externen Technologien (DB, HTTP, Message Broker, SDKs)
isoliert bleibt.

Der Core hängt von Abstraktionen (Ports) ab, während konkrete Integrationen als
Adapter implementiert werden.

#### Kernkonzepte

1. **Domain/Application Core**
   Business-Regeln und Use-Case-Orchestrierung.

2. **Ports**
   Interfaces/Verträge, die der Core nutzt (Output-Ports) oder anbietet
   (Input-Ports).

3. **Adapters**
   Technische Implementierungen der Ports:
   HTTP-Controller, DB-Repositories, Message-Consumer, externe API-Clients.

#### Abhängigkeitsregel

Alle Abhängigkeiten zeigen nach innen:
1. Adapter hängen von Core-Verträgen ab.
2. Der Core hängt nicht von Framework-/Infrastrukturdetails ab.

#### Anwendung in NestJS

1. Port-Interfaces in Domain-/Application-Layer definieren.
2. Adapter in der Infrastruktur-Layer implementieren.
3. Adapterklassen an Port-Tokens in Module-Providern binden.
4. DI verwenden, um Ports in Use-Case-Services zu injizieren.

#### Beispielstruktur

Port (Core-Vertrag):

```ts
export interface PaymentPort {
  charge(input: { orderId: string; amount: number }): Promise<{ paymentId: string }>;
}
```

Application Service:

```ts
@Injectable()
export class CheckoutService {
  constructor(@Inject('PAYMENT_PORT') private readonly payments: PaymentPort) {}

  async checkout(orderId: string, amount: number) {
    return this.payments.charge({ orderId, amount });
  }
}
```

Adapter-Implementierung:

```ts
@Injectable()
export class StripePaymentAdapter implements PaymentPort {
  async charge(input: { orderId: string; amount: number }) {
    // Stripe SDK aufrufen
    return { paymentId: 'pay_123' };
  }
}
```

Provider-Binding:

```ts
{
  provide: 'PAYMENT_PORT',
  useClass: StripePaymentAdapter,
}
```

#### Vorteile

1. Einfacheres Testen (Ports in Unit-Tests mocken).
2. Geringere Kopplung an Framework/ORM/externe Anbieter.
3. Sicherere langfristige Refactorings und Technologiewechsel.
4. Klarere Architekturgrenzen für Teams.

#### Häufige Fallstricke

1. Ports zu generisch (Domänenbedeutung geht verloren).
2. ORM-/HTTP-Typen in Core-Interfaces leaken.
3. Zu viel Abstraktion für sehr kleine/einfache Module.

#### Faustregel

Hexagonale Grenzen um wichtige Business-Flows und instabile externe
Abhängigkeiten legen. Ports business-orientiert halten und Adapter austauschbar
machen.

</details>

<details>
<summary>92. Wie implementiert man strukturiertes Logging und warum wird es benötigt?</summary>

#### NestJS

Strukturiertes Logging bedeutet, Logs als maschinenlesbare Datensätze (meist
JSON) mit konsistenten Feldern zu schreiben, statt als freie Textzeilen.

Es wird für Durchsuchbarkeit, Alerting, Korrelation und verlässliche
Observability in Produktionssystemen benötigt.

#### Warum strukturiertes Logging wichtig ist

1. Schnelles Filtern/Abfragen in Log-Plattformen.
2. Besseres Incident-Debugging mit Correlation IDs.
3. Konsistente Dashboards und Alerts.
4. Einfacheres serviceübergreifendes Tracing in verteilten Systemen.

#### Was in jedem Log enthalten sein sollte

1. `timestamp`
2. `level` (`debug`, `info`, `warn`, `error`)
3. `service` / `env`
4. `message`
5. `requestId` / `traceId`
6. Kontextfelder (`userId`, `route`, `method`, `statusCode`, Latenz)
7. Fehlerdetails (`errorName`, `stack`) bei Fehlerfällen

#### NestJS-Implementierungsansatz

1. Strukturierten Logger (Pino/Winston) als App-Logger nutzen.
2. Request-Kontext (`requestId`, User-Info) via Middleware/Interceptor anhängen.
3. Business-Events und Fehler mit konsistentem Schema loggen.
4. Ad-hoc-`console.log` im Produktionscode vermeiden.

#### Praktischer Beispielstil

```json
{
  "level": "info",
  "message": "order.created",
  "service": "orders-api",
  "requestId": "5e8f...",
  "orderId": "ord_123",
  "userId": "usr_77",
  "durationMs": 42
}
```

#### Leitlinien für Fehler-Logging

1. Vollständigen Stack Trace in Logs behalten.
2. Stack Traces nicht in API-Responses exponieren.
3. Domain-Fehlercodes für zuverlässiges Alert-Routing ergänzen.
4. Root-Cause-Kette beim Wrappen von Exceptions erhalten.

#### Häufige Fehler

1. Nur Plain-Strings ohne Kontextfelder loggen.
2. Inkonsistente Feldnamen über Module/Services hinweg.
3. Secrets/Tokens/PII ohne Redaction loggen.
4. Zu viel Debug-Rauschen in produktiven Hot Paths.

#### Best Practices

1. Log-Schema definieren und dokumentieren.
2. Sensitive Felder zentral redigieren.
3. Log-Levels bewusst einsetzen.
4. Logs mit Metriken und Traces korrelieren.
5. Logging-Ausgabe für kritische Flows in Integrationstests validieren.

#### Faustregel

Wenn Logs nur für Menschen lesbar sind, wird Incident Response langsam. Wenn
Logs für Maschinen und Menschen strukturiert sind, wird Betrieb vorhersagbar und
skalierbar.

</details>

<details>
<summary>93. Wie implementiert man Application-Health-Monitoring in NestJS? (@nestjs/terminus)</summary>

#### NestJS

Application-Health-Monitoring in NestJS wird typischerweise mit
`@nestjs/terminus` umgesetzt. Das Paket liefert standardisierte
Health-Check-Endpunkte für Readiness und Liveness von App und Abhängigkeiten.

#### Warum Health-Monitoring nötig ist

1. Orchestratoren/Load Balancer benötigen Health-Signale.
2. Schnellere Incident-Erkennung und automatische Recovery.
3. Sichere Deployment-Rollouts und Readiness-Gating.

#### Typische Health-Endpunkte

1. **Liveness** (`/health/live`)
   Prüft: „Prozess läuft“.

2. **Readiness** (`/health/ready`)
   Prüft: „Kann jetzt Traffic bedienen“, inklusive kritischer Abhängigkeiten.

#### Grundlegende Setup-Schritte

1. `@nestjs/terminus` installieren.
2. `TerminusModule` importieren.
3. `HealthController` mit `HealthCheckService` erstellen.

#### Beispiel-Controller

```ts
import { Controller, Get } from '@nestjs/common';
import {
  HealthCheck,
  HealthCheckService,
  HttpHealthIndicator,
  MemoryHealthIndicator,
} from '@nestjs/terminus';

@Controller('health')
export class HealthController {
  constructor(
    private readonly health: HealthCheckService,
    private readonly http: HttpHealthIndicator,
    private readonly memory: MemoryHealthIndicator,
  ) {}

  @Get('live')
  @HealthCheck()
  live() {
    return this.health.check([
      () => this.memory.checkHeap('memory_heap', 300 * 1024 * 1024),
    ]);
  }

  @Get('ready')
  @HealthCheck()
  ready() {
    return this.health.check([
      () => this.http.pingCheck('docs', 'https://example.com/health'),
    ]);
  }
}
```

#### Was in Readiness enthalten sein sollte

1. DB-Konnektivität.
2. Redis-/Cache-Konnektivität.
3. Kritische externe Abhängigkeiten (nur wenn wirklich nötig zum Bedienen von Traffic).
4. Interne Ressourcen-Schwellen (Memory, ggf. Event-Loop-Pressure).

#### Operative Best Practices

1. Liveness leichtgewichtig und lokal halten.
2. Readiness abhängigkeitsbewusst, aber schnell halten.
3. Nicht-kritische optionale Services nicht als Readiness-Fail-Kriterium verwenden.
4. Health-Details in öffentlichen Umgebungen absichern/begrenzen.
5. Mit Kubernetes-Probes und Alerting integrieren.

#### Faustregel

Liveness sagt: „Starte mich neu, wenn ich tot bin.“ Readiness sagt: „Leite nur
Traffic zu mir, wenn ich Requests wirklich sicher bedienen kann.“

</details>

<details>
<summary>94. Wie implementiert man Health Checks für abhängige Services (DB, Redis, externe APIs)?</summary>

#### NestJS

Health Checks für Abhängigkeiten prüfen, ob kritische externe Systeme ausreichend
verfügbar sind, damit die App Traffic sicher bedienen kann.

In NestJS wird das typischerweise mit Indicators aus `@nestjs/terminus` umgesetzt.

#### Kategorien von Abhängigkeiten, die geprüft werden sollten

1. **Datenbank** (für die meisten APIs readiness-kritisch).
2. **Redis/Cache** (kritisch oder optional je nach Architektur).
3. **Externe APIs** (nur die, die für Kern-Request-Pfade nötig sind).

#### Implementierungsansatz

1. `/health/live` leichtgewichtig halten (Prozess-Ebene).
2. Abhängigkeits-Checks in `/health/ready` platzieren.
3. Nicht-kritische Abhängigkeiten separat markieren, um unnötige Hard-Fails zu vermeiden.

#### Beispiel-Readiness-Controller

```ts
import { Controller, Get } from '@nestjs/common';
import {
  HealthCheck,
  HealthCheckService,
  HttpHealthIndicator,
  MongooseHealthIndicator,
  TypeOrmHealthIndicator,
} from '@nestjs/terminus';

@Controller('health')
export class HealthController {
  constructor(
    private readonly health: HealthCheckService,
    private readonly db: TypeOrmHealthIndicator,
    private readonly http: HttpHealthIndicator,
    private readonly mongo: MongooseHealthIndicator,
  ) {}

  @Get('ready')
  @HealthCheck()
  ready() {
    return this.health.check([
      () => this.db.pingCheck('postgres'),
      () => this.http.pingCheck('payments-api', 'https://payments.example.com/health'),
      () => this.mongo.pingCheck('mongo-analytics'),
    ]);
  }
}
```

Für Redis je nach Stack einen Custom Health Indicator oder einen unterstützten
Adapter-Indicator nutzen.

#### Wichtige Designentscheidungen

1. **Kritische vs. optionale Abhängigkeit**
   Nur kritische Abhängigkeiten sollten Readiness fehlschlagen lassen.

2. **Timeouts**
   Health Checks müssen kurze, harte Timeouts haben, um Probe-Staus zu vermeiden.

3. **Check-Kosten**
   Leichtgewichtige „Ping“-Checks verwenden, keine teuren Queries.

4. **Failure-Semantik**
   Klaren Status pro Abhängigkeit für Diagnostik zurückgeben.

#### Operative Best Practices

1. Separate Endpunkte für Liveness-/Readiness-/Startup-Probes nutzen.
2. Nicht zu viele instabile externe Services direkt in Readiness prüfen.
3. Bei Bedarf Caching/Debouncing für teure Checks ergänzen.
4. Auf Zustandswechsel von Abhängigkeiten alerten, nicht nur auf kompletten App-Ausfall.
5. Abhängigkeits-Latenz in Observability-Dashboards aufnehmen.

#### Faustregel

Health Checks sollten beantworten: „Kann diese Instanz jetzt Requests korrekt
bedienen?“ Abhängigkeits-Checks um diese Frage herum entwerfen, nicht um
„alles irgendwie zu prüfen“.

</details>

<details>
<summary>95. Wie verwendet man OpenTelemetry in NestJS?</summary>

#### NestJS

OpenTelemetry (OTel) in NestJS wird genutzt, um Traces, Metriken und Logs für
Observability zu erfassen. Der häufigste Startpunkt ist Distributed Tracing für
eingehende Requests und nachgelagerte Aufrufe.

#### Was OpenTelemetry liefert

1. End-to-End-Request-Traces über Services hinweg.
2. Latenzaufschlüsselung nach Spans (DB, HTTP, Cache, Queue).
3. Korrelation zwischen Fehlern und konkreten Abhängigkeiten.
4. Vendor-neutrales Telemetrieformat (Export nach Jaeger/Tempo/Datadog/New Relic usw.).

#### Typischer NestJS-OTel-Setup-Flow

1. OTel-SDK vor dem App-Bootstrap initialisieren.
2. Resource-Attribute konfigurieren (`service.name`, `service.version`, env).
3. Auto-Instrumentierungen aktivieren (HTTP, Express, DB-Clients usw.).
4. Traces per OTLP/Collector exportieren.
5. Custom Spans ergänzen, wo Business-Kontext wichtig ist.

#### Minimales konzeptionelles Bootstrap (Node SDK)

```ts
import { NodeSDK } from '@opentelemetry/sdk-node';
import { getNodeAutoInstrumentations } from '@opentelemetry/auto-instrumentations-node';
import { OTLPTraceExporter } from '@opentelemetry/exporter-trace-otlp-http';
import { Resource } from '@opentelemetry/resources';

const sdk = new NodeSDK({
  resource: new Resource({
    'service.name': 'nestjs-api',
    'service.version': '1.0.0',
    'deployment.environment': process.env.NODE_ENV ?? 'development',
  }),
  traceExporter: new OTLPTraceExporter({
    url: process.env.OTEL_EXPORTER_OTLP_TRACES_ENDPOINT,
  }),
  instrumentations: [getNodeAutoInstrumentations()],
});

sdk.start();
```

Danach die Nest-App normal starten.

#### Beispiel für Custom Span (Business-Grenze)

1. Span um eine kritische Domänenoperation starten.
2. Attribute anhängen (`order.id`, `tenant.id`).
3. Exceptions und Status bei Fehlern erfassen.

#### Praktische Best Practices

1. Intelligent samplen (voll in Staging, abgestimmtes Sampling in Produktion).
2. Context-Header (`traceparent`) über HTTP-/Message-Grenzen propagieren.
3. High-Cardinality-Attribute vermeiden (User-E-Mail, zufällige IDs in Labels).
4. Kritische Abhängigkeiten und Queue-Consumer instrumentieren.
5. Traces mit Logs über trace/span IDs korrelieren.

#### Häufige Fallstricke

1. OTel erst nach App-Start initialisieren (frühe Spans fehlen).
2. Over-Instrumentation erzeugt Overhead/Rauschen.
3. Fehlende Context-Propagation zwischen Services/Workern.
4. Telemetrie in größeren Deployments direkt aus der App ohne Collector senden.

#### Faustregel

Mit Tracing + Auto-Instrumentation starten, dann gezielte Custom Spans um
wertvolle Business-Operationen und Latenz-Hotspots ergänzen.

</details>

<details>
<summary>96. Was ist Distributed Tracing und wie wird es in einer Microservice-Architektur implementiert?</summary>

#### NestJS

Distributed Tracing verfolgt einen Request/eine Transaktion über mehrere
Services und Infrastruktur-Komponenten hinweg und zeigt End-to-End-Flow plus
Latenzaufschlüsselung.

In Microservices ist es essenziell, weil eine einzelne Nutzeraktion viele
Service-Calls, Queue-Hops und DB-Operationen auslösen kann.

#### Kernkonzepte des Tracing

1. **Trace**
   Vollständiger End-to-End-Request-Pfad.

2. **Span**
   Eine Operation innerhalb des Traces (HTTP-Call, DB-Query, Handler-Ausführung).

3. **Context Propagation**
   Weitergabe des Trace-Kontexts zwischen Services (z. B. `traceparent`-Header).

4. **Parent-Child-Beziehungen**
   Spans bilden einen Baum, der die Aufrufhierarchie darstellt.

#### Warum Distributed Tracing benötigt wird

1. Echte Bottlenecks finden (welche Abhängigkeit ist langsam).
2. Service-übergreifende Fehler schnell debuggen.
3. Fan-out/Fan-in-Verhalten und Retry-Stürme verstehen.
4. p95/p99 auf Basis von Evidenz statt Vermutungen verbessern.

#### Umsetzung in Microservices

1. Jeden Service mit OpenTelemetry-SDK instrumentieren.
2. Frameworks/Libraries auto-instrumentieren (HTTP-Server/Client, DB, Message-Clients).
3. Kontext über Grenzen propagieren:
   1. HTTP-Header (`traceparent`, `tracestate`)
   2. Message-Metadaten für Kafka/NATS/Queues
4. Spans an Collector/Backend exportieren (OTLP -> Jaeger/Tempo/Datadog usw.).
5. Logs mit traceId/spanId korrelieren.

#### NestJS-spezifische Implementierungspunkte

1. OTel vor Nest-Bootstrap initialisieren.
2. Eingehende Requests instrumentieren (Express/Fastify).
3. Ausgehende `HttpService`-Aufrufe und DB-Treiber instrumentieren.
4. Custom Spans um wichtige Business-Operationen ergänzen.
5. Context in Worker/Background-Jobs propagieren.

#### Typischer Trace in der Praxis

1. API Gateway empfängt Request (Root-Span).
2. Service A validiert Auth (Child-Span).
3. Service A ruft Service B via gRPC/HTTP auf (Child-Span).
4. Service B führt DB-Query aus (Nested Span).
5. Service B publiziert Event an Broker (Child-Span).
6. Worker konsumiert Event und führt Side Effect aus (verknüpfter/fortgesetzter Kontext).

#### Best Practices

1. Konsistente Service-Namen und Resource-Attribute verwenden.
2. High-Cardinality-Span-Attribute vermeiden.
3. Sampling-Policy abstimmen (tail-based/head-based nach Traffic-Profil).
4. Fehler und Statuscodes auf Spans erfassen.
5. Trace-Retention an Incident-/Debug-Bedarf ausrichten.

#### Faustregel

In Microservices zeigen Metriken, dass etwas langsam ist; Distributed Tracing
zeigt exakt, wo und warum.

</details>

<details>
<summary>97. Wie schreibt man Unit-Tests in NestJS und welche grundlegenden Testing-Ansätze gibt es?</summary>

#### NestJS

Unit-Testing in NestJS fokussiert auf das isolierte Testen des Verhaltens einer
Klasse/eines Moduls, meistens mit gemockten Abhängigkeiten und ohne reale
Netzwerk-/Datenbankaufrufe.

#### Zentrale Testebenen in NestJS

1. **Unit-Tests**
   Testen Services/Guards/Pipes/Interceptors isoliert.

2. **Integrationstests**
   Testen Interaktion zwischen Komponenten/Modulen (oft mit Test-DB).

3. **E2E-Tests**
   Testen das vollständige HTTP-App-Verhalten über echten Nest-App-Bootstrap.

#### Typischer Unit-Testing-Stack

1. Jest als Test-Runner/Assertion-/Mocking-Tool.
2. `@nestjs/testing` zum Erstellen von Testing-Modulen.
3. Mock-Provider für Abhängigkeiten (`useValue`, `useFactory`).

#### Beispiel-Unit-Test für Service

```ts
import { Test, TestingModule } from '@nestjs/testing';
import { NotFoundException } from '@nestjs/common';

describe('UsersService', () => {
  let service: UsersService;
  const repoMock = {
    findById: jest.fn(),
  };

  beforeEach(async () => {
    const module: TestingModule = await Test.createTestingModule({
      providers: [
        UsersService,
        { provide: 'USERS_REPOSITORY', useValue: repoMock },
      ],
    }).compile();

    service = module.get(UsersService);
    jest.clearAllMocks();
  });

  it('returns user when found', async () => {
    repoMock.findById.mockResolvedValue({ id: 'u1', email: 'a@example.com' });
    await expect(service.getById('u1')).resolves.toEqual({
      id: 'u1',
      email: 'a@example.com',
    });
  });

  it('throws NotFoundException when user is missing', async () => {
    repoMock.findById.mockResolvedValue(null);
    await expect(service.getById('missing')).rejects.toBeInstanceOf(NotFoundException);
  });
});
```

#### Grundlegende Testing-Ansätze

1. **Arrange-Act-Assert**
   Tests lesbar und deterministisch halten.

2. **Externe Grenzen mocken**
   DB, HTTP-Clients, Queues und zeitabhängige Systeme.

3. **Verhalten testen, nicht Implementierungsdetails**
   Ergebnisse und Side Effects prüfen, nicht private Interna.

4. **Happy Path + Failure Path abdecken**
   Validierungsfehler, Exceptions, Edge Cases.

#### Was man in NestJS zuerst unit-testen sollte

1. Application-/Domain-Services.
2. Custom Guards/Pipes/Interceptors.
3. Utility-/Domain-Logikklassen.
4. Mapper-/Validierungslogik mit verzweigtem Verhalten.

#### Häufige Fehler

1. Reale DB-Aufrufe in „Unit“-Tests.
2. Over-Mocking bis Tests ihren Wert verlieren.
3. Fragile interne Calls zu strikt asserten.
4. Negative/Fehler-Szenarien ignorieren.

#### Faustregel

Unit-Tests sollten schnell, isoliert und deterministisch sein. Damit
Business-Logik-Verhalten absichern; Integration-/E2E-Tests für Wiring und
Laufzeitrealität nutzen.

</details>

<details>
<summary>98. Wie mockt man Abhängigkeiten in NestJS korrekt und wann sollte man das tun?</summary>

#### NestJS

Abhängigkeiten in NestJS zu mocken bedeutet, reale Kollaboratoren (DB-Repos,
HTTP-Clients, Queues, externe SDKs) durch kontrollierte Test-Doubles zu
ersetzen, um Unit-Verhalten isoliert zu testen.

#### Wann man mocken sollte

1. Bei Unit-Tests von Services/Guards/Pipes/Interceptors.
2. Für Failure-Path-Tests, die mit realen Systemen schwer auslösbar sind.
3. Für schnelle Feedback-Loops, wenn externe I/O Tests verlangsamen würde.

#### Wann man nicht mocken sollte

1. Bei Integrationstests, die Modul-Wiring und reale Adapter validieren.
2. Bei E2E-Tests, die vollständiges Laufzeitverhalten prüfen.
3. Wenn hohes Risiko für Contract Drift besteht und reale Interaktion wichtig ist.

#### Häufiges NestJS-Mocking-Pattern

`TestingModule` nutzen und Provider-Tokens mit `useValue`/`useFactory` überschreiben.

```ts
import { Test } from '@nestjs/testing';

describe('UsersService', () => {
  let service: UsersService;
  const usersRepoMock = {
    findById: jest.fn(),
    save: jest.fn(),
  };

  beforeEach(async () => {
    const moduleRef = await Test.createTestingModule({
      providers: [
        UsersService,
        { provide: 'USERS_REPOSITORY', useValue: usersRepoMock },
      ],
    }).compile();

    service = moduleRef.get(UsersService);
    jest.clearAllMocks();
  });
});
```

#### Mocking-Tipps nach Abhängigkeitstyp

1. **Repository/DAO**
   Nur konkret verwendete Methoden mocken (`findOne`, `save` usw.).

2. **HttpService / externer Client**
   Rückgabewerte/Fehler und Timeout-Szenarien mocken.

3. **Queue-/Event-Publisher**
   Enqueue/Publish-Calls mocken und Payload/Contracts asserten.

4. **ConfigService**
   Explizite Schlüssel mocken, die im Codepfad genutzt werden.

#### Gute Mocking-Praktiken

1. Nur Boundary-Abhängigkeiten mocken, nicht die Klasse unter Test.
2. Mocks minimal und verhaltensorientiert halten.
3. Mocks zwischen Tests zurücksetzen.
4. Zuerst Outcomes, danach Interaktionen asserten.
5. Negative Pfade (throws/rejects) explizit abdecken.

#### Häufige Fehler

1. Interne Methoden derselben Klasse over-mocken (testet Implementierungsdetails).
2. Stateful Mocks ohne Reset über Testfälle hinweg wiederverwenden.
3. Mock-Werte, die reale Contract-Form verletzen (falsches Vertrauen).
4. Nur Happy-Path-Tests schreiben.

#### Faustregel

Mocking isoliert Business-Logik und beschleunigt Unit-Tests. Integration-/E2E-
Tests prüfen dagegen echtes Wiring und externe Verträge.

</details>

<details>
<summary>99. Wie schreibt man Integrationstests in NestJS mit TestingModule?</summary>

#### NestJS

Integrationstests in NestJS prüfen, dass mehrere reale Komponenten korrekt
zusammenarbeiten (Modul-Wiring, DI, Repositories/Services, Pipes/Guards), sind
aber leichter als vollständige E2E-Tests.

`TestingModule` ist das zentrale Werkzeug, um den Test-App-Kontext
zusammenzubauen.

#### Ziel von Integrationstests

1. Interaktion zwischen realen Providern validieren.
2. DI-/Konfigurations-/Modul-Wiring-Probleme finden.
3. Persistence-/Service-Flows mit realistischen Abhängigkeiten testen.

#### Typischer Setup-Flow

1. `TestingModule` mit realen Modul(en) unter Test erstellen.
2. Optional nur externe Boundaries überschreiben (z. B. Third-Party-API).
3. App-/Modul-Kontext initialisieren.
4. Testdaten vorbereiten.
5. Szenario ausführen und Side Effects/Ergebnisse asserten.

#### Beispiel mit `TestingModule` + Repository/Service

```ts
import { Test, TestingModule } from '@nestjs/testing';

describe('UsersModule Integration', () => {
  let moduleRef: TestingModule;
  let service: UsersService;

  beforeAll(async () => {
    moduleRef = await Test.createTestingModule({
      imports: [UsersModule, TestDatabaseModule], // reales Modul-Wiring
    }).compile();

    service = moduleRef.get(UsersService);
  });

  afterAll(async () => {
    await moduleRef.close();
  });

  it('creates and loads user through real repository path', async () => {
    const created = await service.create({
      email: 'integration@example.com',
      password: 'secret123',
    });

    const loaded = await service.getById(created.id);
    expect(loaded.email).toBe('integration@example.com');
  });
});
```

#### Welche Abhängigkeiten man verwenden sollte

1. Reale DB in isolierter Testumgebung bevorzugen (Test-Container/In-Memory-DB,
   wo vertretbar).
2. Nur instabile/teure externe Systeme mocken (Payment Gateways, SaaS-APIs).
3. Konfiguration nahe an Produktionssemantik halten.

#### Strategien für Datenmanagement

1. Transaction-Rollback pro Test (wo möglich).
2. Tabellen zwischen Tests truncaten/resetten.
3. Deterministische Test-Fixtures/Builder.

#### Häufige Fehler

1. Integrationstests zu Unit-Tests machen, indem alles gemockt wird.
2. Mutablen globalen State zwischen Tests teilen.
3. Versehentlich von Produktions-/Staging-DB abhängen.
4. Kein Cleanup, was zu flakigen, reihenfolgeabhängigen Tests führt.

#### Praktische Regel

Integrationstests sollten reale Modul-Kollaboration mit minimalem Mocking
validieren. Sie sind das wichtigste Sicherheitsnetz gegen kaputtes Wiring und
Persistence-Regressionen.

</details>

<details>
<summary>100. Was ist End-to-End-(E2E)-Testing in NestJS und wie unterscheidet es sich von Unit- und Integrationstests?</summary>

#### NestJS

E2E-Testing (End-to-End) in NestJS prüft vollständiges Anwendungsverhalten über
reale öffentliche Schnittstellen (meist HTTP), nah an der realen Nutzung durch
Clients.

Es ist die Testebene mit dem höchsten Vertrauen für API-Verträge,
Middleware/Guards, Validierung, Error-Mapping und Infrastruktur-Wiring.

#### Wie sich E2E von anderen Testebenen unterscheidet

1. **Unit-Tests**
   Testen eine Klasse isoliert mit gemockten Abhängigkeiten.

2. **Integrationstests**
   Testen Zusammenarbeit mehrerer realer Komponenten/Module.

3. **E2E-Tests**
   Testen den vollständigen Pfad Request -> Framework-Pipeline ->
   Business-Logik -> Persistence -> Response.

#### Typisches NestJS-E2E-Setup

1. Testing-Module mit vollständigem `AppModule` (oder fast vollständig) erstellen.
2. Nest-Application-Instanz bootstrappen.
3. Reale HTTP-Requests senden (häufig via `supertest`).
4. Statuscodes, Response-Body und Side Effects asserten.

#### Minimales E2E-Beispiel

```ts
import { Test } from '@nestjs/testing';
import { INestApplication } from '@nestjs/common';
import request from 'supertest';

describe('Users E2E', () => {
  let app: INestApplication;

  beforeAll(async () => {
    const moduleRef = await Test.createTestingModule({
      imports: [AppModule],
    }).compile();

    app = moduleRef.createNestApplication();
    await app.init();
  });

  afterAll(async () => {
    await app.close();
  });

  it('POST /users creates a user', async () => {
    await request(app.getHttpServer())
      .post('/users')
      .send({ email: 'e2e@example.com', password: 'secret123' })
      .expect(201)
      .expect(res => {
        expect(res.body.email).toBe('e2e@example.com');
      });
  });
});
```

#### Was E2E besonders gut findet

1. Defektes Route-/Guard-/Pipe-/Interceptor-Setup.
2. Validierungs- und Serialisierungs-Mismatches.
3. Regressionen im Auth-Flow.
4. Drift realer API-Verträge.
5. Probleme bei globalem Error-Handling und Response-Shape.

#### Häufige Fallstricke

1. Nur auf E2E setzen (zu langsam für volle Logikabdeckung).
2. Gegen geteilte nicht-isolierte Umgebungen laufen.
3. Instabiles Setup/Cleanup von Testdaten führt zu flakigen Tests.
4. Zu breite E2E-Suite, die langsam und schwer wartbar wird.

#### Praktische Testing-Pyramide

1. Viele Unit-Tests (schnelles Logik-Vertrauen).
2. Einige Integrationstests (Wiring-Vertrauen).
3. Weniger, aber hochwertige E2E-Tests (Contract-Vertrauen).

#### Faustregel

E2E-Tests schützen kritische User-/Business-Journeys und externe API-Verträge;
Tests auf niedrigerer Ebene liefern Tiefe und Geschwindigkeit.

</details>

<details>
<summary>101. Was ist die Nest CLI und welche Befehle werden am häufigsten verwendet?</summary>

#### NestJS

Nest CLI ist das offizielle Kommandozeilen-Tool zum Erstellen, Generieren,
Starten und Warten von NestJS-Anwendungen.

Es standardisiert das Project-Scaffolding und beschleunigt die tägliche
Entwicklung.

#### Wofür die Nest CLI verwendet wird

1. Neue Projekte mit empfohlener Struktur erstellen.
2. Module/Controller/Services/Resources schnell generieren.
3. App im Dev-/Watch-Modus starten.
4. Produktions-Builds erstellen.
5. Tests über konfigurierte Skripte/Tooling ausführen.

#### Am häufigsten genutzte Befehle

1. **App erstellen**
   `nest new my-app`

2. **In Entwicklung starten**
   `npm run start:dev`
   (oder `nest start --watch`, je nach Setup)

3. **App bauen**
   `npm run build`
   (oder `nest build`)

4. **Modul generieren**
   `nest g module users`

5. **Controller generieren**
   `nest g controller users`

6. **Service generieren**
   `nest g service users`

7. **Vollständige CRUD-Resource generieren**
   `nest g resource users`

8. **Tests ausführen**
   `npm test`, `npm run test:watch`, `npm run test:e2e`

#### Nützliche Command-Aliasse

1. `nest generate` -> `nest g`
2. `nest controller` -> `nest g co`
3. `nest service` -> `nest g s`
4. `nest module` -> `nest g mo`

#### Praktisches Workflow-Beispiel

1. `nest g resource orders`
2. Domain-/Use-Case-Logik implementieren.
3. `npm run start:dev` für lokale Iteration.
4. `npm run test` und `npm run test:e2e`.
5. `npm run build` vor dem Release.

#### Best Practices

1. CLI-Generatoren nutzen, um teamweit konsistente Struktur zu halten.
2. Generierten Code prüfen und ungenutztes Boilerplate entfernen.
3. Explizite Architekturgrenzen gegenüber blind generierter Layer-Struktur bevorzugen.
4. Skripte in `package.json` am CI-Workflow des Teams ausrichten.

#### Faustregel

Nest CLI ist ein Produktivitätswerkzeug, keine Architektur. Schnell scaffolden,
danach Codebasis nach Domäne und Qualitätsstandards formen.

</details>

<details>
<summary>102. Wie organisiert man ein Dockerfile für eine NestJS-Anwendung korrekt (Multi-Stage-Build)?</summary>

#### NestJS

Ein korrektes Multi-Stage-Dockerfile für NestJS trennt Build-Time-Abhängigkeiten
vom Runtime-Image und ergibt dadurch kleinere, sicherere und schnellere
Produktions-Container.

#### Warum Multi-Stage-Build wichtig ist

1. Kleinere finale Image-Größe.
2. Reduzierte Angriffsfläche (kein Dev-/Build-Tooling im Runtime-Image).
3. Schnellere Deploy-/Pull-Zeiten.
4. Sauberere Abhängigkeitsgrenzen.

#### Empfohlene Multi-Stage-Struktur

1. **deps stage**
   Abhängigkeiten mit Lockfile installieren.

2. **build stage**
   TypeScript nach `dist` kompilieren.

3. **runtime stage**
   Nur kompilierten Output + Produktionsabhängigkeiten kopieren.

#### Beispiel-Dockerfile

```dockerfile
# -------- deps --------
FROM node:20-alpine AS deps
WORKDIR /app

COPY package*.json ./
RUN npm ci

# -------- build --------
FROM node:20-alpine AS build
WORKDIR /app

COPY --from=deps /app/node_modules ./node_modules
COPY . .
RUN npm run build

# -------- runtime --------
FROM node:20-alpine AS runtime
WORKDIR /app

ENV NODE_ENV=production

COPY package*.json ./
RUN npm ci --omit=dev && npm cache clean --force

COPY --from=build /app/dist ./dist

EXPOSE 3000
CMD ["node", "dist/main.js"]
```

#### Empfohlenes `.dockerignore`

1. `node_modules`
2. `dist`
3. `.git`
4. `coverage`
5. lokale Env-Dateien, die im Build-Kontext nicht benötigt werden

#### Security- und Runtime-Best-Practices

1. Wo möglich als non-root User ausführen.
2. Node-Major-Version pinnen und Base-Images aktuell halten.
3. Konfiguration über Environment/Secret-Manager injizieren, nicht ins Image backen.
4. Health Checks und Graceful Shutdown unterstützen.
5. Image in CI auf Vulnerabilities scannen.

#### Build-Performance-Tipps

1. Lockfiles früh kopieren, um Layer-Caching zu nutzen.
2. Dependency-Layer nicht durch häufige Source-only-Änderungen invalidieren.
3. Deterministische Installationen (`npm ci`) verwenden.

#### Häufige Fehler

1. Single-Stage-Image mit vollständigen Dev-Abhängigkeiten.
2. Source-Code und Build-Tools ins Runtime-Image ausliefern.
3. Gesamten Kontext vor Dependency-Installation kopieren (bricht Cache-Effizienz).
4. Secrets im Dockerfile oder in committetem `.env` speichern.

#### Faustregel

Frühere Stages fürs schwere Build nutzen, finale Stage schlank halten.
Produktions-Container sollte nur enthalten, was zum Ausführen von `dist/main.js`
notwendig ist.

</details>
