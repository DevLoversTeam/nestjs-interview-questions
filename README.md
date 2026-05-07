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

Міграції - це версіоновані, явні скрипти змін схеми бази даних. Вони дають
команді можливість еволюціонувати схему безпечно і передбачувано між
середовищами.

У TypeORM/Prisma міграції - це production-safe спосіб застосовувати зміни схеми.

#### Що таке міграції

1. **Впорядкована історія схеми**
   Кожна міграція - це відстежуваний крок (up/down) в еволюції схеми.

2. **Відтворювані деплої**
   Ті самі зміни схеми консистентно застосовуються в dev/staging/prod.

3. **Рев'юваний набір змін**
   Намір SQL/DDL видно в code review і CI.

4. **Стратегія rollback**
   Проблемні зміни можна відкотити (з урахуванням обмежень).

#### Модель міграцій у TypeORM vs Prisma

1. **TypeORM**
   Міграції - це TS/JS-файли (або SQL), які генеруються/пишуться і виконуються
   через CLI.

2. **Prisma**
   Зміни схеми описуються в `schema.prisma`; файли міграцій генеруються і
   застосовуються через Prisma Migrate.

Обидва підходи створюють аудитні migration-артефакти.

#### Чому `synchronize: true` небезпечний у production

1. **Неявні руйнівні зміни**
   ORM може автоматично змінювати/видаляти колонки та індекси без контрольованого
   рев'ю.

2. **Недетермінована поведінка**
   Поведінка schema-diff може відрізнятися через drift entities і runtime-стан.

3. **Відсутність коректної історії міграцій**
   Складно аудіювати, що саме і коли змінилось.

4. **Ризикований зв'язок зі стартом застосунку**
   Під час boot застосунок може неочікувано мутувати production-схему.

5. **Погана безпека при multi-instance**
   Паралельні старти інстансів можуть змагатись за оновлення схеми.

#### Production-safe workflow

1. Ставте `synchronize: false` у production.
2. Генеруйте міграцію для кожної зміни схеми.
3. Рев'юйте SQL міграцій у PR.
4. Запускайте міграції в deployment pipeline до/разом із rollout застосунку.
5. Моніторте виконання міграцій і фейліть деплой при помилках.

#### Практичні приклади

TypeORM production-конфіг:

```ts
TypeOrmModule.forRoot({
  // ...
  synchronize: false,
  migrationsRun: false,
});
```

Підхід для деплою Prisma:
1. Комітьте файли міграцій.
2. Запускайте `prisma migrate deploy` під час релізу.

#### Правило практики

`synchronize: true` використовуйте лише для швидкого локального прототипування.
Для будь-якого серйозного середовища міграції обов'язкові заради безпеки,
трасованості й контрольованої еволюції схеми.

</details>

<details>
<summary>47. Як реалізувати soft delete в TypeORM?</summary>

#### NestJS

Soft delete означає, що записи позначаються як видалені, а не видаляються
фізично з бази даних. У TypeORM це зазвичай робиться через `@DeleteDateColumn`.

#### Навіщо використовувати soft delete

1. Відновлення випадково видалених даних.
2. Збереження audit/history контексту.
3. Збереження foreign key зв'язків і бізнес-трасованості.
4. Підтримка сценаріїв "кошик/відновлення".

#### Крок 1: Додайте колонку часу видалення

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

#### Крок 2: Використовуйте soft-delete методи репозиторію

```ts
// позначити як видалений (встановлює deletedAt)
await this.usersRepo.softDelete(userId);

// відновити soft-deleted запис
await this.usersRepo.restore(userId);
```

Також можна використовувати:
1. `softRemove(entity)` для видалення інстансу entity.
2. `recover(entity)` для відновлення інстансу.

#### Поведінка запитів

1. За замовчуванням TypeORM виключає soft-deleted записи зі стандартних
   `find*` запитів.
2. Щоб включити видалені записи, використовуйте `withDeleted: true`.

```ts
const allRows = await this.usersRepo.find({ withDeleted: true });
```

Тільки видалені записи:

```ts
const deletedOnly = await this.usersRepo.find({
  withDeleted: true,
  where: { deletedAt: Not(IsNull()) },
});
```

#### Приклад на рівні сервісу

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

#### Production-моменти

1. Додавайте індекси для полів, що часто фільтруються (`deleted_at`,
   tenant-ключі).
2. Переконайтесь, що unique constraints враховують soft-deleted рядки
   (partial unique indexes, де підтримується).
3. Визначте retention policy для eventual hard cleanup.
4. Фіксуйте події видалення/відновлення в audit logs.

#### Правило практики

Використовуйте soft delete для user/business даних, які можуть вимагати
відновлення або аудиту. Hard delete застосовуйте лише там, де політики
compliance/storage або доменні правила вимагають постійного видалення.

</details>

<details>
<summary>48. Як реалізувати транзакції в TypeORM у NestJS?</summary>

#### NestJS

Транзакції гарантують, що група операцій з БД або виконується повністю, або
повністю відкочується. У NestJS + TypeORM використовуйте транзакції для
багатокрокових записів, де критична консистентність.

#### Коли транзакції обов'язкові

1. Створення/оновлення кількох пов'язаних таблиць в одному use-case.
2. Операції з балансом/грошима/залишками.
3. Сценарії, де частковий успіх пошкоджує бізнес-стан.

#### Основні підходи в TypeORM

1. **`DataSource.transaction(...)`** (рекомендований дефолт)
2. **`QueryRunner`** (ручний контроль для складних сценаріїв)

#### Підхід 1: `DataSource.transaction` (чисто і безпечно)

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

Важливо: всередині callback транзакції використовуйте репозиторії/entity через
`manager`, а не глобально інжектені репозиторії.

#### Підхід 2: `QueryRunner` (fine-grained контроль)

```ts
const qr = dataSource.createQueryRunner();
await qr.connect();
await qr.startTransaction();
try {
  // use qr.manager for all queries
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

#### Best practices

1. Тримайте scope транзакції коротким і сфокусованим.
2. Уникайте зовнішніх HTTP-викликів усередині DB-транзакції.
3. Використовуйте потрібний isolation level для concurrency-чутливих сценаріїв.
4. Продумайте deadlock/retry стратегію для high-contention операцій.
5. Публікуйте domain events після успішного commit (або використовуйте outbox pattern).

#### Поширені помилки

1. Змішування транзакційних і нетранзакційних репозиторіїв в одному flow.
2. Довгі транзакції, що створюють lock contention.
3. Поглинання помилок із commit неузгодженого стану.

#### Практичне правило

Один бізнес-use-case загортайте в одну межу транзакції, коли консистентність між
кількома записами є безкомпромісною вимогою.

</details>

<details>
<summary>49. Що таке N+1 проблема і як її вирішити в NestJS?</summary>

#### NestJS

Проблема N+1 виникає, коли застосунок виконує:
1. один запит для завантаження списку батьківських записів,
2. а потім ще по одному запиту на кожен батьківський запис для пов'язаних даних.

У підсумку маємо `1 + N` запитів, високу затримку і зайве навантаження на БД.

#### Приклад N+1

1. Запит користувачів (`N` користувачів у результаті).
2. Для кожного користувача окремий запит до posts.
3. Загалом запитів: `1 + N`.

Для 100 користувачів це вже 101 round-trip до БД.

#### Де це з'являється в NestJS-застосунках

1. Lazy access до relation у TypeORM всередині циклів.
2. GraphQL resolvers, які резолвлять вкладені поля для кожної entity.
3. Методи сервісів із повторними per-item викликами репозиторію.

#### Як це вирішувати

1. **Eager load через joins**
   Використовуйте joins у query builder, щоб отримати relation-дані одним
   запитом (або контрольованою малою кількістю запитів).

2. **Batch loading**
   Використовуйте batching у стилі DataLoader (особливо в GraphQL).

3. **IN queries**
   Завантажуйте пов'язані рядки для всіх parent ID одразу і мапте в пам'яті.

4. **Оптимізація проєкції**
   Вибирайте лише потрібні колонки, щоб зменшити payload.

#### Приклад join у TypeORM

```ts
const users = await this.usersRepo
  .createQueryBuilder('u')
  .leftJoinAndSelect('u.posts', 'p')
  .getMany();
```

#### Приклад batch loading патерну

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

#### Сигнали виявлення

1. Різке зростання кількості запитів із ростом result set.
2. Затримка endpoint-а росте майже лінійно з кількістю parent-рядків.
3. Повторювані схожі SQL-запити в логах/моніторингу.

#### Практична стратегія запобігання

1. Увімкніть SQL/query logging у non-prod performance-тестах.
2. Додавайте query-count асерти для критичних endpoint-ів.
3. Віддавайте перевагу repository-методам, спроєктованим для aggregate-читання.
4. Переглядайте GraphQL resolvers на предмет per-field DB-викликів.

#### Правило практики

Якщо endpoint завантажує колекції з relation-даними, проєктуйте доступ до даних
заздалегідь під batching/joins. Не покладайтесь на per-item lazy-fetch цикли в
production-коді.

</details>

<details>
<summary>50. Що таке connection pooling і як його правильно налаштувати для бази даних?</summary>

#### NestJS

Connection pooling - це керований набір повторно використовуваних підключень до
БД, спільних між запитами. Замість створення нового підключення для кожного
запиту застосунок бере конекшн із пулу і повертає його після використання.

#### Чому pooling важливий

1. Зменшує накладні витрати на встановлення підключень.
2. Покращує throughput/latency під навантаженням.
3. Запобігає перевантаженню БД через неконтрольовані піки підключень.
4. Стабілізує поведінку при одночасних запитах.

#### Ключові параметри пулу

1. **max pool size**
   Максимальна кількість одночасних підключень до БД від одного інстансу.

2. **min pool size** (залежить від драйвера)
   Мінімальна кількість idle-підключень, які тримаються відкритими.

3. **acquire timeout**
   Скільки чекати вільне підключення.

4. **idle timeout**
   Скільки тримати невикористовувані підключення до закриття.

5. **max lifetime**
   Максимальний вік підключення до ротації.

#### Стратегія sizing (практична)

1. Починайте від ліміту БД і кількості реплік застосунку:
   `pool_max_per_instance * replica_count < db_connection_limit - safety_margin`.

2. Залишайте запас для:
   1. Міграцій/admin інструментів
   2. Фонових воркерів
   3. Неочікуваних сплесків трафіку

3. Навантажувально тестуйте і тюньте за:
   1. часом очікування на отримання конекшну
   2. DB CPU
   3. lock contention
   4. p95/p99 latency

#### Приклад TypeORM/NestJS (Postgres)

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

#### Operational best practices

1. Використовуйте один глобальний DataSource на процес застосунку (не створюйте
   багато пулів).
2. Налаштовуйте query timeouts і statement timeouts.
3. Моніторте метрики пулу: active, idle, waiting.
4. Тюньте під реальне навантаження, а не за дефолтами.
5. Для serverless/дуже еластичних сценаріїв розгляньте PgBouncer або
   provider-managed pooling.

#### Поширені помилки

1. Занадто великий пул -> DB thrashing/тиск на блокування.
2. Занадто малий пул -> черги запитів/таймаути.
3. Ігнорування мультиплікатора горизонтального масштабування між репліками.
4. Ручне відкриття нових клієнтів у request-handler-ах.

#### Правило практики

Розмір connection pool - це системне capacity-рішення, а не лише ORM-настройка.
Тюньте його з урахуванням production-like навантаження та лімітів БД.

</details>

<details>
<summary>51. Як захиститись від SQL injection у TypeORM/Prisma?</summary>

#### NestJS

Захист від SQL injection у NestJS з TypeORM/Prisma базується на одному принципі:
**ніколи не будуйте SQL через конкатенацію рядків з недовіреним вводом**.

Використовуйте parameterized queries і ORM API, які безпечно bind-ять значення.

#### Безпечні дефолтні підходи

1. **TypeORM repository/query builder з параметрами**
2. **Prisma client methods із типізованими фільтрами**
3. **DTO валідація + парсинг до того, як дані потрапляють у persistence-шар**

#### Безпечні патерни TypeORM

Repository API:

```ts
await usersRepo.findOne({ where: { email: input.email } });
```

QueryBuilder із bound params:

```ts
await usersRepo
  .createQueryBuilder('u')
  .where('u.email = :email', { email: input.email })
  .andWhere('u.status = :status', { status: 'active' })
  .getMany();
