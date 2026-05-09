**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  NestJS <img src="./assets/nestjs.svg" width="40" height="40" alt="NestJS logo"/>
</h1>

<h2>Najpopularniejsze pytania i odpowiedzi rekrutacyjne dotyczące NestJS</h2>

<details>
<summary>1. Czym jest NestJS i jakie problemy rozwiązuje?</summary>

#### NestJS

NestJS to progresywny framework Node.js do budowy aplikacji backendowych.
Domyślnie opiera się na TypeScript i korzysta ze znanych koncepcji
architektonicznych z Angulara (moduły, dependency injection, dekoratory),
działając na adapterach HTTP, takich jak Express lub Fastify.

#### Jakie problemy rozwiązuje NestJS

1. **Brak struktury w rosnących aplikacjach Node.js**
   NestJS wymusza czytelne granice modułów (`@Module`), co ułatwia skalowanie
   i utrzymanie dużych codebase'ów.

2. **Trudne zarządzanie zależnościami**
   Wbudowane **Dependency Injection (DI)** zmniejsza ścisłe powiązania między
   klasami i poprawia testowalność.

3. **Boilerplate w obszarach przekrojowych**
   Guards, Pipes, Interceptors, Filters i Middleware dają spójne wzorce dla
   auth, walidacji, transformacji, logowania i obsługi błędów.

4. **Niespójna architektura między zespołami**
   NestJS dostarcza opiniotwórcze konwencje, dzięki czemu zespoły budują
   serwisy według jednego modelu mentalnego i przewidywalnej struktury projektu.

5. **Skomplikowana konfiguracja testów**
   Narzędzia testowe (`@nestjs/testing`) i architektura przyjazna DI upraszczają
   testy jednostkowe, integracyjne i e2e.

6. **Potrzeba wsparcia wielu transportów backendowych**
   NestJS wspiera HTTP REST, GraphQL, WebSockets i mikroserwisy (TCP, Redis,
   NATS, Kafka, gRPC itd.) w ramach jednego spójnego modelu programowania.

#### W skrócie

NestJS pomaga przejść od „działającego kodu Node.js” do **dobrze
ustrukturyzowanej, gotowej na skalowanie architektury backendowej** o wysokiej
utrzymywalności, testowalności i skalowalności zespołu.

</details>

<details>
<summary>2. Czym NestJS różni się od Express i Fastify?</summary>

#### NestJS

NestJS, Express i Fastify są ze sobą powiązane, ale działają na różnych
poziomach abstrakcji.

#### Główna różnica

1. **Express / Fastify** to frameworki serwera HTTP.
2. **NestJS** to framework aplikacyjny, który może działać na Express lub
   Fastify przez adaptery.

#### Architektura i model tworzenia aplikacji

1. **Express**
   Minimalistyczny i mało opiniotwórczy. Strukturę, wzorce DI, walidację i
   konwencje definiujesz ręcznie.

2. **Fastify**
   Również dość niskopoziomowy, ale zoptymalizowany pod wydajność, z ekosystemem
   pluginów i podejściem schema-first.

3. **NestJS**
   Oferuje gotową, opiniotwórczą architekturę: moduły, providery, controllery,
   dependency injection, lifecycle hooks i standaryzowany pipeline requestów.

#### Perspektywa wydajności

1. **Fastify** zwykle jest szybszy od Express pod względem surowej przepustowości HTTP.
2. **NestJS na adapterze Fastify** zazwyczaj daje lepszą wydajność niż NestJS na Express.
3. W większości systemów biznesowych architektura, utrzymywalność i szybkość
   pracy zespołu są ważniejsze niż różnice z mikrobenchmarków.

#### Porównanie funkcji w praktyce

1. **Dependency Injection**
   Natywne w NestJS; w Express/Fastify zwykle ręczne lub przez biblioteki zewnętrzne.

2. **Ergonomia testowania**
   NestJS ma wbudowane wzorce modułów testowych; frameworki niskopoziomowe
   wymagają więcej własnej konfiguracji.

3. **Skalowalność codebase'u**
   Konwencje NestJS zmniejszają chaos w większych zespołach i projektach.

4. **Zakres ekosystemu**
   NestJS łączy REST, GraphQL, WebSockets i mikroserwisy w jednym modelu mentalnym.

#### Kiedy wybrać które rozwiązanie

1. Wybierz **Express**, gdy tworzysz bardzo małe/proste usługi lub potrzebujesz zgodności legacy.
2. Wybierz **Fastify**, gdy priorytetem jest maksymalna przepustowość i niski narzut.
3. Wybierz **NestJS**, gdy potrzebujesz długoterminowej utrzymywalności,
   klarownej architektury i standaryzowanego podejścia backendowego.

</details>

<details>
<summary>3. Jakie są główne elementy składowe NestJS?</summary>

#### NestJS

NestJS składa się z kilku kluczowych elementów budujących architekturę aplikacji.
Razem tworzą one modularny, testowalny i skalowalny backend.

#### Główne elementy składowe

1. **Modules (`@Module`)**
   Podstawowa jednostka organizacyjna aplikacji. Grupuje powiązane controllery,
   providery i importy/eksporty. Pomaga wyznaczać granice domen.

2. **Controllers (`@Controller`)**
   Obsługują warstwę transportową (np. HTTP). Definiują endpointy
   (`@Get`, `@Post`, itd.) i mapują requesty na logikę aplikacyjną.

3. **Providers (`@Injectable`)**
   Klasy zarządzane przez DI container (najczęściej serwisy, repozytoria,
   adaptery). Zawierają logikę biznesową i współdzielone funkcje.

4. **Dependency Injection (DI)**
   Mechanizm wstrzykiwania zależności między klasami. Zmniejsza sprzężenie,
   poprawia testowalność i ułatwia wymianę implementacji.

5. **Pipes**
   Służą do walidacji i transformacji danych wejściowych przed wejściem do
   handlera (np. DTO validation, parse int).

6. **Guards**
   Decydują, czy request może przejść dalej (auth/authz).

7. **Interceptors**
   Opakowują wykonanie handlera przed i po jego uruchomieniu (logging, mapping
   odpowiedzi, cache, metryki, timeouty).

8. **Exception Filters**
   Centralizują obsługę błędów i mapowanie wyjątków na spójne odpowiedzi HTTP.

9. **Middleware**
   Działa na niskim poziomie requestu przed guardami (np. request ID,
   podstawowe logowanie, manipulacja nagłówkami).

10. **Decorators**
    Metadane deklaratywne używane przez framework (`@Controller`, `@Injectable`,
    `@UseGuards`, custom decorators).

#### Jak te elementy współpracują

1. Request trafia do middleware.
2. Guards sprawdzają dostęp.
3. Interceptors/Pipes przygotowują wykonanie.
4. Controller wywołuje providera (serwis).
5. Exception filters obsługują błędy.

#### W skrócie

Moduły organizują strukturę, controllery obsługują transport, providery zawierają
logikę, a komponenty pipeline (guards/pipes/interceptors/filters/middleware)
standaryzują zachowanie całej aplikacji.

</details>

<details>
<summary>4. Jaka jest rola TypeScript w NestJS i dlaczego tryb ścisły jest ważny?</summary>

#### NestJS

TypeScript jest domyślnym językiem NestJS i stanowi fundament jego modelu
architektonicznego: dekoratorów, dependency injection, DTO oraz kontraktów
między modułami.

#### Rola TypeScript w NestJS

1. **Silne typowanie i jawne kontrakty**
   Interfejsy, klasy i DTO jasno opisują dane wejścia/wyjścia i zależności.

2. **Lepsza współpraca z DI**
   Typy i klasy ułatwiają bezpieczne wstrzykiwanie providerów i utrzymanie granic
   modułów.

3. **Lepsze narzędzia deweloperskie**
   Autouzupełnianie, refaktoryzacja i wykrywanie błędów podczas kompilacji
   przyspieszają pracę zespołu.

4. **Skalowalność kodu**
   W dużych codebase'ach typy ograniczają „ukryte” regresje przy zmianach.

#### Dlaczego tryb ścisły (`"strict": true`) jest kluczowy

1. **Wykrywa błędy wcześniej**
   `null/undefined` i niejawne `any` są łapane na etapie kompilacji.

2. **Chroni granice modułów**
   Wymusza precyzyjne kontrakty między warstwami i serwisami.

3. **Zmniejsza ryzyko błędów runtime**
   Mniej niespodzianek w produkcji dzięki twardszym gwarancjom typów.

4. **Poprawia jakość kodu długoterminowo**
   Utrzymanie i onboarding są łatwiejsze, bo kod jest bardziej jednoznaczny.

#### Najważniejsze opcje strict (praktycznie)

1. `strictNullChecks`
2. `noImplicitAny`
3. `strictBindCallApply`
4. `noUncheckedIndexedAccess` (często warto rozważyć)

#### W skrócie

W NestJS TypeScript to nie „dodatek”, tylko element architektury. Tryb ścisły
przenosi wiele błędów z produkcji do kompilacji, co jest kluczowe dla stabilnych,
skalowalnych systemów backendowych.

</details>

<details>
<summary>5. Czym są dekoratory w NestJS? Podaj przykłady.</summary>

#### NestJS

Dekoratory w NestJS to adnotacje (`@...`) dodawane do klas, metod,
parametrów lub właściwości. Dostarczają metadane, które framework odczytuje,
aby zbudować routing, dependency injection, walidację i pozostałe elementy
pipeline'u requestu.

#### Dlaczego dekoratory są ważne

1. **Deklaratywna architektura**
   Zamiast „ręcznie” rejestrować trasy i zależności, opisujesz intencję
   bezpośrednio w kodzie.

2. **Spójność frameworka**
   Te same wzorce działają w HTTP, GraphQL, WebSockets i mikroserwisach.

3. **Kompozycja zachowań przekrojowych**
   Guards, interceptory, pipes i filtry można nakładać przez dekoratory.

#### Najczęstsze dekoratory w NestJS

1. **Klasy i moduły**
   1. `@Module()` — definiuje moduł.
   2. `@Injectable()` — oznacza providera zarządzanego przez DI.
   3. `@Controller('users')` — definiuje controller i prefix trasy.

2. **Metody routingu**
   1. `@Get()`, `@Post()`, `@Patch()`, `@Delete()` — mapowanie HTTP.

3. **Parametry requestu**
   1. `@Body()`
   2. `@Param('id')`
   3. `@Query('page')`
   4. `@Headers()`

4. **Zachowania przekrojowe**
   1. `@UseGuards(...)`
   2. `@UseInterceptors(...)`
   3. `@UsePipes(...)`
   4. `@UseFilters(...)`

5. **Metadane własne**
   1. `@SetMetadata('roles', ['admin'])`
   2. Custom decorators, np. `@Roles('admin')`

#### Przykład

```ts
import {
  Body,
  Controller,
  Get,
  Param,
  Post,
  UseGuards,
} from '@nestjs/common';

@Controller('users')
@UseGuards(JwtAuthGuard)
export class UsersController {
  @Get(':id')
  findOne(@Param('id') id: string) {
    return this.usersService.findOne(id);
  }

  @Post()
  create(@Body() dto: CreateUserDto) {
    return this.usersService.create(dto);
  }
}
```

#### W skrócie

Dekoratory to mechanizm metadanych, na którym opiera się NestJS. Umożliwiają
tworzenie czytelnej, deklaratywnej i skalowalnej architektury zamiast
niskopoziomowej konfiguracji imperatywnej.

</details>

<details>
<summary>6. Czym jest Reflect.metadata i jak NestJS używa go „pod maską”?</summary>

#### NestJS

`Reflect.metadata` to mechanizm metadanych (z `reflect-metadata`), który pozwala
zapisywać i odczytywać informacje o klasach, metodach i parametrach w runtime.
NestJS intensywnie z tego korzysta do działania dekoratorów.

#### Jak NestJS używa metadanych

1. **Routing**
   Dekoratory jak `@Controller`, `@Get`, `@Post` zapisują metadane tras.

2. **Dependency Injection**
   Nest odczytuje typy konstruktora (`design:paramtypes`) i rozwiązuje zależności.

3. **Guards / Interceptors / Pipes / Filters**
   Dekoratory typu `@UseGuards(...)` zapisują metadane pipeline’u requestu.

4. **Custom decorators**
   `@SetMetadata(...)` zapisuje własne flagi/polityki, które później czyta
   `Reflector` (np. w guardach autoryzacji).

#### Przykład idei

```ts
import 'reflect-metadata';

class ExampleService {}

class UsersController {
  constructor(private readonly service: ExampleService) {}
}

const types = Reflect.getMetadata('design:paramtypes', UsersController);
// [ExampleService]
```

Nest wykorzystuje taki odczyt, aby wstrzyknąć właściwy provider.

#### W skrócie

`Reflect.metadata` jest fundamentem modelu „dekoratory + DI” w NestJS. Bez niego
framework nie mógłby deklaratywnie budować routingu, zależności i pipeline’u
obsługi requestu.

</details>

<details>
<summary>7. Jak utworzyć własny dekorator w NestJS? (createParamDecorator, SetMetadata)</summary>

#### NestJS

W NestJS własne dekoratory tworzy się najczęściej na dwa sposoby:

1. **`createParamDecorator`** — gdy chcesz pobrać dane z requestu do parametru metody.
2. **`SetMetadata`** — gdy chcesz oznaczyć handler/controller metadanymi (np. role,
   flagi autoryzacyjne), które później odczyta guard/interceptor.

#### 1) Własny dekorator parametru (`createParamDecorator`)

Przykład `@CurrentUser()`:

```ts
import { createParamDecorator, ExecutionContext } from '@nestjs/common';

export const CurrentUser = createParamDecorator(
  (data: keyof any | undefined, ctx: ExecutionContext) => {
    const req = ctx.switchToHttp().getRequest();
    const user = req.user;
    return data ? user?.[data] : user;
  },
);
```

Użycie:

```ts
@Get('me')
getMe(@CurrentUser() user: any) {
  return user;
}

@Get('me/id')
getMyId(@CurrentUser('id') userId: string) {
  return { userId };
}
```

#### 2) Dekorator metadanych (`SetMetadata`)

Przykład `@Roles(...)`:

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Użycie:

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin', 'manager')
@Get('admin/report')
getAdminReport() {
  return { ok: true };
}
```

Guard odczytuje metadane przez `Reflector`.

#### Kiedy którego używać

1. `createParamDecorator`:
   1. Ekstrakcja danych z requestu (`user`, `tenantId`, `requestId`).

2. `SetMetadata`:
   1. Deklarowanie polityk i zachowań endpointu (`roles`, `public`, `rate-limit profile`).

#### Dobre praktyki

1. Utrzymuj dekoratory małe i jednoznaczne.
2. Nie wkładaj ciężkiej logiki biznesowej do dekoratora.
3. Dla `SetMetadata` używaj stałych kluczy (`ROLES_KEY`) zamiast „magic strings”.
4. Łącz dekoratory z guardami/pipes, by zachować czystą architekturę.

#### W skrócie

Własne dekoratory w NestJS to wygodny sposób na deklaratywne API:
`createParamDecorator` upraszcza dostęp do danych requestu, a `SetMetadata`
buduje czytelne i wielokrotnego użytku reguły endpointów.

</details>

<details>
<summary>8. Co robi @Injectable() i dlaczego jest potrzebny?</summary>

#### NestJS

`@Injectable()` oznacza klasę jako **providera** zarządzanego przez kontener DI
NestJS. Dzięki temu Nest może tworzyć jej instancję, rozwiązywać zależności i
wstrzykiwać ją do innych klas.

#### Co daje `@Injectable()`

1. **Rejestracja w systemie DI**
   Klasa staje się kandydatem do wstrzykiwania przez konstruktor.

2. **Rozwiązywanie zależności konstruktora**
   Nest odczytuje metadane typów i automatycznie dostarcza wymagane providery.

3. **Zarządzanie cyklem życia i scope**
   Provider może działać jako singleton (`DEFAULT`), `REQUEST` albo `TRANSIENT`.

4. **Lepsza testowalność**
   Łatwiej podmieniać zależności na mocki przez tokeny/provider override.

#### Przykład

```ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class UsersService {
  findAll() {
    return [{ id: 1, email: 'user@example.com' }];
  }
}
```

Wstrzyknięcie do controllera:

```ts
@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get()
  getUsers() {
    return this.usersService.findAll();
  }
}
```

#### Czy zawsze trzeba `@Injectable()`?

1. Dla klas, które mają być providerami DI — **tak, praktycznie zawsze**.
2. Dla prostych utili/statycznych helperów, które nie są wstrzykiwane — nie.

#### W skrócie

`@Injectable()` to sygnał dla NestJS: „ta klasa należy do kontenera DI”. Bez
tego tracisz automatyczne wstrzykiwanie, spójne zarządzanie zależnościami i
wygodę testowania.

</details>

<details>
<summary>9. Jaka jest różnica między dekoratorami @Controller oraz @Get()/@Post()?</summary>

#### NestJS

`@Controller` i `@Get()`/`@Post()` współpracują, ale mają różne poziomy
odpowiedzialności.

#### Główna różnica

1. **`@Controller(...)`**
   Definiuje klasę jako controller i ustawia **prefiks trasy** (np. `users`).

2. **`@Get()` / `@Post()` (i inne metody HTTP)**
   Definiują **konkretne endpointy** w metodach controllera i mapują je na
   odpowiednie HTTP verb.

#### Jak to działa razem

`@Controller('users')` + `@Get(':id')` = endpoint `GET /users/:id`.

#### Przykład

```ts
import { Body, Controller, Get, Param, Post } from '@nestjs/common';

@Controller('users')
export class UsersController {
  @Get()
  findAll() {
    return ['u1', 'u2'];
  }

  @Get(':id')
  findOne(@Param('id') id: string) {
    return { id };
  }

  @Post()
  create(@Body() dto: { email: string }) {
    return { created: true, ...dto };
  }
}
```

Mapowanie:

1. `GET /users` -> `findAll()`
2. `GET /users/:id` -> `findOne()`
3. `POST /users` -> `create()`

#### W skrócie

`@Controller` ustala „obszar” tras dla klasy, a `@Get()`/`@Post()` określają
konkretne operacje HTTP w tym obszarze.

</details>

<details>
<summary>10. Jak NestJS obsługuje żądania HTTP i określa, który controller wywołać?</summary>

#### NestJS

NestJS buduje mapę routingu na podstawie metadanych dekoratorów i uruchamia
zdefiniowany pipeline requestu dla dopasowanego handlera.

#### Przepływ wysokiego poziomu

1. Request trafia do adaptera platformy (Express/Fastify).
2. Router NestJS dopasowuje metodę + ścieżkę do handlera controllera.
3. Uruchamia pipeline frameworka:
   1. Middleware
   2. Guards
   3. Interceptors (przed)
   4. Pipes (parametry)
   5. Handler controllera
   6. Interceptors (po)
4. W przypadku błędu działają Exception Filters.

#### Skąd Nest wie, gdzie routować

1. `@Controller('users')` ustawia prefiks.
2. `@Get(':id')` / `@Post()` itp. ustawiają mapowanie endpointu.
3. Podczas bootstrapu Nest skanuje metadane i tworzy tablicę tras.

Przykład:

```ts
@Controller('users')
export class UsersController {
  @Get(':id')
  findOne(@Param('id') id: string) {
    return { id };
  }
}
```

To mapuje `GET /users/:id` do `UsersController.findOne`.

#### Dodatkowe uwagi

1. Routing jest deterministyczny — kolejność i specyfika tras mają znaczenie.
2. Globalne i lokalne komponenty pipeline są łączone według poziomu
   (globalny -> controller -> route).
3. Adapter (Express/Fastify) wpływa głównie na warstwę transportową,
   ale model Nest pozostaje spójny.

#### W skrócie

NestJS routuje requesty przez metadane dekoratorów, a następnie wykonuje
standaryzowany pipeline, który zapewnia spójność auth, walidacji i obsługi
odpowiedzi w całej aplikacji.

</details>

<details>
<summary>11. Jak NestJS używa dekoratorów do budowy warstwy routingu?</summary>

#### NestJS

NestJS buduje routing na podstawie metadanych zapisanych przez dekoratory
w klasach controllerów i ich metodach.

#### Jak to działa

1. **`@Controller('prefix')`**
   Ustawia bazowy segment ścieżki dla klasy.

2. **`@Get()`, `@Post()`, `@Patch()`...**
   Ustawiają mapowanie HTTP method + podścieżka dla konkretnej metody.

3. **Bootstrap skanuje metadane**
   Nest odczytuje metadane dekoratorów i rejestruje finalne trasy
   w adapterze Express/Fastify.

#### Przykład

```ts
@Controller('users')
export class UsersController {
  @Get()
  findAll() {
    return [];
  }

  @Get(':id')
  findOne(@Param('id') id: string) {
    return { id };
  }

  @Post()
  create(@Body() dto: CreateUserDto) {
    return dto;
  }
}
```

Powstają trasy:

1. `GET /users`
2. `GET /users/:id`
3. `POST /users`

#### Rozszerzenie przez dekoratory dodatkowe

1. `@UseGuards(...)` — auth/authz na poziomie routingu.
2. `@UsePipes(...)` — walidacja/transformacja argumentów route.
3. `@UseInterceptors(...)` — mapowanie odpowiedzi, logowanie, cache.
4. `@Version(...)` — wersjonowanie endpointów.

#### Dlaczego to ważne

1. Routing jest deklaratywny i czytelny.
2. Konfiguracja endpointu i polityk znajduje się „obok” kodu handlera.
3. Skalowanie zespołu jest łatwiejsze dzięki jednolitemu wzorcowi.

#### W skrócie

Dekoratory są językiem opisu warstwy HTTP w NestJS: definiują ścieżki,
metody i zachowania przekrojowe, a framework przekształca to w działający
router podczas uruchamiania aplikacji.

</details>

<details>
<summary>12. Jaka jest różnica między imports, exports, providers i declarations w @Module?</summary>

#### NestJS

W NestJS `@Module()` zarządza granicami i widocznością zależności między
modułami. Najważniejsze pola to `imports`, `providers`, `exports`.
`declarations` **nie istnieje w NestJS** (to pojęcie z Angulara).

#### Rola każdego pola

1. **`imports`**
   Moduły, których wyeksportowane providery chcesz używać w tym module.

2. **`providers`**
   Klasy/factory/value dostępne w kontenerze DI tego modułu.

3. **`exports`**
   Podzbiór providerów z bieżącego modułu, które udostępniasz innym modułom.

4. **`declarations`**
   Brak w NestJS. Jeśli ktoś używa tego terminu, zwykle myli NestJS z Angularem.

#### Przykład

```ts
@Module({
  imports: [DatabaseModule],
  providers: [UsersService, UsersRepository],
  exports: [UsersService],
})
export class UsersModule {}
```

Znaczenie:

1. `UsersModule` korzysta z rzeczy eksportowanych przez `DatabaseModule`.
2. `UsersService` i `UsersRepository` są lokalnymi providerami.
3. Na zewnątrz wystawiony jest tylko `UsersService`.

#### Typowa pułapka

Jeśli provider nie działa w innym module:

1. upewnij się, że moduł źródłowy ma go w `exports`,
2. a moduł docelowy ma moduł źródłowy w `imports`.

#### W skrócie

`imports` = co pobierasz z innych modułów,
`providers` = co definiujesz lokalnie,
`exports` = co wystawiasz dalej,
`declarations` = nie dotyczy NestJS.

</details>

<details>
<summary>13. Jaka jest różnica między @Module imports i @Module providers?</summary>

#### NestJS

`imports` i `providers` w `@Module()` pełnią różne role w kontenerze DI.

#### Główna różnica

1. **`imports`**
   Lista modułów, z których chcesz korzystać.
   Dostajesz dostęp tylko do tego, co te moduły **eksportują**.

2. **`providers`**
   Lista providerów tworzonych lokalnie w bieżącym module.
   Są dostępne wewnątrz modułu i mogą być eksportowane dalej.

#### Jak myśleć praktycznie

1. `imports` = „jakie moduły podłączam”.
2. `providers` = „jakie serwisy/factory definiuję tutaj”.

#### Przykład

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
export class OrdersModule {}
```

W `OrdersModule`:

1. `UsersService` jest dostępny, bo został wyeksportowany przez `UsersModule`.
2. `OrdersService` jest zdefiniowany lokalnie w `providers`.

#### Typowe błędy

1. Dodanie serwisu do `imports` zamiast do `providers`.
2. Oczekiwanie, że `imports` da dostęp do wszystkich providerów modułu
   (dostępne są tylko exporty).

#### W skrócie

`imports` służy do podpinania modułów,
`providers` służy do deklarowania lokalnych zależności DI.

</details>

<details>
<summary>14. Czym są moduły dynamiczne i kiedy warto ich używać?</summary>

#### NestJS

Moduł dynamiczny to moduł, który zwraca konfigurację w runtime przez metodę
statyczną (najczęściej `forRoot`, `forRootAsync`, `register`, `registerAsync`).
Pozwala to budować moduły wielokrotnego użytku i konfigurować je zależnie od
środowiska/projektu.

#### Po co moduły dynamiczne

1. **Parametryzacja modułu**
   Np. przekazanie URL bazy, klucza API, opcji cache.

2. **Asynchroniczna konfiguracja**
   Pobranie konfiguracji z `ConfigService`, secret managera lub zewnętrznego źródła.

3. **Biblioteki współdzielone**
   Tworzenie modułów reusable dla wielu aplikacji.

4. **Warunkowe providery**
   Różne implementacje providerów zależnie od opcji.

#### Przykład (`forRoot`)

```ts
import { DynamicModule, Module } from '@nestjs/common';

@Module({})
export class EmailModule {
  static forRoot(options: { apiKey: string }): DynamicModule {
    return {
      module: EmailModule,
      providers: [
        {
          provide: 'EMAIL_OPTIONS',
          useValue: options,
        },
        EmailService,
      ],
      exports: [EmailService],
    };
  }
}
```

Użycie:

```ts
@Module({
  imports: [EmailModule.forRoot({ apiKey: process.env.EMAIL_API_KEY! })],
})
export class AppModule {}
```

#### Kiedy używać

1. Gdy moduł wymaga konfiguracji z zewnątrz.
2. Gdy chcesz dostarczyć moduł jako bibliotekę dla innych zespołów/aplikacji.
3. Gdy potrzebujesz `forRootAsync` z DI (`ConfigService`, factory providers).

#### Kiedy nie komplikować

1. Jeśli moduł nie potrzebuje żadnej konfiguracji,
   zwykły `@Module` zwykle wystarczy.

#### W skrócie

Moduły dynamiczne to standardowy sposób tworzenia konfigurowalnych,
skalowalnych i wielokrotnego użytku modułów infrastrukturalnych w NestJS.

</details>

<details>
<summary>15. Jaka jest różnica między typami providerów w NestJS? (useClass, useValue, useFactory)</summary>

#### NestJS

W NestJS provider można zarejestrować na kilka sposobów. Najczęściej używa się
`useClass`, `useValue` i `useFactory`.

#### 1) `useClass`

Wskazuje klasę, którą kontener DI ma utworzyć dla danego tokenu.

```ts
{
  provide: PaymentPort,
  useClass: StripePaymentService,
}
```

**Kiedy używać:**

1. Gdy chcesz podpiąć konkretną implementację pod interfejs/token.
2. Gdy implementacja ma własne zależności DI.

#### 2) `useValue`

Wstrzykuje gotową wartość/obiekt bez tworzenia instancji przez Nest.

```ts
{
  provide: 'APP_CONFIG',
  useValue: {
    featureX: true,
    timeoutMs: 3000,
  },
}
```

**Kiedy używać:**

1. Konfiguracja statyczna.
2. Mocki w testach.
3. Proste singletony bez logiki inicjalizacji.

#### 3) `useFactory`

Tworzy wartość dynamicznie przez funkcję fabrykującą.
Może korzystać z innych providerów przez `inject`.

```ts
{
  provide: 'REDIS_CLIENT',
  useFactory: (config: ConfigService) => {
    return new Redis(config.getOrThrow('REDIS_URL'));
  },
  inject: [ConfigService],
}
```

**Kiedy używać:**

1. Gdy obiekt wymaga logiki tworzenia.
2. Gdy konfiguracja zależy od środowiska/DI.
3. Gdy potrzebna jest warunkowa inicjalizacja.

#### W skrócie

1. `useClass` -> wybór implementacji klasy.
2. `useValue` -> gotowy obiekt/wartość.
3. `useFactory` -> dynamiczne tworzenie z logiką i zależnościami.

Dobór zależy od tego, czy provider ma być prosty, klasowy czy konfigurowany
w runtime.

</details>

<details>
<summary>16. Czym jest scope providera? (DEFAULT, REQUEST, TRANSIENT)</summary>

#### NestJS

Scope providera określa, **kiedy i jak często** Nest tworzy jego instancję.
To ważne dla wydajności, izolacji danych i projektowania zależności.

#### Typy scope

1. **`DEFAULT` (singleton)**
   Jedna instancja providera na cały proces aplikacji.

2. **`REQUEST`**
   Nowa instancja providera dla każdego requestu.

3. **`TRANSIENT`**
   Nowa instancja za każdym razem, gdy provider jest wstrzykiwany.

#### 1) `DEFAULT`

```ts
@Injectable()
export class UsersService {}
```

Domyślne zachowanie.

**Plusy:**

1. Najlepsza wydajność.
2. Mały narzut pamięci/CPU.

**Użycie:**

1. Serwisy stateless.
2. Reużywalna logika biznesowa.

#### 2) `REQUEST`

```ts
@Injectable({ scope: Scope.REQUEST })
export class RequestContextService {}
```

**Plusy:**

1. Izolacja danych per request.

