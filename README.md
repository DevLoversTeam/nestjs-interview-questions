**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  NestJS <img src="./assets/nestjs.svg" width="40" height="40" alt="NestJS logo"/>
</h1>

<h2>Найпопулярніші запитання та відповіді на співбесіді з NestJS</h2>

<details>
<summary>1. Що таке NestJS і які він задачі вирішує?</summary>

#### NestJS

NestJS - це прогресивний Node.js-фреймворк для розробки серверних застосунків.
Він спроєктований насамперед для TypeScript і використовує знайомі архітектурні
підходи з Angular (модулі, dependency injection, декоратори), працюючи поверх
HTTP-адаптерів, таких як Express або Fastify.

#### Які задачі вирішує NestJS

1. **Брак структури в зростаючих Node.js-проєктах** NestJS запроваджує чіткі
   модульні межі (`@Module`), що полегшує масштабування та підтримку великих
   кодових баз.

2. **Складне керування залежностями** Вбудований **Dependency Injection (DI)**
   зменшує зв'язність між класами та покращує тестованість.

3. **Надлишковий шаблонний код для наскрізних задач** Guards, Pipes,
   Interceptors, Filters і Middleware дають єдині патерни для аутентифікації,
   валідації, трансформації, логування та обробки помилок.

4. **Непослідовна архітектура в командах** NestJS задає зрозумілі конвенції,
   завдяки яким команди працюють в одній ментальній моделі й передбачуваній
   структурі проєкту.

5. **Складне налаштування тестування** Утиліти тестування (`@nestjs/testing`) і
   DI-орієнтований дизайн спрощують unit, integration та e2e тести.

6. **Потреба у підтримці різних транспортів** NestJS підтримує HTTP REST,
   GraphQL, WebSockets і мікросервіси (TCP, Redis, NATS, Kafka, gRPC тощо) в
   межах єдиної моделі розробки.

#### Коротко

NestJS допомагає перейти від "просто робочого Node.js-коду" до **добре
структурованої, enterprise-ready backend-архітектури** з високою
підтримуваністю, тестованістю та командною масштабованістю.

</details>

<details>
<summary>2. Чим NestJS відрізняється від Express та Fastify?</summary>

#### NestJS

NestJS, Express і Fastify пов'язані між собою, але працюють на різних рівнях
абстракції.

#### Ключова різниця

1. **Express / Fastify** - це HTTP-фреймворки.
2. **NestJS** - це прикладний фреймворк, який може працювати поверх Express або
   Fastify через адаптери.

#### Архітектура і модель розробки

1. **Express**
   Мінімалістичний і не нав'язує архітектуру. Структуру, DI-підходи, валідацію
   та конвенції ви визначаєте вручну.

2. **Fastify**
   Також доволі низькорівневий, але краще оптимізований під продуктивність,
   має плагінну екосистему та schema-first підхід.

3. **NestJS**
   Дає готову opinionated-архітектуру: модулі, провайдери, контролери,
   dependency injection, lifecycle hooks і стандартизований request pipeline.

#### Погляд на продуктивність

1. **Fastify** зазвичай швидший за Express у сирій HTTP-пропускній здатності.
2. **NestJS на Fastify-адаптері** зазвичай продуктивніший, ніж NestJS на
   Express.
3. У більшості бізнес-систем архітектура, підтримуваність і швидкість командної
   розробки важливіші за micro-benchmark різницю.

#### Порівняння можливостей на практиці

1. **Dependency Injection**
   У NestJS DI вбудований нативно; в Express/Fastify - вручну або через
   сторонні бібліотеки.

2. **Зручність тестування**
   У NestJS є вбудовані патерни для тестових модулів; у нижчорівневих
   фреймворках потрібно більше кастомного налаштування.

3. **Масштабованість кодової бази**
   Конвенції NestJS зменшують хаос у великих командах і проєктах.

4. **Широта екосистеми**
   NestJS об'єднує REST, GraphQL, WebSockets і мікросервіси в межах однієї
   ментальної моделі.

#### Що обирати і коли

1. Обирайте **Express** для дуже простих/невеликих сервісів або сумісності з
   legacy-рішеннями.
2. Обирайте **Fastify**, коли пріоритет - максимальна пропускна здатність і
   низькі накладні витрати.
3. Обирайте **NestJS**, коли потрібні довгострокова підтримуваність, чітка
   архітектура і стандартизований enterprise-підхід до backend-розробки.

</details>

<details>
<summary>3. Які основні складові NestJS?</summary>

#### NestJS

NestJS складається з кількох ключових компонентів, які визначають архітектуру
застосунку, поведінку під час виконання та обробку запитів.

#### Основні складові

1. **Модулі (`@Module`)**
   Базова організаційна одиниця. Модуль групує пов'язані контролери та
   провайдери й керує видимістю через `imports` / `exports`.

2. **Контролери (`@Controller`)**
   Приймають вхідні запити та повертають відповіді. Декоратори маршрутів, такі
   як `@Get()`, `@Post()`, `@Patch()`, прив'язують методи до endpoint-ів.

3. **Провайдери (`@Injectable`)**
   Класи, якими керує DI-контейнер Nest (сервіси, репозиторії, фабрики,
   допоміжні компоненти). Вони інкапсулюють бізнес-логіку та можуть
   інжектитися в інші класи.

4. **Контейнер Dependency Injection (DI)**
   Розв'язує залежності провайдерів через токени, scope-и та модульні межі.
   Це фундамент слабкої зв'язаності в NestJS.

#### Компоненти життєвого циклу запиту

1. **Middleware**
   Виконується до route-handler-ів. Підходить для низькорівневої попередньої
   обробки запиту (наприклад, логування, заголовки, ініціалізація контексту).

2. **Guards (`CanActivate`)**
   Вирішують, чи дозволено запиту рухатися далі (auth/authz gate).

3. **Pipes (`PipeTransform`)**
   Трансформують і валідовують вхідні дані (валідація DTO, парсинг,
   нормалізація).

4. **Interceptors (`NestInterceptor`)**
   Обгортають виконання handler-а для наскрізних задач (мапінг відповіді,
   вимірювання часу, кешування, трасування, retry-логіка).

5. **Exception Filters (`ExceptionFilter`)**
   Централізована обробка помилок і формування відповіді для винятків.

#### Платформені та транспортні складові

1. **HTTP-адаптери**
   Інтеграція з Express або Fastify через платформні адаптери.

2. **Транспортний шар мікросервісів**
   TCP, Redis, NATS, Kafka, gRPC, RMQ та інші через API мікросервісів Nest.

3. **Модулі WebSockets / GraphQL**
   Альтернативні моделі взаємодії, що спираються на ті самі принципи DI та
   модульної архітектури.

#### Практична ментальна модель

Використовуйте **модулі** для структурування доменів, **контролери** як точки
входу API, а **провайдери** для бізнес-логіки. Далі компонуйте поведінку через
Middleware, Guards, Pipes, Interceptors і Filters, щоб будувати надійні
production-сервіси.

</details>

<details>
<summary>4. Яка роль TypeScript у NestJS і чому важливий strict mode?</summary>

#### NestJS

TypeScript - це базовий архітектурний елемент NestJS, а не просто опційне
доповнення. Nest використовує класи, декоратори, інтерфейси та
metadata-орієнтовані DI-патерни, які найкраще працюють саме зі сильною
типізацією.

#### Роль TypeScript у NestJS

1. **Type-safe архітектура**
   Контролери, сервіси, DTO та репозиторії реалізуються як типізовані класи й
   контракти, що зменшує кількість runtime-сюрпризів.

2. **Кращий досвід Dependency Injection**
   Типи в конструкторах роблять залежності провайдерів явними та спрощують
   рефакторинг.

3. **DTO-орієнтовані межі API**
   Форми запитів/відповідей стають явними через DTO-класи та mapped types, що
   покращує підтримуваність і консистентність API.

4. **Інструментарій і продуктивність**
   Сильний IntelliSense, безпечні auto-refactor і compile-time зворотний зв'язок
   пришвидшують командну розробку.

5. **Масштабоване керування кодовою базою**
   Типові контракти слугують виконуваною документацією у великих системах.

#### Чому strict mode важливий

1. **Раніше виявляє помилки**
   `strictNullChecks`, `noImplicitAny` та інші strict-перевірки запобігають
   типовим помилкам ще до продакшену.

2. **Безпечніший рефакторинг**
   У великих NestJS-проєктах strict mode зменшує ризик прихованих поломок під час
   перенесення логіки між модулями/сервісами.

3. **Надійніша доменна логіка**
   Явна optional-типізація та точні union-и змушують свідомо обробляти edge-case
   сценарії.

4. **Вища командна узгодженість**
   Строгі правила компілятора формують єдиний стандарт якості між
   контриб'юторами.

#### Найбільш впливові strict-налаштування для NestJS