```

#### Безпечні патерни Prisma

```ts
await prisma.user.findMany({
  where: {
    email: input.email,
    status: 'active',
  },
});
```

Prisma у стандартних client-методах генерує parameterized queries "під капотом".

#### Небезпечні anti-pattern-и

1. Raw SQL зі string interpolation:

```ts
// BAD
await dataSource.query(`SELECT * FROM users WHERE email = '${input.email}'`);
```

2. Небезпечний dynamic `ORDER BY` / назви колонок із user input.
3. Передача невалідованих фрагментів у raw query-функції.

#### Якщо raw SQL неминучий

1. Використовуйте placeholders для параметрів:

```ts
await dataSource.query('SELECT * FROM users WHERE email = $1', [input.email]);
```

2. Явно whitelist-іть dynamic identifiers (поля сортування/колонки):
   мапте input -> відомий безпечний SQL token.

#### Defense in depth

1. Валідовуйте і санітизуйте input через DTO + `ValidationPipe`.
2. Використовуйте DB-акаунти з мінімально необхідними правами.
3. Вимикайте небезпечні DB-права (drop/alter, де не потрібно).
4. Логуйте підозрілі query-патерни і невдалі auth-спроби.
5. Додавайте security-тести з injection payload для критичних endpoint-ів.

#### Практичне правило

Залишайтесь на ORM API для 95% запитів. Для решти raw SQL-випадків завжди
bind-іть параметри і whitelist-іть будь-яку dynamic SQL-структуру.

</details>

<details>
<summary>52. Як правильно організувати pagination у REST API? (offset vs cursor-based)</summary>

#### NestJS

Правильний дизайн pagination у REST API має бути стабільним, продуктивним і
передбачуваним для клієнтів. Основні моделі - offset-based і cursor-based
pagination.

#### Offset vs cursor: ключова різниця

1. **Offset pagination**
   Використовує `limit` + `offset` (або page/pageSize).
   Приклад: `GET /users?limit=20&offset=40`.

2. **Cursor pagination**
   Використовує вказівник на останній побачений запис у відсортованому потоці.
   Приклад: `GET /users?limit=20&cursor=eyJpZCI6MTIzfQ==`.

#### Коли використовувати offset pagination

1. Малі/середні обсяги даних.
2. Потрібні довільні переходи по сторінках (`page=7`).
3. Прості admin dashboard/backoffice інструменти.

Компроміси:
1. Повільніше на великих offset.
2. Нестабільні сторінки при конкурентних insert/delete.

#### Коли використовувати cursor pagination

1. Великі набори даних, що часто змінюються.
2. Infinite scroll/mobile стрічки.
3. Performance-sensitive API.

Переваги:
1. Краща продуктивність БД на масштабі.
2. Стабільніше впорядкування при конкурентних записах.

Компроміс:
1. Немає природного довільного переходу на сторінку.

#### Базові правила дизайну (для обох моделей)

1. Завжди задавайте детермінований порядок сортування:
   наприклад, `ORDER BY created_at DESC, id DESC`.

2. Примусово обмежуйте максимальний розмір сторінки на сервері.

3. Повертайте pagination-метадані:
   `hasNext`, `nextCursor` (cursor-модель) або `total` (offset-модель за потреби).

4. Валідовуйте параметри pagination через DTO + pipes.

#### Приклади форми відповіді

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

#### Нотатки щодо реалізації в NestJS

1. Створюйте окремі DTO: `OffsetPaginationDto`, `CursorPaginationDto`.
2. Тримайте pagination-логіку в repository/query шарі, а не в контролері.
3. Кодуйте cursor як opaque token (base64/json + опційний підпис).
4. Переконайтесь, що індекси БД відповідають ключам сортування/фільтрації
   (`created_at`, `id`, tenant fields).

#### Практична рекомендація

1. Використовуйте **offset** для простих внутрішніх endpoint-ів.
2. Використовуйте **cursor** для публічних/high-volume стрічок.
3. Якщо сумніваєтесь, для write-heavy timeline краще стартувати з cursor, щоб
   уникнути майбутніх проблем продуктивності та консистентності.

</details>

<details>
<summary>53. Як версіонувати API у NestJS? (URI, Header, Media type versioning)</summary>

#### NestJS

Версіонування API у NestJS дозволяє еволюціонувати endpoint-и без поломки
існуючих клієнтів. Nest підтримує стратегії URI, custom header і media type
versioning.

#### Стратегії версіонування

1. **URI versioning**
   Версія в path: `/v1/users`, `/v2/users`.

2. **Header versioning**
   Версія в кастомному header (наприклад, `X-API-Version: 2`).

3. **Media type versioning**
   Версія в media type заголовка `Accept`
   (наприклад, `application/vnd.myapp.v2+json`).

#### Увімкнення версіонування в NestJS

```ts
import { NestFactory, VersioningType } from '@nestjs/core';

const app = await NestFactory.create(AppModule);

app.enableVersioning({
  type: VersioningType.URI, // або HEADER / MEDIA_TYPE
  defaultVersion: '1',
});
```

#### Оголошення версій на контролерах/роутах

На рівні контролера:

```ts
@Controller({ path: 'users', version: '1' })
export class UsersV1Controller {}
```

На рівні маршруту:

```ts
@Get()
@Version('2')
findAllV2() {}
```

Кілька версій для одного handler-а:

```ts
@Version(['1', '2'])
```

#### Вибір стратегії

1. **URI versioning** (найпоширеніший)
   1. Легко дебажити і кешувати.
   2. Чітко видно в логах і документації.
   3. Найкращий дефолт для публічних REST API.

2. **Header versioning**
   1. Зберігає чисті URL.
   2. Зручний у контрольованих enterprise-клієнтах.
   3. Складніше тестується вручну і кешується за замовчуванням.

3. **Media type versioning**
   1. Стандартоорієнтований стиль content negotiation.
   2. Найскладніший для клієнтів/інструментів.

#### Практичні best practices

1. Впроваджуйте versioning до першої breaking-зміни.
2. Тримайте вікно backward compatibility і політику deprecation.
3. Версіонуйте лише тоді, коли зміни контракту справді breaking.
4. Документуйте sunset timeline для старих версій.
5. Спільну бізнес-логіку тримайте в сервісах; версіонуйте переважно
   transport-шар.

#### Правило практики

Для більшості команд варто стартувати з **URI versioning**, бо це явно і
операційно просто. Header/media type versioning використовуйте лише за чітких
платформних вимог.

</details>

<details>
<summary>54. Як реалізувати Swagger документацію у NestJS через @nestjs/swagger?</summary>

#### NestJS

Swagger у NestJS реалізується через `@nestjs/swagger`, щоб автоматично
генерувати OpenAPI-документацію з контролерів, DTO і декораторів.

#### Крок 1: встановіть пакети

1. `@nestjs/swagger`
2. `swagger-ui-express`

#### Крок 2: налаштуйте Swagger у `main.ts`

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

URL документації буде `/docs`.

#### Крок 3: анотуйте контролери і DTO

Анотації контролера:

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

Анотації DTO:

```ts
import { ApiProperty } from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({ example: 'john@example.com' })
  email: string;

  @ApiProperty({ minLength: 8 })
  password: string;
}
```

#### Крок 4: тримайте схеми актуальними

1. Використовуйте class-based DTO (не interface) для runtime metadata.
2. Комбінуйте з `ValidationPipe`, щоб документація відповідала реальним
   обмеженням.
3. Явно документуйте auth, pagination і error-моделі.

#### Розширені практики для production

1. Генеруйте docs для кожної версії API, якщо увімкнене versioning.
2. Ховайте внутрішні/admin endpoint-и, коли потрібно.
3. Використовуйте `operationIdFactory` для стабільної генерації SDK.
4. Експортуйте OpenAPI JSON у CI для contract-check/client codegen.
5. Захищайте docs endpoint у production, якщо API приватне.

#### Практичний висновок

Сприймайте Swagger як контрактний артефакт, а не лише UI. Оновлюйте декоратори
та DTO одночасно зі змінами endpoint-ів, щоб уникати розсинхрону документації.

</details>

<details>
<summary>55. Як реалізувати CORS у NestJS і коли потрібні кастомні налаштування?</summary>

#### NestJS

CORS (Cross-Origin Resource Sharing) визначає, які браузерні origin-и можуть
звертатися до вашого API. У NestJS CORS налаштовується на рівні bootstrap
застосунку.

#### Базове увімкнення CORS

```ts
const app = await NestFactory.create(AppModule);
app.enableCors();
```

Для локальної розробки цього зазвичай достатньо, але для production це занадто
широкий доступ.

#### Production-стиль конфігурації CORS

```ts
app.enableCors({
  origin: ['https://app.example.com', 'https://admin.example.com'],
  methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE', 'OPTIONS'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true,
  maxAge: 86400,
});
```

#### Коли потрібні кастомні CORS-налаштування

1. **Кілька frontend-доменів**
   Потрібен явний allowlist для кожного середовища.

2. **Cookie-based auth (`credentials: true`)**
   Потрібен конкретний origin (не `*`) і коректна політика безпечних cookies.

3. **Кастомні headers/токени**
   Потрібно додати необхідні заголовки в `allowedHeaders`.

4. **Складні методи/preflight**
   Треба налаштувати `methods` і переконатися, що `OPTIONS` працює коректно.

5. **Per-tenant або dynamic origin правила**
   Використовуйте function-based origin resolver.

#### Приклад dynamic origin

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

#### Поширені помилки

1. `origin: '*'` разом із `credentials: true` (некоректно/небезпечно для cookie).
2. Ігнорування preflight (`OPTIONS`) у proxy/gateway.
3. Хардкод одного origin для всіх середовищ.
4. Сприйняття CORS як security boundary для небраузерних клієнтів.

#### Практичні рекомендації

1. Тримайте strict origin allowlist у production.
2. Розділяйте CORS-конфіг за середовищами через `ConfigService`.
3. Логуйте заблоковані origin-и для дебагу.
4. Комбінуйте CORS із реальною auth/authz, rate limiting і CSRF-стратегією там,
   де це доречно.

</details>

<details>
<summary>56. Що таке idempotency в контексті REST API і як її забезпечити?</summary>

#### NestJS

Idempotency означає, що повторення одного й того ж запиту багато разів
призводить до того самого фінального стану системи, що й одноразове виконання.

У REST API це критично для надійності при retry, network timeout і дубльованих
клієнтських відправках.

#### HTTP-семантика і idempotency

1. **Зазвичай ідемпотентні за дизайном**
   `GET`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`.

2. **Не ідемпотентний за замовчуванням**
   `POST` (часто створює новий ресурс при кожному виклику).

#### Чому idempotency важливий

1. Безпечні клієнтські повтори після timeout.
2. Захист від дублю дій (подвійний платіж/замовлення).
3. Краща стійкість у distributed systems і at-least-once delivery сценаріях.

#### Як забезпечити idempotency на практиці

1. **Idempotency key патерн (для POST)**
   Клієнт надсилає унікальний ключ (наприклад, у header `Idempotency-Key`).
   Сервер зберігає ключ + fingerprint запиту + відповідь.
   Повтор із тим самим ключем повертає первинний результат замість повторного
   виконання дії.

2. **Обмеження на рівні БД**
   Впроваджуйте унікальність для бізнес-ідентифікаторів
   (`externalPaymentId`, `orderReference` тощо).

3. **Upsert/compare-and-set патерни**
   Використовуйте детерміновані write-операції там, де можливо.

4. **Транзакційна обробка**
   Захищайте багатокрокові записи від часткового дублювання.

#### Нарис реалізації в NestJS

1. Interceptor/guard перевіряє `Idempotency-Key`.
2. Обчислюється fingerprint (route + user + hash payload).
3. Пошук idempotency-запису:
   1. Якщо completed -> повернути збережену відповідь.
   2. Якщо in-progress -> повернути conflict/retry-later політику.
   3. Якщо відсутній -> зарезервувати ключ і виконати handler.
4. Атомарно зберегти фінальну відповідь і повернути її.

#### Мінімальний концептуальний flow

```text
Request -> Idempotency middleware/interceptor
        -> key exists with completed response? return cached response
        -> else execute use case
        -> persist outcome by key
        -> return response
```

#### Поширені помилки

1. Повторне використання ключа для іншого payload (має детектитись і відхилятись).
2. Зберігання ключів без TTL/cleanup.
3. Відсутність scope ключа за tenant/user там, де це потрібно.
4. Повернення різних відповідей на retry з тим самим ключем.

#### Практична рекомендація

Для всіх money/order/subscription endpoint-ів застосовуйте idempotency keys +
unique constraints у БД. Це дає захист від дублювання і на рівні застосунку, і
на рівні persistence.

</details>

<details>
<summary>57. Як реалізувати rate limiting у NestJS? (@nestjs/throttler)</summary>

#### NestJS

Rate limiting контролює, скільки запитів клієнт може зробити за певний проміжок
часу. У NestJS стандартне рішення - `@nestjs/throttler`.

#### Навіщо потрібен rate limiting

1. Захищає API від зловживань і brute-force спроб.
2. Зменшує випадкове перевантаження від "шумних" клієнтів.
3. Покращує справедливий розподіл ресурсів між users/tenants.
4. Додає стійкість до того, як трафік дійде до дорогих залежностей.

#### Крок 1: встановіть і налаштуйте модуль

```ts
import { Module } from '@nestjs/common';
import { ThrottlerModule } from '@nestjs/throttler';

@Module({
  imports: [
    ThrottlerModule.forRoot([
      {
        ttl: 60_000, // 60 секунд
        limit: 100,  // 100 запитів за вікно
      },
    ]),
  ],
})
export class AppModule {}
```

#### Крок 2: підключіть глобальний guard

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

Тепер усі маршрути мають rate limit за замовчуванням.

#### Крок 3: кастомізуйте ліміти на рівні route/controller

Жорсткіший ліміт:

```ts
@Throttle({ default: { limit: 5, ttl: 60_000 } })
@Post('login')
login() {}
```

Пропустити ліміт для health endpoint:

```ts
@SkipThrottle()
@Get('health')
health() {}
```

#### Стратегія ключа (кого саме лімітуємо)

За замовчуванням це зазвичай IP клієнта. У реальних системах часто потрібні:
1. ліміти за user ID (після auth),
2. ліміти за tenant/API key,
3. окремі політики для груп маршрутів.

Для цього можна розширити логіку guard/tracker під кастомні ключі.

#### Нотатка для distributed deployment

У multi-instance середовищі in-memory storage недостатньо для строгих глобальних
лімітів. Потрібен shared storage adapter (наприклад, Redis-backed throttling
store), щоб ліміти були консистентні між репліками.

#### Практичні best practices

1. Робіть жорсткіші ліміти для auth/reset/token endpoint-ів.
2. Повертайте зрозумілі `429 Too Many Requests` відповіді.
3. За можливості віддавайте retry-метадані (`Retry-After`).
4. Моніторте throttle hits по маршрутах/клієнтах і тюньте ліміти.
5. Комбінуйте з WAF/reverse-proxy rate limiting для багатошарового захисту.

</details>

<details>
<summary>58. Як реалізувати request tracing (додавати requestId до кожного запиту)?</summary>

#### NestJS

Request tracing означає додавання унікального `requestId` до кожного вхідного
запиту і його подальшу передачу через логи, відповіді та downstream-виклики.

Це критично для дебагу distributed systems і кореляції подій між сервісами.

#### Цілі request tracing

1. Корелювати всі логи одного запиту.
2. Відстежувати збої через middleware/guards/services/DB/external APIs.
3. Повертати ідентифікатор запиту клієнтам/команді підтримки.

#### Типовий патерн реалізації

1. Middleware читає наявний header (`x-request-id`) або генерує новий UUID.
2. Зберігає ID в об'єкті request.
3. Додає ID у response headers.
4. Logger автоматично включає `requestId` у кожен лог-запис.

#### Приклад middleware

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

Підключіть middleware глобально в `AppModule.configure(...)`.

#### Інтеграція з логуванням

1. Додавайте `requestId` у структуровані логи з interceptors/services.
2. Використовуйте централізовану logger-абстракцію, щоб кожен рядок логів мав
   correlation-поля.

Приклад interceptor-а (таймінг + requestId):

```ts
const req = context.switchToHttp().getRequest();
const requestId = req.requestId;
this.logger.log({ msg: 'request.start', requestId, path: req.url });
```

#### Поширення async context (advanced)

Для глибоких service-layer і фонових async-ланцюгів використовуйте
`AsyncLocalStorage` (або CLS-модуль), щоб мати доступ до `requestId` без ручної
передачі через кожен метод.

#### Downstream propagation

1. Проксіюйте `x-request-id` у вихідні HTTP-виклики.
2. Додавайте request ID у metadata повідомлень для queues/events.
3. Мапте його до trace/span ID, якщо використовуєте OpenTelemetry.

#### Best practices