**Minusy:**

1. Większy narzut wydajnościowy.

**Użycie:**

1. Kontekst requestu, tenant context, audit per request.

#### 3) `TRANSIENT`

```ts
@Injectable({ scope: Scope.TRANSIENT })
export class RandomIdService {}
```

**Zachowanie:**

1. Każdy konsument dostaje nową instancję.

**Użycie:**

1. Krótkotrwałe obiekty pomocnicze ze stanem lokalnym.

#### Praktyczna zasada

1. Domyślnie używaj `DEFAULT`.
2. `REQUEST` tylko gdy naprawdę potrzebujesz izolacji per request.
3. `TRANSIENT` dla specyficznych przypadków, gdzie singleton/request scope nie pasuje.

#### W skrócie

Scope to kompromis między wydajnością a izolacją stanu:
`DEFAULT` jest najtańszy, `REQUEST` najbezpieczniejszy kontekstowo,
a `TRANSIENT` daje największą „świeżość” instancji.

</details>

<details>
<summary>17. Jak radzić sobie z cyklicznymi zależnościami (forwardRef) w dużych systemach?</summary>

#### NestJS

Cykliczna zależność występuje, gdy dwa elementy zależą od siebie bezpośrednio
lub pośrednio (A -> B i B -> A). W NestJS może to dotyczyć modułów albo
providerów.

`forwardRef()` pozwala przerwać ten cykl na poziomie rozwiązywania zależności,
ale powinien być traktowany jako rozwiązanie tymczasowe/ostrożne.

#### Kiedy użyć `forwardRef`

1. Gdy refaktoryzacja nie jest od razu możliwa, a trzeba odblokować start systemu.
2. Gdy zależność jest realnie dwukierunkowa w krótkim okresie.

#### Przykład provider-level

```ts
@Injectable()
export class UsersService {
  constructor(
    @Inject(forwardRef(() => OrdersService))
    private readonly ordersService: OrdersService,
  ) {}
}

@Injectable()
export class OrdersService {
  constructor(
    @Inject(forwardRef(() => UsersService))
    private readonly usersService: UsersService,
  ) {}
}
```

#### Przykład module-level

```ts
@Module({
  imports: [forwardRef(() => OrdersModule)],
  providers: [UsersService],
  exports: [UsersService],
})
export class UsersModule {}

@Module({
  imports: [forwardRef(() => UsersModule)],
  providers: [OrdersService],
  exports: [OrdersService],
})
export class OrdersModule {}
```

#### Lepsze podejścia długoterminowe

1. Wydziel wspólną logikę do trzeciego serwisu/modułu (`ApplicationService`, `DomainService`).
2. Zastąp bezpośrednie wywołanie zdarzeniami (event-driven komunikacja).
3. Użyj portów/interfejsów zamiast twardych referencji klas.
4. Przenieś orkiestrację do wyższej warstwy use-case.

#### Sygnał architektoniczny

Cykle często oznaczają zbyt silne sprzężenie między bounded contexts.
W dużych systemach to zwykle sygnał do refaktoryzacji granic modułów.

#### W skrócie

`forwardRef()` naprawia problem DI „tu i teraz”, ale nie naprawia projektu.
Używaj go oszczędnie i planuj usunięcie cyklu przez lepszy podział
odpowiedzialności.

</details>

<details>
<summary>18. Jak zaprojektować skalowalną aplikację NestJS?</summary>

#### NestJS

Skalowalna aplikacja NestJS opiera się na wyraźnych granicach domen,
kontrolowanym kierunku zależności i przewidywalnych wzorcach przekrojowych.

#### Kluczowe zasady struktury

1. **Modularność według domeny (bounded contexts)**
   Dziel aplikację według możliwości biznesowych (`Users`, `Billing`, `Orders`),
   a nie wyłącznie według warstw technicznych.

2. **Warstwowe odpowiedzialności w module**
   Controller powinien być cienki, service skoncentrowany na orkiestracji,
   a adaptery infrastrukturalne odizolowane.

3. **Reguła zależności**
   Logika biznesowa wyższego poziomu nie powinna zależeć bezpośrednio od
   frameworka ani szczegółów infrastruktury.

4. **Jawne kontrakty**
   Używaj DTO, schematów walidacji i interfejsów/tokenów na granicach.

#### Przykładowy układ modułu

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

#### Wzorce architektoniczne, które skalują

1. **Feature modules + shared kernel**
   Utrzymuj część wspólną małą, aby uniknąć „god common module”.

2. **Ports and adapters**
   Warstwa biznesowa zależy od abstrakcji, a adaptery implementują DB/API/broker.

3. **CQRS tam, gdzie jest uzasadnione**
   Rozdziel model write/read w złożonych domenach, nie wszędzie domyślnie.

4. **Granice asynchroniczne**
   Używaj eventów/kolejek dla przepływów między modułami i eventual consistency.

#### Skalowalność operacyjna

1. **Zarządzanie konfiguracją**
   Scentralizowana, typowana konfiguracja z walidacją środowiska.

2. **Obserwowalność**
   Structured logging, tracing, metryki i correlation IDs.

3. **Strategia błędów**
   Globalne exception filters + mapowanie błędów domenowych.

4. **Wydajność**
   Cache, paginacja, backpressure, indeksy DB i unikanie nadmiernego request scope.

#### Praktyki skalowania zespołu

1. Egzekwuj bramki lint/format/type/test w CI.
2. Utrzymuj jasne ownership modułów (codeowners/mapa odpowiedzialności).
3. Przeglądaj decyzje architektoniczne (ADR) dla nowych zależności cross-domain.
4. Preferuj refaktoryzację inkrementalną zamiast „big-bang rewrite”.

#### W skrócie

Skalowalność w NestJS to głównie dyscyplina architektoniczna: moduły zorientowane
na domenę, kontrolowane zależności i standaryzowane aspekty platformowe wokół nich.

</details>

<details>
<summary>19. Jak zaprojektować API REST z poprawnym rozdzieleniem odpowiedzialności?</summary>

#### NestJS

Poprawny podział odpowiedzialności w API REST opartym o NestJS oznacza, że każda
warstwa ma jedną, jasną rolę, a zależności płyną w jednym kierunku.

#### Zalecany podział odpowiedzialności

1. **Warstwa controller (transport)**
   Obsługuje tylko kwestie HTTP: routing, status codes, mapowanie request/response,
   dekoratory auth i bindowanie danych wejściowych.

2. **Warstwa application/service (use cases)**
   Orkiestruje przepływy biznesowe i transakcje; bez logiki specyficznej dla HTTP.

3. **Warstwa domain (reguły biznesowe)**
   Enkapsuluje reguły, inwarianty, encje/value objects i domain services.

4. **Warstwa infrastructure**
   Implementuje persystencję, API zewnętrzne, kolejki i inne adaptery.

#### Czego nie mieszać

1. Zapytań DB w controllerach.
2. Obiektów HTTP (`Request`, `Response`) w logice domenowej.
3. Rozproszonej walidacji i inwariantów biznesowych po wielu warstwach.
4. Szczegółów SDK zewnętrznych wyciekających do kontraktów use-case.

#### Praktyczny przepływ

1. Controller przyjmuje DTO (`@Body`, `@Query`, `@Param`).
2. Pipe waliduje/transformuje DTO.
3. Controller wywołuje metodę application service.
4. Service używa repository/portów i reguł domeny.
5. Service zwraca model wyniku.
6. Controller mapuje wynik do response DTO/view model.

#### Szkielet przykładu

```ts
// controller
@Post()
create(@Body() dto: CreateOrderDto): Promise<OrderView> {
  return this.ordersAppService.createOrder(dto);
}

// application service
async createOrder(dto: CreateOrderDto): Promise<OrderView> {
  const order = Order.create(dto.customerId, dto.items); // reguła domenowa
  await this.ordersRepo.save(order);                     // port infrastruktury
  return OrderView.from(order);                          // mapowanie wyjścia
}
```

#### Techniki projektowe, które pomagają

1. **DTO dla kontraktów API**
   Oddziel kontrakty wejścia/wyjścia od encji wewnętrznych.

2. **Interfejsy repository/port**
   Warstwa biznesowa zależy od abstrakcji, nie bezpośrednio od klienta ORM.

3. **Globalne komponenty przekrojowe**
   Używaj guards/pipes/interceptors/filters dla auth, walidacji, logowania i błędów.

4. **Wersjonowanie i idempotencja**
   Stosuj strategię wersjonowania API i klucze idempotencji dla operacji niebezpiecznych.

5. **Spójny model błędów**
   Mapuj błędy domeny/infrastruktury na stabilne odpowiedzi HTTP.

#### Efekt

Przy takim podziale API łatwiej testować, refaktoryzować i skalować: zmiany
transportu nie psują logiki domenowej, a infrastruktura może ewoluować niezależnie.

</details>

<details>
<summary>20. Jaki jest pełny lifecycle requestu w NestJS?</summary>

#### NestJS

Lifecycle requestu w NestJS to deterministyczny pipeline wokół dopasowanego
route handlera. Zrozumienie tej kolejności jest kluczowe przy debugowaniu auth,
walidacji i formatowania odpowiedzi.

#### Sekwencja wysokiego poziomu

1. Przychodzący request trafia do adaptera platformy (Express/Fastify).
2. Trasa zostaje dopasowana do metody controllera.
3. Nest wykonuje komponenty pipeline frameworka w określonej kolejności.
4. Zwracana jest odpowiedź (lub wyjątek przechwytują filtry).

#### Szczegółowa kolejność lifecycle

1. **Middleware**
   Działa przed guardami; używane do niskopoziomowego preprocessingu requestu
   (logging, correlation ID, manipulacja nagłówkami itp.).

2. **Guards**
   Decydują, czy wykonanie jest dozwolone (`canActivate`).
   Jeśli guard zwróci `false`/rzuci wyjątek, request kończy się na tym etapie.

3. **Interceptors (przed handlerem)**
   Owijają wykonanie; mogą uruchamiać timery, dołączać kontekst
   albo short-circuitować zachowanie.

4. **Pipes**
   Działają na argumentach trasy, by transformować/walidować dane wejściowe
   (`@Body`, `@Param`, `@Query`, custom params).

5. **Controller handler**
   Uruchamiany jest use-case biznesowy (najczęściej delegujący do service layer).

6. **Interceptors (po handlerze)**
   Mogą mapować/streamować/cache'ować odpowiedź i finalizować logikę obserwowalności.

7. **Exception filters**
   Przechwytują nieobsłużone wyjątki i zamieniają je na odpowiedzi HTTP.

#### Wizualny model wykonania

1. Middleware -> Guards -> Interceptors (pre) -> Pipes -> Handler ->
   Interceptors (post) -> Response
2. Dowolny błąd rzucony w pipeline/handlerze -> Exception Filters

#### Uwagi o scope i priorytecie

1. Większość komponentów pipeline można zastosować na poziomie:
   1. Globalnym
   2. Controllera
   3. Route-handlera
2. Nest łączy te poziomy; konfiguracja route-level jest zwykle najbardziej szczegółowa.

#### Praktyczny wniosek debugowania

Jeśli zachowanie jest nieoczekiwane:
1. Najpierw sprawdź, czy request blokuje guard.
2. Zweryfikuj transformację/walidację pipe'ów na parametrach.
3. Sprawdź łańcuch interceptorów pod kątem mapowania odpowiedzi.
4. Potwierdź formatowanie błędów przez exception filters.

Znajomość tej kolejności eliminuje „magiczne” założenia i znacząco przyspiesza
diagnozowanie incydentów produkcyjnych.

</details>

<details>
<summary>21. Jaka jest różnica między Middleware, Guards, Pipes i Interceptors?</summary>

#### NestJS

Te cztery komponenty działają w pipeline requestu NestJS, ale mają różne
odpowiedzialności i uruchamiają się na różnych etapach cyklu życia.

#### Szybkie porównanie ról

1. **Middleware**
   Preprocessing HTTP przed routingiem/handlerem.

2. **Guards**
   Bramka autoryzacyjna: decydują, czy request może iść dalej.

3. **Pipes**
   Transformują i walidują argumenty handlera.

4. **Interceptors**
   Owijają wykonanie handlera przed i po, umożliwiając logikę przekrojową
   wokół odpowiedzi.

#### Głębsza różnica odpowiedzialności

1. **Middleware**
   Najlepsze do generycznych zadań transportowych: request logging,
   correlation IDs, nagłówki, cookie parsing, surowa modyfikacja requestu.

2. **Guards**
   Najlepsze do auth/authz: JWT, role, policy checks.
   Zwracają `true/false` (lub rzucają wyjątek), aby zezwolić/odrzucić request.

3. **Pipes**
   Najlepsze do poprawności wejścia: parsing (`string -> number`), walidacja
   reguł DTO, sanitizacja/normalizacja na poziomie parametrów.

4. **Interceptors**
   Najlepsze do opakowania wykonania: mapowanie odpowiedzi, cache, metryki,
   tracing, timeout/retry wrappers, obsługa streamów.

#### Pozycja w lifecycle

1. Middleware
2. Guards
3. Interceptors (before)
4. Pipes
5. Handler
6. Interceptors (after)
7. Exception filters (ścieżka błędu)

#### Typowe przykłady

1. Middleware: dołączenie `requestId`.
2. Guard: odrzucenie requestu przy niepoprawnym tokenie.
3. Pipe: walidacja `CreateUserDto`.
4. Interceptor: transformacja odpowiedzi do koperty `{ data, meta }`.

#### Reguła wyboru

1. Potrzebujesz zdecydować **kto ma dostęp**? -> Guard.
2. Potrzebujesz zapewnić **kształt/typ wejścia**? -> Pipe.
3. Potrzebujesz **opakowania before/after handler**? -> Interceptor.
4. Potrzebujesz niskopoziomowego preprocessingu HTTP poza semantyką routingu? -> Middleware.

</details>

<details>
<summary>22. Jak stosować Middleware globalnie vs dla konkretnej trasy?</summary>

#### NestJS

W NestJS middleware konfiguruje się na poziomie modułu przez
`NestModule.configure()`. Możesz zastosować je globalnie dla wszystkich tras
albo selektywnie dla wybranych controllerów/endpointów.

#### 1) Zastosowanie globalne (wszystkie trasy)

Użyj `forRoutes('*')`.

```ts
import { MiddlewareConsumer, Module, NestModule } from '@nestjs/common';

@Module({})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer.apply(LoggerMiddleware).forRoutes('*');
  }
}
```

#### 2) Zastosowanie dla konkretnego controllera/tras

Używaj, gdy logika dotyczy tylko danej funkcjonalności.

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
        UsersController, // wszystkie trasy controllera
        { path: 'users/:id', method: RequestMethod.PATCH }, // konkretna trasa
      );
  }
}
```

#### Wykluczanie tras

Możesz zastosować middleware szeroko i wykluczyć konkretne endpointy:

```ts
consumer
  .apply(AuthMiddleware)
  .exclude(
    { path: 'health', method: RequestMethod.GET },
    { path: 'auth/login', method: RequestMethod.POST },
  )
  .forRoutes('*');
```

#### Praktyczne wskazówki

1. Globalne middleware tylko dla naprawdę przekrojowych potrzeb.
2. Utrzymuj middleware lekkie; cięższa logika authz powinna być w Guardach.
3. Middleware per-route stosuj do zachowań ograniczonych do konkretnego feature.
4. Gdy potrzebujesz logiki zależnej od metadanych/dekoratorów, rozważ Guards/Interceptors.

</details>

<details>
<summary>23. Czym jest ExecutionContext i jak się go używa?</summary>

#### NestJS

`ExecutionContext` to abstrakcja NestJS opisująca aktualne środowisko wykonania
handlera. Rozszerza `ArgumentsHost` i daje Guardom, Interceptorom, Filterom
oraz custom decorators jednolity dostęp do danych requestu w różnych transportach.

#### Dlaczego `ExecutionContext` istnieje

1. **Transport-agnostic access**
   Ten sam wzorzec API działa dla HTTP, WebSockets i mikroserwisów.

2. **Introspekcja handlera/klasy**
   Możesz sprawdzić, jaka klasa controllera i metoda są wykonywane.

3. **Spójność komponentów przekrojowych**
   Guards/interceptors/filters pracują na jednym modelu kontekstu.

#### Kluczowe API

1. `context.getType()`
   Zwraca typ wykonania (`http`, `ws`, `rpc`).

2. `context.switchToHttp()`
   Dostęp do `getRequest()`, `getResponse()`, `getNext()`.

3. `context.switchToWs()` / `context.switchToRpc()`
   Dostęp do danych specyficznych dla websocketów/mikroserwisów.

4. `context.getClass()` i `context.getHandler()`
   Zwracają aktualną klasę controllera i referencję metody.

#### Typowe użycie w Guardzie

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

#### Typowe użycie z metadata + Reflector

```ts
const isPublic = this.reflector.getAllAndOverride<boolean>('isPublic', [
  context.getHandler(),
  context.getClass(),
]);
```

Ten wzorzec odczytuje metadane trasy/klasy (`@Public()`, `@Roles(...)`) i jest
powszechny w guardach autoryzacji.

#### Praktyczny wniosek

Traktuj `ExecutionContext` jako runtime envelope aktualnego wywołania endpointu:
mówi **gdzie jesteś** (handler/klasa/transport) i pozwala bezpiecznie pobrać
transport-specific dane requestu.

</details>

<details>
<summary>24. Czym jest Guard i czym różni się od Middleware?</summary>

#### NestJS

**Guard** w NestJS to klasa implementująca `CanActivate`, która decyduje,
czy bieżący request może dotrzeć do route handlera.

#### Co robi Guard

1. Działa przed wykonaniem handlera.
2. Zwraca `true`, aby dopuścić request, `false` (lub rzuca wyjątek), aby go odrzucić.
3. Ma dostęp do `ExecutionContext` (handler, controller, transport, request).
4. Najczęściej służy do authentication i authorization.

#### Czym Guard różni się od Middleware

1. **Cel decyzji**
   Guard to jawna bramka autoryzacyjna.
   Middleware to ogólny preprocessing requestu.

2. **Świadomość frameworka**
   Guard zna docelowy handler/klasę przez `ExecutionContext`.
   Middleware zwykle nie ma kontekstu metadanych route-handlera.

3. **Pozycja w lifecycle**
   Middleware działa wcześniej.
   Guard działa po middleware, przed pipes/interceptors/handler.

4. **Typowe use-case**
   Guard: JWT/role/policies.
   Middleware: logging, request IDs, normalizacja nagłówków,
   surowa modyfikacja requestu.

#### Przykład Guarda

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

#### Reguła praktyczna

1. Potrzebujesz zdecydować „czy ten użytkownik ma dostęp do tej trasy?” -> **Guard**.
2. Potrzebujesz niskopoziomowego preprocessingu HTTP przed semantyką trasy -> **Middleware**.

</details>

<details>
<summary>25. Jak Guardy integrują się z autoryzacją?</summary>

#### NestJS

Guardy są główną bramką autoryzacji w NestJS. Ocenią, czy aktualnie
uwierzytelniony podmiot może uzyskać dostęp do konkretnej trasy, łącząc tożsamość
requestu z metadanymi endpointu (role, polityki, uprawnienia).

#### Typowy przepływ autoryzacji z Guardami

1. **Krok uwierzytelnienia**
   Poprzedni guard (lub strategia Passport) waliduje token/sesję i dołącza
   `request.user`.

2. **Deklaracja metadanych na trasie**
   Trasa ma wymagania, np. `@Roles('admin')` lub klucze polityk.

3. **Ewaluacja Guarda autoryzacyjnego**
   Guard czyta metadane przez `Reflector` oraz `request.user` i podejmuje decyzję.

4. **Zezwolenie lub odmowa**
   Zwraca `true`, aby przejść dalej, inaczej `false` lub rzuca `ForbiddenException`.

#### Przykład RBAC (role-based)

Dekorator ról:

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

Użycie:

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Wzorce integracji w realnych systemach

1. **Stackowane guardy**
   `JwtAuthGuard` (tożsamość) + `Roles/PoliciesGuard` (logika autoryzacji).

2. **ABAC/policy engine**
   Guard deleguje decyzję do serwisu policy (`subject`, `action`, `resource`).

3. **Context-aware checks**
   Guard czyta parametry trasy/właściciela zasobu i egzekwuje reguły ownership.

#### Dobre praktyki

1. Guardy utrzymuj cienkie; ciężką logikę przenieś do dedykowanych serwisów autoryzacji.
2. Używaj dekoratorów metadanych dla deklaratywnych, audytowalnych reguł dostępu.
3. Rozróżniaj błędy authentication (`401`) od authorization (`403`).
4. Testuj guardy zarówno scenariuszami pozytywnymi, jak i negatywnymi.

</details>

<details>
<summary>26. Czym jest @SetMetadata() i jak działa z Guardami przez Reflector?</summary>

#### NestJS

`@SetMetadata()` to helper dekorator, który pozwala dołączać własne metadane do
klasy lub metody. Guardy mogą potem odczytać te metadane przez `Reflector` i
egzekwować autoryzację albo inne reguły zależne od endpointu.

#### Główna idea

1. `@SetMetadata(key, value)` zapisuje metadane na trasie/klasie.
2. Guard używa `Reflector`, by odczytać metadane w runtime.
3. Guard decyduje, czy request ma być przepuszczony.

#### Dlaczego ten wzorzec jest ważny

1. **Deklaratywne reguły dostępu**
   Uprawnienia są widoczne bezpośrednio przy endpointach.

2. **Separation of concerns**
   Controller deklaruje intencję, Guard odpowiada za egzekucję.

3. **Reużywalność**
   Jeden Guard może obsłużyć wiele tras z różnymi wartościami metadanych.

#### Przykład: metadane ról

Dekorator:

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Użycie na endpointzie:

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

Guard odczytujący metadane:

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(), // metadane metody
      context.getClass(),   // metadane controllera
    ]);

    if (!requiredRoles) return true;

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];
    return requiredRoles.some(role => userRoles.includes(role));
  }
}
```

#### Metody `Reflector`, których używa się najczęściej

1. `get(key, target)` -> odczyt metadanych z konkretnego targetu.
2. `getAllAndOverride(key, [handler, class])` -> metadane metody nadpisują klasę.
3. `getAllAndMerge(key, [handler, class])` -> łączy wartości z obu poziomów.

#### Praktyczny wniosek

`@SetMetadata()` + `Reflector` to standardowy mechanizm NestJS do budowy
czystych, skalowalnych i metadata-driven reguł autoryzacji i zachowań tras.

</details>

<details>
<summary>27. Jak zaimplementować uwierzytelnianie JWT przez Guard?</summary>

#### NestJS

W NestJS standardowe podejście to Passport + strategia JWT + guard, który tę
strategię aktywuje na chronionych trasach.

#### Główna architektura

1. **AuthService**
   Podpisuje i weryfikuje tokeny JWT.

2. **JWT strategy/guard**
   Pobiera bearer token, waliduje go i ustawia `request.user`.

3. **Chronione trasy**
   Używają `@UseGuards(...)`, aby wymagać uwierzytelnienia.

Można to zrobić przez Passport (`@nestjs/passport`) lub własny guard.

#### Minimalny własny JWT Guard (bez Passport)

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
      req.user = payload; // tożsamość dla dalszych warstw
      return true;
    } catch {
      throw new UnauthorizedException('Invalid or expired token');
    }
  }
}
```

#### Ochrona tras

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

#### Konfiguracja `JwtModule`

```ts
JwtModule.register({
  secret: process.env.JWT_ACCESS_SECRET,
  signOptions: { expiresIn: '15m' },
});
```

#### Dobre praktyki produkcyjne

1. Osobne sekrety dla access i refresh tokenów.
2. Krótkie życie access tokenów.
3. Jawna walidacja issuer/audience/algorithm.
4. `401 Unauthorized` dla błędów tokena.
5. Połączenie z guardem autoryzacji (role/policies).
6. Strategia unieważniania tokenów tam, gdzie to wymagane.

#### Praktyczna uwaga

W większych systemach `AuthGuard('jwt')` + `JwtStrategy` z Passport bywa
czytelniejsze i bardziej reużywalne, ale zasada pozostaje ta sama:
extract -> verify -> attach user -> allow/deny.

</details>

<details>
<summary>28. Jak zaimplementować RBAC i ABAC w NestJS i kiedy które podejście jest lepsze?</summary>

#### NestJS

RBAC i ABAC to dwa modele autoryzacji, które w NestJS najczęściej realizuje się
przez Guardy + metadane + serwisy polityk.

#### RBAC vs ABAC

1. **RBAC (Role-Based Access Control)**
   Dostęp przyznawany na podstawie roli użytkownika (`admin`, `editor`, `viewer`).

2. **ABAC (Attribute-Based Access Control)**
   Dostęp przyznawany przez ocenę atrybutów (użytkownik, zasób, akcja, kontekst):
   ownership, dział, region, status, okno czasowe itd.

#### Kiedy które podejście jest lepsze

1. Wybierz **RBAC**, gdy:
   1. model uprawnień jest prosty i stabilny,
   2. hierarchia ról jest czytelna,
   3. priorytetem jest szybka implementacja i prosty audyt.

2. Wybierz **ABAC**, gdy:
   1. reguły zależą od danych zasobu i kontekstu,
   2. potrzebujesz drobnoziarnistych, dynamicznych decyzji,
   3. złożoność multi-tenant/enterprise jest wysoka.

3. W praktyce często najlepszy jest **hybrydowy RBAC + ABAC**:
   RBAC dla dostępu „grubego”, ABAC dla operacji wrażliwych.

#### Wzorzec RBAC w NestJS

1. Dekorator `@Roles(...)` przez `SetMetadata`.
2. `RolesGuard` czyta metadane przez `Reflector`.
3. Guard porównuje wymagane role z `request.user.roles`.

```ts
export const Roles = (...roles: string[]) => SetMetadata('roles', roles);
```

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Wzorzec ABAC w NestJS

1. Zdefiniuj serwis polityk (`can(user, action, resource)`).
2. W guardzie załaduj docelowy zasób (lub jego atrybuty).
3. Oceń politykę i dopuść/odrzuć.

```ts
@Injectable()
export class PoliciesGuard implements CanActivate {
  constructor(private readonly policy: PolicyService) {}