1. `strict: true`
2. `noImplicitAny: true`
3. `strictNullChecks: true`
4. `noUncheckedIndexedAccess: true` (рекомендовано для безпечнішого доступу до
   об'єктів/масивів)
5. `noFallthroughCasesInSwitch: true`

#### Практична рекомендація

Використовуйте TypeScript як інструмент проєктування, а не лише як "синтаксичний
цукор". У NestJS strict mode швидко окупається завдяки підвищенню коректності,
читабельності та довгострокової підтримуваності backend-сервісів.

</details>

<details>
<summary>5. Що таке декоратори в NestJS? Наведи приклади.</summary>

#### NestJS

Декоратори в NestJS - це TypeScript-анотації, які додають метадані до класів,
методів, параметрів і властивостей. Nest читає ці метадані під час виконання, щоб
побудувати маршрутизацію, dependency injection, валідацію, авторизацію та інші
framework-механізми.

#### Чому декоратори важливі в NestJS

1. **Декларативне налаштування**
   Ви описуєте поведінку поруч із кодом, а не підтримуєте великі зовнішні
   конфігурації.

2. **Metadata-driven runtime**
   Nest використовує метадані декораторів для побудови модулів, розв'язання
   провайдерів і формування request pipeline.

3. **Узгоджена архітектура**
   Команди працюють за передбачуваними патернами в контролерах, сервісах і
   guards.

#### Основні категорії декораторів

1. **Декоратори класів**
   `@Module()`, `@Controller()`, `@Injectable()`

2. **Декоратори методів**
   `@Get()`, `@Post()`, `@UseGuards()`, `@UseInterceptors()`

3. **Декоратори параметрів**
   `@Param()`, `@Body()`, `@Query()`, `@Headers()`, `@Req()`

4. **Декоратори інжекції у властивість/конструктор**
   `@Inject(TOKEN)` (коли використовуються кастомні provider tokens)

#### Приклад

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

#### Практичний висновок

Декоратори - одна з ключових причин, чому NestJS відчувається структурованим:
вони роблять поведінку фреймворку явною, композиційною та зручною для
масштабування у великих сервісах.

</details>

<details>
<summary>6. Що таке Reflect.metadata і як NestJS використовує його під капотом?</summary>

#### NestJS

`Reflect.metadata` - це частина механізму reflection-метаданих, який
використовується з TypeScript-декораторами (через полiфiл `reflect-metadata`).
Він дозволяє прикріплювати структуровані метадані до класів, методів і
параметрів, щоб фреймворки могли читати їх під час виконання.

На практиці NestJS побудований навколо метаданих: декоратори записують
метадані, а Nest читає їх для побудови графа залежностей, карти маршрутів,
ланцюжків guards/pipes/interceptors і логіки резолву параметрів.

#### Ідея в одному реченні

1. Декоратор записує метадані.
2. Nest читає метадані через `Reflector` / `Reflect` API.
3. Runtime-поведінка збирається автоматично.

#### Де NestJS використовує метадані

1. **Dependency Injection**
   Типи параметрів конструктора та явні injection tokens читаються для
   розв'язання провайдерів з IoC-контейнера.

2. **Маршрутизація**
   `@Controller()` та `@Get()/@Post()` зберігають метадані шляху й HTTP-методу,
   які використовуються для реєстрації route-handler-ів.

3. **Guards, Pipes, Interceptors, Filters**
   Метадані на рівні методу/класу визначають, які наскрізні компоненти
   застосовуються.

4. **Кастомні анотації авторизації**
   Декоратори на кшталт `@Roles('admin')` зберігають метадані, які потім читають
   guards.

#### Мінімальний приклад (запис і читання метаданих)

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

#### NestJS-специфічна примітка

У реальних NestJS-застосунках зазвичай використовують:
1. `SetMetadata()` для запису метаданих.
2. Сервіс `Reflector` усередині Guards/Interceptors для безпечного читання.

Такий підхід краще узгоджений із фреймворком і простіше тестується, ніж прямі
виклики `Reflect.getMetadata(...)` по всьому коду.

</details>

<details>
<summary>7. Як створити власний декоратор у NestJS? (createParamDecorator, SetMetadata)</summary>

#### NestJS

У NestJS кастомні декоратори найчастіше створюють двома базовими способами:
1. **`SetMetadata()`** - для додавання кастомних метаданих до роутів/класів.
2. **`createParamDecorator()`** - для витягування кастомних значень із контексту
   запиту.

Ці два підходи покривають більшість реальних сценаріїв: маркери авторизації та
параметри, похідні від request-контексту.

#### 1) Кастомний metadata-декоратор через `SetMetadata`

Використовуйте, коли потрібно анотувати handlers/класи даними, які потім читають
Guards або Interceptors.

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Використання:

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

Guard читає метадані через `Reflector`:

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

#### 2) Кастомний параметр-декоратор через `createParamDecorator`

Використовуйте, коли потрібні чисті сигнатури контролерів і повторно
використовуваний парсинг request-даних.

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

Використання:

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

#### Найкращі практики

1. Тримайте декоратори "тонкими"; бізнес-логіку розміщуйте в Guards/Services.
2. Використовуйте константи для metadata-ключів (уникайте magic strings).
3. Віддавайте перевагу `Reflector.getAllAndOverride()` для злиття метаданих
   класу + методу.
4. Типізуйте вихід param-декоратора, щоб контракти контролера були явними.

</details>

<details>
<summary>8. Що робить @Injectable() і навіщо він потрібен?</summary>

#### NestJS

`@Injectable()` позначає клас як провайдер, що може брати участь у NestJS
Dependency Injection (DI). Тобто він повідомляє Nest, що цим класом керує
IoC-контейнер і в його конструктор можна інжектити залежності.

#### Що робить `@Injectable()`

1. **Реєструє DI-метадані**
   Дає Nest можливість трактувати клас як injectable-провайдер.

2. **Дозволяє constructor injection**
   Nest може розв'язувати й інжектити залежності, оголошені в конструкторі.

3. **Інтегрується з provider scope/lifecycle**
   Клас може працювати у scope `DEFAULT`, `REQUEST` або `TRANSIENT` (коли це
   налаштовано).

4. **Покращує тестованість**
   Injectable-сервіси легко підміняти моками в тестових модулях.

#### Навіщо це потрібно

1. **Декуплінг**
   Контролери залежать від абстракцій/сервісів, а не створюють залежності
   вручну.

2. **Single responsibility**
   Бізнес-логіка зосереджується в сервісах, а не в контролерах.

3. **Централізоване створення об'єктів**
   Контейнер Nest контролює інстанціювання, спільне використання та життєвий
   цикл залежностей.

4. **Масштабована архітектура**
   DI-підхід залишається керованим зі зростанням застосунку та команди.

#### Приклад

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

#### Практичний нюанс

Самого `@Injectable()` недостатньо: провайдер також має бути зареєстрований у
модулі (масив `providers`) або експортований/імпортований через модульні межі,
щоб Nest міг коректно розв'язати його там, де потрібно.

</details>

<details>
<summary>9. У чому різниця між @Controller і @Get()/@Post() декораторами?</summary>

#### NestJS

`@Controller` і декоратори route-методів (`@Get`, `@Post` тощо) працюють разом,
але відповідають за різні рівні маршрутизації.

#### Основна різниця

1. **`@Controller()`**
   Оголошує клас контролером і задає **базовий префікс маршруту** для всіх
   handler-ів усередині цього класу.

2. **`@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`**
   Прив'язують конкретний метод класу до HTTP-методу та route-path.

#### Ментальна модель

1. `@Controller('users')` означає: "Усі endpoint-и цього класу починаються з
   `/users`."
2. `@Get(':id')` означає: "Цей метод обробляє `GET /users/:id`."

#### Приклад

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

Підсумкові маршрути:
1. `GET /users`
2. `GET /users/:id`
3. `POST /users`

#### Чому такий поділ корисний

1. **Чітка структура API**
   Клас групує пов'язані endpoint-и за доменом/ресурсом.

2. **Повторно використовувана конфігурація рівня контролера**
   Guards, interceptors, versioning і префікси можна застосовувати на рівні
   класу.

3. **Читабельний routing layer**
   Декоратори методів роблять намір endpoint-а явним і зручним для перегляду.

</details>

<details>
<summary>10. Як NestJS обробляє HTTP-запити і визначає, який контролер викликати?</summary>

#### NestJS

NestJS визначає цільовий контролер і handler через метадані, зібрані з
декораторів під час bootstrap застосунку, а потім виконує запит через
визначений pipeline.

#### Як маршрутизація будується на старті

1. **Сканування модулів**
   Nest сканує імпортовані модулі та знаходить зареєстровані контролери й
   провайдери.

2. **Збір route-метаданих**
   `@Controller()` задає базовий шлях; `@Get/@Post/...` задають HTTP-метод і
   підшлях.

3. **Реєстрація маршрутів в адаптері**
   Nest об'єднує метадані в конкретні маршрути та реєструє їх у роутері Express
   або Fastify.

#### Що відбувається для кожного вхідного запиту

1. Запит потрапляє в HTTP-адаптер (Express/Fastify).
2. Роутер зіставляє HTTP-метод + URL-шлях із методом контролера.
3. Nest створює `ExecutionContext` для цього handler-а.
4. Далі виконується request pipeline у такому порядку:
   1. Middleware (якщо налаштований)
   2. Guards (рішення щодо авторизації)
   3. Interceptors (до handler-а)
   4. Pipes (парсинг/валідація параметрів)
   5. Виконання методу контролера
   6. Interceptors (після handler-а, мапінг відповіді)
   7. Exception filters (якщо виникли помилки)
5. Фінальна відповідь повертається через адаптер.

#### Як Nest обирає точний метод контролера

1. Зіставлення за HTTP-методом (`GET`, `POST` тощо).
2. Зіставлення за нормалізованим повним шляхом:
   `globalPrefix + controllerPath + handlerPath`.
3. Якщо ввімкнено versioning, додатково перевіряються версійні обмеження.
4. Якщо є route params (`:id`), застосовується відповідний pattern matching.

#### Приклад зіставлення

```ts
@Controller('users')
export class UsersController {
  @Get(':id')
  findOne() {}
}
```

Якщо глобальний префікс - `api`, то запит `GET /api/users/42` буде зіставлений з
`UsersController.findOne`.

#### Практичний висновок

NestJS не "шукає контролери динамічно" на кожен запит. Він попередньо обчислює
карту маршрутів під час bootstrap і далі виконує передбачуваний request-lifecycle
навколо знайденого handler-а.

</details>

<details>
<summary>11. Як NestJS використовує decorators для побудови routing layer?</summary>

#### NestJS

У NestJS маршрутизація є metadata-driven. Декоратори анотують класи та методи, а
Nest під час bootstrap читає ці метадані й формує конкретну карту маршрутів у
базовому HTTP-адаптері.

#### Джерела route-метаданих

1. **`@Controller(path)`**
   Оголошує префікс на рівні контролера (простір ресурсу).

2. **Декоратори методів**
   `@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`, `@Options()`,
   `@Head()`, `@All()` задають HTTP-метод + шлях handler-а.

3. **Декоратори параметрів**
   `@Param()`, `@Query()`, `@Body()`, `@Headers()`, `@Req()`, `@Res()`
   визначають, як дані запиту інжектяться в аргументи handler-а.

4. **Наскрізні декоратори**
   `@UseGuards()`, `@UsePipes()`, `@UseInterceptors()`, `@UseFilters()`
   прикріплюють execution-поведінку до роуту/класу.

#### Як Nest будує маршрути

1. Сканує модулі та знаходить контролери.
2. Читає метадані контролера + методів через reflection.
3. Складає повний шлях:
   `globalPrefix + controllerPath + methodPath`.
4. Реєструє зібрані handler-и в роутері Express/Fastify.
5. Обгортає handler-и pipeline-ланцюжком із guards/pipes/interceptors/filters.

#### Приклад

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

Підсумкова routing-логіка:
1. `GET /users/:id` -> `getById`
2. `POST /users` -> `create` (під захистом guard-а)

#### Чому цей дизайн сильний

1. **Декларативність і локальність**
   Правила маршрутизації розміщені поруч із кодом handler-а.

2. **Композиційність**
   Декоратори на рівні класу й методу природно комбінуються.

3. **Узгодженість фреймворку**
   Той самий підхід працює для REST, GraphQL-resolver-ів і handler-ів
   мікросервісних повідомлень (із transport-specific декораторами).

</details>

<details>
<summary>12. У чому різниця між imports, exports, providers і declarations в @Module?</summary>

#### NestJS

У модулях NestJS поля `imports`, `providers` і `exports` визначають ключові межі
видимості та залежностей. Поле `declarations` **не** є полем модуля NestJS (це
поняття з Angular), тому використовувати його в `@Module()` некоректно.

#### Коректні поля модуля

1. **`providers`**
   Класи/фабрики/значення, які створюються в DI-контексті цього модуля.
   Вони доступні всередині цього модуля за замовчуванням.

2. **`imports`**
   Інші модулі, чиї **експортовані провайдери** ви хочете використати в цьому
   модулі. Імпорт модуля не відкриває всі його провайдери, а лише експортовані.

3. **`exports`**
   Підмножина провайдерів цього модуля (або реекспортованих модулів), яка має
   бути видимою для модулів-споживачів.

4. **`controllers`**
   Route-handler-и, якими володіє цей модуль (для HTTP-шару). Вони не
   експортуються як injectable-провайдери за замовчуванням.

#### Щодо `declarations`

1. `declarations` використовується в Angular NgModule для
   components/directives/pipes.
2. NestJS `@Module()` **не** підтримує `declarations`.
3. Найближчі аналоги в NestJS - переважно `controllers` + `providers` (залежно
   від ролі).

#### Приклад

```ts
import { Module } from '@nestjs/common';

@Module({
  providers: [UsersService],     // створюється в контексті UsersModule
  exports: [UsersService],       // стає доступним для модулів-споживачів
})
export class UsersModule {}

@Module({
  imports: [UsersModule],        // тепер можна інжектити експортований UsersService
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Практичне правило

1. Розміщуйте service/repository/factory класи в `providers`.
2. Розміщуйте route-handler-и в `controllers`.
3. Потрібні зовнішні модулі додавайте в `imports`.
4. В `exports` виносьте лише повторно використовувану API-поверхню
   (уникайте надмірного експорту).

</details>

<details>
<summary>13. Яка різниця між @Module imports та @Module providers?</summary>

#### NestJS

`imports` і `providers` у `@Module()` вирішують різні DI-завдання:
1. `imports` з'єднує модулі між собою.
2. `providers` визначає, що саме цей модуль створює у власному DI-scope.

#### `providers`: локальні визначення

1. Оголошує сервіси/фабрики/значення, які інстанціюються в контексті цього
   модуля.
2. Вони доступні для інжекції всередині самого модуля.
3. Не видимі для інших модулів, доки явно не експортовані.

Приклад:

```ts
@Module({
  providers: [UsersService],
})
export class UsersModule {}
```

#### `imports`: зовнішні залежності

1. Підключає інші модулі, щоб використовувати їхні **експортовані провайдери**.
2. Не копіює всі внутрішні провайдери імпортованого модуля.
3. Формує явний граф модульних залежностей.

Приклад:

```ts
@Module({
  imports: [UsersModule], // можна інжектити лише те, що UsersModule exports
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Комбінований приклад з exports

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

#### Практичне розрізнення

1. Додавайте в `providers`, коли ви **володієте залежністю і створюєте її тут**.
2. Додавайте в `imports`, коли залежністю **володіє інший модуль** і вона
   експортована.
3. Якщо інжекція не працює, перевірте:
   1. Провайдер зареєстрований у вихідному модулі в `providers`.
   2. Вихідний модуль експортує його через `exports`.
   3. Модуль-споживач підключає вихідний модуль через `imports`.

</details>

<details>
<summary>14. Що таке динамічні модулі і коли їх варто використовувати?</summary>

#### NestJS

Динамічні модулі - це модулі, конфігурація яких формується під час виконання
через статичні фабричні методи (зазвичай `forRoot`, `forRootAsync`,
`register`, `registerAsync`). Вони дають змогу створювати повторно
використовувані модулі з різними налаштуваннями для різних застосунків і
середовищ.

#### Навіщо існують динамічні модулі

1. **Runtime-конфігурація**
   Ви передаєте опції (URL, API-ключі, feature flags, вибір стратегії) під час
   імпорту модуля.

2. **Повторно використовувані інфраструктурні модулі**
   Один модуль можна використати в багатьох застосунках із різними
   налаштуваннями.

3. **Асинхронна ініціалізація**
   Можна підвантажувати конфіг із `ConfigService`, секрет-менеджерів або
   віддалених джерел.

4. **Умовні провайдери**
   Провайдери створюються залежно від переданих опцій (наприклад, Redis vs
   in-memory cache).

#### Типові API-патерни

1. `forRoot(options)` - для глобальної singleton-конфігурації застосунку.
2. `forRootAsync({...})` - коли конфіг залежить від async-фабрик або інжектованих
   залежностей.
3. `register(options)` - для feature-scope / per-import конфігурації.

#### Приклад

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

Використання:

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

#### Коли варто використовувати динамічні модулі

1. Для спільних інфраструктурних модулів (DB, mail, cache, queue, auth clients).
2. Коли потрібне environment-specific або tenant-specific налаштування.
3. Коли потрібен async-bootstrap із `ConfigModule` та інжектованими фабриками.

#### Коли вони не потрібні

1. Якщо конфігурація статична й локальна для застосунку, звичайні модулі
   простіші.
2. Якщо варіативність потрібна лише для одного провайдера, достатньо
   factory-провайдера.

</details>

<details>
<summary>15. Яка різниця provider types в NestJS? (useClass, useValue, useFactory)</summary>

#### NestJS

У NestJS провайдери можна реєструвати різними стратегіями залежно від того, як
саме має бути створений екземпляр/значення. Найпоширеніші: `useClass`,
`useValue` і `useFactory`.

#### 1) `useClass`

Створює екземпляр класу через DI-контейнер Nest.

1. Найкраще підходить для стандартних реалізацій сервісів.
2. Автоматично підтримує constructor injection.
3. Зручно для підміни реалізацій залежно від середовища.

```ts
{
  provide: PaymentPort,
  useClass: StripePaymentService,
}
```

#### 2) `useValue`

Прив'язує токен до готового значення/об'єкта/константи.

1. Nest не виконує інстанціювання.
2. Чудово підходить для config-об'єктів, SDK-синглтонів, моків у тестах.
3. Простий і швидкий підхід, але без DI-lifecycle для цього значення.

```ts
{
  provide: 'APP_CONFIG',
  useValue: { region: 'eu', retries: 3 },
}
```

#### 3) `useFactory`

Створює значення провайдера через фабричну функцію.

1. Дозволяє динамічно обчислювати об'єкт.
2. Може інжектити інші провайдери у фабрику (масив `inject`).
3. Працює як для синхронної, так і для асинхронної ініціалізації.

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

#### Швидке порівняння

1. **`useClass`**: "Інстанціюй цей клас через DI."
2. **`useValue`**: "Використовуй це значення як є."
3. **`useFactory`**: "Побудуй значення кастомною логікою (і за потреби з
   інжектованими залежностями)."

#### Коли що обирати

1. Обирайте `useClass` для звичайних сервісів застосунку та поліморфних
   реалізацій.
2. Обирайте `useValue` для констант, сторонніх інстансів і test doubles.
3. Обирайте `useFactory` для умовного/асинхронного створення та складного
   bootstrap.

#### Практична примітка

Усі три стратегії резолвляться через **токен** (`provide`). Якісний дизайн
токенів (class token, symbol або string-constant) критично важливий для
підтримуваного DI.

</details>

<details>
<summary>16. Що таке scope провайдера? (DEFAULT, REQUEST, TRANSIENT)</summary>

#### NestJS

Scope провайдера в NestJS визначає, **скільки живе екземпляр провайдера** і
**як часто створюються нові екземпляри** DI-контейнером.

#### Типи scope

1. **`DEFAULT` (singleton)**
   Один спільний екземпляр на весь життєвий цикл застосунку.

2. **`REQUEST`**
   Новий екземпляр для кожного вхідного запиту (HTTP/RPC/message context).

3. **`TRANSIENT`**
   Новий екземпляр щоразу, коли провайдер інжектиться/резолвиться.

#### 1) `DEFAULT` scope

1. Найпродуктивніший і найпоширеніший.
2. Ідеальний для stateless-сервісів (бізнес-логіка, репозиторії, мапери).
3. Спільний стан усередині такого сервісу є глобальним для процесу застосунку.

```ts
@Injectable()
export class UsersService {}
```

#### 2) `REQUEST` scope

1. Використовуйте, коли сервіс має бути request-aware (tenant, correlation ID,
   per-request cache, user context).
2. Підвищує накладні витрати на створення об'єктів.
3. Якщо singleton залежить від request-scoped провайдера, граф залежностей може
   вимагати додаткового scope propagation налаштування.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.REQUEST })