1. Приймайте upstream request ID від trusted gateways.
2. Генеруйте ID на сервері, якщо його немає.
3. Повертайте ID у кожній error-відповіді для support-діагностики.
4. Тримайте єдину назву заголовка в усіх сервісах.
5. Використовуйте requestId як correlation metadata, не як security token.

</details>

<details>
<summary>59. Як обробити multipart/form-data і завантаження файлів у NestJS?</summary>

#### NestJS

У NestJS (на платформі Express) завантаження файлів зазвичай реалізується через
Multer за допомогою interceptor-ів із `@nestjs/platform-express`.

`multipart/form-data` використовується, коли запит містить файли (і, за потреби,
додаткові поля).

#### Основні будівельні блоки

1. `FileInterceptor()` для одного файлу.
2. `FilesInterceptor()` для кількох файлів в одному полі.
3. `FileFieldsInterceptor()` для кількох іменованих file-полів.
4. `@UploadedFile()` / `@UploadedFiles()` для доступу до розпарсених файлів.

#### Приклад завантаження одного файлу

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

#### Обробка кількох файлів

1. Одне поле:
   `@UseInterceptors(FilesInterceptor('files', 10))`

2. Іменовані поля:
   `@UseInterceptors(FileFieldsInterceptor([{ name: 'avatar', maxCount: 1 }, ...]))`

#### Валідація і вимоги безпеки

1. Обмежуйте максимальний розмір файлів.
2. Перевіряйте MIME-тип і (бажано) фактичну сигнатуру файлу.
3. Санітизуйте назви файлів і не довіряйте клієнтським іменам.
4. Зберігайте файли поза executable/static чутливими шляхами.
5. Для ризикових доменів додавайте malware-сканування.

#### Стратегії зберігання

1. Локальний диск (простий варіант для dev/невеликих деплоїв).
2. Object storage (S3/GCS/MinIO) для масштабованого production.
3. Зберігання в БД - лише для спеціальних кейсів (зазвичай некраще для великих бінарних файлів).

#### Production best practices

1. Для великих файлів віддавайте перевагу direct-to-object-storage upload.
2. У БД зберігайте метадані (owner, key, mime, size, checksum).
3. Використовуйте signed URL для контролю доступу на upload/download.
4. Додавайте auth + rate limits на upload endpoint-и.
5. Впроваджуйте retention/cleanup політики.

</details>

<details>
<summary>60. Як реалізувати compression (gzip/brotli) у NestJS?</summary>

#### NestJS

Compression зменшує розмір response payload і покращує мережеву продуктивність,
особливо для JSON/text-heavy API.

У NestJS (адаптер Express) gzip/brotli зазвичай вмикається через compression
middleware.

#### Базове налаштування (Express)

1. Встановіть `compression`.
2. Зареєструйте middleware у `main.ts`.

