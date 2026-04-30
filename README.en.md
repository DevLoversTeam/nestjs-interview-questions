**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  NestJS <img src="./assets/nestjs.svg" width="40" height="40" alt="NestJS logo"/>
</h1>

<h2>Most Popular NestJS Interview Questions and Answers</h2>

<details>
<summary>1. What is NestJS and what problems does it solve?</summary>

#### NestJS

NestJS is a progressive Node.js framework for building server-side applications.
It is built with TypeScript by default and uses familiar architectural ideas from
Angular (modules, dependency injection, decorators), while running on top of
HTTP adapters such as Express or Fastify.

#### What NestJS solves

1. **Lack of structure in growing Node.js apps**
   NestJS enforces clear modular boundaries (`@Module`), making large codebases
   easier to scale and maintain.

2. **Hard-to-manage dependencies**
   Built-in **Dependency Injection (DI)** reduces tight coupling between classes
   and improves testability.

3. **Boilerplate across cross-cutting concerns**
   Guards, Pipes, Interceptors, Filters, and Middleware provide consistent
   patterns for auth, validation, transformation, logging, and error handling.

4. **Inconsistent architecture across teams**
   NestJS provides opinionated conventions, so teams can build services with the
   same mental model and predictable project layout.

5. **Complex testing setup**
   Testing utilities (`@nestjs/testing`) and DI-friendly design simplify unit,
   integration, and e2e testing.

6. **Need for multi-transport backend support**
   NestJS supports HTTP REST, GraphQL, WebSockets, and microservices (TCP, Redis,
   NATS, Kafka, gRPC, etc.) with a unified programming model.

#### In short

NestJS helps you move from “just working Node.js code” to a **well-structured,
enterprise-ready backend architecture** with strong maintainability, testability,
and team scalability.

</details>

<details>
<summary>2. How does NestJS differ from Express and Fastify?</summary>

#### NestJS

NestJS, Express, and Fastify are related but serve different abstraction levels.

#### Core difference

1. **Express / Fastify** are HTTP server frameworks.
2. **NestJS** is an application framework that can run on top of Express or
   Fastify via adapters.

#### Architecture and development model

1. **Express**
   Minimal and unopinionated. You manually define structure, DI patterns,
   validation, and conventions.

2. **Fastify**
   Also relatively low-level, but optimized for performance with a plugin
   ecosystem and schema-first approach.

3. **NestJS**
   Opinionated architecture out of the box: modules, providers, controllers,
   dependency injection, lifecycle hooks, and standardized request pipeline.

#### Performance perspective

1. **Fastify** is generally faster than Express at raw HTTP throughput.
2. **NestJS on Fastify adapter** usually gives better performance than NestJS on
   Express.
3. In most business systems, architecture, maintainability, and team velocity are
   often more important than micro-benchmark differences.

#### Feature comparison in practice

1. **Dependency Injection**
   Native in NestJS; manual or third-party in Express/Fastify.

2. **Testing ergonomics**
   NestJS has built-in testing module patterns; lower-level frameworks require
   more custom setup.

3. **Scalability of codebase**
   NestJS conventions reduce chaos in large teams/projects.

4. **Ecosystem scope**
   NestJS unifies REST, GraphQL, WebSockets, and microservices under one mental
   model.

#### When to choose what

1. Choose **Express** for very small/simple services or legacy compatibility.
2. Choose **Fastify** when maximal throughput and low overhead are primary goals.
3. Choose **NestJS** when you need long-term maintainability, clear architecture,
   and a standardized enterprise backend approach.

</details>

<details>
<summary>3. What are the main building blocks of NestJS?</summary>

#### NestJS

NestJS is composed of several core building blocks that define application
architecture, runtime behavior, and request flow.

#### Core building blocks

1. **Modules (`@Module`)**
   The top-level organizational unit. A module groups related controllers and
   providers, and controls visibility through `imports` / `exports`.

2. **Controllers (`@Controller`)**
   Handle incoming requests and return responses. Route decorators like `@Get()`,
   `@Post()`, `@Patch()` map handlers to endpoints.

3. **Providers (`@Injectable`)**
   Classes managed by Nest's DI container (services, repositories, factories,
   helpers). They encapsulate business logic and can be injected into other
   classes.

4. **Dependency Injection (DI) container**
   Resolves provider dependencies using tokens, scopes, and module boundaries.
   This is the foundation of decoupled design in NestJS.

#### Request lifecycle components

1. **Middleware**
   Runs before route handlers. Good for low-level request preprocessing (e.g.
   logging, headers, request context bootstrap).

2. **Guards (`CanActivate`)**
   Decide whether a request is allowed to proceed (auth/authz gate).

3. **Pipes (`PipeTransform`)**
   Transform and validate incoming data (DTO validation, parsing, normalization).

4. **Interceptors (`NestInterceptor`)**
   Wrap handler execution for cross-cutting concerns (response mapping, timing,
   caching, tracing, retry logic).

5. **Exception Filters (`ExceptionFilter`)**
   Centralized error handling and response shaping for thrown exceptions.

#### Platform and transport blocks

1. **HTTP adapters**
   Express or Fastify integration via platform adapters.

2. **Microservice transport layer**
   TCP, Redis, NATS, Kafka, gRPC, RMQ and others through Nest microservices API.

3. **WebSockets / GraphQL modules**
   Alternative interaction models using the same DI/module principles.

#### Practical mental model

Use **Modules** to structure domains, **Controllers** as API entry points, and
**Providers** for business logic. Then compose behavior with Middleware, Guards,
Pipes, Interceptors, and Filters to build robust production services.

</details>

<details>
<summary>4. What is the role of TypeScript in NestJS and why is strict mode important?</summary>

#### NestJS

TypeScript is a core design pillar of NestJS, not just an optional add-on. Nest
uses classes, decorators, interfaces, and metadata-driven DI patterns that are
most effective with strong typing.

#### Role of TypeScript in NestJS

1. **Type-safe architecture**
   Controllers, services, DTOs, and repositories are implemented as typed classes
   and contracts, reducing runtime surprises.

2. **Better Dependency Injection experience**
   Constructor types make provider dependencies explicit and easier to reason
   about during refactoring.

3. **DTO-driven API boundaries**
   Request/response shapes become explicit through DTO classes and mapped types,
   improving maintainability and API consistency.

4. **Tooling and productivity**
   Strong IntelliSense, safe auto-refactors, and compile-time feedback speed up
   team development.

5. **Scalable codebase governance**
   Type contracts serve as executable documentation in large systems.

#### Why strict mode is important

1. **Catches bugs early**
   `strictNullChecks`, `noImplicitAny`, and related checks prevent common errors
   before production.

2. **Safer refactoring**
   In large NestJS projects, strict mode reduces hidden breakages when moving
   logic across modules/services.

3. **More reliable domain logic**
   Explicit optionality and precise unions force engineers to handle edge cases
   deliberately.

4. **Improved team consistency**
   Strict compiler rules create shared quality standards across contributors.

#### High-impact strict settings for NestJS

1. `strict: true`
2. `noImplicitAny: true`
3. `strictNullChecks: true`
4. `noUncheckedIndexedAccess: true` (recommended for safer object/array access)
5. `noFallthroughCasesInSwitch: true`

#### Practical recommendation

Use TypeScript as a design tool, not only as syntax sugar. In NestJS, strict mode
pays off quickly by improving correctness, readability, and long-term
maintainability of backend services.

</details>

<details>
<summary>5. What are decorators in NestJS? Provide examples.</summary>

#### NestJS

Decorators in NestJS are TypeScript annotations that attach metadata to classes,
methods, parameters, and properties. Nest reads this metadata at runtime to wire
up routing, dependency injection, validation, authorization, and other framework
features.

#### Why decorators matter in NestJS

1. **Declarative configuration**
   You describe behavior close to the code instead of maintaining large external
   config files.

2. **Metadata-driven runtime**
   Nest uses decorator metadata to build modules, resolve providers, and create
   the request pipeline.

3. **Consistent architecture**
   Teams follow predictable patterns across controllers, services, and guards.

#### Common decorator categories

1. **Class decorators**
   `@Module()`, `@Controller()`, `@Injectable()`

2. **Method decorators**
   `@Get()`, `@Post()`, `@UseGuards()`, `@UseInterceptors()`

3. **Parameter decorators**
   `@Param()`, `@Body()`, `@Query()`, `@Headers()`, `@Req()`

4. **Property/constructor injection decorators**
   `@Inject(TOKEN)` (when using custom provider tokens)

#### Examples

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

#### Practical takeaway

Decorators are one of the core reasons NestJS feels structured: they make
framework behavior explicit, composable, and easy to scale across large services.

</details>

<details>
<summary>6. What is Reflect.metadata and how does NestJS use it under the hood?</summary>

#### NestJS

`Reflect.metadata` is part of the metadata reflection mechanism used with
TypeScript decorators (via the `reflect-metadata` polyfill). It allows attaching
structured metadata to classes, methods, and parameters so frameworks can inspect
that information at runtime.

In practice, NestJS is heavily metadata-driven: decorators write metadata, and
Nest reads it to build dependency graphs, routing maps, guards/pipes/interceptor
chains, and parameter resolution logic.

#### Concept in one line

1. Decorator writes metadata.
2. Nest reads metadata through `Reflector` / `Reflect` APIs.
3. Runtime behavior is assembled automatically.

#### Where NestJS uses metadata

1. **Dependency Injection**
   Constructor parameter types and explicit injection tokens are read to resolve
   providers from the IoC container.

2. **Routing**
   `@Controller()` and `@Get()/@Post()` store path and method metadata used to
   register route handlers.

3. **Guards, Pipes, Interceptors, Filters**
   Method/class-level metadata controls which cross-cutting components apply.

4. **Custom authorization annotations**
   Decorators like `@Roles('admin')` store custom metadata later read by Guards.

#### Minimal example (custom metadata + read)

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

#### Nest-specific note

In real NestJS apps, you usually use:
1. `SetMetadata()` to write metadata.
2. `Reflector` service inside Guards/Interceptors to read metadata safely.

This abstraction keeps your code framework-aligned and easier to test than direct
manual `Reflect.getMetadata(...)` calls everywhere.

</details>

<details>
<summary>7. How do you create a custom decorator in NestJS? (createParamDecorator, SetMetadata)</summary>

#### NestJS

In NestJS, custom decorators are usually created in two common ways:
1. **`SetMetadata()`** for attaching custom metadata to routes/classes.
2. **`createParamDecorator()`** for extracting custom values from request context.

These two patterns cover most real-world cases: authorization markers and
request-derived parameters.

#### 1) Custom metadata decorator with `SetMetadata`

Use this when you want to annotate handlers/classes with data that Guards or
Interceptors can read later.

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Usage:

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

Guard reads metadata via `Reflector`:

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

#### 2) Custom parameter decorator with `createParamDecorator`

Use this when you want clean controller signatures and reusable request parsing.

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

Usage:

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

#### Best practices

1. Keep decorators thin; put business logic in Guards/Services.
2. Use constants for metadata keys (avoid magic strings).
3. Prefer `Reflector.getAllAndOverride()` for class + method metadata merging.
4. Type the param decorator output to keep controller contracts explicit.

</details>

<details>
<summary>8. What does @Injectable() do and why is it needed?</summary>

#### NestJS

`@Injectable()` marks a class as a provider that can participate in NestJS
Dependency Injection (DI). In other words, it tells Nest that this class is
managed by the IoC container and may have dependencies injected into its
constructor.

#### What `@Injectable()` does

1. **Registers DI metadata**
   It enables Nest to treat the class as an injectable provider.

2. **Allows constructor injection**
   Nest can resolve and inject dependencies declared in the constructor.

3. **Integrates with provider scope/lifecycle**
   The class can be `DEFAULT`, `REQUEST`, or `TRANSIENT` scoped when configured.

4. **Improves testability**
   Injectable services are easy to replace/mocks in testing modules.

#### Why it is needed

1. **Decoupling**
   Controllers depend on abstractions/services instead of creating dependencies
   manually.

2. **Single responsibility**
   Business logic lives in services, not in controllers.

3. **Centralized object creation**
   Nest container controls instantiation, sharing, and lifecycle behavior.

4. **Scalable architecture**
   DI patterns remain maintainable as app size and team size grow.

#### Example

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

#### Practical nuance

`@Injectable()` alone is not enough; the provider must also be registered in a
module (`providers` array) or exported/imported through module boundaries so Nest
can resolve it where needed.

</details>

<details>
<summary>9. What is the difference between @Controller and @Get()/@Post() decorators?</summary>

#### NestJS

`@Controller` and route method decorators (`@Get`, `@Post`, etc.) work together
but solve different routing levels.

#### Main difference

1. **`@Controller()`**
   Declares a class as a controller and defines a **base route prefix** for all
   handlers inside that class.

2. **`@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`**
   Map a specific class method to an HTTP method + route path.

#### Mental model

1. `@Controller('users')` says: "All endpoints in this class start with `/users`."
2. `@Get(':id')` says: "This method handles `GET /users/:id`."

#### Example

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

Resolved routes:
1. `GET /users`
2. `GET /users/:id`
3. `POST /users`

#### Why this separation is useful

1. **Clear API structure**
   Class groups related endpoints by domain/resource.

2. **Reusable controller-level config**
   Guards, interceptors, versioning, and prefixes can be applied at class level.

3. **Readable routing layer**
   Method decorators make endpoint intent explicit and easy to scan.

</details>

<details>
<summary>10. How does NestJS handle HTTP requests and determine which controller to call?</summary>

#### NestJS

NestJS determines the target controller and handler through metadata collected
from decorators during application bootstrap, then executes the request through a
defined pipeline.

#### How routing is built at startup

1. **Module scan**
   Nest scans imported modules and discovers registered controllers/providers.

2. **Route metadata collection**
   `@Controller()` provides base path; `@Get/@Post/...` provide HTTP method and
   sub-path.

3. **Route registration in adapter**
   Nest combines metadata into concrete routes and registers them in Express or
   Fastify router.

#### What happens per incoming request

1. Request enters underlying HTTP adapter (Express/Fastify).
2. Router matches method + URL path to a controller method.
3. Nest creates an `ExecutionContext` for that handler.
4. Request pipeline runs in order:
   1. Middleware (if configured)
   2. Guards (authorization decision)
   3. Interceptors (before handler)
   4. Pipes (parameter parsing/validation)
   5. Controller method execution
   6. Interceptors (after handler, response mapping)
   7. Exception filters (if errors are thrown)
5. Final response is returned by the adapter.

#### How Nest chooses the exact controller method

1. Match by HTTP method (`GET`, `POST`, etc.).
2. Match by normalized full route path:
   `globalPrefix + controllerPath + handlerPath`.
3. If versioning is enabled, version constraints are evaluated.
4. If route params exist (`:id`), param pattern matching is applied.

#### Example mapping

```ts
@Controller('users')
export class UsersController {
  @Get(':id')
  findOne() {}
}
```

If global prefix is `api`, request `GET /api/users/42` maps to
`UsersController.findOne`.

#### Practical takeaway

NestJS does not "search controllers dynamically" on each request. It precomputes
the routing map at bootstrap and then executes a predictable request lifecycle
around the matched handler.

</details>

<details>
<summary>11. How does NestJS use decorators to build the routing layer?</summary>

#### NestJS

NestJS routing is metadata-driven. Decorators annotate classes and methods, and
Nest reads that metadata during bootstrap to create a concrete route map in the
underlying HTTP adapter.

#### Routing metadata sources

1. **`@Controller(path)`**
   Declares controller-level prefix (resource namespace).

2. **Method decorators**
   `@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`, `@Options()`,
   `@Head()`, `@All()` define HTTP method + handler path.

3. **Parameter decorators**
   `@Param()`, `@Query()`, `@Body()`, `@Headers()`, `@Req()`, `@Res()` define
   how request data is injected into handler arguments.

4. **Cross-cutting decorators**
   `@UseGuards()`, `@UsePipes()`, `@UseInterceptors()`, `@UseFilters()` attach
   execution behavior to route/class.

#### How Nest builds routes

1. Scans modules and discovers controllers.
2. Reads controller + method metadata via reflection.
3. Composes full path:
   `globalPrefix + controllerPath + methodPath`.
4. Registers compiled handlers in Express/Fastify router.
5. Wraps handlers with guard/pipe/interceptor/filter pipeline.

#### Example

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

Resolved routing intent:
1. `GET /users/:id` -> `getById`
2. `POST /users` -> `create` (guard-protected)

#### Why this design is powerful

1. **Declarative and local**
   Routing rules live near the handler code.

2. **Composable**
   Class-level and method-level decorators combine naturally.

3. **Framework consistency**
   Same pattern applies across REST, GraphQL resolvers, and microservice message
   handlers (with transport-specific decorators).

</details>

<details>
<summary>12. What is the difference between imports, exports, providers, and declarations in @Module?</summary>

#### NestJS

In NestJS modules, `imports`, `providers`, and `exports` are the core visibility
and dependency boundaries. `declarations` is **not** a NestJS module field (it is
an Angular concept), so using it in `@Module()` is incorrect.

#### Correct module fields

1. **`providers`**
   Classes/factories/values created in this module's DI context.
   These are available inside the same module by default.

2. **`imports`**
   Other modules whose **exported providers** you want to use in this module.
   Importing a module does not expose all its providers, only exported ones.

3. **`exports`**
   Subset of this module's providers (or re-exported modules) that should be
   visible to modules importing this module.

4. **`controllers`**
   Route handlers owned by this module (for HTTP layer). They are not exported as
   injectable providers by default.

#### About `declarations`

1. `declarations` is used in Angular NgModules for components/directives/pipes.
2. NestJS `@Module()` does **not** support `declarations`.
3. NestJS analogs are mostly `controllers` + `providers`, depending on role.

#### Example

```ts
import { Module } from '@nestjs/common';

@Module({
  providers: [UsersService],     // created in UsersModule context
  exports: [UsersService],       // made available to importing modules
})
export class UsersModule {}

@Module({
  imports: [UsersModule],        // can now inject exported UsersService
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Practical rule of thumb

1. Put service/repository/factory classes in `providers`.
2. Put route handlers in `controllers`.
3. Put needed external modules in `imports`.
4. Put only reusable API surface in `exports` (avoid over-exporting).

</details>

<details>
<summary>13. What is the difference between @Module imports and @Module providers?</summary>

#### NestJS

`imports` and `providers` in `@Module()` solve different DI concerns:
1. `imports` connects modules.
2. `providers` defines what this module creates in its own DI scope.

#### `providers`: local definitions

1. Declares services/factories/values instantiated in this module context.
2. Available for injection inside this module.
3. Not visible to other modules unless explicitly exported.

Example:

```ts
@Module({
  providers: [UsersService],
})
export class UsersModule {}
```

#### `imports`: external dependencies

1. Pulls in other modules to consume their **exported** providers.
2. Does not copy all internals of imported module.
3. Creates explicit module dependency graph.

Example:

```ts
@Module({
  imports: [UsersModule], // can inject only what UsersModule exports
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Combined example with exports

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

#### Practical distinction

1. Add to `providers` when you **own and create** the dependency here.
2. Add to `imports` when dependency is **owned by another module** and exported.
3. If injection fails, check:
   1. Provider is registered in source module `providers`.
   2. Source module exports it in `exports`.
   3. Consumer module includes source module in `imports`.

</details>

<details>
<summary>14. What are dynamic modules and when should you use them?</summary>

#### NestJS

Dynamic modules are modules whose configuration is produced at runtime via static
factory methods (commonly `forRoot`, `forRootAsync`, `register`,
`registerAsync`). They let you build reusable modules that can be configured
differently across apps/environments.

#### Why dynamic modules exist

1. **Runtime configuration**
   Pass options (URLs, API keys, feature flags, strategy choices) when importing
   a module.

2. **Reusable library modules**
   Package one module that can be consumed by many apps with different settings.

3. **Async initialization**
   Resolve config from `ConfigService`, secrets managers, or remote sources.

4. **Conditional providers**
   Create providers based on options (e.g., Redis vs in-memory cache).

#### Typical API patterns

1. `forRoot(options)` for app-wide singleton config.
2. `forRootAsync({...})` when config depends on async factories/injected deps.
3. `register(options)` for feature-scoped/per-import configuration.

#### Example

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

Usage:

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

#### When you should use dynamic modules

1. Building shared infrastructure modules (DB, mail, cache, queue, auth clients).
2. Needing environment-specific or tenant-specific setup.
3. Requiring async bootstrapping with `ConfigModule` and injected factories.

#### When not necessary

1. If module config is static and app-local, regular modules are simpler.
2. If only one provider needs variability, a factory provider may be enough.

</details>

<details>
<summary>15. What is the difference between provider types in NestJS? (useClass, useValue, useFactory)</summary>

#### NestJS

NestJS providers can be registered with different strategies depending on how an
instance/value should be created. The most common are `useClass`, `useValue`, and
`useFactory`.

#### 1) `useClass`

Creates an instance of a class through Nest DI.

1. Best for standard service implementations.
2. Supports constructor injection automatically.
3. Useful for swapping implementations by environment.

```ts
{
  provide: PaymentPort,
  useClass: StripePaymentService,
}
```

#### 2) `useValue`

Binds a token to a ready-made value/object/constant.

1. No instantiation by Nest.
2. Great for config objects, SDK singletons, mocks in tests.
3. Fast and simple, but no DI lifecycle for that value.

```ts
{
  provide: 'APP_CONFIG',
  useValue: { region: 'eu', retries: 3 },
}
```

#### 3) `useFactory`

Creates provider value via a factory function.

1. Can compute object dynamically.
2. Can inject other providers into factory (`inject` array).
3. Works for sync and async initialization.

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

#### Quick comparison

1. **`useClass`**: "Instantiate this class with DI."
2. **`useValue`**: "Use this exact value as-is."
3. **`useFactory`**: "Build value with custom logic (and optional injected deps)."

#### When to choose which

1. Choose `useClass` for normal app services and polymorphic implementations.
2. Choose `useValue` for constants, third-party instances, and test doubles.
3. Choose `useFactory` for conditional/async construction and complex setup.

#### Practical note

All three strategies are resolved by **token** (`provide`). Good token design
(class token, symbol, or string constant) is critical for maintainable DI.

</details>

<details>
<summary>16. What is provider scope? (DEFAULT, REQUEST, TRANSIENT)</summary>

#### NestJS

Provider scope in NestJS defines **how long provider instances live** and **how
often new instances are created** by the DI container.

#### Scope types

1. **`DEFAULT` (singleton)**
   One shared instance for the whole application lifecycle.

2. **`REQUEST`**
   New instance per incoming request (HTTP/RPC/message context).

3. **`TRANSIENT`**
   New instance every time the provider is injected/resolved.

#### 1) `DEFAULT` scope

1. Most performant and most common.
2. Ideal for stateless services (business logic, repositories, mappers).
3. Shared state inside such service is global for the app process.

```ts
@Injectable()
export class UsersService {}
```

#### 2) `REQUEST` scope

1. Use when service must be request-aware (tenant, correlation ID, per-request
   cache, user context).
2. Increases object creation overhead.
3. If a singleton depends on request-scoped provider, the dependency graph may
   need scope propagation adjustments.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.REQUEST })