export class RequestContextService {}
```

#### 3) `TRANSIENT` scope

1. Свіжий екземпляр для кожної точки інжекції.
2. Корисний для легковагових stateful-хелперів, де спільний екземпляр
   небажаний.
3. Може бути дорогим за ресурсами, якщо зловживати ним у глибоких графах
   залежностей.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.TRANSIENT })
export class AuditBuilder {}
```

#### Практичний гайд вибору

1. Починайте з `DEFAULT`.
2. Переходьте на `REQUEST` лише за реальною потребою в per-request стані.
3. Використовуйте `TRANSIENT` для вузькоспеціалізованих mutable-хелперів.

#### Примітка про продуктивність і архітектуру

Scope - це одночасно питання коректності та продуктивності. Надмірне
використання non-singleton scope може збільшити latency і memory churn, тому
застосовуйте їх свідомо.

</details>

<details>
<summary>17. Як працювати з циклічними залежностями (forwardRef) у великих системах?</summary>

#### NestJS

Циклічні залежності виникають, коли два провайдери/модулі залежать один від
одного напряму або через ланцюжок. У NestJS першочерговий підхід - архітектурне
розв'язання зв'язності; `forwardRef()` - це тактичний інструмент, коли
рефакторинг неможливо зробити одразу.

#### Чому циклічні залежності ризиковані

1. Тісна зв'язаність між доменами.
2. Складніше тестувати й рефакторити.
3. Нечіткі межі відповідальності.
4. Ускладнення bootstrap/DI-резолву.

#### Бажана стратегія: прибрати цикл

1. **Винесення спільної логіки**
   Перенесіть спільну поведінку в третій сервіс/модуль (`SharedDomainService`).

2. **Залежність від абстрактних токенів**
   Замініть пряму залежність від класу на interface-like токен + адаптер.

3. **Domain events / async messaging**
   Публікуйте подію з A і обробляйте її в B замість прямого виклику.

4. **Перерозрізання модульних меж**
   Перебудуйте межі за use-case/доменами так, щоб залежності були односпрямовані.

#### `forwardRef()` для неминучих випадків

Використовуйте `forwardRef()`, коли два провайдери/модулі повинні посилатися один
на одного під час DI-резолву.

Приклад на рівні провайдерів:

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

Приклад на рівні модулів:

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

#### Рекомендації для великих систем

1. Сприймайте `forwardRef()` як тимчасове/виняткове рішення, а не стандарт.
2. Відстежуйте циклічні залежності в архітектурних рев'ю та прибирайте їх
   поступово.
3. Додавайте тести навколо cycle-critical сценаріїв до рефакторингу.
4. Віддавайте перевагу односпрямованому графу залежностей між bounded contexts.

</details>

<details>
<summary>18. Як структурувати масштабований застосунок на NestJS?</summary>

#### NestJS

Масштабований застосунок на NestJS будується навколо чітких доменних меж,
керованого напряму залежностей і передбачуваних наскрізних патернів.

#### Базові принципи структури

1. **Модульність за доменом (bounded contexts)**
   Діліть систему за бізнес-можливостями (`Users`, `Billing`, `Orders`), а не
   лише за технічними шарами.

2. **Шарова відповідальність усередині модуля**
   Контролери - "тонкі", сервіси - оркеструють use-case-и, інфраструктурні
   адаптери - ізольовані.

3. **Правило залежностей**
   Вищий рівень бізнес-логіки не має напряму залежати від
   framework/infrastructure деталей.

4. **Явні контракти**
   Використовуйте DTO, схеми валідації та interfaces/tokens для чітких меж.

#### Практичний layout модулів (приклад)

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

#### Архітектурні патерни, що масштабуються

1. **Feature-модулі + shared kernel**
   Тримайте shared-утиліти мінімальними, щоб уникнути "god common module".

2. **Ports and adapters**
   Бізнес-шар залежить від абстракцій, а адаптери реалізують деталі DB/API/message-bus.

3. **CQRS - там, де це виправдано складністю**
   Розділяйте write/read моделі для складних доменів, а не за замовчуванням
   всюди.

4. **Async-boundaries**
   Використовуйте events/queues для міжмодульних workflow і eventual consistency.

#### Операційні аспекти масштабованості

1. **Керування конфігурацією**
   Централізований типізований конфіг із валідацією середовищ.

2. **Спостережуваність**
   Structured logging, tracing, metrics і correlation IDs.

3. **Стратегія помилок**
   Глобальні exception filters + domain-specific мапінг помилок.

4. **Продуктивність**
   Кешування, пагінація, backpressure, індекси БД і уникнення надмірного
   request-scope.

#### Практики масштабованості команди

1. Впроваджуйте lint/format/type/test gate-и в CI.
2. Фіксуйте ownership модулів (codeowners або map відповідальностей сервісів).
3. Переглядайте архітектурні рішення (ADR) для нових cross-domain залежностей.
4. Віддавайте перевагу інкрементальному рефакторингу замість big-bang перепису.

#### Підсумок

Масштабованість у NestJS - це насамперед архітектурна дисципліна: доменно
орієнтовані модулі, контрольований граф залежностей і стандартизовані платформні
підходи навколо них.

</details>

<details>
<summary>19. Як проєктувати REST API з правильною декомпозицією відповідальностей?</summary>

#### NestJS

Коректна декомпозиція відповідальностей у REST API на NestJS означає, що кожен
шар має одну чітку роль, а залежності рухаються в одному напрямку.

#### Рекомендований поділ відповідальностей

1. **Controller layer (transport)**
   Працює лише з HTTP-аспектами: routing, status codes, мапінг
   request/response, auth-декоратори та прив'язка вхідних даних.

2. **Application/service layer (use cases)**
   Оркеструє бізнес-процеси й транзакції; не містить HTTP-специфічної логіки.

3. **Domain layer (business rules)**
   Інкапсулює ключові правила, інваріанти, entities/value objects і domain
   services.

4. **Infrastructure layer**
   Реалізує persistence, зовнішні API, queues та інші адаптери.

#### Що НЕ можна змішувати

1. Запити до БД у контролерах.
2. HTTP-об'єкти (`Request`, `Response`) у domain-логіці.
3. Валідацію/бізнес-інваріанти, розкидані по різних шарах.
4. Деталі зовнішніх SDK, що "просочуються" в use-case контракти.

#### Практичний потік

1. Контролер отримує DTO (`@Body`, `@Query`, `@Param`).
2. Pipe валідовує/трансформує DTO.
3. Контролер викликає метод application service.
4. Сервіс використовує repositories/ports і domain-правила.
5. Сервіс повертає result model.
6. Контролер мапить результат у response DTO/view model.

#### Skeleton-приклад

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

#### Дизайн-техніки, що допомагають

1. **DTO для API-контрактів**
   Розділяйте вхідні/вихідні контракти та внутрішні сутності.

2. **Repository/port interfaces**
   Залежіть від абстракцій, а не від ORM-клієнтів напряму в бізнес-шарі.

3. **Глобальні наскрізні компоненти**
   Використовуйте guards/pipes/interceptors/filters для auth, валідації,
   логування та помилок.