```ts
import { NestFactory } from '@nestjs/core';
import compression from 'compression';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    compression({
      threshold: 1024, // стискати відповіді > 1KB
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

Header `Accept-Encoding` від клієнта визначає вибір алгоритму
(`br`, `gzip` тощо, залежно від підтримки runtime/proxy).

#### Де зазвичай відбувається brotli

1. Рівень застосунку (Node middleware/runtime support).
2. Reverse proxy/CDN (Nginx, Cloudflare, Vercel тощо).

У багатьох production-сценаріях proxy/CDN стискає ефективніше, ніж процес
застосунку.

#### Що стискати

1. JSON-відповіді
2. Text/HTML/CSS/JS
3. GraphQL-відповіді

#### Що не стискати

1. Уже стиснуті формати (`.zip`, `.jpg`, `.png`, `.mp4`, `.pdf`)
2. Дуже малі payload (overhead стискання може бути вищим за користь)

#### Operational best practices

1. Використовуйте threshold, щоб пропускати дуже малі відповіді.
2. Переконайтесь, що cache/proxy поважає `Vary: Accept-Encoding`.
3. Вимірюйте CPU overhead проти економії bandwidth.
4. Для high-traffic систем віддавайте перевагу стисненню на proxy/CDN.
5. Враховуйте TLS + compression ризики в чутливих контекстах (сьогодні рідко,
   але дотримуйтесь рекомендацій платформи).

#### Нотатка для Fastify

Якщо використовуєте Fastify adapter, підключайте відповідний Fastify compression
plugin замість Express middleware.

#### Практична рекомендація

Вмикайте compression за замовчуванням для API-відповідей, а далі тюньте threshold
і місце стискання (app vs edge/proxy) за реальним трафіком і CPU-профілем.

</details>

<details>
<summary>61. Як реалізувати helmet і які HTTP-заголовки він встановлює?</summary>

#### NestJS

Helmet - це security middleware, який встановлює захисні HTTP-заголовки для
зменшення поверхні типових веб-атак (XSS, clickjacking, MIME sniffing, витоки
даних через referrer тощо).

У NestJS (Express adapter) його зазвичай підключають глобально в `main.ts`.

#### Базове налаштування

1. Встановіть `helmet`.
2. Зареєструйте як middleware.

```ts
import { NestFactory } from '@nestjs/core';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    helmet({
      // Налаштуйте CSP/HSTS тощо під потреби середовища
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

#### Типові заголовки, які встановлює Helmet (залежить від версії/конфігу)

1. `Content-Security-Policy` (CSP)
2. `Cross-Origin-Opener-Policy`
3. `Cross-Origin-Resource-Policy`
4. `Origin-Agent-Cluster`
5. `Referrer-Policy`
6. `Strict-Transport-Security` (HSTS, коли доречний HTTPS-контекст)
7. `X-Content-Type-Options: nosniff`
8. `X-DNS-Prefetch-Control`
9. `X-Download-Options` (legacy-захист для IE)
10. `X-Frame-Options` (захист від clickjacking)
11. `X-Permitted-Cross-Domain-Policies`
12. `X-XSS-Protection` (legacy-поведінка; сучасні браузери покладаються на CSP)

Точні дефолти можуть відрізнятися залежно від версії Helmet і runtime-середовища.

#### Практичні нотатки з конфігурації

1. **Тюнінг CSP критично важливий**
   Строгий CSP підвищує безпеку, але без налаштування може ламати scripts/styles.

2. **HSTS лише на HTTPS**
   Увімкнюйте обережно на production-доменах; уникайте випадкового lock-in на локалі/dev.

3. **CORS + Helmet**
   Вони вирішують різні задачі; налаштовуйте обидва явно.

4. **Враховуйте reverse proxy**
   Переконайтесь, що trusted proxy/HTTPS termination налаштовані коректно для
   HSTS та загальної security-поведінки.

#### Типовий production-патерн

1. Увімкнути Helmet глобально.
2. Кастомізувати CSP directives під frontend/API поведінку.
3. Тримати окремі профілі конфігурації для dev і production.
4. Перевіряти заголовки через integration-тести та security-скани.

#### Правило практики

Helmet дає сильний базовий hardening, але не є повною безпекою. Комбінуйте його
з auth, валідацією, rate limits, secure cookies і dependency hygiene.

</details>

<details>
<summary>62. Які основні OWASP-вразливості і як від них захиститись?</summary>

#### NestJS

OWASP Top-ризики - це поширені класи веб-уразливостей. У NestJS захист
реалізується шарово: валідація, auth, безпечні дефолти, моніторинг та
інфраструктурний hardening.

#### Основні OWASP-ризики та захисти в контексті NestJS

1. **Broken Access Control**
   1. Використовуйте Guards для authz (`RolesGuard`, policy/ABAC guards).
   2. Перевіряйте ownership при доступі до ресурсів.
   3. Застосовуйте deny-by-default; уникайте неявного доступу.

2. **Cryptographic Failures**
   1. Використовуйте HTTPS всюди.
   2. Хешуйте паролі надійними алгоритмами (argon2/bcrypt із коректною cost).
   3. Зберігайте секрети в secret manager, не в коді.
   4. Шифруйте чутливі дані at rest, коли це потрібно.

3. **Injection (SQL/NoSQL/Command)**
   1. Використовуйте parameterized ORM-запити (TypeORM/Prisma).
   2. Валідовуйте/whitelist-іть input через DTO + `ValidationPipe`.
   3. Уникайте raw-запитів і shell-команд, зібраних рядком із user input.

4. **Insecure Design**
   1. Проводьте threat modeling для критичних флоу (auth, платежі, адмінка).
   2. Закладайте idempotency, rate limits і anti-abuse механіки на етапі дизайну.
   3. Дотримуйтесь least privilege в архітектурних межах.

5. **Security Misconfiguration**
   1. Увімкніть Helmet і строгий CORS.
   2. Вимкніть debug-дефолти у production.
   3. Тримайте production-середовище ізольованим і жорстко налаштованим.

6. **Vulnerable and Outdated Components**
   1. Регулярно оновлюйте залежності.
   2. Запускайте SCA-скани в CI (`npm audit`, Snyk, Dependabot тощо).
   3. Видаляйте невикористані пакети.

7. **Identification and Authentication Failures**
   1. Використовуйте short-lived access token + ротацію refresh token.
   2. Додавайте MFA для high-risk акаунтів.
   3. Забезпечуйте безпечну роботу з cookie/token, lockout/rate-limit для login endpoint-ів.

8. **Software and Data Integrity Failures**
   1. Використовуйте підписані артефакти та довірений CI/CD pipeline.
   2. Перевіряйте сторонні джерела і pin-іть версії.
   3. Контролюйте зміни конфігурації та процеси approve релізів.

9. **Security Logging and Monitoring Failures**
   1. Впроваджуйте структуровані логи з requestId/userId/action/outcome.
   2. Налаштуйте алерти на auth-аномалії та сплески помилок.
   3. Зберігайте stack traces у логах, а не у відповідях клієнту.

10. **Server-Side Request Forgery (SSRF)**
   1. Обмежуйте outbound network destinations.
   2. Валідовуйте й allowlist-іть зовнішні URL.
   3. Блокуйте internal metadata IP-діапазони.

#### Базовий NestJS checklist

1. Глобальний `ValidationPipe` (`whitelist`, `forbidNonWhitelisted`, `transform`).
2. Глобальний exception filter із безпечними error-відповідями.
3. Auth + authorization guards на захищених маршрутах.
4. Rate limiting (`@nestjs/throttler`) на чутливих endpoint-ах.
5. Helmet + строгий CORS-конфіг.
6. Безпечний конфіг із валідацією на старті (Joi/Zod).
7. Dependency/security scanning у CI.

#### Практичний висновок

Безпека - це не один пакет. У NestJS сильна security-позиція досягається
послідовним defense-in-depth на рівні коду, конфігурації, інфраструктури й
операцій.

</details>

<details>
<summary>63. Як використовувати HttpModule (axios) у NestJS для запитів до зовнішніх API?</summary>

#### NestJS

У NestJS зовнішні HTTP-виклики зазвичай виконуються через `HttpModule` з
`@nestjs/axios`, який обгортає Axios і інтегрується з DI.

#### Навіщо використовувати `HttpModule`

1. DI-friendly спільний HTTP-клієнт.
2. Централізована конфігурація (base URL, timeout, headers).
3. Зручне тестування/мокання.
4. Вбудована інтеграція з RxJS (`Observable`-відповіді).

#### Крок 1: зареєструйте `HttpModule`

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

Асинхронний варіант конфігурації:
`HttpModule.registerAsync(...)` із `ConfigService`.

#### Крок 2: інжектіть `HttpService` у провайдер

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

#### Патерн обробки помилок

1. Перехоплюйте Axios-помилки і мапте їх у domain/app exceptions.
2. Не віддавайте raw upstream-помилки напряму клієнтам API.

```ts
try {
  const res = await firstValueFrom(this.http.get('/health'));
  return res.data;
} catch (e: any) {
  const status = e?.response?.status;
  throw new BadGatewayException(`Upstream error: ${status ?? 'unknown'}`);
}
```

#### Production best practices

1. Встановлюйте строгі timeout для всіх outbound-викликів.
2. Додавайте retries/circuit breaker для нестабільних залежностей.
3. Проксіюйте request/correlation ID в headers.
4. Використовуйте типізовані response DTO/адаптери для зовнішніх контрактів.
5. Інструментуйте latency, помилки та upstream status codes.

#### Стратегія тестування

1. Мокайте `HttpService` в unit-тестах.
2. Для integration-тестів використовуйте mock servers (наприклад, nock/wiremock).
3. Явно перевіряйте шляхи timeout/retry/error mapping.

#### Практичний висновок

Сприймайте зовнішній HTTP як ненадійний I/O: централізовано конфігуруйте
`HttpModule`, обгортайте його в окремі client-сервіси і застосовуйте надійні
політики timeout/retry/error.

</details>

<details>
<summary>64. Як додати глобальні interceptors до axios у NestJS? (додавання headers, логування)</summary>

#### NestJS

У NestJS Axios interceptors налаштовуються на інстансі `axiosRef`, який надає
`HttpService` (`@nestjs/axios`). Це дозволяє застосувати глобальну поведінку для
вихідних запитів: headers, логування, таймінги, auth-токени і нормалізацію
помилок.

#### Навіщо використовувати Axios interceptors

1. Централізувати поведінку outbound HTTP.
2. Уникнути повторення headers/auth логіки у кожному виклику.
3. Додати консистентне request/response логування і метрики.
4. Нормалізувати upstream-помилки в одному місці.

#### Типовий патерн реалізації

1. Створіть provider/service, який отримує `HttpService`.
2. У lifecycle init модуля один раз зареєструйте request/response interceptors.
3. Тримайте логіку interceptor-ів легкою та детермінованою.

#### Приклад: глобальні outbound headers + логування

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

Зареєструйте цей provider у модулі, який імпортує `HttpModule`.

#### Важливі production-нотатки

1. Переконайтесь, що interceptors реєструються один раз (уникайте дублювань при
   hot reload/module re-init).
2. Проксіюйте correlation/request ID з inbound request context.
3. Редагуйте/маскуйте секрети (Authorization, API keys) у логах.
4. Тримайте timeout/retry/circuit-breaker стратегію явною (interceptors самі по
   собі не є повноцінним resilience-шаром).

#### Поширені use-case

1. Інжекція auth-токенів із `ConfigService` або token providers.
2. Додавання tenant/context headers для downstream-сервісів.
3. Стандартизація error-об'єктів перед повторним throw.
4. Відправка metrics/traces у observability-системи.

#### Практичний висновок

Сприймайте Axios interceptors як outbound-аналог Nest middleware: одна точка
для наскрізної політики HTTP-клієнта у всіх викликах зовнішніх API.

</details>

<details>
<summary>65. Як правильно типізувати відповідь зовнішнього API у TypeScript?</summary>

#### NestJS

Коректна типізація відповідей зовнішнього API означає, що remote-дані
розглядаються як **недовірені**, доки не пройдуть валідацію, навіть якщо ви
використовуєте TypeScript для зручності розробки.

#### Ключовий принцип

1. Compile-time типи (`interface`/`type`) покращують DX.
2. Runtime-валідація (Zod/class-validator/custom guards) гарантує безпеку.
3. Потрібні обидва підходи разом, а не лише один.

#### Рекомендований патерн

1. Опишіть response DTO/type для очікуваної структури.
2. Отримайте дані через типізований HTTP-виклик.
3. Провалідуйте/розпарсьте дані на boundary.
4. Замапте у внутрішню domain-модель до бізнес-логіки.

#### Приклад з `HttpService` + Zod

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

#### Чому не варто покладатися лише на generics

```ts
this.http.get<MyType>(...)
```

Це лише підказує TypeScript, що ви *очікуєте*; реальний runtime payload від
upstream-сервісу це не перевіряє.

#### Практичні стратегії типізації

1. Використовуйте окремі client-модулі для кожного зовнішнього API.
2. Тримайте upstream DTO окремо від внутрішніх domain entities.
3. Нормалізуйте/трансформуйте зовнішні enum-и та назви полів на boundary.
4. Явно обробляйте nullable/optional поля (`null` з upstream трапляється часто).

#### Best practices обробки помилок

1. Розрізняйте transport-помилки (timeout, 5xx) і schema-помилки.
2. Мапте обидва типи в стабільні внутрішні exceptions.
3. Логуйте метадані upstream-відповідей для діагностики (без витоку секретів).

#### Правило практики

Типізуйте зовнішні відповіді двічі:
1. статичним типом для code intelligence,
2. runtime schema-валідацією для коректності й безпеки.

</details>

<details>
<summary>66. Як реалізувати retry логіку для зовнішніх HTTP-запитів у NestJS?</summary>

#### NestJS

Retry-логіка допомагає обробляти тимчасові збої (timeouts, короткочасні 5xx,
мережеві збої) під час викликів зовнішніх API.

У NestJS retry зазвичай реалізують через RxJS-оператори на `HttpService` або
через resilience-бібліотеки на межі client-сервісу.

#### Коли retries доречні

1. Timeout/network помилки.
2. Тимчасові upstream 5xx.
3. Rate-limit відповіді, коли сервер дає retry-підказки (`429` з `Retry-After`).

#### Коли retries небезпечні

1. Неідемпотентні операції без idempotency keys.
2. Постійні помилки (`400`, `401`, `403`, validation failures).
3. Великі retry-штормові хвилі під час outage upstream.

#### Базовий retry з RxJS

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

#### Рекомендована retry-політика

1. Використовуйте exponential backoff.
2. Додавайте jitter, щоб уникати синхронізованих retry-сплесків.
3. Жорстко обмежуйте максимальну кількість спроб.
4. Повторюйте лише idempotent-операції або idempotency-захищені записи.

#### Поєднуйте retries із захисними механізмами

1. Глобальний timeout на запит.
2. Circuit breaker для тривалих відмов.
3. Rate limiting і bulkheads для outbound-клієнтів.
4. Централізовані метрики: кількість retry, фінальний failure rate, вплив на latency.

#### Практичне правило

Retries мають підвищувати надійність, а не приховувати outage. Робіть їх
вибірковими, обмеженими й observability-friendly.

</details>

<details>
<summary>67. Що таке Circuit Breaker патерн і коли він потрібен?</summary>

#### NestJS

</details>

<details>
<summary>68. Як реалізувати кешування (in-memory, Redis), і коли який підхід використовувати?</summary>

#### NestJS

Кешування зберігає попередньо обчислені/часто запитувані дані, щоб зменшити
latency і навантаження на backend. У NestJS найпоширеніші варіанти - in-memory
cache і Redis cache.

#### In-memory vs Redis

1. **In-memory cache**
   Дані зберігаються в пам'яті одного процесу застосунку.

2. **Redis cache**
   Зовнішній shared cache-сервіс, доступний усім інстансам застосунку.

#### Коли використовувати in-memory cache

1. Single-instance застосунки або локальна розробка.
2. Невеликі, короткоживучі кешовані значення.
3. Наднизька latency для локальних читань.

Обмеження:
1. Не шариться між репліками.
2. Втрачається при рестарті/деплої процесу.
3. Memory pressure впливає на сам процес застосунку.

#### Коли використовувати Redis cache

1. Multi-instance/distributed деплои.
2. Shared cache між сервісами.
3. Потрібна централізована поведінка TTL/invalidation.
4. Вищі вимоги до надійності та observability.

Компроміс:
1. Додається невелика мережна затримка.

#### Варіанти реалізації в NestJS

1. `CacheModule` + cache-manager adapters.
2. Ручний Redis client для розширених патернів.
3. `CacheInterceptor` для response-level кешування на вибраних endpoint-ах.

#### Концептуальний приклад `CacheModule`

In-memory:

```ts
CacheModule.register({
  ttl: 30_000,
  max: 500,
});
```

Redis (adapter-specific конфіг):

```ts
CacheModule.registerAsync({
  useFactory: () => ({
    store: /* redis store adapter */,
    url: process.env.REDIS_URL,
    ttl: 60_000,
  }),
});
```

#### Що кешувати

1. Read-heavy дані, що рідко змінюються.
2. Дорогі обчислювані агрегати.
3. Відповіді зовнішніх API з чітко допустимою застарілістю.

#### Що не варто кешувати бездумно

1. Дуже волатильні дані без плану invalidation.
2. Security-sensitive per-user дані без scoped keys.
3. Write-critical шляхи, де застарілі читання неприйнятні.

#### Ключові практики дизайну

1. Використовуйте явне іменування ключів (`user:{id}`, `catalog:v2:{region}`).
2. Задавайте TTL усвідомлено для кожного типу даних.
3. Додавайте cache-aside патерн:
   read -> miss -> load source -> set cache -> return.
4. Плануйте invalidation на writes/events.
5. Моніторте hit ratio, evictions і вплив stale-read.

#### Правило практики

In-memory підходить для простих single-node кейсів. Для production із
кількома інстансами або shared-state потребами переходьте на Redis-backed cache.

</details>

<details>
<summary>69. Що таке інвалідація кешу і як правильно її реалізувати?</summary>

#### NestJS

</details>

<details>
<summary>70. Коли в NestJS варто використовувати Observables замість Promise?</summary>

#### NestJS

Використовуйте Observables у NestJS, коли потрібні **стріми, скасування,
композиція кількох async-подій або reactive-оператори**. Promises краще підходять
для простих одноразових async-операцій.

#### Ключова різниця

1. **Promise**
   Одне майбутнє значення (або помилка), резолвиться один раз.

2. **Observable**
   Лінивий стрім 0..N значень у часі, з потужними RxJS-операторами та
   підтримкою скасування.

#### Коли Observables кращий вибір

1. **Streaming-сценарії**
   Server-Sent Events, websocket-подібні флоу, chunked-відповіді.

2. **Композиція кількох async-джерел**
   Комбінування таймерів, HTTP-викликів, user events і retry через оператори.

3. **Складна retry/backoff/circuit поведінка**
   RxJS-оператори (`retryWhen`, `timeout`, `catchError`, `switchMap` тощо).

4. **Скасування виконання**
   `unsubscribe` зупиняє роботу і вивільняє ресурси.

5. **Особливості екосистеми Nest**
   Interceptors і `HttpService` природно повертають Observables.

#### Коли краще Promise

1. Один запит -> одна відповідь (DB/API виклик).
2. Проста service-логіка через `async/await`.
3. Команда не використовує глибоко reactive-підхід.

#### Практичні приклади в NestJS

1. `HttpService.get(...)` повертає `Observable<AxiosResponse<T>>`.
2. SSE endpoint-и часто повертають `Observable<MessageEvent>`.
3. Message patterns у мікросервісах можуть працювати як reactive-стріми.

#### Interop-патерн

Якщо код пишеться в `async/await`, але ви отримали Observable:

```ts
const response = await firstValueFrom(this.http.get('/users'));
```

Якщо потрібне лише одне значення зі стріму, конвертуйте явно
(`firstValueFrom` або `lastValueFrom`) і тримайте межі чіткими.

#### Практичне правило вибору

1. Потрібне одне значення один раз -> Promise (`async/await`).
2. Потрібні стріми/retry-композиція/скасування -> Observable.

По можливості тримайте один стиль на межі модуля, щоб не створювати зайву
асинхронну складність.

</details>

<details>
<summary>71. У чому різниця між async/await і RxJS для роботи з асинхронною логікою, і коли який підхід використовувати?</summary>

#### NestJS

</details>

<details>
<summary>72. Як уникнути блокування event loop у NestJS і підтримувати продуктивність?</summary>

#### NestJS

NestJS працює на Node.js event loop. Якщо блокувати loop CPU-важкими або
синхронними операціями, затримка зростає для всіх одночасних запитів.

#### Що блокує event loop

1. Важкі синхронні CPU-задачі (хешування великих payload, обробка image/video).
2. Великі синхронні цикли JSON parse/stringify.
3. Синхронні filesystem API (`fs.readFileSync` тощо) в request path.
4. Довгі tight loops без yield.
5. Дорогі regex/backtracking і неефективні алгоритми.

#### Практичні стратегії уникнення блокування

1. **Віддавайте перевагу async I/O API**
   Використовуйте неблокуючі filesystem/network/DB операції.

2. **Виносьте CPU-heavy роботу з request thread**
   1. Worker threads (`worker_threads`)
   2. Background jobs/queues (BullMQ, RabbitMQ тощо)
   3. Окремі processing-сервіси

3. **Використовуйте streaming для великих payload**
   Уникайте буферизації великих файлів/об'єктів у пам'яті.

4. **Пагінуйте та діліть роботу на чанки**
   Обробляйте великі набори даних батчами замість одного великого sync-проходу.

5. **Кешуйте дорогі обчислення**
   Повторно використовуйте результати, де можливо.

#### Архітектурні патерни NestJS

1. Тримайте контролери "тонкими"; важкі задачі делегуйте в async workers.
2. Використовуйте черги для email/PDF/report/media conversion задач.
3. Налаштовуйте timeout і backpressure-політики для зовнішніх викликів.
4. Додавайте rate limiting на дорогих endpoint-ах.

#### Сигнали блокування event loop

1. Ріст p95/p99 latency навіть при помірному трафіку.
2. Низький CPU idle при слабкому throughput.
3. Затримані таймери та повільні health checks.
4. Зростання event loop lag метрик.

#### Корисні operational інструменти

1. Моніторинг event loop lag (`perf_hooks`, APM-інструменти).
2. CPU profiling/flamegraphs для hot paths.
3. Дашборди latency та payload-size на рівні endpoint-ів.

#### Поширені помилки

1. Синхронні crypto/compression операції у request handlers.
2. Генерація великих звітів inline у HTTP-запиті.
3. Читання великих файлів у пам'ять замість streaming.
4. Ігнорування algorithmic complexity у циклах по великих масивах.

#### Правило практики

Request thread має оркеструвати, а не важко обчислювати. Тримайте його
неблокуючим і делегуйте дорогі задачі в async-інфраструктуру.

</details>

<details>
<summary>73. Як оптимізувати latency (p95 / p99) і що впливає на ці метрики?</summary>

#### NestJS

</details>

<details>
<summary>74. Як використовувати cluster mode у Node.js разом з NestJS для масштабування?</summary>

#### NestJS

Cluster mode запускає кілька worker-процесів Node.js на одній машині, що дає
NestJS-застосунку змогу використовувати кілька CPU-ядер замість одного event loop.

#### Навіщо використовувати cluster mode

1. Краще використання CPU на multi-core серверах.
2. Вищий throughput для CPU/mixed workload.
3. Ізоляція на рівні процесів (падіння одного воркера не зупиняє всі).

#### Базова ідея налаштування cluster

1. Primary-процес форкає `N` worker-ів (`N` зазвичай = кількість CPU-ядер).
2. Кожен worker піднімає Nest-застосунок на тому ж порту.
3. Node розподіляє вхідні з'єднання між воркерами.

#### Приклад bootstrap (концептуально)

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
    cluster.fork(); // naive auto-restart
  });
} else {
  bootstrapWorker();
}
```

#### Важливі production-моменти

1. **Statelessness**
   In-memory стан окремий для кожного воркера і не шариться.
   Для shared sessions/cache/locks використовуйте Redis/DB.

2. **WebSockets**
   Потрібні sticky sessions або зовнішній pub/sub adapter для консистентності
   між воркерами.

3. **Rate limiting/cache**
   In-memory реалізації стають неконсистентними між воркерами.
   Краще використовувати Redis-backed stores.

4. **Graceful shutdown**
   Обробляйте SIGTERM/SIGINT і коректно дренуйте з'єднання в кожному воркері.

5. **Observability**
   Додавайте worker ID/process ID у логи та метрики.

#### Cluster vs containers/orchestrators

1. Cluster масштабує вертикально в межах одного хоста.
2. Kubernetes/PM2/systemd replicas масштабує горизонтально між хостами.
3. Багато команд спочатку покладаються на горизонтальне масштабування, а cluster
   додають за потреби.

#### Коли cluster mode доречний

1. Bare-metal/VM деплои з multi-core CPU.
2. Потрібен додатковий throughput без негайних infra-змін.
3. Застосунок переважно stateless і готовий до multi-process поведінки.

#### Правило практики

Cluster може підвищити throughput на одному хості, але це не заміна
distributed-архітектурі. Поєднуйте його із зовнішнім зберіганням стану та
надійним process management.

</details>

<details>
<summary>75. Як реалізувати cron-задачі у NestJS через @nestjs/schedule?</summary>

#### NestJS

</details>

<details>
<summary>76. Що таке EventEmitter у NestJS і чим він відрізняється від черг (Bull)?</summary>

#### NestJS

`EventEmitter` у NestJS (`@nestjs/event-emitter`) - це in-process pub/sub
механізм для внутрішньої комунікації між модулями. Він швидкий і простий, але
не забезпечує надійне збереження подій при падінні/перезапуску процесу.

Черги Bull/BullMQ - це персистентні системи обробки job-ів (зазвичай на Redis),
призначені для фонового виконання, retry і надійності.

#### Ключова різниця

1. **EventEmitter**
   1. In-memory, у межах одного процесу.
   2. Fire-and-forget модульні події.
   3. Без durable persistence за замовчуванням.

2. **Bull/BullMQ**
   1. Персистентне зберігання черги (Redis).
   2. Job-и обробляються фоновими воркерами.
   3. Є retries, delays, backoff, concurrency і monitoring.

#### Коли використовувати EventEmitter

1. Внутрішні domain events в межах одного інстансу сервісу.
2. Легкі side effects (тригер audit log, сигнал invalidation кешу).
3. Некритичне async-розв'язування компонентів, де допустима епізодична втрата події.

#### Коли використовувати Bull/BullMQ

1. Критичні задачі, які мають переживати рестарти.
2. Довгі/важкі job-и (email, звіти, обробка медіа).
3. Потрібні retry/backoff і dead-letter обробка.
4. Потрібне згладжування навантаження і контроль concurrency.

#### Порівняння моделі надійності

1. **EventEmitter**
   Якщо застосунок впав після emit і до виконання handler-а, подія може
   загубитись.

2. **Queue**
   Job збережений персистентно; воркер може відновити обробку пізніше з retry-політиками.

#### Компроміс latency і складності

1. EventEmitter:
   Нижча latency, нижча операційна складність.

2. Queue:
   Трохи вища latency і складність інфраструктури, зате значно вища надійність.

#### Практичний патерн у NestJS

1. Емітьте локальні domain events для миттєвих некритичних реакцій.
2. Ставте durable background jobs у чергу для важливої/дорогої роботи.
3. Для міжсервісної інтеграції використовуйте message brokers/events, а не лише
   in-process EventEmitter.

#### Правило практики

Якщо втрата події неприйнятна, використовуйте Bull/BullMQ (або broker-backed
messaging), а не plain EventEmitter.

</details>

<details>
<summary>77. Як реалізувати внутрішню event-driven комунікацію між модулями через EventEmitter2?</summary>

#### NestJS

</details>

<details>
<summary>78. Як реалізувати фонові задачі за допомогою Bull або BullMQ?</summary>

#### NestJS

Фонові задачі в NestJS використовують, щоб винести важку або не термінову роботу
з request/response шляху (email, звіти, обробка медіа, sync-задачі).

Bull/BullMQ надають Redis-backed durable черги з retries, delays і контролем
конкурентності воркерів.

#### Типова архітектура

1. API/сервіс швидко ставить job у чергу.
2. Worker/processor асинхронно обробляє job.
3. Стан job відстежується (`waiting`, `active`, `completed`, `failed`).

#### Крок 1: зареєструйте queue module

Налаштування модуля в стилі Bull:

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

#### Крок 2: продюсинг job-ів

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

#### Крок 3: обробка job-ів у processor

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

#### Нотатка про BullMQ

BullMQ використовує новіші API (`Queue`, `Worker`, `QueueEvents`) і рекомендований
для сучасних екосистем. Концептуальний флоу той самий:
producer -> Redis queue -> worker.

#### Production best practices

1. Робіть job-и ідемпотентними (безпечними для retry).
2. Явно задавайте attempts/backoff і політики обробки помилок.
3. Використовуйте окремі worker-процеси для важких черг.
4. Моніторте глибину черги, час обробки та failure rate.
5. Впроваджуйте dead-letter/retry analysis workflow для poisoned jobs.
6. Обережно версіонуйте payload-и/контракти job-ів.

#### Поширені помилки

1. Запуск важкої job-логіки тільки в API-процесі.
2. Відсутність retry/backoff стратегії (або безкінечні retry).
3. Неідемпотентні side effects, що дають дублікати на retry.
4. Відсутність observability для failed jobs.

#### Правило практики

Якщо робота повільна, потребує retry або не критична для миттєвої відповіді -
ставте її в чергу. Тримайте request path швидким, а обробку делегуйте воркерам.

</details>

<details>
<summary>79. Як проєктувати ідемпотентні джоби (черги задач), щоб уникати дублювання виконання?</summary>

#### NestJS

Ідемпотентний дизайн job-ів означає: багаторазове виконання тієї самої задачі
дає той самий фінальний стан, що й одноразове виконання.

Для queue-систем це обов'язково, бо retries, рестарти воркерів і семантика
доставки можуть спричиняти дублікати виконання.

#### Чому виникають дублікати

1. Воркер падає після side effect, але до ACK.
2. Retry після timeout/network partition.
3. Ручні requeue/replay операції.
4. Гонки між кількома консюмерами.

#### Базові стратегії ідемпотентності

1. **Business idempotency key**
   Додавайте стабільний унікальний ключ операції
   (`paymentId`, `orderId:action`).

2. **Deduplication store**
   Зберігайте оброблені ключі/статуси в DB/Redis з унікальним обмеженням.

3. **Atomic check-and-set**
   Гарантуйте "first execution wins" через транзакцію/lock/unique insert.

4. **Outbox/inbox patterns**
   Ведіть облік оброблених message ID, щоб уникати повторних side effects.

5. **Idempotent side-effect API**
   Використовуйте idempotency keys зовнішнього провайдера, якщо підтримується.

#### Практичний job flow

1. Job стартує з `idempotencyKey`.
2. Спроба атомарно зарезервувати ключ:
   1. Якщо вже `completed` -> завершити успішно (no-op).
   2. Якщо зарезервовано зараз -> продовжити.
3. Виконати side effects.
4. Позначити ключ як `completed` з метаданими результату.
5. У разі помилки зберегти retry-політику, не ламаючи семантику idempotency-запису.

#### Приклад моделі ключа

1. `job_key` (unique)
2. `status` (`processing`, `completed`, `failed`)
3. `updated_at`
4. опційно `result_hash` / `external_reference`

#### Техніки на рівні черги

1. Встановлюйте детермінований `jobId` при enqueue
   (у багатьох engine це запобігає дублю enqueue).
2. Використовуйте обмежені retries + backoff.
3. Уникайте паралельної обробки однієї сутності (partitioning/locking).

#### Практичні підказки для NestJS/Bull

1. Ставте idempotency guard на старті processor-а, не лише на producer-стороні.
2. По можливості тримайте processor транзакційним.
3. Для зовнішніх викликів прокидуйте idempotency header/key downstream.
4. Логуйте структуровано: key + attempt + outcome.

#### Поширені помилки

1. Припущення про "exactly once" доставку з черги.
2. Виконання side effects до резервування idempotency-ключа.
3. Ключування випадковим UUID на кожному retry (ламає deduplication).
4. Надто раннє видалення idempotency-записів.

#### Правило практики

Проєктуйте кожен background job як at-least-once delivered. Безпечними retries
робить саме бізнес-ідемпотентність на межі операції.

</details>

<details>
<summary>80. Як реалізувати WebSockets у NestJS?</summary>

#### NestJS

WebSockets у NestJS реалізуються через Gateway, зазвичай із пакетом
`@nestjs/websockets` та адаптером Socket.IO (найпоширеніший дефолтний підхід).

#### Базові концепції

1. **Gateway**
   Точка входу WebSocket (подібна до ролі контролера в HTTP).

2. **Events/messages**
   Клієнт відправляє події з payload; сервер обробляє і відповідає/емітить події.

3. **Lifecycle hooks**
   Обробка connect/disconnect та ініціалізації сервера.

#### Базовий приклад gateway

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

#### Патерни кімнат і broadcast

1. Приєднання до кімнати: `client.join(roomId)`.
2. Відправка в кімнату: `server.to(roomId).emit(...)`.
3. Відправка всім: `server.emit(...)`.
4. Відповідь тільки відправнику: `client.emit(...)`.

#### Валідація і безпека

1. Валідовуйте payload повідомлень (DTO/pipes).
2. Автентифікуйте з'єднання (token/session під час handshake).
3. Авторизуйте доступ до кімнат для кожної події.
4. Додавайте rate limiting/throttling для "шумних" подій.

#### Production-моменти

1. Для multi-instance масштабування потрібен adapter/pub-sub
   (наприклад, Redis adapter) для міжвузлової доставки подій.
2. Використовуйте sticky sessions/load balancer стратегію, якщо цього вимагає транспорт.
3. Відстежуйте кількість з'єднань, throughput подій і причини disconnect.
4. Тримайте handlers легкими; важку роботу виносьте в queues/workers.

#### Правило практики

WebSockets використовуйте для low-latency двосторонніх фіч (чат, live updates,
presence). Контракти протоколу робіть явними й захищайте так само, як будь-який
публічний API.

</details>

<details>
<summary>81. Як реалізувати автентифікацію у WebSocket Gateway?</summary>

#### NestJS

Автентифікацію WebSocket у NestJS зазвичай виконують під час handshake, а потім
додатково перевіряють на рівні кожної події через guards/перевірки авторизації.

#### Типовий флоу автентифікації

1. Клієнт передає токен (JWT/session) у handshake:
   `auth`, headers або query params (краще `auth`/headers).
2. Сервер валідує токен у gateway middleware/guard.
3. Контекст автентифікованого користувача додається в socket (`client.data.user`).
4. Наступні message handlers використовують цей контекст для авторизації.

#### Приклад: автентифікація під час підключення

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

    const user = await this.authService.verifyAccessToken(token); // кидає помилку, якщо токен невалідний
    client.data.user = user;
  }

  @SubscribeMessage('chat.send')
  async onSend(
    @ConnectedSocket() client: Socket,
    @MessageBody() payload: { roomId: string; text: string },
  ) {
    const user = client.data.user;
    // тут перевіряємо доступ користувача до room
    return { ok: true, userId: user.id, text: payload.text };
  }
}
```