export class RequestContextService {}
```

#### 3) `TRANSIENT` scope

1. Fresh instance each injection point.
2. Useful for lightweight, stateful helpers where shared instance is undesirable.
3. Can be expensive if overused in deep object graphs.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.TRANSIENT })
export class AuditBuilder {}
```

#### Practical decision guide

1. Start with `DEFAULT`.
2. Move to `REQUEST` only for real per-request state requirements.
3. Use `TRANSIENT` for narrowly scoped, mutable helper objects.

#### Performance and architecture note

Scope is both a correctness and performance choice. Overusing non-singleton
scopes can increase latency and memory churn, so apply them intentionally.

</details>

<details>
<summary>17. How do you handle circular dependencies (forwardRef) in large systems?</summary>

#### NestJS

Circular dependencies happen when two providers/modules depend on each other
directly or through a chain. In NestJS, the first-line fix is architectural
decoupling; `forwardRef()` is a tactical tool when refactor is not immediately
possible.

#### Why circular dependencies are risky

1. Tight coupling between domains.
2. Harder testing and refactoring.
3. Unclear ownership boundaries.
4. Bootstrapping/DI resolution complexity.

#### Preferred strategy: remove the cycle

1. **Extract shared logic**
   Move common behavior to a third service/module (`SharedDomainService`).

2. **Depend on abstraction tokens**
   Replace direct class dependency with interface-like token + adapter.

3. **Domain events / async messaging**
   Publish event from A, handle in B instead of direct call chain.

4. **Re-slice module boundaries**
   Reorganize by use-case/domain so one direction of dependency is preserved.

#### `forwardRef()` for unavoidable cases

Use `forwardRef()` when two providers/modules must reference each other during DI
resolution.

Provider-level example:

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

Module-level example:

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

#### Large-system guidance

1. Treat `forwardRef()` as temporary/edge-case, not default design.
2. Track circular deps in architecture review and remove over time.
3. Add tests around cycle-critical flows before refactoring.
4. Prefer uni-directional dependency graphs between bounded contexts.

</details>

<details>
<summary>18. How do you structure a scalable NestJS application?</summary>

#### NestJS

A scalable NestJS application is structured around clear domain boundaries,
dependency direction, and predictable cross-cutting patterns.

#### Core structural principles

1. **Modular by domain (bounded contexts)**
   Split by business capabilities (`Users`, `Billing`, `Orders`), not by
   technical layers only.

2. **Layered responsibilities inside each module**
   Keep controllers thin, services orchestration-focused, and infrastructure
   adapters isolated.

3. **Dependency rule**
   Higher-level business logic must not depend directly on framework/infrastructure
   details.

4. **Explicit contracts**
   Use DTOs, validation schemas, and interfaces/tokens for boundaries.

#### Practical module layout (example)

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

#### Architectural patterns that scale

1. **Feature modules + shared kernel**
   Keep shared utilities minimal to avoid "god common module".

2. **Ports and adapters**
   Business layer depends on abstractions; adapters implement DB/API/message-bus
   details.

3. **CQRS where complexity justifies it**
   Separate write/read models for complex domains, not by default everywhere.

4. **Async boundaries**
   Use events/queues for cross-module workflows and eventual consistency.

#### Operational scalability concerns

1. **Configuration management**
   Centralized typed config with environment validation.

2. **Observability**
   Structured logging, tracing, metrics, and correlation IDs.

3. **Error strategy**
   Global exception filters + domain-specific error mapping.

4. **Performance**
   Caching, pagination, backpressure, DB indexing, and avoiding request-scope
   overuse.

#### Team scalability practices

1. Enforce lint/format/type/test gates in CI.
2. Keep module ownership clear (codeowners or service ownership map).
3. Review architecture decisions (ADRs) for new cross-domain dependencies.
4. Prefer incremental refactoring over big-bang rewrites.

#### Bottom line

Scalability in NestJS is mostly an architecture discipline: domain-oriented
modules, controlled dependencies, and standardized platform concerns around them.

</details>

<details>
<summary>19. How do you design a REST API with proper separation of concerns?</summary>

#### NestJS

Proper separation of concerns in a NestJS REST API means each layer has a single,
clear responsibility and dependencies flow in one direction.

#### Recommended responsibility split

1. **Controller layer (transport)**
   Handles HTTP concerns only: routing, status codes, request/response mapping,
   auth decorators, and input binding.

2. **Application/service layer (use cases)**
   Orchestrates business workflows and transactions; no HTTP-specific logic.

3. **Domain layer (business rules)**
   Encapsulates core rules, invariants, entities/value objects, domain services.

4. **Infrastructure layer**
   Implements persistence, external APIs, queues, and other adapters.

#### What should NOT be mixed

1. Database queries in controllers.
2. HTTP objects (`Request`, `Response`) inside domain logic.
3. Validation/business invariants scattered across multiple layers.
4. External SDK details leaking into use-case contracts.

#### Practical flow

1. Controller receives DTO (`@Body`, `@Query`, `@Param`).
2. Pipe validates/transforms DTO.
3. Controller calls application service method.
4. Service uses repositories/ports and domain rules.
5. Service returns result model.
6. Controller maps result to response DTO/view model.

#### Example skeleton

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

#### Design techniques that help

1. **DTOs for API contracts**
   Separate input/output contracts from internal entities.

2. **Repository/port interfaces**
   Depend on abstractions, not ORM clients directly in business layer.

3. **Global cross-cutting components**
   Use guards/pipes/interceptors/filters for auth, validation, logging, errors.

4. **Versioning and idempotency**
   Apply API versioning strategy and idempotency keys for unsafe operations.

5. **Consistent error model**
   Map domain/infrastructure errors to stable HTTP problem responses.

#### Outcome

With this separation, your API is easier to test, refactor, and scale: transport
changes do not break domain logic, and infrastructure can evolve independently.

</details>

<details>
<summary>20. What is the full request lifecycle in NestJS?</summary>

#### NestJS

The NestJS request lifecycle is a deterministic pipeline around a matched route
handler. Understanding this order is critical for debugging auth, validation, and
response-shaping behavior.

#### High-level sequence

1. Incoming request reaches platform adapter (Express/Fastify).
2. Route is matched to a controller method.
3. Nest executes framework pipeline components in defined order.
4. Response is returned (or exception is handled by filters).

#### Detailed lifecycle order

1. **Middleware**
   Runs before guards; used for low-level request preprocessing (logging,
   correlation ID, raw header manipulation, etc.).

2. **Guards**
   Decide whether execution is allowed (`canActivate`).
   If guard returns `false`/throws, request stops here.

3. **Interceptors (before handler)**
   Wrap execution; can start timers, attach context, or short-circuit behavior.

4. **Pipes**
   Run on route arguments to transform/validate incoming data (`@Body`, `@Param`,
   `@Query`, custom params).

5. **Controller handler**
   Business use case is invoked (usually delegating to service layer).

6. **Interceptors (after handler)**
   Can map/stream/cache responses, and finalize observability logic.

7. **Exception filters**
   Catch unhandled exceptions and convert to HTTP responses.

#### Visual execution model

1. Middleware -> Guards -> Interceptors (pre) -> Pipes -> Handler ->
   Interceptors (post) -> Response
2. Any thrown error in pipeline/handler -> Exception Filters

#### Scope and precedence notes

1. Most pipeline components can be applied at:
   1. Global level
   2. Controller level
   3. Route-handler level
2. Nest merges these levels; route-level config is usually the most specific.

#### Practical debugging takeaway

If behavior is unexpected:
1. Check whether request is blocked by guard first.
2. Verify pipe transformation/validation on parameters.
3. Inspect interceptor chain for response mapping changes.
4. Confirm exception filter formatting for thrown errors.

Knowing this order prevents "magic" assumptions and makes production incidents
much faster to diagnose.

</details>

<details>
<summary>21. What is the difference between Middleware, Guards, Pipes, and Interceptors?</summary>

#### NestJS

These four NestJS components all participate in request processing, but they have
different responsibilities and run at different lifecycle stages.

#### Quick role comparison

1. **Middleware**
   Pre-routing/pre-handler HTTP preprocessing.

2. **Guards**
   Authorization gate: decide whether request may continue.

3. **Pipes**
   Transform and validate handler arguments.

4. **Interceptors**
   Wrap handler execution before/after, enabling cross-cutting response logic.

#### Deeper difference by responsibility

1. **Middleware**
   Best for generic transport-level work: request logging, correlation IDs,
   headers, cookie parsing, raw request mutation.

2. **Guards**
   Best for auth/authz decisions: JWT presence, role checks, policy checks.
   Return `true/false` (or throw) to allow/deny route execution.

3. **Pipes**
   Best for input correctness: parsing (`string -> number`), validation (DTO
   rules), sanitization/normalization at parameter level.

4. **Interceptors**
   Best for execution wrapping: response mapping, caching, metrics timing,
   tracing, timeout/retry wrappers, stream handling.

#### Lifecycle position

1. Middleware
2. Guards
3. Interceptors (before)
4. Pipes
5. Handler
6. Interceptors (after)
7. Exception filters (error path)

#### Typical examples

1. Middleware: attach `requestId`.
2. Guard: reject request if token invalid.
3. Pipe: validate `CreateUserDto`.
4. Interceptor: transform `{ data, meta }` response envelope.

#### Selection rule of thumb

1. Need to decide **who can access**? -> Guard.
2. Need to ensure **input shape/type**? -> Pipe.
3. Need **before/after handler wrapping**? -> Interceptor.
4. Need low-level HTTP preprocessing outside route semantics? -> Middleware.

</details>

<details>
<summary>22. How do you apply Middleware globally vs for a specific route?</summary>

#### NestJS

In NestJS, middleware can be applied either globally (for many/all routes) or
selectively (specific controllers/routes). The mechanism differs from guards and
interceptors because middleware is configured through module consumer API or app
bootstrap.

#### 1) Apply middleware globally

Use this when behavior is needed for almost every request (request IDs, common
logging, security headers bootstrap, etc.).

Module-level global configuration:

```ts
import { MiddlewareConsumer, Module, NestModule } from '@nestjs/common';

@Module({})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer.apply(LoggerMiddleware).forRoutes('*');
  }
}
```

You can also target all controllers by class-based patterns in `forRoutes(...)`.

#### 2) Apply middleware to specific routes/controllers

Use this for feature-specific concerns only.

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
        UsersController, // all routes in controller
        { path: 'users/:id', method: RequestMethod.PATCH }, // exact route
      );
  }
}
```

#### Excluding routes

You can attach broad middleware and exclude sensitive/public endpoints:

```ts
consumer
  .apply(AuthMiddleware)
  .exclude(
    { path: 'health', method: RequestMethod.GET },
    { path: 'auth/login', method: RequestMethod.POST },
  )
  .forRoutes('*');
```

#### Practical guidance

1. Prefer global middleware only for truly cross-cutting concerns.
2. Keep middleware lightweight; heavy authz logic belongs in Guards.
3. Use route-specific middleware for bounded feature behavior.
4. If you need DI-heavy business checks, move logic from middleware to Guards or
   Interceptors.

</details>

<details>
<summary>23. What is ExecutionContext and how is it used?</summary>

#### NestJS

`ExecutionContext` is a NestJS abstraction that describes the current handler
execution environment. It extends `ArgumentsHost` and gives framework components
(Guards, Interceptors, Filters, custom decorators) a unified way to access
request-specific data across different transports.

#### Why `ExecutionContext` exists

1. **Transport-agnostic access**
   Same API pattern works for HTTP, WebSockets, and microservices.

2. **Handler/class introspection**
   You can inspect which controller class and method are being executed.

3. **Cross-cutting component consistency**
   Guards/interceptors/filters can operate with one context model.

#### Key APIs

1. `context.getType()`
   Returns execution type (`http`, `ws`, `rpc`).

2. `context.switchToHttp()`
   Gives access to `getRequest()`, `getResponse()`, `getNext()`.

3. `context.switchToWs()` / `context.switchToRpc()`
   Access protocol-specific data for websockets/microservices.

4. `context.getClass()` and `context.getHandler()`
   Returns current controller class and method reference.

#### Common usage in a Guard

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

#### Common usage with metadata + Reflector

```ts
const isPublic = this.reflector.getAllAndOverride<boolean>('isPublic', [
  context.getHandler(),
  context.getClass(),
]);
```

This pattern reads route/class metadata (e.g., `@Public()`, `@Roles(...)`) and is
widely used in authorization guards.

#### Practical takeaway

Think of `ExecutionContext` as the framework's runtime envelope for the current
endpoint call: it tells you **where you are** (handler/class/transport) and lets
you safely access transport-specific request data.

</details>

<details>
<summary>24. What is a Guard and how does it differ from Middleware?</summary>

#### NestJS

A **Guard** in NestJS is a class implementing `CanActivate` that decides whether
the current request is allowed to reach a route handler.

#### What a Guard does

1. Runs before handler execution.
2. Returns `true` to allow, `false` (or throws) to deny.
3. Has access to `ExecutionContext` (handler, controller, transport, request).
4. Is commonly used for authentication and authorization.

#### How Guard differs from Middleware

1. **Decision purpose**
   Guard is an explicit authorization gate.
   Middleware is generic request preprocessing.

2. **Framework awareness**
   Guard knows the target handler/class via `ExecutionContext`.
   Middleware usually does not have route-handler metadata context.

3. **Lifecycle position**
   Middleware runs earlier.
   Guard runs after middleware, before pipes/interceptors/handler.

4. **Typical use cases**
   Guard: JWT/roles/policies.
   Middleware: logging, request IDs, header normalization, raw request mutation.

#### Example Guard

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

#### Rule of thumb

1. Need to decide "can this user access this route?" -> **Guard**.
2. Need low-level pre-handler HTTP processing regardless of route semantics ->
   **Middleware**.

</details>

<details>
<summary>25. How do Guards integrate with authorization?</summary>

#### NestJS

Guards are the primary authorization gate in NestJS. They evaluate whether the
current authenticated principal can access a specific route, usually by combining
request identity with route metadata (roles, policies, permissions).

#### Typical authorization flow with Guards

1. **Authentication step**
   A prior guard (or Passport strategy) validates token/session and attaches
   `request.user`.

2. **Metadata declaration on route**
   Route is annotated with requirements, e.g. `@Roles('admin')` or policy keys.

3. **Authorization guard evaluation**
   Guard reads metadata via `Reflector` + reads `request.user` and decides access.

4. **Allow or deny**
   Return `true` to proceed, otherwise return `false` or throw
   `ForbiddenException`.

#### Role-based example (RBAC)

Roles decorator:

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

Usage:

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### Integration patterns in real systems

1. **Stacked guards**
   `JwtAuthGuard` (identity) + `Roles/PoliciesGuard` (authorization logic).

2. **ABAC/policy engine**
   Guard delegates decision to policy service (subject, action, resource).

3. **Context-aware checks**
   Guard reads route params/resource owner and enforces ownership rules.

#### Best practices

1. Keep guards thin; move heavy logic into dedicated authorization services.
2. Use metadata decorators for declarative, auditable access rules.
3. Distinguish authentication failures (`401`) from authorization failures (`403`).
4. Test guards with both positive and negative permission scenarios.

</details>

<details>
<summary>26. What is @SetMetadata() and how does it work with Guards through Reflector?</summary>

#### NestJS

`@SetMetadata()` is a NestJS helper decorator used to attach custom metadata to a
class or method. Guards can then read that metadata via `Reflector` and enforce
authorization or other route-specific behavior.

#### Core idea

1. `@SetMetadata(key, value)` writes metadata on route/class.
2. Guard uses `Reflector` to read metadata at runtime.
3. Guard decides whether request is allowed.

#### Why this pattern is important

1. **Declarative access rules**
   Permissions are visible directly on endpoints.

2. **Separation of concerns**
   Controllers declare intent; guards implement enforcement logic.

3. **Reusability**
   One guard can handle many routes with different metadata values.

#### Example: roles metadata

Decorator:

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Usage on endpoint:

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

Guard reading metadata:

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';
import { Reflector } from '@nestjs/core';
import { ROLES_KEY } from './roles.decorator';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private readonly reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.getAllAndOverride<string[]>(ROLES_KEY, [
      context.getHandler(), // method metadata
      context.getClass(),   // controller metadata
    ]);

    if (!requiredRoles) return true;

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];
    return requiredRoles.some(role => userRoles.includes(role));
  }
}
```

#### `Reflector` methods you will use most

1. `get(key, target)` -> reads metadata from a specific target.
2. `getAllAndOverride(key, [handler, class])` -> method metadata overrides class.
3. `getAllAndMerge(key, [handler, class])` -> combines values from both levels.

#### Practical takeaway

`@SetMetadata()` + `Reflector` is the standard NestJS mechanism for building
clean, scalable, metadata-driven authorization and route behavior rules.

</details>

<details>
<summary>27. How do you implement JWT authentication via a Guard?</summary>

#### NestJS

JWT authentication in NestJS is commonly implemented with a Guard that validates
the token and attaches user identity to the request context.

#### Standard architecture

1. **AuthService**
   Signs and verifies JWTs.

2. **JWT strategy/guard**
   Extracts bearer token, validates it, and sets `request.user`.

3. **Protected routes**
   Use `@UseGuards(...)` to require authentication.

You can implement this with Passport (`@nestjs/passport`) or a custom guard.

#### Minimal custom JWT Guard (without Passport)

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
      req.user = payload; // attach identity for downstream handlers/guards
      return true;
    } catch {
      throw new UnauthorizedException('Invalid or expired token');
    }
  }
}
```

#### Protecting routes

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

#### `JwtModule` setup

```ts
JwtModule.register({
  secret: process.env.JWT_ACCESS_SECRET,
  signOptions: { expiresIn: '15m' },
});
```

#### Production best practices

1. Use separate access and refresh secrets.
2. Keep access tokens short-lived.
3. Validate issuer/audience/algorithm explicitly.
4. Prefer `401 Unauthorized` for token failures.
5. Combine with authorization guard (roles/policies) for permissions.
6. Add token revocation strategy where required (blacklist/versioning/rotation).

#### Practical note

In larger apps, Passport's `AuthGuard('jwt')` + `JwtStrategy` is often cleaner
for reuse and ecosystem integration, but the core principle remains the same:
extract -> verify -> attach user -> allow/deny.

</details>

<details>
<summary>28. How do you implement RBAC and ABAC in NestJS, and when is each approach better?</summary>

#### NestJS

RBAC and ABAC are two authorization models that can both be implemented in NestJS
using Guards + metadata + authorization services.

#### RBAC vs ABAC

1. **RBAC (Role-Based Access Control)**
   Access is granted by user roles (e.g., `admin`, `editor`, `viewer`).

2. **ABAC (Attribute-Based Access Control)**
   Access is granted by evaluating attributes (user, resource, action, context):
   ownership, department, region, status, time window, etc.

#### When each model is better

1. Choose **RBAC** when:
   1. Permission model is simple and stable.
   2. Role hierarchy is clear.
   3. Fast implementation and easy auditing are priorities.

2. Choose **ABAC** when:
   1. Rules depend on resource data and context.
   2. You need fine-grained, dynamic decisions.
   3. Multi-tenant or enterprise policy complexity is high.

3. Use **hybrid RBAC + ABAC** in most real systems:
   RBAC for coarse access, ABAC for sensitive operations.

#### RBAC implementation pattern in NestJS

1. `@Roles(...)` decorator via `SetMetadata`.
2. `RolesGuard` reads metadata with `Reflector`.
3. Guard compares required roles with `request.user.roles`.

```ts
export const Roles = (...roles: string[]) => SetMetadata('roles', roles);
```

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Delete(':id')
removeUser() {}
```

#### ABAC implementation pattern in NestJS

1. Define a policy ability service (`can(user, action, resource)`).
2. In guard, load target resource (or enough attributes).
3. Evaluate policy and allow/deny.

```ts
@Injectable()
export class PoliciesGuard implements CanActivate {
  constructor(private readonly policy: PolicyService) {}

  async canActivate(ctx: ExecutionContext): Promise<boolean> {
    const req = ctx.switchToHttp().getRequest();
    const user = req.user;
    const order = await req.orderLoader.load(req.params.id); // example
    return this.policy.can(user, 'update', order);
  }
}
```

#### Design best practices

1. Keep guard thin; delegate rule logic to dedicated policy service.
2. Avoid hardcoding rules in controllers.
3. Cache policy-relevant lookups when safe.
4. Return `403 Forbidden` for authorization denials (not `401`).
5. Log decision context for auditability in critical domains.

#### Practical recommendation

Start with RBAC for baseline speed, then introduce ABAC in high-risk/high-variance
flows (ownership checks, data sensitivity, tenant boundaries, conditional actions).

</details>

<details>
<summary>29. How do you implement refresh token rotation and why is it important?</summary>