4. **Versioning та idempotency**
   Застосовуйте стратегію версіонування API й idempotency keys для небезпечних
   операцій.

5. **Консистентна error-модель**
   Мапте domain/infrastructure помилки на стабільні HTTP problem responses.

#### Результат

За такої декомпозиції API простіше тестувати, рефакторити й масштабувати:
зміни transport-шару не ламають domain-логіку, а інфраструктура може еволюціонувати
незалежно.

</details>

<details>
<summary>20. Який повний життєвий цикл запиту в NestJS?</summary>

#### NestJS

Життєвий цикл запиту в NestJS - це детермінований pipeline навколо
зіставленого route-handler-а. Розуміння цього порядку критично важливе для
дебагу auth, validation і логіки формування відповіді.

#### Високорівнева послідовність

1. Вхідний запит потрапляє в платформний адаптер (Express/Fastify).
2. Маршрут зіставляється з методом контролера.
3. Nest виконує framework-компоненти pipeline у визначеному порядку.
4. Повертається відповідь (або виняток обробляється filters).

#### Детальний порядок lifecycle

1. **Middleware**
   Працює до guards; використовується для низькорівневої pre-processing логіки
   (логування, correlation ID, робота із "сирими" заголовками тощо).

2. **Guards**
   Вирішують, чи дозволено продовжувати виконання (`canActivate`).
   Якщо guard повертає `false`/кидає помилку, запит зупиняється тут.

3. **Interceptors (before handler)**
   Обгортають виконання; можуть запускати таймери, додавати контекст або
   short-circuit поведінку.

4. **Pipes**
   Працюють над аргументами роута для трансформації/валідації вхідних даних
   (`@Body`, `@Param`, `@Query`, custom params).

5. **Controller handler**
   Виконується бізнес-use-case (зазвичай через делегування в service layer).

6. **Interceptors (after handler)**
   Можуть мапити/стрімити/кешувати відповіді та завершувати observability-логіку.

7. **Exception filters**
   Перехоплюють необроблені винятки й перетворюють їх на HTTP-відповідь.

#### Візуальна модель виконання

1. Middleware -> Guards -> Interceptors (pre) -> Pipes -> Handler ->
   Interceptors (post) -> Response
2. Будь-яка помилка в pipeline/handler -> Exception Filters

#### Нотатки про scope і пріоритет

1. Більшість pipeline-компонентів можна застосувати на:
   1. Global level
   2. Controller level
   3. Route-handler level
2. Nest об'єднує ці рівні; конфігурація рівня роута зазвичай найспецифічніша.

#### Практичний висновок для дебагу

Якщо поведінка неочікувана:
1. Спершу перевірте, чи запит не блокується guard-ом.
2. Перевірте трансформацію/валідацію параметрів у pipes.
3. Перегляньте interceptor-ланцюжок на предмет змін response mapping.
4. Підтвердьте форматування помилок у exception filters.

Знання цього порядку прибирає "магічні" припущення й значно пришвидшує діагностику
production-інцидентів.

</details>

<details>
<summary>21. У чому різниця між Middleware, Guards, Pipes та Interceptors?</summary>

#### NestJS

Усі чотири компоненти NestJS беруть участь в обробці запиту, але мають різні
зони відповідальності та працюють на різних етапах lifecycle.

#### Коротке порівняння ролей

1. **Middleware**
   HTTP-preprocessing до маршрутизації/handler-а.

2. **Guards**
   Authorization gate: вирішують, чи може запит продовжити виконання.

3. **Pipes**
   Трансформують і валідовують аргументи handler-а.

4. **Interceptors**
   Обгортають виконання handler-а до/після, даючи наскрізну логіку для відповіді.

#### Глибша різниця за відповідальністю

1. **Middleware**
   Найкраще підходить для загальних transport-level задач: request logging,
   correlation IDs, headers, cookie parsing, мутація "сирого" request.

2. **Guards**
   Найкраще підходять для auth/authz-рішень: наявність JWT, role checks,
   policy checks. Повертають `true/false` (або кидають помилку), щоб
   дозволити/заборонити виконання роута.

3. **Pipes**
   Найкраще підходять для коректності входу: parsing (`string -> number`),
   validation (DTO-правила), sanitization/normalization на рівні параметрів.

4. **Interceptors**
   Найкраще підходять для execution-wrapping: response mapping, caching,
   вимірювання метрик, tracing, timeout/retry-обгортки, stream-handling.

#### Позиція у lifecycle

1. Middleware
2. Guards
3. Interceptors (before)
4. Pipes
5. Handler
6. Interceptors (after)
7. Exception filters (error path)

#### Типові приклади

1. Middleware: додати `requestId`.
2. Guard: відхилити запит, якщо токен невалідний.
3. Pipe: валідовувати `CreateUserDto`.
4. Interceptor: трансформувати envelope відповіді у вигляд `{ data, meta }`.

#### Практичне правило вибору

1. Потрібно вирішити, **хто має доступ**? -> Guard.
2. Потрібно гарантувати **форму/тип вхідних даних**? -> Pipe.
3. Потрібно **обгорнути виконання до/після handler-а**? -> Interceptor.
4. Потрібен низькорівневий HTTP-preprocessing поза route-семантикою? ->
   Middleware.

</details>

<details>
<summary>22. Як застосувати Middleware глобально vs для конкретного роуту?</summary>

#### NestJS

У NestJS middleware можна застосовувати або глобально (для багатьох/усіх
роутів), або вибірково (для конкретних контролерів/роутів). На відміну від
guards та interceptors, middleware налаштовується через module consumer API або
під час bootstrap.

#### 1) Глобальне застосування middleware

Використовуйте, коли поведінка потрібна майже для кожного запиту
(request IDs, базове логування, ініціалізація security headers тощо).

Глобальна конфігурація на рівні модуля:

```ts
import { MiddlewareConsumer, Module, NestModule } from '@nestjs/common';

@Module({})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer.apply(LoggerMiddleware).forRoutes('*');
  }
}
```

Можна також таргетувати всі контролери через class-based патерни в
`forRoutes(...)`.

#### 2) Middleware для конкретних роутів/контролерів

Використовуйте для feature-specific задач.

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
        UsersController, // усі роути контролера
        { path: 'users/:id', method: RequestMethod.PATCH }, // точковий роут
      );
  }
}
```

#### Виключення роутів

Можна застосувати широке middleware і виключити чутливі/публічні endpoint-и:

```ts
consumer
  .apply(AuthMiddleware)
  .exclude(
    { path: 'health', method: RequestMethod.GET },
    { path: 'auth/login', method: RequestMethod.POST },
  )
  .forRoutes('*');
```

#### Практичні рекомендації

1. Використовуйте глобальний middleware лише для справді наскрізних задач.
2. Тримайте middleware легким; важка authz-логіка має жити в Guards.
3. Для локальної поведінки конкретної фічі використовуйте route-specific
   middleware.
4. Якщо потрібні DI-heavy бізнес-перевірки, переносіть логіку з middleware в
   Guards або Interceptors.

</details>

<details>
<summary>23. Що таке ExecutionContext і як він використовується?</summary>

#### NestJS

`ExecutionContext` - це абстракція NestJS, яка описує поточне середовище
виконання handler-а. Вона розширює `ArgumentsHost` і дає framework-компонентам
(Guards, Interceptors, Filters, custom decorators) уніфікований спосіб доступу до
даних запиту в різних транспортах.

#### Навіщо потрібен `ExecutionContext`

1. **Transport-agnostic доступ**
   Той самий API-підхід працює для HTTP, WebSockets і мікросервісів.

2. **Інтроспекція handler-а/класу**
   Можна визначити, який саме клас контролера та метод зараз виконуються.

3. **Консистентність наскрізних компонентів**
   Guards/interceptors/filters можуть працювати в єдиній моделі контексту.

#### Ключові API

1. `context.getType()`
   Повертає тип виконання (`http`, `ws`, `rpc`).

2. `context.switchToHttp()`
   Дає доступ до `getRequest()`, `getResponse()`, `getNext()`.

3. `context.switchToWs()` / `context.switchToRpc()`
   Доступ до transport-specific даних для websockets/мікросервісів.

4. `context.getClass()` і `context.getHandler()`
   Повертають поточний клас контролера та посилання на метод.

#### Типове використання в Guard

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

#### Поширене використання з metadata + Reflector

```ts
const isPublic = this.reflector.getAllAndOverride<boolean>('isPublic', [
  context.getHandler(),
  context.getClass(),
]);
```

Цей патерн читає метадані роута/класу (наприклад, `@Public()`, `@Roles(...)`) і
широко застосовується в authorization guards.

#### Практичний висновок

Сприймайте `ExecutionContext` як runtime-обгортку фреймворку для поточного
endpoint-виклику: він показує, **де ви знаходитесь** (handler/class/transport) і
дозволяє безпечно отримувати transport-specific дані запиту.

</details>

<details>
<summary>24. Що таке Guard і чим він відрізняється від Middleware?</summary>

#### NestJS

**Guard** у NestJS - це клас, що реалізує `CanActivate` і вирішує, чи дозволено
поточному запиту дійти до route-handler-а.

#### Що робить Guard

1. Виконується перед запуском handler-а.
2. Повертає `true`, щоб дозволити, і `false` (або кидає помилку), щоб
   заборонити доступ.
3. Має доступ до `ExecutionContext` (handler, controller, transport, request).
4. Найчастіше використовується для аутентифікації та авторизації.

#### Чим Guard відрізняється від Middleware

1. **Призначення рішення**
   Guard - явний authorization gate.
   Middleware - загальний request preprocessing.

2. **Обізнаність про фреймворк**
   Guard знає цільовий handler/class через `ExecutionContext`.
   Middleware зазвичай не має контексту метаданих route-handler-а.

3. **Позиція в lifecycle**
   Middleware виконується раніше.
   Guard виконується після middleware, але до pipes/interceptors/handler-а.

4. **Типові use-case-и**
   Guard: JWT/roles/policies.
   Middleware: логування, request IDs, нормалізація заголовків, мутація "сирого"
   request.

#### Приклад Guard

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

#### Практичне правило

1. Потрібно вирішити "чи може цей користувач отримати доступ до цього роута?" ->
   **Guard**.
2. Потрібна низькорівнева HTTP-preprocessing логіка до handler-а незалежно від
   route-семантики -> **Middleware**.

</details>

<details>
<summary>25. Як Guards інтегрується з авторизацією?</summary>

#### NestJS

Guards - це основний authorization gate у NestJS. Вони перевіряють, чи може
поточний автентифікований principal отримати доступ до конкретного роута,
зазвичай поєднуючи identity запиту з route-метаданими (roles, policies,
permissions).

#### Типовий потік авторизації через Guards

1. **Крок автентифікації**
   Попередній guard (або Passport strategy) валідовує токен/сесію і додає
   `request.user`.

2. **Оголошення метаданих на роуті**
   Роут анотується вимогами, наприклад `@Roles('admin')` або policy-ключами.

3. **Оцінка авторизації guard-ом**
   Guard читає метадані через `Reflector` + читає `request.user` і приймає
   рішення щодо доступу.

4. **Дозвіл або відмова**
   Повертає `true`, щоб продовжити виконання, або `false`/кидає
   `ForbiddenException`, щоб заборонити доступ.

#### Role-based приклад (RBAC)

Roles-декоратор:

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

Використання:

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Інтеграційні патерни в реальних системах

1. **Stacked guards**
   `JwtAuthGuard` (identity) + `Roles/PoliciesGuard` (authorization-логіка).

2. **ABAC/policy engine**
   Guard делегує рішення policy-сервісу (subject, action, resource).

3. **Context-aware перевірки**
   Guard читає route params/resource owner і застосовує ownership-правила.

#### Найкращі практики

1. Тримайте guards "тонкими"; важку логіку переносіть у dedicated
   authorization-сервіси.
2. Використовуйте metadata-декоратори для декларативних і audit-friendly правил
   доступу.
3. Розділяйте помилки автентифікації (`401`) і авторизації (`403`).
4. Тестуйте guards як на позитивних, так і на негативних permission-сценаріях.

</details>

<details>
<summary>26. Що таке @SetMetadata() і як він працює з Guards через Reflector?</summary>

#### NestJS

`@SetMetadata()` - це допоміжний декоратор NestJS для прикріплення кастомних
метаданих до класу або методу. Потім Guards можуть читати ці метадані через
`Reflector` і застосовувати авторизацію або іншу route-specific поведінку.

#### Базова ідея

1. `@SetMetadata(key, value)` записує метадані на роут/клас.
2. Guard читає метадані через `Reflector` під час виконання.
3. Guard приймає рішення, чи дозволяти запит.

#### Чому цей патерн важливий

1. **Декларативні правила доступу**
   Вимоги до доступу видно безпосередньо в endpoint-ах.

2. **Розділення відповідальностей**
   Контролер декларує намір, а guard реалізує логіку контролю доступу.

3. **Повторне використання**
   Один guard може обслуговувати багато роутів із різними metadata-значеннями.

#### Приклад: roles-метадані

Декоратор:

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Використання на endpoint-і:

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

Guard, що читає метадані:

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(), // метадані методу
      context.getClass(),   // метадані контролера
    ]);

    if (!requiredRoles) return true;

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];
    return requiredRoles.some(role => userRoles.includes(role));
  }
}
```