#### Авторизація подій через guard

1. Використовуйте `WsGuard`, щоб валідувати auth context для кожної події.
2. Комбінуйте з role/policy checks (членство в room, tenant scope, permissions).

#### Best practices безпеки

1. Віддавайте перевагу короткоживучим access tokens.
2. Для чутливих подій повторно перевіряйте авторизацію, не лише при connect.
3. Обробляйте expiry/revocation токена (disconnect або повторна автентифікація).
4. Не довіряйте user ID, надісланому клієнтом у payload; використовуйте auth context socket.
5. Додавайте throttling/rate limits для чутливих до auth подій.

#### Нотатки про масштабування

1. У multi-instance сетапах використовуйте спільну стратегію перевірки session/token.
2. Якщо presence/rooms розподілені, використовуйте Redis adapter для синхронізації state між нодами.

#### Правило

Автентифікацію робіть один раз під час handshake (ефективність), а
авторизацію — на кожній події (безпека). Потрібні обидва рівні.

</details>

<details>
<summary>82. Які підходи використовують для масштабування real-time систем?</summary>

#### NestJS

Масштабування real-time систем вимагає одночасно контролювати три виміри:
1. масштаб зʼєднань,
2. пропускну здатність повідомлень,
3. консистентність стану між нодами.

#### Ключові підходи до масштабування

1. **Горизонтальне масштабування gateway-інстансів**
   Запускайте кілька реплік WebSocket gateway за load balancer.
2. **Sticky sessions (коли потрібно)**
   Забезпечуйте, щоб той самий клієнт залишався на тій самій ноді, якщо
   транспорт/модель сесій потребує affinity.
3. **Pub/Sub adapter для cross-node broadcast**
   Використовуйте Redis adapter (або еквівалент), щоб події з однієї ноди
   доходили до клієнтів на інших нодах.
4. **Винесений спільний state**
   Зберігайте metadata presence/rooms/session у Redis/DB, а не лише в памʼяті процесу.
5. **Backpressure і rate limiting**
   Обмежуйте шумних клієнтів, контролюйте fan-out bursts і захищайте downstream-системи.

#### Архітектурні патерни

1. **Gateway tier + worker tier**
   Gateways обробляють зʼєднання; важку обробку виносьте в queue workers.
2. **Partitioning каналів/кімнат**
   Діліть high-volume потоки за tenant/region/topic.
3. **Event-driven backbone**
   Для durable або high-throughput розподілу подій використовуйте брокери
   (Redis Streams/Kafka/NATS), коли простого pub/sub недостатньо.
4. **Оптимізація fan-out**
   Попередньо обчислюйте множини отримувачів і уникайте дорогих DB lookup на кожне повідомлення.

#### Техніки продуктивності та надійності

1. Використовуйте компактні payload повідомлень і уникайте надто великих подій.
2. Застосовуйте heartbeats/ping-pong із адекватними timeout.
3. Реалізуйте reconnect + replay стратегію для пропущених критичних повідомлень.
4. Додавайте circuit breakers/timeout для зовнішніх залежностей.
5. Моніторте p95/p99 latency доставки подій і drop rates.

#### Обовʼязкова операційна observability

1. Кількість активних зʼєднань на ноду.
2. Повідомлення/сек вхідні та вихідні.
3. Розподіл розмірів room і hot rooms.
4. Lag у cross-node pub/sub.
5. Причини error/disconnect і частка успішних reconnect.

#### NestJS-специфічний стек реалізації (типово)

1. `@WebSocketGateway` для real-time endpoint.
2. Redis adapter для multi-instance propagation подій.
3. Bull/BullMQ для винесення важких async задач.
4. `@nestjs/throttler` або custom guards для контролю зловживань.

#### Правило

Масштабування real-time — це не просто «додати більше pod». Потрібно
поєднати горизонтальні gateway, спільний pub/sub/state і суворий контроль потоку,
щоб latency залишалася передбачуваною.

</details>

<details>
<summary>83. Які підходи до інтеграції GraphQL у NestJS (code-first vs schema-first), і в чому їх різниця?</summary>

#### NestJS

NestJS підтримує два підходи до інтеграції GraphQL:
1. **Code-first**
2. **Schema-first**

Обидва підходи підходять для production. Різниця в тому, де спочатку
визначається API contract: у TypeScript класах/декораторах чи в `.graphql`
SDL-файлах.

#### Підхід code-first

Типи GraphQL і resolvers описуються в TypeScript через декоратори, а схема
генерується автоматично.

Типовий стиль:
1. `@ObjectType()`, `@Field()`, `@InputType()`
2. `@Resolver()`, `@Query()`, `@Mutation()`

Плюси:
1. Одна мова (TS) для застосунку і схеми.
2. Сильна типізація та зручний refactor у IDE.
3. Менше дублювання між DTO і моделлю схеми.

Мінуси:
1. Читабельність схеми для стейкхолдерів не з TS може бути нижчою.
2. Згенеровану схему все одно потрібно ретельно review/version.

#### Підхід schema-first

Схема описується у `.graphql` файлах (SDL), а resolvers реалізуються в TS.

Плюси:
1. Contract-first workflow (добре для API governance).
2. SDL явний і зручний для cross-team review.
3. Добре підходить, коли схема спільна для різних мов/команд.

Мінуси:
1. Можливе дублювання між SDL і TS типами.
2. Потрібна дисципліна синхронізації, щоб уникати drift.