#### NestJS

Refresh token rotation means issuing a **new refresh token on every refresh**
request and invalidating the previous one. This reduces replay risk if a refresh
token is stolen.

#### Why it is important

1. Limits damage from leaked refresh tokens.
2. Detects token reuse attacks (stolen old token used again).
3. Enables secure long-lived sessions without long-lived access tokens.
4. Improves session control across devices.

#### Recommended token model

1. **Access token**: short TTL (e.g., 5-15 min), stateless JWT.
2. **Refresh token**: longer TTL (days/weeks), rotated every use.
3. Store only **hashed refresh token** (or token family metadata) in DB.
4. Track token family/session (`sessionId`, `jti`, `rotatedFrom`, `revokedAt`).

#### Rotation flow in NestJS

1. User logs in -> issue access + refresh token (RT1), persist RT1 hash + metadata.
2. Client calls `/auth/refresh` with RT1.
3. Server verifies signature/expiry and compares hash with active stored token.
4. If valid:
   1. Revoke RT1.
   2. Issue AT2 + RT2.
   3. Persist RT2 hash as active token for that session.
5. If old RT1 is reused later:
   1. Mark as suspicious reuse.
   2. Revoke whole session/token family.
   3. Force re-authentication.

#### Minimal service-level sketch

```ts
async rotateRefreshToken(userId: string, presentedRt: string, sessionId: string) {
  const session = await this.sessionsRepo.findById(sessionId);
  if (!session || session.revokedAt) throw new UnauthorizedException();

  const matches = await this.hash.compare(presentedRt, session.refreshTokenHash);
  if (!matches) {
    await this.sessionsRepo.revokeFamily(session.familyId); // reuse detection response
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

#### NestJS implementation notes

1. Use dedicated `JwtModule` config/secrets for access vs refresh tokens.
2. Protect refresh endpoint with refresh-token guard/strategy.
3. Keep refresh token in secure httpOnly cookie when possible.
4. Add device/session table for multi-device logout and revocation.

#### Security best practices

1. Hash refresh tokens at rest.
2. Bind refresh token to session/device metadata.
3. Rotate on every refresh request, no exceptions.
4. Revoke token family on detected reuse.
5. Log rotation/reuse events for incident monitoring.

</details>

<details>
<summary>30. What is a Pipe in NestJS and when should you use it?</summary>

#### NestJS

A Pipe in NestJS is a class that implements `PipeTransform` and runs before a
route handler to **transform** and/or **validate** incoming data.

#### What Pipes do

1. **Transformation**
   Convert raw transport values into expected types (e.g., string -> number,
   string -> UUID object, trimming/normalization).

2. **Validation**
   Enforce DTO/schema rules and reject invalid input early.

3. **Fail-fast behavior**
   Throw an exception (typically `BadRequestException`) before business logic runs.

#### Where Pipes fit in lifecycle

1. Middleware
2. Guards
3. Interceptors (pre)
4. **Pipes**
5. Handler
6. Interceptors (post)
7. Exception filters

#### Built-in pipes examples

1. `ValidationPipe`
2. `ParseIntPipe`
3. `ParseBoolPipe`
4. `ParseUUIDPipe`
5. `DefaultValuePipe`
6. `ParseArrayPipe`

#### Usage examples

Parameter-level:

```ts
@Get(':id')
findOne(@Param('id', ParseIntPipe) id: number) {
  return this.usersService.findOne(id);
}
```

Global validation:

```ts
app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
    forbidNonWhitelisted: true,
    transform: true,
  }),
);
```

#### Custom Pipe example

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

#### When to use Pipes

1. Validate request DTOs and query/param payloads.
2. Parse primitive route/query params to typed values.
3. Centralize input normalization rules.
4. Keep controllers/services free from repetitive validation/parsing code.

#### Rule of thumb

Use Pipes for **input correctness**, Guards for **access control**, Interceptors
for **execution wrapping**, and Middleware for **low-level request preprocessing**.

</details>

<details>
<summary>31. What is a DTO?</summary>

#### NestJS

A DTO (Data Transfer Object) is an object shape used to transfer data between
application boundaries, most commonly between the client and your API layer.

In NestJS, DTOs are typically implemented as **classes** to support runtime
validation and transformation with `class-validator` and `class-transformer`.

#### Why DTOs are important

1. **Explicit API contracts**
   Define exactly what input/output fields are allowed.

2. **Validation boundary**
   Reject malformed or unsafe payloads before business logic executes.

3. **Decoupling**
   Prevent direct exposure of domain entities/ORM models to external clients.

4. **Maintainability**
   Clear request/response schemas make refactoring safer and documentation easier.

#### Typical DTO types in NestJS

1. **Request DTOs**
   `CreateUserDto`, `UpdateUserDto`, query/filter DTOs.

2. **Response/View DTOs**
   Controlled output shape (hide internal fields like passwords, tokens, flags).

3. **Command-style DTOs**
   Inputs for specific use cases (especially in CQRS-style modules).

#### Example request DTO

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

Controller usage:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Practical rules

1. Never use raw `any` payloads in controllers.
2. Keep DTOs transport-focused (not full domain entities).
3. Separate input DTOs from output DTOs.
4. Combine DTOs with global `ValidationPipe` for consistent enforcement.

</details>

<details>
<summary>32. What is the difference between interface and class for typing DTOs — and why is class preferred in NestJS?</summary>

#### NestJS

Both interfaces and classes can describe TypeScript shapes, but in NestJS DTOs
are usually implemented as **classes** because Nest validation/transformation
works at runtime, not only compile time.

#### Key difference

1. **Interface**
   Exists only at TypeScript compile time; erased at runtime.

2. **Class**
   Exists at runtime as a real constructor/function object; can carry decorator
   metadata used by Nest pipes and tooling.

#### Why class is preferred for DTOs in NestJS

1. **Runtime validation support**
   `class-validator` decorators (`@IsEmail`, `@IsString`, etc.) are attached to
   class properties and used by `ValidationPipe`.

2. **Transformation support**
   `class-transformer` can instantiate/transform plain payloads into class
   instances (`transform: true` in `ValidationPipe`).

3. **OpenAPI/Swagger integration**
   DTO classes provide metadata for `@nestjs/swagger` schema generation.

4. **Mapped types support**
   `PartialType`, `PickType`, `OmitType`, `IntersectionType` operate on classes.

#### Practical example

Interface (type-only, no runtime metadata):

```ts
interface CreateUserDto {
  email: string;
}
```

Class DTO (runtime + decorators):

```ts
import { IsEmail } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;
}
```

With global validation:

```ts
app.useGlobalPipes(new ValidationPipe({ whitelist: true, transform: true }));
```

Only the class-based DTO can be validated/transformed using decorator metadata.

#### When interfaces are still useful

1. Internal service contracts not requiring runtime reflection.
2. Generic utility typing and domain abstractions.
3. Read-only compile-time boundaries where validation is handled elsewhere.

#### Rule of thumb

Use **classes for external API DTOs** (controller input/output contracts). Use
interfaces for internal compile-time contracts where runtime metadata is not
needed.

</details>

<details>
<summary>33. What are mapped types in NestJS? (PartialType, OmitType, PickType, IntersectionType)</summary>

#### NestJS

Mapped types in NestJS are utilities that generate new DTO classes from existing
ones, reducing duplication while preserving validation/Swagger metadata.

They are commonly imported from:
1. `@nestjs/mapped-types` (framework-agnostic usage)
2. `@nestjs/swagger` (when using Swagger and schema decorators)

#### Why mapped types are useful

1. Avoid repetitive DTO definitions.
2. Keep create/update DTOs consistent.
3. Preserve decorator metadata for validation/docs.
4. Make API contract evolution safer.

#### Main mapped types

1. **`PartialType(BaseDto)`**
   Makes all properties optional.
   Typical use: `UpdateDto` from `CreateDto`.

2. **`PickType(BaseDto, ['a', 'b'])`**
   Keeps only selected properties.
   Typical use: slim input for a focused endpoint.

3. **`OmitType(BaseDto, ['x'])`**
   Excludes selected properties.
   Typical use: hide forbidden input fields like `role`, `id`.

4. **`IntersectionType(A, B)`**
   Combines properties from two DTO classes.
   Typical use: composed filter/pagination/query DTOs.

#### Example

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

#### Practical cautions

1. Mapped types operate on class metadata; base DTO should be a class.
2. Keep DTO inheritance readable; avoid deep, confusing chains.
3. Review generated OpenAPI schema after complex intersections.

#### Rule of thumb

Use mapped types for contract reuse, especially `Create` -> `Update`, while
keeping DTO hierarchy simple and explicit.

</details>

<details>
<summary>34. How do you implement validation using class-validator and pipes?</summary>

#### NestJS

In NestJS, validation is commonly implemented with:
1. DTO classes annotated by `class-validator` decorators.
2. `ValidationPipe` (global or route-level) to enforce rules at runtime.

#### Step 1: Define DTO with validation decorators

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

#### Step 2: Enable `ValidationPipe`

Global setup (recommended):

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

#### What these options do

1. `whitelist: true`
   Strips properties not defined in DTO.

2. `forbidNonWhitelisted: true`
   Throws error when unknown properties are present.

3. `transform: true`
   Converts payload into DTO instance and applies type transformation.

4. `enableImplicitConversion: true`
   Allows safe primitive conversion based on DTO property types.

#### Step 3: Use DTO in controller

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Route-level validation (when needed)

```ts
@Post('strict')
@UsePipes(new ValidationPipe({ whitelist: true, forbidNonWhitelisted: true }))
createStrict(@Body() dto: CreateUserDto) {}
```

#### Typical validation error response

1. HTTP `400 Bad Request`
2. Message array with failed constraints
3. Clear field-level diagnostics for client developers

#### Best practices

1. Keep DTOs focused per endpoint/use case.
2. Separate Create/Update DTOs (often via `PartialType`).
3. Do not rely on validation only in services if controllers accept external data.
4. Customize `exceptionFactory` in `ValidationPipe` for consistent API error shape.

</details>

<details>
<summary>35. How do you implement a global Exception Filter and custom HTTP errors?</summary>

#### NestJS

In NestJS, a global Exception Filter centralizes error-to-response mapping so all
unhandled exceptions produce a consistent API format.

Custom HTTP errors are typically created by extending `HttpException` or using
built-in exceptions (`BadRequestException`, `NotFoundException`, etc.).

#### 1) Create a global exception filter

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

#### 2) Register filter globally

In `main.ts`:

```ts
app.useGlobalFilters(new GlobalExceptionFilter());
```

#### 3) Create custom HTTP exception

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

Usage:

```ts
if (!canCloseOrder) {
  throw new BusinessRuleViolationException('Order cannot be closed in current state');
}
```

#### Why this approach is good

1. Consistent response format across the whole API.
2. Cleaner controllers/services (no repetitive try/catch for formatting).
3. Centralized observability hooks (logging, correlation IDs, error codes).
4. Easy to map domain/infrastructure errors to meaningful HTTP semantics.

#### Best practices

1. Avoid leaking internal stack traces in production responses.
2. Include machine-readable error codes for clients.
3. Preserve stack traces in logs (not necessarily in HTTP body).
4. Map expected business errors to 4xx; unexpected failures to 5xx.

</details>

<details>
<summary>36. How do you properly handle errors and return a consistent response structure?</summary>

#### NestJS

Proper error handling in NestJS means separating:
1. where errors are created (domain/application/infrastructure),
2. where errors are translated to HTTP (filters),
3. and how responses are standardized (global contract).

#### Recommended strategy

1. **Throw meaningful exceptions in business flow**
   Use domain-specific exceptions or appropriate `HttpException` subclasses.

2. **Centralize HTTP response formatting**
   Use a global exception filter to enforce one error schema.

3. **Standardize success responses too**
   Optionally use an interceptor for uniform success envelope.

4. **Preserve observability**
   Log error context (requestId, path, userId, stack) in one place.

#### Example consistent error response shape

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

#### Implementation components

1. **Global Exception Filter**
   Maps all exceptions to the same response structure.

2. **Custom exception classes**
   Encapsulate domain/business error code + message + status.

3. **Optional response interceptor**
   Wraps successful responses:
   `{ success: true, data, meta }`.

#### Error categorization guideline

1. **Validation/client input errors** -> `400`.
2. **Authentication errors** -> `401`.
3. **Authorization errors** -> `403`.
4. **Missing resources** -> `404`.
5. **Business rule conflicts** -> `409` or `422`.
6. **Unexpected system failures** -> `500`.

#### What to avoid

1. Returning ad-hoc error shapes from different controllers.
2. Swallowing exceptions and returning `200` with `"error"` in body.
3. Exposing internal stack traces/SQL errors in production responses.
4. Mixing transport formatting logic directly into services.

#### Practical best practices

1. Define an error code catalog (`USER_NOT_FOUND`, `TOKEN_EXPIRED`, etc.).
2. Add correlation/request ID to every error response and log entry.
3. Ensure global filter handles both known (`HttpException`) and unknown errors.
4. Cover error paths with e2e tests to lock API error contract.

</details>

<details>
<summary>37. How do you properly log errors without losing the stack trace in production?</summary>

#### NestJS

To log errors correctly in production, you need two parallel outputs:
1. **safe client response** (no sensitive internals),
2. **full structured server log** (including stack trace and context).

#### Core principle

Never expose stack traces to API clients, but always preserve them in logs for
debugging and incident response.

#### Recommended approach in NestJS

1. Capture errors centrally in a global exception filter.
2. Log with a structured logger (Pino/Winston/Nest Logger adapter).
3. Include stack, error code, request metadata, correlation ID, and user context.
4. Return sanitized error payload from filter.

#### Example (global filter logging stack)

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

#### What to log for production-grade diagnostics

1. Timestamp, level, service name, environment.
2. Request ID / trace ID.
3. Route, method, status code, latency.
4. Auth context (userId/tenantId when available).
5. Full stack + root cause chain.

#### Common mistakes

1. Logging only `error.message` (loses stack and cause chain).
2. String-concatenated logs instead of structured JSON logs.
3. Duplicate logging at multiple layers (noise).
4. Returning raw exception objects to clients.

#### Practical best practices

1. Use a single structured logger across app.
2. Add correlation ID middleware/interceptor early in request lifecycle.
3. Redact secrets/PII before log emission.
4. Forward logs to centralized observability stack (ELK, Datadog, Grafana Loki).
5. Test error paths to ensure stack is retained in logs after deploy.

</details>

<details>
<summary>38. What is ConfigModule and why should you use it instead of process.env?</summary>

#### NestJS

`ConfigModule` is NestJS’s configuration system (`@nestjs/config`) that loads,
validates, and provides environment/config values through DI.

Using `ConfigModule` is preferred over direct `process.env` access because it
centralizes config logic, improves type safety, and makes testing/maintenance
much cleaner.

#### Why `process.env` alone is not enough

1. Scattered environment reads across codebase.
2. No central validation of required variables.
3. String-only values without typed parsing.
4. Harder testing/mocking and poorer discoverability.

#### What `ConfigModule` gives you

1. **Centralized config loading**
   One place to define env files and config factories.

2. **Validation at startup**
   Fail fast if required vars are missing/invalid.

3. **Typed access via `ConfigService`**
   Better contracts and fewer runtime surprises.

4. **DI integration**
   Any provider can inject config cleanly.

5. **Environment-specific composition**
   Easy split for dev/staging/prod settings.

#### Basic setup

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

Usage:

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

#### Validation example (recommended)

Use `validationSchema` (Joi) or custom validation function:
1. Require mandatory vars.
2. Validate formats/ranges.
3. Stop app bootstrap on invalid config.

#### Practical recommendation

Use `process.env` only inside config factories/bootstrap boundaries. Everywhere
else, consume config through `ConfigService` or typed config providers for
consistency, testability, and safer production behavior.

</details>

<details>
<summary>39. How do you properly organize .env files for different environments (dev, staging, prod)?</summary>

#### NestJS

Proper `.env` organization should provide predictable configuration per
environment, avoid secret leaks, and keep local development convenient.

#### Recommended environment strategy

1. Keep one **base** file for shared defaults.
2. Add **environment-specific** files for overrides.
3. Keep secrets out of git and inject them via deployment platform/secret store.

Typical layout:
1. `.env` (shared local defaults)
2. `.env.development`
3. `.env.staging`
4. `.env.production`
5. `.env.test`
6. `.env.local` (developer machine overrides, gitignored)

#### With NestJS `ConfigModule`

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

Loading order matters: earlier files usually have higher priority in this pattern.

#### What should be committed vs ignored

1. Commit:
   1. `.env.example` (document all required keys without real secrets)
   2. Non-sensitive defaults if your policy allows

2. Do not commit:
   1. Real secrets/tokens/private keys
   2. `.env.local` and machine-specific overrides

#### Validation and fail-fast

Always validate config at startup (Joi or custom validator):
1. Required keys exist.
2. Types/ranges are valid (`PORT`, timeouts, feature flags).
3. URLs and credentials format are correct.

#### Production/staging best practices

1. Prefer platform secret managers (AWS SSM/Secrets Manager, Vault, Doppler, etc.)
   over plain files.
2. Rotate secrets regularly.
3. Separate staging/prod credentials strictly.
4. Keep `NODE_ENV` explicit in deployment config.
5. Never bake secrets into Docker images/source code.

#### Practical team workflow

1. Maintain `.env.example` as the contract.
2. Add onboarding script/check that verifies missing env vars.
3. Use typed config wrappers so app code never reads random env keys directly.
4. Document ownership for critical variables (DB, JWT, external APIs).

</details>

<details>
<summary>40. How do you use Joi or zod to validate configuration at application startup?</summary>

#### NestJS

Validate configuration at startup so the app fails fast on missing/invalid env
values instead of crashing later at runtime.

In NestJS this is typically done with `ConfigModule.forRoot(...)` plus either:
1. `validationSchema` (Joi), or
2. `validate` function (custom logic, often using Zod).

#### Option A: Joi with `validationSchema`

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

How it works:
1. Env is loaded.
2. Joi validates shape and constraints.
3. App bootstrap fails immediately if config is invalid.

#### Option B: Zod with `validate` function

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

Why teams like Zod:
1. Strong TS inference from schema.
2. Composable schemas for modular config.
3. Clear parse errors and transformation support.

#### Practical best practices

1. Validate all required secrets/URLs/ports at startup.
2. Coerce primitive types explicitly (`PORT`, booleans, timeouts).
3. Keep one schema as single source of truth.
4. Expose typed config through wrappers/services, not raw `process.env`.
5. Use different env files per environment, but one validation contract.

#### Joi vs Zod in short

1. **Joi**: mature, straightforward with built-in `validationSchema`.
2. **Zod**: TS-first typing and composability; great for typed config pipelines.

Both are production-valid; choose one and enforce it consistently.

</details>

<details>
<summary>41. How do you implement feature flags in NestJS?</summary>

#### NestJS

Feature flags in NestJS are typically implemented as a dedicated service that
evaluates whether a feature is enabled for a given context (environment, user,
tenant, percentage rollout, etc.).

#### Why feature flags matter

1. Safe gradual rollout.
2. Fast kill-switch for problematic features.
3. A/B experimentation.
4. Decoupling deployment from release.

#### Common architecture

1. **FeatureFlagService**
   Single entry point: `isEnabled(flag, context)`.

2. **Flag source**
   Env config, DB table, or external flag provider.

3. **Evaluation context**
   User ID, tenant ID, plan, region, app version, request metadata.

4. **Usage points**
   Guards, services, controllers, interceptors, UI response shaping.

#### Simple in-app implementation (config-based)

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

Usage in service:

```ts
if (this.flags.isEnabled('new_checkout', { userId, tenantId })) {
  return this.newCheckoutFlow();
}
return this.legacyCheckoutFlow();
```

#### Route-level enforcement via Guard (optional)

1. Create `@Feature('new_checkout')` metadata decorator.
2. Guard reads metadata with `Reflector`.
3. Guard calls `FeatureFlagService.isEnabled(...)`.
4. Deny or reroute behavior if disabled.

#### Production-ready practices

1. Support rollout strategies:
   1. Global on/off
   2. Percentage rollout
   3. User/tenant allowlists
   4. Time-window activation

2. Add local cache with TTL for external flag providers.
3. Keep default values explicit (fail-closed vs fail-open per flag).
4. Log/evidence flag decisions for debugging.
5. Remove stale flags quickly to avoid long-term complexity.

#### Build vs buy

1. Build in-app for simple needs and low operational overhead.
2. Use managed providers (LaunchDarkly, Unleash, ConfigCat, etc.) for advanced
   targeting, analytics, and governance.

#### Rule of thumb

Treat flags as short-lived release controls, not permanent business logic
branches. Create ownership and sunset dates for every flag.

</details>

<details>
<summary>42. How do you integrate databases? (TypeORM, Prisma, Drizzle, Mongoose)</summary>

#### NestJS

In NestJS, database integration should be done through dedicated infrastructure
modules/providers, not directly inside controllers. Choice depends on data model,
team preferences, and query complexity.

#### Common options

1. **TypeORM**
   Full-featured ORM with decorators, repositories, migrations, and strong Nest
   module integration.

2. **Prisma**
   Schema-first ORM/client with excellent DX, typed queries, and predictable
   migrations.

3. **Drizzle**
   Lightweight typed SQL toolkit/ORM with explicit SQL-oriented approach.

4. **Mongoose**
   ODM for MongoDB with schema modeling and document-oriented workflows.

#### Integration patterns by tool

1. **TypeORM**
   Use `TypeOrmModule.forRoot(...)` in root module, `forFeature([Entity])` in
   feature modules, inject repositories via `@InjectRepository`.

2. **Prisma**
   Create `PrismaService` (extends `PrismaClient`) and provide it in a module.
   Inject service into repositories/application services.

3. **Drizzle**
   Build a DB provider (`drizzle(...)`) using connection pool (`pg`, `mysql2`).
   Inject typed DB instance via custom token.

4. **Mongoose**
   Use `MongooseModule.forRoot(...)` + `forFeature([{ name, schema }])`, inject
   model via `@InjectModel`.

#### Minimal examples

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

#### Decision guide

1. Choose **TypeORM** if you want classic Nest-style decorators/repositories.
2. Choose **Prisma** for strong typed client and modern migration workflow.
3. Choose **Drizzle** if you prefer SQL-first explicitness with type safety.
4. Choose **Mongoose** when MongoDB document model is the natural fit.

#### Production best practices (regardless of tool)

1. Keep DB access in repositories/adapters, not controllers.
2. Use migrations; avoid schema auto-sync in production.
3. Configure connection pooling and timeouts.
4. Add health checks and startup fail-fast behavior.
5. Instrument query latency and error rates.
6. Encapsulate transactions in application-service boundaries.

</details>

<details>
<summary>43. What is the difference between TypeOrmModule.forRoot() and forFeature()?</summary>

#### NestJS

`TypeOrmModule.forRoot()` and `TypeOrmModule.forFeature()` serve different
scopes in NestJS TypeORM integration.

#### `forRoot()` — application-level database connection setup

Use in root module (usually `AppModule`) to configure the DataSource/connection.

It defines:
1. DB driver/type (`postgres`, `mysql`, etc.)
2. Connection credentials/URL
3. Global TypeORM options (entities loading, logging, migrations, `synchronize`)

Example:

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  url: process.env.DATABASE_URL,
  autoLoadEntities: true,
  synchronize: false,
});
```