  async canActivate(ctx: ExecutionContext): Promise<boolean> {
    const req = ctx.switchToHttp().getRequest();
    const user = req.user;
    const order = await req.orderLoader.load(req.params.id); // przykład
    return this.policy.can(user, 'update', order);
  }
}
```

#### Dobre praktyki projektowe

1. Guard utrzymuj cienki; logikę reguł deleguj do dedykowanego policy service.
2. Unikaj hardcodowania reguł w controllerach.
3. Cache'uj lookups polityk tam, gdzie to bezpieczne.
4. Dla odmowy autoryzacji zwracaj `403 Forbidden` (nie `401`).
5. Loguj kontekst decyzji w domenach wymagających audytu.

#### Praktyczna rekomendacja

Zacznij od RBAC dla szybkości, a ABAC dołóż tam, gdzie pojawiają się złożone
reguły ownership, wrażliwości danych i granic tenantów.

</details>

<details>
<summary>29. Jak zaimplementować rotację refresh tokenów i dlaczego to ważne?</summary>

#### NestJS

Rotacja refresh tokenów oznacza wydawanie **nowego refresh tokena przy każdym
odświeżeniu** i unieważnianie poprzedniego. To ogranicza ryzyko replay, gdy
refresh token zostanie przejęty.

#### Dlaczego to ważne

1. Ogranicza skutki wycieku refresh tokena.
2. Umożliwia wykrywanie reuse attack (ponowne użycie starego tokena).
3. Pozwala utrzymywać długie sesje bez długiego życia access tokenów.
4. Daje lepszą kontrolę sesji między urządzeniami.

#### Zalecany model tokenów

1. **Access token**: krótki TTL (np. 5-15 min), stateless JWT.
2. **Refresh token**: dłuższy TTL (dni/tygodnie), rotowany przy każdym użyciu.
3. W DB przechowuj tylko **hash refresh tokena** (lub metadane rodziny tokenów).
4. Śledź rodzinę tokenów/sesję (`sessionId`, `jti`, `rotatedFrom`, `revokedAt`).

#### Przepływ rotacji

1. Login -> wydaj access + refresh (RT1), zapisz hash RT1 + metadane.
2. Klient wywołuje `/auth/refresh` z RT1.
3. Serwer weryfikuje podpis/expiry i porównuje hash z aktywnym rekordem.
4. Jeśli poprawny:
   1. unieważnij RT1,
   2. wydaj AT2 + RT2,
   3. zapisz hash RT2 jako aktywny dla sesji.
5. Jeśli później stary RT1 zostanie użyty:
   1. oznacz to jako podejrzany reuse,
   2. unieważnij całą sesję/rodzinę tokenów,
   3. wymuś ponowne logowanie.

#### Minimalny szkic na poziomie serwisu

```ts
async rotateRefreshToken(userId: string, presentedRt: string, sessionId: string) {
  const session = await this.sessionsRepo.findById(sessionId);
  if (!session || session.revokedAt) throw new UnauthorizedException();

  const matches = await this.hash.compare(presentedRt, session.refreshTokenHash);
  if (!matches) {
    await this.sessionsRepo.revokeFamily(session.familyId); // reakcja na reuse
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

#### Dobre praktyki

1. Haszuj refresh tokeny „at rest”.
2. Powiąż refresh token z metadanymi sesji/urządzenia.
3. Rotuj przy każdym refresh bez wyjątków.
4. Unieważniaj rodzinę tokenów po wykryciu reuse.
5. Loguj zdarzenia rotacji/reuse do monitoringu incydentów.

</details>

<details>
<summary>30. Czym jest Pipe w NestJS i kiedy należy go używać?</summary>

#### NestJS

Pipe w NestJS to klasa implementująca `PipeTransform`, uruchamiana przed
route handlerem w celu **transformacji** i/lub **walidacji** danych wejściowych.

#### Co robią Pipes

1. **Transformacja**
   Konwersja surowych wartości transportowych do oczekiwanych typów
   (np. `string -> number`, normalizacja tekstu).

2. **Walidacja**
   Egzekwowanie reguł DTO/schematu i odrzucanie niepoprawnych danych wcześnie.

3. **Fail-fast**
   Rzucenie wyjątku (najczęściej `BadRequestException`) zanim uruchomi się logika biznesowa.

#### Gdzie Pipes są w lifecycle

1. Middleware
2. Guards
3. Interceptors (pre)
4. **Pipes**
5. Handler
6. Interceptors (post)
7. Exception filters

#### Wbudowane Pipes (przykłady)

1. `ValidationPipe`
2. `ParseIntPipe`
3. `ParseBoolPipe`
4. `ParseUUIDPipe`
5. `DefaultValuePipe`
6. `ParseArrayPipe`

#### Przykłady użycia

Poziom parametru:

```ts
@Get(':id')
findOne(@Param('id', ParseIntPipe) id: number) {
  return this.usersService.findOne(id);
}
```

Globalna walidacja:

```ts
app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
    forbidNonWhitelisted: true,
    transform: true,
  }),
);
```

#### Przykład custom Pipe

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

#### Kiedy używać Pipes

1. Walidacja DTO i payloadów query/param.
2. Parsowanie prymitywów route/query do typów.
3. Centralizacja reguł normalizacji wejścia.
4. Utrzymanie controllerów/services bez powtarzalnego kodu walidacji/parsingu.

#### Reguła praktyczna

Pipes służą do **poprawności wejścia**, Guardy do **kontroli dostępu**,
Interceptors do **opakowania wykonania**, a Middleware do
**niskopoziomowego preprocessingu requestu**.

</details>

<details>
<summary>31. Czym jest DTO?</summary>

#### NestJS

DTO (*Data Transfer Object*) to kształt obiektu używanego do przenoszenia danych
między granicami aplikacji — najczęściej między klientem a warstwą API.

W NestJS DTO zazwyczaj implementuje się jako **klasy**, aby wspierać walidację
runtime i transformację przez `class-validator` oraz `class-transformer`.

#### Dlaczego DTO są ważne

1. **Jawne kontrakty API**
   Precyzyjnie definiują, jakie pola wejścia/wyjścia są dozwolone.

2. **Granica walidacji**
   Odrzucają błędne lub niebezpieczne payloady przed logiką biznesową.

3. **Decoupling**
   Zapobiegają bezpośredniemu wystawianiu encji domenowych/modeli ORM klientom.

4. **Utrzymywalność**
   Jasne schematy request/response ułatwiają refaktoryzację i dokumentację.

#### Typowe rodzaje DTO w NestJS

1. **Request DTOs**
   `CreateUserDto`, `UpdateUserDto`, DTO filtrów/query.

2. **Response/View DTOs**
   Kontrolowany kształt wyjścia (ukrycie pól wewnętrznych, np. haseł, tokenów).

3. **Command-style DTOs**
   Wejścia dla konkretnych use-case (często w modułach CQRS).

#### Przykład request DTO

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

Użycie w controllerze:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Praktyczne zasady

1. Nie używaj surowych payloadów `any` w controllerach.
2. DTO utrzymuj jako kontrakty transportowe (nie pełne encje domenowe).
3. Oddziel DTO wejściowe od wyjściowych.
4. Łącz DTO z globalnym `ValidationPipe` dla spójnej egzekucji.

</details>

<details>
<summary>32. Jaka jest różnica między interface i class do typowania DTO i dlaczego class jest preferowana w NestJS?</summary>

#### NestJS

W TypeScript zarówno `interface`, jak i `class` mogą opisywać kształt danych,
ale w NestJS DTO preferuje się jako **klasy**, ponieważ Nest potrzebuje metadanych
w runtime do walidacji, transformacji i dokumentacji.

#### Kluczowa różnica

1. **interface**
   Istnieje tylko w compile-time i znika po transpile do JavaScript.
   Nie zostawia metadanych w runtime.

2. **class**
   Istnieje w runtime jako realny konstruktor/obiekt.
   Umożliwia dekoratory (`@IsEmail`, `@ApiProperty` itd.) i refleksję.

#### Dlaczego NestJS preferuje class dla DTO

1. `ValidationPipe` korzysta z metadanych dekoratorów do walidacji.
2. `class-transformer` zamienia payload plain object na instancję klasy.
3. Swagger (`@nestjs/swagger`) generuje schematy z dekorowanych klas.
4. Mapped types (`PartialType`, `PickType`, `OmitType`) działają na klasach.

#### Przykład

`interface` (ograniczone możliwości):

```ts
interface CreateUserDto {
  email: string;
  password: string;
}
```

`class` (zalecane):

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

#### Praktyczna konsekwencja

Jeśli użyjesz interface dla DTO wejściowego:

1. Tracisz automatyczną walidację deklaratywną.
2. Tracisz spójną transformację typów.
3. Tracisz pełną integrację ze Swagger i mapped types.

#### Reguła praktyczna

1. Używaj **class** dla DTO transportowych (request/response) w NestJS.
2. Używaj **interface** dla kontraktów wewnętrznych (porty, repozytoria,
   serwisy), gdzie nie potrzebujesz metadanych runtime.

</details>

<details>
<summary>33. Czym są mapped types w NestJS? (PartialType, OmitType, PickType, IntersectionType)</summary>

#### NestJS

Mapped types w NestJS to narzędzia, które generują nowe klasy DTO na bazie
istniejących, zmniejszając duplikację przy zachowaniu metadanych walidacji i
Swagger.

Najczęściej importuje się je z:

1. `@nestjs/mapped-types` (użycie framework-agnostic)
2. `@nestjs/swagger` (gdy używasz Swagger i dekoratorów schematów)

#### Dlaczego mapped types są przydatne

1. Ograniczają powtarzalne definicje DTO.
2. Utrzymują spójność między Create/Update DTO.
3. Zachowują metadane dekoratorów dla walidacji i dokumentacji.
4. Ułatwiają bezpieczną ewolucję kontraktów API.

#### Główne mapped types

1. **`PartialType(BaseDto)`**
   Ustawia wszystkie właściwości jako opcjonalne.
   Typowe użycie: `UpdateDto` na bazie `CreateDto`.

2. **`PickType(BaseDto, ['a', 'b'])`**
   Zostawia tylko wybrane pola.
   Typowe użycie: „odchudzone” wejście dla konkretnego endpointu.

3. **`OmitType(BaseDto, ['x'])`**
   Wyklucza wskazane pola.
   Typowe użycie: ukrycie niedozwolonych pól wejściowych (np. `role`, `id`).

4. **`IntersectionType(A, B)`**
   Łączy pola z dwóch klas DTO.
   Typowe użycie: kompozycja DTO filtrów/paginacji/query.

#### Przykład

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

#### Praktyczne uwagi

1. Mapped types działają na metadanych klas; DTO bazowe musi być klasą.
2. Utrzymuj dziedziczenie DTO czytelne; unikaj głębokich, zagmatwanych łańcuchów.
3. Po złożonych intersectionach sprawdzaj wygenerowany schemat OpenAPI.

#### Reguła praktyczna

Używaj mapped types do reużycia kontraktów, szczególnie `Create` -> `Update`,
zachowując prostą i jawną hierarchię DTO.

</details>

<details>
<summary>34. Jak zaimplementować walidację przy użyciu class-validator i pipes?</summary>

#### NestJS

W NestJS standardowe podejście to:
1. definiować reguły w klasach DTO przez `class-validator`,
2. włączyć `ValidationPipe` (globalnie lub per-route), aby egzekwować je w runtime.

#### Krok 1: zdefiniuj DTO z dekoratorami walidacji

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

#### Krok 2: włącz `ValidationPipe`

Globalna konfiguracja (zalecana):

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

#### Co robią te opcje

1. `whitelist: true`
   Usuwa właściwości, których nie ma w DTO.

2. `forbidNonWhitelisted: true`
   Rzuca błąd, gdy payload zawiera nieznane pola.

3. `transform: true`
   Konwertuje payload do instancji DTO i uruchamia transformację typów.

4. `enableImplicitConversion: true`
   Pozwala na bezpieczną konwersję prymitywów wg typów DTO.

#### Krok 3: użyj DTO w controllerze

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Walidacja per-route (gdy potrzeba)

```ts
@Post('strict')
@UsePipes(new ValidationPipe({ whitelist: true, forbidNonWhitelisted: true }))
createStrict(@Body() dto: CreateUserDto) {}
```

#### Typowa odpowiedź błędu walidacji

1. HTTP `400 Bad Request`
2. Tablica komunikatów o niespełnionych constraintach
3. Diagnostyka na poziomie pól dla klientów API

#### Dobre praktyki

1. Trzymaj DTO per endpoint/use-case.
2. Rozdziel Create/Update DTO (często przez `PartialType`).
3. Nie polegaj wyłącznie na walidacji w service, jeśli controller przyjmuje dane z zewnątrz.
4. Dostosuj `exceptionFactory` w `ValidationPipe`, by utrzymać spójny kształt błędu API.

</details>

<details>
<summary>35. Jak zaimplementować globalny Exception Filter i własne błędy HTTP?</summary>

#### NestJS

W NestJS globalny Exception Filter centralizuje mapowanie błędów na odpowiedzi,
dzięki czemu wszystkie nieobsłużone wyjątki zwracają spójny format API.

Własne błędy HTTP zwykle tworzy się przez rozszerzenie `HttpException` albo
użycie wbudowanych wyjątków (`BadRequestException`, `NotFoundException` itd.).

#### 1) Utwórz globalny exception filter

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

#### 2) Zarejestruj filter globalnie

W `main.ts`:

```ts
app.useGlobalFilters(new GlobalExceptionFilter());
```

#### 3) Utwórz własny wyjątek HTTP

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

Użycie:

```ts
if (!canCloseOrder) {
  throw new BusinessRuleViolationException('Order cannot be closed in current state');
}
```

#### Dlaczego to podejście jest dobre

1. Spójny format odpowiedzi błędów w całym API.
2. Czystsze controllery/services (mniej powtarzalnego try/catch pod formatowanie).
3. Jedno miejsce na observability hooki (logging, correlation IDs, error codes).
4. Łatwe mapowanie błędów domeny/infrastruktury na sensowną semantykę HTTP.

#### Dobre praktyki

1. Nie ujawniaj wewnętrznych stack trace w odpowiedziach produkcyjnych.
2. Dodawaj machine-readable error codes dla klientów.
3. Zachowuj stack trace w logach (niekoniecznie w body HTTP).
4. Błędy biznesowe mapuj do 4xx, nieoczekiwane awarie do 5xx.

</details>

<details>
<summary>36. Jak poprawnie obsługiwać błędy i zwracać spójną strukturę odpowiedzi?</summary>

#### NestJS

Poprawna obsługa błędów w NestJS wymaga rozdzielenia:
1. miejsca, gdzie błędy powstają (domain/application/infrastructure),
2. miejsca, gdzie są mapowane na HTTP (filters),
3. sposobu standaryzacji odpowiedzi (globalny kontrakt).

#### Zalecana strategia

1. **Rzucaj znaczące wyjątki w logice biznesowej**
   Używaj wyjątków domenowych lub odpowiednich klas `HttpException`.

2. **Centralizuj formatowanie odpowiedzi HTTP**
   Użyj globalnego exception filtera, aby egzekwować jeden schemat błędu.

3. **Ustandaryzuj także odpowiedzi sukcesu**
   Opcjonalnie użyj interceptora dla jednolitej koperty sukcesu.

4. **Zachowaj obserwowalność**
   Loguj kontekst błędu (requestId, path, userId, stack) w jednym miejscu.

#### Przykład spójnego formatu błędu

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

#### Komponenty implementacji

1. **Global Exception Filter**
   Mapuje wszystkie wyjątki do jednego kształtu odpowiedzi.

2. **Własne klasy wyjątków**
   Zawierają domenowy/business code + message + status.

3. **Opcjonalny response interceptor**
   Owijanie udanych odpowiedzi:
   `{ success: true, data, meta }`.

#### Wytyczne kategoryzacji błędów

1. **Błędy walidacji/wejścia klienta** -> `400`.
2. **Błędy uwierzytelnienia** -> `401`.
3. **Błędy autoryzacji** -> `403`.
4. **Brak zasobu** -> `404`.
5. **Konflikty reguł biznesowych** -> `409` lub `422`.
6. **Nieoczekiwane awarie systemowe** -> `500`.

#### Czego unikać

1. Różnych ad-hoc formatów błędu w różnych controllerach.
2. Łapania wyjątków i zwracania `200` z polem `"error"`.
3. Ujawniania stack trace/SQL errors w odpowiedziach produkcyjnych.
4. Mieszania logiki formatowania transportu bezpośrednio w service.

#### Praktyczne dobre praktyki

1. Zdefiniuj katalog kodów błędów (`USER_NOT_FOUND`, `TOKEN_EXPIRED` itd.).
2. Dodawaj correlation/request ID do każdej odpowiedzi błędu i wpisu logów.
3. Upewnij się, że global filter obsługuje wyjątki znane (`HttpException`) i nieznane.
4. Pokryj ścieżki błędów testami e2e, aby utrzymać kontrakt API.

</details>

<details>
<summary>37. Jak poprawnie logować błędy, nie tracąc stack trace w produkcji?</summary>

#### NestJS

Celem jest logowanie błędów z pełnym kontekstem operacyjnym i zachowaniem
pełnego stack trace w logach, bez ujawniania wrażliwych szczegółów klientowi HTTP.

#### Kluczowa zasada

Nigdy nie pokazuj stack trace klientowi API, ale zawsze zachowuj go w logach dla
debugowania i response na incydenty.

#### Zalecane podejście w NestJS

1. Przechwytuj błędy centralnie w globalnym exception filterze.
2. Loguj przez structured logger (Pino/Winston/Nest Logger adapter).
3. Dołączaj stack, error code, metadane requestu, correlation ID i kontekst usera.
4. Zwracaj z filtra „sanitized” payload błędu.

#### Przykład (globalny filter logujący stack)

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
      stack: err?.stack, // pełny stack w logach
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

#### Co logować w produkcji

1. Timestamp, level, service name, environment.
2. Request ID / trace ID.
3. Route, method, status code, latency.
4. Kontekst auth (userId/tenantId, jeśli dostępny).
5. Pełny stack + root cause chain.

#### Częste błędy

1. Logowanie tylko `error.message` (utrata stack i cause chain).
2. String-concatenated logi zamiast structured JSON.
3. Podwójne logowanie na wielu warstwach (szum).
4. Zwracanie surowych obiektów wyjątków klientowi.

#### Praktyczne dobre praktyki

1. Używaj jednego structured loggera w całej aplikacji.
2. Dodaj correlation ID middleware/interceptor wcześnie w lifecycle requestu.
3. Redaguj sekrety/PII przed emisją logu.
4. Wysyłaj logi do scentralizowanego stacku observability (ELK, Datadog, Grafana Loki).
5. Testuj ścieżki błędów, by upewnić się, że stack jest zachowany po deployu.

</details>

<details>
<summary>38. Czym jest ConfigModule i dlaczego warto używać go zamiast process.env?</summary>

#### NestJS

`ConfigModule` (`@nestjs/config`) to system konfiguracji NestJS, który ładuje,
waliduje i udostępnia wartości środowiskowe przez DI.

Jest preferowany względem bezpośredniego używania `process.env`, bo centralizuje
logikę konfiguracji, poprawia bezpieczeństwo typów i ułatwia testy/utrzymanie.

#### Dlaczego samo `process.env` to za mało

1. Rozproszone odczyty env w całym codebase.
2. Brak centralnej walidacji wymaganych zmiennych.
3. Wartości string-only bez jawnego parsowania typów.
4. Trudniejsze mockowanie/testowanie i gorsza discoverability.

#### Co daje `ConfigModule`

1. **Scentralizowane ładowanie konfiguracji**
   Jedno miejsce dla env files i config factories.

2. **Walidacja przy starcie aplikacji**
   Fail fast, gdy kluczowe zmienne są brakujące/niepoprawne.

3. **Typowany dostęp przez `ConfigService`**
   Lepsze kontrakty i mniej niespodzianek runtime.

4. **Integracja z DI**
   Każdy provider może wstrzykiwać konfigurację.

5. **Kompozycja per środowisko**
   Łatwy podział ustawień dev/staging/prod.

#### Podstawowa konfiguracja

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

Użycie:

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

#### Walidacja (zalecana)

Użyj `validationSchema` (Joi) albo custom function:
1. Wymuś obecność kluczowych zmiennych.
2. Waliduj formaty i zakresy.
3. Przerwij bootstrap przy błędnej konfiguracji.

#### Praktyczna rekomendacja

Używaj `process.env` tylko w granicach bootstrap/config factory. W pozostałej
części aplikacji korzystaj z `ConfigService` lub typowanych providerów config,
aby utrzymać spójność, testowalność i bezpieczne zachowanie produkcyjne.

</details>

<details>
<summary>39. Jak poprawnie organizować pliki .env dla różnych środowisk (dev, staging, prod)?</summary>

#### NestJS

Poprawna organizacja `.env` powinna zapewniać przewidywalną konfigurację
per środowisko, zapobiegać wyciekom sekretów i jednocześnie zachować wygodę
lokalnego developmentu.

#### Zalecana strategia środowisk

1. Trzymaj jeden **bazowy** plik ze wspólnymi domyślnymi wartościami.
2. Dodaj pliki **per środowisko** z nadpisaniami.
3. Sekrety trzymaj poza gitem i wstrzykuj przez platformę deploy/secret store.

Typowy układ:
1. `.env` (wspólne lokalne domyślne wartości)
2. `.env.development`
3. `.env.staging`
4. `.env.production`
5. `.env.test`
6. `.env.local` (lokalne nadpisania dewelopera, gitignored)

#### Z `ConfigModule` w NestJS

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

Kolejność ładowania ma znaczenie: wcześniejsze pliki zwykle mają wyższy priorytet.

#### Co commitować, a co ignorować

1. Commituj:
   1. `.env.example` (lista wymaganych kluczy bez prawdziwych sekretów)
   2. Niewrażliwe defaults, jeśli polityka na to pozwala

2. Nie commituj:
   1. Prawdziwych sekretów/tokenów/private keys
   2. `.env.local` i nadpisań zależnych od maszyny

#### Walidacja i fail-fast

Zawsze waliduj konfigurację przy starcie (Joi albo custom validator):
1. wymagane klucze istnieją,
2. typy i zakresy są poprawne (`PORT`, timeouty, feature flags),
3. format URL i poświadczeń jest prawidłowy.

#### Dobre praktyki staging/production

1. Preferuj secret managery (AWS SSM/Secrets Manager, Vault, Doppler itd.) zamiast plików.
2. Rotuj sekrety regularnie.
3. Ściśle rozdzielaj poświadczenia staging/prod.
4. Jawnie ustawiaj `NODE_ENV` w konfiguracji deploy.
5. Nigdy nie „wypiekaj” sekretów w obrazach Docker/kodzie źródłowym.

#### Praktyczny workflow zespołowy

1. Traktuj `.env.example` jako kontrakt.
2. Dodaj onboarding script/check wykrywający brakujące zmienne.
3. Używaj typowanych wrapperów config, aby kod aplikacji nie czytał losowych kluczy env.
4. Dokumentuj ownership dla krytycznych zmiennych (DB, JWT, external APIs).

</details>

<details>
<summary>40. Jak używać Joi lub zod do walidacji konfiguracji przy starcie aplikacji?</summary>

#### NestJS

Walidacja konfiguracji podczas bootstrapu zapobiega uruchomieniu aplikacji z
brakującymi lub niepoprawnymi zmiennymi środowiskowymi. W NestJS robi się to
zwykle w `ConfigModule.forRoot(...)`.

#### Opcja A: Joi przez `validationSchema`

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

Jak to działa:
1. Env zostaje załadowany.
2. Joi waliduje kształt i ograniczenia.
3. Bootstrap kończy się błędem natychmiast przy niepoprawnej konfiguracji.

#### Opcja B: zod przez funkcję `validate`

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

Dlaczego zespoły lubią zod:
1. Silna inferencja typów TS ze schematu.
2. Komponowalne schematy dla modularnej konfiguracji.
3. Czytelne błędy parse i wsparcie transformacji.

#### Praktyczne dobre praktyki

1. Waliduj wszystkie wymagane sekrety/URL/porty przy starcie.
2. Jawnie konwertuj typy prymitywne (`PORT`, booleans, timeouty).
3. Trzymaj jeden schemat jako single source of truth.
4. Udostępniaj typowaną konfigurację przez wrappery/services, nie przez surowe `process.env`.
5. Używaj różnych plików env per środowisko, ale jednego kontraktu walidacji.

#### Joi vs zod w skrócie

1. **Joi**: dojrzałe i proste przy wbudowanym `validationSchema`.
2. **zod**: TS-first, świetna typowalność i kompozycja.

Oba podejścia są produkcyjnie poprawne; wybierz jedno i stosuj konsekwentnie.

</details>

<details>
<summary>41. Jak zaimplementować feature flags w NestJS?</summary>

#### NestJS

Feature flags w NestJS zwykle implementuje się przez dedykowany serwis,
który ocenia, czy funkcja jest aktywna w danym kontekście (środowisko,
użytkownik, tenant, procent rolloutu itd.).

#### Dlaczego feature flags są ważne

1. Bezpieczny, stopniowy rollout.
2. Szybki kill-switch dla problematycznych funkcji.
3. Eksperymenty A/B.
4. Rozdzielenie deploy od release.

#### Typowa architektura

1. **FeatureFlagService**
   Jeden punkt wejścia: `isEnabled(flag, context)`.

2. **Źródło flag**
   Env config, tabela DB lub zewnętrzny provider flag.

3. **Kontekst ewaluacji**
   User ID, tenant ID, plan, region, wersja aplikacji, metadane requestu.

4. **Miejsca użycia**
   Guards, services, controllers, interceptors, kształtowanie odpowiedzi UI.

#### Prosta implementacja in-app (config-based)

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

Użycie w serwisie:

```ts
if (this.flags.isEnabled('new_checkout', { userId, tenantId })) {
  return this.newCheckoutFlow();
}
return this.legacyCheckoutFlow();
```

#### Egzekwowanie per-route przez Guard (opcjonalnie)

1. Utwórz dekorator metadanych `@Feature('new_checkout')`.
2. Guard czyta metadane przez `Reflector`.
3. Guard wywołuje `FeatureFlagService.isEnabled(...)`.
4. Odrzuca lub zmienia zachowanie, gdy flaga jest wyłączona.

#### Praktyki produkcyjne

1. Wspieraj strategie rolloutu:
   1. global on/off,
   2. procent rolloutu,
   3. allowlist user/tenant,
   4. aktywacja w oknie czasowym.

2. Dodaj local cache z TTL dla zewnętrznych providerów flag.
3. Jawnie określ defaulty (fail-closed vs fail-open per flaga).
4. Loguj decyzje flag dla łatwiejszego debugowania.
5. Usuwaj przestarzałe flagi, aby uniknąć długoterminowej złożoności.

#### Build vs buy

1. Build in-app dla prostych potrzeb i niskiego narzutu operacyjnego.
2. Managed provider (LaunchDarkly, Unleash, ConfigCat itd.) dla zaawansowanego
   targetowania, analityki i governance.

#### Reguła praktyczna

Traktuj flagi jako krótkotrwały mechanizm releasowania, a nie stałe gałęzie
logiki biznesowej. Każda flaga powinna mieć ownera i datę sunset.

</details>

<details>
<summary>42. Jak integrować bazy danych? (TypeORM, Prisma, Drizzle, Mongoose)</summary>

#### NestJS

NestJS integruje się z różnymi technologiami persystencji przez moduły i
providery. Wybór zależy od modelu danych, wymagań wydajnościowych i stylu
pracy zespołu.

#### Najczęstsze opcje

1. **TypeORM**
   Klasyczny ORM z dekoratorami, repozytoriami i migracjami.

2. **Prisma**
   Nowoczesny ORM ze schematem deklaratywnym i generowanym, silnie typowanym
   klientem.

3. **Drizzle**
   Lekki ORM SQL-first, bardzo jawny i bliski czystemu SQL.

4. **Mongoose**
   ODM dla MongoDB oparty na modelu dokumentowym i schematach.

#### Wzorzec integracji w NestJS

1. Utwórz moduł infrastruktury DB.
2. Zarejestruj globalne połączenie (`forRoot` albo custom provider).
3. Zarejestruj encje/modele per feature (`forFeature` albo własne repo).
4. Wstrzykuj repozytoria/klientów do warstwy application.

#### Przykład TypeORM

```ts
// app.module.ts
TypeOrmModule.forRoot({
  type: 'postgres',
  host: process.env.DB_HOST,
  port: Number(process.env.DB_PORT),
  username: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME,
  autoLoadEntities: true,
  synchronize: false,
});

// users.module.ts
TypeOrmModule.forFeature([UserEntity]);
```

#### Przykład Prisma

```ts
@Injectable()
export class PrismaService extends PrismaClient implements OnModuleInit {
  async onModuleInit() {
    await this.$connect();
  }
}

@Module({
  providers: [PrismaService],
  exports: [PrismaService],
})
export class PrismaModule {}
```

#### Przykład Mongoose

```ts
MongooseModule.forRoot(process.env.MONGO_URI!);
MongooseModule.forFeature([{ name: User.name, schema: UserSchema }]);
```

#### Szybkie kryteria wyboru

1. **TypeORM**: dobre, gdy zespół używa klasycznego repository pattern.
2. **Prisma**: świetne DX, mocne typowanie i czytelne migracje.
3. **Drizzle**: precyzyjna kontrola SQL z nowoczesnym typowaniem.
4. **Mongoose**: naturalny wybór, gdy domena dobrze pasuje do dokumentów MongoDB.

#### Dobre praktyki

1. Wyłącz `synchronize: true` w produkcji.
2. Stosuj wersjonowane migracje niezależnie od stacku.
3. Enkapsuluj dostęp do DB za services/repositories domeny.
4. Skonfiguruj connection pooling, timeouty i observability zapytań.
5. Miej jasną strategię transakcji i idempotencji.

#### W skrócie

NestJS nie wiąże Cię z jednym ORM/ODM: ustaw czyste granice infrastruktury i
wybierz narzędzie adekwatne do domeny oraz wymagań operacyjnych.

</details>

<details>
<summary>43. Jaka jest różnica między TypeOrmModule.forRoot() i forFeature()?</summary>

#### NestJS

`TypeOrmModule.forRoot()` i `TypeOrmModule.forFeature()` rozwiązują różne poziomy
integracji TypeORM w NestJS.

#### `forRoot()` — konfiguracja połączenia DB na poziomie aplikacji

Używaj w module root (zwykle `AppModule`) do skonfigurowania DataSource/połączenia.

Definiuje:

1. Typ drivera DB (`postgres`, `mysql` itd.)
2. URL/poświadczenia połączenia
3. Globalne opcje TypeORM (ładowanie encji, logging, migracje, `synchronize`)

Przykład:

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

#### `forFeature()` — rejestracja repozytoriów encji w module feature

Używaj w modułach domenowych/feature, aby zarejestrować konkretne encje i
udostępnić ich repozytoria do wstrzykiwania w scope tego modułu.

Przykład:

```ts
@Module({
  imports: [TypeOrmModule.forFeature([UserEntity])],
  providers: [UsersService],
})
export class UsersModule {}
```

Wstrzyknięcie repozytorium:

```ts
constructor(
  @InjectRepository(UserEntity)
  private readonly usersRepo: Repository<UserEntity>,
) {}
```

#### Praktyczne podsumowanie różnicy

1. `forRoot()`:
   1. Tworzy/konfiguruje połączenie DB raz (lub nazwane połączenia).
   2. Dotyczy globalnej infrastruktury.

2. `forFeature()`:
   1. Wystawia repozytoria wybranych encji w scope modułu.
   2. Dotyczy warstwy feature/biznesowej.

#### Częsty błąd

Użycie `forFeature()` bez `forRoot()` (albo bez zainicjalizowanego DataSource)
prowadzi do błędów DI/runtime, bo repozytoria nie mają aktywnego połączenia.

#### Reguła praktyczna

1. Skonfiguruj połączenie raz przez `forRoot` w ścieżce bootstrapu.
2. Rejestruj encje per moduł przez `forFeature` tam, gdzie repozytoria są potrzebne.
3. W produkcji trzymaj `synchronize: false` i używaj migracji.

</details>

<details>
<summary>44. Czym jest Repository pattern w NestJS + TypeORM?</summary>

#### NestJS

Repository pattern abstrahuje dostęp do danych za dedykowanym interfejsem/
serwisem, tak aby logika biznesowa nie zależała bezpośrednio od szczegółów ORM.

W NestJS + TypeORM zwykle oznacza to opakowanie `Repository<Entity>` własnym
kontraktem repozytorium zorientowanym domenowo i jego implementacją.

#### Dlaczego warto używać Repository pattern

1. Oddziela logikę application/domain od API TypeORM.
2. Poprawia testowalność (łatwe mockowanie interfejsów repozytoriów).
3. Centralizuje logikę zapytań i mapowanie modeli.
4. Ułatwia późniejszą wymianę ORM/refaktoryzację.

#### Typowa struktura

1. **Kontrakt domenowy (port)**
   Interfejs `UsersRepository` z metodami biznesowymi.

2. **Implementacja infrastrukturalna**
   `TypeOrmUsersRepository` używające `Repository<UserEntity>`.

3. **Warstwa service/application**
   Zależy od tokenu interfejsu, nie od konkretnej klasy TypeORM.

#### Przykład

Kontrakt repozytorium:

```ts
export interface UsersRepository {
  findByEmail(email: string): Promise<UserEntity | null>;
  save(user: UserEntity): Promise<UserEntity>;
}
```

Implementacja TypeORM:

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

Binding providera:

```ts
{
  provide: 'USERS_REPOSITORY',
  useClass: TypeOrmUsersRepository,
}
```

Service zależny od abstrakcji:

```ts
constructor(
  @Inject('USERS_REPOSITORY')
  private readonly usersRepo: UsersRepository,
) {}
```

#### Co powinno być w repozytorium vs w serwisie

1. Repozytorium:
   persystencja, ładowanie/zapisy agregatów, DB-specific filtering.

2. Service/use-case:
   orkiestracja, reguły biznesowe, koordynacja granic transakcji.

#### Częsty antywzorzec

Wstrzykiwanie surowych repozytoriów TypeORM do wielu services/controllerów i
powielanie fragmentów zapytań. To zwiększa sprzężenie i niespójność.

#### Praktyczny wniosek

Używaj repozytorium TypeORM „pod spodem”, ale wystawiaj własny domenowy
interfejs repozytorium, aby utrzymać modułową i testowalną architekturę.

</details>

<details>
<summary>45. Jaka jest różnica między Repository pattern a Active Record i kiedy wybrać każde podejście?</summary>

#### NestJS

Repository pattern i Active Record to dwa różne sposoby organizacji logiki
persystencji.

#### Główna różnica

1. **Repository pattern**
   Warstwa domenowa/biznesowa korzysta z abstrakcji repozytoriów; logika
   persystencji jest wydzielona do klas repozytoriów.

2. **Active Record**
   Obiekty encji/modeli zawierają metody persystencji (`save`, `remove`,
   statyczne findery), łącząc dane z logiką zapisu.

#### Cechy Repository pattern

1. Lepsze separation of concerns.
2. Łatwiejsze testy jednostkowe przez mockowanie interfejsów.
3. Lepsza skalowalność w złożonych domenach/mikroserwisach.
4. Wspiera domenowe podejście i czyste granice architektury.

#### Cechy Active Record

1. Szybszy start dla małych/prostych aplikacji.
2. Mniej boilerplate przy prostym CRUD.
3. Z czasem może mocno sprzęgać z ORM.
4. Trudniej utrzymać izolację logiki biznesowej przy rosnącej złożoności.

#### Kiedy wybrać które

1. Wybierz **Repository pattern**, gdy:
   1. projekt jest średni/duży lub ma rosnąć,
   2. zespół potrzebuje rygoru architektury i testowalności,
   3. logika domeny jest nietrywialna,
   4. możliwa jest przyszła wymiana ORM.

2. Wybierz **Active Record**, gdy:
   1. aplikacja jest mała, CRUD-heavy i niskozłożona,
   2. priorytetem jest szybkość startu developmentu,
   3. zespół akceptuje większe sprzężenie z ORM.

#### W praktyce NestJS

1. Architektura NestJS (moduły/providery/DI) naturalnie sprzyja repository pattern.
2. Nawet przy TypeORM wiele zespołów produkcyjnych preferuje styl
   Data Mapper/repository zamiast Active Record, by utrzymać „czyste” services.

#### Szybkie porównanie

1. **Sprzężenie**
   Repository: niższe
   Active Record: wyższe

2. **Testowalność**
   Repository: wysoka
   Active Record: średnia/niższa (mocniej zależna od DB)

3. **Boilerplate**
   Repository: więcej
   Active Record: mniej

4. **Długoterminowa utrzymywalność**
   Repository: lepsze dla złożonych systemów
   Active Record: wystarczające dla prostych aplikacji

#### Praktyczna rekomendacja

Dla architektury NestJS o jakości produkcyjnej domyślnie wybieraj
Repository pattern. Active Record stosuj, gdy domena jest świadomie prosta,
a koszt długoterminowy niski.

</details>

<details>
<summary>46. Czym są migracje w TypeORM/Prisma i dlaczego synchronize: true jest niebezpieczne w produkcji?</summary>

#### NestJS

Migracje to wersjonowane, jawne skrypty zmian schematu bazy danych. Pozwalają
rozwijać schemat bezpiecznie i przewidywalnie między środowiskami.

W TypeORM/Prisma migracje są produkcyjnie bezpiecznym sposobem aplikowania zmian.

#### Czym są migracje

1. **Uporządkowana historia schematu**
   Każda migracja to śledzony krok ewolucji (up/down).

2. **Reprodukowalne wdrożenia**
   Te same zmiany schematu uruchamiasz spójnie na dev/staging/prod.

3. **Reviewowalny zestaw zmian**
   Intencja SQL/DDL jest widoczna w code review i CI.

4. **Strategia rollback**
   Możesz cofać problematyczne zmiany (z pewnymi ograniczeniami).

#### TypeORM vs Prisma

1. **TypeORM**
   Migracje jako pliki TS/JS (lub SQL), generowane/pisane i uruchamiane przez CLI.

2. **Prisma**
   Zmiany definiujesz w `schema.prisma`; pliki migracji są generowane i
   aplikowane przez Prisma Migrate.

Oba podejścia tworzą audytowalne artefakty migracyjne.

#### Dlaczego `synchronize: true` jest niebezpieczne w produkcji

1. **Niejawne, potencjalnie destrukcyjne zmiany**
   ORM może automatycznie zmienić/usunąć kolumny i indeksy bez kontrolowanego review.

2. **Niedeterministyczne zachowanie**
   Diff schematu może zależeć od driftu encji i aktualnego stanu runtime.

3. **Brak historii migracji**
   Trudniej ustalić co, kiedy i dlaczego zostało zmienione.

4. **Ryzykowne sprzężenie ze startem aplikacji**
   Bootstrap może nieoczekiwanie mutować produkcyjny schemat.

5. **Słabe bezpieczeństwo w środowisku multi-instance**
   Równoległe starty instancji mogą ścigać się o aktualizację schematu.

#### Produkcyjny workflow

1. Ustaw `synchronize: false` w produkcji.
2. Generuj migrację dla każdej zmiany schematu.
3. Reviewuj SQL migracji w PR.
4. Uruchamiaj migracje w pipeline deploymentu przed/razem z rolloutem aplikacji.
5. Monitoruj wykonanie migracji i failuj deploy przy błędach.

#### Przykłady praktyczne

Konfiguracja TypeORM:

```ts
TypeOrmModule.forRoot({
  // ...
  synchronize: false,
  migrationsRun: false,
});
```

Podejście Prisma:

1. Commituj pliki migracji.
2. Uruchamiaj `prisma migrate deploy` podczas release.

#### Reguła praktyczna

`sync: true` nadaje się do szybkiego prototypowania lokalnego. W każdym
poważnym środowisku migracje są obowiązkowe dla bezpieczeństwa, traceability i
kontrolowanej ewolucji schematu.

</details>

<details>
<summary>47. Jak zaimplementować soft delete w TypeORM?</summary>

#### NestJS

Soft delete oznacza, że rekordy są oznaczane jako usunięte zamiast fizycznego
kasowania z bazy. W TypeORM realizuje się to zwykle przez `@DeleteDateColumn`.

#### Dlaczego używać soft delete

1. Możliwość odzyskania przypadkowo usuniętych danych.
2. Zachowanie kontekstu audytu/historii.
3. Utrzymanie relacji FK i śladu biznesowego.
4. Wsparcie workflow typu „kosz/przywróć”.

#### Krok 1: dodaj kolumnę znacznika usunięcia

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

#### Krok 2: używaj metod soft delete repozytorium

```ts
// oznacza rekord jako usunięty (ustawia deletedAt)
await this.usersRepo.softDelete(userId);

// przywraca rekord soft-deleted
await this.usersRepo.restore(userId);
```

Możesz też użyć:
1. `softRemove(entity)` dla instancji encji,
2. `recover(entity)` dla przywrócenia instancyjnego.

#### Zachowanie zapytań

1. Domyślnie TypeORM wyklucza soft-deleted w standardowych `find*`.
2. Aby dołączyć usunięte rekordy, użyj `withDeleted: true`.

```ts
const allRows = await this.usersRepo.find({ withDeleted: true });
```

Tylko usunięte:

```ts
const deletedOnly = await this.usersRepo.find({
  withDeleted: true,
  where: { deletedAt: Not(IsNull()) },
});
```

#### Przykład na poziomie serwisu

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

#### Uwagi produkcyjne

1. Dodaj indeksy dla często filtrowanych pól (`deleted_at`, klucze tenantów).
2. Zaprojektuj unique constraints z uwzględnieniem soft-delete (partial unique
   indexes tam, gdzie wspierane).
3. Zdefiniuj politykę retencji i ewentualnego hard cleanup.
4. Uwzględnij zdarzenia delete/restore w audit logach.

#### Reguła praktyczna

Stosuj soft delete dla danych użytkownika/biznesowych wymagających odzyskiwania
lub audytu. Hard delete tylko tam, gdzie wymuszają to reguły domeny albo compliance.

</details>

<details>
<summary>48. Jak zaimplementować transakcje w TypeORM z NestJS?</summary>

#### NestJS

Transakcje gwarantują, że grupa operacji na bazie danych wykona się atomowo:
albo wszystko zostanie zatwierdzone, albo wszystko się wycofa.

#### Kiedy transakcje są wymagane

1. Tworzenie/aktualizacja wielu powiązanych tabel w jednym use-case.
2. Operacje na saldzie/płatnościach/inwentarzu.
3. Przypadki, gdzie częściowy sukces zepsułby stan biznesowy.

#### Główne podejścia w TypeORM

1. **`DataSource.transaction(...)`** (zalecane domyślnie)
2. **`QueryRunner`** (ręczna kontrola dla bardziej złożonych flow)

#### Podejście 1: `DataSource.transaction` (czyste i bezpieczne)

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

Ważne: wewnątrz callbacka transakcji używaj `manager`, nie globalnie
wstrzykniętych repozytoriów.

#### Podejście 2: `QueryRunner` (pełniejsza kontrola)

```ts
const qr = dataSource.createQueryRunner();
await qr.connect();
await qr.startTransaction();
try {
  // używaj qr.manager dla wszystkich zapytań
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

#### Dobre praktyki

1. Utrzymuj krótki i skupiony zakres transakcji.
2. Unikaj zewnętrznych wywołań HTTP wewnątrz transakcji DB.
3. Ustawiaj właściwy isolation level przy flow wrażliwych na współbieżność.
4. Obsługuj retry/deadlock strategy dla operacji wysokiej konkurencji.
5. Emituj domain events po commit (albo stosuj outbox pattern).

#### Częste błędy

1. Mieszanie repozytoriów transakcyjnych i nietransakcyjnych w jednym flow.
2. Długie transakcje powodujące lock contention.
3. „Połykanie” wyjątków i commit niespójnego stanu.

#### Reguła praktyczna

Obejmij jeden use-case biznesowy jedną granicą transakcji tam, gdzie spójność
wielu zapisów jest nienegocjowalna.

</details>

<details>
<summary>49. Czym jest problem N+1 i jak go rozwiązać w NestJS?</summary>

#### NestJS

Problem N+1 pojawia się, gdy aplikacja wykonuje:
1. jedno zapytanie pobierające listę rekordów nadrzędnych,
2. a potem jedno dodatkowe zapytanie dla każdego rekordu, aby pobrać relacje.

To daje `1 + N` zapytań, wysoką latencję i niepotrzebne obciążenie DB.

#### Przykład N+1

1. Pobierasz użytkowników (`N` rekordów).
2. Dla każdego użytkownika osobno pobierasz posty.
3. Łącznie zapytań: `1 + N`.

Przy 100 użytkownikach to 101 round-tripów do bazy.

#### Gdzie występuje w NestJS

1. Lazy relacje TypeORM wywoływane w pętli.
2. GraphQL resolvers rozwiązujące zagnieżdżone pola per encja.
3. Serwisy wykonujące powtarzalne wywołania repozytorium „na element”.

#### Jak rozwiązywać

1. **Eager load przez joiny**
   Użyj query buildera, aby pobrać relacje jednym (lub kontrolowaną liczbą) zapytań.

2. **Batch loading**
   Użyj DataLoader-style batching (szczególnie w GraphQL).

3. **Zapytania IN**
   Pobierz relacje dla wszystkich parent IDs naraz i zmapuj w pamięci.

4. **Optymalizacja projekcji**
   Wybieraj tylko potrzebne kolumny, żeby zmniejszyć payload.

#### Przykład join w TypeORM

```ts
const users = await this.usersRepo
  .createQueryBuilder('u')
  .leftJoinAndSelect('u.posts', 'p')
  .getMany();
```

#### Przykład batch loading

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

#### Sygnały wykrywania

1. Gwałtowny wzrost liczby zapytań wraz z większym zbiorem wyników.
2. Latencja endpointu rośnie liniowo z liczbą rekordów nadrzędnych.
3. Powtarzające się podobne SQL-e w logach/monitoringu.

#### Praktyka zapobiegania

1. Włącz logowanie zapytań SQL w testach wydajnościowych non-prod.
2. Dodaj asercje liczby zapytań dla krytycznych endpointów.
3. Projektuj metody repozytoriów pod odczyt agregatów.
4. Przeglądaj GraphQL resolvers pod kątem per-field DB calls.

#### Reguła praktyczna

Jeśli endpoint ładuje kolekcje z relacjami, zaprojektuj od razu batching/joiny.
Nie opieraj ścieżek produkcyjnych na pętlach z lazy fetch per element.

</details>

<details>
<summary>50. Czym jest connection pooling i jak poprawnie go skonfigurować dla bazy danych?</summary>

#### NestJS

Connection pooling to zarządzany zestaw wielokrotnego użytku połączeń DB
współdzielonych między requestami. Zamiast otwierać nowe połączenie dla każdego
zapytania, aplikacja „pożycza” połączenie z puli i oddaje je po użyciu.

#### Dlaczego pooling jest ważny

1. Ogranicza narzut ustanawiania połączeń.
2. Poprawia throughput i latencję pod obciążeniem.
3. Chroni bazę przed skokami liczby połączeń.
4. Stabilizuje zachowanie przy współbieżnych requestach.

#### Kluczowe parametry puli

1. **max pool size**
   Maksymalna liczba równoczesnych połączeń DB z jednej instancji aplikacji.

2. **min pool size** (zależne od drivera)
   Minimalna liczba utrzymywanych połączeń bezczynnych.

3. **acquire timeout**
   Jak długo czekać na wolne połączenie.

4. **idle timeout**
   Jak długo nieużywane połączenie pozostaje otwarte.

5. **max lifetime**
   Maksymalny wiek połączenia przed recyklingiem.

#### Strategia doboru rozmiaru

1. Zacznij od limitu DB i liczby replik:
   `pool_max_per_instance * replica_count < db_connection_limit - safety_margin`.

2. Zostaw zapas dla:
   1. migracji i narzędzi administracyjnych,
   2. workerów background,
   3. nieoczekiwanych pików ruchu.

3. Dostrajaj po load testach wg:
   1. czasu oczekiwania na połączenie,
   2. CPU DB,
   3. lock contention,
   4. p95/p99 latency.

#### Przykład TypeORM/NestJS (Postgres)

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  synchronize: false,
  extra: {
    max: 20,
    connectionTimeoutMillis: 5000,
    idleTimeoutMillis: 30000,
  },
});
```

#### Dobre praktyki operacyjne

1. Używaj jednego globalnego DataSource na proces (unikaj wielu pul).
2. Ustawiaj query timeouts i statement timeouts.
3. Monitoruj metryki puli: active, idle, waiting.
4. Dostrajaj na podstawie realnego workloadu, nie domyślnych wartości.
5. W serverless/highly elastic rozważ PgBouncer lub managed pooling dostawcy.

#### Częste błędy

1. Zbyt duża pula -> thrashing DB i większa kontencja locków.
2. Zbyt mała pula -> kolejki requestów i timeouty.
3. Ignorowanie mnożnika skalowania poziomego między replikami.
4. Ręczne otwieranie nowych klientów DB w handlerach requestów.

#### Reguła praktyczna

Rozmiar puli połączeń to decyzja systemowa, nie tylko ustawienie ORM.
Dobieraj go pod realne limity bazy i ruch produkcyjny.

</details>

<details>
<summary>51. Jak chronić się przed SQL injection w TypeORM/Prisma?</summary>

#### NestJS

Ochrona przed SQL injection w NestJS z TypeORM/Prisma opiera się na jednej
zasadzie: **nigdy nie buduj SQL przez konkatenację stringów z nieufnym inputem**.

Używaj zapytań parametryzowanych i API ORM, które bezpiecznie bindowa wartości.

#### Bezpieczne domyślne podejście

1. **TypeORM repository/query builder z parametrami**
2. **Prisma client methods z typowanymi filtrami**
3. **Walidacja i parsowanie DTO zanim dane trafią do warstwy persystencji**

#### TypeORM: bezpieczne wzorce

Repository API:

```ts
await usersRepo.findOne({ where: { email: input.email } });
```

QueryBuilder z bindowaniem parametrów:

```ts
await usersRepo
  .createQueryBuilder('u')
  .where('u.email = :email', { email: input.email })
  .andWhere('u.status = :status', { status: 'active' })
  .getMany();
```

#### Prisma: bezpieczne wzorce

```ts
await prisma.user.findMany({
  where: {
    email: input.email,
    status: 'active',
  },
});
```

Prisma domyślnie generuje zapytania parametryzowane dla standardowych metod clienta.

#### Niebezpieczne antywzorce

1. Raw SQL z interpolacją stringa:

```ts
// BAD
await dataSource.query(`SELECT * FROM users WHERE email = '${input.email}'`);
```

2. Niebezpieczne dynamiczne ORDER BY / nazwy kolumn od użytkownika.
3. Przekazywanie niewalidowanych fragmentów do raw query functions.

#### Gdy raw SQL jest nieuniknione

1. Używaj placeholderów parametrów:

```ts
await dataSource.query('SELECT * FROM users WHERE email = $1', [input.email]);
```

2. Whitelistuj dynamiczne identyfikatory (kolumny/pola sortowania):
   mapuj input -> znany bezpieczny token SQL.

#### Defense in depth

1. Waliduj i sanityzuj input przez DTO + `ValidationPipe`.
2. Stosuj least-privilege dla kont DB.
3. Ogranicz niebezpieczne uprawnienia DB (drop/alter tam, gdzie niepotrzebne).
4. Loguj podejrzane wzorce zapytań i nieudane próby auth.
5. Dodawaj testy security pod payloady injection na krytycznych endpointach.

#### Reguła praktyczna

W 95% przypadków trzymaj się API ORM. W pozostałych przypadkach raw SQL zawsze
parametryzuj i whitelistuj każdy dynamiczny fragment struktury SQL.

</details>

<details>
<summary>52. Jak poprawnie zorganizować paginację w API REST? (offset vs cursor-based)</summary>

#### NestJS

Poprawny design paginacji w REST API powinien być stabilny, wydajny i
przewidywalny dla klientów. Dwa główne modele to paginacja offsetowa i cursorowa.

#### Offset vs cursor: kluczowa różnica

1. **Offset pagination**
   Używa `limit` + `offset` (albo page/pageSize).
   Przykład: `GET /users?limit=20&offset=40`.

2. **Cursor pagination**
   Używa wskaźnika na ostatnio widziany rekord w posortowanym strumieniu.
   Przykład: `GET /users?limit=20&cursor=eyJpZCI6MTIzfQ==`.

#### Kiedy używać offset pagination

1. Małe/średnie zbiory danych.
2. Potrzeba losowych skoków po stronach (`page=7`).
3. Proste dashboardy admin/backoffice.

Trade-offy:

1. Wolniejsze dla dużych offsetów.
2. Mniej stabilne strony przy równoczesnych insertach/delete.

#### Kiedy używać cursor pagination

1. Duże i często zmieniające się zbiory.
2. Infinite scroll / feedy mobilne.
3. Endpointy wrażliwe na wydajność.

Korzyści:

1. Lepsza wydajność DB przy skali.
2. Stabilniejsze sortowanie przy równoczesnych zapisach.

Trade-off:

1. Brak naturalnych „skoków” do dowolnej strony.

#### Kluczowe zasady projektowe (oba modele)

1. Zawsze definiuj deterministyczne sortowanie:
   np. `ORDER BY created_at DESC, id DESC`.

2. Egzekwuj max page size po stronie serwera.

3. Zwracaj metadane paginacji:
   `hasNext`, `nextCursor` (cursor) albo `total` (offset, gdy potrzebne).

4. Waliduj parametry paginacji przez DTO + pipes.

#### Przykładowe odpowiedzi

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

#### Uwagi implementacyjne w NestJS

1. Twórz dedykowane DTO: `OffsetPaginationDto`, `CursorPaginationDto`.
2. Trzymaj logikę paginacji w warstwie repository/query, nie w controllerze.
3. Koduj cursor jako opaque token (base64/json + opcjonalny podpis).
4. Dopasuj indeksy DB do kluczy sort/filter (`created_at`, `id`, tenant fields).

#### Praktyczna rekomendacja

1. Używaj **offset** dla prostych endpointów wewnętrznych.
2. Używaj **cursor** dla publicznych/high-volume feedów.
3. Gdy masz wątpliwości, wybierz cursor dla write-heavy timeline'ów, by
   uniknąć przyszłych problemów wydajności i spójności.

</details>

<details>
<summary>53. Jak wersjonować API w NestJS? (URI, Header, Media type versioning)</summary>

#### NestJS

Wersjonowanie API w NestJS pozwala rozwijać endpointy bez psucia istniejących
klientów. Nest wspiera strategie URI, custom header i media type versioning.

#### Strategie wersjonowania

1. **URI versioning**
   Wersja w ścieżce: `/v1/users`, `/v2/users`.

2. **Header versioning**
   Wersja w custom headerze (np. `X-API-Version: 2`).

3. **Media type versioning**
   Wersja w nagłówku `Accept`
   (np. `application/vnd.myapp.v2+json`).

#### Włączenie wersjonowania w NestJS

```ts
import { NestFactory, VersioningType } from '@nestjs/core';

const app = await NestFactory.create(AppModule);

app.enableVersioning({
  type: VersioningType.URI, // albo HEADER / MEDIA_TYPE
  defaultVersion: '1',
});
```

#### Deklarowanie wersji na controllerach/trasach

Poziom controllera:

```ts
@Controller({ path: 'users', version: '1' })
export class UsersV1Controller {}
```

Poziom metody:

```ts
@Get()
@Version('2')
findAllV2() {}
```

Wiele wersji na jednym handlerze:

```ts
@Version(['1', '2'])
```

#### Jak wybrać strategię

1. **URI versioning** (najczęstsze)
   1. Łatwe debugowanie i cache.
   2. Czytelne w logach i dokumentacji.
   3. Dobry domyślny wybór dla publicznych REST API.

2. **Header versioning**
   1. Czystsze URL-e.
   2. Dobre w kontrolowanych klientach enterprise.
   3. Trudniejsze do ręcznych testów i domyślnego cache.

3. **Media type versioning**
   1. Bardziej „HTTP standards-oriented” styl content negotiation.
   2. Najbardziej złożone dla klientów/toolingu.

#### Dobre praktyki

1. Wprowadź wersjonowanie zanim pojawi się pierwszy breaking change.
2. Utrzymuj okno kompatybilności wstecz i politykę deprecacji.
3. Wersjonuj tylko wtedy, gdy zmiany kontraktu są breaking.
4. Dokumentuj timeline sunset dla starych wersji.
5. Trzymaj współdzieloną logikę biznesową w service; wersjonuj głównie warstwę transportu.

#### Reguła praktyczna

Dla większości zespołów najlepszy start to **URI versioning** — jest jawny i
operacyjnie prosty. Header/media type wybieraj przy konkretnych wymaganiach
platformowych.

</details>

<details>
<summary>54. Jak zaimplementować dokumentację Swagger w NestJS przez @nestjs/swagger?</summary>

#### NestJS

Swagger w NestJS wdraża się przez `@nestjs/swagger`, aby automatycznie generować
dokumentację OpenAPI z controllerów, DTO i dekoratorów.

#### Krok 1: zainstaluj pakiety

1. `@nestjs/swagger`
2. `swagger-ui-express`

#### Krok 2: skonfiguruj Swagger w `main.ts`

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

Dokumentacja będzie pod `/docs`.

#### Krok 3: adnotuj controllery i DTO

Adnotacje controllera:

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

Adnotacje DTO:

```ts
import { ApiProperty } from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({ example: 'john@example.com' })
  email: string;

  @ApiProperty({ minLength: 8 })
  password: string;
}
```

#### Krok 4: utrzymuj zgodność schematów

1. Używaj klasowych DTO (nie interfejsów) dla metadanych runtime.
2. Łącz ze `ValidationPipe`, aby docs odpowiadały realnym ograniczeniom.
3. Dokumentuj auth, paginację i modele błędów explicite.

#### Zaawansowane praktyki produkcyjne

1. Generuj docs per wersję API, jeśli wersjonowanie jest aktywne.
2. Ukrywaj endpointy wewnętrzne/admin, gdy to potrzebne.
3. Używaj `operationIdFactory` dla stabilnego SDK generation.
4. Eksportuj OpenAPI JSON w CI do contract checks/client codegen.
5. Traktuj zmiany endpointów i dokumentacji jako jeden artefakt PR.

#### Praktyczny wniosek

Swagger to kontrakt API, nie tylko UI. Utrzymuj dekoratory i DTO aktualne
równolegle ze zmianami endpointów, by uniknąć „doc drift”.

</details>

<details>
<summary>55. Jak zaimplementować CORS w NestJS i kiedy potrzebne są ustawienia niestandardowe?</summary>

#### NestJS

CORS (Cross-Origin Resource Sharing) kontroluje, które originy przeglądarki
mogą odpytywać Twoje API. W NestJS konfigurujesz go na etapie bootstrapu aplikacji.

#### Podstawowe włączenie CORS

```ts
const app = await NestFactory.create(AppModule);
app.enableCors();
```

To wystarcza lokalnie, ale bywa zbyt liberalne w produkcji.

#### Konfiguracja produkcyjna CORS

```ts
app.enableCors({
  origin: ['https://app.example.com', 'https://admin.example.com'],
  methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE', 'OPTIONS'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true,
  maxAge: 86400,
});
```

#### Kiedy potrzebujesz konfiguracji niestandardowej

1. **Wiele domen frontendowych**
   Potrzebna jawna allowlista per środowisko.

2. **Auth oparty o cookies (`credentials: true`)**
   Wymaga konkretnego originu (nie `*`) i poprawnej polityki secure cookies.

3. **Custom headers/tokens**
   Dodaj wymagane nagłówki do `allowedHeaders`.

4. **Złożone metody/preflight**
   Skonfiguruj `methods` i upewnij się, że `OPTIONS` działa poprawnie.

5. **Dynamiczne reguły originów (tenanty/partnerzy)**
   Użyj funkcji `origin`.

#### Przykład dynamicznego origin

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

#### Częste błędy

1. `origin: '*'` razem z `credentials: true` (niepoprawne/niebezpieczne dla cookies).
2. Brak obsługi preflight (`OPTIONS`) w proxy/gateway.
3. Jeden hardcoded origin dla wszystkich środowisk.
4. Traktowanie CORS jako granicy bezpieczeństwa dla klientów spoza przeglądarki.

#### Praktyczne rekomendacje

1. W produkcji trzymaj restrykcyjną allowlistę originów.
2. Rozdziel konfigurację CORS per środowisko przez `ConfigService`.
3. Loguj blokowane originy do debugowania.
4. Łącz CORS z realnym auth/authz, rate limitingiem i strategią CSRF tam,
   gdzie to potrzebne.

</details>

<details>
<summary>56. Czym jest idempotencja w kontekście REST API i jak ją zapewnić?</summary>

#### NestJS

Idempotencja oznacza, że wielokrotne wykonanie tego samego requestu daje ten
sam końcowy stan systemu jak pojedyncze wykonanie.

W REST API to krytyczne dla niezawodności przy retry, timeoutach sieciowych i
duplikatach po stronie klienta.

#### Semantyka HTTP a idempotencja

1. **Zwykle idempotentne z natury**
   `GET`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`.

2. **Domyślnie nieidempotentne**
   `POST` (często tworzy nowy zasób przy każdym wywołaniu).

#### Dlaczego idempotencja jest ważna

1. Bezpieczne retry klienta po timeout.
2. Ochrona przed duplikacją akcji (podwójna płatność/zamówienie).
3. Lepsza odporność w systemach rozproszonych i at-least-once delivery.

#### Jak zapewnić idempotencję w praktyce

1. **Idempotency key pattern (dla POST)**
   Klient wysyła unikalny klucz (np. header `Idempotency-Key`).
   Serwer zapisuje klucz + fingerprint requestu + odpowiedź.
   Powtórzony ten sam klucz zwraca oryginalny wynik, zamiast ponownego wykonania.

2. **Ograniczenia bazy danych**
   Wymuś unikalność po business identifierach
   (`externalPaymentId`, `orderReference` itd.).

3. **Wzorce upsert/compare-and-set**
   Stosuj deterministyczne operacje zapisu, gdy to możliwe.

4. **Transakcyjne przetwarzanie**
   Chroń wieloetapowe zapisy przed częściową duplikacją.

#### Szkic implementacji w NestJS

1. Interceptor/guard sprawdza `Idempotency-Key`.
2. Wylicza fingerprint (route + user + hash payloadu).
3. Szuka rekordu idempotencji:
   1. jeśli completed -> zwraca zapisaną odpowiedź,
   2. jeśli in-progress -> zwraca conflict/retry-later policy,
   3. jeśli brak -> rezerwuje klucz i wykonuje handler.
4. Atomowo zapisuje finalną odpowiedź i ją zwraca.

#### Minimalny flow koncepcyjny

```text
Request -> Idempotency middleware/interceptor
        -> key exists with completed response? return cached response
        -> else execute use case
        -> persist outcome by key
        -> return response
```

#### Częste pułapki

1. Użycie tego samego klucza dla innego payloadu (należy wykryć i odrzucić).
2. Przechowywanie kluczy bez TTL/cleanup.
3. Brak scope klucza per tenant/user tam, gdzie to konieczne.
4. Zwracanie innej odpowiedzi przy retry dla tego samego klucza.

#### Praktyczna rekomendacja

Dla endpointów płatności/zamówień/subskrypcji wymuszaj idempotency keys +
unikalne constraints DB. To daje ochronę zarówno na poziomie aplikacji,
jak i persystencji.

</details>

<details>
<summary>57. Jak zaimplementować rate limiting w NestJS? (@nestjs/throttler)</summary>

#### NestJS

Rate limiting kontroluje liczbę requestów, jakie klient może wysłać w danym
oknie czasowym. W NestJS standardowym rozwiązaniem jest `@nestjs/throttler`.

#### Dlaczego rate limiting jest potrzebny

1. Chroni API przed abuse i brute-force.
2. Ogranicza przypadkowe przeciążenia od „hałaśliwych” klientów.
3. Poprawia fairness między użytkownikami/tenantami.
4. Zwiększa odporność zanim ruch dotrze do kosztownych zależności.

#### Krok 1: instalacja i konfiguracja modułu

```ts
import { Module } from '@nestjs/common';
import { ThrottlerModule } from '@nestjs/throttler';

@Module({
  imports: [
    ThrottlerModule.forRoot([
      {
        ttl: 60_000, // 60 sekund
        limit: 100,  // 100 requestów na okno
      },
    ]),
  ],
})
export class AppModule {}
```

#### Krok 2: globalny guard

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

Teraz wszystkie trasy są domyślnie limitowane.

#### Krok 3: nadpisania per route/controller

Bardziej restrykcyjny limit:

```ts
@Throttle({ default: { limit: 5, ttl: 60_000 } })
@Post('login')
login() {}
```

Wyłączenie limitu dla health check:

```ts
@SkipThrottle()
@Get('health')
health() {}
```

#### Strategia klucza (kogo limitujesz)

Domyślnie zwykle IP. W realnych systemach często potrzebujesz:

1. limitu po user ID (po auth),
2. limitu po tenant/API key,
3. osobnych polityk per grupa tras.

Możesz rozszerzyć guard/tracker logic pod custom key.

#### Uwaga dla deploymentów rozproszonych

W środowisku multi-instance in-memory storage nie wystarczy do ścisłych,
globalnych limitów. Użyj współdzielonego storage (np. Redis-backed), aby limity
były spójne między replikami.

#### Praktyczne dobre praktyki

1. Bardziej restrykcyjne limity dla auth/reset/token endpointów.
2. Czytelne odpowiedzi `429 Too Many Requests`.
3. Wystawianie `Retry-After`, gdy ma sens dla klientów.
4. Monitoring throttle hits per route/client i tuning limitów.
5. Warstwowa obrona: rate limiting w app + WAF/reverse proxy.

</details>

<details>
<summary>58. Jak zaimplementować request tracing (dodanie requestId do każdego requestu)?</summary>

#### NestJS

Request tracing oznacza dołączenie unikalnego `requestId` do każdego
przychodzącego requestu i propagowanie go przez logi, odpowiedzi oraz wywołania
downstream.

To kluczowe dla debugowania systemów rozproszonych i korelacji zdarzeń między
serwisami.

#### Cele request tracing

1. Korelacja wszystkich logów jednego requestu.
2. Śledzenie awarii przez middleware/guards/services/DB/external APIs.
3. Zwracanie identyfikatora requestu klientom i supportowi.

#### Typowy wzorzec implementacji

1. Middleware odczytuje istniejący header (`x-request-id`) albo generuje UUID.
2. Zapisuje ID na obiekcie request.
3. Dodaje ID do response headers.
4. Logger automatycznie uwzględnia `requestId` w każdym wpisie.

#### Przykład middleware

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

Zastosuj middleware globalnie w `AppModule.configure(...)`.

#### Integracja z logowaniem

1. Dodawaj `requestId` do structured logów z interceptorów/services.
2. Preferuj centralny logger abstraction, aby każda linia miała pola korelacyjne.

Przykład (interceptor timing + requestId):

```ts
const req = context.switchToHttp().getRequest();
const requestId = req.requestId;
this.logger.log({ msg: 'request.start', requestId, path: req.url });
```

#### Propagacja kontekstu async (zaawansowane)

Dla głębokich warstw service/łańcuchów async użyj `AsyncLocalStorage` (lub CLS),
aby mieć dostęp do `requestId` bez ręcznego przekazywania przez każde wywołanie.

#### Propagacja downstream

1. Przekazuj `x-request-id` w outbound HTTP calls.
2. Dodawaj request ID do metadanych wiadomości queue/event.
3. Mapuj na trace/span IDs przy OpenTelemetry.

#### Dobre praktyki

1. Akceptuj upstream request ID tylko z zaufanych gatewayów.
2. Gdy brak ID, generuj je po stronie serwera.
3. Zwracaj ID w odpowiedziach błędów dla szybkiej diagnostyki.
4. Utrzymuj spójną nazwę nagłówka we wszystkich serwisach.
5. Traktuj requestId jako metadane korelacyjne, nie token bezpieczeństwa.

</details>

<details>
<summary>59. Jak obsłużyć multipart/form-data i upload plików w NestJS?</summary>

#### NestJS

W NestJS (adapter Express) upload plików najczęściej realizuje się przez Multer
z interceptorami `@nestjs/platform-express`.

`multipart/form-data` stosujesz, gdy request zawiera pliki (i opcjonalne pola formularza).

#### Kluczowe elementy

1. `FileInterceptor()` dla pojedynczego pliku.
2. `FilesInterceptor()` dla wielu plików (to samo pole).
3. `FileFieldsInterceptor()` dla wielu nazwanych pól plikowych.
4. `@UploadedFile()` / `@UploadedFiles()` do dostępu do sparsowanych plików.

#### Przykład pojedynczego uploadu

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

#### Obsługa wielu plików

1. To samo pole:
   `@UseInterceptors(FilesInterceptor('files', 10))`

2. Nazwane pola:
   `@UseInterceptors(FileFieldsInterceptor([{ name: 'avatar', maxCount: 1 }, ...]))`

#### Walidacja i bezpieczeństwo

1. Egzekwuj limity rozmiaru.
2. Waliduj MIME type i (najlepiej) signature pliku.
3. Sanityzuj nazwy plików, nie ufaj nazwie od klienta.
4. Przechowuj poza wrażliwymi/executable ścieżkami statycznymi.
5. Dla ryzykownych domen uruchamiaj skanowanie malware.

#### Strategie storage

1. Local disk (prosty dev/małe deploymenty).
2. Object storage (S3/GCS/MinIO) dla skali produkcyjnej.
3. DB storage tylko w szczególnych przypadkach (zwykle słabe dla dużych binariów).

#### Praktyki produkcyjne

1. Preferuj direct-to-object-storage dla dużych plików.
2. Metadane trzymaj w DB (owner, key, mime, size, checksum).
3. Używaj signed URLs dla kontroli dostępu upload/download.
4. Dodaj auth + rate limits do endpointów uploadu.
5. Ustal polityki retencji i cleanup.

</details>

<details>
<summary>60. Jak zaimplementować kompresję (gzip/brotli) w NestJS?</summary>

#### NestJS

Kompresja zmniejsza rozmiar odpowiedzi i poprawia wydajność sieciową,
szczególnie dla API zwracających dużo JSON/text.

W NestJS (adapter Express) gzip/brotli zwykle włącza się przez middleware
`compression`.

#### Podstawowa konfiguracja (Express)

1. Zainstaluj `compression`.
2. Zarejestruj middleware w `main.ts`.

```ts
import { NestFactory } from '@nestjs/core';
import compression from 'compression';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    compression({
      threshold: 1024, // kompresuj odpowiedzi > 1KB
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

Negocjację algorytmu determinuje `Accept-Encoding` klienta (`br`, `gzip` itd.,
zależnie od wsparcia runtime/proxy).

#### Gdzie zwykle działa brotli

1. Warstwa aplikacji (middleware Node/runtime support).
2. Reverse proxy/CDN (Nginx, Cloudflare, Vercel itd.).

W wielu systemach produkcyjnych kompresję bardziej efektywnie obsługuje edge/proxy
niż sam proces aplikacji.

#### Co kompresować

1. Odpowiedzi JSON.
2. Treści text/HTML/CSS/JS.
3. Odpowiedzi GraphQL.

#### Czego zwykle nie kompresować

1. Już skompresowanych plików (`.zip`, `.jpg`, `.png`, `.mp4`, `.pdf`).
2. Bardzo małych payloadów (narzut kompresji > zysk).

#### Praktyki operacyjne

1. Ustaw `threshold`, aby pomijać mikro-odpowiedzi.
2. Upewnij się, że cache/proxy respektuje `Vary: Accept-Encoding`.
3. Mierz koszt CPU vs oszczędność transferu.
4. Dla wysokiego ruchu preferuj kompresję na proxy/CDN.
5. Uwzględnij ryzyka TLS + compression w wrażliwych kontekstach (rzadsze dziś,
   ale trzymaj się zaleceń platformy).

#### Uwaga Fastify

Przy adapterze Fastify używaj odpowiedniego pluginu Fastify zamiast middleware
Express.

#### Praktyczna rekomendacja

Włącz kompresję domyślnie dla odpowiedzi API, a następnie dostrój `threshold`
oraz miejsce kompresji (app vs edge/proxy) na podstawie realnego profilu ruchu i CPU.

</details>

<details>
<summary>61. Jak wdrożyć helmet i jakie nagłówki HTTP ustawia?</summary>

#### NestJS

Helmet to middleware bezpieczeństwa ustawiające ochronne nagłówki HTTP,
które zmniejszają powierzchnię ataku (XSS, clickjacking, MIME sniffing,
wycieki przez referrer itd.).

W NestJS (adapter Express) integrujesz go globalnie w `main.ts`.

#### Podstawowa konfiguracja

1. Zainstaluj `helmet`.
2. Zarejestruj middleware.

```ts
import { NestFactory } from '@nestjs/core';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    helmet({
      // CSP/HSTS itd. dostrój do środowiska
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

#### Typowe nagłówki ustawiane przez Helmet (zależne od wersji/konfiguracji)

1. `Content-Security-Policy` (CSP)
2. `Cross-Origin-Opener-Policy`
3. `Cross-Origin-Resource-Policy`
4. `Origin-Agent-Cluster`
5. `Referrer-Policy`
6. `Strict-Transport-Security` (HSTS, gdy kontekst HTTPS jest właściwy)
7. `X-Content-Type-Options: nosniff`
8. `X-DNS-Prefetch-Control`
9. `X-Download-Options` (legacy IE)
10. `X-Frame-Options` (ochrona przed clickjacking)
11. `X-Permitted-Cross-Domain-Policies`
12. Obsługa `X-XSS-Protection` (legacy; nowoczesne przeglądarki polegają głównie na CSP)

Dokładne domyślne wartości zależą od wersji Helmet i środowiska.

#### Praktyczne uwagi konfiguracyjne

1. **Krytyczne jest dostrojenie CSP**
   Restrykcyjne CSP poprawia bezpieczeństwo, ale może blokować skrypty/style,
   jeśli nie jest dobrze skonfigurowane.

2. **HSTS tylko na HTTPS**
   Włączaj ostrożnie dla domen produkcyjnych; unikaj przypadkowego „lock-in” lokalnie.

3. **CORS + Helmet**
   Rozwiązują różne problemy; konfiguruj oba jawnie.

4. **Świadomość reverse proxy**
   Upewnij się, że trusted proxy/HTTPS termination są poprawnie ustawione.

#### Typowy wzorzec produkcyjny

1. Włącz Helmet globalnie.
2. Dostosuj CSP do zachowania frontend/API.
3. Utrzymuj osobne profile konfiguracji dla dev i production.
4. Weryfikuj nagłówki przez testy integracyjne i security skany.

#### Reguła praktyczna

Helmet daje mocny baseline hardeningu, ale to nie „całe bezpieczeństwo”.
Łącz go z auth, walidacją, rate limitami, secure cookies i higieną zależności.

</details>

<details>
<summary>62. Jakie są główne podatności OWASP i jak się przed nimi chronić?</summary>

#### NestJS

Ryzyka OWASP Top 10 to najczęstsze klasy błędów bezpieczeństwa aplikacji web.
W NestJS skuteczna ochrona to podejście warstwowe: walidacja, auth, bezpieczne
domyślne ustawienia, monitoring i hardening infrastruktury.

#### Główne ryzyka OWASP i zabezpieczenia w NestJS

1. **Broken Access Control**
   1. Używaj Guardów do authz (`RolesGuard`, policy/ABAC guards).
   2. Egzekwuj ownership checks na zasobach.
   3. Stosuj deny-by-default.

2. **Cryptographic Failures**
   1. Wymuś HTTPS wszędzie.
   2. Haszuj hasła mocnymi algorytmami (argon2/bcrypt z odpowiednim kosztem).
   3. Trzymaj sekrety w secret managerze, nie w kodzie.
   4. Szyfruj dane wrażliwe „at rest”, gdy wymagane.

3. **Injection (SQL/NoSQL/Command)**
   1. Używaj parametryzowanych zapytań ORM.
   2. Waliduj/whitelistuj input przez DTO + `ValidationPipe`.
   3. Unikaj budowania SQL/command przez konkatenację z inputem usera.

4. **Insecure Design**
   1. Stosuj threat modeling dla krytycznych flow (auth, płatności, admin).
   2. Projektuj idempotencję, rate limiting i abuse controls od początku.
   3. Trzymaj least privilege na granicach architektury.

5. **Security Misconfiguration**
   1. Włącz Helmet i restrykcyjny CORS.
   2. Wyłącz debug defaults w produkcji.
   3. Rozdziel i usztywnij konfigurację production.

6. **Vulnerable/Outdated Components**
   1. Regularnie aktualizuj zależności.
   2. Dodaj SCA skany w CI (`npm audit`, Snyk, Dependabot itd.).
   3. Usuwaj nieużywane pakiety.

7. **Identification & Authentication Failures**
   1. Krótkie access tokeny + rotacja refresh tokenów.
   2. MFA dla kont o podwyższonym ryzyku.
   3. Secure obsługa cookies/tokenów + lockout/rate-limit na login.

8. **Software and Data Integrity Failures**
   1. Podpisane artefakty i zaufany pipeline CI/CD.
   2. Weryfikacja źródeł third-party i pinowanie wersji.
   3. Kontrola zmian konfiguracji i zatwierdzania release.

9. **Security Logging & Monitoring Failures**
   1. Structured logi z requestId/userId/action/outcome.
   2. Alerty na anomalie auth i skoki błędów.
   3. Stack trace w logach backendu, nie w odpowiedziach.

10. **SSRF**
   1. Ogranicz destynacje ruchu wychodzącego.
   2. Waliduj i whitelistuj URL-e zewnętrzne.
   3. Blokuj zakresy IP metadanych/internal.

#### Minimalny baseline dla NestJS

1. Globalny `ValidationPipe` (`whitelist`, `forbidNonWhitelisted`, `transform`).
2. Globalny exception filter z bezpiecznym formatem błędów.
3. Guardy auth + authorization na chronionych trasach.
4. Rate limiting (`@nestjs/throttler`) na wrażliwych endpointach.
5. Helmet + restrykcyjna konfiguracja CORS.
6. Bezpieczna konfiguracja z walidacją startupu (Joi/Zod).
7. Security/dependency skany w CI.

#### Praktyczny wniosek

Bezpieczeństwo to nie jedna biblioteka. W NestJS solidny poziom uzyskujesz przez
konsekwentne defense-in-depth na poziomie kodu, konfiguracji, infrastruktury i operacji.

</details>

<details>
<summary>63. Jak używać HttpModule (axios) w NestJS do zapytań do zewnętrznych API?</summary>

#### NestJS

W NestJS wywołania HTTP do zewnętrznych API najczęściej realizuje się przez
`HttpModule` z `@nestjs/axios`, który opakowuje Axios i integruje go z DI.

#### Dlaczego warto używać `HttpModule`

1. DI-friendly współdzielony klient HTTP.
2. Scentralizowana konfiguracja (base URL, timeout, headers).
3. Łatwiejsze testowanie i mockowanie.
4. Wbudowana integracja z RxJS (`Observable` responses).

#### Krok 1: zarejestruj `HttpModule`

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

Wariant async:
`HttpModule.registerAsync(...)` z `ConfigService`.

#### Krok 2: wstrzyknij `HttpService` do providera

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

#### Wzorzec obsługi błędów

1. Łap błędy Axios i mapuj je na wyjątki domenowe/aplikacyjne.
2. Nie ujawniaj surowych upstream errorów bezpośrednio klientom API.

```ts
try {
  const res = await firstValueFrom(this.http.get('/health'));
  return res.data;
} catch (e: any) {
  const status = e?.response?.status;
  throw new BadGatewayException(`Upstream error: ${status ?? 'unknown'}`);
}
```

#### Praktyki produkcyjne

1. Ustawiaj ścisłe timeouty dla wszystkich outbound calls.
2. Dodaj retry/circuit breaker dla niestabilnych zależności.
3. Propaguj request/correlation IDs w nagłówkach.
4. Używaj typowanych response DTO/adapters dla kontraktów zewnętrznych.
5. Instrumentuj latency, failure rate i upstream status codes.

#### Strategia testowania

1. Mockuj `HttpService` w unit testach.
2. Dla integration testów używaj mock serverów (np. nock/wiremock).
3. Jawnie testuj ścieżki timeout/retry/error mapping.

#### Praktyczny wniosek

Traktuj zewnętrzny HTTP jako niepewne I/O: konfiguruj `HttpModule` centralnie,
opakowuj go w dedykowane client services i egzekwuj odporne polityki timeout/
retry/error.

</details>

<details>
<summary>64. Jak dodać globalne interceptory do axios w NestJS? (dodawanie nagłówków, logowanie)</summary>

#### NestJS

W NestJS interceptory Axios konfigurujesz na `axiosRef` z `HttpService`
(`@nestjs/axios`). Dzięki temu stosujesz globalne zachowanie dla outbound HTTP:
headers, logging, timing, auth tokeny i normalizację błędów.

#### Dlaczego warto używać interceptorów Axios

1. Centralizacja outbound HTTP policy.
2. Brak duplikacji logiki headers/auth w każdym wywołaniu.
3. Spójne request/response logging i metryki.
4. Jedno miejsce normalizacji błędów upstream.

#### Typowy wzorzec implementacji

1. Utwórz providera/serwis, który dostaje `HttpService`.
2. W lifecycle init modułu zarejestruj interceptory raz.
3. Trzymaj logikę interceptorów lekką i deterministyczną.

#### Przykład: globalne nagłówki + logowanie

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

Zarejestruj ten provider w module importującym `HttpModule`.

#### Ważne uwagi produkcyjne

1. Rejestruj interceptory tylko raz (unikaj duplikacji przy hot reload/re-init).
2. Propaguj correlation/request ID z kontekstu requestu wejściowego.
3. Redaguj sekrety (Authorization, API keys) w logach.
4. Trzymaj jawną politykę timeout/retry/circuit-breaker (interceptory to nie cała warstwa resilience).

#### Częste use-case

1. Wstrzykiwanie tokenów auth z `ConfigService`/token providerów.
2. Dodawanie nagłówków tenant/context dla downstream.
3. Standaryzacja obiektów błędów przed rethrow.
4. Emitowanie metryk/traces do systemów observability.

#### Praktyczny wniosek

Interceptors Axios to outbound odpowiednik middleware: jedno miejsce dla
cross-cutting HTTP client policy we wszystkich wywołaniach external API.

</details>

<details>
<summary>65. Jak poprawnie typować odpowiedzi zewnętrznych API w TypeScript?</summary>

#### NestJS

Poprawne typowanie odpowiedzi zewnętrznych API wymaga traktowania danych
zdalnych jako **nieufnych**, dopóki nie przejdą walidacji runtime, przy
jednoczesnym wykorzystaniu typów TypeScript dla ergonomii developmentu.

#### Kluczowa zasada

1. Typy compile-time (`interface`/`type`) poprawiają DX.
2. Walidacja runtime (Zod/class-validator/custom guards) daje bezpieczeństwo.
3. Potrzebujesz obu warstw, nie jednej.

#### Zalecany wzorzec

1. Zdefiniuj response DTO/type dla oczekiwanego kształtu.
2. Pobierz dane przez typowane wywołanie klienta HTTP.
3. Zweryfikuj/parsuj na granicy.
4. Zmapuj do wewnętrznego modelu domenowego przed logiką biznesową.

#### Przykład z `HttpService` + Zod

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

#### Dlaczego same generyki nie wystarczą

```ts
this.http.get<MyType>(...)
```

To mówi TypeScriptowi, czego *oczekujesz*, ale nie weryfikuje faktycznego
payloadu runtime od zewnętrznego serwisu.

#### Praktyczne strategie typowania

1. Twórz dedykowane client moduły per upstream API.
2. Trzymaj upstream DTO oddzielnie od wewnętrznych encji domenowych.
3. Normalizuj/transformuj zewnętrzne enumy i nazwy pól na granicy.
4. Jawnie obsługuj nullable/optional pola (`null` z upstreamu jest częsty).

#### Dobre praktyki obsługi błędów

1. Rozróżniaj błędy transportowe (timeout, 5xx) od schema errors.
2. Mapuj oba typy na stabilne wyjątki wewnętrzne.
3. Loguj metadane odpowiedzi upstream dla diagnostyki (bez wycieku sekretów).

#### Reguła praktyczna

Typuj zewnętrzne odpowiedzi podwójnie:
1. typ statyczny dla code intelligence,
2. walidacja runtime dla poprawności i bezpieczeństwa.

</details>

<details>
<summary>66. Jak zaimplementować logikę retry dla zewnętrznych zapytań HTTP w NestJS?</summary>

#### NestJS

Retry pomaga radzić sobie z transient failures (timeouty, chwilowe 5xx,
krótkie problemy sieciowe) przy wywołaniach external API.

W NestJS retry najczęściej realizuje się operatorami RxJS na `HttpService`
albo przez biblioteki resilience przy granicy klienta.

#### Kiedy retry ma sens

1. Timeouty i błędy sieciowe.
2. Tymczasowe upstream 5xx.
3. Odpowiedzi rate-limit (`429`) z sensowną wskazówką retry (`Retry-After`).

#### Kiedy retry bywa niebezpieczne

1. Operacje nieidempotentne bez idempotency keys.
2. Błędy trwałe (`400`, `401`, `403`, validation failures).
3. Retry storms podczas awarii upstream.

#### Podstawowy retry z RxJS

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

#### Zalecana polityka retry

1. Stosuj exponential backoff.
2. Dodawaj jitter, aby uniknąć zsynchronizowanych fal retry.
3. Ściśle ogranicz max liczbę prób.
4. Retry tylko dla idempotentnych operacji albo zapisów chronionych idempotencją.

#### Łącz retry z zabezpieczeniami

1. Global timeout per request.
2. Circuit breaker dla długotrwałych awarii.
3. Rate limiting i bulkheads dla outbound clients.
4. Centralne metryki: liczba retry, final failure rate, wpływ na latencję.

#### Reguła praktyczna

Retry ma podnosić niezawodność, a nie maskować awarie. Utrzymuj je selektywne,
ograniczone i obserwowalne.

</details>

<details>
<summary>67. Czym jest Circuit Breaker pattern i kiedy go potrzebujesz?</summary>

#### NestJS

Circuit Breaker to wzorzec odpornościowy, który zapobiega ciągłym wywołaniom
niedziałającej zależności. Zamiast bez końca retry'ować uszkodzony upstream,
„otwiera obwód” i przez pewien czas failuje natychmiast.

#### Dlaczego Circuit Breaker jest potrzebny

1. Zapobiega kaskadowym awariom między serwisami.
2. Ogranicza wyczerpanie zasobów (wątki/połączenia/event-loop pressure).
3. Poprawia latencję podczas outage przez fast-fail.
4. Daje niestabilnej zależności czas na odzyskanie.

#### Stany obwodu

1. **Closed**
   Normalna praca, requesty przechodzą.

2. **Open**
   Zależność uznana za niezdrową; wywołania blokowane natychmiast.

3. **Half-open**
   Ograniczona liczba próbnych requestów do testu recovery.
   Sukces -> zamknięcie, porażka -> ponowne otwarcie.

#### Kiedy stosować

1. Wywołania external API/payment/identity providers.
2. Zależność ma istotny failure rate albo latency spikes.
3. Serwis ma duży ruch i retry mogą amplifikować incydent.
4. Biznes toleruje fallback behavior przy niedostępności upstream.

#### Typowa integracja w NestJS

1. Opakuj outbound call policy breakerem.
2. Łącz z timeoutem + bounded retry + fallback.
3. Emituj metryki/zdarzenia zmian stanu obwodu.

Schemat:

```text
request -> timeout check -> circuit breaker -> outbound call
        -> success: normal response
        -> failure threshold exceeded: circuit OPEN
        -> OPEN: fail fast / fallback
```

#### Opcje implementacyjne

1. Biblioteki resilience (np. opossum) wokół `HttpService` calls.
2. Własny lekki breaker dla ograniczonych use-case.
3. Konfiguracja thresholdów przez `ConfigService`.

#### Kluczowe parametry strojenia

1. Failure threshold (% lub liczba).
2. Rozmiar rolling window.
3. Czas cooldown stanu open.
4. Liczba prób half-open.
5. Timeout per call.

#### Częste błędy

1. Brak observability dla stanu breakera.
2. Zbyt agresywne progi (false open).
3. Brak sensownego fallbacka przy open state.
4. Łączenie infinite retry z breakerem (niweluje sens wzorca).

#### Reguła praktyczna

Jeśli awaria upstream może zdestabilizować cały serwis, dodaj circuit breaker na
tej granicy i monitoruj jego state transitions jako pierwszorzędny sygnał SRE.

</details>

<details>
<summary>68. Jak zaimplementować caching (in-memory, Redis) i kiedy używać którego podejścia?</summary>

#### NestJS

Caching przechowuje często odczytywane lub kosztowne dane, aby zmniejszyć
latencję i obciążenie backendu. W NestJS najczęściej używa się cache in-memory
albo Redis.

#### In-memory vs Redis

1. **In-memory cache**
   Przechowywany w pamięci pojedynczego procesu aplikacji.

2. **Redis cache**
   Zewnętrzny współdzielony cache dostępny dla wszystkich instancji.

#### Kiedy używać in-memory

1. Aplikacje single-instance albo lokalny development.
2. Małe, krótkotrwałe wartości cache.
3. Ultra-niska latencja lokalnych odczytów.

Ograniczenia:
1. Brak współdzielenia między replikami.
2. Utrata cache po restarcie/deployu.
3. Presja pamięci bezpośrednio wpływa na proces aplikacji.

#### Kiedy używać Redis

1. Deployment rozproszony/multi-instance.
2. Współdzielony cache między serwisami.
3. Potrzeba centralnego TTL i bardziej kontrolowanej invalidacji.
4. Wyższe wymagania niezawodności i observability.

Trade-off:
1. Dodatkowy network hop i niewielka latencja.

#### Opcje implementacji w NestJS

1. `CacheModule` + adaptery cache-manager.
2. Ręczny klient Redis dla zaawansowanych wzorców.
3. `CacheInterceptor` dla response-level cache na wybranych endpointach.

#### Koncepcyjny setup `CacheModule`

In-memory:

```ts
CacheModule.register({
  ttl: 30_000,
  max: 500,
});
```

Redis (adapter-specific):

```ts
CacheModule.registerAsync({
  useFactory: () => ({
    store: /* redis store adapter */,
    url: process.env.REDIS_URL,
    ttl: 60_000,
  }),
});
```

#### Co warto cache'ować

1. Read-heavy, rzadko zmieniające się dane referencyjne.
2. Kosztowne agregaty obliczeniowe.
3. Odpowiedzi external API z jasno akceptowalną staleness.

#### Czego nie cache'ować bez planu

1. Highly volatile danych bez invalidacji.
2. Wrażliwych danych per-user bez poprawnego scope klucza.
3. Write-critical ścieżek, gdzie stale reads są nieakceptowalne.

#### Dobre praktyki projektowe kluczy

1. Używaj jawnego schematu kluczy (`user:{id}`, `catalog:v2:{region}`).
2. Dobieraj TTL per typ danych.
3. Stosuj cache-aside:
   read -> miss -> load source -> set cache -> return.
4. Miej plan invalidacji przy write/events.
5. Monitoruj hit ratio, evictions i wpływ stale reads.

#### Reguła praktyczna

In-memory tylko dla prostych/single-node przypadków. Dla produkcji z wieloma
instancjami lub współdzielonym stanem przechodź na Redis-backed cache.

</details>

<details>
<summary>69. Czym jest cache invalidation i jak wdrożyć ją poprawnie?</summary>

#### NestJS

Cache invalidation to proces usuwania/aktualizacji danych cache, gdy źródło
prawdy się zmienia, aby klienci nie dostawali nieaktualnych odpowiedzi.

To najtrudniejsza część cachingu, bo poprawność zależy od reguł spójności
biznesowej, a nie tylko od szybkości.

#### Dlaczego invalidation jest kluczowe

1. Zapobiega stale/inconsistent danym widocznym dla użytkownika.
2. Utrzymuje cache zgodny z operacjami zapisu.
3. Ogranicza subtelne, trudne do odtworzenia bugi.

#### Typowe strategie invalidation

1. **TTL-based expiration**
   Klucze wygasają automatycznie po określonym czasie.

2. **Event/write-driven invalidation**
   Po udanym zapisie jawnie usuwasz/aktualizujesz powiązane klucze cache.

3. **Versioned keys**
   Włączasz wersję/tag do klucza; nowe zapisy naturalnie przełączają odczyty na nową przestrzeń kluczy.

4. **Tag/group invalidation** (jeśli narzędzie wspiera)
   Unieważnianie wielu wpisów przez logiczną grupę.

#### Praktyczne wzorce implementacji

1. **Cache-aside z delete-on-write**
   1. Read: cache miss -> DB -> set cache.
   2. Write: update DB -> delete powiązane klucze.

2. **Write-through**
   Aktualizacja cache i DB w jednym flow (uważaj na failure handling).

3. **Event-driven invalidation**
   Publikujesz event domenowy (`user.updated`) i invalidujesz w subscriberach/workerach.

#### Zasady projektowania kluczy

1. Używaj przewidywalnego schematu:
   `user:{id}`, `users:list:{filterHash}`, `product:{id}:v{n}`.

2. Trzymaj jawne mapowanie write -> keys:
   które mutacje unieważniają które klucze odczytu.

3. Dla krytycznych hot keys łącz short TTL + explicit invalidation.

4. W systemach multi-instance używaj shared cache (Redis), nie tylko local memory.

#### Przykładowy flow invalidacji

```text
PATCH /users/42
 -> update DB
 -> del user:42
 -> del users:list:*
 -> return updated response
```

(invalidation list można zawęzić, jeśli śledzisz zależności kluczy/filtrów).

#### Częste błędy

1. Cache list endpointów bez równoległej invalidacji detail/list keys.
2. Poleganie wyłącznie na długim TTL dla często zmienianych danych.
3. Brak obsługi race conditions przy współbieżnych zapisach.
4. Brak tenant/user scope w kluczach.

#### Praktyczna rekomendacja

Zacznij prosto:
1. cache-aside,
2. krótkie TTL,
3. explicit delete-on-write,
a potem przechodź do event-driven/tag-based invalidation wraz ze wzrostem złożoności domeny.

</details>

<details>
<summary>70. Kiedy używać Observables zamiast Promises w NestJS?</summary>

#### NestJS

W NestJS możesz używać zarówno Promise, jak i Observable. Wybór zależy od
modelu przepływu: pojedyncza wartość vs strumień/compozycja reaktywna.

#### Używaj `Promise`, gdy

1. Oczekujesz **jednego wyniku** asynchronicznego.
2. Flow jest prosty request/response.
3. Chcesz czytelny kod z `async/await`.

Typowe przykłady: CRUD w DB, pojedynczy outbound HTTP call.

#### Używaj `Observable`, gdy

1. Obsługujesz **wiele wartości w czasie** (streaming).
2. Potrzebujesz zaawansowanej kompozycji reaktywnej (retry, debounce, merge, cancellation).
3. Pracujesz z WebSockets, eventami, mikroserwisami, SSE.
4. Chcesz deklaratywne pipeline'y operatorów RxJS.

#### Konkretne przypadki w NestJS

1. `HttpService` domyślnie zwraca Observables.
2. `@WebSocketGateway` i event streams naturalnie pasują do RxJS.
3. Transporty mikroserwisowe dobrze mapują się na wzorce reaktywne.

#### Reguła praktyczna

1. Jeśli handler zwraca pojedynczą odpowiedź: `Promise`.
2. Jeśli domena jest stream/event-driven lub wymaga operatorów RxJS: `Observable`.

#### Interoperacyjność

Możesz konwertować między podejściami:

1. Observable -> Promise: `firstValueFrom()` / `lastValueFrom()`.
2. Promise -> Observable: `from(promise)`.

#### Częste pułapki

1. Nadużywanie Observable w prostych przypadkach (niepotrzebna złożoność).
2. Brak obsługi unsubscribe/cancel w długich flow.
3. Mieszanie stylów bez konwencji zespołowej.

#### W skrócie

`Promise` to domyślny wybór dla flow liniowych. `Observable` „błyszczy” przy
streamingu, eventach i zaawansowanej kompozycji asynchronicznej.

</details>

<details>
<summary>71. Jaka jest różnica między async/await i RxJS w obsłudze logiki asynchronicznej i kiedy używać którego podejścia?</summary>

#### NestJS

`async/await` i RxJS rozwiązują asynchroniczność na różnych poziomach złożoności.
Żadne nie jest uniwersalnie „lepsze” — wybór zależy od modelu wykonania.

#### Kluczowa różnica

1. **`async/await` (Promises)**
   Najlepsze dla pojedynczego wyniku i liniowego przepływu.

2. **RxJS (Observables)**
   Najlepsze dla strumieni zdarzeń, wielu wartości, anulowania i zaawansowanej
   kompozycji w czasie.

#### Mocne strony `async/await`

1. Bardzo czytelny, imperatywny kod.
2. Prosta obsługa błędów przez `try/catch`.
3. Idealne dla request-response (pojedyncze DB/API call).
4. Niższy narzut poznawczy dla większości zespołów.

#### Mocne strony RxJS

1. Kompozycja wielu async źródeł (`mergeMap`, `switchMap`, `combineLatest`).
2. Potężne operatory retry/backoff/timeout.
3. Natywne anulowanie przez unsubscribe.
4. Wzorce stream processing (SSE, websockets, reactive pipelines).

#### Typowy podział użycia w NestJS

1. **Services/controllers**
   Najczęściej `async/await` dla use-case biznesowych.

2. **`HttpService` / interceptory / endpointy streamingowe**
   Często Observables, opcjonalnie konwertowane do Promise przy pojedynczym wyniku.

#### Interoperacyjność

Observable -> Promise:

```ts
const res = await firstValueFrom(this.http.get('/health'));
```

Promise -> Observable:

```ts
from(this.usersService.findById(id))
```

#### Kiedy wybrać `async/await`

1. CRUD-style endpointy.
2. One-shot DB/API calls.
3. Priorytet prostego, liniowego flow.

#### Kiedy wybrać RxJS

1. Ciągłe strumienie lub real-time pipeline'y.
2. Złożona orkiestracja wielu async źródeł.
3. Potrzeba cancellation-aware behavior i operator-based flow control.

#### Częste błędy

1. Używanie RxJS do trywialnych one-off operacji (overengineering).
2. Wymuszanie Promise style przy streamingu (utrata korzyści reaktywnych).
3. Chaotyczne mieszanie obu stylów w tym samym module.

#### Reguła praktyczna

Domyślnie stosuj `async/await` dla prostych flow biznesowych; RxJS wprowadzaj tam,
gdzie reaktywność/kompozycja strumieni daje realny zysk operacyjny.

</details>

<details>
<summary>72. Jak unikać blokowania event loop w NestJS i utrzymać wydajność?</summary>

#### NestJS

NestJS działa na event loop Node.js. Jeśli zablokujesz główny wątek,
wzrastają latencje wszystkich równoczesnych requestów.

#### Co blokuje event loop

1. Ciężkie synchroniczne operacje CPU (hashowanie dużych payloadów,
   przetwarzanie obrazów/wideo).
2. Duże synchroniczne parsowanie/stringify JSON.
3. Sync API filesystem (`fs.readFileSync` itd.) w request path.
4. Długie „tight loops” bez oddawania kontroli event loop.
5. Kosztowne regex/backtracking i nieefektywne algorytmy.

#### Praktyczne strategie unikania blokad

1. **Preferuj async I/O API**
   Używaj nieblokujących operacji filesystem/network/DB.

2. **Przenieś CPU-heavy pracę poza request thread**
   1. Worker threads (`worker_threads`)
   2. Background jobs/queues (BullMQ, RabbitMQ itd.)
   3. Dedykowane processing services

3. **Używaj streamingu dla dużych payloadów**
   Unikaj buforowania ogromnych plików/obiektów w pamięci.

4. **Paginuj i dziel pracę na chunki**
   Przetwarzaj duże zbiory partiami, zamiast jednego gigantycznego synchronicznego kroku.

5. **Cache'uj kosztowne obliczenia**
   Reużywaj wyniki tam, gdzie to możliwe.

#### Wzorce architektoniczne NestJS

1. Trzymaj controllery cienkie; ciężkie zadania deleguj do async workers.
2. Używaj kolejek dla email/PDF/report generation/media conversion.
3. Ustawiaj timeouty i backpressure policy na external calls.
4. Stosuj rate limiting na drogich endpointach.

#### Sygnały blokowania event loop

1. Rosnące p95/p99 latency przy umiarkowanym ruchu.
2. Niska „idle” CPU, a słaby throughput.
3. Opóźnione timery i wolne health checks.
4. Rosnące metryki event loop lag.

#### Przydatne narzędzia operacyjne

1. Monitoring event loop lag (`perf_hooks`, APM).
2. CPU profiling/flamegraph dla hot paths.
3. Dashboardy latencji endpointów i rozmiaru payloadów.

#### Częste błędy

1. Sync crypto/compression w handlerach requestów.
2. Generowanie dużych raportów inline w request path.
3. Wczytywanie ogromnych plików do pamięci zamiast streamingu.
4. Ignorowanie złożoności algorytmicznej przy pętlach na dużych kolekcjach.

#### Reguła praktyczna

Request thread powinien orkiestrować, nie wykonywać ciężkich obliczeń.
Utrzymuj go nieblokujący, a kosztowną pracę deleguj do async infrastruktury.

</details>

<details>
<summary>73. Jak optymalizować latencję (p95 / p99) i co wpływa na te metryki?</summary>

#### NestJS

`p95` i `p99` to percentyle „ogona” latencji: pokazują jak wolne jest najgorsze
5% i 1% requestów. Niezawodność produkcyjna zależy bardziej od tych ogonów niż
od średniej.

#### Co najbardziej wpływa na p95/p99

1. Nieefektywne zapytania DB (N+1, brak indeksów, lock contention).
2. Wolne zależności zewnętrzne (HTTP APIs, kolejki, auth providers).
3. Blokowanie event loop (CPU-heavy sync tasks).
4. Saturacja connection pooli (DB/HTTP).
5. Rozmiar payloadów i narzut serializacji.
6. Niski cache hit rate i cold starts.
7. GC pauses i memory pressure.
8. Retry storms i timeout cascades podczas awarii.

#### Strategia optymalizacji (od największego wpływu)

1. **Najpierw pomiar**
   Dodaj dashboardy p50/p95/p99 per endpoint i trace spans per dependency.

2. **Napraw hot paths DB**
   Indeksy krytycznych filtrów, usunięcie N+1, poprawne joiny, paginacja.

3. **Chroń external calls**
   Ścisłe timeouty, bounded retry z jitterem, circuit breakers, fallbacki.

4. **Zmniejsz pracę per request**
   Offload CPU-heavy zadań do workers/queues, lekki request path.

5. **Cache'uj selektywnie**
   Cache read-heavy i kosztownych danych (Redis/in-memory adekwatnie do architektury).

6. **Dostrój pule i współbieżność**
   Right-size DB/HTTP pools, unikaj narastania kolejek.

7. **Kontroluj payloady**
   Ogranicz pola odpowiedzi, stosuj kompresję, unikaj ogromnych obiektów JSON.

#### Techniki praktyczne w NestJS

1. Interceptor-based latency logging z requestId.
2. Instrumentacja downstream calls (DB, HttpService) z timing + status.
3. Global timeout policy dla upstream.
4. Throttling na kosztownych endpointach.
5. Connection pooling dopasowany do realnego ruchu.

#### Typowe antywzorce tail-latency

1. Endpoint robi wiele sekwencyjnych external calls.
2. Długie transakcje DB na ścieżkach odczytu.
3. Per-request cache warmup bez memoizacji.
4. Masowe transformacje DTO na gorących ścieżkach.

#### Podejście SLO

1. Zdefiniuj latency SLO per klasa endpointów (read/write/auth).
2. Alarmuj na breach p95/p99 (nie tylko na średnią).
3. Rób load testy z produkcyjną dystrybucją ruchu.
4. Śledź regresje per release przez perf checks w CI (tam, gdzie możliwe).

#### Reguła praktyczna

Aby poprawić p99, optymalizuj najgorsze ścieżki i zachowanie podczas awarii,
nie tylko ścieżki medianowe. Tail latency to głównie problem systemu i zależności.

</details>
<details>
<summary>74. Jak używać trybu cluster w Node.js razem z NestJS do skalowania?</summary>

#### NestJS

Tryb cluster uruchamia wiele procesów roboczych Node.js na jednej maszynie, co
pozwala aplikacji NestJS wykorzystywać wiele rdzeni CPU zamiast jednej pętli event loop.

#### Dlaczego warto używać trybu cluster

1. Lepsze wykorzystanie CPU na serwerach wielordzeniowych.
2. Wyższa przepustowość dla obciążeń CPU/mieszanych.
3. Izolacja na poziomie procesu (awaria jednego workera nie zatrzymuje wszystkich).

#### Podstawowa koncepcja konfiguracji cluster

1. Proces główny fork-uje `N` workerów (`N` często = liczba rdzeni CPU).
2. Każdy worker uruchamia aplikację Nest na tym samym porcie.
3. Node rozdziela przychodzące połączenia między workerami.

#### Przykład bootstrap (koncepcyjny)

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
    cluster.fork(); // naiwny auto-restart
  });
} else {
  bootstrapWorker();
}
```

#### Ważne aspekty produkcyjne

1. **Bezstanowość**
   Stan w pamięci jest per-worker i nie jest współdzielony.
   Używaj Redis/DB dla wspólnych sesji/cache/locków.

2. **WebSockety**
   Wymagają sticky sessions albo zewnętrznego adaptera pub/sub dla spójności między workerami.

3. **Rate limiting/cache**
   Implementacje in-memory będą niespójne między workerami.
   Preferuj store'y oparte na Redis.

4. **Graceful shutdown**
   Obsłuż `SIGTERM`/`SIGINT` i zamykaj połączenia per worker w kontrolowany sposób.

5. **Obserwowalność**
   Dodawaj worker ID/process ID do logów i metryk.

#### Cluster vs kontenery/orkiestratory

1. Cluster skaluje wertykalnie w ramach jednego hosta.
2. Repliki Kubernetes/PM2/systemd skalują horyzontalnie między hostami.
3. Wiele zespołów stawia najpierw na skalowanie horyzontalne, a cluster stosuje tylko gdy potrzeba.

#### Kiedy tryb cluster ma sens

1. Wdrożenia bare-metal/VM z wielordzeniowym CPU.
2. Potrzeba większej przepustowości bez natychmiastowych zmian infrastruktury.
3. Aplikacja jest w dużej mierze bezstanowa i gotowa na działanie wieloprocesowe.

#### Reguła praktyczna

Cluster może zwiększyć przepustowość na pojedynczym hoście, ale nie zastępuje
architektury rozproszonej. Łącz go z wyniesionym stanem i solidnym zarządzaniem procesami.

</details>

<details>
<summary>75. Jak implementować zadania cron w NestJS przez @nestjs/schedule?</summary>

#### NestJS

W NestJS zadania cron implementuje się przez `@nestjs/schedule`, które udostępnia
deklaratywne dekoratory dla stałych interwałów, timeoutów i wyrażeń cron.

#### Krok 1: zainstaluj i włącz ScheduleModule

```ts
import { Module } from '@nestjs/common';
import { ScheduleModule } from '@nestjs/schedule';

@Module({
  imports: [ScheduleModule.forRoot()],
})
export class AppModule {}
```

#### Krok 2: utwórz serwis z zadaniami harmonogramu

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

#### Własne wyrażenie cron z timezone

```ts
@Cron('0 9 * * 1-5', { timeZone: 'Europe/Kyiv' })
runWeekdayAt9am() {}
```

#### Dynamiczne zadania cron (runtime)

Dla harmonogramów konfigurowanych przez użytkownika użyj `SchedulerRegistry`, aby
dodawać/usuwać zadania w runtime zamiast statycznych dekoratorów.

#### Aspekty produkcyjne

1. **Ryzyko duplikacji w wielu instancjach**
   W skalowanych wdrożeniach każda instancja uruchamia cron, jeśli nie ma koordynacji.
   Użyj rozproszonego locka (Redis/DB) albo uruchamiaj joby w dedykowanym workerze.

2. **Idempotencja**
   Handlery jobów powinny być bezpieczne przy retry i ponownych uruchomieniach.

3. **Obsługa błędów**
   Owijaj joby w try/catch oraz używaj ustrukturyzowanych logów/alertów.

4. **Timeouty i backpressure**
   Unikaj nakładania się długich wykonaniach, jeśli nie jest to zamierzone.

5. **Obserwowalność**
   Emituj metryki: start/koniec/czas trwania/sukces/porażka.

#### Typowe przypadki użycia

1. Cleanup wygasłych sesji/tokenów.
2. Synchronizacja z systemami zewnętrznymi.
3. Raporty/powiadomienia według harmonogramu.
4. Agregacja danych i rozgrzewanie cache.

#### Reguła praktyczna

`@nestjs/schedule` świetnie nadaje się do harmonogramu na poziomie aplikacji, ale
w systemach rozproszonych potrzebna jest koordynacja, aby zapobiec duplikacji wykonań.

</details>

<details>
<summary>76. Czym jest EventEmitter w NestJS i czym różni się od kolejek (Bull)?</summary>

#### NestJS

`EventEmitter` w NestJS (`@nestjs/event-emitter`) to mechanizm pub/sub działający
w obrębie procesu do wewnętrznej komunikacji między modułami. Jest szybki i prosty,
ale nie jest trwały przy awarii/restarcie procesu.

Kolejki Bull/BullMQ to trwałe systemy przetwarzania zadań (zwykle oparte o Redis),
zaprojektowane pod background execution, retry i niezawodność.

#### Kluczowa różnica

1. **EventEmitter**
   1. In-memory, ten sam proces.
   2. Fire-and-forget dla zdarzeń modułowych.
   3. Brak trwałej persystencji domyślnie.

2. **Bull/BullMQ**
   1. Trwałe przechowywanie kolejki (Redis).
   2. Workery przetwarzają joby w tle.
   3. Retry, opóźnienia, backoff, concurrency i wsparcie monitoringu.

#### Kiedy używać EventEmitter

1. Wewnętrzne zdarzenia domenowe w jednej instancji usługi.
2. Lekkie efekty uboczne (trigger audit logu, sygnał invalidacji cache).
3. Nie-krytyczne asynchroniczne rozdzielenie, gdzie sporadyczna utrata jest akceptowalna.

#### Kiedy używać Bull/BullMQ

1. Krytyczne zadania, które muszą przetrwać restarty.
2. Długotrwałe/ciężkie joby (email, raporty, media processing).
3. Potrzeba retry/backoff i obsługi dead-letter.
4. Potrzeba wygładzania obciążenia i kontrolowanej współbieżności.

#### Porównanie modelu niezawodności

1. **EventEmitter**
   Jeśli aplikacja padnie po `emit`, a przed uruchomieniem handlera, zdarzenie może zostać utracone.

2. **Queue**
   Job jest zapisany trwale; worker może wznowić pracę później zgodnie z polityką retry.

#### Tradeoff latencja vs złożoność

1. EventEmitter:
   Niższa latencja, niższa złożoność operacyjna.

2. Queue:
   Nieco wyższa latencja i złożoność infrastruktury, ale dużo wyższa niezawodność.

#### Praktyczny wzorzec NestJS

1. Emituj lokalne zdarzenia domenowe dla natychmiastowych, nie-krytycznych reakcji.
2. Enqueue trwałe joby w tle dla ważnej/kosztownej pracy.
3. Dla integracji cross-service używaj brokerów wiadomości/zdarzeń, nie tylko
   in-process EventEmitter.

#### Reguła praktyczna

Jeśli utrata zdarzenia jest niedopuszczalna, użyj Bull/BullMQ (albo broker-based messaging),
a nie zwykłego EventEmitter.

</details>

<details>
<summary>77. Jak zaimplementować wewnętrzną komunikację event-driven między modułami przez EventEmitter2?</summary>

#### NestJS

Wewnętrzna komunikacja event-driven w NestJS z EventEmitter2 rozsprzęga moduły:
jeden moduł emituje zdarzenie domenowe, a inne moduły reagują bez bezpośrednich wywołań serwisów.

#### Krok 1: włącz EventEmitterModule

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

#### Krok 2: emituj zdarzenia z przepływu aplikacyjnego

```ts
import { Injectable } from '@nestjs/common';
import { EventEmitter2 } from '@nestjs/event-emitter';

@Injectable()
export class OrdersService {
  constructor(private readonly events: EventEmitter2) {}

  async createOrder(input: { orderId: string; userId: string; total: number }) {
    // ...persist order
    this.events.emit('order.created', {
      orderId: input.orderId,
      userId: input.userId,
      total: input.total,
      occurredAt: new Date().toISOString(),
    });
  }
}
```

#### Krok 3: subskrybuj w innych modułach przez `@OnEvent`

```ts
import { Injectable, Logger } from '@nestjs/common';
import { OnEvent } from '@nestjs/event-emitter';

@Injectable()
export class NotificationsListener {
  private readonly logger = new Logger(NotificationsListener.name);

  @OnEvent('order.created')
  async handleOrderCreated(event: { orderId: string; userId: string; total: number }) {
    this.logger.log(`Send confirmation for order ${event.orderId}`);
    // send email / push / audit entry
  }
}
```

#### Konwencje nazw i payloadu

1. Używaj stabilnych nazw: `domain.action` (`order.created`, `user.deleted`).
2. Payload trzymaj jawny i wersjonowalny.
3. Dodawaj metadane (`occurredAt`, `correlationId`, `source`).

#### Aspekty obsługi błędów

1. Handlery zdarzeń powinny samodzielnie łapać/logować błędy.
2. Awaria jednego listenera nie powinna psuć głównego flow transakcyjnego.
3. Dla krytycznych efektów ubocznych enqueue trwałe joby zamiast polegać wyłącznie
   na dostarczaniu zdarzeń in-memory.

#### Wskazówki architektoniczne modułów

1. Emituj zdarzenia z serwisów aplikacyjnych po udanej zmianie stanu.
2. Trzymaj listenery w dedykowanych modułach (notifications, analytics, audit).
3. Unikaj zależności cyklicznych, komunikując się przez zdarzenia zamiast
   bezpośredniego wstrzykiwania serwisów.

#### Reguła praktyczna

Używaj EventEmitter2 do wewnętrznego rozsprzęgania w ramach jednego procesu usługi.
Dla komunikacji cross-service albo gwarantowanego dostarczenia używaj kolejek/brokerów wiadomości.

</details>

<details>
<summary>78. Jak implementować background jobs z użyciem Bull lub BullMQ?</summary>

#### NestJS

Background jobs w NestJS służą do wyniesienia ciężkiej lub niepilnej pracy poza
ścieżkę request/response (emaile, raporty, przetwarzanie mediów, zadania synchronizacji).

Bull/BullMQ dostarczają trwałe kolejki oparte o Redis z retry, opóźnieniami i
kontrolą współbieżności workerów.

#### Typowa architektura

1. API/serwis szybko enqueue-uje job.
2. Worker/processor konsumuje job asynchronicznie.
3. Stan joba jest śledzony (`waiting`, `active`, `completed`, `failed`).

#### Krok 1: zarejestruj moduł kolejki

Konfiguracja modułu w stylu Bull:

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

#### Krok 2: produkuj joby

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

#### Krok 3: konsumuj joby w processorze

```ts
import { Process, Processor } from '@nestjs/bull';
import { Job } from 'bull';

@Processor('emails')
export class EmailsProcessor {
  @Process('send-welcome-email')
  async handleWelcome(job: Job<{ userId: string; email: string }>) {
    // call provider/send email
  }
}
```

#### Uwaga o BullMQ

BullMQ używa nowszych API (`Queue`, `Worker`, `QueueEvents`) i jest zalecany w
nowszych ekosystemach. Przepływ koncepcyjny jest taki sam: producer -> Redis queue -> worker.

#### Dobre praktyki produkcyjne

1. Twórz joby idempotentne (bezpieczne przy retry).
2. Ustawiaj jawnie `attempts`/`backoff` i polityki błędów.
3. Używaj dedykowanych procesów worker dla ciężkich kolejek.
4. Monitoruj głębokość kolejki, czas przetwarzania i failure rate.
5. Stosuj dead-letter/retry analysis workflow dla „poisoned jobs”.
6. Ostrożnie wersjonuj payloady/kontrakty jobów.

#### Częste błędy

1. Uruchamianie ciężkiej logiki joba tylko w procesie API.
2. Brak strategii retry/backoff (albo nieskończone retry).
3. Nieidempotentne efekty uboczne powodujące duplikaty przy retry.
4. Brak obserwowalności dla failed jobs.

#### Reguła praktyczna

Jeśli praca jest wolna, retryowalna lub niekrytyczna dla natychmiastowej odpowiedzi,
enqueue-uj ją do kolejki.

</details>

<details>
<summary>79. Jak projektować idempotentne joby (kolejki zadań), aby uniknąć duplikatów wykonania?</summary>

#### NestJS

Projekt idempotentnego joba oznacza, że wielokrotne uruchomienie tego samego joba
daje ten sam stan końcowy co pojedyncze uruchomienie.

To obowiązkowe w systemach kolejkowych, bo retry, restarty workerów i semantyka
dostarczania mogą powodować zduplikowane próby wykonania.

#### Dlaczego pojawiają się duplikaty

1. Worker pada po efekcie ubocznym, ale przed ACK.
2. Retry po timeout lub partycji sieciowej.
3. Ręczne operacje requeue/replay.
4. Race conditions przy wielu konsumentach.

#### Kluczowe strategie idempotencji

1. **Biznesowy idempotency key**
   Dodaj stabilny unikalny klucz na operację (`paymentId`, `orderId:action`).

2. **Deduplication store**
   Zapisuj przetworzone klucze/status w DB/Redis z ograniczeniem unikalności.

3. **Atomowy check-and-set**
   Zapewnij zasadę „first execution wins” przez transakcję/lock/unikalny insert.

4. **Wzorce outbox/inbox**
   Śledź przetworzone identyfikatory wiadomości, by zapobiec powtórnym efektom ubocznym.

5. **Idempotentne API efektów ubocznych**
   Używaj idempotency keys u dostawców zewnętrznych, jeśli to wspierają.

#### Praktyczny przepływ joba

1. Job startuje z `idempotencyKey`.
2. Spróbuj atomowo zarezerwować klucz:
   1. Jeśli już `completed` -> zakończ sukcesem (no-op).
   2. Jeśli zarezerwowany teraz -> kontynuuj.
3. Wykonaj efekty uboczne.
4. Oznacz klucz jako `completed` z metadanymi wyniku.
5. Przy błędzie zachowaj politykę retry, ale utrzymaj semantykę rekordu idempotencji.

#### Przykładowy model klucza

1. `job_key` (unikalny)
2. `status` (`processing`, `completed`, `failed`)
3. `updated_at`
4. opcjonalnie `result_hash` / `external_reference`

#### Techniki na poziomie kolejki

1. Ustaw deterministyczne `jobId` przy enqueue (zapobiega duplikatom enqueue w wielu
   silnikach kolejek).
2. Używaj ograniczonych retry + backoff.
3. Unikaj równoczesnego przetwarzania tej samej encji (partycjonowanie/locking).

#### Praktyczne wskazówki NestJS/Bull

1. Guard idempotencji umieszczaj na starcie processora, nie tylko po stronie producenta.
2. Trzymaj processor transakcyjny, gdzie to możliwe.
3. Dla wywołań zewnętrznych przekazuj idempotency header/key downstream.
4. Emituj ustrukturyzowane logi z kluczem + attempt + outcome.

#### Częste błędy

1. Zakładanie „exactly once” delivery z kolejki.
2. Wykonywanie efektów ubocznych przed rezerwacją idempotencji.
3. Kluczowanie losowym UUID per retry (psuje deduplikację).
4. Zbyt wczesne usuwanie rekordów idempotencji.

#### Reguła praktyczna

Projektuj każdy background job jako dostarczany co najmniej raz (at-least-once).
Idempotencja na granicy biznesowej sprawia, że retry są bezpieczne.

</details>

<details>
<summary>80. Jak zaimplementować WebSockety w NestJS?</summary>

#### NestJS

WebSockety w NestJS implementuje się przez Gatewaye, najczęściej z użyciem
pakietu `@nestjs/websockets` z adapterem Socket.IO (domyślna, popularna konfiguracja).

#### Kluczowe pojęcia

1. **Gateway**
   Punkt wejścia WebSocket (podobna rola jak controller dla HTTP).

2. **Events/messages**
   Klient emituje nazwy eventów z payloadem; serwer obsługuje je i odpowiada/emituje.

3. **Lifecycle hooks**
   Obsługa połączenia/rozłączenia i inicjalizacji serwera.

#### Podstawowy przykład gatewaya

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
    // auth/context checks can happen here
  }

  handleDisconnect(client: Socket) {
    // cleanup presence/resources
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

#### Wzorce pokoi i broadcastu

1. Dołączanie do pokoju: `client.join(roomId)`.
2. Emit do pokoju: `server.to(roomId).emit(...)`.
3. Emit do wszystkich: `server.emit(...)`.
4. Emit tylko do nadawcy: `client.emit(...)`.

#### Walidacja i bezpieczeństwo

1. Waliduj payloady wiadomości (DTO/pipes).
2. Uwierzytelniaj połączenie (token/sesja podczas handshake).
3. Autoryzuj dostęp do pokoju per event.
4. Stosuj rate limiting/throttling dla „hałaśliwych” eventów.

#### Aspekty produkcyjne

1. Skalowanie wieloinstancyjne wymaga adaptera/pub-sub (np. Redis adapter) do
   propagacji eventów między węzłami.
2. Używaj sticky sessions/strategii load balancera, jeśli wymaga tego transport.
3. Śledź liczbę połączeń, przepustowość eventów i powody rozłączeń.
4. Trzymaj handlery lekkie; ciężką pracę przenoś do kolejek/workerów.

#### Reguła praktyczna

Używaj WebSocketów dla niskolatencyjnych funkcji dwukierunkowych (chat, live updates,
presence). Kontrakty protokołu utrzymuj jawne i zabezpieczone jak każde publiczne API.

</details>

<details>
<summary>81. Jak zaimplementować uwierzytelnianie w WebSocket Gateway?</summary>

#### NestJS

Uwierzytelnianie WebSocket w NestJS zwykle realizuje się podczas handshake,
a następnie egzekwuje per-event przez guardy i kontrole autoryzacji.

#### Typowy przepływ uwierzytelniania

1. Klient wysyła token (JWT/sesja) w handshake:
   `auth`, nagłówki lub query params (preferowane `auth`/headers).

2. Serwer weryfikuje token w middleware/guardzie gatewaya.

3. Kontekst uwierzytelnionego użytkownika jest przypinany do socketu (`client.data.user`).

4. Kolejne handlery wiadomości używają tego kontekstu do autoryzacji.

#### Przykład: uwierzytelnienie przy połączeniu

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

    const user = await this.authService.verifyAccessToken(token); // throws if invalid
    client.data.user = user;
  }

  @SubscribeMessage('chat.send')
  async onSend(
    @ConnectedSocket() client: Socket,
    @MessageBody() payload: { roomId: string; text: string },
  ) {
    const user = client.data.user;
    // authorize user for room access here
    return { ok: true, userId: user.id, text: payload.text };
  }
}
```

#### Autoryzacja eventów przez guardy

1. Używaj `WsGuard`, aby walidować kontekst auth dla każdego eventu.
2. Łącz to z kontrolą ról/polityk (membership w roomie, scope tenantu, uprawnienia).

#### Dobre praktyki bezpieczeństwa

1. Preferuj krótko żyjące access tokeny.
2. Ponownie sprawdzaj autoryzację dla wrażliwych eventów, nie tylko przy connect.
3. Obsługuj wygaśnięcie/cofnięcie tokenu (disconnect albo wymuszenie re-auth).
4. Nigdy nie ufaj user ID przesłanym przez klienta w payloadzie; używaj kontekstu auth socketu.
5. Stosuj throttling/rate limits dla eventów wrażliwych na nadużycia.

#### Uwagi dot. skalowania

1. W setupach wieloinstancyjnych używaj współdzielonej strategii weryfikacji sesji/tokenów.
2. Jeśli presence/roomy są rozproszone, użyj Redis adaptera do synchronizacji stanu między węzłami.

#### Reguła praktyczna

Uwierzytelniaj raz podczas handshake dla wydajności, autoryzuj per-event dla bezpieczeństwa.
Obie warstwy są potrzebne w bezpiecznych systemach real-time.

</details>

<details>
<summary>82. Jakie podejścia stosuje się do skalowania systemów real-time?</summary>

#### NestJS

Skalowanie systemów real-time wymaga jednoczesnego opanowania trzech wymiarów:
1. skali połączeń,
2. przepustowości wiadomości,
3. spójności stanu między węzłami.

#### Kluczowe podejścia do skalowania

1. **Skalowanie horyzontalne instancji gatewaya**
   Uruchamiaj wiele replik WebSocket gatewaya za load balancerem.

2. **Sticky sessions (gdy wymagane)**
   Zapewnij, że ten sam klient pozostaje na tym samym węźle, jeśli model
   transportu/sesji wymaga affinity.

3. **Adapter Pub/Sub do broadcastu między węzłami**
   Użyj Redis adaptera (lub odpowiednika), aby eventy emitowane na jednym węźle
   docierały do klientów podłączonych do innych węzłów.

4. **Wyniesiony stan współdzielony**
   Trzymaj metadane presence/roomów/sesji w Redis/DB, a nie tylko w pamięci procesu.

5. **Backpressure i rate limiting**
   Ograniczaj „hałaśliwych” klientów, limituj bursty fan-out i chroń systemy downstream.

#### Wzorce architektoniczne

1. **Warstwa gateway + warstwa workerów**
   Gatewaye obsługują połączenia; ciężkie przetwarzanie trafia do workerów kolejkowych.

2. **Partycjonowanie kanałów/pokoi**
   Dziel strumienie o dużym wolumenie według tenantu/regionu/tematu.

3. **Event-driven backbone**
   Używaj brokerów (Redis Streams/Kafka/NATS) do trwałej lub wysokoprzepustowej
   dystrybucji eventów, gdy proste pub/sub nie wystarcza.

4. **Optymalizacja fan-out**
   Wstępnie wyliczaj zestawy odbiorców i unikaj kosztownych lookupów DB per wiadomość.

#### Techniki wydajności i niezawodności

1. Używaj kompaktowych payloadów i unikaj zbyt dużych eventów.
2. Stosuj heartbeaty/ping-pong z rozsądnymi timeoutami.
3. Obsługuj reconnect + strategię replay dla utraconych krytycznych wiadomości.
4. Dodawaj circuit breakery/timeouty dla zależności zewnętrznych.
5. Monitoruj p95/p99 latencję dostarczania eventów i drop rate.

#### Niezbędna obserwowalność operacyjna

1. Aktywne połączenia per węzeł.
2. Wiadomości/sek in/out.
3. Rozkład wielkości pokoi i „hot rooms”.
4. Opóźnienie cross-node pub/sub.
5. Powody błędów/rozłączeń i skuteczność reconnectu.

#### Typowy stack implementacyjny NestJS

1. `@WebSocketGateway` dla endpointów real-time.
2. Redis adapter do propagacji eventów między instancjami.
3. Bull/BullMQ do offloadu ciężkich zadań asynchronicznych.
4. `@nestjs/throttler` lub custom guardy do kontroli nadużyć.

#### Reguła praktyczna

Skalowanie real-time to nie tylko „więcej podów”. Trzeba połączyć gatewaye
horyzontalne, współdzielone pub/sub i stan oraz ścisłą kontrolę przepływu,
aby utrzymać przewidywalną latencję.

</details>

<details>
<summary>83. Jakie są podejścia do integracji GraphQL w NestJS (code-first vs schema-first) i czym się różnią?</summary>

#### NestJS

NestJS wspiera dwa podejścia do integracji GraphQL:
1. **Code-first**
2. **Schema-first**

Oba są poprawne produkcyjnie. Różnica polega na tym, gdzie najpierw tworzysz kontrakt API:
w klasach/dekoratorach TypeScript czy w plikach SDL `.graphql`.

#### Podejście code-first

Definiujesz typy i resolvery GraphQL w TypeScript za pomocą dekoratorów, a schema
jest generowana automatycznie.

Przykładowy styl:
1. `@ObjectType()`, `@Field()`, `@InputType()`
2. `@Resolver()`, `@Query()`, `@Mutation()`

Plusy:
1. Jeden język (TS) dla aplikacji i schematu.
2. Silne typowanie i wsparcie refaktoryzacji w IDE.
3. Mniej duplikacji między DTO a modelem schematu.

Minusy:
1. Czytelność schematu dla osób nietechnicznych TS bywa niższa.
2. Wygenerowany schemat nadal trzeba uważnie przeglądać i wersjonować.

#### Podejście schema-first

Definiujesz schemat w plikach SDL `.graphql`, a następnie implementujesz resolvery w TS.

Plusy:
1. Workflow contract-first (dobre dla governance API).
2. SDL jest jawny i łatwy do przeglądu między zespołami.
3. Dobre dopasowanie, gdy schemat jest współdzielony między językami/zespołami.

Minusy:
1. Możliwa duplikacja między SDL a typami TS.
2. Wymaga dyscypliny synchronizacji, aby uniknąć driftu.

#### Przykłady konfiguracji NestJS (koncepcyjnie)

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

#### Jak wybrać

1. Wybierz **code-first**, gdy:
   1. Zespół jest silnie TypeScript-centric.
   2. Priorytetem jest szybkość iteracji.
   3. Schemat jest głównie własnością zespołu backendowego.

2. Wybierz **schema-first**, gdy:
   1. Kontrakt API jest szeroko współdzielony i zarządzany.
   2. Wielu implementatorów/konsumentów zależy od SDL.
   3. Przegląd kontraktu i wersjonowanie to kluczowy workflow.

#### Praktyczna rekomendacja

Dla większości zespołów NestJS code-first daje najszybszy development i silne typowanie.
Schema-first wybieraj tam, gdzie kluczowe są governance kontraktu i współwłasność SDL między zespołami.

</details>

<details>
<summary>84. Czym są resolvery w GraphQL i czym różnią się od kontrolerów REST?</summary>

#### NestJS

Resolvery w GraphQL to funkcje rozwiązujące pola schematu GraphQL.
Stanowią warstwę wykonawczą dostarczającą dane dla zapytań, mutacji i
zagnieżdżonych pól obiektów.

W NestJS resolvery definiuje się przez `@Resolver()` oraz dekoratory metod,
takie jak `@Query()`, `@Mutation()` i `@ResolveField()`.

#### Co robią resolvery

1. Obsługują operacje GraphQL (`query`, `mutation`, subscriptions tam, gdzie używane).
2. Leniwie rozwiązują pola zagnieżdżone (zgodnie z żądanym selection setem).
3. Uzyskują dostęp do kontekstu (użytkownik auth, metadane requestu, loadery).
4. Delegują logikę biznesową do serwisów.

#### Czym resolvery różnią się od kontrolerów REST

1. **Kształt API**
   Kontrolery REST wystawiają wiele endpointów URL.
   Resolver GraphQL wystawia jeden endpoint z operacjami sterowanymi schematem.

2. **Wybór danych**
   REST zwraca stałą odpowiedź dla endpointu.
   GraphQL zwraca pola dynamicznie wybrane przez klienta.

3. **Model wykonania**
   Kontroler REST zwykle obsługuje pełną odpowiedź naraz.
   Drzewo resolverów GraphQL może wykonywać wiele resolverów pól.

4. **Over/under-fetching**
   REST często wymaga kompromisów w projektowaniu endpointów.
   GraphQL ogranicza over/under-fetching przez selection sety zapytań.

5. **Styl wersjonowania**
   REST często używa jawnego wersjonowania API.
   GraphQL zwykle ewoluuje schemat przez deprecacje i zmiany addytywne.

#### Przykład resolvera NestJS

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

#### Dobre praktyki

1. Utrzymuj resolvery cienkie; logikę biznesową trzymaj w serwisach.
2. Używaj DataLoader/batchingu, aby unikać N+1 w zagnieżdżonych polach.
3. Waliduj args/inputy i wymuszaj authz w guardach/kontekście.
4. Projektuj typy schematu wokół języka domeny, nie bezpośrednio wokół tabel DB.

#### Reguła praktyczna

Resolvery są odpowiednikiem kontrolerów w GraphQL, ale z wykonaniem na poziomie pól
i semantyką wyboru danych sterowaną przez klienta.

</details>

<details>
<summary>85. Jak pracować z contextem w GraphQL i jak wdrożyć przez niego autoryzację?</summary>

#### NestJS

W NestJS GraphQL `context` to kontener per-request, który przenosi metadane
żądania (user, headers, requestId, loadery, tenant info) do resolverów i guardów.

Autoryzację zwykle realizuje się przez:
1. uwierzytelnienie użytkownika do contextu,
2. egzekwowanie reguł dostępu przez guardy/polityki świadome GraphQL.

#### Krok 1: wypełnij GraphQL context

Podczas konfiguracji `GraphQLModule` udostępnij dane requestu w context:

```ts
GraphQLModule.forRoot({
  autoSchemaFile: true,
  context: ({ req, res }) => ({ req, res, requestId: req.headers['x-request-id'] }),
});
```

Jeśli middleware/strategia JWT przypina `req.user`, będzie on dostępny przez
GraphQL context.

#### Krok 2: odczytaj context w resolverze

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

#### Krok 3: autoryzuj przez GraphQL guard

Użyj `GqlExecutionContext`, aby odczytać `req.user` w guardach:

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

Zastosowanie:

```ts
@UseGuards(GqlAuthGuard)
@Query(() => User)
me(@Context() ctx: any) {
  return ctx.req.user;
}
```

#### Autoryzacja granularna

1. Kontrola ról przez metadata + guard (`@Roles(...)`).
2. Kontrola policy/ABAC przez serwis subject-action-resource.
3. Autoryzacja na poziomie pola w `@ResolveField()`, gdy potrzebna.

#### Dobre praktyki

1. Utrzymuj context minimalny, ale wystarczający (user, requestId, loadery, tenant).
2. Uwierzytelniaj raz per request, autoryzuj per operacja/pole.
3. Używaj DataLoaderów w context, aby zapobiegać N+1.
4. Nigdy nie ufaj identyfikatorom użytkownika przesłanym przez klienta; używaj
   tylko uwierzytelnionego contextu.

#### Reguła praktyczna

GraphQL context to zaufana „koperta” requestu. Umieść tam tożsamość, a następnie
egzekwuj autoryzację przez guardy/polityki oparte o ten context.

</details>

<details>
<summary>86. Jakie protokoły transportowe i brokerzy wiadomości są wspierani (Kafka, Redis, gRPC, NATS) i czym się różnią?</summary>

#### NestJS

Mikrousługi NestJS wspierają wiele transportów, w tym Kafka, Redis, gRPC
i NATS. Każdy z nich ma inną semantykę dostarczania, profil wydajności oraz
przypadki użycia.

#### Porównanie wysokopoziomowe

1. **Kafka**
   Rozproszony broker commit-log o wysokiej przepustowości, trwałej retencji,
   consumer groups i możliwości replay.

2. **Transport Redis (pub/sub lub wzorce oparte o streams)**
   Bardzo szybkie, proste, niskolatencyjne przesyłanie wiadomości; semantyka
   trwałości/kolejności zależy od wybranego wzorca Redis i konfiguracji.

3. **gRPC**
   Protokół RPC po HTTP/2 z kontraktami Protobuf; świetny do silnie typowanych,
   synchronicznych wywołań service-to-service.

4. **NATS**
   Lekki, wysokowydajny system wiadomości; bardzo dobry do niskolatencyjnego
   pub/sub i request/reply, z opcjonalną trwałością przez JetStream.

#### Kiedy wybrać każde rozwiązanie

1. **Kafka**
   1. Event streaming i audit trails.
   2. Asynchroniczne pipeline'y o wysokiej przepustowości.
   3. Potrzeba replay/historii i mocnego skalowania konsumentów.

2. **Redis**
   1. Prosty, lekki fan-out eventów.
   2. Wzorce messagingowe blisko warstwy cache.
   3. Niski narzut operacyjny w mniejszych systemach.

3. **gRPC**
   1. Niskolatencyjne wewnętrzne RPC ze ścisłymi kontraktami.
   2. Polyglot mikrousługi wymagające generowanych klientów/stubów.
   3. Przypadki użycia bi-directional streaming RPC.

4. **NATS**
   1. Szybki cloud-native messaging.
   2. Request/reply i pub/sub przy minimalnym śladzie.
   3. JetStream, gdy potrzebujesz trwałości/ack/replay.

#### Istotne różnice semantyczne

1. **Styl komunikacji**
   Kafka/NATS/Redis: asynchroniczne wzorce event/message-driven.
   gRPC: bezpośrednie RPC request/response (bardziej synchroniczne).

2. **Trwałość/replay**
   Kafka: silny, trwały log i replay z założenia.
   NATS core: efemeryczny, jeśli nie włączysz JetStream.
   Redis pub/sub: domyślnie efemeryczny.
   gRPC: brak warstwy persystencji brokerowej (semantyka wywołania RPC).

3. **Model kontraktu**
   gRPC używa ścisłych schematów Protobuf-first.
   Transporty brokerowe często opierają się na konwencjach schematów wiadomości
   (Avro/JSON/Protobuf) egzekwowanych przez zespół/tooling.

#### Praktyczne wskazówki projektowe dla NestJS

1. Używaj **gRPC** dla synchronicznych API wewnętrznych wymagających ścisłego typowania.
2. Używaj **Kafka/NATS/Redis** dla asynchronicznych, rozsprzęgniętych workflow.
3. Dla krytycznych eventów biznesowych wymagających replay/audytu preferuj **Kafka**
   albo trwałe wzorce **NATS JetStream**.
4. Standaryzuj envelope wiadomości (`eventName`, `version`, `correlationId`, `payload`).
5. Dodawaj obserwowalność dla lagu, retry, DLQ i zdrowia konsumentów.

#### Reguła praktyczna

Transport wybieraj najpierw po modelu awarii i gwarancjach dostarczenia,
a nie wyłącznie po surowej przepustowości.

</details>

<details>
<summary>87. Jak poprawnie zaprojektować architekturę event-driven i jakie są jej kluczowe zasady?</summary>

#### NestJS

Architektura event-driven (EDA) organizuje systemy wokół zdarzeń: faktów, że
coś się wydarzyło (`order.created`, `payment.failed` itd.). Producenci publikują
zdarzenia, a konsumenci reagują asynchronicznie.

#### Kluczowe zasady

1. **Luźne sprzężenie**
   Producenci nie zależą od wewnętrznej implementacji konsumentów.

2. **Komunikacja asynchroniczna**
   Usługi koordynują się przez zdarzenia zamiast blokującego RPC, tam gdzie to możliwe.

3. **Jedno źródło prawdy per domena**
   Każda usługa jest właścicielem swoich danych i publikuje zdarzenia domenowe po zmianie stanu.

4. **Zarządzanie kontraktami zdarzeń**
   Zdarzenia to wersjonowane kontrakty ze stabilnym schematem i znaczeniem semantycznym.

5. **Idempotentni konsumenci**
   Handlery muszą bezpiecznie przetwarzać duplikaty dostarczeń.

6. **Obserwowalność i śledzalność**
   Correlation ID, metadane zdarzeń i metryki przetwarzania są obowiązkowe.

#### Wskazówki projektowania zdarzeń

1. Nazywaj zdarzenia jako fakty w czasie przeszłym: `invoice.paid`, `user.email_changed`.
2. Dodawaj metadane:
   `eventId`, `eventType`, `occurredAt`, `version`, `correlationId`, `source`.
3. Trzymaj payload skupiony na znaczeniu biznesowym, a nie na wewnętrznej strukturze DB.
4. Preferuj addytywną ewolucję schematu; unikaj zmian łamiących kompatybilność.

#### Model dostarczania i spójności

1. Zakładaj at-least-once delivery w większości systemów brokerowych.
2. Stosuj eventual consistency ponad granicami usług.
3. Używaj retry + DLQ dla nieudanych przetworzeń.
4. Stosuj wzorzec outbox, aby uniknąć luk typu „zapis DB się udał, publikacja eventu nie”.

#### Klocki implementacyjne NestJS

1. Wewnętrzne zdarzenia modułowe: `@nestjs/event-emitter` (in-process).
2. Trwałe przetwarzanie asynchroniczne: kolejki Bull/BullMQ.
3. Cross-service messaging: adaptery transportu Kafka/NATS/Redis.
4. Handlery konsumentów z walidacją + kontrolą idempotencji.

#### Antywzorce, których unikać

1. Payloady zdarzeń z ogromnymi, mutowalnymi snapshotami obiektów.
2. Ukryte synchroniczne sprzężenie przebrane za eventy.
3. Brak strategii wersjonowania schematu.
4. Brak planu replay/recovery przy awarii konsumentów.
5. Traktowanie eventów jak komend (chyba że modelowane świadomie).

#### Praktyczny przepływ architektoniczny

1. Komenda aktualizuje stan domeny w usłudze właściciela.
2. Właściciel emituje zdarzenie domenowe (transakcyjnie przez outbox).
3. Broker dostarcza zdarzenie zainteresowanym konsumentom.
4. Konsumenci aktualizują własne modele odczytu/efekty uboczne.
5. Monitoring śledzi lag, błędy i DLQ.

#### Reguła praktyczna

Projektuj zdarzenia jako trwałe fakty biznesowe, nie szczegóły implementacyjne.
Niezawodność wynika z idempotencji, dyscypliny kontraktów i obserwowalności operacyjnej.

</details>

<details>
<summary>88. Jak obsługiwać transakcje rozproszone w mikrousługach? (wzorzec Saga, eventual consistency)</summary>

#### NestJS

W mikrousługach klasyczna transakcja ACID obejmująca wiele usług/baz danych
zwykle jest niepraktyczna. Zamiast tego stosuje się **eventual consistency**
oraz wzorce koordynacji, takie jak **Saga**.

#### Dlaczego transakcje rozproszone są trudne

1. Usługi mają oddzielne bazy danych.
2. Awarie sieci i częściowe sukcesy są normalne.
3. Globalne transakcje w stylu 2PC obniżają dostępność i zwiększają złożoność.

#### Preferowane podejście: wzorzec Saga

Saga to sekwencja lokalnych transakcji między usługami, sterowana krokami
sukces/porażka.

Dwa warianty:
1. **Choreografia**
   Usługi reagują na zdarzenia bez centralnego koordynatora.
2. **Orkiestracja**
   Dedykowany orkiestrator kontroluje przepływ kroków i kompensacje.

#### Kluczowe pojęcia

1. **Lokalna transakcja per usługa**
   Każda usługa zatwierdza tylko własne zmiany w DB.

2. **Akcje kompensacyjne**
   Gdy późniejszy krok zawiedzie, wcześniej zakończone kroki są kompensowane
   (`reserve -> release`, `charge -> refund`).

3. **Idempotencja**
   Wszystkie handlery/kompensacje muszą tolerować duplikaty dostarczeń.

4. **Eventual consistency**
   Tymczasowe niespójności są akceptowane, dopóki saga nie zbiegnie do stanu końcowego.

#### Przykładowy flow (checkout zamówienia)

1. Serwis zamówień tworzy zamówienie `PENDING`.
2. Serwis płatności obciąża klienta.
3. Serwis magazynu rezerwuje stock.
4. Jeśli wszystko się powiedzie -> zamówienie staje się `CONFIRMED`.
5. Jeśli magazyn zawiedzie po płatności -> uruchom kompensację (`payment.refund`)
   i ustaw zamówienie na `CANCELLED`.

#### Klocki implementacyjne NestJS

1. Transport/broker wiadomości (Kafka, NATS, Redis itd.).
2. Trwała obsługa jobów/eventów z retry i DLQ.
3. Wzorzec outbox do niezawodnej publikacji eventów po lokalnym commicie.
4. Śledzenie stanu sagi (tabela DB/workflow store).
5. Ustrukturyzowane logi z `correlationId`/`sagaId`.

#### Tradeoff choreografia vs orkiestracja

1. **Choreografia**
   + Prosta na starcie, mniejsza zależność centralna
   - Trudniejsza globalna widoczność/kontrola, gdy flow rośnie

2. **Orkiestracja**
   + Jasna własność flow, łatwiejsze debugowanie i kontrola polityk
   - Dodatkowy komponent i logika koordynacji

#### Praktyczne zabezpieczenia

1. Dodawaj timeouty dla każdego kroku sagi.
2. Implementuj retry z backoff dla błędów przejściowych.
3. Definiuj kompensację dla każdego nieidempotentnego efektu ubocznego.
4. Utrzymuj kroki sagi małe i jawne.
5. Monitoruj zacięte/niedokończone sagi.

#### Reguła praktyczna

W mikrousługach nie dąż do globalnego ACID. Modeluj workflow biznesowy jako sagi
z idempotentnymi handlerami, kompensacjami i silną obserwowalnością.

</details>

<details>
<summary>89. Czym jest CQRS i jak wdrożyć go w NestJS za pomocą @nestjs/cqrs?</summary>

#### NestJS

CQRS (Command Query Responsibility Segregation) rozdziela operacje zapisu
(commands) od operacji odczytu (queries), często z różnymi modelami i
strategiami optymalizacji po każdej stronie.

#### Dlaczego używa się CQRS

1. Jasne rozdzielenie mutacji biznesowych od potrzeb odczytu.
2. Lepsza skalowalność dla systemów z przewagą odczytów.
3. Łatwiejsze modelowanie złożonych workflow domenowych.
4. Czystsza integracja ze zdarzeniami i eventual consistency.

#### Kluczowe komponenty CQRS

1. **Command**
   Intencja zmiany stanu (`CreateOrderCommand`).

2. **CommandHandler**
   Wykonuje logikę biznesową i zapisuje stan.

3. **Query**
   Prośba o dane bez efektów ubocznych (`GetOrderByIdQuery`).

4. **QueryHandler**
   Zwraca model odczytu/projekcję danych.

5. **Events** (opcjonalnie, ale często)
   Fakty emitowane po udanych zmianach stanu.

#### Implementacja NestJS z `@nestjs/cqrs`

Krok 1: zainstaluj i zaimportuj `CqrsModule`.

```ts
@Module({
  imports: [CqrsModule],
  providers: [CreateOrderHandler, GetOrderByIdHandler],
})
export class OrdersModule {}
```

Krok 2: zdefiniuj command + handler.

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

Krok 3: zdefiniuj query + handler.

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

Krok 4: użyj busów w kontrolerze/serwisie.

```ts
constructor(
  private readonly commandBus: CommandBus,
  private readonly queryBus: QueryBus,
) {}

await this.commandBus.execute(new CreateOrderCommand(userId, items));
return this.queryBus.execute(new GetOrderByIdQuery(orderId));
```

#### Kiedy CQRS ma sens

1. Złożone reguły domenowe i workflow.
2. Różne potrzeby skalowania dla odczytów i zapisów.
3. Potrzeba projekcji/modeli odczytu event-driven.

#### Kiedy nie nadużywać CQRS

1. Małe aplikacje CRUD z prostą logiką.
2. Zespoły niegotowe na dodatkową złożoność architektoniczną.

#### Reguła praktyczna

Używaj CQRS tam, gdzie uzasadnia to złożoność biznesowa lub potrzeby skalowania.
W przeciwnym razie trzymaj prostszy model service/repository i rozwijaj go stopniowo.

</details>

<details>
<summary>90. Czym jest Domain-Driven Design i jak jego zasady stosuje się w NestJS?</summary>

#### NestJS

Domain-Driven Design (DDD) to podejście, które modeluje oprogramowanie wokół
kluczowych domen biznesowych i ich języka, a nie tylko wokół warstw technicznych.

W NestJS DDD stosuje się przez dopasowanie modułów i granic kodu do możliwości
biznesowych oraz reguł domenowych.

#### Kluczowe zasady DDD

1. **Ubiquitous language**
   Wspólny słownik biznesowy w kodzie, dokumentacji i rozmowach.

2. **Bounded contexts**
   Jasne granice, w których model ma konkretne znaczenie.

3. **Entities / Value Objects / Aggregates**
   Obiekty domenowe z jawnymi inwariantami i regułami spójności.

4. **Domain services**
   Bezstanowe operacje biznesowe, które nie należą do jednej encji.

5. **Repositories**
   Abstrakcje do ładowania/zapisywania agregatów.

6. **Domain events**
   Fakty biznesowe emitowane przy istotnych zmianach stanu.

#### Jak to mapuje się na NestJS

1. **Feature modules jako bounded contexts**
   `OrdersModule`, `BillingModule`, `InventoryModule`.

2. **Serwisy warstwy aplikacyjnej**
   Orkiestrują use case’y, transakcje i integracje.

3. **Warstwa domenowa**
   Czysty model biznesowy (encje/value objects/polityki), niezależny od frameworka.

4. **Adaptery infrastrukturalne**
   DB, messaging, zewnętrzne API, kontrolery HTTP.

#### Typowa struktura folderów (przykład)

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

#### Praktyczne korzyści DDD w NestJS

1. Lepsze dopasowanie do złożonej logiki biznesowej.
2. Mniejsze ryzyko przypadkowego sprzężenia między domenami.
3. Łatwiejsze testowanie logiki core niezależnie od frameworka/infrastruktury.
4. Prostsza ewolucja architektury wraz ze wzrostem systemu.

#### Częste pułapki

1. Nazywanie dowolnego kodu warstwowego „DDD” bez głębi modelu domenowego.
2. Przeciekanie encji ORM bezpośrednio do logiki domenowej.
3. Niespójne mieszanie języka technicznego z pojęciami biznesowymi.
4. Przeinżynierowanie DDD dla trywialnych usług CRUD.

#### Kiedy DDD ma największą wartość

1. Bogate, zmienne reguły biznesowe.
2. Wiele zespołów/domen w jednej platformie.
3. Potrzeba długoterminowej klarowności modelu i autonomii bounded contexts.

#### Reguła praktyczna

Stosuj DDD stopniowo: zacznij od jasnych bounded contexts i ubiquitous language,
a potem rozwijaj głębsze wzorce taktyczne tam, gdzie uzasadnia to złożoność domeny.

</details>

<details>
<summary>91. Czym jest architektura heksagonalna (Ports & Adapters) i jak wdrożyć ją w NestJS?</summary>

#### NestJS

Architektura heksagonalna (Ports & Adapters) porządkuje aplikację tak, aby logika
biznesowa była odizolowana od technologii zewnętrznych (DB, HTTP, brokerów, SDK).

Core zależy od abstrakcji (portów), a konkretne integracje są implementowane jako adaptery.

#### Kluczowe pojęcia

1. **Domain/Application Core**
   Reguły biznesowe i orkiestracja use case’ów.

2. **Ports**
   Interfejsy/kontrakty używane przez core (output ports) albo wystawiane przez core (input ports).

3. **Adapters**
   Techniczne implementacje portów:
   kontrolery HTTP, repozytoria DB, konsumenci wiadomości, klienci API zewnętrznych.

#### Zasada zależności

Wszystkie zależności wskazują do środka:
1. Adaptery zależą od kontraktów core.
2. Core nie zależy od szczegółów frameworka/infrastruktury.

#### Jak zastosować w NestJS

1. Zdefiniuj interfejsy portów w warstwie domain/application.
2. Zaimplementuj adaptery w warstwie infrastrukturalnej.
3. Powiąż klasy adapterów z tokenami portów w providerach modułu.
4. Użyj DI, aby wstrzykiwać port do serwisów use case.

#### Przykładowy kształt

Port (kontrakt core):

```ts
export interface PaymentPort {
  charge(input: { orderId: string; amount: number }): Promise<{ paymentId: string }>;
}
```

Serwis aplikacyjny:

```ts
@Injectable()
export class CheckoutService {
  constructor(@Inject('PAYMENT_PORT') private readonly payments: PaymentPort) {}

  async checkout(orderId: string, amount: number) {
    return this.payments.charge({ orderId, amount });
  }
}
```

Implementacja adaptera:

```ts
@Injectable()
export class StripePaymentAdapter implements PaymentPort {
  async charge(input: { orderId: string; amount: number }) {
    // call Stripe SDK
    return { paymentId: 'pay_123' };
  }
}
```

Powiązanie providera:

```ts
{
  provide: 'PAYMENT_PORT',
  useClass: StripePaymentAdapter,
}
```

#### Korzyści

1. Łatwiejsze testowanie (mockowanie portów w testach jednostkowych).
2. Mniejsze sprzężenie z frameworkiem/ORM/dostawcami zewnętrznymi.
3. Bezpieczniejsze długoterminowe refaktoryzacje i zmiany technologii.
4. Wyraźniejsze granice architektoniczne dla zespołów.

#### Częste pułapki

1. Zbyt ogólne porty (utrata znaczenia domenowego).
2. Przeciekanie typów ORM/HTTP do interfejsów core.
3. Nadmierna abstrakcja dla małych/prostych modułów.

#### Reguła praktyczna

Stosuj granice heksagonalne wokół ważnych flow biznesowych i niestabilnych
zewnętrznych zależności. Porty utrzymuj biznesowe, a adaptery wymienne.

</details>

<details>
<summary>92. Jak wdrożyć ustrukturyzowane logowanie i dlaczego jest potrzebne?</summary>

#### NestJS

Ustrukturyzowane logowanie oznacza zapisywanie logów jako rekordów czytelnych
dla maszyn (zwykle JSON) ze spójnymi polami, zamiast swobodnych tekstów.

Jest potrzebne do wyszukiwalności, alertowania, korelacji i niezawodnej
obserwowalności w systemach produkcyjnych.

#### Dlaczego structured logging jest ważny

1. Szybkie filtrowanie/zapytania na platformach logowych.
2. Lepsze debugowanie incydentów dzięki correlation ID.
3. Spójne dashboardy i alerty.
4. Łatwiejsze śledzenie cross-service w systemach rozproszonych.

#### Co powinno być w każdym logu

1. `timestamp`
2. `level` (`debug`, `info`, `warn`, `error`)
3. `service` / `env`
4. `message`
5. `requestId` / `traceId`
6. Pola kontekstowe (`userId`, `route`, `method`, `statusCode`, latency)
7. Szczegóły błędu (`errorName`, `stack`) dla awarii

#### Podejście implementacyjne w NestJS

1. Użyj structured loggera (Pino/Winston) jako loggera aplikacji.
2. Dołączaj kontekst requestu (`requestId`, user info) przez middleware/interceptor.
3. Loguj zdarzenia biznesowe i błędy według spójnego schematu.
4. Unikaj ad-hoc `console.log` w kodzie produkcyjnym.

#### Praktyczny styl przykładu

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

#### Wskazówki dot. logowania błędów

1. Przechowuj pełny stack trace w logach.
2. Nie wystawiaj stack trace w odpowiedziach API.
3. Dodawaj domenowe kody błędów do niezawodnego routingu alertów.
4. Zachowuj łańcuch przyczyn (root cause) przy opakowywaniu wyjątków.

#### Częste błędy

1. Logowanie zwykłych stringów bez pól kontekstowych.
2. Niespójne nazwy pól między modułami/usługami.
3. Logowanie sekretów/tokenów/PII bez redakcji.
4. Nadmierny debug noise na gorących ścieżkach produkcyjnych.

#### Dobre praktyki

1. Zdefiniuj i udokumentuj schemat logów.
2. Redaguj wrażliwe pola centralnie.
3. Używaj poziomów logowania świadomie.
4. Koreluj logi z metrykami i trace’ami.
5. Waliduj output logowania w testach integracyjnych dla krytycznych flow.

#### Reguła praktyczna

Jeśli logi są tylko dla ludzi, reakcja na incydenty będzie wolna. Gdy logi są
ustrukturyzowane dla maszyn i ludzi, operacje stają się przewidywalne i skalowalne.

</details>

<details>
<summary>93. Jak wdrożyć monitoring zdrowia aplikacji w NestJS? (@nestjs/terminus)</summary>

#### NestJS

Monitoring zdrowia aplikacji w NestJS najczęściej wdraża się przez
`@nestjs/terminus`, które udostępnia ustandaryzowane endpointy health-check
dla gotowości i żywotności aplikacji oraz jej zależności.

#### Dlaczego monitoring zdrowia jest potrzebny

1. Orkiestratory/load balancery potrzebują sygnałów health.
2. Szybsze wykrywanie incydentów i automatyczne odzyskiwanie.
3. Bezpieczne rollouty wdrożeń i bramkowanie readiness.

#### Typowe endpointy health

1. **Liveness** (`/health/live`)
   Kontrola „proces działa”.

2. **Readiness** (`/health/ready`)
   Kontrola „może teraz obsługiwać ruch”, łącznie z krytycznymi zależnościami.

#### Podstawowe kroki konfiguracji

1. Zainstaluj `@nestjs/terminus`.
2. Zaimportuj `TerminusModule`.
3. Utwórz `HealthController` z użyciem `HealthCheckService`.

#### Przykładowy kontroler

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

#### Co uwzględnić w readiness

1. Łączność z DB.
2. Łączność z Redis/cache.
3. Krytyczne zależności zewnętrzne (gdy są faktycznie wymagane do obsługi ruchu).
4. Progi zasobów wewnętrznych (pamięć, pressure event-loop tam, gdzie ma zastosowanie).

#### Dobre praktyki operacyjne

1. Utrzymuj liveness lekki i lokalny.
2. Utrzymuj readiness świadomy zależności, ale szybki.
3. Nie dodawaj niekrytycznych, opcjonalnych usług do kryteriów fail readiness.
4. Ograniczaj/szyfruj szczegóły health w środowiskach publicznych.
5. Integruj z probe’ami Kubernetes i alertowaniem.

#### Reguła praktyczna

Liveness mówi: „zrestartuj mnie, jeśli padłem”. Readiness mówi: „kieruj ruch do mnie
tylko wtedy, gdy mogę bezpiecznie obsługiwać żądania”.

</details>

<details>
<summary>94. Jak wdrożyć health checki dla usług zależnych (DB, Redis, zewnętrzne API)?</summary>

#### NestJS

Health checki zależności weryfikują, czy krytyczne systemy zewnętrzne są
wystarczająco dostępne, aby aplikacja mogła bezpiecznie obsługiwać ruch.

W NestJS zwykle realizuje się to przez wskaźniki `@nestjs/terminus`.

#### Kategorie zależności do sprawdzania

1. **Database** (krytyczna dla readiness w większości API).
2. **Redis/cache** (krytyczne lub opcjonalne zależnie od architektury).
3. **External APIs** (tylko te wymagane na kluczowych ścieżkach requestów).

#### Podejście implementacyjne

1. Utrzymuj `/health/live` lekkie (poziom procesu).
2. Kontrole zależności umieszczaj w `/health/ready`.
3. Oznaczaj zależności niekrytyczne osobno, aby unikać zbędnego hard-fail.

#### Przykładowy kontroler readiness

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

Dla Redis użyj custom health indicatora albo wspieranego adaptera zależnie od stacku.

#### Ważne decyzje projektowe

1. **Krytyczna vs opcjonalna zależność**
   Tylko zależności krytyczne powinny powodować fail readiness.

2. **Timeouty**
   Health checki muszą mieć krótkie, rygorystyczne timeouty, aby uniknąć kumulacji probe’ów.

3. **Koszt checka**
   Używaj lekkich checków typu „ping”, nie kosztownych zapytań.

4. **Semantyka awarii**
   Zwracaj czytelny status per zależność dla diagnostyki.

#### Dobre praktyki operacyjne

1. Używaj oddzielnych endpointów dla probe’ów liveness/readiness/startup.
2. Unikaj sprawdzania zbyt wielu niestabilnych usług zewnętrznych bezpośrednio w readiness.
3. Dodaj cache/debounce dla kosztownych checków, jeśli to potrzebne.
4. Alertuj o zmianach statusu zależności, nie tylko o całkowitym down aplikacji.
5. Uwzględniaj latencję zależności w dashboardach obserwowalności.

#### Reguła praktyczna

Health checki powinny odpowiadać na pytanie: „Czy ta instancja może teraz poprawnie
obsługiwać requesty?”. Projektuj kontrole zależności wokół tego pytania, a nie
wokół sprawdzania wszystkiego.

</details>

<details>
<summary>95. Jak używać OpenTelemetry w NestJS?</summary>

#### NestJS

OpenTelemetry (OTel) w NestJS służy do zbierania trace’ów, metryk i logów na
potrzeby obserwowalności. Najczęstszy punkt startowy to distributed tracing dla
żądań przychodzących i wywołań downstream.

#### Co daje OpenTelemetry

1. End-to-end trace’y requestów między usługami.
2. Rozkład latencji na spany (DB, HTTP, cache, kolejki).
3. Korelację błędów z konkretnymi zależnościami.
4. Vendor-neutral format telemetryczny (eksport do Jaeger/Tempo/Datadog/New Relic itd.).

#### Typowy flow konfiguracji OTel w NestJS

1. Zainicjalizuj OTel SDK przed bootstrapem aplikacji.
2. Skonfiguruj resource attributes (`service.name`, `service.version`, env).
3. Włącz auto-instrumentation (HTTP, Express, klienci DB itd.).
4. Eksportuj trace’y przez OTLP/collector.
5. Dodaj custom spany tam, gdzie ważny jest kontekst biznesowy.

#### Minimalny bootstrap koncepcyjny (Node SDK)

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

Następnie uruchom aplikację Nest normalnie.

#### Przykład custom span (granica biznesowa)

1. Uruchom span wokół krytycznej operacji domenowej.
2. Dodaj atrybuty (`order.id`, `tenant.id`).
3. Rejestruj wyjątki i status przy błędzie.

#### Praktyczne dobre praktyki

1. Stosuj świadome próbkowanie (pełne w staging, dostrojone w produkcji).
2. Propaguj nagłówki kontekstu (`traceparent`) przez granice HTTP/message.
3. Unikaj atrybutów high-cardinality (email użytkownika, losowe ID w etykietach).
4. Instrumentuj krytyczne zależności i konsumentów kolejek.
5. Koreluj trace’y z logami przez trace/span IDs.

#### Częste pułapki

1. Inicjalizacja OTel po starcie aplikacji (utrata wczesnych spanów).
2. Nadmierna instrumentacja powodująca narzut/szum.
3. Brak propagacji kontekstu między usługami/workerami.
4. Wysyłanie telemetry bezpośrednio z aplikacji bez collectora w większych wdrożeniach.

#### Reguła praktyczna

Zacznij od tracingu + auto-instrumentation, a następnie dodawaj celowane custom
spany wokół kluczowych operacji biznesowych i hotspotów latencji.

</details>

<details>
<summary>96. Czym jest distributed tracing i jak wdraża się go w architekturze mikrousług?</summary>

#### NestJS

Distributed tracing śledzi jeden request/transakcję przez wiele usług i
komponentów infrastruktury, pokazując przepływ end-to-end oraz rozkład latencji.

Jest kluczowy w mikrousługach, gdzie pojedyncza akcja użytkownika może uruchomić
wiele wywołań usług, skoków przez kolejki i operacji DB.

#### Kluczowe pojęcia trace’ingu

1. **Trace**
   Pełna ścieżka requestu end-to-end.

2. **Span**
   Jedna operacja wewnątrz trace’a (wywołanie HTTP, zapytanie DB, wykonanie handlera).

3. **Context propagation**
   Przekazywanie kontekstu trace’a między usługami (np. nagłówek `traceparent`).

4. **Relacje parent-child**
   Spany tworzą drzewo reprezentujące hierarchię wywołań.

#### Dlaczego distributed tracing jest potrzebny

1. Pozwala znaleźć prawdziwe bottlenecki (która zależność jest wolna).
2. Umożliwia szybkie debugowanie awarii cross-service.
3. Pomaga zrozumieć fan-out/fan-in i retry storms.
4. Ułatwia poprawę p95/p99 na podstawie danych, a nie domysłów.

#### Jak wdraża się go w mikrousługach

1. Instrumentuj każdą usługę przez OpenTelemetry SDK.
2. Włącz auto-instrumentation frameworków/bibliotek (HTTP server/client, DB, klienci message).
3. Propaguj kontekst przez granice:
   1. Nagłówki HTTP (`traceparent`, `tracestate`)
   2. Metadane wiadomości dla Kafka/NATS/kolejek
4. Eksportuj spany do collectora/backendu (OTLP -> Jaeger/Tempo/Datadog itd.).
5. Koreluj logi przez traceId/spanId.

#### Punkty implementacyjne specyficzne dla NestJS

1. Inicjalizuj OTel przed bootstrapem Nest.
2. Instrumentuj requesty przychodzące (Express/Fastify).
3. Instrumentuj wywołania wychodzące `HttpService` i sterowniki DB.
4. Dodawaj custom spany wokół ważnych operacji biznesowych.
5. Propaguj kontekst do workerów/background jobs.

#### Typowy trace w praktyce

1. API Gateway odbiera request (root span).
2. Service A waliduje auth (child span).
3. Service A wywołuje Service B przez gRPC/HTTP (child span).
4. Service B odpytuje DB (nested span).
5. Service B publikuje event do brokera (child span).
6. Worker konsumuje event i wykonuje efekt uboczny (linked/continued context).

#### Dobre praktyki

1. Używaj spójnego nazewnictwa usług i resource attributes.
2. Unikaj span attributes o wysokiej kardynalności.
3. Dostrajaj politykę próbkowania (tail-based/head-based wg profilu ruchu).
4. Zapisuj błędy i status codes na spanach.
5. Utrzymuj retencję trace’ów zgodnie z potrzebami incydent/debug.

#### Reguła praktyczna

W mikrousługach metryki mówią, że coś jest wolne; distributed tracing pokazuje
dokładnie gdzie i dlaczego.

</details>

<details>
<summary>97. Jak pisać testy jednostkowe w NestJS i jakie są podstawowe podejścia do testowania?</summary>

#### NestJS

Testy jednostkowe w NestJS koncentrują się na testowaniu zachowania jednej klasy/modułu
w izolacji, zwykle z mockowanymi zależnościami i bez realnych wywołań sieci/DB.

#### Główne poziomy testowania w NestJS

1. **Unit tests**
   Testują serwisy/guardy/pipes/interceptory w izolacji.

2. **Integration tests**
   Testują współdziałanie komponentów/modułów (często z testową DB).

3. **E2E tests**
   Testują pełne zachowanie aplikacji HTTP przez realny bootstrap Nest.

#### Typowy stack do testów jednostkowych

1. Jest jako runner/assertion/mocking tool.
2. `@nestjs/testing` do tworzenia modułów testowych.
3. Mock providers dla zależności (`useValue`, `useFactory`).

#### Przykład testu jednostkowego serwisu

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

#### Podstawowe podejścia do testowania

1. **Arrange-Act-Assert**
   Utrzymuj testy czytelne i deterministyczne.

2. **Mockuj zewnętrzne granice**
   DB, klienci HTTP, kolejki i systemy zależne od czasu.

3. **Testuj zachowanie, nie szczegóły implementacji**
   Asercje rób na wynikach i efektach ubocznych, nie na prywatnych detalach.

4. **Pokrywaj happy path + failure path**
   Błędy walidacji, wyjątki, edge case’y.

#### Co testować jednostkowo najpierw w NestJS

1. Serwisy aplikacyjne/domenowe.
2. Custom guardy/pipes/interceptory.
3. Klasy utility/logiki domenowej.
4. Logikę mapperów/walidacji z wieloma gałęziami.

#### Częste błędy

1. Wywoływanie realnej DB w testach „unit”.
2. Nadmierne mockowanie, przez które testy tracą wartość.
3. Zbyt sztywne asercje na kruche wywołania wewnętrzne.
4. Ignorowanie scenariuszy negatywnych/błędów.

#### Reguła praktyczna

Testy jednostkowe powinny być szybkie, izolowane i deterministyczne. Używaj ich
do blokowania zachowania logiki biznesowej; integration/e2e używaj do walidacji
wiringu i realnego zachowania runtime.

</details>

<details>
<summary>98. Jak poprawnie mockować zależności w NestJS i kiedy należy to robić?</summary>

#### NestJS

Mockowanie zależności w NestJS oznacza zastępowanie realnych współpracowników
(repozytoria DB, klienci HTTP, kolejki, zewnętrzne SDK) kontrolowanymi dublerami
testowymi, aby izolować zachowanie jednostki.

#### Kiedy należy mockować

1. W testach jednostkowych serwisów/guardów/pipes/interceptorów.
2. Przy testowaniu ścieżek błędów trudnych do wywołania na realnych systemach.
3. Gdy zależy Ci na szybkim feedback loop i zewnętrzne I/O spowalnia testy.

#### Kiedy nie należy mockować

1. W testach integracyjnych walidujących wiring modułów i realne adaptery.
2. W testach E2E walidujących pełne zachowanie runtime.
3. Gdy ryzyko driftu kontraktu jest wysokie i ważna jest interakcja z realną zależnością.

#### Typowy wzorzec mockowania w NestJS

Użyj `TestingModule` i nadpisuj tokeny providerów przez `useValue`/`useFactory`.

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

#### Wskazówki mockowania według typu zależności

1. **Repository/DAO**
   Mockuj konkretne metody używane w teście (`findOne`, `save` itd.).

2. **HttpService / external client**
   Mockuj wartości zwracane/błędy oraz scenariusze timeoutów.

3. **Queue/event publishers**
   Mockuj wywołania enqueue/publish i asertywnie sprawdzaj payload/kontrakty.

4. **ConfigService**
   Mockuj jawne klucze używane w danej ścieżce kodu.

#### Dobre praktyki mockowania

1. Mockuj tylko zależności graniczne, nie klasę testowaną.
2. Utrzymuj mocki minimalne i skupione na zachowaniu.
3. Resetuj mocki między testami.
4. Najpierw asercje na wynikach, potem na interakcjach.
5. Jawnie pokrywaj ścieżki negatywne (`throws`/`rejects`).

#### Częste błędy

1. Nadmierne mockowanie metod wewnętrznych tej samej klasy (testowanie implementacji).
2. Współdzielenie stanowych mocków między testami bez resetu.
3. Mockowane wartości niezgodne z realnym kształtem kontraktu (fałszywa pewność).
4. Pisanie wyłącznie testów happy-path.

#### Reguła praktyczna

Mockuj, by izolować logikę biznesową i przyspieszać testy jednostkowe.
Używaj integration/e2e, aby zweryfikować realny wiring i kontrakty zewnętrzne.

</details>

<details>
<summary>99. Jak pisać testy integracyjne w NestJS z użyciem TestingModule?</summary>

#### NestJS

Testy integracyjne w NestJS weryfikują, że wiele realnych komponentów działa
razem (wiring modułów, DI, repozytoria/serwisy, pipes/guards), pozostając
jednocześnie lżejszymi od pełnych testów E2E.

`TestingModule` to podstawowe narzędzie do złożenia testowego kontekstu aplikacji.

#### Cel testów integracyjnych

1. Zweryfikować interakcję między realnymi providerami.
2. Wyłapać problemy DI/config/wiring modułów.
3. Testować przepływy persistence/service z realistycznymi zależnościami.

#### Typowy flow konfiguracji

1. Utwórz `TestingModule` z realnym modułem/modułami pod test.
2. Opcjonalnie nadpisz tylko zewnętrzne granice (np. third-party API).
3. Zainicjalizuj kontekst app/module.
4. Przygotuj dane testowe.
5. Wykonaj scenariusz i asertywnie sprawdź efekty uboczne/wyniki.

#### Przykład z `TestingModule` + repository/service

```ts
import { Test, TestingModule } from '@nestjs/testing';

describe('UsersModule Integration', () => {
  let moduleRef: TestingModule;
  let service: UsersService;

  beforeAll(async () => {
    moduleRef = await Test.createTestingModule({
      imports: [UsersModule, TestDatabaseModule], // real module wiring
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

#### Jakie zależności stosować

1. Preferuj realną DB w izolowanym środowisku testowym (test container/in-memory DB tam,
   gdzie akceptowalne).
2. Mockuj tylko niestabilne/kosztowne systemy zewnętrzne (payment gateways, SaaS API).
3. Utrzymuj konfigurację możliwie blisko semantyki produkcyjnej.

#### Strategie zarządzania danymi

1. Transaction rollback per test (gdzie wykonalne).
2. Truncate/reset tabel między testami.
3. Deterministyczne fixture’y/buildery testowe.

#### Częste błędy

1. Zamienianie testów integracyjnych w unit testy przez mockowanie wszystkiego.
2. Współdzielenie mutowalnego globalnego stanu między testami.
3. Przypadkowa zależność od DB produkcyjnej/stagingowej.
4. Brak cleanupu, powodujący flaky testy zależne od kolejności.

#### Reguła praktyczna

Testy integracyjne powinny weryfikować realną współpracę modułów przy minimalnym mockowaniu.
To Twoja główna siatka bezpieczeństwa przed błędnym wiringiem i regresjami persistence.

</details>

<details>
<summary>100. Czym jest testowanie end-to-end (E2E) w NestJS i czym różni się od testów jednostkowych oraz integracyjnych?</summary>

#### NestJS

Testowanie E2E (end-to-end) w NestJS weryfikuje pełne zachowanie aplikacji przez
realne publiczne interfejsy (zwykle HTTP), blisko tego, jak systemu używają klienci.

To poziom testów o najwyższej pewności dla kontraktów API, middleware/guardów,
walidacji, mapowania błędów i wiringu infrastruktury.

#### Czym E2E różni się od innych poziomów testów

1. **Unit tests**
   Testują jedną klasę w izolacji z mockowanymi zależnościami.

2. **Integration tests**
   Testują współpracę kilku realnych komponentów/modułów.

3. **E2E tests**
   Testują pełną ścieżkę request -> pipeline frameworka -> logika biznesowa ->
   persistence -> odpowiedź.

#### Typowa konfiguracja E2E w NestJS

1. Utwórz moduł testowy z pełnym `AppModule` (lub prawie pełnym).
2. Zbootstrappuj instancję aplikacji Nest.
3. Wysyłaj realne requesty HTTP (najczęściej przez `supertest`).
4. Sprawdzaj status code, response body i efekty uboczne.

#### Minimalny przykład E2E

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

#### Co E2E wykrywa najlepiej

1. Błędny setup route/guard/pipe/interceptor.
2. Niezgodności walidacji i serializacji.
3. Regresje flow autoryzacji/uwierzytelniania.
4. Drift realnego kontraktu API.
5. Problemy globalnej obsługi błędów i kształtu odpowiedzi.

#### Częste pułapki

1. Poleganie wyłącznie na E2E (za wolne dla pełnego pokrycia logiki).
2. Uruchamianie testów na współdzielonych, nieizolowanych środowiskach.
3. Niestabilny setup/cleanup danych testowych powodujący flaky testy.
4. Zbyt szeroki pakiet E2E, który staje się wolny i trudny w utrzymaniu.

#### Praktyczna piramida testów

1. Wiele testów jednostkowych (szybka pewność logiki).
2. Część testów integracyjnych (pewność wiringu).
3. Mniej, ale wartościowych testów E2E (pewność kontraktu).

#### Reguła praktyczna

Używaj testów E2E do ochrony krytycznych ścieżek użytkownika/biznesu i zewnętrznych
kontraktów API; testy niższych poziomów wykorzystuj do głębokości i szybkości.

</details>

<details>
<summary>101. Czym jest Nest CLI i które komendy są używane najczęściej?</summary>

#### NestJS

Nest CLI to oficjalne narzędzie wiersza poleceń do tworzenia, generowania,
uruchamiania i utrzymywania aplikacji NestJS.

Standaryzuje scaffolding projektu i przyspiesza codzienny development.

#### Do czego służy Nest CLI

1. Tworzenie nowych projektów z rekomendowaną strukturą.
2. Szybkie generowanie modułów/kontrolerów/serwisów/zasobów.
3. Uruchamianie aplikacji w trybie dev/watch.
4. Budowanie bundli produkcyjnych.
5. Uruchamianie testów przez skonfigurowane skrypty/tooling.

#### Najczęściej używane komendy

1. **Create app**
   `nest new my-app`

2. **Run in development**
   `npm run start:dev`
   (albo `nest start --watch` zależnie od konfiguracji)

3. **Build app**
   `npm run build`
   (albo `nest build`)

4. **Generate module**
   `nest g module users`

5. **Generate controller**
   `nest g controller users`

6. **Generate service**
   `nest g service users`

7. **Generate full CRUD resource**
   `nest g resource users`

8. **Run tests**
   `npm test`, `npm run test:watch`, `npm run test:e2e`

#### Przydatne aliasy komend

1. `nest generate` -> `nest g`
2. `nest controller` -> `nest g co`
3. `nest service` -> `nest g s`
4. `nest module` -> `nest g mo`

#### Przykładowy workflow praktyczny

1. `nest g resource orders`
2. Zaimplementuj logikę domenową/use-case.
3. `npm run start:dev` do lokalnej iteracji.
4. `npm run test` i `npm run test:e2e`.
5. `npm run build` przed wydaniem.

#### Dobre praktyki

1. Używaj generatorów CLI, aby utrzymać spójną strukturę w zespole.
2. Przeglądaj wygenerowany kod i usuwaj nieużywany boilerplate.
3. Preferuj jawne granice architektoniczne zamiast ślepo generowanego warstwowania.
4. Utrzymuj skrypty w `package.json` zgodne z workflow CI zespołu.

#### Reguła praktyczna

Nest CLI to narzędzie produktywności, nie architektura. Używaj go do szybkiego
scaffoldingu, a następnie kształtuj kod zgodnie z domeną i standardami jakości.

</details>

<details>
<summary>102. Jak poprawnie zorganizować Dockerfile dla aplikacji NestJS (multi-stage build)?</summary>

#### NestJS

Poprawny, wieloetapowy Dockerfile dla NestJS oddziela zależności build-time od
obrazu runtime, dzięki czemu kontenery produkcyjne są mniejsze, bezpieczniejsze i szybsze.

#### Dlaczego multi-stage build jest ważny

1. Mniejszy rozmiar finalnego obrazu.
2. Mniejsza powierzchnia ataku (brak narzędzi dev/build w runtime).
3. Szybsze czasy deploy/pull.
4. Czystsze granice zależności.

#### Rekomendowana struktura multi-stage

1. **deps stage**
   Instalacja zależności z lockfile.

2. **build stage**
   Kompilacja TypeScript -> `dist`.

3. **runtime stage**
   Kopiowanie tylko skompilowanego outputu + zależności produkcyjnych.

#### Przykładowy Dockerfile

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

#### Rekomendowany `.dockerignore`

1. `node_modules`
2. `dist`
3. `.git`
4. `coverage`
5. lokalne pliki env niewymagane w build context

#### Dobre praktyki bezpieczeństwa i runtime

1. Uruchamiaj jako użytkownik non-root, gdy to możliwe.
2. Pinuj główną wersję Node i aktualizuj obrazy bazowe.
3. Wstrzykuj konfigurację przez environment/secret manager, nie przez „wypiekane” pliki.
4. Używaj health checków i wsparcia graceful shutdown.
5. Skanuj obraz pod kątem podatności w CI.

#### Wskazówki wydajności buildu

1. Kopiuj lockfile wcześnie, aby wykorzystać cache warstw.
2. Unikaj unieważniania warstwy zależności przez częste zmiany tylko w source.
3. Używaj deterministycznych instalacji (`npm ci`).

#### Częste błędy

1. Obraz single-stage z pełnymi zależnościami dev.
2. Dostarczanie source i narzędzi buildowych w obrazie runtime.
3. Kopiowanie całego kontekstu przed instalacją zależności (psuje efektywność cache).
4. Przechowywanie sekretów w Dockerfile lub w commitowanym `.env`.

#### Reguła praktyczna

Buduj „ciężko” na wcześniejszych etapach, uruchamiaj „lekko” w etapie finalnym.
Kontener produkcyjny powinien zawierać tylko to, co potrzebne do wykonania `dist/main.js`.

</details>