#### Приклади налаштування NestJS (концептуально)

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

#### Як обирати між ними

1. Обирайте **code-first**, якщо:
   1. Команда TypeScript-центрична.
   2. Важлива швидкість ітерацій.
   3. Схемою переважно володіє backend-команда.
2. Обирайте **schema-first**, якщо:
   1. API contract широко керується/шерується.
   2. Кілька реалізацій/споживачів залежать від SDL.
   3. Основний процес — contract review/versioning.

#### Практична рекомендація

Для більшості NestJS-команд code-first дає найшвидшу розробку і сильну
типізацію. Schema-first варто брати там, де ключові contract governance і
cross-team ownership SDL.

</details>

<details>
<summary>84. Що таке resolvers у GraphQL і чим вони відрізняються від контролерів REST?</summary>

#### NestJS

Resolvers у GraphQL — це функції, які резолвлять поля в GraphQL schema.
Це execution layer, що надає дані для queries, mutations і nested object fields.

У NestJS resolvers визначаються через `@Resolver()` і декоратори методів,
наприклад `@Query()`, `@Mutation()` і `@ResolveField()`.

#### Що роблять resolvers

1. Обробляють GraphQL operations (`query`, `mutation`, subscriptions за потреби).
2. Ліниво резолвлять вкладені поля (відповідно до запитаного selection set).
3. Використовують context (auth user, request metadata, loaders).
4. Делегують business logic у сервіси.

#### Чим resolvers відрізняються від REST контролерів

1. **Форма API**
   REST контролери відкривають багато URL endpoint.
   GraphQL resolver зазвичай працює через один endpoint зі schema-driven operations.
2. **Вибірка даних**
   REST повертає фіксовану response для endpoint.
   GraphQL динамічно повертає поля, обрані клієнтом.
3. **Модель виконання**
   REST контролер зазвичай формує всю response одразу.
   GraphQL resolver tree може виконувати багато field resolvers.
4. **Over/under-fetching**
   У REST часто потрібні компроміси в дизайні endpoint.
   GraphQL зменшує over/under-fetching через query selection sets.
5. **Підхід до versioning**
   У REST частіше явне versioning API.
   У GraphQL схема зазвичай еволюціонує через deprecations і additive changes.

#### Приклад resolver у NestJS

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

#### Best practices

1. Тримайте resolvers thin; business logic виносьте в сервіси.
2. Використовуйте DataLoader/batching, щоб уникати N+1 у nested fields.
3. Валідуйте args/inputs і забезпечуйте authz через guards/context.
4. Проєктуйте schema types навколо domain language, а не напряму від DB tables.

#### Правило

Resolvers — це GraphQL-аналог контролерів, але з field-level execution і
семантикою client-driven data selection.

</details>

<details>
<summary>85. Як у GraphQL працювати з context і реалізувати авторизацію через нього?</summary>

#### NestJS

У NestJS GraphQL `context` — це per-request контейнер, який передає request
metadata (user, headers, requestId, loaders, tenant info) у resolvers і guards.

Авторизація зазвичай реалізується так:
1. автентифікуємо користувача в context,
2. застосовуємо правила доступу через GraphQL-aware guards/policies.

#### Крок 1: наповнити GraphQL context

Під час конфігурації `GraphQLModule` зробіть request-дані доступними в context:

```ts
GraphQLModule.forRoot({
  autoSchemaFile: true,
  context: ({ req, res }) => ({ req, res, requestId: req.headers['x-request-id'] }),
});
```

Якщо JWT auth middleware/strategy додає `req.user`, це автоматично доступне
через GraphQL context.

#### Крок 2: використати context у resolver

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

#### Крок 3: авторизувати через GraphQL guard

Використайте `GqlExecutionContext`, щоб читати `req.user` у guard:

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

Застосування:

```ts
@UseGuards(GqlAuthGuard)
@Query(() => User)
me(@Context() ctx: any) {
  return ctx.req.user;
}
```

#### Fine-grained авторизація

1. Role-based checks через metadata + guard (`@Roles(...)`).
2. Policy/ABAC checks через subject-action-resource service.
3. Field-level авторизація в `@ResolveField()` за потреби.

#### Best practices

1. Тримайте context мінімальним, але достатнім (user, requestId, loaders, tenant).
2. Автентифікацію робіть один раз на request, авторизацію — на операцію/поле.
3. Використовуйте DataLoaders у context для запобігання N+1.
4. Не довіряйте user identifiers від клієнта; використовуйте лише authenticated context.

#### Правило

GraphQL context — це довірений request-envelope. Кладіть туди identity, а потім
застосовуйте авторизацію через guards/policies, побудовані на цьому context.

</details>

<details>
<summary>86. Які транспортні протоколи та брокери повідомлень підтримуються (Kafka, Redis, gRPC, NATS) і в чому їх відмінності?</summary>

#### NestJS

NestJS мікросервіси підтримують кілька transport-рішень, зокрема Kafka, Redis,
gRPC і NATS. Кожне має різну delivery-семантику, performance profile і use cases.

#### Порівняння на високому рівні

1. **Kafka**
   Розподілений commit-log broker з високим throughput, durable retention,
   consumer groups і можливістю replay.
2. **Redis transport (pub/sub або streams-based patterns)**
   Дуже швидкий, простий і низьколатентний messaging; durability/ordering
   залежать від обраного Redis-патерну і налаштування.
3. **gRPC**
   RPC-протокол поверх HTTP/2 з Protobuf contracts; добре підходить для
   сильно типізованих синхронних service-to-service викликів.
4. **NATS**
   Легкий високопродуктивний messaging-сервер; ефективний для low-latency
   pub/sub і request/reply, з optional persistence через JetStream.

#### Коли що обирати

1. **Kafka**
   1. Event streaming і audit trails.
   2. Async pipelines з високим throughput.
   3. Потрібні replay/history і масштабування consumers.
2. **Redis**
   1. Простий легковаговий event fan-out.
   2. Messaging-патерни поруч із кешем.
   3. Невеликий операційний overhead для менших систем.
3. **gRPC**
   1. Low-latency внутрішній RPC зі строгими контрактами.
   2. Polyglot мікросервіси, яким потрібні generated clients/stubs.
   3. Bidirectional streaming RPC сценарії.
4. **NATS**
   1. Швидкий cloud-native messaging.
   2. Request/reply і pub/sub з мінімальним footprint.
   3. JetStream, коли потрібні durability/ack/replay.

#### Важливі семантичні відмінності

1. **Стиль комунікації**
   Kafka/NATS/Redis: асинхронні event/message-driven патерни.
   gRPC: прямий RPC request/response (більше sync-орієнтований).
2. **Durability/replay**
   Kafka: сильний durable log і replay by design.
   NATS core: ephemeral, якщо не ввімкнено JetStream.
   Redis pub/sub: за замовчуванням ephemeral.
   gRPC: немає broker persistence layer (RPC-семантика виклику).
3. **Contract model**
   gRPC використовує Protobuf-first strict schemas.
   Broker-based transports часто покладаються на message schema conventions
   (Avro/JSON/Protobuf), які забезпечуються командою/інструментами.

#### Практичні поради для дизайну в NestJS

1. Використовуйте **gRPC** для синхронних внутрішніх API зі строгою типізацією.
2. Використовуйте **Kafka/NATS/Redis** для асинхронних декомпозованих workflow.
3. Для критичних business events з вимогами replay/audit обирайте **Kafka** або
   persistent патерни **NATS JetStream**.
4. Стандартизуйте message envelopes (`eventName`, `version`, `correlationId`, `payload`).
5. Додавайте observability для lag, retry, DLQ і health consumer-ів.

#### Правило

Обирайте transport насамперед за failure model і delivery guarantees, а не лише
за сирим throughput.

</details>

<details>
<summary>87. Як правильно проєктувати event-driven архітектуру і основні принципи такої системи?</summary>

#### NestJS

Event-driven architecture (EDA) організовує систему навколо подій: фактів, що
щось сталося (`order.created`, `payment.failed` тощо). Producers публікують
події, consumers реагують асинхронно.

#### Ключові принципи

1. **Loose coupling**
   Producers не залежать від внутрішньої реалізації consumers.
2. **Asynchronous communication**
   Сервіси координуються через події, а не через blocking RPC, де це можливо.
3. **Single source of truth per domain**
   Кожен сервіс володіє своїми даними й публікує domain events після зміни state.
4. **Event contract governance**
   Події — це versioned contracts зі стабільною схемою і чіткою семантикою.
5. **Idempotent consumers**
   Обробники мають безпечно обробляти дублікати delivery.
6. **Observability і traceability**
   Correlation IDs, metadata подій і processing metrics є обовʼязковими.

#### Рекомендації з дизайну подій

1. Називайте події як факти в минулому часі: `invoice.paid`, `user.email_changed`.
2. Додавайте metadata:
   `eventId`, `eventType`, `occurredAt`, `version`, `correlationId`, `source`.
3. Тримайте payload сфокусованим на бізнес-сенсі, а не на внутрішній DB-структурі.
4. Віддавайте перевагу additive schema evolution; уникайте breaking changes.

#### Модель доставки і консистентності

1. У більшості broker-систем закладайте at-least-once delivery.
2. Використовуйте eventual consistency між сервісами.
3. Для failed processing застосовуйте retries + DLQ.
4. Використовуйте outbox pattern, щоб уникнути розриву
   «DB write succeeded, but event publish failed».

#### Будівельні блоки реалізації в NestJS

1. Внутрішні модульні події: `@nestjs/event-emitter` (in-process).
2. Durable async обробка: Bull/BullMQ queues.
3. Cross-service messaging: Kafka/NATS/Redis transport adapters.
4. Consumer handlers із validation + idempotency checks.

#### Anti-patterns, яких варто уникати

1. Event payload з величезними mutable object snapshots.
2. Прихована синхронна звʼязаність, замаскована під події.
3. Відсутність стратегії versioning для schema.
4. Відсутність replay/recovery плану при збоях consumers.
5. Використання подій як команд (якщо це явно не змодельовано).

#### Практичний архітектурний flow

1. Command оновлює domain state у сервісі-власнику.
2. Власник емітить domain event (транзакційно через outbox).
3. Broker доставляє подію зацікавленим consumers.
4. Consumers оновлюють власні read models/side effects.
5. Monitoring відстежує lag, failures і DLQ.

#### Правило

Проєктуйте події як durable business facts, а не як implementation details.
Надійність забезпечують idempotency, дисципліна контрактів і операційна
observability.

</details>

<details>
<summary>88. Як працювати з distributed transactions у мікросервісах? (Saga pattern, eventual consistency)</summary>

#### NestJS

У мікросервісах класична ACID-транзакція через кілька сервісів/баз зазвичай
непрактична. Замість цього використовують **eventual consistency** і патерни
координації, наприклад **Saga**.

#### Чому distributed transactions складні

1. Сервіси мають окремі бази даних.
2. Мережеві збої та частковий успіх — нормальна ситуація.
3. Глобальні транзакції в стилі 2PC зменшують доступність і додають складність.

#### Базовий підхід: Saga pattern

Saga — це послідовність локальних транзакцій між сервісами, керована
результатами success/failure на кожному кроці.

Два варіанти:
1. **Choreography**
   Сервіси реагують на події без центрального координатора.
2. **Orchestration**
   Виділений orchestrator керує порядком кроків і компенсаціями.

#### Ключові концепції

1. **Локальна транзакція на сервіс**
   Кожен сервіс комітить тільки свої зміни в БД.
2. **Compensating actions**
   Якщо пізніший крок падає, раніше успішні кроки компенсуються
   (`reserve -> release`, `charge -> refund`).
3. **Idempotency**
   Усі handlers/compensations мають витримувати duplicate delivery.
4. **Eventual consistency**
   Тимчасова неузгодженість допустима, доки saga не зійдеться до фінального стану.

#### Приклад flow (order checkout)

1. Order service створює замовлення `PENDING`.
2. Payment service списує кошти з клієнта.
3. Inventory service резервує залишки.
4. Якщо все успішно -> замовлення стає `CONFIRMED`.
5. Якщо inventory падає після payment -> виконуємо compensation
   (`payment.refund`) і ставимо замовлення в `CANCELLED`.

#### Будівельні блоки реалізації в NestJS

1. Message transport/broker (Kafka, NATS, Redis тощо).
2. Durable обробка job/event із retries і DLQ.
3. Outbox pattern для надійного event publishing після локального commit.
4. Відстеження saga state (DB table/workflow store).
5. Structured logs з `correlationId`/`sagaId`.

#### Tradeoff: choreography vs orchestration

1. **Choreography**
   + Простий старт, менше центральних залежностей
   - Гірша глобальна видимість/керованість із ростом флоу
2. **Orchestration**
   + Чіткий ownership флоу, простіше дебажити й контролювати політики
   - Додаткова компонента й логіка координації

#### Практичні запобіжники

1. Додавайте timeout для кожного кроку saga.
2. Реалізуйте retry з backoff для transient failures.
3. Визначайте compensation для кожного non-idempotent side effect.
4. Тримайте кроки saga невеликими і явними.
5. Моніторте stuck/incomplete sagas.

#### Правило

У мікросервісах не намагайтеся отримати глобальний ACID. Моделюйте бізнес-флоу
як sagas: з idempotent handlers, compensation-механізмами і сильною
observability.

</details>

<details>
<summary>89. Що таке CQRS і як його реалізувати в NestJS за допомогою @nestjs/cqrs?</summary>

#### NestJS

CQRS (Command Query Responsibility Segregation) розділяє операції запису
(commands) та операції читання (queries), часто з різними моделями й
стратегіями оптимізації для кожної сторони.

#### Навіщо використовують CQRS

1. Чітке розділення business mutations і read concerns.
2. Краща масштабованість для read-heavy систем.
3. Простіше моделювати складні domain workflows.
4. Чистіша інтеграція з подіями та eventual consistency.

#### Базові компоненти CQRS

1. **Command**
   Намір змінити стан (`CreateOrderCommand`).
2. **CommandHandler**
   Виконує бізнес-логіку і записує стан.
3. **Query**
   Запит даних без side effects (`GetOrderByIdQuery`).
4. **QueryHandler**
   Повертає read model/data projection.
5. **Events** (опціонально, але часто)
   Факти, що емітяться після успішних змін стану.

#### Реалізація в NestJS через `@nestjs/cqrs`

Крок 1: встановити і підключити `CqrsModule`.

```ts
@Module({
  imports: [CqrsModule],
  providers: [CreateOrderHandler, GetOrderByIdHandler],
})
export class OrdersModule {}
```

Крок 2: визначити command + handler.

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

Крок 3: визначити query + handler.

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