#### `forFeature()` — feature-module repository registration

Use inside domain/feature modules to register specific entities and make their
repositories injectable in that module context.

Example:

```ts
@Module({
  imports: [TypeOrmModule.forFeature([UserEntity])],
  providers: [UsersService],
})
export class UsersModule {}
```

Inject repository:

```ts
constructor(
  @InjectRepository(UserEntity)
  private readonly usersRepo: Repository<UserEntity>,
) {}
```

#### Practical difference summary

1. `forRoot()`:
   1. Creates/configures DB connection once (or named connections).
   2. Global infrastructure concern.

2. `forFeature()`:
   1. Exposes repositories for selected entities in module scope.
   2. Feature/business concern.

#### Common mistake

Using `forFeature()` without `forRoot()` (or without an initialized DataSource)
leads to DI/runtime errors because repositories have no active connection backing
them.

#### Rule of thumb

1. Configure connection once with `forRoot` in app bootstrap path.
2. Register per-module entities with `forFeature` where repositories are needed.
3. Keep `synchronize: false` in production and use migrations.

</details>

<details>
<summary>44. What is the Repository pattern in NestJS + TypeORM?</summary>

#### NestJS

The Repository pattern abstracts data access behind a dedicated interface/service
so business logic does not depend directly on ORM details.

In NestJS + TypeORM, this usually means wrapping `Repository<Entity>` with your
own domain-oriented repository contract and implementation.

#### Why use Repository pattern

1. Decouples application/domain logic from TypeORM API.
2. Improves testability (easy mocking of repository interfaces).
3. Centralizes query logic and mapping.
4. Makes ORM replacement/refactor less painful.

#### Typical structure

1. **Domain contract (port)**
   `UsersRepository` interface with business-oriented methods.

2. **Infrastructure implementation**
   `TypeOrmUsersRepository` that uses `Repository<UserEntity>`.

3. **Service/application layer**
   Depends on interface token, not concrete TypeORM class.

#### Example

Repository contract:

```ts
export interface UsersRepository {
  findByEmail(email: string): Promise<UserEntity | null>;
  save(user: UserEntity): Promise<UserEntity>;
}
```

TypeORM implementation:

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

Provider binding:

```ts
{
  provide: 'USERS_REPOSITORY',
  useClass: TypeOrmUsersRepository,
}
```

Service depends on abstraction:

```ts
constructor(
  @Inject('USERS_REPOSITORY')
  private readonly usersRepo: UsersRepository,
) {}
```

#### What belongs in repository vs service

1. Repository:
   persistence queries, aggregate loading/saving, DB-specific filtering.

2. Service/use-case:
   orchestration, business rules, transactions boundary coordination.

#### Common anti-pattern

Injecting TypeORM repositories directly into many services/controllers and
duplicating query fragments everywhere. This increases coupling and inconsistency.

#### Practical takeaway

Use TypeORM’s repository under the hood, but expose your own domain-level
repository interface to keep architecture modular and test-friendly.

</details>

<details>
<summary>45. What is the difference between Repository pattern and Active Record — and when should you choose each?</summary>

#### NestJS

Repository pattern and Active Record are two different ways to organize
persistence logic.

#### Core difference

1. **Repository pattern**
   Domain/business layer works with repository abstractions; persistence logic is
   separated into repository classes.

2. **Active Record**
   Entity/model objects contain persistence methods themselves (`save`, `remove`,
   static finders), mixing data + persistence behavior.

#### Repository pattern characteristics

1. Better separation of concerns.
2. Easier unit testing via interface mocks.
3. Scales better in complex domains/microservices.
4. Encourages domain-centric design and clean boundaries.

#### Active Record characteristics

1. Faster to start for small/simple apps.
2. Less boilerplate for straightforward CRUD.
3. Can become tightly coupled to ORM over time.
4. Harder to keep business logic isolated as complexity grows.

#### When to choose each

1. Choose **Repository pattern** when:
   1. Project is medium/large or expected to grow.
   2. Team needs strict architecture/testability.
   3. Domain logic is non-trivial.
   4. Future ORM replacement is possible concern.

2. Choose **Active Record** when:
   1. App is small, CRUD-heavy, and low-complexity.
   2. Speed of initial development is priority.
   3. Team accepts tighter ORM coupling tradeoff.

#### In NestJS practice

1. NestJS architecture (modules/providers/DI) naturally aligns with repository
   pattern.
2. Even with TypeORM, many production teams prefer Data Mapper/repository style
   over Active Record to keep services clean.

#### Quick comparison table

1. **Coupling**
   Repository: lower
   Active Record: higher

2. **Testability**
   Repository: high
   Active Record: moderate/low (more DB-coupled)

3. **Boilerplate**
   Repository: more
   Active Record: less

4. **Long-term maintainability**
   Repository: better for complex systems
   Active Record: okay for simple apps

#### Practical recommendation

For interview-quality and production-grade NestJS architecture, default to
Repository pattern. Use Active Record only when the domain is intentionally simple
and lifecycle cost is low.

</details>

<details>
<summary>46. What are migrations in TypeORM/Prisma and why is synchronize: true dangerous in production?</summary>

#### NestJS

Migrations are versioned, explicit database schema change scripts. They let teams
evolve schema safely and predictably across environments.

In TypeORM/Prisma, migrations are the production-safe way to apply schema changes.

#### What migrations are

1. **Ordered schema history**
   Each migration is a tracked step (up/down) in schema evolution.

2. **Reproducible deployments**
   Same schema changes run in dev/staging/prod consistently.

3. **Reviewable change set**
   SQL/DDL intent is visible in code review and CI.

4. **Rollback strategy**
   You can revert problematic changes (with constraints).

#### TypeORM vs Prisma migration model

1. **TypeORM**
   Migrations are TS/JS files (or SQL) generated/written and executed via CLI.

2. **Prisma**
   Schema changes are defined in `schema.prisma`; migration files are generated
   and applied with Prisma Migrate.

Both approaches create auditable migration artifacts.

#### Why `synchronize: true` is dangerous in production

1. **Implicit destructive changes**
   ORM may alter/drop columns/indexes automatically without controlled review.

2. **Non-deterministic behavior**
   Schema diff behavior can vary with entity drift and runtime state.

3. **No proper migration history**
   Hard to audit what changed and when.

4. **Risky startup coupling**
   App boot can mutate production schema unexpectedly.

5. **Poor multi-instance safety**
   Concurrent app startups can race on schema updates.

#### Production-safe workflow

1. Set `synchronize: false` in production.
2. Generate migration for every schema change.
3. Review migration SQL in PR.
4. Run migrations in deployment pipeline before/with app rollout.
5. Monitor migration execution and fail deployment on migration errors.

#### Practical examples

TypeORM production config:

```ts
TypeOrmModule.forRoot({
  // ...
  synchronize: false,
  migrationsRun: false,
});
```

Prisma deployment approach:
1. Commit migration files.
2. Run `prisma migrate deploy` during release.

#### Rule of thumb

Use `synchronize: true` only for quick local prototyping. For any serious
environment, migrations are mandatory for safety, traceability, and controlled
schema evolution.

</details>

<details>
<summary>47. How do you implement soft delete in TypeORM?</summary>

#### NestJS

Soft delete means records are marked as deleted instead of being physically
removed from the database. In TypeORM, this is typically done with a
`@DeleteDateColumn`.

#### Why use soft delete

1. Recover accidentally deleted data.
2. Keep audit/history context.
3. Preserve foreign key relations and business traceability.
4. Support "trash/restore" workflows.

#### Step 1: Add delete timestamp column

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

#### Step 2: Use soft-delete repository methods

```ts
// mark as deleted (sets deletedAt)
await this.usersRepo.softDelete(userId);

// restore soft-deleted row
await this.usersRepo.restore(userId);
```

You can also use:
1. `softRemove(entity)` for entity instance deletion.
2. `recover(entity)` for instance restore.

#### Query behavior

1. By default, TypeORM excludes soft-deleted rows in standard `find*` queries.
2. To include deleted rows, use `withDeleted: true`.

```ts
const allRows = await this.usersRepo.find({ withDeleted: true });
```

Only deleted rows:

```ts
const deletedOnly = await this.usersRepo.find({
  withDeleted: true,
  where: { deletedAt: Not(IsNull()) },
});
```

#### Service-level example

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

#### Production considerations

1. Add indexes for frequently filtered fields (`deleted_at`, tenant keys).
2. Ensure unique constraints account for soft-deleted rows (partial unique indexes
   where supported).
3. Define retention policy for eventual hard cleanup.
4. Include delete/restore events in audit logs.

#### Rule of thumb

Use soft delete for user/business data that may require recovery or audit. Use
hard delete only when compliance/storage policies or domain rules require
permanent removal.

</details>

<details>
<summary>48. How do you implement transactions in TypeORM with NestJS?</summary>

#### NestJS

Transactions ensure a group of database operations either all succeed or all
rollback together. In NestJS + TypeORM, use transactions for multi-step writes
that must stay consistent.

#### When transactions are required

1. Creating/updating multiple related tables in one use case.
2. Balance/money/inventory changes.
3. Operations where partial success would corrupt business state.

#### Main approaches in TypeORM

1. **`DataSource.transaction(...)`** (recommended default)
2. **`QueryRunner`** (manual control for advanced flows)

#### Approach 1: `DataSource.transaction` (clean and safe)

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

Important: inside transaction callback, use `manager` repositories/entities, not
global injected repositories.

#### Approach 2: `QueryRunner` (fine-grained control)

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

1. Keep transaction scope short and focused.
2. Avoid external HTTP calls inside DB transaction.
3. Use proper isolation level when needed for concurrency-sensitive flows.
4. Handle deadlock/retry strategy for high-contention operations.
5. Emit domain events after successful commit (or use outbox pattern).

#### Common mistakes

1. Mixing transactional and non-transactional repositories in same flow.
2. Long-running transactions causing lock contention.
3. Swallowing errors and committing inconsistent state.

#### Practical rule

Wrap one business use case in one transaction boundary when consistency between
multiple writes is non-negotiable.

</details>

<details>
<summary>49. What is the N+1 problem and how do you solve it in NestJS?</summary>

#### NestJS

The N+1 problem occurs when your app runs:
1. one query to load a list of parent records,
2. then one extra query per parent to load related data.

This causes `1 + N` queries, high latency, and unnecessary DB load.

#### Example of N+1

1. Query users (`N` users returned).
2. For each user, query posts separately.
3. Total queries: `1 + N`.

With 100 users, that becomes 101 DB round-trips.

#### Where it appears in NestJS apps

1. TypeORM lazy relation access in loops.
2. GraphQL resolvers resolving nested fields per entity.
3. Service methods doing repeated per-item repository calls.

#### How to solve it

1. **Eager load with joins**
   Use query builder joins to fetch relations in one query (or controlled few).

2. **Batch loading**
   Use DataLoader-style batching (especially in GraphQL).

3. **IN queries**
   Fetch related rows for all parent IDs at once and map in memory.

4. **Projection optimization**
   Select only needed columns to reduce payload.

#### TypeORM join example

```ts
const users = await this.usersRepo
  .createQueryBuilder('u')
  .leftJoinAndSelect('u.posts', 'p')
  .getMany();
```

#### Batch loading pattern example

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

#### Detection signals

1. Sudden query count growth with larger result sets.
2. Endpoint latency scaling linearly with number of parent rows.
3. Repeated similar SQL statements in logs/monitoring.

#### Practical prevention strategy

1. Enable SQL/query logging in non-prod performance testing.
2. Add query-count assertions for critical endpoints.
3. Prefer repository methods designed around aggregate reads.
4. Review GraphQL resolvers for per-field DB calls.

#### Rule of thumb

If an endpoint loads collections with relations, design data access upfront for
batching/joins. Never rely on per-item lazy fetch loops in production paths.

</details>

<details>
<summary>50. What is connection pooling and how do you configure it properly for a database?</summary>

#### NestJS

Connection pooling is a managed set of reusable database connections shared by
requests. Instead of opening a new DB connection for every query, the app borrows
one from the pool and returns it after use.

#### Why pooling matters

1. Reduces connection setup overhead.
2. Improves throughput/latency under load.
3. Prevents DB overload from uncontrolled connection spikes.
4. Stabilizes behavior across concurrent requests.

#### Key pool parameters

1. **max pool size**
   Maximum simultaneous DB connections from one app instance.

2. **min pool size** (driver-specific)
   Minimum idle connections kept open.

3. **acquire timeout**
   How long to wait for a free connection.

4. **idle timeout**
   How long unused connections are kept before closing.

5. **max lifetime**
   Maximum age of a connection before recycle.

#### Sizing strategy (practical)

1. Start from DB limit and number of app replicas:
   `pool_max_per_instance * replica_count < db_connection_limit - safety_margin`.

2. Keep headroom for:
   1. Migrations/admin tools
   2. Background workers
   3. Unexpected traffic bursts

3. Load test and tune based on:
   1. wait time for connection acquisition
   2. DB CPU
   3. lock contention
   4. p95/p99 latency

#### TypeORM/NestJS example (Postgres)

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

1. Use one global DataSource per app process (avoid creating many pools).
2. Set query timeouts and statement timeouts.
3. Monitor pool metrics: active, idle, waiting.
4. Tune with real workload, not defaults.
5. If serverless/highly elastic, consider PgBouncer or provider-managed pooling.

#### Common mistakes

1. Pool too large -> DB thrashing/lock pressure.
2. Pool too small -> request queuing/timeouts.
3. Ignoring horizontal scaling multiplier across replicas.
4. Opening new clients manually in request handlers.

#### Rule of thumb

Connection pool size is a system-level capacity decision, not just ORM config.
Tune it with production-like load and database limits in mind.

</details>

<details>
<summary>51. How do you protect against SQL injection in TypeORM/Prisma?</summary>

#### NestJS

SQL injection protection in NestJS with TypeORM/Prisma relies on one principle:
**never build SQL by string concatenation with untrusted input**.

Use parameterized queries and ORM query APIs that bind values safely.

#### Safe defaults

1. **TypeORM repository/query builder with parameters**
2. **Prisma client methods with typed filters**
3. **DTO validation + parsing before data reaches persistence layer**

#### TypeORM safe patterns

Repository API:

```ts
await usersRepo.findOne({ where: { email: input.email } });
```

QueryBuilder with bound params:

```ts
await usersRepo
  .createQueryBuilder('u')
  .where('u.email = :email', { email: input.email })
  .andWhere('u.status = :status', { status: 'active' })
  .getMany();
```

#### Prisma safe patterns

```ts
await prisma.user.findMany({
  where: {
    email: input.email,
    status: 'active',
  },
});
```

Prisma generates parameterized queries under the hood for standard client methods.

#### Dangerous anti-patterns

1. Raw SQL with string interpolation:

```ts
// BAD
await dataSource.query(`SELECT * FROM users WHERE email = '${input.email}'`);
```

2. Unsafe dynamic ORDER BY / column names from user input.
3. Passing unvalidated fragments into raw query functions.

#### If raw SQL is unavoidable

1. Use parameter placeholders:

```ts
await dataSource.query('SELECT * FROM users WHERE email = $1', [input.email]);
```

2. Whitelist dynamic identifiers (column/order fields) explicitly:
   map input -> known safe SQL token.

#### Defense in depth

1. Validate and sanitize input via DTO + `ValidationPipe`.
2. Use least-privilege DB accounts.
3. Disable dangerous DB permissions (drop/alter where not needed).
4. Log suspicious query patterns and failed auth attempts.
5. Add security tests for injection payloads on critical endpoints.

#### Practical rule

Stay on ORM APIs for 95% of queries. For the remaining raw SQL cases, always bind
parameters and whitelist any dynamic SQL structure.

</details>

<details>
<summary>52. How do you properly organize pagination in a REST API? (offset vs cursor-based)</summary>

#### NestJS

Proper pagination design in REST API should be stable, performant, and predictable
for clients. The two main models are offset-based and cursor-based pagination.

#### Offset vs cursor: core difference

1. **Offset pagination**
   Uses `limit` + `offset` (or page/pageSize).
   Example: `GET /users?limit=20&offset=40`.

2. **Cursor pagination**
   Uses a pointer to the last seen record in a sorted stream.
   Example: `GET /users?limit=20&cursor=eyJpZCI6MTIzfQ==`.

#### When to use offset pagination

1. Small/medium datasets.
2. Need random page jumps (`page=7`).
3. Simpler admin dashboards/backoffice tools.

Tradeoffs:
1. Slower on large offsets.
2. Inconsistent pages under concurrent inserts/deletes.

#### When to use cursor pagination

1. Large, frequently changing datasets.
2. Infinite scroll/mobile feeds.
3. Performance-sensitive APIs.

Benefits:
1. Better DB performance at scale.
2. More stable ordering under concurrent writes.

Tradeoff:
1. No natural random page jump.

#### Essential design rules (both models)

1. Always define deterministic sort order:
   e.g. `ORDER BY created_at DESC, id DESC`.

2. Enforce max page size server-side.

3. Return pagination metadata:
   `hasNext`, `nextCursor` (cursor model) or `total` (offset model when needed).

4. Validate pagination params via DTO + pipes.

#### Response shape examples

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

#### NestJS implementation notes

1. Create dedicated DTOs: `OffsetPaginationDto`, `CursorPaginationDto`.
2. Keep pagination logic in repository/query layer, not controller.
3. Encode cursor as opaque token (base64/json + optional signature).
4. Ensure DB indexes match sort/filter keys (`created_at`, `id`, tenant fields).

#### Practical recommendation

1. Use **offset** for simple internal endpoints.
2. Use **cursor** for public/high-volume feeds.
3. If uncertain, start with cursor for write-heavy timelines to avoid future
   performance and consistency issues.

</details>

<details>
<summary>53. How do you version an API in NestJS? (URI, Header, Media type versioning)</summary>

#### NestJS

API versioning in NestJS lets you evolve endpoints without breaking existing
clients. Nest supports URI, custom header, and media type versioning strategies.

#### Versioning strategies

1. **URI versioning**
   Version in path: `/v1/users`, `/v2/users`.

2. **Header versioning**
   Version in custom header (e.g., `X-API-Version: 2`).

3. **Media type versioning**
   Version in `Accept` header media type
   (e.g., `application/vnd.myapp.v2+json`).

#### Enabling versioning in NestJS

```ts
import { NestFactory, VersioningType } from '@nestjs/core';

const app = await NestFactory.create(AppModule);

app.enableVersioning({
  type: VersioningType.URI, // or HEADER / MEDIA_TYPE
  defaultVersion: '1',
});
```

#### Declaring versions on controllers/routes

Controller-level:

```ts
@Controller({ path: 'users', version: '1' })
export class UsersV1Controller {}
```

Route-level:

```ts
@Get()
@Version('2')
findAllV2() {}
```

Multiple versions on one handler:

```ts
@Version(['1', '2'])
```

#### Choosing the strategy

1. **URI versioning** (most common)
   1. Easy to debug and cache.
   2. Clear in logs and docs.
   3. Best default for public REST APIs.

2. **Header versioning**
   1. Keeps URLs clean.
   2. Useful in controlled enterprise clients.
   3. Harder to test manually and cache by default.

3. **Media type versioning**
   1. Standards-oriented content negotiation style.
   2. Most complex for clients/tooling.

#### Practical best practices

1. Introduce versioning before first breaking change.
2. Keep backward compatibility window and deprecation policy.
3. Version only when contract changes are breaking.
4. Document sunset timelines for old versions.
5. Keep shared business logic in services; version primarily transport layer.

#### Rule of thumb

For most teams, start with **URI versioning** because it is explicit and
operationally simple. Use header/media type versioning only with clear platform
requirements.

</details>

<details>
<summary>54. How do you implement Swagger documentation in NestJS via @nestjs/swagger?</summary>

#### NestJS

Swagger in NestJS is implemented with `@nestjs/swagger` to auto-generate OpenAPI
documentation from controllers, DTOs, and decorators.

#### Step 1: install packages

1. `@nestjs/swagger`
2. `swagger-ui-express`

#### Step 2: configure Swagger in `main.ts`

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

Docs URL will be `/docs`.

#### Step 3: annotate controllers and DTOs

Controller annotations:

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

DTO annotations:

```ts
import { ApiProperty } from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({ example: 'john@example.com' })
  email: string;

  @ApiProperty({ minLength: 8 })
  password: string;
}
```

#### Step 4: keep schemas accurate

1. Use class-based DTOs (not interfaces) for runtime metadata.
2. Combine with `ValidationPipe` so docs match real constraints.
3. Document auth, pagination, and error models explicitly.

#### Advanced production practices