#### Методи `Reflector`, які використовуються найчастіше

1. `get(key, target)` -> читає метадані з конкретної цілі.
2. `getAllAndOverride(key, [handler, class])` -> метадані методу мають пріоритет
   над метаданими класу.
3. `getAllAndMerge(key, [handler, class])` -> об'єднує значення з обох рівнів.

#### Практичний висновок

`@SetMetadata()` + `Reflector` - стандартний механізм NestJS для побудови чистих,
масштабованих, metadata-driven правил авторизації та поведінки роутів.

</details>

<details>
<summary>27. Як реалізувати JWT аутентифікацію через Guard?</summary>

#### NestJS

JWT-аутентифікація в NestJS зазвичай реалізується через Guard, який валідовує
токен і прикріплює user identity до контексту запиту.

#### Стандартна архітектура

1. **AuthService**
   Підписує та верифікує JWT.

2. **JWT strategy/guard**
   Витягує bearer token, валідовує його і записує `request.user`.

3. **Захищені роуты**
   Використовують `@UseGuards(...)`, щоб вимагати аутентифікацію.

Реалізувати це можна через Passport (`@nestjs/passport`) або кастомним guard-ом.

#### Мінімальний кастомний JWT Guard (без Passport)

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
      req.user = payload; // прикріплюємо identity для наступних handlers/guards
      return true;
    } catch {
      throw new UnauthorizedException('Invalid or expired token');
    }
  }
}
```

#### Захист роутів

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

#### Налаштування `JwtModule`

```ts
JwtModule.register({
  secret: process.env.JWT_ACCESS_SECRET,
  signOptions: { expiresIn: '15m' },
});
```

#### Production best practices

1. Використовуйте окремі secrets для access і refresh токенів.
2. Робіть access tokens короткоживучими.
3. Явно валідовуйте issuer/audience/algorithm.
4. Для token-failure віддавайте `401 Unauthorized`.
5. Поєднуйте з authorization guard-ом (roles/policies) для permissions.
6. Додавайте стратегію відкликання токенів за потреби
   (blacklist/versioning/rotation).

#### Практична примітка

У великих застосунках зв'язка Passport `AuthGuard('jwt')` + `JwtStrategy`
часто чистіша для повторного використання та інтеграції з екосистемою, але
базовий принцип той самий: extract -> verify -> attach user -> allow/deny.

</details>

<details>
<summary>28. Як у NestJS реалізувати RBAC та ABAC і коли який підхід краще використовувати?</summary>

#### NestJS

RBAC і ABAC - це дві моделі авторизації, які в NestJS можна реалізувати через
Guards + metadata + authorization services.

#### RBAC vs ABAC

1. **RBAC (Role-Based Access Control)**
   Доступ надається на основі ролей користувача (наприклад, `admin`, `editor`,
   `viewer`).

2. **ABAC (Attribute-Based Access Control)**
   Доступ визначається через оцінку атрибутів (user, resource, action, context):
   ownership, department, region, status, time window тощо.

#### Коли яка модель краща

1. Обирайте **RBAC**, коли:
   1. Permission-модель проста й стабільна.
   2. Ієрархія ролей чітко визначена.
   3. Пріоритет - швидка реалізація та простий аудит.

2. Обирайте **ABAC**, коли:
   1. Правила залежать від даних ресурсу та контексту.
   2. Потрібні fine-grained, динамічні рішення.
   3. Висока складність політик у multi-tenant або enterprise-середовищі.

3. У більшості реальних систем використовуйте **гібрид RBAC + ABAC**:
   RBAC для грубого контролю доступу, ABAC - для чутливих операцій.

#### Патерн реалізації RBAC у NestJS

1. Декоратор `@Roles(...)` через `SetMetadata`.
2. `RolesGuard` читає метадані через `Reflector`.
3. Guard порівнює потрібні ролі з `request.user.roles`.

```ts
export const Roles = (...roles: string[]) => SetMetadata('roles', roles);
```

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Патерн реалізації ABAC у NestJS

1. Визначте policy ability service (`can(user, action, resource)`).
2. У guard-і завантажте цільовий ресурс (або достатній набір атрибутів).
3. Оцініть policy і дозвольте/забороніть доступ.

```ts
@Injectable()
export class PoliciesGuard implements CanActivate {
  constructor(private readonly policy: PolicyService) {}