Крок 4: використовувати buses у controller/service.

```ts
constructor(
  private readonly commandBus: CommandBus,
  private readonly queryBus: QueryBus,
) {}

await this.commandBus.execute(new CreateOrderCommand(userId, items));
return this.queryBus.execute(new GetOrderByIdQuery(orderId));
```

#### Коли CQRS виправданий

1. Складні domain rules і workflows.
2. Різні вимоги до масштабування reads та writes.
3. Потреба в event-driven projections/read models.

#### Коли не варто overuse CQRS

1. Невеликі CRUD-застосунки з простою логікою.
2. Команди, які ще не готові до додаткової архітектурної складності.

#### Правило

Використовуйте CQRS там, де це виправдано бізнес-складністю або вимогами
масштабування. В інших випадках тримайте простішу service/repository модель і
розвивайте її поступово.

</details>

<details>
<summary>90. Що таке Domain-Driven Design і як його принципи застосовуються в NestJS?</summary>

#### NestJS

Domain-Driven Design (DDD) — це підхід, у якому програму моделюють навколо
ключових бізнес-доменів і їхньої мови, а не лише навколо технічних шарів.

У NestJS DDD застосовується через узгодження модулів і меж коду з
бізнес-можливостями та доменними правилами.

#### Основні принципи DDD

1. **Ubiquitous language**
   Спільний бізнес-словник у коді, документації та комунікації.
2. **Bounded contexts**
   Чіткі межі, в яких модель має конкретне значення.
3. **Entities / Value Objects / Aggregates**
   Доменні обʼєкти з явними інваріантами та правилами консистентності.
4. **Domain services**
   Stateless бізнес-операції, що не належать одній конкретній сутності.
5. **Repositories**
   Абстракції для завантаження/збереження агрегатів.
6. **Domain events**
   Бізнес-факти, які емітяться при важливих змінах стану.

#### Як це мапиться на NestJS

1. **Feature modules як bounded contexts**
   `OrdersModule`, `BillingModule`, `InventoryModule`.
2. **Application layer services**
   Оркеструють use cases, транзакції, інтеграції.
3. **Domain layer**
   Чиста бізнес-модель (entities/value objects/policies), framework-agnostic.
4. **Infrastructure adapters**
   DB, messaging, зовнішні API, HTTP controllers.

#### Типова структура папок (приклад)

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

#### Практичні переваги DDD у NestJS

1. Краще підходить для складної бізнес-логіки.
2. Зменшує випадкову звʼязаність між доменами.
3. Робить core-логіку більш тестованою незалежно від framework/infrastructure.
4. Полегшує еволюцію архітектури в міру росту системи.

#### Типові помилки

1. Називати будь-який layered code «DDD» без глибокої доменної моделі.
2. Протікання ORM entities напряму в доменну логіку.
3. Непослідовне змішування технічної мови з бізнес-поняттями.
4. Overengineering DDD для тривіальних CRUD-сервісів.

#### Коли DDD найбільш корисний

1. Багаті й мінливі бізнес-правила.
2. Кілька команд/доменів в одній платформі.
3. Потреба у довгостроковій ясності моделі та автономії bounded contexts.

#### Правило

Впроваджуйте DDD поступово: починайте з чітких bounded contexts і ubiquitous
language, а далі поглиблюйте тактичні патерни там, де це виправдано
складністю домену.

</details>

<details>
<summary>91. Що таке Hexagonal Architecture (Ports & Adapters) і як її реалізувати в NestJS?</summary>

#### NestJS

Hexagonal Architecture (Ports & Adapters) організовує застосунок так, щоб
бізнес-логіка була ізольована від зовнішніх технологій (DB, HTTP, message
brokers, SDKs).

Core залежить від абстракцій (ports), а конкретні інтеграції реалізуються як
adapters.

#### Ключові концепції

1. **Domain/Application Core**
   Бізнес-правила і оркестрація use cases.
2. **Ports**
   Інтерфейси/контракти, які core використовує (output ports) або експонує
   (input ports).
3. **Adapters**
   Технічні реалізації портів:
   HTTP controllers, DB repositories, message consumers, external API clients.

#### Правило залежностей

Усі залежності мають бути направлені всередину:
1. Adapters залежать від core contracts.
2. Core не залежить від details framework/infrastructure.

#### Як застосувати в NestJS

1. Визначити port interfaces у domain/application layer.
2. Реалізувати adapters в infrastructure layer.
3. Привʼязати adapter-класи до port tokens у providers модуля.
4. Використовувати DI, щоб інжектити port у use-case сервіси.

#### Приклад структури

Port (core contract):

```ts
export interface PaymentPort {
  charge(input: { orderId: string; amount: number }): Promise<{ paymentId: string }>;
}
```

Application service:

```ts
@Injectable()
export class CheckoutService {
  constructor(@Inject('PAYMENT_PORT') private readonly payments: PaymentPort) {}

  async checkout(orderId: string, amount: number) {
    return this.payments.charge({ orderId, amount });
  }
}
```

Реалізація adapter:

```ts
@Injectable()
export class StripePaymentAdapter implements PaymentPort {
  async charge(input: { orderId: string; amount: number }) {
    // виклик Stripe SDK
    return { paymentId: 'pay_123' };
  }
}
```

Provider binding:

```ts
{
  provide: 'PAYMENT_PORT',
  useClass: StripePaymentAdapter,
}
```

#### Переваги

1. Простіше тестувати (можна мокати ports в unit-тестах).
2. Менша звʼязаність із framework/ORM/зовнішніми вендорами.
3. Безпечніші довгострокові refactor-и і заміни технологій.
4. Чіткіші архітектурні межі для команд.

#### Типові помилки

1. Занадто generic ports (втрачається domain-значення).
2. Протікання ORM/HTTP типів у core interfaces.
3. Надмірна абстракція для дуже маленьких/простих модулів.

#### Правило

Використовуйте hexagonal boundaries навколо важливих business flows та
нестабільних зовнішніх залежностей. Тримайте ports business-oriented, а adapters
— взаємозамінними.

</details>

<details>
<summary>92. Як реалізувати структуроване логування, і навіщо це потрібно?</summary>

#### NestJS

Структуроване логування означає запис логів у machine-readable форматі (зазвичай
JSON) з консистентними полями, а не як довільні текстові рядки.

Це потрібно для пошуку, алертингу, кореляції й надійної observability у
production-системах.

#### Чому structured logging важливий

1. Швидка фільтрація/запити в log-платформах.
2. Краще дебаження інцидентів через correlation IDs.
3. Консистентні дашборди й алерти.
4. Простіший cross-service tracing у distributed systems.

#### Що має бути в кожному логу

1. `timestamp`
2. `level` (`debug`, `info`, `warn`, `error`)
3. `service` / `env`
4. `message`
5. `requestId` / `traceId`
6. Context-поля (`userId`, `route`, `method`, `statusCode`, latency)
7. Error details (`errorName`, `stack`) для збоїв

#### Підхід реалізації в NestJS

1. Використовуйте structured logger (Pino/Winston) як app logger.
2. Додавайте request context (`requestId`, user info) через middleware/interceptor.
3. Логуйте business events і failures у консистентній схемі.
4. Уникайте ad-hoc `console.log` у production-коді.

#### Практичний стиль прикладу

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

#### Рекомендації для error-логування

1. Зберігайте повний stack trace у логах.
2. Не повертайте stack traces у API-відповідях.
3. Додавайте domain error codes для надійного маршрутування алертів.
4. Зберігайте root cause chain при wrapping exceptions.

#### Типові помилки

1. Логування plain strings без context-полів.
2. Неконсистентні назви полів між модулями/сервісами.
3. Логування secrets/tokens/PII без редагування.
4. Надмірний debug-шум у hot paths продакшену.

#### Best practices

1. Визначте й задокументуйте log schema.
2. Централізовано редагуйте чутливі поля.
3. Свідомо використовуйте log levels.
4. Корелюйте логи з метриками й трасами.
5. Перевіряйте logging output в integration-тестах для критичних флоу.

#### Правило

Якщо логи лише для людей, incident response буде повільним. Якщо логи
структуровані для машин і людей, операційна робота стає передбачуваною й
масштабованою.

</details>

<details>
<summary>93. Як у NestJS реалізувати моніторинг стану застосунку? (@nestjs/terminus)</summary>

#### NestJS

Моніторинг health стану застосунку в NestJS зазвичай реалізують через
`@nestjs/terminus`, який надає стандартизовані health-check endpoint для app і
залежностей (readiness/liveness).

#### Навіщо потрібен health monitoring

1. Оркестраторам/load balancer потрібні health-сигнали.
2. Швидше виявлення інцидентів і автоматичне відновлення.
3. Безпечні deployment rollout і readiness gating.

#### Типові health endpoint

1. **Liveness** (`/health/live`)
   Перевірка «процес працює».
2. **Readiness** (`/health/ready`)
   Перевірка «інстанс може обслуговувати трафік зараз», включно з критичними залежностями.

#### Базові кроки налаштування

1. Встановіть `@nestjs/terminus`.
2. Імпортуйте `TerminusModule`.
3. Створіть `HealthController` з використанням `HealthCheckService`.

#### Приклад контролера

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

#### Що додавати в readiness

1. DB connectivity.
2. Redis/cache connectivity.
3. Критичні зовнішні залежності (лише якщо справді потрібні для обслуговування трафіку).
4. Внутрішні resource thresholds (memory, event-loop pressure за потреби).

#### Операційні best practices

1. Тримайте liveness легким і локальним.
2. Тримайте readiness залежним від критичних сервісів, але швидким.
3. Не включайте некритичні опційні сервіси в fail-критерії readiness.
4. Обмежуйте/захищайте health-деталі в публічних середовищах.
5. Інтегруйте з Kubernetes probes та alerting.

#### Правило

Liveness каже: «перезапусти мене, якщо я мертвий». Readiness каже:
«маршрутизуй трафік на мене лише тоді, коли я реально можу безпечно обробляти
запити».

</details>

<details>
<summary>94. Як реалізувати health checks для залежних сервісів (DB, Redis, зовнішні API)?</summary>

#### NestJS

Health checks для залежностей перевіряють, чи критичні зовнішні системи
достатньо доступні, щоб застосунок міг безпечно обслуговувати трафік.

У NestJS це зазвичай реалізується через indicators з `@nestjs/terminus`.

#### Категорії залежностей для перевірки

1. **Database** (readiness-критична для більшості API).
2. **Redis/cache** (критична або опційна залежно від архітектури).
3. **External APIs** (лише ті, що потрібні для core request paths).

#### Підхід до реалізації

1. Тримайте `/health/live` легким (перевірка рівня процесу).
2. Dependency checks розміщуйте в `/health/ready`.
3. Некритичні залежності позначайте окремо, щоб уникати зайвих hard-fail.

#### Приклад readiness controller

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

Для Redis використовуйте custom health indicator або підтримуваний adapter
indicator, залежно від вашого стеку.

#### Важливі дизайн-рішення

1. **Critical vs optional dependency**
   Лише критичні залежності мають валити readiness.
2. **Timeouts**
   Health checks повинні мати короткі жорсткі timeout, щоб уникати накопичення probes.
3. **Check cost**
   Використовуйте легкі "ping" checks, а не дорогі запити.
4. **Failure semantics**
   Повертайте зрозумілий статус по кожній залежності для діагностики.

#### Операційні best practices

1. Використовуйте окремі endpoint для liveness/readiness/startup probes.
2. Уникайте перевірки занадто великої кількості нестабільних external services у readiness.
3. Додавайте caching/debouncing для дорогих checks, якщо потрібно.
4. Алертіть на transitions статусів залежностей, а не лише на повний app down.
5. Виносьте latency залежностей в observability dashboards.

#### Правило

Health checks повинні відповідати на питання: "Чи може цей інстанс коректно
обслуговувати запити прямо зараз?" Проєктуйте dependency checks саме навколо
цього питання, а не навколо спроби перевірити все підряд.

</details>

<details>
<summary>95. Як використовувати OpenTelemetry у NestJS?</summary>

#### NestJS

OpenTelemetry (OTel) у NestJS використовується для збору traces, metrics і logs
для observability. Найчастіший старт — distributed tracing для вхідних запитів
і downstream-викликів.

#### Що дає OpenTelemetry

1. End-to-end трасування запитів між сервісами.
2. Розбиття latency по spans (DB, HTTP, cache, queue).
3. Кореляцію між помилками та конкретними залежностями.
4. Vendor-neutral формат телеметрії (експорт у Jaeger/Tempo/Datadog/New Relic тощо).

#### Типовий flow налаштування OTel у NestJS

1. Ініціалізувати OTel SDK до bootstrap застосунку.
2. Налаштувати resource attributes (`service.name`, `service.version`, env).
3. Увімкнути auto-instrumentations (HTTP, Express, DB clients тощо).
4. Експортувати traces через OTLP/collector.
5. Додати custom spans там, де важливий бізнес-контекст.

#### Мінімальний концептуальний bootstrap (Node SDK)

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

Після цього запускайте Nest app як звичайно.

#### Приклад custom span (business boundary)

1. Створіть span навколо критичної доменної операції.
2. Додайте attributes (`order.id`, `tenant.id`).
3. Записуйте exceptions і статус у разі збою.

#### Практичні best practices

1. Розумно налаштовуйте sampling (повний у staging, tuned у production).
2. Пропагуйте context headers (`traceparent`) через HTTP/message boundaries.
3. Уникайте high-cardinality attributes (email користувача, випадкові ID в labels).
4. Інструментуйте критичні залежності та queue consumers.
5. Корелюйте traces з logs через trace/span IDs.

#### Типові помилки

1. Ініціалізація OTel після старту app (втрачаються ранні spans).
2. Over-instrumentation, що дає зайвий overhead/noise.
3. Відсутня context propagation між сервісами/воркерами.
4. Відправка телеметрії напряму з app без collector у великих деплойментах.

#### Правило

Починайте з tracing + auto-instrumentation, а далі додавайте цільові custom
spans навколо high-value бізнес-операцій і latency hotspots.

</details>

<details>
<summary>96. Що таке distributed tracing і як його реалізують у мікросервісній архітектурі?</summary>

#### NestJS

Distributed tracing відстежує один request/transaction через кілька сервісів та
інфраструктурних компонентів, показуючи end-to-end flow і розкладку latency.

Це критично для мікросервісів, де одна дія користувача може запускати багато
service calls, queue hops і DB operations.

#### Базові поняття tracing

1. **Trace**
   Повний end-to-end шлях запиту.
2. **Span**
   Одна операція всередині trace (HTTP call, DB query, виконання handler).