1. Generate docs per API version if versioning is enabled.
2. Hide internal/admin endpoints when needed.
3. Use `operationIdFactory` for stable SDK generation.
4. Export OpenAPI JSON in CI for contract checks/client codegen.
5. Protect docs endpoint in production if API is private.

#### Practical takeaway

Treat Swagger as a contract artifact, not just UI. Keep decorators and DTOs
updated alongside endpoint changes to prevent doc drift.

</details>

<details>
<summary>55. How do you implement CORS in NestJS and when are custom settings needed?</summary>

#### NestJS

CORS (Cross-Origin Resource Sharing) controls which browser origins can access
your API. In NestJS, it is configured at application bootstrap level.

#### Basic CORS enablement

```ts
const app = await NestFactory.create(AppModule);
app.enableCors();
```

This is fine for local development, but too permissive for production.

#### Production-style CORS configuration

```ts
app.enableCors({
  origin: ['https://app.example.com', 'https://admin.example.com'],
  methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE', 'OPTIONS'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true,
  maxAge: 86400,
});
```

#### When custom CORS settings are needed

1. **Multiple frontend domains**
   You need explicit allowlist by environment.

2. **Cookie-based auth (`credentials: true`)**
   Requires specific origin (not `*`) and secure cookie policy.

3. **Custom headers/tokens**
   Add required headers to `allowedHeaders`.

4. **Complex methods/preflight**
   Configure `methods` and ensure `OPTIONS` works properly.

5. **Per-tenant or dynamic origin rules**
   Use function-based origin resolver.

#### Dynamic origin example

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

#### Common mistakes

1. Using `origin: '*'` with `credentials: true` (invalid/insecure for cookies).
2. Forgetting preflight (`OPTIONS`) handling in proxies/gateways.
3. Hardcoding one origin for all environments.
4. Treating CORS as security boundary for non-browser clients.

#### Practical recommendations

1. Keep strict origin allowlist in production.
2. Separate CORS config per environment via `ConfigService`.
3. Log blocked origins for debugging.
4. Combine CORS with real auth/authz, rate limiting, and CSRF strategy where
   relevant.

</details>

<details>
<summary>56. What is idempotency in the context of REST API and how do you ensure it?</summary>

#### NestJS

Idempotency means that repeating the same request multiple times produces the
same final system state as executing it once.

In REST APIs this is critical for reliability under retries, network timeouts,
and client-side duplicate submissions.

#### HTTP semantics and idempotency

1. **Usually idempotent by design**
   `GET`, `PUT`, `DELETE`, `HEAD`, `OPTIONS`.

2. **Not idempotent by default**
   `POST` (commonly creates new resources each call).

#### Why idempotency is important

1. Safe client retries after timeout.
2. Protection from duplicate actions (double charge/order).
3. Better resilience in distributed systems and at-least-once delivery flows.

#### How to ensure idempotency in practice

1. **Idempotency key pattern (for POST)**
   Client sends unique key (e.g., `Idempotency-Key` header).
   Server stores key + request fingerprint + response.
   Repeated same key returns original result instead of re-executing action.

2. **Database constraints**
   Enforce uniqueness on business identifiers
   (`externalPaymentId`, `orderReference`, etc.).

3. **Upsert/compare-and-set patterns**
   Use deterministic write operations when possible.

4. **Transactional processing**
   Protect multi-step writes from partial duplication.

#### NestJS implementation sketch

1. Interceptor/guard checks `Idempotency-Key`.
2. Compute fingerprint (route + user + payload hash).
3. Lookup idempotency record:
   1. If completed -> return stored response.
   2. If in-progress -> return conflict/retry-later policy.
   3. If absent -> reserve key and execute handler.
4. Store final response atomically and return.

#### Minimal conceptual flow

```text
Request -> Idempotency middleware/interceptor
        -> key exists with completed response? return cached response
        -> else execute use case
        -> persist outcome by key
        -> return response
```

#### Common pitfalls

1. Reusing key for different payload (must detect and reject).
2. Storing keys without TTL/cleanup.
3. Not scoping key by tenant/user where needed.
4. Returning different response on retry for same key.

#### Practical recommendation

For all money/order/subscription endpoints, enforce idempotency keys + unique DB
constraints. This gives both application-level and persistence-level protection
against duplicates.

</details>

<details>
<summary>57. How do you implement rate limiting in NestJS? (@nestjs/throttler)</summary>

#### NestJS

Rate limiting controls how many requests a client can make in a time window. In
NestJS, the standard solution is `@nestjs/throttler`.

#### Why rate limiting is needed

1. Protects API from abuse and brute-force attempts.
2. Reduces accidental overload from noisy clients.
3. Improves fairness across users/tenants.
4. Adds resilience before traffic reaches expensive dependencies.

#### Step 1: install and configure module

```ts
import { Module } from '@nestjs/common';
import { ThrottlerModule } from '@nestjs/throttler';

@Module({
  imports: [
    ThrottlerModule.forRoot([
      {
        ttl: 60_000, // 60 seconds
        limit: 100,  // 100 requests per window
      },
    ]),
  ],
})
export class AppModule {}
```

#### Step 2: apply global guard

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

Now all routes are rate limited by default.

#### Step 3: customize per route/controller

Tighter limit:

```ts
@Throttle({ default: { limit: 5, ttl: 60_000 } })
@Post('login')
login() {}
```

Skip limit for health endpoint:

```ts
@SkipThrottle()
@Get('health')
health() {}
```

#### Keying strategy (who is limited)

Default is usually client IP. In real systems you may need:
1. user ID based limit (after auth),
2. tenant/API key based limit,
3. route-group specific policies.

You can extend guard/tracker logic for custom keys.

#### Distributed deployment note

In multi-instance environments, in-memory storage is not enough for strict global
limits. Use shared storage adapter (e.g., Redis-backed throttling store) to keep
limits consistent across replicas.

#### Practical best practices

1. Use stricter limits on auth/reset/token endpoints.
2. Return clear `429 Too Many Requests` responses.
3. Expose retry metadata (`Retry-After`) where possible.
4. Monitor throttle hits per route/client to tune limits.
5. Combine with WAF/reverse proxy rate limiting for layered defense.

</details>

<details>
<summary>58. How do you implement request tracing (adding requestId to each request)?</summary>

#### NestJS

Request tracing means attaching a unique `requestId` to each incoming request and
propagating it through logs, responses, and downstream calls.

This is essential for debugging distributed systems and correlating events across
services.

#### Goals of request tracing

1. Correlate all logs for one request.
2. Track failures across middleware/guards/services/DB/external APIs.
3. Return request identifier to clients/support teams.

#### Common implementation pattern

1. Middleware reads existing header (`x-request-id`) or generates new UUID.
2. Store ID on request object.
3. Add ID to response headers.
4. Logger includes `requestId` automatically in every log entry.

#### Middleware example

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

Apply middleware globally in `AppModule.configure(...)`.

#### Logging integration

1. Include `requestId` in structured logs from interceptors/services.
2. Prefer centralized logger abstraction so every log line carries correlation
   fields.

Interceptor example (timing + requestId):

```ts
const req = context.switchToHttp().getRequest();
const requestId = req.requestId;
this.logger.log({ msg: 'request.start', requestId, path: req.url });
```

#### Async context propagation (advanced)

For deep service layers/background async chains, use `AsyncLocalStorage` (or CLS
module) to access `requestId` without passing it manually through every method.

#### Downstream propagation

1. Forward `x-request-id` in outbound HTTP calls.
2. Include request ID in message metadata for queues/events.
3. Map to trace/span IDs if using OpenTelemetry.

#### Best practices

1. Accept upstream request ID from trusted gateways.
2. Generate ID server-side when missing.
3. Return ID in every error response for support diagnostics.
4. Keep header naming consistent across all services.
5. Treat requestId as correlation metadata, not as security token.

</details>

<details>
<summary>59. How do you handle multipart/form-data and file uploads in NestJS?</summary>

#### NestJS

In NestJS (Express platform), file uploads are typically handled with Multer via
`@nestjs/platform-express` interceptors.

`multipart/form-data` is used when requests include files (and optional fields).

#### Core building blocks

1. `FileInterceptor()` for single file.
2. `FilesInterceptor()` for multiple files (same field).
3. `FileFieldsInterceptor()` for multiple named file fields.
4. `@UploadedFile()` / `@UploadedFiles()` to access parsed files.

#### Single file upload example

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

#### Handling multiple files

1. Same field:
   `@UseInterceptors(FilesInterceptor('files', 10))`

2. Named fields:
   `@UseInterceptors(FileFieldsInterceptor([{ name: 'avatar', maxCount: 1 }, ...]))`

#### Validation and security requirements

1. Enforce max size limits.
2. Validate MIME type and (ideally) actual file signature.
3. Sanitize file names and avoid trusting client-provided names.
4. Store outside executable/static sensitive paths.
5. Run malware scanning for high-risk domains.

#### Storage strategies

1. Local disk (simple dev/small deployments).
2. Object storage (S3/GCS/MinIO) for scalable production.
3. DB storage only for special cases (usually not ideal for large binaries).

#### Production best practices

1. Prefer direct-to-object-storage uploads for large files.
2. Keep metadata in DB (owner, key, mime, size, checksum).
3. Use signed URLs for download/upload access control.
4. Apply auth + rate limits to upload endpoints.
5. Add retention/cleanup policies.

</details>

<details>
<summary>60. How do you implement compression (gzip/brotli) in NestJS?</summary>

#### NestJS

Compression reduces response payload size and improves network performance,
especially for JSON/text-heavy APIs.

In NestJS (Express adapter), gzip/brotli is typically enabled via compression
middleware.

#### Basic setup (Express)

1. Install `compression`.
2. Register middleware in `main.ts`.