  async canActivate(ctx: ExecutionContext): Promise<boolean> {
    const req = ctx.switchToHttp().getRequest();
    const user = req.user;
    const order = await req.orderLoader.load(req.params.id); // приклад
    return this.policy.can(user, 'update', order);
  }
}
```

#### Best practices у дизайні

1. Тримайте guard "тонким"; rule-логіку делегуйте в dedicated policy service.
2. Уникайте hardcode правил у контролерах.
3. Кешуйте policy-relevant lookup-и там, де це безпечно.
4. Для відмов авторизації повертайте `403 Forbidden` (а не `401`).
5. Логуйте контекст рішення для auditability у критичних доменах.

#### Практична рекомендація

Починайте з RBAC для базової швидкості реалізації, а потім додавайте ABAC у
high-risk/high-variance потоках (ownership checks, чутливість даних, межі
тенантів, умовні дії).

</details>

<details>
<summary>29. Як реалізувати refresh token rotation і чому це важливо?</summary>

#### NestJS

Refresh token rotation означає, що під час кожного refresh-запиту видається
**новий refresh token**, а попередній інвалідовується. Це зменшує replay-ризик,
якщо refresh token було скомпрометовано.

#### Чому це важливо

1. Обмежує наслідки витоку refresh token.
2. Дозволяє виявляти reuse-атаки (коли вкрадений старий токен використовується
   повторно).
3. Дає безпечні довготривалі сесії без довгоживучих access token.
4. Покращує контроль сесій між пристроями.

#### Рекомендована токен-модель

1. **Access token**: короткий TTL (наприклад, 5-15 хв), stateless JWT.
2. **Refresh token**: довший TTL (дні/тижні), ротується при кожному використанні.
3. У БД зберігайте лише **хеш refresh token** (або metadata token family).
4. Відстежуйте token family/session (`sessionId`, `jti`, `rotatedFrom`,
   `revokedAt`).

#### Потік ротації в NestJS

1. Користувач логіниться -> видаються access + refresh token (RT1), у сховищі
   зберігається хеш RT1 + metadata.
2. Клієнт викликає `/auth/refresh` з RT1.
3. Сервер перевіряє підпис/строк дії і порівнює хеш із активним токеном у
   сховищі.
4. Якщо все валідно:
   1. Ревокується RT1.
   2. Видаються AT2 + RT2.
   3. Хеш RT2 зберігається як активний токен цієї сесії.
5. Якщо старий RT1 використовується повторно:
   1. Позначається підозра на reuse.
   2. Ревокується вся session/token family.
   3. Форсується повторна автентифікація.

#### Мінімальний sketch на рівні сервісу

```ts
async rotateRefreshToken(userId: string, presentedRt: string, sessionId: string) {
  const session = await this.sessionsRepo.findById(sessionId);
  if (!session || session.revokedAt) throw new UnauthorizedException();

  const matches = await this.hash.compare(presentedRt, session.refreshTokenHash);
  if (!matches) {
    await this.sessionsRepo.revokeFamily(session.familyId); // реакція на reuse
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

#### Примітки реалізації в NestJS

1. Використовуйте окремі `JwtModule` config/secrets для access і refresh токенів.
2. Захистіть refresh endpoint через refresh-token guard/strategy.
3. За можливості зберігайте refresh token у захищеному httpOnly cookie.
4. Додайте таблицю device/session для multi-device logout і ревокації.

#### Security best practices

1. Хешуйте refresh tokens у сховищі.
2. Прив'язуйте refresh token до metadata сесії/пристрою.
3. Ротуйте токен на **кожен** refresh-запит, без винятків.
4. Ревокуйте token family при виявленні reuse.
5. Логуйте rotation/reuse події для security-моніторингу.

</details>

<details>
<summary>30. Що таке Pipe у NestJS і коли його використовувати?</summary>

#### NestJS

Pipe у NestJS - це клас, який реалізує `PipeTransform` і виконується перед
route-handler-ом для **трансформації** та/або **валідації** вхідних даних.

#### Що роблять Pipes

1. **Трансформація**
   Перетворюють "сирі" transport-значення в очікувані типи
   (наприклад, string -> number, string -> UUID object, trimming/normalization).

2. **Валідація**
   Застосовують DTO/schema-правила і відхиляють невалідний вхід на ранньому
   етапі.

3. **Fail-fast поведінка**
   Кидають помилку (зазвичай `BadRequestException`) до виконання бізнес-логіки.

#### Де Pipes розташовані в lifecycle

1. Middleware
2. Guards
3. Interceptors (pre)
4. **Pipes**
5. Handler
6. Interceptors (post)
7. Exception filters

#### Приклади вбудованих pipes

1. `ValidationPipe`
2. `ParseIntPipe`
3. `ParseBoolPipe`
4. `ParseUUIDPipe`
5. `DefaultValuePipe`
6. `ParseArrayPipe`

#### Приклади використання

На рівні параметра:

```ts
@Get(':id')
findOne(@Param('id', ParseIntPipe) id: number) {
  return this.usersService.findOne(id);
}
```

Глобальна валідація:

```ts
app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
    forbidNonWhitelisted: true,
    transform: true,
  }),
);
```

#### Приклад кастомного Pipe

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

#### Коли використовувати Pipes

1. Для валідації request DTO і query/param payloads.
2. Для парсингу примітивних route/query параметрів у типізовані значення.
3. Для централізації правил нормалізації входу.
4. Щоб прибрати повторюваний validation/parsing код із контролерів і сервісів.

#### Практичне правило

Використовуйте Pipes для **коректності вхідних даних**, Guards - для
**контролю доступу**, Interceptors - для **обгортки виконання**, а Middleware -
для **низькорівневого request preprocessing**.

</details>

<details>
<summary>31. Що таке DTO?</summary>

#### NestJS

DTO (Data Transfer Object) - це структура даних, яка використовується для
передавання інформації між межами застосунку, найчастіше між клієнтом і вашим
API-шаром.

У NestJS DTO зазвичай реалізуються як **класи**, щоб підтримувати runtime
валідацію і трансформацію через `class-validator` та `class-transformer`.

#### Чому DTO важливі

1. **Явні API-контракти**
   Визначають точно, які поля дозволені на вході/виході.

2. **Validation boundary**
   Відхиляють malformed або небезпечні payload-и до виконання бізнес-логіки.

3. **Декуплінг**
   Запобігають прямому витоку domain entities/ORM-моделей назовні.

4. **Підтримуваність**
   Чіткі схеми запитів/відповідей роблять рефакторинг безпечнішим, а
   документацію - зрозумілішою.

#### Типові типи DTO у NestJS

1. **Request DTOs**
   `CreateUserDto`, `UpdateUserDto`, query/filter DTOs.

2. **Response/View DTOs**
   Контрольована форма виходу (приховує внутрішні поля: паролі, токени, прапори).

3. **Command-style DTOs**
   Входи для конкретних use-case-ів (особливо в CQRS-підході).

#### Приклад request DTO

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

Використання в контролері:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Практичні правила

1. Ніколи не використовуйте "сирі" `any` payload-и в контролерах.
2. Тримайте DTO transport-focused (а не як повні domain entities).
3. Розділяйте input DTO та output DTO.
4. Поєднуйте DTO з глобальним `ValidationPipe` для консистентного enforcement.

</details>

<details>
<summary>32. Чим відрізняється interface від class для типізації DTO — і чому в NestJS краще class?</summary>

#### NestJS

І interfaces, і classes можуть описувати структури TypeScript, але в NestJS DTO
зазвичай реалізують як **класи**, оскільки валідація/трансформація працює на
runtime-рівні, а не лише на compile-time.

#### Ключова різниця

1. **Interface**
   Існує тільки на етапі компіляції TypeScript і видаляється на runtime.

2. **Class**
   Існує на runtime як реальний constructor/function object і може нести
   decorator-метадані, які використовує Nest.

#### Чому в NestJS для DTO краще class

1. **Підтримка runtime-валідації**
   Декоратори `class-validator` (`@IsEmail`, `@IsString` тощо) вішаються на поля
   класу й використовуються `ValidationPipe`.

2. **Підтримка трансформації**
   `class-transformer` може інстанціювати/трансформувати plain payload у
   class-екземпляри (`transform: true` у `ValidationPipe`).

3. **Інтеграція з OpenAPI/Swagger**
   DTO-класи надають метадані для генерації схем у `@nestjs/swagger`.

4. **Підтримка mapped types**
   `PartialType`, `PickType`, `OmitType`, `IntersectionType` працюють із класами.

#### Практичний приклад

Interface (лише тип, без runtime-метаданих):

```ts
interface CreateUserDto {
  email: string;
}
```

Class DTO (runtime + декоратори):

```ts
import { IsEmail } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;
}
```

З глобальною валідацією:

```ts
app.useGlobalPipes(new ValidationPipe({ whitelist: true, transform: true }));
```

Лише class-based DTO може бути валідований/трансформований через
decorator-метадані.

#### Коли interfaces все ще доречні

1. Для внутрішніх service-контрактів, де не потрібна runtime-reflection.
2. Для generic utility typing і domain-абстракцій.
3. Для read-only compile-time меж, де валідацію виконують в іншому місці.

#### Практичне правило

Використовуйте **classes для зовнішніх API DTO** (input/output контракти
контролерів). Використовуйте interfaces для внутрішніх compile-time контрактів,
де runtime-метадані не потрібні.

</details>

<details>
<summary>33. Що таке mapped types у NestJS? (PartialType, OmitType, PickType, IntersectionType)</summary>

#### NestJS

Mapped types у NestJS - це утиліти, що генерують нові DTO-класи на основі
наявних, зменшуючи дублювання й зберігаючи metadata для валідації/Swagger.

Зазвичай імпортуються з:
1. `@nestjs/mapped-types` (framework-agnostic використання)
2. `@nestjs/swagger` (коли використовуєте Swagger і schema-декоратори)

#### Чому mapped types корисні

1. Прибирають повторювані визначення DTO.
2. Підтримують консистентність між create/update DTO.
3. Зберігають decorator-метадані для validation/docs.
4. Роблять еволюцію API-контракту безпечнішою.

#### Основні mapped types

1. **`PartialType(BaseDto)`**
   Робить усі поля опційними.
   Типовий use-case: `UpdateDto` на базі `CreateDto`.

2. **`PickType(BaseDto, ['a', 'b'])`**
   Залишає лише вибрані поля.
   Типовий use-case: "вузький" input для конкретного endpoint-а.

3. **`OmitType(BaseDto, ['x'])`**
   Прибирає вибрані поля.
   Типовий use-case: приховати заборонені input-поля на кшталт `role`, `id`.

4. **`IntersectionType(A, B)`**
   Об'єднує поля двох DTO-класів.
   Типовий use-case: складені query DTO для filter/pagination.

#### Приклад

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

#### Практичні застереження

1. Mapped types працюють із class-метаданими; базовий DTO має бути класом.
2. Тримайте DTO-наслідування читабельним; уникайте глибоких заплутаних ланцюжків.
3. Перевіряйте згенеровану OpenAPI-схему після складних `IntersectionType`.

#### Практичне правило

Використовуйте mapped types для повторного використання контрактів, особливо
`Create` -> `Update`, зберігаючи DTO-ієрархію простою та явною.

</details>

<details>
<summary>34. Як реалізувати валідацію за допомогою class-validator і pipes?</summary>

#### NestJS

У NestJS валідація зазвичай реалізується через:
1. DTO-класи з декораторами `class-validator`.
2. `ValidationPipe` (глобально або на рівні роута), який застосовує правила на
   runtime.

#### Крок 1: Описати DTO з validation-декораторами

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

#### Крок 2: Увімкнути `ValidationPipe`

Глобальне налаштування (рекомендовано):

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

#### Що роблять ці опції

1. `whitelist: true`
   Видаляє поля, яких немає в DTO.

2. `forbidNonWhitelisted: true`
   Кидає помилку, якщо присутні невідомі поля.

3. `transform: true`
   Перетворює payload у DTO-екземпляр і застосовує type transformation.

4. `enableImplicitConversion: true`
   Дозволяє безпечну неявну конвертацію примітивів за типами DTO-полів.

#### Крок 3: Використати DTO в контролері

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Route-level валідація (коли потрібно)

```ts
@Post('strict')
@UsePipes(new ValidationPipe({ whitelist: true, forbidNonWhitelisted: true }))
createStrict(@Body() dto: CreateUserDto) {}
```

#### Типова відповідь при помилці валідації

1. HTTP `400 Bad Request`
2. Масив повідомлень із failed constraints
3. Зрозуміла діагностика по полях для клієнтських розробників

#### Best practices

1. Тримайте DTO сфокусованими на конкретному endpoint/use-case.
2. Розділяйте Create/Update DTO (часто через `PartialType`).
3. Не покладайтеся лише на валідацію в сервісах, якщо контролери приймають
   зовнішні дані.
4. Налаштовуйте `exceptionFactory` у `ValidationPipe` для консистентної
   структури API-помилок.

</details>

<details>
<summary>35. Як реалізувати глобальний Exception Filter і кастомні HTTP-помилки?</summary>

#### NestJS

У NestJS глобальний Exception Filter централізує мапінг "помилка -> відповідь",
щоб усі необроблені винятки повертали консистентний API-формат.

Кастомні HTTP-помилки зазвичай створюють через наслідування `HttpException` або
використання built-in винятків (`BadRequestException`, `NotFoundException` тощо).

#### 1) Створіть глобальний exception filter

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

#### 2) Зареєструйте filter глобально

У `main.ts`:

```ts
app.useGlobalFilters(new GlobalExceptionFilter());
```

#### 3) Створіть кастомний HTTP exception

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

Використання:

```ts
if (!canCloseOrder) {
  throw new BusinessRuleViolationException('Order cannot be closed in current state');
}
```

#### Чому цей підхід ефективний

1. Єдиний формат відповіді для всієї API-поверхні.
2. Чистіші контролери/сервіси (без повторюваних try/catch для форматування).
3. Централізовані observability hooks (logging, correlation IDs, error codes).
4. Просте мапування domain/infrastructure помилок у коректну HTTP-семантику.

#### Best practices

1. Не розкривайте внутрішні stack traces у production-відповідях.
2. Додавайте machine-readable error codes для клієнтів.
3. Зберігайте stack traces у логах (не обов'язково в HTTP-body).
4. Очікувані бізнес-помилки мапте в 4xx; неочікувані збої - у 5xx.

</details>

<details>
<summary>36. Як правильно обробляти помилки і повертати консистентну структуру відповіді?</summary>

#### NestJS

Коректна обробка помилок у NestJS означає розділення:
1. де помилки виникають (domain/application/infrastructure),
2. де вони транслюються в HTTP (filters),
3. і як стандартизується формат відповіді (глобальний контракт).

#### Рекомендована стратегія

1. **Кидайте змістовні винятки в бізнес-потоці**
   Використовуйте domain-specific винятки або відповідні `HttpException`
   підкласи.

2. **Централізуйте форматування HTTP-відповіді**
   Використовуйте глобальний exception filter для єдиної схеми помилок.

3. **Стандартизуйте і success-відповіді**
   За потреби застосуйте interceptor для уніфікованого success-envelope.

4. **Збережіть observability**
   Логуйте error-context (requestId, path, userId, stack) в одному місці.

#### Приклад консистентної структури помилки

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

#### Компоненти реалізації

1. **Global Exception Filter**
   Мапить усі винятки в єдину структуру відповіді.

2. **Custom exception classes**
   Інкапсулюють domain/business error code + message + status.

3. **Опціональний response interceptor**
   Обгортає успішні відповіді у вигляд:
   `{ success: true, data, meta }`.

#### Рекомендації з категоризації помилок

1. **Validation/client input errors** -> `400`.
2. **Authentication errors** -> `401`.
3. **Authorization errors** -> `403`.
4. **Missing resources** -> `404`.
5. **Business rule conflicts** -> `409` або `422`.
6. **Unexpected system failures** -> `500`.

#### Чого варто уникати

1. Повернення ad-hoc формату помилок із різних контролерів.
2. "Поглинання" винятків і повернення `200` з `"error"` у body.
3. Розкриття внутрішніх stack traces/SQL-помилок у production-відповідях.
4. Змішування transport-formatting логіки напряму в сервісах.

#### Практичні best practices

1. Визначте каталог error codes (`USER_NOT_FOUND`, `TOKEN_EXPIRED` тощо).
2. Додавайте correlation/request ID в кожну error-відповідь і лог.
3. Переконайтесь, що global filter обробляє і відомі (`HttpException`), і
   невідомі помилки.
4. Покрийте error-path сценарії e2e-тестами, щоб зафіксувати API error-contract.

</details>

<details>
<summary>37. Як правильно логувати помилки і не втрачати stack trace у production?</summary>

#### NestJS

Щоб правильно логувати помилки у production, потрібні два паралельні виходи:
1. **safe client response** (без чутливих внутрішніх деталей),
2. **повний structured server log** (включно зі stack trace і контекстом).

#### Базовий принцип

Ніколи не показуйте stack traces API-клієнтам, але завжди зберігайте їх у логах
для дебагу та incident response.

#### Рекомендований підхід у NestJS

1. Централізовано перехоплюйте помилки в глобальному exception filter.
2. Логуйте через structured logger (Pino/Winston/Nest Logger adapter).
3. Додавайте stack, error code, request metadata, correlation ID і user context.
4. Повертайте sanitized error payload із filter-а.

#### Приклад (глобальний filter із логуванням stack)

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
      stack: err?.stack, // keep full stack in logs
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

#### Що логувати для production-grade діагностики

1. Timestamp, level, service name, environment.
2. Request ID / trace ID.
3. Route, method, status code, latency.
4. Auth context (userId/tenantId, якщо доступно).
5. Повний stack + root cause chain.

#### Типові помилки

1. Логування лише `error.message` (втрачається stack і ланцюжок причин).
2. Логи через конкатенацію рядків замість structured JSON.
3. Дублювання логування на різних шарах (noise).
4. Повернення raw exception-об'єктів клієнтам.

#### Практичні best practices

1. Використовуйте один structured logger на рівні всього застосунку.
2. Додавайте correlation ID middleware/interceptor якомога раніше в lifecycle.
3. Редагуйте/маскуйте secrets і PII перед записом у логи.
4. Відправляйте логи в централізований observability-стек (ELK, Datadog,
   Grafana Loki).
5. Тестуйте error-path сценарії, щоб переконатися, що stack зберігається в логах
   після деплою.

</details>

<details>
<summary>38. Що таке ConfigModule і чому його варто використовувати замість process.env?</summary>

#### NestJS

`ConfigModule` — це система конфігурації NestJS (`@nestjs/config`), яка
завантажує, валідовує та надає значення середовища/конфігурації через DI.

Використовувати `ConfigModule` краще, ніж прямий доступ до `process.env`, бо він
централізує логіку конфігурації, підвищує type-safety і значно спрощує
тестування та підтримку.

#### Чому одного `process.env` недостатньо

1. Зчитування змінних середовища розкидані по всій кодовій базі.
2. Немає централізованої валідації обов'язкових змінних.
3. Лише рядкові значення без типізованого парсингу.
4. Складніше тестувати/мокати й гірша прозорість конфігурації.

#### Що дає `ConfigModule`

1. **Централізоване завантаження конфігурації**
   Одне місце для визначення env-файлів і config factory.

2. **Валідація на старті**
   Fail-fast, якщо обов'язкові змінні відсутні або невалідні.

3. **Типізований доступ через `ConfigService`**
   Кращі контракти й менше runtime-сюрпризів.

4. **Інтеграція з DI**
   Будь-який провайдер може чисто інжектити конфіг.

5. **Композиція під різні середовища**
   Легко розділяти налаштування для dev/staging/prod.

#### Базове налаштування

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

Приклад використання:

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

#### Приклад валідації (рекомендовано)

Використовуйте `validationSchema` (Joi) або власну validation-функцію:
1. Вимагайте обов'язкові змінні.
2. Валідовуйте формати/діапазони.
3. Зупиняйте bootstrap застосунку за невалідного конфігу.

#### Практична рекомендація

Використовуйте `process.env` лише в межах config factory/bootstrap. В усіх інших
місцях отримуйте конфіг через `ConfigService` або типізовані config-провайдери —
це дає консистентність, кращу тестованість і безпечнішу поведінку в продакшені.

</details>

<details>
<summary>39. Як правильно організувати .env файли для різних середовищ (dev, staging, prod)?</summary>

#### NestJS

Правильна організація `.env` має забезпечувати передбачувану конфігурацію для
кожного середовища, запобігати витокам секретів і залишати локальну розробку
зручною.

#### Рекомендована стратегія середовищ

1. Тримайте один **базовий** файл для спільних дефолтів.
2. Додавайте **environment-specific** файли для перевизначень.
3. Не зберігайте секрети в git; інжектіть їх через платформу деплою/secret store.

Типовий layout:
1. `.env` (спільні локальні дефолти)
2. `.env.development`
3. `.env.staging`
4. `.env.production`
5. `.env.test`
6. `.env.local` (локальні перевизначення розробника, `gitignored`)

#### З NestJS `ConfigModule`

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

Порядок завантаження важливий: у цьому патерні файли на початку списку зазвичай
мають вищий пріоритет.

#### Що комітити, а що ігнорувати

1. Комітити:
   1. `.env.example` (документує всі потрібні ключі без реальних секретів)
   2. Несекретні дефолти, якщо це дозволяє ваша політика

2. Не комітити:
   1. Реальні секрети/токени/приватні ключі
   2. `.env.local` та machine-specific перевизначення

#### Валідація і fail-fast

Завжди валідовуйте конфіг на старті (Joi або кастомний валідатор):
1. Обов'язкові ключі присутні.
2. Типи/діапазони валідні (`PORT`, таймаути, feature flags).
3. Формат URL і credentials коректний.

#### Практики для production/staging

1. Віддавайте перевагу platform secret manager-ам (AWS SSM/Secrets Manager,
   Vault, Doppler тощо), а не plaintext-файлам.
2. Регулярно ротируйте секрети.
3. Строго розділяйте staging/prod credentials.
4. Явно задавайте `NODE_ENV` у конфігурації деплою.
5. Ніколи не вбудовуйте секрети в Docker-образи або вихідний код.

#### Практичний командний workflow

1. Підтримуйте `.env.example` як контракт.
2. Додайте onboarding-скрипт/перевірку на відсутні env-змінні.
3. Використовуйте типізовані config-обгортки, щоб код застосунку не читав
   випадкові env-ключі напряму.
4. Документуйте відповідальних за критичні змінні (DB, JWT, зовнішні API).

</details>

<details>
<summary>40. Як використовувати Joi або zod для валідації конфігурації при старті застосунку?</summary>

#### NestJS

Валідуйте конфігурацію на старті, щоб застосунок завершувався одразу за
відсутніх/невалідних env-значень, а не падав пізніше під час runtime.

У NestJS це зазвичай робиться через `ConfigModule.forRoot(...)` і один із
підходів:
1. `validationSchema` (Joi), або
2. `validate` функція (кастомна логіка, часто на базі Zod).

#### Варіант A: Joi через `validationSchema`

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

Як це працює:
1. Завантажуються env-змінні.
2. Joi перевіряє форму і обмеження.
3. Якщо конфіг невалідний, bootstrap застосунку падає одразу.

#### Варіант B: Zod через `validate` функцію

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

Чому команди обирають Zod:
1. Сильна TS-інференція зі схеми.
2. Компоновані схеми для модульного конфігу.
3. Прозорі parse-помилки і підтримка трансформацій.

#### Практичні best practices

1. Валідовуйте всі обов'язкові секрети/URL/порти на старті.
2. Явно приводьте примітивні типи (`PORT`, boolean-и, таймаути).
3. Тримайте одну схему як single source of truth.
4. Віддавайте типізований конфіг через обгортки/сервіси, а не raw `process.env`.
5. Використовуйте різні env-файли для різних середовищ, але один контракт
   валідації.

#### Joi vs Zod коротко

1. **Joi**: зрілий інструмент, простий старт через вбудований `validationSchema`.
2. **Zod**: TS-first типізація і композиційність; зручний для типізованих
   конфіг-пайплайнів.

Обидва підходи production-ready; оберіть один і застосовуйте послідовно.

</details>

<details>
<summary>41. Як реалізувати feature flags у NestJS?</summary>

#### NestJS

Feature flags у NestJS зазвичай реалізують через окремий сервіс, який визначає,
чи ввімкнена фіча для конкретного контексту (середовище, користувач, tenant,
відсотковий rollout тощо).

#### Чому feature flags важливі

1. Безпечний поступовий rollout.
2. Швидкий kill-switch для проблемних фіч.
3. A/B-експерименти.
4. Розділення деплою і релізу.

#### Типова архітектура

1. **FeatureFlagService**
   Єдина точка входу: `isEnabled(flag, context)`.

2. **Джерело флагів**
   Env-конфіг, таблиця БД або зовнішній flag-провайдер.

3. **Контекст оцінки**
   User ID, tenant ID, plan, регіон, версія застосунку, метадані запиту.

4. **Точки використання**
   Guards, сервіси, контролери, interceptors, формування UI-відповіді.

#### Простий in-app варіант (на базі конфігу)

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

Використання в сервісі:

```ts
if (this.flags.isEnabled('new_checkout', { userId, tenantId })) {
  return this.newCheckoutFlow();
}
return this.legacyCheckoutFlow();
```

#### Контроль на рівні маршруту через Guard (опційно)

1. Створіть метадекоратор `@Feature('new_checkout')`.
2. Guard читає метадані через `Reflector`.
3. Guard викликає `FeatureFlagService.isEnabled(...)`.
4. Якщо фіча вимкнена - забороняє доступ або reroute-ить поведінку.

#### Production-ready практики

1. Підтримуйте rollout-стратегії:
   1. Глобальне on/off
   2. Percentage rollout
   3. User/tenant allowlists
   4. Активація за time-window

2. Додайте локальний TTL-кеш для зовнішніх flag-провайдерів.
3. Явно задавайте default-поведінку (fail-closed vs fail-open для кожного флага).
4. Логуйте/фіксуйте рішення по флагах для дебагу.
5. Швидко прибирайте застарілі флаги, щоб не накопичувати складність.

#### Build vs buy

1. Реалізуйте in-app, якщо потреби прості й хочете низькі операційні витрати.
2. Використовуйте керовані сервіси (LaunchDarkly, Unleash, ConfigCat тощо) для
   складного таргетингу, аналітики та governance.

#### Практичне правило

Сприймайте флаги як короткоживучі release-контролі, а не як постійні гілки
бізнес-логіки. Для кожного флага призначайте відповідального та sunset date.

</details>

<details>
<summary>42. Як інтегрувати бази даних? (TypeORM, Prisma, Drizzle, Mongoose)</summary>

#### NestJS

У NestJS інтеграцію з БД варто робити через окремі інфраструктурні
модулі/провайдери, а не напряму в контролерах. Вибір залежить від моделі даних,
вподобань команди та складності запитів.

#### Поширені варіанти

1. **TypeORM**
   Повнофункціональний ORM з декораторами, репозиторіями, міграціями та сильною
   інтеграцією з модулями Nest.

2. **Prisma**
   Schema-first ORM/client з відмінним DX, типізованими запитами і
   передбачуваними міграціями.

3. **Drizzle**
   Легкий типізований SQL toolkit/ORM з явним SQL-орієнтованим підходом.

4. **Mongoose**
   ODM для MongoDB зі схемами та document-oriented workflow.

#### Патерни інтеграції за інструментом

1. **TypeORM**
   Використовуйте `TypeOrmModule.forRoot(...)` у кореневому модулі і
   `forFeature([Entity])` у feature-модулях; репозиторії інжектіть через
   `@InjectRepository`.

2. **Prisma**
   Створіть `PrismaService` (успадкований від `PrismaClient`) і зареєструйте його
   в модулі. Інжектіть сервіс у репозиторії/сервіси прикладного шару.

3. **Drizzle**
   Побудуйте DB-провайдер (`drizzle(...)`) на базі connection pool (`pg`,
   `mysql2`). Типізований DB-інстанс інжектіть через кастомний токен.

4. **Mongoose**
   Використовуйте `MongooseModule.forRoot(...)` +
   `forFeature([{ name, schema }])`; модель інжектіть через `@InjectModel`.

#### Мінімальні приклади

TypeORM:

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

Prisma service:

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

#### Як обирати

1. Обирайте **TypeORM**, якщо потрібен класичний Nest-style з
   decorators/repositories.
2. Обирайте **Prisma** для сильного типізованого клієнта і сучасного
   migration-workflow.
3. Обирайте **Drizzle**, якщо вам потрібна SQL-first явність із type safety.
4. Обирайте **Mongoose**, коли природною є document-модель MongoDB.

#### Production best practices (незалежно від інструмента)

1. Тримайте доступ до БД у репозиторіях/адаптерах, не в контролерах.
2. Використовуйте міграції; уникайте auto-sync схеми в production.
3. Налаштовуйте connection pooling і таймаути.
4. Додайте health checks і fail-fast поведінку на старті.
5. Інструментуйте latency запитів і error rates.
6. Інкапсулюйте транзакції в межах application-service.

</details>

<details>
<summary>43. У чому різниця між TypeOrmModule.forRoot() і forFeature()?</summary>

#### NestJS

`TypeOrmModule.forRoot()` і `TypeOrmModule.forFeature()` мають різні зони
відповідальності в інтеграції TypeORM з NestJS.

#### `forRoot()` — налаштування підключення до БД на рівні застосунку

Використовується в кореневому модулі (зазвичай `AppModule`) для конфігурації
DataSource/connection.

Визначає:
1. Драйвер/тип БД (`postgres`, `mysql` тощо)
2. Credentials/URL підключення
3. Глобальні опції TypeORM (завантаження entities, логування, міграції,
   `synchronize`)

Приклад:

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

#### `forFeature()` — реєстрація репозиторіїв у feature-модулі

Використовується в доменних/feature-модулях для реєстрації конкретних entities і
надання їхніх репозиторіїв для інжекції в межах цього модуля.

Приклад:

```ts
@Module({
  imports: [TypeOrmModule.forFeature([UserEntity])],
  providers: [UsersService],
})
export class UsersModule {}
```

Інжекція репозиторію:

```ts
constructor(
  @InjectRepository(UserEntity)
  private readonly usersRepo: Repository<UserEntity>,
) {}
```

#### Практична різниця в одному блоці

1. `forRoot()`:
   1. Створює/конфігурує підключення до БД один раз (або іменовані підключення).
   2. Глобальна інфраструктурна відповідальність.

2. `forFeature()`:
   1. Експонує репозиторії вибраних entities у scope конкретного модуля.
   2. Feature/business відповідальність.

#### Типова помилка

Використання `forFeature()` без `forRoot()` (або без ініціалізованого DataSource)
призводить до DI/runtime-помилок, тому що репозиторії не мають активного
підключення.

#### Правило практики

1. Налаштовуйте підключення один раз через `forRoot` у bootstrap-шляху.
2. Реєструйте entities через `forFeature` у модулях, де потрібні репозиторії.
3. Тримайте `synchronize: false` у production і використовуйте міграції.

</details>

<details>
<summary>44. Що таке Repository pattern у NestJS + TypeORM?</summary>

#### NestJS

Repository pattern абстрагує доступ до даних через окремий інтерфейс/сервіс, щоб
бізнес-логіка не залежала напряму від деталей ORM.

У NestJS + TypeORM це зазвичай означає обгортку над `Repository<Entity>` у
вигляді власного доменно-орієнтованого контракту репозиторію та його
реалізації.

#### Навіщо використовувати Repository pattern

1. Розв'язує application/domain логіку від API TypeORM.
2. Покращує тестованість (легко мокати інтерфейси репозиторіїв).
3. Централізує query-логіку і мапінг.
4. Полегшує заміну ORM/рефакторинг у майбутньому.

#### Типова структура

1. **Доменний контракт (port)**
   Інтерфейс `UsersRepository` з бізнес-орієнтованими методами.

2. **Інфраструктурна реалізація**
   `TypeOrmUsersRepository`, який використовує `Repository<UserEntity>`.

3. **Service/application шар**
   Залежить від interface token, а не від конкретного класу TypeORM.

#### Приклад

Контракт репозиторію:

```ts
export interface UsersRepository {
  findByEmail(email: string): Promise<UserEntity | null>;
  save(user: UserEntity): Promise<UserEntity>;
}
```

Реалізація на TypeORM:

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

Прив'язка провайдера:

```ts
{
  provide: 'USERS_REPOSITORY',
  useClass: TypeOrmUsersRepository,
}
```

Сервіс залежить від абстракції:

```ts
constructor(
  @Inject('USERS_REPOSITORY')
  private readonly usersRepo: UsersRepository,
) {}
```

#### Що має бути в repository, а що в service

1. Repository:
   persistence-запити, завантаження/збереження aggregate, DB-специфічна фільтрація.

2. Service/use-case:
   оркестрація, бізнес-правила, координація меж транзакцій.

#### Поширений anti-pattern

Інжектити TypeORM-репозиторії напряму в багато сервісів/контролерів і дублювати
фрагменти запитів всюди. Це підвищує зв'язаність і неузгодженість.

#### Практичний висновок

Використовуйте TypeORM repository "під капотом", але назовні експонуйте власний
доменний інтерфейс репозиторію, щоб архітектура залишалась модульною і
test-friendly.

</details>

<details>
<summary>45. Чим відрізняється Repository pattern від Active Record — і коли який підхід обирати?</summary>

#### NestJS

Repository pattern і Active Record - це два різні підходи до організації
persistence-логіки.

#### Ключова різниця

1. **Repository pattern**
   Domain/business шар працює з абстракціями репозиторіїв; persistence-логіка
   винесена в окремі класи репозиторіїв.

2. **Active Record**
   Entity/model об'єкти містять методи збереження самі (`save`, `remove`,
   static finders), тобто поєднують дані + persistence-поведінку.

#### Характеристики Repository pattern

1. Краще розділення відповідальностей.
2. Простіше unit-тестування через interface mocks.
3. Краще масштабується у складних доменах/мікросервісах.
4. Підтримує domain-centric дизайн і чисті межі.

#### Характеристики Active Record

1. Швидший старт для малих/простих застосунків.
2. Менше boilerplate для простого CRUD.
3. З часом може виникати сильна зв'язаність з ORM.
4. Складніше ізолювати бізнес-логіку, коли росте складність.

#### Коли який підхід обирати

1. Обирайте **Repository pattern**, коли:
   1. Проєкт середній/великий або очікується ріст.
   2. Команді потрібні строга архітектура і тестованість.
   3. Доменна логіка нетривіальна.
   4. Потенційно можлива заміна ORM у майбутньому.

2. Обирайте **Active Record**, коли:
   1. Застосунок малий, CRUD-орієнтований і низької складності.
   2. Пріоритет - швидкість початкової розробки.
   3. Команда приймає компроміс більшої зв'язаності з ORM.

#### Практика в NestJS

1. Архітектура NestJS (modules/providers/DI) природно узгоджується з
   repository pattern.
2. Навіть із TypeORM багато production-команд віддають перевагу
   Data Mapper/repository стилю замість Active Record, щоб сервіси залишались
   чистими.

#### Швидке порівняння

1. **Coupling**
   Repository: нижчий
   Active Record: вищий

2. **Testability**
   Repository: висока
   Active Record: середня/низька (більша прив'язка до БД)

3. **Boilerplate**
   Repository: більше
   Active Record: менше

4. **Long-term maintainability**
   Repository: кращий для складних систем
   Active Record: прийнятний для простих застосунків

#### Практична рекомендація

Для interview-level і production-grade архітектури NestJS за замовчуванням
обирайте Repository pattern. Active Record використовуйте лише тоді, коли домен
свідомо простий і життєвий цикл системи має низьку складність.

</details>

<details>
<summary>46. Що таке міграції в TypeORM/Prisma і чому synchronize: true небезпечно в production?</summary>

#### NestJS

</details>

<details>
<summary>47. Як реалізувати soft delete в TypeORM?</summary>

#### NestJS

</details>

<details>
<summary>48. Як реалізувати транзакції в TypeORM у NestJS?</summary>

#### NestJS

</details>

<details>
<summary>49. Що таке N+1 проблема і як її вирішити в NestJS?</summary>

#### NestJS

</details>

<details>
<summary>50. Що таке connection pooling і як його правильно налаштувати для бази даних?</summary>

#### NestJS

</details>

<details>
<summary>51. Як захиститись від SQL injection у TypeORM/Prisma?</summary>

#### NestJS

</details>

<details>
<summary>52. Як правильно організувати pagination у REST API? (offset vs cursor-based)</summary>

#### NestJS

</details>

<details>
<summary>53. Як версіонувати API у NestJS? (URI, Header, Media type versioning)</summary>

#### NestJS

</details>

<details>
<summary>54. Як реалізувати Swagger документацію у NestJS через @nestjs/swagger?</summary>

#### NestJS

</details>

<details>
<summary>55. Як реалізувати CORS у NestJS і коли потрібні кастомні налаштування?</summary>

#### NestJS

</details>

<details>
<summary>56. Що таке idempotency в контексті REST API і як її забезпечити?</summary>

#### NestJS

</details>

<details>
<summary>57. Як реалізувати rate limiting у NestJS? (@nestjs/throttler)</summary>

#### NestJS

</details>

<details>
<summary>58. Як реалізувати request tracing (додавати requestId до кожного запиту)?</summary>

#### NestJS

</details>

<details>
<summary>59. Як обробити multipart/form-data і завантаження файлів у NestJS?</summary>

#### NestJS

</details>

<details>
<summary>60. Як реалізувати compression (gzip/brotli) у NestJS?</summary>

#### NestJS

</details>

<details>
<summary>61. Як реалізувати helmet і які HTTP-заголовки він встановлює?</summary>

#### NestJS

</details>

<details>
<summary>62. Які основні OWASP-вразливості і як від них захиститись?</summary>

#### NestJS

</details>

<details>
<summary>63. Як використовувати HttpModule (axios) у NestJS для запитів до зовнішніх API?</summary>

#### NestJS

</details>

<details>
<summary>64. Як додати глобальні interceptors до axios у NestJS? (додавання headers, логування)</summary>

#### NestJS

</details>

<details>
<summary>65. Як правильно типізувати відповідь зовнішнього API у TypeScript?</summary>

#### NestJS

</details>

<details>
<summary>66. Як реалізувати retry логіку для зовнішніх HTTP-запитів у NestJS?</summary>

#### NestJS

</details>

<details>
<summary>67. Що таке Circuit Breaker патерн і коли він потрібен?</summary>

#### NestJS

</details>

<details>
<summary>68. Як реалізувати кешування (in-memory, Redis), і коли який підхід використовувати?</summary>

#### NestJS

</details>

<details>
<summary>69. Що таке інвалідація кешу і як правильно її реалізувати?</summary>

#### NestJS

</details>

<details>
<summary>70. Коли в NestJS варто використовувати Observables замість Promise?</summary>

#### NestJS

</details>

<details>
<summary>71. У чому різниця між async/await і RxJS для роботи з асинхронною логікою, і коли який підхід використовувати?</summary>

#### NestJS

</details>

<details>
<summary>72. Як уникнути блокування event loop у NestJS і підтримувати продуктивність?</summary>

#### NestJS

</details>

<details>
<summary>73. Як оптимізувати latency (p95 / p99) і що впливає на ці метрики?</summary>

#### NestJS

</details>

<details>
<summary>74. Як використовувати cluster mode у Node.js разом з NestJS для масштабування?</summary>

#### NestJS

</details>

<details>
<summary>75. Як реалізувати cron-задачі у NestJS через @nestjs/schedule?</summary>

#### NestJS

</details>

<details>
<summary>76. Що таке EventEmitter у NestJS і чим він відрізняється від черг (Bull)?</summary>

#### NestJS

</details>

<details>
<summary>77. Як реалізувати внутрішню event-driven комунікацію між модулями через EventEmitter2?</summary>

#### NestJS

</details>

<details>
<summary>78. Як реалізувати фонові задачі за допомогою Bull або BullMQ?</summary>

#### NestJS

</details>

<details>
<summary>79. Як проєктувати ідемпотентні джоби (черги задач), щоб уникати дублювання виконання?</summary>

#### NestJS

</details>

<details>
<summary>80. Як реалізувати WebSockets у NestJS?</summary>

#### NestJS

</details>

<details>
<summary>81. Як реалізувати автентифікацію у WebSocket Gateway?</summary>

#### NestJS

</details>

<details>
<summary>82. Які підходи використовують для масштабування real-time систем?</summary>

#### NestJS

</details>

<details>
<summary>83. Які підходи до інтеграції GraphQL у NestJS (code-first vs schema-first), і в чому їх різниця?</summary>

#### NestJS

</details>

<details>
<summary>84. Що таке resolvers у GraphQL і чим вони відрізняються від контролерів REST?</summary>

#### NestJS

</details>

<details>
<summary>85. Як у GraphQL працювати з context і реалізувати авторизацію через нього?</summary>

#### NestJS

</details>

<details>
<summary>86. Які транспортні протоколи та брокери повідомлень підтримуються (Kafka, Redis, gRPC, NATS) і в чому їх відмінності?</summary>

#### NestJS

</details>

<details>
<summary>87. Як правильно проєктувати event-driven архітектуру і основні принципи такої системи?</summary>

#### NestJS

</details>

<details>
<summary>88. Як працювати з distributed transactions у мікросервісах? (Saga pattern, eventual consistency)</summary>

#### NestJS

</details>

<details>
<summary>89. Що таке CQRS і як його реалізувати в NestJS за допомогою @nestjs/cqrs?</summary>

#### NestJS

</details>

<details>
<summary>90. Що таке Domain-Driven Design і як його принципи застосовуються в NestJS?</summary>

#### NestJS

</details>

<details>
<summary>91. Що таке Hexagonal Architecture (Ports & Adapters) і як її реалізувати в NestJS?</summary>

#### NestJS

</details>

<details>
<summary>92. Як реалізувати структуроване логування, і навіщо це потрібно?</summary>

#### NestJS

</details>

<details>
<summary>93. Як у NestJS реалізувати моніторинг стану застосунку? (@nestjs/terminus)</summary>

#### NestJS

</details>

<details>
<summary>94. Як реалізувати health checks для залежних сервісів (DB, Redis, зовнішні API)?</summary>

#### NestJS

</details>

<details>
<summary>95. Як використовувати OpenTelemetry у NestJS?</summary>

#### NestJS

</details>

<details>
<summary>96. Що таке distributed tracing і як його реалізують у мікросервісній архітектурі?</summary>

#### NestJS

</details>

<details>
<summary>97. Як писати unit-тести в NestJS, і які є базові підходи до тестування?</summary>

#### NestJS

</details>

<details>
<summary>98. Як правильно мокати залежності в NestJS, і коли це потрібно робити?</summary>

#### NestJS

</details>

<details>
<summary>99. Як писати інтеграційні тести в NestJS з використанням TestingModule?</summary>

#### NestJS

</details>

<details>
<summary>100. Що таке end-to-end (E2E) тестування в NestJS, і чим воно відрізняється від unit та integration тестів?</summary>

#### NestJS

</details>

<details>
<summary>101. Що таке Nest CLI і які команди використовуються найчастіше?</summary>

#### NestJS

</details>

<details>
<summary>102. Як правильно організувати Dockerfile для NestJS застосунку (multi-stage build)?</summary>

#### NestJS

</details>