3. **Context propagation**
   Передача trace context між сервісами (наприклад, заголовок `traceparent`).
4. **Parent-child relationships**
   Spans формують дерево, яке відображає ієрархію викликів.

#### Навіщо потрібен distributed tracing

1. Знаходити реальні bottleneck (яка залежність повільна).
2. Швидко дебажити cross-service failures.
3. Розуміти fan-out/fan-in поведінку і retry storms.
4. Покращувати p95/p99 на основі фактів, а не здогадок.

#### Як це реалізується в мікросервісах

1. Інструментувати кожен сервіс через OpenTelemetry SDK.
2. Увімкнути auto-instrumentation для framework/library (HTTP server/client, DB, message clients).
3. Пропагувати context через межі:
   1. HTTP headers (`traceparent`, `tracestate`)
   2. Message metadata для Kafka/NATS/queues
4. Експортувати spans у collector/backend (OTLP -> Jaeger/Tempo/Datadog тощо).
5. Корелювати логи з traceId/spanId.

#### NestJS-специфічні точки реалізації

1. Ініціалізувати OTel до bootstrap Nest.
2. Інструментувати вхідні запити (Express/Fastify).
3. Інструментувати вихідні `HttpService` виклики і DB drivers.
4. Додавати custom spans навколо важливих бізнес-операцій.
5. Пропагувати context у workers/background jobs.

#### Типовий trace на практиці

1. API Gateway отримує запит (root span).
2. Service A валідовує auth (child span).
3. Service A викликає Service B через gRPC/HTTP (child span).
4. Service B робить запит у DB (nested span).
5. Service B публікує подію в broker (child span).
6. Worker споживає подію і виконує side effect (linked/continued context).

#### Best practices

1. Використовуйте консистентні назви сервісів і resource attributes.
2. Уникайте high-cardinality span attributes.
3. Налаштовуйте sampling policy (tail-based/head-based за профілем трафіку).
4. Фіксуйте помилки й статус-коди на spans.
5. Узгоджуйте trace retention з потребами incident/debug.

#### Правило

У мікросервісах metrics показують, що щось повільне; distributed tracing показує
точно де і чому.

</details>

<details>
<summary>97. Як писати unit-тести в NestJS, і які є базові підходи до тестування?</summary>

#### NestJS

Unit testing у NestJS фокусується на перевірці поведінки одного класу/модуля в
ізоляції, зазвичай із моками залежностей і без реальних network/database calls.

#### Основні рівні тестування в NestJS

1. **Unit tests**
   Тестують services/guards/pipes/interceptors ізольовано.
2. **Integration tests**
   Тестують взаємодію між компонентами/модулями (часто з test DB).
3. **E2E tests**
   Тестують повну HTTP-поведінку app через реальний bootstrap Nest застосунку.

#### Типовий стек для unit-тестів

1. Jest як test runner/assertion/mocking tool.
2. `@nestjs/testing` для створення testing modules.
3. Mock providers для залежностей (`useValue`, `useFactory`).

#### Приклад unit-тесту для service

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

#### Базові підходи до тестування

1. **Arrange-Act-Assert**
   Тримайте тести читабельними та детермінованими.
2. **Mock external boundaries**
   DB, HTTP-клієнти, queues та системи, залежні від часу.
3. **Тестуйте поведінку, а не implementation details**
   Перевіряйте результати та side effects, а не приватні внутрішні деталі.
4. **Покривайте happy path + failure path**
   Validation errors, exceptions, edge cases.

#### Що unit-тестувати в NestJS у першу чергу

1. Application/domain services.
2. Custom guards/pipes/interceptors.
3. Utility/domain logic класи.
4. Mapper/validation логіку з розгалуженою поведінкою.

#### Типові помилки

1. Виклики реальної БД у "unit" тестах.
2. Надмірний mocking, коли тести втрачають цінність.
3. Занадто жорсткі assert на крихкі внутрішні виклики.
4. Ігнорування негативних/error сценаріїв.

#### Правило

Unit-тести мають бути швидкими, ізольованими і детермінованими. Використовуйте
їх для фіксації поведінки бізнес-логіки; integration/e2e тести залишайте для
перевірки wiring і реальної runtime-поведінки.

</details>

<details>
<summary>98. Як правильно мокати залежності в NestJS, і коли це потрібно робити?</summary>

#### NestJS

Мокання залежностей у NestJS означає заміну реальних колабораторів (DB repos,
HTTP clients, queues, external SDKs) контрольованими test doubles, щоб
ізолювати поведінку unit-рівня.

#### Коли потрібно мокати

1. У unit-тестах для services/guards/pipes/interceptors.
2. Для тестування failure-path, який важко відтворити на реальних системах.
3. Для швидкого feedback loop, де зовнішній I/O уповільнює тести.

#### Коли не потрібно мокати

1. В integration-тестах, що перевіряють module wiring і реальні adapters.
2. В E2E-тестах, що перевіряють повну runtime-поведінку.
3. Коли високий ризик contract drift і важлива взаємодія з реальною залежністю.

#### Типовий патерн мокання в NestJS

Використовуйте `TestingModule` і перевизначайте provider tokens через
`useValue`/`useFactory`.

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

#### Поради з мокання за типом залежності

1. **Repository/DAO**
   Мокайте конкретні методи, що використовуються в тесті (`findOne`, `save` тощо).
2. **HttpService / external client**
   Мокайте return values/errors і timeout-сценарії.
3. **Queue/event publishers**
   Мокайте enqueue/publish виклики і перевіряйте payload/contracts.
4. **ConfigService**
   Мокайте явні ключі, що використовуються у code path.

#### Хороші практики мокання

1. Мокайте тільки boundary dependencies, а не сам class under test.
2. Тримайте моки мінімальними й сфокусованими на поведінці.
3. Скидайте моки між тестами.
4. Спочатку перевіряйте outcomes, потім interactions.
5. Явно включайте negative paths (throws/rejects).

#### Типові помилки

1. Over-mocking внутрішніх методів того самого класу (тестуються implementation details).
2. Повторне використання stateful mocks між тест-кейсами без reset.
3. Mock values, що порушують форму реального контракту (false confidence).
4. Написання лише happy-path тестів.

#### Правило

Мокайте, щоб ізолювати бізнес-логіку й пришвидшити unit-тести.
Integration/e2e тести використовуйте для перевірки реального wiring і зовнішніх
контрактів.

</details>

<details>
<summary>99. Як писати інтеграційні тести в NestJS з використанням TestingModule?</summary>

#### NestJS

Integration tests у NestJS перевіряють, що кілька реальних компонентів
працюють разом (module wiring, DI, repositories/services, pipes/guards), але
залишаються легшими за повні E2E-тести.

`TestingModule` — основний інструмент для складання тестового контексту
застосунку.

#### Мета integration-тестів

1. Валідовувати взаємодію між реальними providers.
2. Ловити проблеми DI/config/module wiring.
3. Тестувати persistence/service flows з реалістичними залежностями.

#### Типовий setup flow

1. Створити `TestingModule` з реальним(и) модулем(ями) під тестом.
2. Опційно перевизначити лише зовнішні boundaries (наприклад, third-party API).
3. Ініціалізувати app/module context.
4. Підготувати test data.
5. Виконати сценарій і перевірити side effects/results.

#### Приклад з `TestingModule` + repository/service

```ts
import { Test, TestingModule } from '@nestjs/testing';

describe('UsersModule Integration', () => {
  let moduleRef: TestingModule;
  let service: UsersService;

  beforeAll(async () => {
    moduleRef = await Test.createTestingModule({
      imports: [UsersModule, TestDatabaseModule], // реальне module wiring
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

#### Які залежності використовувати

1. Віддавайте перевагу реальній БД в ізольованому test environment
   (test container/in-memory DB, де це прийнятно).
2. Мокайте лише нестабільні/дорогі зовнішні системи
   (payment gateways, SaaS APIs).
3. Тримайте конфігурацію близькою до production semantics.

#### Стратегії керування даними

1. Transaction rollback на тест (де можливо).
2. Truncate/reset таблиць між тестами.
3. Deterministic test fixtures/builders.

#### Типові помилки

1. Перетворення integration-тестів на unit-тести через мокання всього.
2. Спільний mutable global state між тестами.
3. Випадкова залежність від production/staging DB.
4. Відсутність cleanup, що дає flaky order-dependent тести.

#### Практичне правило

Integration-тести мають валідовувати реальну співпрацю модулів із мінімальним
mocking. Це головна страховка від поламаного wiring і регресій у persistence.

</details>

<details>
<summary>100. Що таке end-to-end (E2E) тестування в NestJS, і чим воно відрізняється від unit та integration тестів?</summary>

#### NestJS

E2E (end-to-end) тестування в NestJS перевіряє повну поведінку застосунку через
реальні публічні інтерфейси (зазвичай HTTP), максимально наближено до того, як
системою користуються реальні клієнти.

Це рівень тестування з найвищою довірою для API contracts, middleware/guards,
validation, error mapping і infrastructure wiring.

#### Чим E2E відрізняється від інших рівнів тестування

1. **Unit tests**
   Тестують один клас ізольовано з моками залежностей.
2. **Integration tests**
   Тестують співпрацю кількох реальних компонентів/модулів.
3. **E2E tests**
   Тестують повний ланцюжок request -> framework pipeline -> business logic ->
   persistence -> response.

#### Типовий E2E setup у NestJS

1. Створити testing module з повним `AppModule` (або майже повним).
2. Підняти інстанс Nest application.
3. Надсилати реальні HTTP requests (часто через `supertest`).
4. Перевіряти статус-коди, response body і side effects.

#### Мінімальний E2E приклад

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

#### Що E2E ловить найкраще

1. Зламаний route/guard/pipe/interceptor setup.
2. Проблеми валідації та серіалізації.
3. Regression в auth flow.
4. Drift реального API contract.
5. Проблеми глобального error handling і response shape.

#### Типові помилки

1. Покладатися лише на E2E (надто повільно для повного покриття логіки).
2. Запускати тести на спільних неізольованих середовищах.
3. Нестабільний setup/cleanup тест-даних, що дає flaky тести.
4. Надто широка E2E-сюїта, яка стає повільною і важкою в підтримці.

#### Практична testing pyramid

1. Багато unit-тестів (швидка впевненість у логіці).
2. Деяка кількість integration-тестів (впевненість у wiring).
3. Менше, але цінних E2E-тестів (впевненість у контрактах).

#### Правило

Використовуйте E2E-тести для захисту критичних user/business journey та
зовнішніх API contracts; нижчі рівні тестів використовуйте для глибини й
швидкості.

</details>

<details>
<summary>101. Що таке Nest CLI і які команди використовуються найчастіше?</summary>

#### NestJS

Nest CLI — це офіційний command-line інструмент для створення, генерації,
запуску та підтримки NestJS-застосунків.

Він стандартизує scaffolding проєкту і пришвидшує щоденну розробку.

#### Для чого використовується Nest CLI

1. Створювати нові проєкти з рекомендованою структурою.
2. Швидко генерувати modules/controllers/services/resources.
3. Запускати app у dev/watch mode.
4. Збирати production bundles.
5. Запускати тести через налаштовані scripts/tooling.

#### Найуживаніші команди

1. **Створити застосунок**
   `nest new my-app`
2. **Запуск у development**
   `npm run start:dev`
   (або `nest start --watch`, залежно від setup)
3. **Зібрати застосунок**
   `npm run build`
   (або `nest build`)
4. **Згенерувати модуль**
   `nest g module users`
5. **Згенерувати контролер**
   `nest g controller users`
6. **Згенерувати сервіс**
   `nest g service users`
7. **Згенерувати повний CRUD resource**
   `nest g resource users`
8. **Запустити тести**
   `npm test`, `npm run test:watch`, `npm run test:e2e`

#### Корисні aliases

1. `nest generate` -> `nest g`
2. `nest controller` -> `nest g co`
3. `nest service` -> `nest g s`
4. `nest module` -> `nest g mo`

#### Приклад практичного workflow

1. `nest g resource orders`
2. Реалізувати domain/use-case логіку.
3. `npm run start:dev` для локальної ітерації.
4. `npm run test` і `npm run test:e2e`.
5. `npm run build` перед релізом.

#### Best practices

1. Використовуйте CLI generators, щоб структура була консистентною в команді.
2. Переглядайте згенерований код і прибирайте зайвий boilerplate.
3. Віддавайте перевагу явним архітектурним межам, а не сліпо згенерованому layering.
4. Тримайте scripts у `package.json` узгодженими з CI workflow команди.

#### Правило

Nest CLI — це інструмент продуктивності, а не архітектура. Використовуйте його
для швидкого scaffolding, а далі формуйте кодову базу під домен і стандарти
якості.

</details>

<details>
<summary>102. Як правильно організувати Dockerfile для NestJS застосунку (multi-stage build)?</summary>

#### NestJS

Правильний multi-stage Dockerfile для NestJS відділяє build-time залежності від
runtime image, що дає менші, безпечніші й швидші production-контейнери.

#### Чому multi-stage build важливий

1. Менший фінальний розмір image.
2. Менша attack surface (без dev/build tooling у runtime).
3. Швидші deploy/pull.
4. Чистіші межі залежностей.

#### Рекомендована multi-stage структура

1. **deps stage**
   Встановлення залежностей через lockfile.
2. **build stage**
   Компіляція TypeScript -> `dist`.
3. **runtime stage**
   Копіювання лише скомпільованого output + production dependencies.

#### Приклад Dockerfile

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

#### Рекомендований `.dockerignore`

1. `node_modules`
2. `dist`
3. `.git`
4. `coverage`
5. локальні env-файли, які не потрібні в build context

#### Security і runtime best practices

1. За можливості запускайте під non-root user.
2. Фіксуйте major-версію Node і оновлюйте base images.
3. Інжектіть конфіг через environment/secret manager, а не запікайте у файли.
4. Додавайте health checks і graceful shutdown support.
5. Скануйте image на вразливості в CI.

#### Поради для build performance

1. Копіюйте lockfile рано, щоб використовувати layer caching.
2. Уникайте інвалідації dependency layer через часті source-only зміни.
3. Використовуйте детерміновані інсталяції (`npm ci`).

#### Типові помилки

1. Single-stage image з повними dev dependencies.
2. Постачання source і build tools у runtime image.
3. Копіювання всього контексту до встановлення залежностей (ламає ефективність кешу).
4. Зберігання secrets у Dockerfile або закоміченому `.env`.

#### Правило

Виконуйте «важкий» build на ранніх stage, а фінальний stage тримайте lean.
Production-контейнер має містити лише те, що потрібно для запуску `dist/main.js`.

</details>