```ts
import { NestFactory } from '@nestjs/core';
import compression from 'compression';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    compression({
      threshold: 1024, // compress responses > 1KB
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

The client’s `Accept-Encoding` header determines algorithm negotiation
(`br`, `gzip`, etc., depending on runtime/proxy support).

#### Where brotli usually happens

1. Application layer (Node middleware/runtime support).
2. Reverse proxy/CDN (Nginx, Cloudflare, Vercel, etc.).

In many production setups, proxy/CDN handles compression more efficiently than
application process.

#### What to compress

1. JSON responses
2. Text/HTML/CSS/JS
3. GraphQL responses

#### What not to compress

1. Already-compressed assets (`.zip`, `.jpg`, `.png`, `.mp4`, `.pdf`)
2. Very small payloads (compression overhead may outweigh benefits)

#### Operational best practices

1. Use threshold to skip tiny responses.
2. Ensure cache/proxy respects `Vary: Accept-Encoding`.
3. Measure CPU overhead vs bandwidth savings.
4. Prefer proxy/CDN compression for high-traffic workloads.
5. Keep TLS + compression risks in mind for sensitive contexts (rare modern risk,
   but follow platform guidance).

#### Fastify note

If using Fastify adapter, use corresponding Fastify compression plugin instead of
Express middleware.

#### Practical recommendation

Enable compression by default for API responses, then tune threshold and placement
(app vs edge/proxy) based on real traffic and CPU profile.

</details>

<details>
<summary>61. How do you implement helmet and which HTTP headers does it set?</summary>

#### NestJS

Helmet is a security middleware that sets protective HTTP headers to reduce common
web attack surface (XSS, clickjacking, MIME sniffing, data leakage via referrer,
etc.).

In NestJS (Express adapter), integrate it globally in `main.ts`.

#### Basic setup

1. Install `helmet`.
2. Register as middleware.

```ts
import { NestFactory } from '@nestjs/core';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    helmet({
      // Configure CSP/HSTS/etc. per environment needs
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

#### Common headers Helmet sets (version/config dependent)

1. `Content-Security-Policy` (CSP)
2. `Cross-Origin-Opener-Policy`
3. `Cross-Origin-Resource-Policy`
4. `Origin-Agent-Cluster`
5. `Referrer-Policy`
6. `Strict-Transport-Security` (HSTS, when HTTPS context is appropriate)
7. `X-Content-Type-Options: nosniff`
8. `X-DNS-Prefetch-Control`
9. `X-Download-Options` (legacy IE protection)
10. `X-Frame-Options` (clickjacking protection)
11. `X-Permitted-Cross-Domain-Policies`
12. `X-XSS-Protection` behavior handling (legacy; modern browsers rely on CSP)

Exact defaults can vary by Helmet version and runtime environment.

#### Practical configuration notes

1. **CSP tuning is critical**
   Strict CSP improves security but may break scripts/styles if not configured.

2. **HSTS only on HTTPS**
   Enable carefully in production domains; avoid accidental lock-in on local/dev.

3. **CORS + Helmet**
   They solve different concerns; configure both explicitly.

4. **Reverse proxy awareness**
   Ensure trusted proxy/HTTPS termination config is correct for HSTS/security
   behavior.

#### Typical production pattern

1. Enable Helmet globally.
2. Customize CSP directives for frontend/API behavior.
3. Keep separate config profiles for dev vs production.
4. Verify headers via integration tests and security scans.

#### Rule of thumb

Helmet gives strong baseline hardening, but it is not full security. Combine it
with auth, validation, rate limits, secure cookies, and dependency hygiene.

</details>

<details>
<summary>62. What are the main OWASP vulnerabilities and how do you protect against them?</summary>

#### NestJS

OWASP Top risks are common web security failure classes. In NestJS, mitigation is
done through layered controls: validation, auth, secure defaults, monitoring, and
infrastructure hardening.

#### Main OWASP risks and NestJS-focused protections

1. **Broken Access Control**
   1. Use Guards for authz (`RolesGuard`, policy/ABAC guards).
   2. Enforce ownership checks on resource access.
   3. Deny by default; avoid implicit access.

2. **Cryptographic Failures**
   1. Use HTTPS everywhere.
   2. Hash passwords with strong algorithms (argon2/bcrypt with proper cost).
   3. Keep secrets in secret manager, not source code.
   4. Encrypt sensitive data at rest where required.

3. **Injection (SQL/NoSQL/Command)**
   1. Use parameterized ORM queries (TypeORM/Prisma).
   2. Validate/whitelist input via DTO + `ValidationPipe`.
   3. Avoid string-built raw queries and shell commands with user input.

4. **Insecure Design**
   1. Apply threat modeling for critical flows (auth, payments, admin).
   2. Add idempotency, rate limits, and abuse controls by design.
   3. Use least privilege in architecture boundaries.

5. **Security Misconfiguration**
   1. Enable Helmet and strict CORS.
   2. Disable debug defaults in production.
   3. Keep production env separated and locked down.

6. **Vulnerable and Outdated Components**
   1. Regular dependency updates.
   2. SCA scans in CI (`npm audit`, Snyk, Dependabot, etc.).
   3. Remove unused packages.

7. **Identification and Authentication Failures**
   1. Short-lived access tokens + refresh rotation.
   2. MFA for high-risk accounts.
   3. Secure cookie/token handling, lockout/rate-limit login endpoints.

8. **Software and Data Integrity Failures**
   1. Signed artifacts, trusted CI/CD pipeline.
   2. Verify third-party sources and pin versions.
   3. Control config changes and release approvals.

9. **Security Logging and Monitoring Failures**
   1. Structured logs with requestId/userId/action/outcome.
   2. Alerting on auth anomalies and error spikes.
   3. Preserve stack traces in logs, not responses.

10. **Server-Side Request Forgery (SSRF)**
   1. Restrict outbound network destinations.
   2. Validate and allowlist external URLs.
   3. Block internal metadata IP ranges.

#### NestJS baseline checklist

1. Global `ValidationPipe` (`whitelist`, `forbidNonWhitelisted`, `transform`).
2. Global exception filter with safe error responses.
3. Auth + authorization guards on protected routes.
4. Rate limiting (`@nestjs/throttler`) on sensitive endpoints.
5. Helmet + strict CORS config.
6. Secure config with startup validation (Joi/Zod).
7. Dependency/security scans in CI.

#### Practical takeaway

Security is not one package. In NestJS, strong posture comes from consistent
defense-in-depth across code, config, infrastructure, and operations.

</details>

<details>
<summary>63. How do you use HttpModule (axios) in NestJS for external API requests?</summary>

#### NestJS

In NestJS, external HTTP calls are commonly made via `HttpModule` from
`@nestjs/axios`, which wraps Axios and integrates with DI.

#### Why use `HttpModule`

1. DI-friendly shared HTTP client.
2. Centralized config (base URL, timeout, headers).
3. Easy testing/mocking.
4. Built-in RxJS integration (`Observable` responses).

#### Step 1: register `HttpModule`

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

Async config variant:
`HttpModule.registerAsync(...)` with `ConfigService`.

#### Step 2: inject `HttpService` in provider

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

#### Error handling pattern

1. Catch Axios errors and map to domain/app exceptions.
2. Avoid leaking raw upstream errors directly to API clients.

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

1. Set strict timeouts for all outbound calls.
2. Add retries/circuit breaker for unstable dependencies.
3. Propagate request/correlation IDs in headers.
4. Use typed response DTOs/adapters for external contracts.
5. Instrument latency, failures, and upstream status codes.

#### Testing strategy

1. Mock `HttpService` in unit tests.
2. For integration tests, use mock servers (e.g., nock/wiremock).
3. Validate timeout/retry/error mapping paths explicitly.

#### Practical takeaway

Treat external HTTP as unreliable I/O: configure `HttpModule` centrally, wrap it
in dedicated client services, and enforce robust timeout/retry/error policies.

</details>

<details>
<summary>64. How do you add global interceptors to axios in NestJS? (adding headers, logging)</summary>

#### NestJS

In NestJS, Axios interceptors are configured on the `axiosRef` instance exposed by
`HttpService` (`@nestjs/axios`). This lets you apply global behavior for outbound
requests: headers, logging, timing, auth tokens, and error normalization.

#### Why use Axios interceptors

1. Centralize outbound HTTP behavior.
2. Avoid repeating headers/auth logic in every call.
3. Add consistent request/response logging and metrics.
4. Normalize upstream errors in one place.

#### Typical implementation pattern

1. Create a provider/service that receives `HttpService`.
2. In module init lifecycle, register request/response interceptors once.
3. Keep interceptor logic lightweight and deterministic.

#### Example: global outbound headers + logging

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

Register this provider in a module that imports `HttpModule`.

#### Important production notes

1. Ensure interceptors are registered once (avoid duplicates on hot reload/module
   re-init).
2. Propagate correlation/request IDs from inbound request context.
3. Redact secrets (Authorization, API keys) in logs.
4. Keep timeout/retry/circuit-breaker strategy explicit (interceptors are not a
   full resilience layer).

#### Common use cases

1. Injecting auth tokens from `ConfigService` or token providers.
2. Adding tenant/context headers for downstream services.
3. Standardizing error objects before rethrow.
4. Emitting metrics/traces for observability systems.

#### Practical takeaway

Use Axios interceptors as the outbound equivalent of Nest middleware: one place
for cross-cutting HTTP client policy across all external API calls.

</details>

<details>
<summary>65. How do you properly type external API responses in TypeScript?</summary>

#### NestJS

Proper typing of external API responses means treating remote data as **untrusted**
until validated, while still using TypeScript types for developer ergonomics.

#### Key principle

1. Compile-time types (`interface`/`type`) improve DX.
2. Runtime validation (Zod/class-validator/custom guards) ensures safety.
3. Use both, not one without the other.

#### Recommended pattern

1. Define response DTO/type for expected shape.
2. Fetch data via typed HTTP client call.
3. Validate/parse at boundary.
4. Map to internal domain model before business logic.

#### Example with `HttpService` + Zod

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

#### Why not rely on generics alone

```ts
this.http.get<MyType>(...)
```

This only tells TypeScript what you *expect*; it does not verify real runtime
payload from upstream service.

#### Practical typing strategies

1. Use dedicated client modules per upstream API.
2. Keep upstream DTOs separate from internal domain entities.
3. Normalize/transform external enums/field names at boundary.
4. Include nullable/optional handling explicitly (`null` from upstream is common).

#### Error handling best practices

1. Distinguish transport errors (timeout, 5xx) from schema errors.
2. Map both to stable internal exceptions.
3. Log upstream response metadata for diagnostics (without leaking secrets).

#### Rule of thumb

Type external responses twice:
1. static type for code intelligence,
2. runtime schema validation for correctness and security.

</details>

<details>
<summary>66. How do you implement retry logic for external HTTP requests in NestJS?</summary>

#### NestJS

Retry logic helps handle transient failures (timeouts, temporary 5xx, brief
network glitches) when calling external APIs.

In NestJS, retries are commonly implemented with RxJS operators on `HttpService`
or with resilience libraries at client boundary.

#### When retries are appropriate

1. Timeout/network errors.
2. Temporary upstream 5xx.
3. Rate-limit responses when server provides retry hints (`429` with
   `Retry-After`).

#### When retries are dangerous

1. Non-idempotent operations without idempotency keys.
2. Permanent errors (`400`, `401`, `403`, validation failures).
3. Large retry storms during upstream outages.

#### Basic retry with RxJS

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

#### Recommended retry policy

1. Use exponential backoff.
2. Add jitter to avoid synchronized retry spikes.
3. Limit max attempts strictly.
4. Retry only idempotent operations or idempotency-protected writes.

#### Pair retries with safeguards

1. Global timeout per request.
2. Circuit breaker for sustained failures.
3. Rate limiting and bulkheads on outbound clients.
4. Centralized metrics: retry count, final failure rate, latency impact.

#### Practical rule

Retries should improve reliability, not hide outages. Keep them selective,
bounded, and observable.

</details>

<details>
<summary>67. What is the Circuit Breaker pattern and when do you need it?</summary>

#### NestJS

The Circuit Breaker is a resilience pattern that prevents repeated calls to a
failing dependency. Instead of endlessly retrying a broken upstream service, it
"opens the circuit" and fails fast for a period of time.

#### Why circuit breaker is needed

1. Prevents cascading failures across services.
2. Reduces resource exhaustion (threads/connections/event-loop pressure).
3. Improves latency during outages by failing fast.
4. Gives unstable dependency time to recover.

#### Circuit states

1. **Closed**
   Normal operation, requests pass through.

2. **Open**
   Dependency is considered unhealthy; calls are blocked immediately.

3. **Half-open**
   Limited trial requests are allowed to test recovery.
   If successful -> close; if failing -> reopen.

#### When to use it

1. Calling external APIs/payment providers/identity services.
2. Dependency has non-trivial failure rate or latency spikes.
3. Service is high-traffic and retries alone can amplify incidents.
4. Business can tolerate fallback behavior when upstream is down.

#### Typical NestJS integration

1. Wrap external client call in breaker policy.
2. Combine with timeout + retry (bounded) + fallback.
3. Emit metrics/events for breaker state changes.

Conceptual flow:

```text
request -> timeout check -> circuit breaker -> outbound call
        -> success: normal response
        -> failure threshold exceeded: circuit OPEN
        -> OPEN: fail fast / fallback
```

#### Practical implementation options

1. Use resilience libraries (e.g., opossum) around `HttpService` calls.
2. Build custom lightweight breaker for limited use cases.
3. Keep breaker config externalized via `ConfigService`.

#### Key tuning parameters

1. Failure threshold (% or count).
2. Rolling window size.
3. Open-state cooldown duration.
4. Half-open probe count.
5. Timeout per call.

#### Common mistakes

1. Using breaker without observability (no state metrics/logs).
2. Aggressive thresholds causing false opens.
3. Missing fallback strategy for open state.
4. Combining infinite retries with breaker (defeats purpose).

#### Rule of thumb

If an upstream failure can degrade your whole service, add a circuit breaker at
that boundary and monitor its state transitions as first-class SRE signals.

</details>

<details>
<summary>68. How do you implement caching (in-memory, Redis), and when should you use each approach?</summary>

#### NestJS

Caching stores precomputed/frequently requested data to reduce latency and backend
load. In NestJS, common choices are in-memory cache and Redis cache.

#### In-memory vs Redis

1. **In-memory cache**
   Stored inside one app process memory.

2. **Redis cache**
   External shared cache service accessible by all app instances.

#### When to use in-memory cache

1. Single-instance apps or local development.
2. Small, short-lived cached values.
3. Ultra-low-latency local reads.

Limitations:
1. Not shared across replicas.
2. Lost on process restart/deploy.
3. Memory pressure affects app process.

#### When to use Redis cache

1. Multi-instance/distributed deployments.
2. Cross-service shared cache.
3. Need centralized TTL/invalidation behavior.
4. Higher reliability and observability needs.

Tradeoff:
1. Network hop adds small latency.

#### NestJS implementation options

1. `CacheModule` + cache manager adapters.
2. Manual Redis client for advanced patterns.
3. `CacheInterceptor` for response-level caching on selected endpoints.

#### Conceptual `CacheModule` setup

In-memory:

```ts
CacheModule.register({
  ttl: 30_000,
  max: 500,
});
```

Redis (adapter-specific config):

```ts
CacheModule.registerAsync({
  useFactory: () => ({
    store: /* redis store adapter */,
    url: process.env.REDIS_URL,
    ttl: 60_000,
  }),
});
```

#### What to cache

1. Read-heavy, rarely changing reference data.
2. Expensive computed aggregates.
3. External API responses with clear staleness tolerance.

#### What not to cache blindly

1. Highly volatile data without invalidation plan.
2. Security-sensitive per-user data without scoped keys.
3. Write-critical paths where stale reads are unacceptable.

#### Key design practices

1. Use explicit key naming (`user:{id}`, `catalog:v2:{region}`).
2. Set TTL intentionally per data type.
3. Add cache-aside pattern:
   read -> miss -> load source -> set cache -> return.
4. Plan invalidation on writes/events.
5. Monitor hit ratio, evictions, and stale-read impact.

#### Rule of thumb

Start with in-memory only for simple/single-node cases. For production with
multiple instances or shared state needs, move to Redis-backed caching.

</details>

<details>
<summary>69. What is cache invalidation and how do you implement it correctly?</summary>

#### NestJS

Cache invalidation is the process of removing/updating cached data when source
data changes, so clients do not receive stale responses.

It is often the hardest part of caching because correctness depends on data
consistency rules, not just speed.

#### Why invalidation matters

1. Prevents stale or inconsistent user-visible data.
2. Keeps cache aligned with writes.
3. Avoids subtle bugs in business-critical flows.

#### Common invalidation strategies

1. **TTL-based expiration**
   Cached keys expire automatically after fixed time.

2. **Event/write-driven invalidation**
   On successful write, explicitly delete/update related cache keys.

3. **Versioned keys**
   Include version/tag in key so new writes naturally shift reads to new keyspace.

4. **Tag/group invalidation** (if supported by tooling)
   Invalidate multiple related entries by logical group.

#### Practical implementation patterns

1. **Cache-aside with delete-on-write**
   1. Read: cache miss -> DB -> set cache.
   2. Write: update DB -> delete relevant cache keys.

2. **Write-through**
   Update cache and DB in one flow (careful with failure handling).

3. **Event-driven invalidation**
   Publish domain event (`user.updated`) and invalidate in subscribers/workers.

#### Key design rules

1. Use predictable key schema:
   `user:{id}`, `users:list:{filterHash}`, `product:{id}:v{n}`.

2. Keep write-to-key mapping explicit:
   which mutations invalidate which read keys.

3. Prefer short TTL + explicit invalidation for critical hot keys.

4. In multi-instance systems, use shared cache (Redis), not local memory only.

#### Example invalidation flow

```text
PATCH /users/42
 -> update DB
 -> del user:42
 -> del users:list:*
 -> return updated response
```

(List invalidation can be selective if you track filter/index key sets.)

#### Common mistakes

1. Caching list endpoints without invalidating related detail/list keys together.
2. Relying only on long TTL for frequently updated data.
3. Not handling concurrent writes/race conditions.
4. Forgetting tenant/user scoping in keys.

#### Practical recommendation

Start simple:
1. cache-aside,
2. short TTLs,
3. explicit delete-on-write.

Then evolve to event-driven/tag-based invalidation as domain complexity grows.

</details>

<details>
<summary>70. When should you use Observables instead of Promises in NestJS?</summary>

#### NestJS

Use Observables in NestJS when you need **streams, cancellation, composition of
multiple async events, or reactive operators**. Use Promises for simple one-shot
async operations.

#### Core difference

1. **Promise**
   Single eventual value (or error), resolves once.

2. **Observable**
   Lazy stream of 0..N values over time, with rich RxJS operators and
   cancellation.

#### When Observables are a better fit

1. **Streaming use cases**
   Server-Sent Events, websocket-like flows, chunked responses.

2. **Composing multiple async sources**
   Combine timers, HTTP calls, user events, and retries with operators.

3. **Advanced retry/backoff/circuit behavior**
   RxJS operators (`retryWhen`, `timeout`, `catchError`, `switchMap`, etc.).

4. **Cancellation-aware flows**
   Unsubscribe to stop work and release resources.

5. **Nest ecosystem features**
   Interceptors and `HttpService` naturally return Observables.

#### When Promise is preferable

1. One request -> one response DB/API call.
2. Straightforward service method logic with `async/await`.
3. Team not using reactive patterns deeply.

#### Practical NestJS examples

1. `HttpService.get(...)` returns `Observable<AxiosResponse<T>>`.
2. SSE endpoints often return `Observable<MessageEvent>`.
3. Microservice message patterns can leverage reactive streams.

#### Interop pattern

If your app uses `async/await` style but receives Observable:

```ts
const response = await firstValueFrom(this.http.get('/users'));
```

If you need only one value from stream, convert intentionally (`firstValueFrom`
or `lastValueFrom`) and keep boundaries clear.

#### Decision rule of thumb

1. Need one value once -> Promise (`async/await`).
2. Need stream/retry composition/cancellation -> Observable.

Pick one style per module boundary where possible to avoid mixed async complexity.

</details>

<details>
<summary>71. What is the difference between async/await and RxJS for handling asynchronous logic, and when should you use each approach?</summary>

#### NestJS

`async/await` and RxJS solve asynchronous work at different complexity levels.
Neither is universally better; choose based on execution model.

#### Core difference

1. **`async/await` (Promises)**
   Best for single-result async tasks with linear control flow.

2. **RxJS (Observables)**
   Best for event streams, multi-value flows, cancellation, and advanced
   composition over time.

#### `async/await` strengths

1. Very readable imperative code.
2. Easy error handling with `try/catch`.
3. Ideal for request-response service methods (DB/API once).
4. Lower cognitive overhead for most teams.

#### RxJS strengths

1. Composing multiple async streams (`mergeMap`, `switchMap`, `combineLatest`).
2. Powerful retry/backoff/timeout operators.
3. Native cancellation via unsubscribe.
4. Stream processing patterns (SSE, websockets, reactive pipelines).

#### Typical NestJS usage split

1. **Services/controllers**
   Often `async/await` for business use cases.

2. **`HttpService` / interceptors / streaming endpoints**
   Often Observables, optionally converted to Promise when only one value needed.

#### Interoperability

Observable -> Promise:

```ts
const res = await firstValueFrom(this.http.get('/health'));
```

Promise -> Observable:

```ts
from(this.usersService.findById(id))
```

#### When to choose `async/await`

1. CRUD-style endpoints.
2. One-shot DB/API calls.
3. Team values straightforward control flow.

#### When to choose RxJS

1. Continuous streams or real-time pipelines.
2. Complex orchestration of multiple async sources.
3. Need cancellation-aware behavior and operator-based flow control.

#### Common mistakes

1. Using RxJS for trivial one-off operations (overengineering).
2. Forcing Promise style in streaming scenarios (losing reactive benefits).
3. Mixing both styles chaotically inside same module.

#### Practical rule

Default to `async/await` for simple business logic; introduce RxJS where
reactivity/stream composition provides clear operational benefit.

</details>

<details>
<summary>72. How do you avoid blocking the event loop in NestJS and maintain performance?</summary>

#### NestJS

NestJS runs on Node.js event loop. If you block that loop with CPU-heavy or
synchronous operations, all concurrent requests suffer latency spikes.

#### What blocks the event loop

1. Heavy synchronous CPU tasks (hashing large payloads, image/video processing).
2. Big synchronous JSON parsing/stringifying loops.
3. Sync filesystem APIs (`fs.readFileSync`, etc.) on request path.
4. Long tight loops without yielding.
5. Expensive regex/backtracking and inefficient algorithms.

#### Practical strategies to avoid blocking

1. **Prefer async I/O APIs**
   Use non-blocking filesystem/network/DB operations.

2. **Move CPU-heavy work off request thread**
   1. Worker threads (`worker_threads`)
   2. Background jobs/queues (BullMQ, RabbitMQ, etc.)
   3. Dedicated processing services

3. **Use streaming for large payloads**
   Avoid buffering huge files/objects in memory.

4. **Paginate and chunk work**
   Process large datasets in batches instead of one giant synchronous operation.

5. **Cache expensive computations**
   Reuse results where possible.

#### NestJS architecture patterns

1. Keep controllers thin; delegate heavy tasks to async workers.
2. Use queues for email/PDF/report generation/media conversion.
3. Set timeouts and backpressure policies on external calls.
4. Apply rate limiting on expensive endpoints.

#### Monitoring signals of event loop blocking

1. Rising p95/p99 latency with moderate traffic.
2. Low CPU idle yet poor throughput.
3. Delayed timers and slow health checks.
4. Event loop lag metrics increasing.

#### Helpful operational tools

1. Event loop lag monitoring (`perf_hooks`, APM tools).
2. CPU profiling/flamegraphs for hot paths.
3. Endpoint-level latency and payload-size dashboards.

#### Common mistakes

1. Performing synchronous crypto/compression in request handlers.
2. Generating large reports inline during HTTP request.
3. Reading huge files into memory instead of streaming.
4. Ignoring algorithmic complexity in loops over large arrays.

#### Rule of thumb

Request thread should orchestrate, not compute heavily. Keep it non-blocking and
delegate expensive work to async infrastructure.

</details>

<details>
<summary>73. How do you optimize latency (p95 / p99) and what affects these metrics?</summary>

#### NestJS

`p95` and `p99` are tail-latency percentiles: they show how slow the worst 5% and
1% of requests are. Production reliability depends more on these tails than on
average latency.

#### What affects p95/p99 most

1. Database query inefficiency (N+1, missing indexes, lock contention).
2. External dependency slowness (HTTP APIs, queues, auth providers).
3. Event loop blocking (CPU-heavy sync tasks).
4. Connection pool saturation (DB/HTTP).
5. Payload size and serialization overhead.
6. Cache miss rates and cold starts.
7. GC pauses and memory pressure.
8. Retry storms/timeouts cascading under failure.

#### Optimization strategy (highest impact first)

1. **Measure first**
   Add endpoint-level p50/p95/p99 dashboards and trace spans by dependency.

2. **Fix hot database paths**
   Index critical filters, remove N+1, optimize joins, paginate correctly.

3. **Protect external calls**
   Use strict timeouts, bounded retries with jitter, circuit breakers, fallbacks.

4. **Reduce request-path work**
   Move CPU-heavy tasks to workers/queues; keep HTTP path lightweight.

5. **Cache smartly**
   Cache read-heavy expensive data (Redis/in-memory as appropriate).

6. **Tune pools and concurrency**
   Right-size DB/HTTP pools and avoid queue buildup.

7. **Control payloads**
   Limit response fields, use compression, avoid giant JSON objects.

#### NestJS-specific practical actions

1. Add interceptor-based latency logging with requestId.
2. Instrument downstream calls (DB and HttpService) with timing and status.
3. Use global timeout policies for upstream calls.
4. Apply rate limiting on expensive endpoints.
5. Use background jobs for non-critical synchronous tasks.

#### Typical tail-latency anti-patterns

1. Endpoint does several sequential external calls.
2. Long DB transactions on read paths.
3. Per-request cache warmups without memoization.
4. Massive DTO transformations in hot paths.

#### SLO-oriented approach

1. Define latency SLOs per endpoint class (read, write, auth).
2. Alert on p95/p99 breach (not only average).
3. Run load tests with production-like traffic distribution.
4. Track regressions per release via CI perf checks where possible.

#### Rule of thumb

To improve p99, optimize worst-case paths and failure behavior, not just median
code paths. Tail latency is mostly a systems and dependency problem.

</details>

<details>
<summary>74. How do you use cluster mode in Node.js together with NestJS for scaling?</summary>

#### NestJS

Cluster mode runs multiple Node.js worker processes on one machine, allowing a
NestJS app to use multiple CPU cores instead of a single event loop.

#### Why use cluster mode

1. Better CPU utilization on multi-core servers.
2. Higher throughput for CPU/mixed workloads.
3. Process-level isolation (one worker crash does not kill all workers).

#### Basic cluster setup concept

1. Primary process forks `N` workers (`N` often = CPU cores).
2. Each worker starts Nest app on same port.
3. Node distributes incoming connections among workers.

#### Example bootstrap (conceptual)

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

#### Important production considerations

1. **Statelessness**
   In-memory state is per-worker and not shared.
   Use Redis/DB for shared sessions/cache/locks.

2. **WebSockets**
   Need sticky sessions or external pub/sub adapter for multi-worker consistency.

3. **Rate limiting/cache**
   In-memory implementations become inconsistent across workers.
   Prefer Redis-backed stores.

4. **Graceful shutdown**
   Handle SIGTERM/SIGINT and drain connections cleanly per worker.

5. **Observability**
   Include worker ID/process ID in logs and metrics.

#### Cluster vs containers/orchestrators

1. Cluster scales vertically within one host.
2. Kubernetes/PM2/systemd replicas scale horizontally across hosts.
3. Many teams rely on horizontal scaling first, using cluster only when needed.

#### When cluster mode is a good fit

1. Bare-metal/VM deployments with multi-core CPU.
2. Need extra throughput without immediate infra changes.
3. App is largely stateless and ready for multi-process behavior.

#### Rule of thumb

Cluster can boost single-host throughput, but it is not a substitute for
distributed architecture. Combine with externalized state and solid process
management.

</details>

<details>
<summary>75. How do you implement cron jobs in NestJS via @nestjs/schedule?</summary>

#### NestJS

In NestJS, cron jobs are implemented with `@nestjs/schedule`, which provides
declarative decorators for fixed intervals, timeouts, and cron expressions.

#### Step 1: install and enable ScheduleModule

```ts
import { Module } from '@nestjs/common';
import { ScheduleModule } from '@nestjs/schedule';

@Module({
  imports: [ScheduleModule.forRoot()],
})
export class AppModule {}
```

#### Step 2: create a scheduled service

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

#### Custom cron expression with timezone

```ts
@Cron('0 9 * * 1-5', { timeZone: 'Europe/Kyiv' })
runWeekdayAt9am() {}
```

#### Dynamic cron jobs (runtime)

For user-configurable schedules, use `SchedulerRegistry` to add/remove jobs at
runtime instead of static decorators.

#### Production considerations

1. **Multi-instance duplication risk**
   In scaled deployments, each instance runs cron unless coordinated.
   Use distributed locking (Redis/DB lock) or run jobs in a dedicated worker.

2. **Idempotency**
   Job handlers should be safe on retries/re-runs.

3. **Error handling**
   Wrap jobs with try/catch and structured logs/alerts.

4. **Timeouts and backpressure**
   Avoid overlapping long-running executions unless intended.

5. **Observability**
   Emit metrics: start/end/duration/success/failure.

#### Common use cases

1. Cleanup of expired sessions/tokens.
2. Sync with external systems.
3. Scheduled reports/notifications.
4. Data aggregation and cache warmup.

#### Rule of thumb

`@nestjs/schedule` is perfect for app-level scheduling, but in distributed systems
you need coordination to prevent duplicate executions.

</details>

<details>
<summary>76. What is EventEmitter in NestJS and how does it differ from queues (Bull)?</summary>

#### NestJS

`EventEmitter` in NestJS (`@nestjs/event-emitter`) is an in-process pub/sub
mechanism for internal module communication. It is fast and simple, but not
durable across process crashes/restarts.

Bull/BullMQ queues are persistent job-processing systems (usually Redis-backed)
designed for background execution, retries, and reliability.

#### Core difference

1. **EventEmitter**
   1. In-memory, same process.
   2. Fire-and-forget module events.
   3. No durable persistence by default.

2. **Bull/BullMQ**
   1. Persistent queue storage (Redis).
   2. Background workers process jobs.
   3. Retries, delays, backoff, concurrency, and monitoring support.

#### When to use EventEmitter

1. Internal domain events inside one service instance.
2. Lightweight side effects (audit log trigger, cache invalidation signal).
3. Non-critical async decoupling where occasional loss is acceptable.

#### When to use Bull/BullMQ

1. Critical tasks that must survive restarts.
2. Long-running/heavy jobs (emails, reports, media processing).
3. Need retry/backoff and dead-letter handling.
4. Need workload smoothing and controlled concurrency.

#### Reliability model comparison

1. **EventEmitter**
   If app crashes after emit and before handler runs, event may be lost.

2. **Queue**
   Job is persisted; worker can resume later with retry policies.

#### Latency and complexity tradeoff

1. EventEmitter:
   Lower latency, lower operational complexity.

2. Queue:
   Slightly higher latency and infra complexity, much higher reliability.

#### Practical NestJS pattern

1. Emit local domain events for immediate non-critical reactions.
2. Enqueue durable background jobs for important/expensive work.
3. For cross-service integration, use message brokers/events, not in-process
   EventEmitter alone.

#### Rule of thumb

If losing an event is unacceptable, use Bull/BullMQ (or broker-backed messaging),
not plain EventEmitter.

</details>

<details>
<summary>77. How do you implement internal event-driven communication between modules via EventEmitter2?</summary>

#### NestJS

Internal event-driven communication in NestJS with EventEmitter2 decouples modules:
one module emits a domain event, other modules react without direct service calls.

#### Step 1: enable EventEmitterModule

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

#### Step 2: emit events from application flow

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

#### Step 3: subscribe in other modules with `@OnEvent`

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

#### Naming and payload conventions

1. Use stable names: `domain.action` (`order.created`, `user.deleted`).
2. Keep payload explicit and versionable.
3. Include metadata (`occurredAt`, `correlationId`, `source`).

#### Error-handling considerations

1. Event handlers should catch/log their own failures.
2. One failing listener must not break core transaction flow.
3. For critical side effects, enqueue durable jobs instead of relying on in-memory
   event delivery only.

#### Module architecture guidance

1. Emit events from application services after successful state change.
2. Keep listeners in dedicated modules (notifications, analytics, audit).
3. Avoid circular dependencies by communicating through events instead of direct
   service injection.

#### Rule of thumb

Use EventEmitter2 for internal decoupling inside one service process. For
cross-service or guaranteed delivery, use queues/message brokers.

</details>

<details>
<summary>78. How do you implement background jobs using Bull or BullMQ?</summary>

#### NestJS

Background jobs in NestJS are used to move heavy or non-immediate work out of the
request/response path (emails, reports, media processing, sync tasks).

Bull/BullMQ provide Redis-backed durable queues with retries, delays, and worker
concurrency control.

#### Typical architecture

1. API/service enqueues job quickly.
2. Worker/processor consumes job asynchronously.
3. Job state is tracked (`waiting`, `active`, `completed`, `failed`).

#### Step 1: register queue module

Bull-style module setup:

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

#### Step 2: produce jobs

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

#### Step 3: consume jobs in processor

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

#### BullMQ note

BullMQ uses newer APIs (`Queue`, `Worker`, `QueueEvents`) and is recommended for
newer ecosystems. Conceptual flow is identical: producer -> Redis queue -> worker.

#### Production best practices

1. Make jobs idempotent (safe on retries).
2. Set attempts/backoff and failure policies explicitly.
3. Use dedicated worker processes for heavy queues.
4. Monitor queue depth, processing time, and failure rate.
5. Use dead-letter/retry analysis workflow for poisoned jobs.
6. Version job payloads/contracts carefully.

#### Common mistakes

1. Running heavy job logic inside API process only.
2. No retry/backoff strategy (or infinite retries).
3. Non-idempotent side effects causing duplicates on retry.
4. Missing observability for failed jobs.

#### Rule of thumb

If work is slow, retryable, or non-critical to immediate response, enqueue it.
Keep request path fast and delegate processing to queue workers.

</details>

<details>
<summary>79. How do you design idempotent jobs (task queues) to avoid duplicate execution?</summary>

#### NestJS

Idempotent job design means running the same job multiple times produces the same
final state as running it once.

This is mandatory in queue systems because retries, worker restarts, and delivery
semantics can cause duplicate execution attempts.

#### Why duplicates happen

1. Worker crashes after side effect but before ACK.
2. Retry after timeout/network partition.
3. Manual requeue/replay operations.
4. Multi-consumer race conditions.

#### Core idempotency strategies

1. **Business idempotency key**
   Include stable unique key per operation (`paymentId`, `orderId:action`).

2. **Deduplication store**
   Persist processed keys/status in DB/Redis with uniqueness constraint.

3. **Atomic check-and-set**
   Ensure "first execution wins" using transaction/lock/unique insert.

4. **Outbox/inbox patterns**
   Track processed message IDs to prevent repeat side effects.

5. **Idempotent side-effect APIs**
   Use external provider idempotency keys where supported.

#### Practical job flow

1. Job starts with `idempotencyKey`.
2. Try to reserve key atomically:
   1. If already completed -> exit successfully (no-op).
   2. If reserved now -> proceed.
3. Execute side effects.
4. Mark key completed with result metadata.
5. On failure, keep retry policy but preserve idempotency record semantics.

#### Example key model

1. `job_key` (unique)
2. `status` (`processing`, `completed`, `failed`)
3. `updated_at`
4. optional `result_hash` / `external_reference`

#### Queue-level techniques

1. Set deterministic `jobId` when enqueueing (prevents duplicate enqueues in many
   queue engines).
2. Use bounded retries + backoff.
3. Avoid concurrent processing of same entity (partitioning/locking).

#### NestJS/Bull practical hints

1. Put idempotency guard at processor start, not only producer side.
2. Keep processor transactional where possible.
3. For external calls, pass idempotency header/key downstream.
4. Emit structured logs with key + attempt + outcome.

#### Common mistakes

1. Assuming "exactly once" delivery from queue.
2. Performing side effects before idempotency reservation.
3. Keying by random UUID per retry (breaks deduplication).
4. Deleting idempotency records too early.

#### Rule of thumb

Design every background job as at-least-once delivered. Idempotency at business
boundary is what makes retries safe.

</details>

<details>
<summary>80. How do you implement WebSockets in NestJS?</summary>

#### NestJS

WebSockets in NestJS are implemented via Gateways, typically using the
`@nestjs/websockets` package with a Socket.IO adapter (default common setup).

#### Core concepts

1. **Gateway**
   WebSocket entry point (similar role to controller for HTTP).

2. **Events/messages**
   Client emits event names with payloads; server handles and responds/emits.

3. **Lifecycle hooks**
   Handle connect/disconnect and server initialization.

#### Basic gateway example

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

#### Room and broadcast patterns

1. Join room: `client.join(roomId)`.
2. Emit to room: `server.to(roomId).emit(...)`.
3. Emit to all: `server.emit(...)`.
4. Emit to sender only: `client.emit(...)`.

#### Validation and security

1. Validate message payloads (DTO/pipes).
2. Authenticate connection (token/session during handshake).
3. Authorize room access per event.
4. Apply rate limiting/throttling for noisy events.

#### Production considerations

1. Multi-instance scaling needs adapter/pub-sub (e.g., Redis adapter) for
   cross-node event propagation.
2. Use sticky sessions/load balancer strategy when required by transport.
3. Track connection count, event throughput, and disconnect reasons.
4. Keep handlers lightweight; move heavy work to queues/workers.

#### Rule of thumb

Use WebSockets for low-latency bidirectional features (chat, live updates,
presence). Keep protocol contracts explicit and secured like any public API.

</details>

<details>
<summary>81. How do you implement authentication in a WebSocket Gateway?</summary>

#### NestJS

WebSocket authentication in NestJS is usually done during the handshake phase,
then enforced per-event with guards/authorization checks.

#### Typical authentication flow

1. Client sends token (JWT/session) in handshake:
   `auth`, headers, or query params (prefer `auth`/headers).

2. Server verifies token in gateway middleware/guard.

3. Authenticated user context is attached to socket (`client.data.user`).

4. Subsequent message handlers use that context for authorization.

#### Example: authenticate on connection

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

#### Guard-based event authorization

1. Use `WsGuard` to validate auth context per event.
2. Combine with role/policy checks (room membership, tenant scope, permissions).

#### Security best practices

1. Prefer short-lived access tokens.
2. Re-check authorization on sensitive events, not only at connect time.
3. Handle token expiry/revocation (disconnect or require re-auth).
4. Never trust client-sent user IDs in message payload; use socket auth context.
5. Apply throttling/rate limits for auth-sensitive events.

#### Scaling notes

1. In multi-instance setups, use shared session/token verification strategy.
2. If presence/rooms are distributed, use Redis adapter for cross-node state sync.

#### Rule of thumb

Authenticate once at handshake for efficiency, authorize per-event for safety.
Both layers are required for secure real-time systems.

</details>

<details>
<summary>82. What approaches are used for scaling real-time systems?</summary>

#### NestJS

Scaling real-time systems requires handling three dimensions together:
1. connection scale,
2. message throughput,
3. state consistency across nodes.

#### Core scaling approaches

1. **Horizontal scaling of gateway instances**
   Run multiple WebSocket gateway replicas behind a load balancer.

2. **Sticky sessions (when required)**
   Ensure the same client remains on the same node if transport/session model
   requires affinity.

3. **Pub/Sub adapter for cross-node broadcast**
   Use Redis adapter (or equivalent) so events emitted on one node reach clients
   connected to other nodes.

4. **Externalized shared state**
   Store presence/rooms/session metadata in Redis/DB, not process memory only.

5. **Backpressure and rate limiting**
   Throttle noisy clients, cap fan-out bursts, and protect downstream systems.

#### Architecture patterns

1. **Gateway tier + worker tier**
   Gateways handle connections; heavy processing moved to queue workers.

2. **Channel/room partitioning**
   Partition high-volume streams by tenant/region/topic.

3. **Event-driven backbone**
   Use brokers (Redis Streams/Kafka/NATS) for durable or high-throughput event
   distribution when simple pub/sub is not enough.

4. **Fan-out optimization**
   Precompute recipient sets and avoid per-message expensive DB lookups.

#### Performance and reliability techniques

1. Use compact message payloads and avoid oversized events.
2. Apply heartbeats/ping-pong with sane timeouts.
3. Handle reconnect + replay strategy for missed critical messages.
4. Add circuit breakers/timeouts for external dependencies.
5. Monitor p95/p99 event delivery latency and drop rates.

#### Operational observability must-haves

1. Active connections per node.
2. Messages/sec in/out.
3. Room size distribution and hot rooms.
4. Cross-node pub/sub lag.
5. Error/disconnect reasons and reconnect success rate.

#### NestJS-specific implementation stack (typical)

1. `@WebSocketGateway` for real-time endpoints.
2. Redis adapter for multi-instance event propagation.
3. Bull/BullMQ for offloading heavy async tasks.
4. `@nestjs/throttler` or custom guards for abuse control.

#### Rule of thumb

Real-time scaling is not just "more pods." You must combine horizontal gateways,
shared pub/sub/state, and strict flow control to keep latency predictable.

</details>

<details>
<summary>83. What are the approaches to integrating GraphQL in NestJS (code-first vs schema-first), and what is the difference?</summary>

#### NestJS

NestJS supports two GraphQL integration approaches:
1. **Code-first**
2. **Schema-first**

Both are production-valid. The difference is where your API contract is authored
first: TypeScript classes/decorators or `.graphql` SDL files.

#### Code-first approach

You define GraphQL types/resolvers in TypeScript using decorators, and schema is
generated automatically.

Example style:
1. `@ObjectType()`, `@Field()`, `@InputType()`
2. `@Resolver()`, `@Query()`, `@Mutation()`

Pros:
1. Single language (TS) for app + schema.
2. Strong typing and refactor support in IDE.
3. Less duplication between DTOs and schema model.

Cons:
1. Schema readability for non-TS stakeholders can be lower.
2. Generated schema must still be reviewed/versioned carefully.

#### Schema-first approach

You define schema in `.graphql` files (SDL), then implement resolvers in TS.

Pros:
1. Contract-first workflow (good for API governance).
2. SDL is explicit and easy for cross-team review.
3. Strong fit when schema is shared across languages/teams.

Cons:
1. Potential duplication between SDL and TS types.
2. Requires synchronization discipline to avoid drift.

#### NestJS setup examples (conceptual)

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

#### Choosing between them

1. Choose **code-first** when:
   1. Team is TypeScript-centric.
   2. Speed of iteration is priority.
   3. Schema is primarily owned by backend team.

2. Choose **schema-first** when:
   1. API contract is governed/shared broadly.
   2. Multiple implementations/consumers depend on SDL.
   3. Contract review/versioning is a primary workflow.

#### Practical recommendation

For most NestJS teams, code-first gives fastest development and strong typing.
Use schema-first where contract governance and cross-team SDL ownership are key.

</details>

<details>
<summary>84. What are resolvers in GraphQL and how do they differ from REST controllers?</summary>

#### NestJS

Resolvers in GraphQL are functions that resolve fields in the GraphQL schema.
They are the execution layer that provides data for queries, mutations, and
nested object fields.

In NestJS, resolvers are defined with `@Resolver()` and method decorators like
`@Query()`, `@Mutation()`, and `@ResolveField()`.

#### What resolvers do

1. Handle GraphQL operations (`query`, `mutation`, subscriptions where used).
2. Resolve nested fields lazily (per requested selection set).
3. Access context (auth user, request metadata, loaders).
4. Delegate business logic to services.

#### How resolvers differ from REST controllers

1. **API shape**
   REST controllers expose multiple URL endpoints.
   GraphQL resolver exposes one endpoint with schema-driven operations.

2. **Data selection**
   REST returns fixed response per endpoint.
   GraphQL returns client-selected fields dynamically.

3. **Execution model**
   REST controller usually handles full response at once.
   GraphQL resolver tree may execute multiple field resolvers.

4. **Over/under-fetching**
   REST often requires endpoint design tradeoffs.
   GraphQL reduces over/under-fetching via query selection sets.

5. **Versioning style**
   REST often uses explicit API versioning.
   GraphQL typically evolves schema with deprecations and additive changes.

#### NestJS resolver example

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

1. Keep resolvers thin; put business logic in services.
2. Use DataLoader/batching to avoid N+1 in nested fields.
3. Validate args/inputs and enforce authz in guards/context.
4. Design schema types around domain language, not DB tables directly.

#### Rule of thumb

Resolvers are GraphQL’s equivalent of controllers, but with field-level execution
and client-driven data selection semantics.

</details>

<details>
<summary>85. How do you work with context in GraphQL and implement authorization through it?</summary>

#### NestJS

In NestJS GraphQL, `context` is the per-request container that carries request
metadata (user, headers, requestId, loaders, tenant info) into resolvers and
guards.

Authorization is typically implemented by:
1. authenticating user into context,
2. enforcing access rules with GraphQL-aware guards/policies.

#### Step 1: populate GraphQL context

When configuring `GraphQLModule`, expose request data in context:

```ts
GraphQLModule.forRoot({
  autoSchemaFile: true,
  context: ({ req, res }) => ({ req, res, requestId: req.headers['x-request-id'] }),
});
```

If JWT auth middleware/strategy attaches `req.user`, it becomes available through
GraphQL context.

#### Step 2: access context in resolver

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

#### Step 3: authorize with GraphQL guard

Use `GqlExecutionContext` to read `req.user` in guards:

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

Apply:

```ts
@UseGuards(GqlAuthGuard)
@Query(() => User)
me(@Context() ctx: any) {
  return ctx.req.user;
}
```

#### Fine-grained authorization

1. Role-based checks via metadata + guard (`@Roles(...)`).
2. Policy/ABAC checks using subject-action-resource service.
3. Field-level authorization in `@ResolveField()` when needed.

#### Best practices

1. Keep context minimal but sufficient (user, requestId, loaders, tenant).
2. Do authentication once per request, authorization per operation/field.
3. Use DataLoaders in context for N+1 prevention.
4. Never trust client-provided user identifiers; use authenticated context only.

#### Rule of thumb

GraphQL context is your trusted request envelope. Put identity there, then enforce
authorization through guards/policies built on that context.

</details>

<details>
<summary>86. What transport protocols and message brokers are supported (Kafka, Redis, gRPC, NATS) and what are their differences?</summary>

#### NestJS

NestJS microservices support multiple transports, including Kafka, Redis, gRPC,
and NATS. Each has different delivery semantics, performance profile, and use
cases.

#### High-level comparison

1. **Kafka**
   Distributed commit-log broker with high throughput, durable retention, consumer
   groups, and replay capability.

2. **Redis transport (pub/sub or streams-based patterns)**
   Very fast, simple, low-latency messaging; durability/ordering semantics depend
   on chosen Redis pattern and setup.

3. **gRPC**
   RPC protocol over HTTP/2 using Protobuf contracts; excellent for strongly typed
   synchronous service-to-service calls.

4. **NATS**
   Lightweight high-performance messaging system; great for low-latency pub/sub
   and request/reply, with optional persistence via JetStream.

#### When to choose each

1. **Kafka**
   1. Event streaming and audit trails.
   2. High-throughput async pipelines.
   3. Need replay/history and strong scaling of consumers.

2. **Redis**
   1. Simple lightweight event fan-out.
   2. Cache-adjacent messaging patterns.
   3. Low operational overhead for smaller systems.

3. **gRPC**
   1. Low-latency internal RPC with strict contracts.
   2. Polyglot microservices needing generated clients/stubs.
   3. Bi-directional streaming RPC use cases.

4. **NATS**
   1. Fast cloud-native messaging.
   2. Request/reply and pub/sub with minimal footprint.
   3. JetStream when you need durability/ack/replay features.

#### Semantic differences that matter

1. **Communication style**
   Kafka/NATS/Redis: event/message-driven async patterns.
   gRPC: direct RPC request/response (sync-oriented).

2. **Durability/replay**
   Kafka: strong durable log and replay by design.
   NATS core: ephemeral unless JetStream enabled.
   Redis pub/sub: ephemeral by default.
   gRPC: no broker persistence layer (RPC call semantics).

3. **Contract model**
   gRPC uses Protobuf-first strict schemas.
   Broker-based transports often rely on message schema conventions
   (Avro/JSON/Protobuf) enforced by team/tooling.

#### Practical NestJS design guidance

1. Use **gRPC** for synchronous internal APIs that need strict typing.
2. Use **Kafka/NATS/Redis** for asynchronous decoupled workflows.
3. For critical business events needing replay/audit, prefer **Kafka** or
   persistent **NATS JetStream** patterns.
4. Standardize message envelopes (eventName, version, correlationId, payload).
5. Add observability for lag, retry, DLQ, and consumer health.

#### Rule of thumb

Choose transport by failure model and delivery guarantees first, not by raw
throughput alone.

</details>

<details>
<summary>87. How do you properly design an event-driven architecture and what are the core principles?</summary>

#### NestJS

Event-driven architecture (EDA) organizes systems around events: facts that
something happened (`order.created`, `payment.failed`, etc.). Producers publish
events; consumers react asynchronously.

#### Core principles

1. **Loose coupling**
   Producers do not depend on consumer internals.

2. **Asynchronous communication**
   Services coordinate through events instead of blocking RPC where possible.

3. **Single source of truth per domain**
   Each service owns its data and publishes domain events after state changes.

4. **Event contract governance**
   Events are versioned contracts with stable schema and semantic meaning.

5. **Idempotent consumers**
   Handlers must safely process duplicate deliveries.

6. **Observability and traceability**
   Correlation IDs, event metadata, and processing metrics are mandatory.

#### Event design guidelines

1. Name events as past-tense facts: `invoice.paid`, `user.email_changed`.
2. Include metadata:
   `eventId`, `eventType`, `occurredAt`, `version`, `correlationId`, `source`.
3. Keep payload focused on business meaning, not internal DB structure.
4. Prefer additive schema evolution; avoid breaking changes.

#### Delivery and consistency model

1. Assume at-least-once delivery in most broker systems.
2. Use eventual consistency across service boundaries.
3. Use retries + DLQ for failed processing.
4. Apply outbox pattern to avoid "DB write succeeded but event publish failed"
   gaps.

#### NestJS implementation building blocks

1. Internal module events: `@nestjs/event-emitter` (in-process).
2. Durable async processing: Bull/BullMQ queues.
3. Cross-service messaging: Kafka/NATS/Redis transport adapters.
4. Consumer handlers with validation + idempotency checks.

#### Anti-patterns to avoid

1. Event payloads with huge mutable object snapshots.
2. Hidden synchronous coupling disguised as events.
3. No schema versioning strategy.
4. No replay/recovery plan for consumer outages.
5. Treating events as commands (unless explicitly modeled).

#### Practical architecture flow

1. Command updates domain state in owner service.
2. Owner emits domain event (transactionally via outbox).
3. Broker delivers to interested consumers.
4. Consumers update their own read models/side effects.
5. Monitoring tracks lag, failures, and DLQ.

#### Rule of thumb

Design events as durable business facts, not implementation details. Reliability
comes from idempotency, contract discipline, and operational observability.

</details>

<details>
<summary>88. How do you handle distributed transactions in microservices? (Saga pattern, eventual consistency)</summary>

#### NestJS

In microservices, classic ACID transaction across multiple services/databases is
usually impractical. Instead, use **eventual consistency** and coordination
patterns like **Saga**.

#### Why distributed transactions are hard

1. Services own separate databases.
2. Network failures and partial success are normal.
3. 2PC-style global transactions reduce availability and add complexity.

#### Preferred approach: Saga pattern

A Saga is a sequence of local transactions across services with
success/failure-driven steps.

Two variants:
1. **Choreography**
   Services react to events without central coordinator.
2. **Orchestration**
   Dedicated orchestrator controls step flow and compensations.

#### Core concepts

1. **Local transaction per service**
   Each service commits only its own DB changes.

2. **Compensating actions**
   If later step fails, previously completed steps are compensated
   (`reserve -> release`, `charge -> refund`).

3. **Idempotency**
   All handlers/compensations must tolerate duplicate delivery.

4. **Eventual consistency**
   Temporary inconsistencies are accepted until saga converges.

#### Example flow (order checkout)

1. Order service creates `PENDING` order.
2. Payment service charges customer.
3. Inventory service reserves stock.
4. If all succeed -> order becomes `CONFIRMED`.
5. If inventory fails after payment -> run compensation (`payment.refund`) and set
   order `CANCELLED`.

#### NestJS implementation building blocks

1. Message transport/broker (Kafka, NATS, Redis, etc.).
2. Durable job/event handling with retries and DLQ.
3. Outbox pattern for reliable event publishing after local commit.
4. Saga state tracking (DB table/workflow store).
5. Structured logs with `correlationId`/`sagaId`.

#### Choreography vs orchestration tradeoff

1. **Choreography**
   + Simple at start, less central dependency
   - Harder global visibility/control as flows grow

2. **Orchestration**
   + Clear flow ownership, easier debugging and policy control
   - Extra component and coordination logic

#### Practical safeguards

1. Add timeouts per saga step.
2. Implement retry with backoff for transient failures.
3. Define compensation for each non-idempotent side effect.
4. Keep saga steps small and explicit.
5. Monitor stuck/incomplete sagas.

#### Rule of thumb

In microservices, do not chase global ACID. Model business workflows as sagas with
idempotent handlers, compensations, and strong observability.

</details>

<details>
<summary>89. What is CQRS and how do you implement it in NestJS using @nestjs/cqrs?</summary>

#### NestJS

CQRS (Command Query Responsibility Segregation) separates write operations
(commands) from read operations (queries), often with different models and
optimization strategies for each side.

#### Why CQRS is used

1. Clear separation of business mutations vs read concerns.
2. Better scalability for read-heavy systems.
3. Easier modeling of complex domain workflows.
4. Cleaner integration with events and eventual consistency.

#### Core CQRS components

1. **Command**
   Intention to change state (`CreateOrderCommand`).

2. **CommandHandler**
   Executes business logic and writes state.

3. **Query**
   Request for data without side effects (`GetOrderByIdQuery`).

4. **QueryHandler**
   Returns read model/data projection.

5. **Events** (optional but common)
   Facts emitted after successful state changes.

#### NestJS implementation with `@nestjs/cqrs`

Step 1: install and import `CqrsModule`.

```ts
@Module({
  imports: [CqrsModule],
  providers: [CreateOrderHandler, GetOrderByIdHandler],
})
export class OrdersModule {}
```

Step 2: define command + handler.

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

Step 3: define query + handler.

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

Step 4: use buses in controller/service.

```ts
constructor(
  private readonly commandBus: CommandBus,
  private readonly queryBus: QueryBus,
) {}

await this.commandBus.execute(new CreateOrderCommand(userId, items));
return this.queryBus.execute(new GetOrderByIdQuery(orderId));
```

#### When CQRS is worth it

1. Complex domain rules and workflows.
2. Different scaling needs for reads vs writes.
3. Need for event-driven projections/read models.

#### When not to overuse CQRS

1. Small CRUD apps with simple logic.
2. Teams not ready for extra architectural complexity.

#### Rule of thumb

Use CQRS where business complexity or scaling needs justify it. Otherwise, keep a
simpler service/repository model and evolve incrementally.

</details>

<details>
<summary>90. What is Domain-Driven Design and how are its principles applied in NestJS?</summary>

#### NestJS

Domain-Driven Design (DDD) is an approach that models software around core
business domains and their language, rather than around technical layers only.

In NestJS, DDD is applied by aligning modules and code boundaries with business
capabilities and domain rules.

#### Core DDD principles

1. **Ubiquitous language**
   Shared business vocabulary across code, docs, and conversations.

2. **Bounded contexts**
   Clear boundaries where a model has specific meaning.

3. **Entities / Value Objects / Aggregates**
   Domain objects with explicit invariants and consistency rules.

4. **Domain services**
   Stateless business operations that do not belong to one entity.

5. **Repositories**
   Abstractions for loading/saving aggregates.

6. **Domain events**
   Business facts emitted when meaningful state changes occur.

#### How this maps to NestJS

1. **Feature modules as bounded contexts**
   `OrdersModule`, `BillingModule`, `InventoryModule`.

2. **Application layer services**
   Orchestrate use cases, transactions, integrations.

3. **Domain layer**
   Pure business model (entities/value objects/policies), framework-agnostic.

4. **Infrastructure adapters**
   DB, messaging, external APIs, HTTP controllers.

#### Typical folder structure (example)

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

#### Practical DDD benefits in NestJS

1. Better fit for complex business logic.
2. Reduced accidental coupling between domains.
3. More testable core logic independent of framework/infrastructure.
4. Easier evolution of architecture as system grows.

#### Common pitfalls

1. Calling any layered code "DDD" without domain model depth.
2. Leaking ORM entities directly into domain logic.
3. Mixing technical language with business concepts inconsistently.
4. Overengineering DDD for trivial CRUD services.

#### When DDD is most valuable

1. Rich, changing business rules.
2. Multiple teams/domains in one platform.
3. Need for long-term model clarity and bounded context autonomy.

#### Rule of thumb

Apply DDD incrementally: start with clear bounded contexts and ubiquitous language,
then evolve deeper tactical patterns where domain complexity justifies them.

</details>

<details>
<summary>91. What is Hexagonal Architecture (Ports & Adapters) and how do you implement it in NestJS?</summary>

#### NestJS

Hexagonal Architecture (Ports & Adapters) structures an application so business
logic is isolated from external technologies (DB, HTTP, message brokers, SDKs).

The core depends on abstractions (ports), while concrete integrations are adapter
implementations.

#### Core concepts

1. **Domain/Application Core**
   Business rules and use-case orchestration.

2. **Ports**
   Interfaces/contracts the core uses (output ports) or exposes (input ports).

3. **Adapters**
   Technical implementations of ports:
   HTTP controllers, DB repositories, message consumers, external API clients.

#### Dependency rule

All dependencies point inward:
1. Adapters depend on core contracts.
2. Core does not depend on frameworks/infrastructure details.

#### Applying in NestJS

1. Define port interfaces in domain/application layer.
2. Implement adapters in infrastructure layer.
3. Bind adapter classes to port tokens in module providers.
4. Use DI to inject port into use-case services.

#### Example shape

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

Adapter implementation:

```ts
@Injectable()
export class StripePaymentAdapter implements PaymentPort {
  async charge(input: { orderId: string; amount: number }) {
    // call Stripe SDK
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

#### Benefits

1. Easier testing (mock ports in unit tests).
2. Lower coupling to framework/ORM/external vendors.
3. Safer long-term refactors and technology swaps.
4. Clearer architecture boundaries for teams.

#### Common pitfalls

1. Ports too generic (lose domain meaning).
2. Leaking ORM/HTTP types into core interfaces.
3. Excessive abstraction for tiny/simple modules.

#### Rule of thumb

Use hexagonal boundaries around important business flows and unstable external
dependencies. Keep ports business-oriented and adapters replaceable.

</details>

<details>
<summary>92. How do you implement structured logging, and why is it needed?</summary>

#### NestJS

Structured logging means writing logs as machine-readable records (usually JSON)
with consistent fields, instead of free-form text strings.

It is needed for searchability, alerting, correlation, and reliable observability
in production systems.

#### Why structured logging matters

1. Fast filtering/querying in log platforms.
2. Better incident debugging with correlation IDs.
3. Consistent dashboards and alerts.
4. Easier cross-service tracing in distributed systems.

#### What to include in every log

1. `timestamp`
2. `level` (`debug`, `info`, `warn`, `error`)
3. `service` / `env`
4. `message`
5. `requestId` / `traceId`
6. Context fields (`userId`, `route`, `method`, `statusCode`, latency)
7. Error details (`errorName`, `stack`) for failures

#### NestJS implementation approach

1. Use a structured logger (Pino/Winston) as app logger.
2. Attach request context (`requestId`, user info) via middleware/interceptor.
3. Log business events and failures with consistent schema.
4. Avoid ad-hoc `console.log` in production code.

#### Practical example style

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

#### Error logging guidance

1. Keep full stack trace in logs.
2. Do not expose stack traces in API responses.
3. Add domain error codes for reliable alert routing.
4. Preserve root cause chain when wrapping exceptions.

#### Common mistakes

1. Logging plain strings without context fields.
2. Inconsistent field names across modules/services.
3. Logging secrets/tokens/PII unredacted.
4. Excessive debug noise in production hot paths.

#### Best practices

1. Define and document a log schema.
2. Redact sensitive fields centrally.
3. Use log levels intentionally.
4. Correlate logs with metrics and traces.
5. Validate logging output in integration tests for critical flows.

#### Rule of thumb

If logs are for humans only, incident response will be slow. If logs are
structured for machines and humans, operations become predictable and scalable.

</details>

<details>
<summary>93. How do you implement application health monitoring in NestJS? (@nestjs/terminus)</summary>

#### NestJS

Application health monitoring in NestJS is commonly implemented with
`@nestjs/terminus`, which provides standardized health-check endpoints for app and
dependency readiness/liveness.

#### Why health monitoring is needed

1. Orchestrators/load balancers need health signals.
2. Faster incident detection and automated recovery.
3. Safe deployment rollouts and readiness gating.

#### Typical health endpoints

1. **Liveness** (`/health/live`)
   "Process is running" check.

2. **Readiness** (`/health/ready`)
   "Can serve traffic now" check, including critical dependencies.

#### Basic setup steps

1. Install `@nestjs/terminus`.
2. Import `TerminusModule`.
3. Create `HealthController` using `HealthCheckService`.

#### Example controller

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

#### What to include in readiness

1. DB connectivity.
2. Redis/cache connectivity.
3. Critical external dependencies (when truly required for serving traffic).
4. Internal resource thresholds (memory, event-loop pressure where applicable).

#### Operational best practices

1. Keep liveness lightweight and local.
2. Keep readiness dependency-aware but fast.
3. Do not include non-critical optional services in readiness fail criteria.
4. Secure/limit health details in public environments.
5. Integrate with Kubernetes probes and alerting.

#### Rule of thumb

Liveness says "restart me if dead." Readiness says "route traffic to me only when
I can actually serve requests safely."

</details>

<details>
<summary>94. How do you implement health checks for dependent services (DB, Redis, external APIs)?</summary>

#### NestJS

Health checks for dependencies verify whether critical external systems are
available enough for your app to serve traffic safely.

In NestJS, this is typically implemented with `@nestjs/terminus` indicators.

#### Dependency categories to check

1. **Database** (readiness-critical for most APIs).
2. **Redis/cache** (critical or optional depending on architecture).
3. **External APIs** (only those required for core request paths).

#### Implementation approach

1. Keep `/health/live` lightweight (process-level).
2. Put dependency checks in `/health/ready`.
3. Mark non-critical dependencies separately to avoid unnecessary hard-fail.

#### Example readiness controller

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

For Redis, use a custom health indicator or supported adapter indicator depending
on your stack.

#### Design decisions that matter

1. **Critical vs optional dependency**
   Only critical dependencies should fail readiness.

2. **Timeouts**
   Health checks must have strict short timeouts to avoid probe pileups.

3. **Check cost**
   Use lightweight "ping" checks, not expensive queries.

4. **Failure semantics**
   Return clear status per dependency for diagnostics.

#### Operational best practices

1. Use separate endpoints for liveness/readiness/startup probes.
2. Avoid checking too many flaky external services directly in readiness.
3. Add caching/debouncing of expensive checks if needed.
4. Alert on dependency status transitions, not only complete app down.
5. Include dependency latency in observability dashboards.

#### Rule of thumb

Health checks should answer: "Can this instance serve requests correctly now?"
Design dependency checks around that question, not around checking everything.

</details>

<details>
<summary>95. How do you use OpenTelemetry in NestJS?</summary>

#### NestJS

OpenTelemetry (OTel) in NestJS is used to collect traces, metrics, and logs for
observability. The most common starting point is distributed tracing for incoming
requests and downstream calls.

#### What OpenTelemetry gives you

1. End-to-end request traces across services.
2. Latency breakdown by spans (DB, HTTP, cache, queue).
3. Correlation between errors and specific dependencies.
4. Vendor-neutral telemetry format (export to Jaeger/Tempo/Datadog/New Relic, etc.).

#### Typical NestJS OTel setup flow

1. Initialize OTel SDK before app bootstrap.
2. Configure resource attributes (`service.name`, `service.version`, env).
3. Enable auto-instrumentations (HTTP, Express, DB clients, etc.).
4. Export traces via OTLP/collector.
5. Add custom spans where business context is important.

#### Minimal conceptual bootstrap (Node SDK)

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

Then start Nest app normally.

#### Custom span example (business boundary)

1. Start span around critical domain operation.
2. Attach attributes (`order.id`, `tenant.id`).
3. Record exceptions and status on failure.

#### Practical best practices

1. Sample intelligently (full in staging, tuned sampling in production).
2. Propagate context headers (`traceparent`) across HTTP/message boundaries.
3. Avoid high-cardinality attributes (user email, random IDs in labels).
4. Instrument critical dependencies and queue consumers.
5. Correlate traces with logs using trace/span IDs.

#### Common pitfalls

1. Initializing OTel after app start (misses early spans).
2. Over-instrumentation causing overhead/noise.
3. Missing context propagation between services/workers.
4. Sending telemetry directly from app without collector in larger deployments.

#### Rule of thumb

Start with tracing + auto-instrumentation, then add targeted custom spans around
high-value business operations and latency hotspots.

</details>

<details>
<summary>96. What is distributed tracing and how is it implemented in a microservice architecture?</summary>

#### NestJS

Distributed tracing tracks one request/transaction across multiple services and
infrastructure components, showing end-to-end flow and latency breakdown.

It is essential in microservices, where a single user action may trigger many
service calls, queue hops, and DB operations.

#### Core tracing concepts

1. **Trace**
   Full end-to-end request path.

2. **Span**
   One operation inside the trace (HTTP call, DB query, handler execution).

3. **Context propagation**
   Passing trace context between services (e.g., `traceparent` header).

4. **Parent-child relationships**
   Spans form a tree representing call hierarchy.

#### Why distributed tracing is needed

1. Find real bottlenecks (which dependency is slow).
2. Debug cross-service failures quickly.
3. Understand fan-out/fan-in behavior and retry storms.
4. Improve p95/p99 through evidence, not guesswork.

#### How it is implemented in microservices

1. Instrument each service with OpenTelemetry SDK.
2. Auto-instrument frameworks/libraries (HTTP server/client, DB, message clients).
3. Propagate context across boundaries:
   1. HTTP headers (`traceparent`, `tracestate`)
   2. Message metadata for Kafka/NATS/queues
4. Export spans to collector/backend (OTLP -> Jaeger/Tempo/Datadog/etc.).
5. Correlate logs with traceId/spanId.

#### NestJS-specific implementation points

1. Initialize OTel before Nest bootstrap.
2. Instrument inbound requests (Express/Fastify).
3. Instrument outbound `HttpService` and DB drivers.
4. Add custom spans around important business operations.
5. Propagate context to workers/background jobs.

#### Typical trace in practice

1. API Gateway receives request (root span).
2. Service A validates auth (child span).
3. Service A calls Service B over gRPC/HTTP (child span).
4. Service B queries DB (nested span).
5. Service B publishes event to broker (child span).
6. Worker consumes event and performs side effect (linked/continued context).

#### Best practices

1. Use consistent service naming and resource attributes.
2. Avoid high-cardinality span attributes.
3. Tune sampling policy (tail-based/head-based by traffic profile).
4. Capture errors and status codes on spans.
5. Keep trace retention aligned with incident/debug needs.

#### Rule of thumb

In microservices, metrics tell you that something is slow; distributed tracing
tells you exactly where and why.

</details>

<details>
<summary>97. How do you write unit tests in NestJS, and what are the basic testing approaches?</summary>

#### NestJS

Unit testing in NestJS focuses on testing one class/module behavior in isolation,
usually with mocked dependencies and no real network/database calls.

#### Core testing levels in NestJS

1. **Unit tests**
   Test services/guards/pipes/interceptors in isolation.

2. **Integration tests**
   Test interaction between components/modules (often with test DB).

3. **E2E tests**
   Test full HTTP app behavior via real Nest app bootstrap.

#### Typical unit testing stack

1. Jest as test runner/assertion/mocking tool.
2. `@nestjs/testing` for creating testing modules.
3. Mock providers for dependencies (`useValue`, `useFactory`).

#### Example unit test for service

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

#### Basic testing approaches

1. **Arrange-Act-Assert**
   Keep tests readable and deterministic.

2. **Mock external boundaries**
   DB, HTTP clients, queues, and time-dependent systems.

3. **Test behavior, not implementation details**
   Assert outcomes and side effects, not private internals.

4. **Cover happy path + failure path**
   Validation errors, exceptions, edge cases.

#### What to unit-test first in NestJS

1. Application/domain services.
2. Custom guards/pipes/interceptors.
3. Utility/domain logic classes.
4. Mapper/validation logic with branchy behavior.

#### Common mistakes

1. Calling real DB in "unit" tests.
2. Over-mocking to the point tests lose value.
3. Asserting fragile internal calls too strictly.
4. Ignoring negative/error scenarios.

#### Rule of thumb

Unit tests should be fast, isolated, and deterministic. Use them to lock business
logic behavior; use integration/e2e tests to validate wiring and runtime reality.

</details>

<details>
<summary>98. How do you properly mock dependencies in NestJS, and when should you do it?</summary>

#### NestJS

Mocking dependencies in NestJS means replacing real collaborators (DB repos, HTTP
clients, queues, external SDKs) with controlled test doubles to isolate unit
behavior.

#### When you should mock

1. Unit tests of services/guards/pipes/interceptors.
2. Failure-path testing that is hard to trigger with real systems.
3. Fast feedback loops where external I/O would slow tests down.

#### When you should not mock

1. Integration tests validating module wiring and real adapters.
2. E2E tests validating full runtime behavior.
3. Cases where contract drift risk is high and real dependency interaction matters.

#### Common NestJS mocking pattern

Use `TestingModule` and override provider tokens with `useValue`/`useFactory`.

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

#### Mocking tips by dependency type

1. **Repository/DAO**
   Mock specific methods used in test (`findOne`, `save`, etc.).

2. **HttpService / external client**
   Mock return values/errors and timeout scenarios.

3. **Queue/event publishers**
   Mock enqueue/publish calls and assert payload/contracts.

4. **ConfigService**
   Mock explicit keys used in code path.

#### Good mocking practices

1. Mock only boundary dependencies, not the class under test.
2. Keep mocks minimal and behavior-focused.
3. Reset mocks between tests.
4. Assert outcomes first, interactions second.
5. Include negative paths (throws/rejects) explicitly.

#### Common mistakes

1. Over-mocking internal methods of same class (tests implementation details).
2. Reusing stateful mocks across test cases without reset.
3. Mock values that violate real contract shape (false confidence).
4. Writing only happy-path tests.

#### Rule of thumb

Mock to isolate business logic and speed up unit tests. Use integration/e2e tests
to verify real wiring and external contracts.

</details>

<details>
<summary>99. How do you write integration tests in NestJS using TestingModule?</summary>

#### NestJS

Integration tests in NestJS verify that multiple real components work together
(module wiring, DI, repositories/services, pipes/guards), while still being
lighter than full E2E tests.

`TestingModule` is the core tool for assembling test application context.

#### Goal of integration tests

1. Validate interaction between real providers.
2. Catch DI/config/module wiring issues.
3. Test persistence/service flows with realistic dependencies.

#### Typical setup flow

1. Create `TestingModule` with real module(s) under test.
2. Optionally override only external boundaries (e.g., third-party API).
3. Initialize app/module context.
4. Prepare test data.
5. Execute scenario and assert side effects/results.

#### Example using `TestingModule` + repository/service

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

#### What to use as dependencies

1. Prefer real DB in isolated test environment (test container/in-memory DB where
   acceptable).
2. Mock only unstable/expensive external systems (payment gateways, SaaS APIs).
3. Keep configuration close to production semantics.

#### Data management strategies

1. Transaction rollback per test (where feasible).
2. Truncate/reset tables between tests.
3. Deterministic test fixtures/builders.

#### Common mistakes

1. Turning integration tests into unit tests by mocking everything.
2. Sharing mutable global state across tests.
3. Depending on production/staging DB accidentally.
4. No cleanup, causing flaky order-dependent tests.

#### Practical rule

Integration tests should validate real module collaboration with minimal mocking.
They are your main safety net against broken wiring and persistence regressions.

</details>

<details>
<summary>100. What is end-to-end (E2E) testing in NestJS, and how does it differ from unit and integration tests?</summary>

#### NestJS

E2E (end-to-end) testing in NestJS verifies complete application behavior through
real public interfaces (usually HTTP), close to how real clients use the system.

It is the highest-confidence test level for API contracts, middleware/guards,
validation, error mapping, and infrastructure wiring.

#### How E2E differs from other test levels

1. **Unit tests**
   Test one class in isolation with mocked dependencies.

2. **Integration tests**
   Test collaboration of several real components/modules.

3. **E2E tests**
   Test full request -> framework pipeline -> business logic -> persistence ->
   response path.

#### Typical NestJS E2E setup

1. Create testing module with full `AppModule` (or near-full).
2. Bootstrap Nest application instance.
3. Send real HTTP requests (commonly via `supertest`).
4. Assert status codes, response body, and side effects.

#### Minimal E2E example

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

#### What E2E is best at catching

1. Broken route/guard/pipe/interceptor setup.
2. Validation and serialization mismatches.
3. Auth flow regressions.
4. Real API contract drift.
5. Global error handling and response-shape issues.

#### Common pitfalls

1. Relying only on E2E (too slow for full logic coverage).
2. Running against shared non-isolated environments.
3. Unstable test data setup/cleanup causing flaky tests.
4. Overly broad E2E suite that becomes slow and hard to maintain.

#### Practical testing pyramid

1. Many unit tests (fast logic confidence).
2. Some integration tests (wiring confidence).
3. Fewer high-value E2E tests (contract confidence).

#### Rule of thumb

Use E2E tests to protect critical user/business journeys and external API
contracts; use lower-level tests for depth and speed.

</details>

<details>
<summary>101. What is Nest CLI and which commands are used most often?</summary>

#### NestJS

Nest CLI is the official command-line tool for creating, generating, running, and
maintaining NestJS applications.

It standardizes project scaffolding and accelerates day-to-day development.

#### What Nest CLI is used for

1. Create new projects with recommended structure.
2. Generate modules/controllers/services/resources quickly.
3. Run app in dev/watch mode.
4. Build production bundles.
5. Run tests via configured scripts/tooling.

#### Most commonly used commands

1. **Create app**
   `nest new my-app`

2. **Run in development**
   `npm run start:dev`
   (or `nest start --watch` depending on setup)

3. **Build app**
   `npm run build`
   (or `nest build`)

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

#### Useful command aliases

1. `nest generate` -> `nest g`
2. `nest controller` -> `nest g co`
3. `nest service` -> `nest g s`
4. `nest module` -> `nest g mo`

#### Practical workflow example

1. `nest g resource orders`
2. Implement domain/use-case logic.
3. `npm run start:dev` for local iteration.
4. `npm run test` and `npm run test:e2e`.
5. `npm run build` before release.

#### Best practices

1. Use CLI generators to keep structure consistent across team.
2. Review generated code and remove unused boilerplate.
3. Prefer explicit architectural boundaries over blindly generated layering.
4. Keep scripts in `package.json` aligned with team CI workflow.

#### Rule of thumb

Nest CLI is a productivity tool, not architecture. Use it to scaffold fast, then
shape the codebase according to your domain and quality standards.

</details>

<details>
<summary>102. How do you properly organize a Dockerfile for a NestJS application (multi-stage build)?</summary>

#### NestJS

A proper multi-stage Dockerfile for NestJS separates build-time dependencies from
runtime image, resulting in smaller, safer, and faster production containers.

#### Why multi-stage build is important

1. Smaller final image size.
2. Reduced attack surface (no dev/build tooling in runtime).
3. Faster deploy/pull times.
4. Cleaner dependency boundaries.

#### Recommended multi-stage structure

1. **deps stage**
   Install dependencies with lockfile.

2. **build stage**
   Compile TypeScript -> `dist`.

3. **runtime stage**
   Copy only compiled output + production deps.

#### Example Dockerfile

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

#### Recommended `.dockerignore`

1. `node_modules`
2. `dist`
3. `.git`
4. `coverage`
5. local env files not required in build context

#### Security and runtime best practices

1. Run as non-root user where possible.
2. Pin Node major version and keep base images updated.
3. Inject config via environment/secret manager, not baked files.
4. Use health checks and graceful shutdown support.
5. Scan image for vulnerabilities in CI.

#### Build performance tips

1. Copy lockfiles early for layer caching.
2. Avoid invalidating dependency layer with frequent source-only changes.
3. Use deterministic installs (`npm ci`).

#### Common mistakes

1. Single-stage image with full dev dependencies.
2. Shipping source and build tools in runtime image.
3. Copying whole context before dependency install (breaks cache efficiency).
4. Storing secrets in Dockerfile or committed `.env`.

#### Rule of thumb

Build heavy in earlier stages, run lean in final stage. Production container
should contain only what is needed to execute `dist/main.js`.

</details>
