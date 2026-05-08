**Read in other languages: [English 🇺🇸](README.en.md),
[Polska 🇵🇱](README.pl.md), [German 🇩🇪](README.de.md), [French 🇫🇷](README.fr.md),
[Spanish 🇪🇸](README.es.md), [Українська 🇺🇦](README.md).**

<h1>
  NestJS <img src="./assets/nestjs.svg" width="40" height="40" alt="NestJS logo"/>
</h1>

<h2>Preguntas y respuestas más populares de entrevista sobre NestJS</h2>

<details>
<summary>1. ¿Qué es NestJS y qué problemas resuelve?</summary>

#### NestJS

NestJS es un framework progresivo de Node.js para construir aplicaciones del lado
servidor. Está construido con TypeScript por defecto y usa ideas arquitectónicas
familiares de Angular (módulos, inyección de dependencias, decoradores), mientras
se ejecuta sobre adaptadores HTTP como Express o Fastify.

#### Qué resuelve NestJS

1. **Falta de estructura en apps Node.js que crecen**
   NestJS impone límites modulares claros (`@Module`), haciendo que bases de código
   grandes sean más fáciles de escalar y mantener.

2. **Dependencias difíciles de gestionar**
   La **Inyección de Dependencias (DI)** integrada reduce el acoplamiento fuerte
   entre clases y mejora la capacidad de prueba.

3. **Boilerplate en preocupaciones transversales**
   Guards, Pipes, Interceptors, Filters y Middleware proporcionan patrones
   consistentes para auth, validación, transformación, logging y manejo de errores.

4. **Arquitectura inconsistente entre equipos**
   NestJS ofrece convenciones opinadas, para que los equipos construyan servicios
   con el mismo modelo mental y una estructura de proyecto predecible.

5. **Configuración de testing compleja**
   Las utilidades de testing (`@nestjs/testing`) y el diseño amigable con DI
   simplifican testing unitario, de integración y e2e.

6. **Necesidad de soporte backend multi-transporte**
   NestJS soporta HTTP REST, GraphQL, WebSockets y microservicios (TCP, Redis,
   NATS, Kafka, gRPC, etc.) con un modelo de programación unificado.

#### En resumen

NestJS te ayuda a pasar de “código Node.js que solo funciona” a una
**arquitectura backend bien estructurada y lista para entorno enterprise**,
con fuerte mantenibilidad, testabilidad y escalabilidad de equipo.

</details>

<details>
<summary>2. ¿En qué se diferencia NestJS de Express y Fastify?</summary>

#### NestJS

NestJS, Express y Fastify están relacionados, pero sirven a niveles de abstracción
distintos.

#### Diferencia principal

1. **Express / Fastify** son frameworks de servidor HTTP.
2. **NestJS** es un framework de aplicación que puede ejecutarse sobre Express o
   Fastify mediante adaptadores.

#### Arquitectura y modelo de desarrollo

1. **Express**
   Minimalista y sin opiniones fuertes. Tú defines manualmente estructura,
   patrones de DI, validación y convenciones.

2. **Fastify**
   También relativamente de bajo nivel, pero optimizado para rendimiento con un
   ecosistema de plugins y enfoque schema-first.

3. **NestJS**
   Arquitectura opinada desde el inicio: módulos, providers, controllers,
   inyección de dependencias, lifecycle hooks y pipeline de request estandarizado.

#### Perspectiva de rendimiento

1. **Fastify** suele ser más rápido que Express en throughput HTTP bruto.
2. **NestJS con adaptador Fastify** normalmente da mejor rendimiento que NestJS
   sobre Express.
3. En la mayoría de sistemas de negocio, arquitectura, mantenibilidad y velocidad
   del equipo suelen importar más que diferencias de micro-benchmark.

#### Comparación de características en la práctica

1. **Inyección de Dependencias**
   Nativa en NestJS; manual o de terceros en Express/Fastify.

2. **Ergonomía de testing**
   NestJS tiene patrones integrados de módulo de testing; frameworks de bajo nivel
   requieren más configuración personalizada.

3. **Escalabilidad de la base de código**
   Las convenciones de NestJS reducen el caos en equipos/proyectos grandes.

4. **Alcance del ecosistema**
   NestJS unifica REST, GraphQL, WebSockets y microservicios bajo un solo modelo
   mental.

#### Cuándo elegir cada uno

1. Elige **Express** para servicios muy pequeños/simples o compatibilidad legacy.
2. Elige **Fastify** cuando throughput máximo y bajo overhead sean objetivos primarios.
3. Elige **NestJS** cuando necesites mantenibilidad a largo plazo, arquitectura
   clara y productividad de equipo consistente.

#### En resumen

Express/Fastify te dan bloques HTTP flexibles.
NestJS te da un marco arquitectónico completo encima de ellos para construir
backends complejos y mantenibles.

</details>

<details>
<summary>3. ¿Cuáles son los bloques de construcción principales de NestJS?</summary>

#### NestJS

NestJS está compuesto por varios bloques base que definen la arquitectura de la
aplicación, el comportamiento en runtime y el flujo de requests.

#### Bloques de construcción principales

1. **Módulos (`@Module`)**
   La unidad organizativa de nivel superior. Un módulo agrupa controllers y
   providers relacionados, y controla visibilidad con `imports` / `exports`.

2. **Controllers (`@Controller`)**
   Manejan requests entrantes y devuelven respuestas. Decoradores de ruta como
   `@Get()`, `@Post()`, `@Patch()` mapean handlers a endpoints.

3. **Providers (`@Injectable`)**
   Clases gestionadas por el contenedor DI de Nest (services, repositories,
   factories, helpers). Encapsulan lógica de negocio y pueden inyectarse en otras clases.

4. **Contenedor de Inyección de Dependencias (DI)**
   Resuelve dependencias de providers usando tokens, scopes y límites de módulo.
   Esta es la base de un diseño desacoplado en NestJS.

#### Componentes del ciclo de vida de la request

1. **Middleware**
   Se ejecuta antes de los route handlers. Útil para preprocesamiento de bajo nivel
   (por ejemplo logging, headers, bootstrap del contexto de request).

2. **Guards (`CanActivate`)**
   Deciden si una request puede continuar (puerta de auth/authz).

3. **Pipes (`PipeTransform`)**
   Transforman y validan datos entrantes (validación DTO, parsing, normalización).

4. **Interceptors (`NestInterceptor`)**
   Envuelven la ejecución del handler para preocupaciones transversales
   (mapeo de respuesta, timing, caché, tracing, lógica de retry).

5. **Exception Filters (`ExceptionFilter`)**
   Manejo centralizado de errores y forma de respuesta para excepciones lanzadas.

#### Otros bloques clave del framework

1. **Decoradores**
   Metadatos declarativos para rutas, inyección, validación y guards.

2. **Lifecycle hooks**
   Hooks como `OnModuleInit`, `OnApplicationBootstrap`, `OnModuleDestroy`
   para controlar inicialización y apagado.

3. **Adapters de plataforma**
   Nest abstrae la capa HTTP vía adapters (Express o Fastify), permitiendo cambiar
   motor sin reescribir la arquitectura de app.

#### En resumen

NestJS proporciona bloques composables y bien definidos (módulos, controllers,
providers + pipeline request) que ayudan a construir backends mantenibles,
testables y escalables.

</details>

<details>
<summary>4. ¿Cuál es el rol de TypeScript en NestJS y por qué es importante el modo estricto?</summary>

#### NestJS

TypeScript es un pilar central de diseño en NestJS, no solo un complemento opcional.
Nest usa clases, decoradores, interfaces y patrones DI basados en metadata que
funcionan mejor con tipado fuerte.

#### Rol de TypeScript en NestJS

1. **Arquitectura type-safe**
   Controllers, services, DTOs y repositories se implementan como clases y
   contratos tipados, reduciendo sorpresas en runtime.

2. **Mejor experiencia con Inyección de Dependencias**
   Los tipos en constructores hacen explícitas las dependencias de providers y
   facilitan razonar durante refactors.

3. **Límites API guiados por DTOs**
   Las formas de request/response quedan explícitas mediante clases DTO y mapped
   types, mejorando mantenibilidad y consistencia de API.

4. **Tooling y productividad**
   IntelliSense fuerte, auto-refactors seguros y feedback en compilación aceleran
   el desarrollo del equipo.

5. **Gobernanza escalable de base de código**
   Los contratos de tipos actúan como documentación ejecutable en sistemas grandes.

#### Por qué el modo estricto es importante

1. **Detecta bugs temprano**
   `strictNullChecks`, `noImplicitAny` y chequeos relacionados previenen errores
   comunes antes de producción.

2. **Refactor más seguro**
   En proyectos NestJS grandes, el modo estricto reduce roturas ocultas al mover
   lógica entre módulos/services.

3. **Lógica de dominio más fiable**
   Opcionalidad explícita y unions precisas obligan a manejar edge cases
   deliberadamente.

4. **Mejor consistencia de equipo**
   Reglas estrictas del compilador crean estándares de calidad compartidos.

#### Ajustes strict de alto impacto para NestJS

1. `strict: true`
2. `noImplicitAny: true`
3. `strictNullChecks: true`
4. `noUncheckedIndexedAccess: true`
5. `exactOptionalPropertyTypes: true` (cuando aplique)

#### Recomendación práctica

Si adoptas NestJS para calidad enterprise, evita “aflojar” TypeScript para pasar
más rápido. El costo inicial del tipado estricto se recupera con menos regresiones
y mantenimiento más rápido a largo plazo.

</details>

<details>
<summary>5. ¿Qué son los decoradores en NestJS? Proporciona ejemplos.</summary>

#### NestJS

Los decoradores en NestJS son anotaciones de TypeScript que adjuntan metadata a
clases, métodos, parámetros y propiedades. Nest lee esa metadata en runtime para
configurar routing, inyección de dependencias, validación, autorización y otras
funcionalidades del framework.

#### Por qué importan los decoradores en NestJS

1. **Configuración declarativa**
   Describes comportamiento cerca del código en lugar de mantener grandes archivos
   de configuración externos.

2. **Runtime guiado por metadata**
   Nest usa metadata de decoradores para construir módulos, resolver providers y
   crear el pipeline de request.

3. **Arquitectura consistente**
   Los equipos siguen patrones predecibles en controllers, services y guards.

#### Categorías comunes de decoradores

1. **Decoradores de clase**
   `@Module()`, `@Controller()`, `@Injectable()`

2. **Decoradores de método**
   `@Get()`, `@Post()`, `@UseGuards()`, `@UseInterceptors()`

3. **Decoradores de parámetro**
   `@Param()`, `@Body()`, `@Query()`, `@Headers()`, `@Req()`

4. **Decoradores de inyección en propiedad/constructor**
   `@Inject(TOKEN)` (cuando usas tokens personalizados de provider)

#### Ejemplos

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

#### Conclusión práctica

Los decoradores son una de las razones centrales por las que NestJS se siente
estructurado: hacen explícitas las intenciones arquitectónicas y permiten al
framework conectar componentes automáticamente.

</details>

<details>
<summary>6. ¿Qué es Reflect.metadata y cómo lo usa NestJS internamente?</summary>

#### NestJS

`Reflect.metadata` forma parte del mecanismo de reflexión de metadata usado con
los decoradores de TypeScript (vía el polyfill `reflect-metadata`). Permite
adjuntar metadata estructurada a clases, métodos y parámetros para que los
frameworks inspeccionen esa información en runtime.

En la práctica, NestJS está fuertemente guiado por metadata: los decoradores
escriben metadata, y Nest la lee para construir grafos de dependencias, mapas
de rutas, cadenas de guards/pipes/interceptors y lógica de resolución de parámetros.

#### Concepto en una línea

Los decoradores dicen **qué** hace una clase/método; `Reflect.metadata` permite que
Nest descubra eso en runtime y ejecute el comportamiento correcto.

#### Qué metadata guarda NestJS típicamente

1. **Metadata de inyección de dependencias**
   Qué dependencias necesita un provider (tipos de constructor o tokens custom).

2. **Metadata de routing**
   Path HTTP, método (`GET`, `POST`, etc.) y vínculo handler-endpoint.

3. **Metadata de parámetros**
   Cómo resolver `@Body()`, `@Param()`, `@Query()`, `@Headers()`, etc.

4. **Metadata de composición del pipeline**
   Qué guards, pipes, interceptors y filters están aplicados en clase/método.

#### Ejemplo conceptual

```ts
@Controller('users')
export class UsersController {
  constructor(private readonly usersService: UsersService) {}

  @Get(':id')
  getById(@Param('id') id: string) {
    return this.usersService.findById(id);
  }
}
```

Internamente, Nest usa metadata para responder preguntas como:
1. ¿Cuál es el path base del controller?
2. ¿Qué método HTTP activa `getById`?
3. ¿De dónde sale el parámetro `id`?
4. ¿Qué provider debe inyectarse en el constructor?

#### APIs clave de metadata usadas por NestJS

1. `Reflect.defineMetadata(...)` / `Reflect.metadata(...)`
2. `Reflect.getMetadata(...)`
3. Helpers de Nest (`SetMetadata`, `Reflector`) para metadatos custom en guards/policies.

#### Ejemplo de metadata custom

```ts
export const Roles = (...roles: string[]) => SetMetadata('roles', roles);
```

Luego un guard lee `'roles'` con `Reflector` para aplicar autorización.

#### Por qué esto importa en la práctica

1. Explica por qué NestJS es declarativo y consistente.
2. Ayuda a depurar DI/routing cuando algo “no se conecta”.
3. Permite construir decoradores custom para reglas de dominio transversales.

#### Regla práctica

Si entiendes cómo NestJS escribe y lee metadata, entiendes la base de cómo el
framework “ensambla” tu aplicación detrás de los decoradores.

</details>

<details>
<summary>7. ¿Cómo crear un decorador personalizado en NestJS? (createParamDecorator, SetMetadata)</summary>

#### NestJS

En NestJS, los decoradores personalizados normalmente se crean de dos formas:
1. **`SetMetadata()`** para adjuntar metadata personalizada a rutas/clases.
2. **`createParamDecorator()`** para extraer valores personalizados del contexto de request.

Estos dos patrones cubren la mayoría de casos reales: marcadores de autorización
y parámetros derivados de la request.

#### 1) Decorador de metadata personalizado con `SetMetadata`

Úsalo cuando quieras anotar handlers/clases con datos que Guards o Interceptors
leerán después.

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Uso:

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

Guard lee metadata vía `Reflector`:

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

#### 2) Decorador de parámetro personalizado con `createParamDecorator`

Úsalo cuando quieras firmas de controller limpias y parsing reutilizable de request.

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

Uso:

```ts
@Get('me')
getMe(@CurrentUser() user: any) {
  return user;
}

@Get('email')
getMyEmail(@CurrentUser('email') email: string) {
  return { email };
}
```

#### Cuándo usar cada uno

1. Usa **`SetMetadata`** para anotar reglas/políticas que leerán guards/interceptors.
2. Usa **`createParamDecorator`** para simplificar handlers extrayendo contexto repetido.

#### Buenas prácticas

1. Mantén los decoradores pequeños y orientados a un propósito.
2. Define constantes para claves de metadata (`ROLES_KEY`) para evitar typos.
3. Valida supuestos dentro de guards/pipes, no solo en el decorador.
4. Documenta el contrato del decorador para el equipo.

#### Regla práctica

Si necesitas adjuntar intención para el pipeline -> `SetMetadata`.
Si necesitas inyectar datos de request al handler -> `createParamDecorator`.

</details>

<details>
<summary>8. ¿Qué hace @Injectable() y por qué es necesario?</summary>

#### NestJS

`@Injectable()` marca una clase como provider que puede participar en la
Inyección de Dependencias (DI) de NestJS. En otras palabras, le dice a Nest que
esa clase es gestionada por el contenedor IoC y que puede recibir dependencias
en su constructor.

#### Qué hace `@Injectable()`

1. **Registra metadata de DI**
   Permite que Nest trate la clase como un provider inyectable.

2. **Permite inyección por constructor**
   Nest puede resolver e inyectar dependencias declaradas en el constructor.

3. **Integra con scope/ciclo de vida de providers**
   La clase puede tener scope `DEFAULT`, `REQUEST` o `TRANSIENT` cuando se configura.

4. **Mejora la testabilidad**
   Los servicios inyectables se reemplazan/mockean fácilmente en módulos de testing.

#### Por qué es necesario

1. **Desacoplamiento**
   Los controllers dependen de abstracciones/services en vez de crear dependencias
   manualmente.

2. **Responsabilidad única**
   La lógica de negocio vive en services, no en controllers.

3. **Creación centralizada de objetos**
   El contenedor de Nest controla instanciación, compartición y ciclo de vida.

4. **Arquitectura escalable**
   Los patrones DI se mantienen manejables al crecer la app y el equipo.

#### Ejemplo

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

#### Matiz práctico

`@Injectable()` por sí solo no basta; el provider también debe registrarse en un
módulo (array `providers`) o exportarse/importarse entre límites de módulos para
que Nest lo pueda resolver donde se necesite.

</details>

<details>
<summary>9. ¿Cuál es la diferencia entre los decoradores @Controller y @Get()/@Post()?</summary>

#### NestJS

`@Controller` y los decoradores de método de ruta (`@Get`, `@Post`, etc.)
trabajan juntos, pero resuelven niveles de routing distintos.

#### Diferencia principal

1. **`@Controller()`**
   Declara una clase como controller y define un **prefijo base de ruta** para
   todos los handlers dentro de esa clase.

2. **`@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`**
   Mapean un método específico de clase a un método HTTP + path de ruta.

#### Modelo mental

1. `@Controller('users')` dice: “Todos los endpoints de esta clase empiezan con `/users`.”
2. `@Get(':id')` dice: “Este método maneja `GET /users/:id`.”

#### Ejemplo

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

Rutas resultantes:
1. `GET /users`
2. `GET /users/:id`
3. `POST /users`

#### Por qué esta separación es útil

1. **Estructura API clara**
   La clase agrupa endpoints relacionados por dominio/recurso.

2. **Configuración reutilizable a nivel controller**
   Guards, interceptors, versionado y prefijos se pueden aplicar a nivel clase.

3. **Capa de routing legible**
   El prefijo vive en `@Controller`; la intención HTTP vive en decoradores de método.

#### Regla práctica

Piensa en `@Controller` como el “namespace de recurso”, y en `@Get/@Post/...`
como las operaciones concretas dentro de ese namespace.

</details>

<details>
<summary>10. ¿Cómo maneja NestJS las solicitudes HTTP y determina qué controller llamar?</summary>

#### NestJS

NestJS determina el controller y handler objetivo a través de metadata recopilada
de los decoradores durante el bootstrap de la aplicación, y luego ejecuta la
request a través de un pipeline definido.

#### Cómo se construye el routing al iniciar

1. **Escaneo de módulos**
   Nest escanea módulos importados y descubre controllers/providers registrados.

2. **Recolección de metadata de rutas**
   `@Controller()` aporta el path base; `@Get/@Post/...` aportan método HTTP y
   sub-path.

3. **Registro de rutas en el adapter**
   Nest combina metadata en rutas concretas y las registra en el router de
   Express o Fastify.

#### Qué pasa por cada request entrante

1. La request entra al adapter HTTP subyacente (Express/Fastify).
2. El router hace match de método + URL path con un método de controller.
3. Nest crea un `ExecutionContext` para ese handler.
4. El pipeline de request corre en orden:
   1. Middleware (si está configurado)
   2. Guards (decisión de autorización)
   3. Interceptors (antes del handler)
   4. Pipes (parsing/validación de parámetros)
   5. Ejecución del método del controller
   6. Interceptors (después del handler, mapeo de respuesta)
   7. Exception filters (si se lanzan errores)
5. La respuesta final la devuelve el adapter.

#### Cómo elige Nest el método exacto del controller

1. Match por método HTTP (`GET`, `POST`, etc.).
2. Match por path completo normalizado:
   `globalPrefix + controllerPath + handlerPath`.
3. Si hay versionado habilitado, se evalúan restricciones de versión.
4. Si hay params de ruta (`:id`), se aplica matching por patrón de parámetros.

#### Ejemplo de mapeo

```ts
@Controller('users')
export class UsersController {
  @Get(':id')
  findOne() {}
}
```

Si el prefijo global es `api`, la request `GET /api/users/42` mapea a
`UsersController.findOne`.

#### Conclusión práctica

NestJS no “busca controllers dinámicamente” en cada request. Precalcula el mapa
de routing en bootstrap y luego ejecuta un ciclo de vida de request predecible
alrededor del handler que hizo match.

</details>

<details>
<summary>11. ¿Cómo usa NestJS los decoradores para construir la capa de routing?</summary>

#### NestJS

El routing en NestJS está guiado por metadata. Los decoradores anotan clases y
métodos, y Nest lee esa metadata durante el bootstrap para crear un mapa de rutas
concreto en el adapter HTTP subyacente.

#### Fuentes de metadata de routing

1. **`@Controller('path')`**
   Define el prefijo base de ruta para una clase.

2. **Decoradores de método** (`@Get`, `@Post`, `@Patch`, etc.)
   Definen el método HTTP y subruta para un handler específico.

3. **Decoradores de parámetro** (`@Param`, `@Body`, `@Query`, etc.)
   Definen cómo extraer y transformar datos de la request.

4. **Decoradores adicionales de pipeline**
   `@UseGuards`, `@UsePipes`, `@UseInterceptors`, `@Version`, etc., adjuntan
   metadata extra al comportamiento de esa ruta.

#### Qué hace Nest internamente

1. Escanea módulos para descubrir controllers.
2. Lee metadata de controller + métodos.
3. Compone ruta final:
   `globalPrefix + controllerPath + handlerPath`.
4. Registra handlers en el router de Express/Fastify.
5. Prepara contexto de ejecución para aplicar guards/pipes/interceptors/filters
   cuando esa ruta reciba tráfico.

#### Ejemplo

```ts
@Controller('users')
export class UsersController {
  @Get(':id')
  findOne(@Param('id') id: string) {
    return { id };
  }

  @Post()
  create(@Body() dto: { email: string }) {
    return dto;
  }
}
```

Nest construye algo como:
1. `GET /users/:id` -> `UsersController.findOne`
2. `POST /users` -> `UsersController.create`

#### Por qué este enfoque es poderoso

1. **Declarativo**
   La intención de routing vive junto al código del handler.

2. **Componible**
   Puedes mezclar metadata de routing, auth, validación y versionado en un mismo
   punto.

3. **Escalable**
   El framework mantiene una estructura consistente incluso en bases de código grandes.

#### Regla práctica

En NestJS, los decoradores no son “solo sintaxis”: son la fuente de verdad para
el runtime de routing y request pipeline.

</details>

<details>
<summary>12. ¿Cuál es la diferencia entre imports, exports, providers y declarations en @Module?</summary>

#### NestJS

En módulos de NestJS, `imports`, `providers` y `exports` son los límites centrales
de visibilidad y dependencias. `declarations` **no** es un campo de módulo de
NestJS (es un concepto de Angular), por lo que usarlo en `@Module()` es incorrecto.

#### Campos correctos del módulo

1. **`providers`**
   Clases/factories/values creados en el contexto DI de este módulo.
   Están disponibles dentro del mismo módulo por defecto.

2. **`imports`**
   Otros módulos cuyos **providers exportados** quieres usar en este módulo.
   Importar un módulo no expone todos sus providers, solo los exportados.

3. **`exports`**
   Subconjunto de providers de este módulo (o módulos re-exportados) que deben
   ser visibles para módulos que importen este módulo.

4. **`controllers`**
   Route handlers pertenecientes a este módulo (capa HTTP). No se exportan como
   providers inyectables por defecto.

#### Sobre `declarations`

1. `declarations` se usa en Angular NgModules para components/directives/pipes.
2. `@Module()` de NestJS **no** soporta `declarations`.
3. Los análogos en NestJS son principalmente `controllers` + `providers`, según el rol.

#### Ejemplo

```ts
import { Module } from '@nestjs/common';

@Module({
  providers: [UsersService],     // creado en el contexto de UsersModule
  exports: [UsersService],       // disponible para módulos importadores
})
export class UsersModule {}

@Module({
  imports: [UsersModule],        // ahora puede inyectar UsersService exportado
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Regla práctica

1. Pon clases service/repository/factory en `providers`.
2. Pon route handlers en `controllers`.
3. Pon módulos externos necesarios en `imports`.
4. Pon solo la superficie reutilizable en `exports` (evita sobre-exportar).

</details>

<details>
<summary>13. ¿Cuál es la diferencia entre @Module imports y @Module providers?</summary>

#### NestJS

`imports` y `providers` en `@Module()` resuelven preocupaciones DI distintas:
1. `imports` conecta módulos.
2. `providers` define qué crea este módulo en su propio scope DI.

#### `providers`: definiciones locales

1. Declara services/factories/values instanciados en el contexto de este módulo.
2. Están disponibles para inyección dentro de este módulo.
3. No son visibles para otros módulos salvo que se exporten explícitamente.

Ejemplo:

```ts
@Module({
  providers: [UsersService],
})
export class UsersModule {}
```

#### `imports`: dependencias externas

1. Trae otros módulos para consumir sus providers **exportados**.
2. No copia todos los internos del módulo importado.
3. Crea un grafo explícito de dependencias entre módulos.

Ejemplo:

```ts
@Module({
  imports: [UsersModule], // solo puede inyectar lo que UsersModule exporta
  providers: [OrdersService],
})
export class OrdersModule {}
```

#### Diferencia conceptual

1. `providers` responde: **“¿Qué objetos gestiona este módulo?”**
2. `imports` responde: **“¿De qué otros módulos depende este módulo?”**

#### Error común

Poner un service en `imports` en lugar de en `providers`.
En NestJS, `imports` acepta **módulos**, no clases de provider sueltas.

#### Regla práctica

1. Si el módulo **posee/crea** un service -> va en `providers`.
2. Si el módulo **consume** un service de otro módulo -> ese módulo va en `imports`, y el service debe estar en `exports` del módulo proveedor.

</details>

<details>
<summary>14. ¿Qué son los módulos dinámicos y cuándo deberías usarlos?</summary>

#### NestJS

Los módulos dinámicos son módulos cuya configuración se produce en runtime vía
métodos factory estáticos (normalmente `forRoot`, `forRootAsync`, `register`,
`registerAsync`). Te permiten construir módulos reutilizables que pueden
configurarse de forma distinta según app/entorno.

#### Por qué existen los módulos dinámicos

1. **Configuración en runtime**
   Pasar opciones (URLs, API keys, feature flags, elecciones de estrategia)
   al importar un módulo.

2. **Módulos de librería reutilizables**
   Empaquetar un módulo consumible por muchas apps con settings distintos.

3. **Inicialización asíncrona**
   Resolver config desde `ConfigService`, secret managers o fuentes remotas.

4. **Providers condicionales**
   Crear providers según opciones (por ejemplo Redis vs caché en memoria).

#### Patrones API típicos

1. `forRoot(options)` para configuración singleton global.
2. `forRootAsync({...})` cuando la config depende de factories async/deps inyectadas.
3. `register(options)` para configuración por feature/por import.

#### Ejemplo

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

Uso:

```ts
@Module({
  imports: [
    MailModule.forRoot({
      host: process.env.MAIL_HOST!,
      apiKey: process.env.MAIL_API_KEY!,
    }),
  ],
})
export class AppModule {}
```

#### Cuándo deberías usar módulos dinámicos

1. Al construir infraestructura configurable (mail, cache, auth, db clients).
2. Cuando el mismo módulo necesita configuraciones diferentes por entorno.
3. Al publicar módulos compartidos para varios servicios.

#### Cuándo evitarlos

1. Módulos de dominio simples sin necesidades de configuración.
2. Cuando la configuración es fija y puede residir en providers normales.
3. Si la complejidad adicional no aporta reutilización real.

#### Regla práctica

Usa módulos dinámicos para **infraestructura reusable + configurable**.
Para lógica de negocio local/simple, prefiere módulos estáticos normales.

</details>

<details>
<summary>15. ¿Cuál es la diferencia entre tipos de provider en NestJS? (useClass, useValue, useFactory)</summary>

#### NestJS

Los providers en NestJS pueden registrarse con estrategias distintas según cómo
se deba crear una instancia/valor. Las más comunes son `useClass`, `useValue` y
`useFactory`.

#### 1) `useClass`

Crea una instancia de una clase mediante DI de Nest.

1. Mejor para implementaciones estándar de services.
2. Soporta inyección por constructor automáticamente.
3. Útil para intercambiar implementaciones por entorno.

```ts
{
  provide: PaymentPort,
  useClass: StripePaymentService,
}
```

#### 2) `useValue`

Vincula un token a un valor/objeto/constante ya listo.

1. Nest no instancia nada aquí.
2. Ideal para objetos de config, singletons SDK, mocks en tests.
3. Rápido y simple, pero sin ciclo de vida DI para ese valor.

```ts
{
  provide: 'APP_CONFIG',
  useValue: { region: 'eu', retries: 3 },
}
```

#### 3) `useFactory`

Crea el valor del provider mediante una función factory.

1. Puede construir objetos dinámicamente.
2. Puede inyectar otros providers en la factory (array `inject`).
3. Funciona para inicialización sync y async.

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

#### Comparación rápida

1. **`useClass`**: “Instancia esta clase con DI.”
2. **`useValue`**: “Usa exactamente este valor tal cual.”
3. **`useFactory`**: “Construye el valor con lógica custom (y deps inyectadas opcionales).”

#### Cuándo elegir cada uno

1. Elige `useClass` para services normales de app e implementaciones polimórficas.
2. Elige `useValue` para constantes, instancias de terceros y test doubles.
3. Elige `useFactory` para construcción condicional/async y setup complejo.

#### Regla práctica

Si solo necesitas “esta clase”, usa `useClass`.
Si ya tienes el objeto, usa `useValue`.
Si necesitas lógica de construcción, usa `useFactory`.

</details>

<details>
<summary>16. ¿Qué es el scope de provider? (DEFAULT, REQUEST, TRANSIENT)</summary>

#### NestJS

El scope de provider en NestJS define **cuánto vive una instancia de provider** y
**con qué frecuencia el contenedor DI crea nuevas instancias**.

#### Tipos de scope

1. **`DEFAULT` (singleton)**
   Una instancia compartida para todo el ciclo de vida de la aplicación.

2. **`REQUEST`**
   Nueva instancia por cada request entrante (contexto HTTP/RPC/mensaje).

3. **`TRANSIENT`**
   Nueva instancia cada vez que el provider se inyecta/se resuelve.

#### 1) Scope `DEFAULT`

1. El más performante y el más común.
2. Ideal para services stateless (lógica de negocio, repositories, mappers).
3. Estado compartido dentro de ese service es global para el proceso de app.

```ts
@Injectable()
export class UsersService {}
```

#### 2) Scope `REQUEST`

1. Úsalo cuando el service debe ser request-aware (tenant, correlation ID,
   caché por request, contexto de usuario).
2. Incrementa el overhead de creación de objetos.
3. Si un singleton depende de un provider request-scoped, el grafo de
   dependencias puede requerir ajustes de propagación de scope.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.REQUEST })
export class RequestContextService {}
```

#### 3) Scope `TRANSIENT`

1. Instancia fresca en cada punto de inyección.
2. Útil para helpers ligeros con estado, donde no conviene compartir instancia.
3. Puede ser costoso si se sobreusa en grafos de objetos profundos.

```ts
import { Injectable, Scope } from '@nestjs/common';

@Injectable({ scope: Scope.TRANSIENT })
export class AuditBuilder {}
```

#### Guía práctica de decisión

1. Empieza con `DEFAULT`.
2. Pasa a `REQUEST` solo si hay requerimientos reales de estado por request.
3. Usa `TRANSIENT` para objetos helper mutables de alcance acotado.

#### Nota de performance y arquitectura

El scope es una elección de corrección y rendimiento. Sobreusar scopes no
singleton puede aumentar latencia y churn de memoria, así que aplícalos
intencionalmente.

</details>

<details>
<summary>17. ¿Cómo manejar dependencias circulares (forwardRef) en sistemas grandes?</summary>

#### NestJS

Las dependencias circulares aparecen cuando dos providers/módulos dependen entre
sí, de forma directa o en cadena. En NestJS, la corrección de primera línea es
el desacoplamiento arquitectónico; `forwardRef()` es una herramienta táctica
cuando no es posible refactorizar de inmediato.

#### Por qué las dependencias circulares son riesgosas

1. Acoplamiento fuerte entre dominios.
2. Testing y refactor más difíciles.
3. Límites de ownership poco claros.
4. Complejidad en bootstrap/resolución DI.

#### Estrategia preferida: eliminar el ciclo

1. **Extraer lógica compartida**
   Mover comportamiento común a un tercer service/módulo (`SharedDomainService`).

2. **Invertir dependencia con puertos/interfaces**
   Depender de abstracciones/tokens en vez de clases concretas.

3. **Comunicación orientada a eventos**
   Sustituir llamadas sync directas por eventos internos o jobs de cola cuando tenga sentido.

4. **Rediseñar límites de módulo**
   Alinear módulos por bounded contexts, no por conveniencia técnica.

#### Cuándo usar `forwardRef()`

Úsalo cuando:
1. El ciclo es conocido y temporal.
2. Un refactor completo no cabe en este sprint.
3. Necesitas mantener la app operativa mientras migras arquitectura.

No debería ser la solución por defecto en diseño nuevo.

#### Ejemplo provider-level

```ts
import { Inject, Injectable, forwardRef } from '@nestjs/common';

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

#### Ejemplo module-level

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

#### Patrones más seguros en sistemas grandes

1. Introducir una capa application/orchestration para coordinar ambos lados.
2. Mantener servicios de dominio unidireccionales cuando sea posible.
3. Usar contratos explícitos (tokens/interfaces) por frontera.
4. Añadir tests arquitectónicos/lint rules para detectar nuevos ciclos temprano.

#### Regla práctica

`forwardRef()` resuelve el síntoma DI; no resuelve el problema de acoplamiento.
Trátalo como puente temporal y paga la deuda arquitectónica cuanto antes.

</details>

<details>
<summary>18. ¿Cómo estructuras una aplicación NestJS escalable?</summary>

#### NestJS

Una aplicación NestJS escalable se estructura alrededor de límites de dominio claros,
dirección correcta de dependencias y patrones transversales predecibles.

#### Principios estructurales clave

1. **Modular por dominio (bounded contexts)**
   Divide por capacidades de negocio (`Users`, `Billing`, `Orders`), no solo por
   capas técnicas.

2. **Responsabilidades por capas dentro de cada módulo**
   Mantén controllers livianos, services enfocados en orquestación y adapters de
   infraestructura aislados.

3. **Regla de dependencias**
   La lógica de negocio de alto nivel no debe depender directamente de detalles del
   framework o de infraestructura.

4. **Contratos explícitos**
   Usa DTOs, esquemas de validación e interfaces/tokens en los límites.

#### Estructura práctica de módulos (ejemplo)

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

#### Patrones arquitectónicos que escalan

1. **Feature modules + shared kernel**
   Mantén utilidades compartidas al mínimo para evitar un "god common module".

2. **Ports and adapters**
   La capa de negocio depende de abstracciones; los adapters implementan detalles
   de DB/API/message-bus.

3. **CQRS cuando la complejidad lo justifique**
   Separa modelos de escritura/lectura en dominios complejos, no por defecto en
   todas partes.

4. **Límites asíncronos**
   Usa eventos/colas para flujos entre módulos y consistencia eventual.

#### Aspectos de escalabilidad operativa

1. **Gestión de configuración**
   Configuración tipada centralizada con validación de entorno.

2. **Observabilidad**
   Logging estructurado, tracing, métricas y correlation IDs.

3. **Estrategia de errores**
   Exception filters globales + mapeo de errores específico del dominio.

4. **Rendimiento**
   Caché, paginación, backpressure, indexación de DB y evitar sobreuso de
   request-scope.

#### Prácticas para escalar equipos

1. Aplicar puertas de lint/format/type/test en CI.
2. Mantener clara la ownership de módulos (codeowners o mapa de ownership).
3. Revisar decisiones arquitectónicas (ADR) para nuevas dependencias cross-domain.
4. Preferir refactor incremental en lugar de reescrituras big-bang.

#### Conclusión

La escalabilidad en NestJS es principalmente disciplina arquitectónica:
módulos orientados al dominio, dependencias controladas y preocupaciones de
plataforma estandarizadas alrededor de ellos.

</details>

<details>
<summary>19. ¿Cómo diseñas una API REST con una separación correcta de responsabilidades?</summary>

#### NestJS

Una separación correcta de responsabilidades en una API REST con NestJS significa
que cada capa tiene una única responsabilidad clara y las dependencias fluyen en
una sola dirección.

#### División recomendada de responsabilidades

1. **Capa controller (transporte)**
   Maneja solo aspectos HTTP: routing, códigos de estado, mapeo request/response,
   decoradores de auth y binding de entrada.

2. **Capa application/service (casos de uso)**
   Orquesta flujos de negocio y transacciones; sin lógica específica de HTTP.

3. **Capa domain (reglas de negocio)**
   Encapsula reglas centrales, invariantes, entidades/value objects y servicios de dominio.

4. **Capa infrastructure**
   Implementa persistencia, APIs externas, colas y otros adapters.

#### Qué NO debe mezclarse

1. Consultas de base de datos en controllers.
2. Objetos HTTP (`Request`, `Response`) dentro de la lógica de dominio.
3. Validación/invariantes de negocio dispersas en varias capas.
4. Detalles de SDKs externos filtrándose en contratos de casos de uso.

#### Flujo práctico

1. El controller recibe DTO (`@Body`, `@Query`, `@Param`).
2. Un pipe valida/transforma el DTO.
3. El controller llama a un método del application service.
4. El service usa repositories/ports y reglas de dominio.
5. El service devuelve el modelo de resultado.
6. El controller mapea el resultado a response DTO/view model.

#### Esqueleto de ejemplo

```ts
// controller
@Post()
create(@Body() dto: CreateOrderDto): Promise<OrderView> {
  return this.ordersAppService.createOrder(dto);
}

// application service
async createOrder(dto: CreateOrderDto): Promise<OrderView> {
  const order = Order.create(dto.customerId, dto.items); // regla de dominio
  await this.ordersRepo.save(order);                     // puerto de infraestructura
  return OrderView.from(order);                          // mapeo de salida
}
```

#### Técnicas de diseño que ayudan

1. **DTOs para contratos de API**
   Separa contratos de entrada/salida de las entidades internas.

2. **Interfaces de repository/port**
   Depende de abstracciones, no de clientes ORM directos en la capa de negocio.

3. **Componentes transversales globales**
   Usa guards/pipes/interceptors/filters para auth, validación, logging y errores.

4. **Versionado e idempotencia**
   Aplica estrategia de versionado de API y claves de idempotencia para operaciones no seguras.

5. **Modelo de error consistente**
   Mapea errores de dominio/infraestructura a respuestas HTTP estables de tipo problem.

#### Resultado

Con esta separación, tu API es más fácil de testear, refactorizar y escalar: los
cambios de transporte no rompen la lógica de dominio, y la infraestructura puede
evolucionar de forma independiente.

</details>

<details>
<summary>20. ¿Cuál es el ciclo de vida completo de una solicitud en NestJS?</summary>

#### NestJS

El ciclo de vida de una solicitud en NestJS es un pipeline determinista alrededor
de un route handler ya encontrado. Entender este orden es crítico para depurar
comportamientos de auth, validación y modelado de respuesta.

#### Secuencia de alto nivel

1. La solicitud entrante llega al platform adapter (Express/Fastify).
2. La ruta se asigna a un método de controller.
3. Nest ejecuta componentes del pipeline del framework en orden definido.
4. Se devuelve la respuesta (o una excepción es manejada por filters).

#### Orden detallado del ciclo de vida

1. **Middleware**
   Se ejecuta antes de los guards; se usa para preprocesamiento de bajo nivel
   (logging, correlation ID, manipulación de headers raw, etc.).

2. **Guards**
   Deciden si la ejecución está permitida (`canActivate`).
   Si un guard devuelve `false`/lanza error, la solicitud se detiene aquí.

3. **Interceptors (antes del handler)**
   Envuelven la ejecución; pueden iniciar timers, adjuntar contexto o
   short-circuit de comportamiento.

4. **Pipes**
   Se ejecutan sobre argumentos de ruta para transformar/validar datos entrantes
   (`@Body`, `@Param`, `@Query`, params personalizados).

5. **Controller handler**
   Se invoca el caso de uso de negocio (normalmente delegando a la capa service).

6. **Interceptors (después del handler)**
   Pueden mapear/stream/cache respuestas y finalizar lógica de observabilidad.

7. **Exception filters**
   Capturan excepciones no manejadas y las convierten en respuestas HTTP.

#### Modelo visual de ejecución

1. Middleware -> Guards -> Interceptors (pre) -> Pipes -> Handler ->
   Interceptors (post) -> Response
2. Cualquier error lanzado en pipeline/handler -> Exception Filters

#### Notas sobre alcance y precedencia

1. La mayoría de componentes del pipeline se pueden aplicar a:
   1. Nivel global
   2. Nivel controller
   3. Nivel route-handler
2. Nest combina estos niveles; la config de ruta suele ser la más específica.

#### Conclusión práctica para depuración

Si el comportamiento es inesperado:
1. Primero verifica si un guard bloquea la solicitud.
2. Verifica transformación/validación de pipes en parámetros.
3. Revisa la cadena de interceptors para cambios de mapeo de respuesta.
4. Confirma el formato del exception filter para errores lanzados.

Conocer este orden evita supuestos de "magia" y acelera mucho el diagnóstico de
incidentes en producción.

</details>

<details>
<summary>21. ¿Cuál es la diferencia entre Middleware, Guards, Pipes e Interceptors?</summary>

#### NestJS

Estos cuatro componentes pertenecen a diferentes etapas del pipeline de NestJS
y resuelven problemas distintos. Elegir el componente correcto evita acoplamiento
y código difícil de mantener.

#### Diferencias por responsabilidad

1. **Middleware**
   Se ejecuta al inicio de la solicitud (antes de guards).
   Ideal para tareas de bajo nivel HTTP: logging, correlation IDs, parsing adicional,
   manipulación de headers, etc.

2. **Guards**
   Deciden si la solicitud puede continuar (`canActivate`).
   Principal caso de uso: autenticación y autorización (roles/policies).

3. **Pipes**
   Transforman y validan datos de entrada para parámetros del handler
   (`@Body`, `@Param`, `@Query`).
   Si la validación falla, lanzan una excepción.

4. **Interceptors**
   Envuelven la ejecución del handler (antes y después).
   Útiles para response mapping, caching, métricas, tracing, timeout y
   estandarización del formato de salida.

#### Regla rápida de decisión

1. ¿Necesitas preprocesamiento HTTP general antes de auth? -> `Middleware`
2. ¿Necesitas permitir/bloquear acceso? -> `Guard`
3. ¿Necesitas validar/transformar input del endpoint? -> `Pipe`
4. ¿Necesitas envolver ejecución o modificar output? -> `Interceptor`

#### Comparación resumida

1. **Momento de ejecución**:
   1. Middleware -> Guard -> Pipe -> Handler -> Interceptor (post)
2. **Conocimiento del contexto Nest**:
   1. Middleware: bajo
   2. Guard/Pipe/Interceptor: alto (ExecutionContext/metadata)
3. **Caso de uso principal**:
   1. Middleware: transporte
   2. Guard: control de acceso
   3. Pipe: saneamiento de entrada
   4. Interceptor: comportamiento transversal alrededor del handler

#### Error común

Poner validación de DTO o lógica de autorización en middleware.
En NestJS eso normalmente debe vivir en pipes y guards, donde hay metadata de
rutas, decorators y contexto de ejecución.

#### Conclusión

Usa cada componente en su capa natural: middleware para transporte, guards para
acceso, pipes para entrada e interceptors para envolver ejecución/respuesta.
Esa separación mantiene la arquitectura limpia y predecible.

</details>

<details>
<summary>22. ¿Cómo aplicar Middleware globalmente frente a una ruta específica?</summary>

#### NestJS

En NestJS, el middleware se configura a nivel de módulo mediante
`NestModule.configure()`. Puedes aplicarlo a todas las rutas o solo a rutas
específicas según path, método HTTP o controller.

#### 1) Aplicación global (todas las rutas)

Usa `forRoutes('*')` o un controller raíz.

```ts
import { MiddlewareConsumer, Module, NestModule, RequestMethod } from '@nestjs/common';

@Module({})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer
      .apply(RequestIdMiddleware, LoggingMiddleware)
      .forRoutes('*');
  }
}
```

#### 2) Aplicación por controller

Aplica middleware a todas las rutas de un controller concreto.

```ts
consumer.apply(AuthAuditMiddleware).forRoutes(UsersController);
```

#### 3) Aplicación por ruta/método específico

Control fino por path + método HTTP.

```ts
consumer
  .apply(AdminMiddleware)
  .forRoutes({ path: 'users/:id', method: RequestMethod.PATCH });
```

#### 4) Excluir rutas

Puedes aplicar middleware de forma amplia y excluir endpoints concretos.

```ts
consumer
  .apply(AuthMiddleware)
  .exclude(
    { path: 'health', method: RequestMethod.GET },
    { path: 'auth/login', method: RequestMethod.POST },
  )
  .forRoutes('*');
```

#### Orden de ejecución

1. Middleware se ejecuta antes de guards/pipes/interceptors.
2. Si aplicas varios, se ejecutan en el orden en que se declaran en `apply(...)`.
3. Middleware declarado en módulos distintos depende del orden de resolución de rutas.

#### Cuándo usar global vs específico

1. **Global**: correlation ID, logging base, seguridad de headers, métricas de entrada.
2. **Específico**: reglas de auditoría por dominio, validaciones transport-level raras,
   lógica que solo aplica a ciertos endpoints.

#### Nota importante

Para casos transversales con conocimiento de metadata de ruta (roles, decorators,
contexto de ejecución), normalmente Guards/Interceptors son mejor opción que middleware.

</details>

<details>
<summary>23. ¿Qué es ExecutionContext y cómo se usa?</summary>

#### NestJS

`ExecutionContext` es un objeto de abstracción que NestJS pasa a guards,
interceptors y filters para describir el contexto actual de ejecución
(HTTP, WebSocket, RPC, GraphQL).

Permite escribir lógica transversal reutilizable sin acoplarla a un único
transporte.

#### Qué información ofrece

1. **Tipo de contexto**: `context.getType()` -> `'http' | 'ws' | 'rpc'` (y GraphQL vía helper).
2. **Target de handler**: `context.getHandler()` -> método actual.
3. **Clase actual**: `context.getClass()` -> controller/resolver.
4. **Cambio de host**:
   1. `switchToHttp().getRequest()/getResponse()`
   2. `switchToWs().getClient()/getData()`
   3. `switchToRpc().getData()/getContext()`

#### Caso de uso típico en Guard

```ts
import { CanActivate, ExecutionContext, Injectable } from '@nestjs/common';

@Injectable()
export class RolesGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const req = context.switchToHttp().getRequest();
    const user = req.user;
    return !!user && user.roles?.includes('admin');
  }
}
```

#### Metadata + Reflector con ExecutionContext

`ExecutionContext` permite obtener `handler` y `class`, que se usan con
`Reflector` para leer metadata de decorators personalizados.

```ts
const roles = this.reflector.getAllAndOverride<string[]>('roles', [
  context.getHandler(),
  context.getClass(),
]);
```

#### En GraphQL

Para GraphQL, se adapta mediante `GqlExecutionContext`:

```ts
const gqlCtx = GqlExecutionContext.create(context);
const { req } = gqlCtx.getContext();
```

#### Cuándo usarlo

1. Control de acceso dependiente de ruta/decorator.
2. Logging/tracing contextual.
3. Políticas multi-transporte (HTTP + WS + RPC).
4. Manejo uniforme de errores con información del handler.

#### Idea clave

`ExecutionContext` es la "vista unificada" del runtime de NestJS.
Si un componente necesita saber *dónde* y *cómo* se está ejecutando, este es
el objeto correcto.

</details>

<details>
<summary>24. ¿Qué es un Guard y en qué se diferencia de Middleware?</summary>

#### NestJS

Un **Guard** en NestJS es un componente que decide si una solicitud puede
continuar hacia un route handler (`canActivate`).

La diferencia principal frente a middleware: el guard trabaja en un nivel más
cercano al framework y conoce metadata de rutas/controllers/decorators.

#### Guard vs Middleware: diferencia conceptual

1. **Middleware**
   Se ejecuta antes en el pipeline y está orientado a transporte HTTP de bajo nivel.
   No está diseñado para reglas de autorización ricas basadas en metadata de ruta.

2. **Guard**
   Se ejecuta después del middleware y antes del handler.
   Tiene acceso a `ExecutionContext`, `getHandler()`, `getClass()` y puede leer
   metadata (`@Roles`, `@Public`, etc.) vía `Reflector`.

#### Cuándo usar cada uno

1. Usa **Middleware** para:
   1. request ID
   2. logging básico de entrada
   3. parsing/mutación técnica de headers/cookies

2. Usa **Guard** para:
   1. autenticación (¿usuario autenticado?)
   2. autorización (¿tiene permisos/rol?)
   3. policy checks por endpoint

#### Ejemplo de Guard

```ts
import { CanActivate, ExecutionContext, Injectable, UnauthorizedException } from '@nestjs/common';

@Injectable()
export class JwtAuthGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const req = context.switchToHttp().getRequest();
    const token = req.headers.authorization;

    if (!token) throw new UnauthorizedException('Missing token');
    return true;
  }
}
```

#### Regla práctica

Si la pregunta es "¿esta persona puede acceder a este endpoint?" -> `Guard`.
Si la pregunta es "¿cómo preprocesar esta solicitud HTTP?" -> `Middleware`.

</details>

<details>
<summary>25. ¿Cómo se integran los Guards con la autorización?</summary>

#### NestJS

En NestJS, los guards son el mecanismo principal para aplicar autorización
a nivel de endpoint. Se ejecutan antes del handler y pueden permitir o bloquear
la ejecución según identidad, roles o políticas.

#### Flujo típico de autorización con Guards

1. Un guard de autenticación valida credenciales (por ejemplo, JWT) y adjunta
   `user` al request.
2. Un guard de autorización lee metadata del endpoint (`@Roles`, `@Permissions`,
   `@Policy`) usando `Reflector`.
3. Compara claims del usuario con los requisitos del endpoint.
4. Si no cumple, devuelve `false` o lanza `ForbiddenException`.

#### Metadata + Reflector (patrón común)

Decorator personalizado:

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Guard de roles:

```ts
import {
  CanActivate,
  ExecutionContext,
  ForbiddenException,
  Injectable,
} from '@nestjs/common';
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

    if (!requiredRoles?.length) return true;

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];

    const allowed = requiredRoles.some((r) => userRoles.includes(r));
    if (!allowed) throw new ForbiddenException('Insufficient role');

    return true;
  }
}
```

Uso:

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Get('reports')
getReports() {
  return this.reportsService.getAll();
}
```

#### Buenas prácticas

1. Separa autenticación y autorización en guards distintos.
2. Usa metadata declarativa (`@Roles`, `@Permissions`) en lugar de lógica hardcoded.
3. Implementa deny-by-default para rutas sensibles.
4. Mantén políticas complejas en servicios dedicados (CASL/ABAC) e invócalos desde guard.

#### Resultado

Los guards convierten la autorización en una capa explícita, consistente y
testeable, integrada con decorators y contexto de ejecución de NestJS.

</details>

<details>
<summary>26. ¿Qué es @SetMetadata() y cómo funciona con Guards mediante Reflector?</summary>

#### NestJS

`@SetMetadata()` es un helper para adjuntar metadata personalizada a handlers o
controllers. Los guards leen esa metadata en runtime usando `Reflector` para
aplicar autorización o reglas condicionales.

#### Idea clave

1. `@SetMetadata(clave, valor)` escribe metadata.
2. `Reflector` la lee en `canActivate(...)`.
3. El guard decide permitir/bloquear según ese valor.

#### Ejemplo básico: roles

Decorator:

```ts
import { SetMetadata } from '@nestjs/common';

export const ROLES_KEY = 'roles';
export const Roles = (...roles: string[]) => SetMetadata(ROLES_KEY, roles);
```

Guard:

```ts
import {
  CanActivate,
  ExecutionContext,
  ForbiddenException,
  Injectable,
} from '@nestjs/common';
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

    const req = context.switchToHttp().getRequest();
    const userRoles: string[] = req.user?.roles ?? [];

    const ok = requiredRoles.some((role) => userRoles.includes(role));
    if (!ok) throw new ForbiddenException('Insufficient role');

    return true;
  }
}
```

Uso en controller:

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin')
@Get('admin/stats')
getAdminStats() {
  return { ok: true };
}
```

#### Métodos útiles de Reflector

1. `get<T>(key, target)`
   Lee metadata de un target concreto.

2. `getAllAndOverride<T>(key, [handler, class])`
   Prioriza handler sobre class (el más específico sobrescribe).

3. `getAllAndMerge<T>(key, [handler, class])`
   Fusiona metadata de ambos niveles (útil para arrays/flags).

#### Cuándo usarlo

1. Roles y permisos (RBAC).
2. Endpoints públicos (`@Public()`).
3. Flags de auditoría, rate limits personalizados, requisitos multi-tenant.

#### Conclusión

`@SetMetadata()` + `Reflector` convierten reglas en configuración declarativa
sobre endpoints, manteniendo guards genéricos y reutilizables.

</details>

<details>
<summary>27. ¿Cómo implementar autenticación JWT mediante un Guard?</summary>

#### NestJS

En NestJS, la forma estándar es usar Passport con estrategia JWT y un guard que
active esa estrategia para proteger rutas.

#### Pasos principales

1. Configurar `JwtModule` con `secret` y expiración.
2. Crear `JwtStrategy` (extiende `PassportStrategy(Strategy)`).
3. Crear `JwtAuthGuard` (extiende `AuthGuard('jwt')`).
4. Aplicar `@UseGuards(JwtAuthGuard)` en rutas protegidas.

#### 1) Módulo de auth

```ts
import { Module } from '@nestjs/common';
import { JwtModule } from '@nestjs/jwt';
import { PassportModule } from '@nestjs/passport';

@Module({
  imports: [
    PassportModule,
    JwtModule.register({
      secret: process.env.JWT_ACCESS_SECRET,
      signOptions: { expiresIn: '15m' },
    }),
  ],
  providers: [JwtStrategy],
  exports: [JwtModule],
})
export class AuthModule {}
```

#### 2) Estrategia JWT

```ts
import { Injectable, UnauthorizedException } from '@nestjs/common';
import { PassportStrategy } from '@nestjs/passport';
import { ExtractJwt, Strategy } from 'passport-jwt';

@Injectable()
export class JwtStrategy extends PassportStrategy(Strategy) {
  constructor() {
    super({
      jwtFromRequest: ExtractJwt.fromAuthHeaderAsBearerToken(),
      ignoreExpiration: false,
      secretOrKey: process.env.JWT_ACCESS_SECRET,
    });
  }

  async validate(payload: { sub: string; email: string; roles?: string[] }) {
    if (!payload?.sub) throw new UnauthorizedException('Invalid token payload');

    return {
      userId: payload.sub,
      email: payload.email,
      roles: payload.roles ?? [],
    };
  }
}
```

`validate()` retorna el objeto `user` que Nest adjuntará en `request.user`.

#### 3) Guard JWT

```ts
import { Injectable } from '@nestjs/common';
import { AuthGuard } from '@nestjs/passport';

@Injectable()
export class JwtAuthGuard extends AuthGuard('jwt') {}
```

#### 4) Uso en controller

```ts
import { Controller, Get, Req, UseGuards } from '@nestjs/common';

@Controller('profile')
export class ProfileController {
  @UseGuards(JwtAuthGuard)
  @Get('me')
  me(@Req() req: any) {
    return req.user;
  }
}
```

#### Buenas prácticas

1. Guarda `secret` en configuración segura (`ConfigModule`, secret manager).
2. Usa access token corto + refresh token con rotación.
3. Diferencia errores `401` (no autenticado) de `403` (sin permisos).
4. Combina `JwtAuthGuard` con `RolesGuard/PoliciesGuard` para autorización.

#### Resultado

Con esta estructura, JWT auth queda desacoplada, reutilizable y alineada con el
pipeline nativo de seguridad de NestJS.

</details>

<details>
<summary>28. ¿Cómo implementar RBAC y ABAC en NestJS, y cuándo conviene cada enfoque?</summary>

#### NestJS

RBAC y ABAC son dos estrategias de autorización. En NestJS, normalmente se
implementan mediante guards + metadata, pero con distinta granularidad de reglas.

#### Diferencia conceptual

1. **RBAC (Role-Based Access Control)**
   El acceso se decide por roles (`admin`, `manager`, `user`).

2. **ABAC (Attribute-Based Access Control)**
   El acceso se decide por atributos del sujeto, recurso, acción y contexto
   (ownerId, estado del recurso, tenantId, horario, etc.).

#### Cuándo usar RBAC

1. Permisos simples y estables por rol.
2. Sistemas con bajo número de excepciones.
3. Requisitos de implementación rápida y fácil auditoría.

#### Cuándo usar ABAC

1. Reglas finas por recurso/propiedad.
2. Multi-tenant con ownership y condiciones dinámicas.
3. Necesidad de políticas contextuales complejas.

#### Implementación RBAC en NestJS (resumen)

1. Decorador `@Roles(...)` con `SetMetadata`.
2. `RolesGuard` que usa `Reflector`.
3. Guard compara `req.user.roles` con roles requeridos.

```ts
@UseGuards(JwtAuthGuard, RolesGuard)
@Roles('admin', 'manager')
@Delete(':id')
removeUser() {}
```

#### Implementación ABAC en NestJS (resumen)

Patrón recomendado: guard liviano + servicio de políticas.

```ts
@UseGuards(JwtAuthGuard, PoliciesGuard)
@CheckPolicy((ability) => ability.can('update', 'Article'))
@Patch(':id')
updateArticle() {}
```

En `PoliciesGuard`:

1. Carga usuario (`req.user`).
2. Carga recurso si hace falta (por `id`).
3. Construye contexto de autorización (tenant, ownership, estado).
4. Delega decisión a policy engine (`CASL` u otro).

#### Arquitectura práctica

1. **RBAC base + ABAC complementario**
   RBAC filtra acceso grueso; ABAC aplica reglas finas por recurso.

2. **Separar definición y ejecución**
   Controllers declaran intención (decorators), guards ejecutan reglas.

3. **Políticas versionables y testeables**
   Evita reglas hardcoded dispersas en services/controllers.

#### Riesgos comunes

1. Usar solo RBAC en dominios con ownership complejo -> sobrepermisos.
2. Implementar ABAC directamente en controllers -> acoplamiento y baja mantenibilidad.
3. No cachear/optimizar cargas de recurso en guards ABAC -> impacto en latencia.

#### Regla práctica

Empieza con RBAC si el dominio es simple. Migra a RBAC+ABAC cuando aparezcan
reglas por recurso, tenant o contexto que los roles ya no modelen bien.

</details>

<details>
<summary>29. ¿Cómo implementar rotación de refresh token y por qué es importante?</summary>

#### NestJS

La rotación de refresh token significa que en cada operación de refresh se invalida
el token anterior y se emite uno nuevo. Esto reduce el impacto del robo de tokens
y mejora el control de sesiones.

#### Por qué es importante

1. Si un refresh token se filtra y no hay rotación, puede reutilizarse durante mucho tiempo.
2. Con rotación, un token viejo reutilizado puede detectarse como compromiso.
3. Permite revocar familias de tokens por dispositivo/sesión.

#### Patrón recomendado

1. En login:
   1. Emitir `accessToken` (corto) + `refreshToken` (más largo).
   2. Guardar hash del refresh token en DB junto con `sessionId`/`deviceId`.

2. En `/auth/refresh`:
   1. Verificar firma/expiración del refresh token.
   2. Buscar sesión/token almacenado.
   3. Comparar hash del token recibido con hash almacenado.
   4. Si coincide: invalidar token actual, emitir nuevo par y persistir nuevo hash.
   5. Si no coincide: marcar sesión/familia como comprometida y revocar.

#### Esquema de entidad de sesión (ejemplo)

```ts
interface RefreshSession {
  id: string;               // sessionId
  userId: string;
  refreshTokenHash: string;
  userAgent?: string;
  ip?: string;
  expiresAt: Date;
  revokedAt?: Date;
  replacedByTokenId?: string;
}
```

#### Flujo básico en service

```ts
async rotateRefreshToken(oldToken: string) {
  const payload = this.jwt.verify(oldToken, { secret: REFRESH_SECRET });
  const session = await this.sessionsRepo.findById(payload.sid);

  if (!session || session.revokedAt) throw new UnauthorizedException();

  const ok = await this.hash.compare(oldToken, session.refreshTokenHash);
  if (!ok) {
    await this.sessionsRepo.revokeFamily(session.id); // posible replay
    throw new UnauthorizedException('Refresh token reuse detected');
  }

  const { accessToken, refreshToken, newSession } = await this.issueNewPair(session.userId, session);
  return { accessToken, refreshToken };
}
```

#### Buenas prácticas

1. Nunca guardes refresh tokens en texto plano; guarda hash.
2. Usa secretos distintos para access y refresh.
3. Usa `jti`/`sid` para rastrear familia de tokens.
4. Limita refresh por dispositivo/sesión y permite logout por dispositivo.
5. Registra eventos de reuse para alertas de seguridad.

#### Conclusión

La rotación de refresh token es una protección crítica: convierte el refresh en
un mecanismo de sesión controlable y reduce drásticamente el riesgo de secuestro
persistente de sesión.

</details>

<details>
<summary>30. ¿Qué es un Pipe en NestJS y cuándo debes usarlo?</summary>

#### NestJS

Un **Pipe** en NestJS es un componente que se ejecuta antes del handler para
**transformar** y/o **validar** datos de entrada.

Se aplica a parámetros de ruta (`@Body`, `@Param`, `@Query`, etc.) y protege
la lógica de negocio de datos inválidos.

#### Para qué sirve un Pipe

1. **Validación**
   Verificar que el input cumpla reglas (campos obligatorios, formatos, rangos).

2. **Transformación**
   Convertir tipos (`'42' -> 42`), normalizar strings, mapear estructuras.

3. **Fail-fast**
   Detener la solicitud temprano con error HTTP claro (`400 Bad Request`).

#### Cuándo usar Pipes

1. Validar DTOs de entrada en endpoints REST.
2. Parsear parámetros (`id` como número/UUID).
3. Sanitizar datos de entrada de forma consistente.
4. Aplicar reglas reutilizables entre múltiples rutas.

#### Pipes integrados comunes

1. `ValidationPipe`
2. `ParseIntPipe`
3. `ParseBoolPipe`
4. `ParseUUIDPipe`
5. `DefaultValuePipe`

#### Ejemplos

Validación global:

```ts
app.useGlobalPipes(
  new ValidationPipe({
    whitelist: true,
    forbidNonWhitelisted: true,
    transform: true,
  }),
);
```

Parsing de parámetro:

```ts
@Get(':id')
findOne(@Param('id', ParseIntPipe) id: number) {
  return this.usersService.findOne(id);
}
```

Pipe personalizado:

```ts
import { Injectable, PipeTransform, BadRequestException } from '@nestjs/common';

@Injectable()
export class TrimPipe implements PipeTransform {
  transform(value: any) {
    if (typeof value === 'string') return value.trim();
    if (value && typeof value === 'object') {
      for (const k of Object.keys(value)) {
        if (typeof value[k] === 'string') value[k] = value[k].trim();
      }
    }
    return value;
  }
}
```

#### Buenas prácticas

1. Usa `ValidationPipe` global en casi todas las APIs.
2. Mantén pipes enfocados en input transformation/validation, no lógica de negocio.
3. Combina pipes con DTO + `class-validator` para contratos explícitos.
4. Evita lógica pesada o I/O bloqueante dentro de pipes.

#### Conclusión

Los pipes son la capa correcta para garantizar que los handlers reciban datos
limpios y tipados, mejorando seguridad, consistencia y mantenibilidad.

</details>

<details>
<summary>31. ¿Qué es un DTO?</summary>

#### NestJS

Un **DTO** (*Data Transfer Object*) es un objeto que define de forma explícita
la estructura de datos que entra o sale de la API.

En NestJS, normalmente se implementa como clase TypeScript para habilitar
validación y transformación en runtime con `class-validator` y `class-transformer`.

#### Para qué sirve un DTO

1. Definir contrato de entrada/salida claro por endpoint.
2. Validar payloads antes de llegar a la lógica de negocio.
3. Evitar acoplar entidades internas de dominio/DB al API contract.
4. Mejorar documentación (Swagger) y mantenibilidad.

#### Ejemplo básico

```ts
import { IsEmail, IsString, MinLength } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;

  @IsString()
  @MinLength(8)
  password: string;

  @IsString()
  name: string;
}
```

Uso en controller:

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

Con `ValidationPipe`, Nest validará automáticamente el body contra este DTO.

#### DTO vs Entity

1. **DTO**: contrato de transporte (API boundary).
2. **Entity/Model**: representación interna de dominio/persistencia.

No deben mezclarse en sistemas medianos/grandes.

#### Buenas prácticas

1. Crear DTOs separados para create/update/response.
2. Usar mapped types (`PartialType`, `PickType`, etc.) para reducir duplicación.
3. Mantener DTOs sin lógica de negocio.
4. Versionar DTOs cuando evoluciona la API.

#### Conclusión

DTOs son la base de contratos estables en NestJS: hacen la API predecible,
segura y fácil de evolucionar.

</details>

<details>
<summary>32. ¿Cuál es la diferencia entre interface y class para tipar DTOs, y por qué class es preferida en NestJS?</summary>

#### NestJS

En TypeScript, `interface` y `class` pueden describir forma de datos, pero en
NestJS los DTOs se definen preferentemente como **classes** porque Nest necesita
metadata en runtime para validación, transformación y documentación.

#### Diferencia clave

1. **interface**
   Existe solo en compile-time; se elimina al transpilar a JavaScript.
   No deja metadata en runtime.

2. **class**
   Existe en runtime como constructor/objeto real.
   Permite decorators (`@IsEmail`, `@ApiProperty`, etc.) y reflexión.

#### Por qué NestJS prefiere class para DTO

1. `ValidationPipe` usa metadata de decorators para validar.
2. `class-transformer` convierte payload plano a instancia de clase.
3. Swagger (`@nestjs/swagger`) genera schemas desde clases decoradas.
4. Mapped types (`PartialType`, `PickType`, `OmitType`) operan sobre clases.

#### Ejemplo

Con `interface` (limitado):

```ts
interface CreateUserDto {
  email: string;
  password: string;
}
```

Con `class` (recomendado):

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

#### Consecuencia práctica

Si usas interfaces para DTO de entrada:

1. Pierdes validación declarativa automática.
2. Pierdes transformación tipada consistente.
3. Pierdes integración completa con Swagger y mapped types.

#### Regla práctica

1. Usa **classes** para DTOs de transporte (request/response) en NestJS.
2. Usa **interfaces** para contratos internos (ports, repositorios, servicios)
   donde no necesitas metadata runtime.

#### Conclusión

`interface` tipa en compile-time; `class` habilita capacidades de framework en
runtime. Por eso, para DTOs en NestJS, `class` es la opción correcta.

</details>

<details>
<summary>33. ¿Qué son los mapped types en NestJS? (PartialType, OmitType, PickType, IntersectionType)</summary>

#### NestJS

Los **mapped types** en NestJS permiten crear nuevos DTOs a partir de otros,
reutilizando estructura y metadata (validación/swagger) sin duplicar código.

Se usan desde `@nestjs/mapped-types` (y también desde `@nestjs/swagger` cuando
integras OpenAPI).

#### Para qué sirven

1. Reducir duplicación entre DTOs de create/update/read.
2. Mantener consistencia de reglas de validación.
3. Evolucionar contratos de API con menos mantenimiento.

#### Mapped types principales

1. **`PartialType(BaseDto)`**
   Convierte todas las propiedades en opcionales.
   Uso típico: `UpdateXDto` desde `CreateXDto`.

2. **`PickType(BaseDto, ['a', 'b'])`**
   Toma solo propiedades específicas del DTO base.

3. **`OmitType(BaseDto, ['a', 'b'])`**
   Crea un DTO excluyendo ciertas propiedades.

4. **`IntersectionType(A, B)`**
   Combina propiedades de dos DTOs en uno.

#### Ejemplo

```ts
import { PartialType, PickType, OmitType, IntersectionType } from '@nestjs/mapped-types';
import { IsEmail, IsString, MinLength } from 'class-validator';

export class CreateUserDto {
  @IsEmail()
  email: string;

  @IsString()
  @MinLength(8)
  password: string;

  @IsString()
  name: string;
}

export class UpdateUserDto extends PartialType(CreateUserDto) {}

export class UserLoginDto extends PickType(CreateUserDto, ['email', 'password'] as const) {}

export class UserPublicDto extends OmitType(CreateUserDto, ['password'] as const) {}

export class AuditDto {
  @IsString()
  requestId: string;
}

export class CreateUserWithAuditDto extends IntersectionType(CreateUserDto, AuditDto) {}
```

#### Buenas prácticas

1. Usa `PartialType` para updates PATCH en lugar de reescribir DTOs.
2. Evita cadenas muy profundas de composición (difícil de leer).
3. Verifica Swagger schema final cuando combines tipos complejos.
4. Mantén el DTO base limpio y orientado al contrato.

#### Conclusión

Los mapped types son una herramienta clave para escalar APIs NestJS: menos
boilerplate, contratos consistentes y validación/documentación reutilizables.

</details>

<details>
<summary>34. ¿Cómo implementar validación usando class-validator y pipes?</summary>

#### NestJS

La forma estándar en NestJS es: definir reglas en DTOs con `class-validator` y
activar `ValidationPipe` (global o por ruta) para validar automáticamente la entrada.

#### Pasos de implementación

1. Instala dependencias:
   1. `class-validator`
   2. `class-transformer`

2. Define DTO con decorators de validación.
3. Activa `ValidationPipe`.
4. Usa DTO en `@Body()`, `@Query()`, `@Param()`.

#### DTO de ejemplo

```ts
import { IsEmail, IsInt, IsOptional, IsString, MaxLength, Min } from 'class-validator';
import { Type } from 'class-transformer';

export class CreateUserDto {
  @IsEmail()
  email: string;

  @IsString()
  @MaxLength(64)
  name: string;

  @Type(() => Number)
  @IsInt()
  @Min(18)
  age: number;

  @IsOptional()
  @IsString()
  bio?: string;
}
```

#### Activación global en `main.ts`

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

#### Qué hace cada opción importante

1. `whitelist: true` -> elimina campos no definidos en DTO.
2. `forbidNonWhitelisted: true` -> lanza error si llegan campos extra.
3. `transform: true` -> transforma payload plano a instancia DTO.
4. `enableImplicitConversion` -> convierte tipos básicos cuando es posible.

#### Uso en controller

```ts
@Post()
create(@Body() dto: CreateUserDto) {
  return this.usersService.create(dto);
}
```

#### Validación por ruta (si no quieres global)

```ts
@Post('strict')
createStrict(
  @Body(new ValidationPipe({ whitelist: true, forbidNonWhitelisted: true }))
  dto: CreateUserDto,
) {
  return this.usersService.create(dto);
}
```

#### Buenas prácticas

1. Mantén DTOs separados para create/update/filter.
2. Usa `PartialType` para updates parciales.
3. No pongas lógica de negocio en DTOs/pipes.
4. Personaliza `exceptionFactory` si necesitas formato de error uniforme.

#### Conclusión

`class-validator` + `ValidationPipe` crean una frontera de entrada robusta: datos
inválidos se rechazan antes de tocar la lógica de negocio.

</details>

<details>
<summary>35. ¿Cómo implementar un Exception Filter global y errores HTTP personalizados?</summary>

#### NestJS

En NestJS, un **Exception Filter** centraliza el manejo de errores para devolver
respuestas consistentes y evitar duplicación de `try/catch` en controllers/services.

#### Objetivo

1. Capturar excepciones no controladas.
2. Estandarizar formato de error HTTP.
3. Mapear errores de dominio/infraestructura a códigos correctos.
4. Registrar contexto útil para observabilidad.

#### 1) Filter global básico

```ts
import {
  ArgumentsHost,
  Catch,
  ExceptionFilter,
  HttpException,
  HttpStatus,
} from '@nestjs/common';

@Catch()
export class GlobalExceptionFilter implements ExceptionFilter {
  catch(exception: unknown, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const req = ctx.getRequest();
    const res = ctx.getResponse();

    const isHttp = exception instanceof HttpException;
    const status = isHttp
      ? exception.getStatus()
      : HttpStatus.INTERNAL_SERVER_ERROR;

    const raw = isHttp ? exception.getResponse() : 'Internal server error';
    const message =
      typeof raw === 'string'
        ? raw
        : (raw as any).message ?? 'Internal server error';

    res.status(status).json({
      success: false,
      statusCode: status,
      path: req.url,
      timestamp: new Date().toISOString(),
      message,
    });
  }
}
```

Registro global en `main.ts`:

```ts
app.useGlobalFilters(new GlobalExceptionFilter());
```

#### 2) Errores HTTP personalizados

```ts
import { HttpException, HttpStatus } from '@nestjs/common';

export class BusinessRuleException extends HttpException {
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

Uso:

```ts
if (order.total <= 0) {
  throw new BusinessRuleException('Order total must be greater than zero');
}
```

#### 3) Mapeo de errores de dominio

Patrón recomendado:

1. Dominio lanza errores semánticos (`DomainError`, `PolicyViolationError`).
2. Capa application/adapters los mapea a `HttpException` (o códigos propios).
3. Filter global solo formatea y protege detalle sensible.

#### Buenas prácticas

1. No expongas stack traces ni detalles internos en producción.
2. Incluye `requestId/correlationId` en respuesta y logs.
3. Diferencia bien 4xx (error cliente/regla) y 5xx (fallo servidor).
4. Mantén un catálogo de códigos de error estable para clientes.

#### Conclusión

Un filter global + excepciones personalizadas crean una estrategia de errores
predecible, segura y mantenible en toda la API.

</details>

<details>
<summary>36. ¿Cómo manejar correctamente errores y devolver una estructura de respuesta consistente?</summary>

#### NestJS

Para manejar errores correctamente en NestJS, necesitas una estrategia unificada:
excepciones semánticas, filtro global y contrato de error estable para clientes.

#### Principios clave

1. Usar excepciones de dominio claras (no `throw new Error()` genérico).
2. Mapear errores esperados a códigos 4xx apropiados.
3. Reservar 5xx para fallos inesperados del servidor.
4. Devolver siempre el mismo shape de error.

#### Estructura de respuesta recomendada

```json
{
  "success": false,
  "statusCode": 422,
  "code": "BUSINESS_RULE_VIOLATION",
  "message": "Order cannot be closed in current state",
  "path": "/orders/123/close",
  "timestamp": "2026-01-10T10:00:00.000Z",
  "requestId": "req-7f3a..."
}
```

#### Flujo recomendado

1. Controller/service lanza excepción tipada (`NotFoundException`, `ForbiddenException`, excepción custom).
2. Exception Filter global captura todo.
3. Filter normaliza la salida al contrato estándar.
4. Logger registra stack + contexto interno (sin exponer detalles sensibles al cliente).

#### Ejemplo de mapeo práctico

1. `EntityNotFound` -> `404 Not Found`
2. `ValidationError` -> `400 Bad Request`
3. `BusinessRuleViolation` -> `422 Unprocessable Entity`
4. `AuthError` -> `401/403`
5. `Unknown error` -> `500 Internal Server Error`

#### Buenas prácticas

1. Define catálogo estable de `code` legible por máquina.
2. Incluye `requestId` para trazabilidad entre cliente y logs.
3. No retornes stack trace en producción.
4. Mantén mensajes seguros y útiles, sin filtrar secretos internos.
5. Documenta errores en Swagger/OpenAPI.

#### Conclusión

Una respuesta de error consistente reduce ambigüedad para frontend/integraciones,
acelera debugging y mejora la resiliencia operativa de la API.

</details>

<details>
<summary>37. ¿Cómo registrar correctamente errores sin perder stack trace en producción?</summary>

#### NestJS

El objetivo es registrar errores con suficiente contexto operativo, conservar
stack trace completo en logs y al mismo tiempo no exponer detalles sensibles al
cliente HTTP.

#### Principios clave

1. Separar **respuesta al cliente** de **registro interno**.
2. Mantener stack trace original en logger/observabilidad.
3. Añadir contexto estructurado (requestId, userId, path, método, módulo).
4. Evitar `console.error` disperso y logging no estructurado.

#### Estrategia recomendada

1. Exception Filter global captura excepciones.
2. El filter registra error con logger estructurado (`pino`/`winston`/OTel).
3. La respuesta HTTP devuelve mensaje seguro y código estable.
4. Stack trace queda en logs centralizados (ELK, Datadog, Grafana, etc.).

#### Ejemplo de filter con logging estructurado

```ts
import {
  ArgumentsHost,
  Catch,
  ExceptionFilter,
  HttpException,
  HttpStatus,
  Injectable,
} from '@nestjs/common';
import { Request, Response } from 'express';

@Injectable()
@Catch()
export class GlobalExceptionFilter implements ExceptionFilter {
  constructor(private readonly logger: AppLogger) {}

  catch(exception: unknown, host: ArgumentsHost) {
    const ctx = host.switchToHttp();
    const req = ctx.getRequest<Request>();
    const res = ctx.getResponse<Response>();

    const isHttp = exception instanceof HttpException;
    const status = isHttp ? exception.getStatus() : HttpStatus.INTERNAL_SERVER_ERROR;

    const message = isHttp
      ? exception.message
      : 'Internal server error';

    this.logger.error({
      msg: 'Unhandled exception',
      err: exception instanceof Error ? exception : new Error(String(exception)),
      status,
      method: req.method,
      path: req.url,
      requestId: (req as any).requestId,
      userId: (req as any).user?.id,
    });

    res.status(status).json({
      success: false,
      statusCode: status,
      message,
      requestId: (req as any).requestId,
      timestamp: new Date().toISOString(),
    });
  }
}
```

#### Buenas prácticas críticas

1. Nunca reemplaces error original por string sin conservar `stack`.
2. Usa objeto `err` nativo en logger para serializar `name/message/stack`.
3. No loguees secretos (tokens, passwords, datos sensibles).
4. Configura niveles: `error` (fallos), `warn` (degradación), `info` (flujo normal).
5. Activa source maps en producción para stacks legibles en TS.

#### Antipatrones frecuentes

1. `catch (e) { throw new Error('failed') }` (pierde stack original).
2. Atrapar excepción y retornar `200` con campo `error`.
3. Duplicar logging en múltiples capas sin correlación.

#### Conclusión

En producción, la regla es: cliente recibe error seguro y consistente; el equipo
recibe logs estructurados con stack trace completo y contexto correlacionable.

</details>

<details>
<summary>38. ¿Qué es ConfigModule y por qué debes usarlo en lugar de process.env?</summary>

#### NestJS

`ConfigModule` (`@nestjs/config`) es la forma estándar de gestionar configuración
en NestJS: carga variables de entorno, permite validarlas, tiparlas e inyectarlas
por DI.

Usarlo es mejor que leer `process.env` directamente en cualquier parte del código.

#### Problemas de usar `process.env` directo

1. Configuración dispersa y difícil de auditar.
2. Sin validación temprana (errores aparecen en runtime tardío).
3. Tipado débil (`string | undefined` en todas partes).
4. Acoplamiento global y baja testabilidad.

#### Qué aporta `ConfigModule`

1. **Centralización** de configuración.
2. **Validación al arranque** (Joi/zod/custom).
3. **Inyección por dependencia** (`ConfigService`) en providers.
4. **Tipado y namespaces** para dominios (`database`, `jwt`, `redis`, etc.).
5. **Soporte multi-entorno** con `envFilePath`.

#### Configuración básica

```ts
import { Module } from '@nestjs/common';
import { ConfigModule } from '@nestjs/config';

@Module({
  imports: [
    ConfigModule.forRoot({
      isGlobal: true,
      envFilePath: ['.env.local', '.env'],
    }),
  ],
})
export class AppModule {}
```

Uso en un servicio:

```ts
import { Injectable } from '@nestjs/common';
import { ConfigService } from '@nestjs/config';

@Injectable()
export class JwtSettingsService {
  constructor(private readonly config: ConfigService) {}

  get accessSecret(): string {
    return this.config.getOrThrow<string>('JWT_ACCESS_SECRET');
  }
}
```

#### Patrón recomendado en sistemas grandes

1. Crear archivos de configuración por dominio (`config/database.config.ts`, etc.).
2. Exportar objetos tipados mediante `registerAs(...)`.
3. Validar variables críticas al bootstrap.
4. Nunca hardcodear secretos en código.

#### Conclusión

`ConfigModule` convierte la configuración en un contrato explícito y validado.
Reduce fallos en producción y mejora mantenibilidad, seguridad y testabilidad.

</details>

<details>
<summary>39. ¿Cómo organizar correctamente archivos .env para distintos entornos (dev, staging, prod)?</summary>

#### NestJS

Una organización correcta de `.env` evita errores de despliegue, reduce deriva
entre entornos y mejora seguridad operacional.

#### Principios clave

1. Separar configuración por entorno.
2. Mantener una lista base de variables requeridas.
3. Nunca versionar secretos reales.
4. Validar configuración al arrancar.

#### Estructura recomendada

1. `.env.example` -> plantilla sin secretos (sí en Git).
2. `.env.development` -> valores locales de dev.
3. `.env.staging` -> valores de staging (normalmente gestionados en plataforma CI/CD).
4. `.env.production` -> valores de prod (gestor de secretos, no en repo).
5. `.env.test` -> configuración aislada para tests.

#### Carga en NestJS

```ts
ConfigModule.forRoot({
  isGlobal: true,
  envFilePath: [
    `.env.${process.env.NODE_ENV ?? 'development'}`,
    '.env',
  ],
});
```

Orden: el primero tiene prioridad y puede sobreescribir valores del segundo.

#### Buenas prácticas críticas

1. **Versiona solo `.env.example`**.
2. **No subas `.env.*` con secretos** (usa `.gitignore`).
3. **Usa secret manager** en staging/prod (AWS SM, Vault, Doppler, etc.).
4. **Tipa y valida** con Joi/zod (`getOrThrow` para claves críticas).
5. **Define naming consistente**: `DB_HOST`, `DB_PORT`, `JWT_ACCESS_SECRET`.

#### Estrategia para CI/CD

1. CI ejecuta con variables inyectadas por pipeline/plataforma.
2. No depender de archivos locales en contenedores de producción.
3. Revisar paridad de variables entre entornos (checklist automática).

#### Errores comunes

1. Reutilizar `.env` de dev en producción.
2. Variables opcionales sin default razonable ni validación.
3. Mezclar configuración sensible con flags de feature sin control.

#### Conclusión

La configuración por entorno debe ser explícita, validada y externalizada.
Eso evita fallos silenciosos y mejora la confiabilidad del sistema.

</details>

<details>
<summary>40. ¿Cómo usar Joi o zod para validar configuración al iniciar la aplicación?</summary>

#### NestJS

La validación de configuración en bootstrap evita que la app arranque con
variables faltantes o inválidas. En NestJS se hace típicamente en `ConfigModule.forRoot()`.

#### Opción 1: Joi (integración directa)

```ts
import * as Joi from 'joi';
import { ConfigModule } from '@nestjs/config';

ConfigModule.forRoot({
  isGlobal: true,
  validationSchema: Joi.object({
    NODE_ENV: Joi.string().valid('development', 'test', 'staging', 'production').required(),
    PORT: Joi.number().port().default(3000),
    DB_HOST: Joi.string().required(),
    DB_PORT: Joi.number().port().required(),
    DB_USER: Joi.string().required(),
    DB_PASSWORD: Joi.string().required(),
    JWT_ACCESS_SECRET: Joi.string().min(32).required(),
  }),
  validationOptions: {
    abortEarly: false,
    allowUnknown: true,
  },
});
```

#### Opción 2: zod (schema tipado)

```ts
import { z } from 'zod';

const envSchema = z.object({
  NODE_ENV: z.enum(['development', 'test', 'staging', 'production']),
  PORT: z.coerce.number().int().min(1).max(65535).default(3000),
  DB_HOST: z.string().min(1),
  DB_PORT: z.coerce.number().int().min(1).max(65535),
  DB_USER: z.string().min(1),
  DB_PASSWORD: z.string().min(1),
  JWT_ACCESS_SECRET: z.string().min(32),
});

export function validateEnv(config: Record<string, unknown>) {
  const parsed = envSchema.safeParse(config);
  if (!parsed.success) {
    throw new Error(`Config validation error: ${parsed.error.message}`);
  }
  return parsed.data;
}
```

Y en `ConfigModule`:

```ts
ConfigModule.forRoot({
  isGlobal: true,
  validate: validateEnv,
});
```

#### Qué validar siempre

1. Presencia de claves obligatorias (DB, JWT, URLs externas).
2. Tipos y rangos (`PORT`, timeouts, límites).
3. Formatos (URL, email, enum de entorno).
4. Reglas de seguridad (longitud mínima de secretos).

#### Buenas prácticas

1. Fallar rápido en startup si hay error de config.
2. Mantener un único schema fuente de verdad.
3. Usar `getOrThrow`/config tipada en servicios.
4. No exponer valores sensibles en mensajes de error/logs.

#### Conclusión

Joi y zod convierten `.env` en un contrato verificable. El beneficio principal
es prevenir incidentes de producción por configuración inválida.

</details>

<details>
<summary>41. ¿Cómo implementar feature flags en NestJS?</summary>

#### NestJS

Los **feature flags** permiten activar/desactivar funcionalidades sin redeploy,
controlar rollouts graduales y reducir riesgo en cambios productivos.

#### Estrategia base

1. Definir fuente de flags (env, DB, Redis o servicio externo).
2. Centralizar lectura en un `FeatureFlagsService`.
3. Evaluar flags en puntos de decisión (guards, services, controllers).
4. Soportar targeting (por tenant, usuario, porcentaje, entorno).

#### Implementación mínima (config + service)

```ts
// feature-flags.config.ts
export default () => ({
  features: {
    newCheckout: process.env.FEATURE_NEW_CHECKOUT === 'true',
    betaReports: process.env.FEATURE_BETA_REPORTS === 'true',
  },
});
```

```ts
// feature-flags.service.ts
import { Injectable } from '@nestjs/common';
import { ConfigService } from '@nestjs/config';

@Injectable()
export class FeatureFlagsService {
  constructor(private readonly config: ConfigService) {}

  isEnabled(flag: string): boolean {
    return this.config.get<boolean>(`features.${flag}`) === true;
  }
}
```

Uso:

```ts
if (this.flags.isEnabled('newCheckout')) {
  return this.newCheckoutFlow(data);
}
return this.legacyCheckoutFlow(data);
```

#### Flag guard (opcional)

```ts
@Injectable()
export class FeatureFlagGuard implements CanActivate {
  constructor(
    private readonly reflector: Reflector,
    private readonly flags: FeatureFlagsService,
  ) {}

  canActivate(context: ExecutionContext): boolean {
    const flag = this.reflector.get<string>('featureFlag', context.getHandler());
    if (!flag) return true;
    return this.flags.isEnabled(flag);
  }
}
```

Decorator:

```ts
export const FeatureFlag = (name: string) => SetMetadata('featureFlag', name);
```

#### Escalado para producción

1. Guardar flags dinámicas en DB/Redis o usar LaunchDarkly/Unleash.
2. Cachear evaluaciones con TTL corto.
3. Añadir auditoría: quién cambió qué flag y cuándo.
4. Soportar porcentaje de rollout y segmentación por tenant/plan.

#### Buenas prácticas

1. Nombres explícitos (`checkout_v2_enabled`).
2. Evitar flags permanentes: planear fecha de retiro.
3. Tests para ambos caminos (flag on/off).
4. No mezclar autorización con flags (son conceptos distintos).

#### Conclusión

Feature flags en NestJS se implementan mejor como una capacidad transversal,
centralizada y observable para entregar cambios de forma segura.

</details>

<details>
<summary>42. ¿Cómo integrar bases de datos? (TypeORM, Prisma, Drizzle, Mongoose)</summary>

#### NestJS

NestJS se integra con distintas tecnologías de persistencia mediante módulos y
providers. La elección depende de tu modelo de datos, requisitos de rendimiento
y estilo de desarrollo.

#### Opciones comunes

1. **TypeORM**
   ORM clásico con decorators, repositories y migraciones.

2. **Prisma**
   ORM moderno con schema declarativo y cliente tipado generado.

3. **Drizzle**
   ORM ligero SQL-first, muy explícito y cercano a SQL.

4. **Mongoose**
   ODM para MongoDB basado en esquemas/documentos.

#### Patrón de integración en NestJS

1. Crear módulo de infraestructura de DB.
2. Registrar conexión global (`forRoot` o provider custom).
3. Registrar entidades/modelos por feature (`forFeature` o repositorio propio).
4. Inyectar repositorios/clients en servicios de aplicación.

#### Ejemplo TypeORM

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

#### Ejemplo Prisma

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

#### Ejemplo Mongoose

```ts
MongooseModule.forRoot(process.env.MONGO_URI!);
MongooseModule.forFeature([{ name: User.name, schema: UserSchema }]);
```

#### Criterios de elección (rápidos)

1. **TypeORM**: bueno si tu equipo ya trabaja con patrón repository clásico.
2. **Prisma**: excelente DX, tipado fuerte y migraciones claras.
3. **Drizzle**: control SQL fino con tipado moderno y bajo overhead.
4. **Mongoose**: opción natural si tu dominio encaja en documentos MongoDB.

#### Buenas prácticas

1. Desactiva `synchronize: true` en producción.
2. Usa migraciones versionadas en cualquier stack.
3. Encapsula acceso a DB tras servicios/repositorios del dominio.
4. Configura pool de conexiones, timeouts y observabilidad de queries.
5. Mantén una estrategia clara de transacciones e idempotencia.

#### Conclusión

NestJS no te ata a un ORM/ODM concreto: define límites limpios de infraestructura,
y elige la herramienta según tu dominio y necesidades operativas.

</details>

<details>
<summary>43. ¿Cuál es la diferencia entre TypeOrmModule.forRoot() y forFeature()?</summary>

#### NestJS + TypeORM

`forRoot()` y `forFeature()` cumplen roles distintos en la integración con TypeORM.

#### `TypeOrmModule.forRoot()`

1. Configura la **conexión global** a la base de datos.
2. Se declara normalmente una vez en `AppModule`.
3. Define host, puerto, credenciales, DB, opciones de conexión, etc.

Ejemplo:

```ts
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
```

#### `TypeOrmModule.forFeature([...])`

1. Registra **entidades/repositories** dentro de un módulo feature.
2. Permite inyectar repositorios con `@InjectRepository(Entity)`.
3. Se usa en cada módulo que necesita acceso a esas entidades.

Ejemplo:

```ts
@Module({
  imports: [TypeOrmModule.forFeature([UserEntity, OrderEntity])],
  providers: [UsersService],
})
export class UsersModule {}
```

#### Cómo trabajan juntos

1. `forRoot()` crea y mantiene el `DataSource`.
2. `forFeature()` expone repositories ligados a ese `DataSource` en el scope del módulo.

#### Regla práctica

1. `forRoot()` -> **conectar** a la DB.
2. `forFeature()` -> **usar entidades/repositorios** en un módulo concreto.

#### Error común

Intentar inyectar `Repository<UserEntity>` sin haber importado
`TypeOrmModule.forFeature([UserEntity])` en ese módulo.

#### Conclusión

Piensa `forRoot` como bootstrap de infraestructura global, y `forFeature` como
registro local por módulo para trabajar con entidades específicas.

</details>

<details>
<summary>44. ¿Qué es el patrón Repository en NestJS + TypeORM?</summary>

#### NestJS + TypeORM

El patrón **Repository** encapsula acceso a datos y consultas de persistencia
para una entidad, separando la lógica de almacenamiento de la lógica de negocio.

En TypeORM, `Repository<Entity>` ya implementa este patrón base y NestJS lo
inyecta por DI mediante `@InjectRepository`.

#### Qué resuelve

1. Evita mezclar SQL/ORM en controllers/services de negocio.
2. Centraliza queries reutilizables por agregado/entidad.
3. Facilita testeo (mock del repositorio).
4. Permite cambiar detalles de persistencia con menor impacto.

#### Uso básico en NestJS

```ts
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { UserEntity } from './user.entity';

@Injectable()
export class UsersService {
  constructor(
    @InjectRepository(UserEntity)
    private readonly usersRepo: Repository<UserEntity>,
  ) {}

  findByEmail(email: string) {
    return this.usersRepo.findOne({ where: { email } });
  }
}
```

#### Patrón recomendado en sistemas grandes

No exponer `Repository` crudo por toda la app. Crear una abstracción propia:

1. Definir interfaz de puerto de persistencia en capa dominio/app.
2. Implementarla con TypeORM en infraestructura.

Ejemplo conceptual:

```ts
export interface UsersRepository {
  findById(id: string): Promise<User | null>;
  save(user: User): Promise<void>;
}
```

Implementación:

```ts
@Injectable()
export class TypeOrmUsersRepository implements UsersRepository {
  constructor(
    @InjectRepository(UserEntity)
    private readonly repo: Repository<UserEntity>,
  ) {}

  async findById(id: string): Promise<User | null> {
    const entity = await this.repo.findOne({ where: { id } });
    return entity ? mapToDomain(entity) : null;
  }

  async save(user: User): Promise<void> {
    await this.repo.save(mapToEntity(user));
  }
}
```

#### Buenas prácticas

1. Mantén queries complejas dentro del repositorio, no en controllers.
2. Separa entidades ORM de modelos de dominio cuando el dominio crece.
3. Evita filtrar detalles de TypeORM hacia capas superiores.
4. Cubre repositorios con tests de integración (contra DB real/testcontainer).

#### Conclusión

El patrón Repository en NestJS + TypeORM es la frontera entre dominio y
persistencia. Bien aplicado, mejora mantenibilidad, testabilidad y evolución de
arquitectura.

</details>

<details>
<summary>45. ¿Cuál es la diferencia entre Repository pattern y Active Record, y cuándo elegir cada uno?</summary>

#### NestJS / Arquitectura

**Repository pattern** y **Active Record** son dos estilos de acceso a datos con
trade-offs distintos en acoplamiento, testabilidad y complejidad.

#### Diferencia conceptual

1. **Active Record**
   La entidad combina estado + lógica de persistencia (`save`, `remove`, etc.).
   El modelo “se guarda a sí mismo”.

2. **Repository pattern**
   La entidad/modelo de dominio está separada de la persistencia.
   Repositorios externos cargan/guardan datos.

#### Ejemplo mental

1. Active Record: `user.name = 'A'; await user.save();`
2. Repository: `user.rename('A'); await usersRepository.save(user);`

#### Cuándo elegir Active Record

1. Proyectos pequeños/medianos con dominio simple.
2. CRUD rápido con baja complejidad de reglas.
3. Equipos que priorizan velocidad inicial sobre aislamiento arquitectónico.

#### Cuándo elegir Repository pattern

1. Dominios complejos (reglas, invariantes, múltiples agregados).
2. Necesidad alta de tests unitarios aislados.
3. Arquitecturas DDD/CQRS/hexagonales.
4. Posible cambio de ORM o estrategia de persistencia en el tiempo.

#### Trade-offs

1. **Active Record**
   1. Pros: menos boilerplate, onboarding simple.
   2. Contras: acoplamiento fuerte a ORM y menor separación de responsabilidades.

2. **Repository**
   1. Pros: desacoplamiento, mantenibilidad, testabilidad.
   2. Contras: más capas/boilerplate inicial.

#### En NestJS (regla práctica)

1. Si estás construyendo un sistema empresarial que crecerá: empieza con Repository.
2. Si es un servicio simple de vida corta: Active Record puede ser suficiente.
3. En equipos grandes, Repository suele escalar mejor organizacionalmente.

#### Conclusión

Active Record optimiza velocidad de arranque; Repository optimiza evolución a
largo plazo. Elige según complejidad del dominio y horizonte del producto.

</details>

<details>
<summary>46. ¿Qué son las migraciones en TypeORM/Prisma y por qué synchronize: true es peligroso en producción?</summary>

#### NestJS + DB

Las **migraciones** son cambios versionados del esquema de base de datos
(tablas, columnas, índices, constraints) aplicados de forma controlada y repetible.

#### Qué aportan las migraciones

1. Historial explícito de evolución del esquema.
2. Despliegues reproducibles entre dev/staging/prod.
3. Revisión en PR (cambio de DB visible y auditado).
4. Rollback/forward planificado.

#### TypeORM / Prisma

1. **TypeORM**
   Genera/escribe migraciones (`migration:generate`, `migration:run`).

2. **Prisma**
   Usa `prisma migrate dev/deploy` con historial en carpeta `migrations/`.

#### Por qué `synchronize: true` es peligroso en producción

`synchronize: true` intenta alinear esquema automáticamente en runtime basándose
en entidades actuales. Riesgos:

1. Cambios no versionados ni auditables.
2. Posible pérdida de datos (drop/alter inesperado).
3. Comportamientos distintos según estado real de cada DB.
4. Imposible coordinar cambios complejos (backfills, índices concurrentes, zero-downtime).

#### Regla de producción

1. `synchronize: false`
2. Migraciones obligatorias en pipeline de deploy.
3. Backup y plan de rollback antes de cambios críticos.

#### Flujo recomendado

1. Cambias entidades/schema en código.
2. Generas migración.
3. Revisas SQL en PR.
4. Aplicas en staging.
5. Deploy a prod + `migrate deploy/run`.
6. Monitoreas errores/latencia tras cambio.

#### Buenas prácticas

1. Mantén migraciones pequeñas y atómicas.
2. Evita operaciones bloqueantes grandes en horas pico.
3. Separa migraciones de esquema y data backfills pesados.
4. Versiona índices/constraints explícitamente.
5. Automatiza verificación de migraciones pendientes en CI.

#### Conclusión

Migraciones = disciplina de cambio seguro del esquema.
`sync: true` puede parecer cómodo en dev, pero en producción es una fuente real
de incidentes y pérdida de control.

</details>

<details>
<summary>47. ¿Cómo implementar soft delete en TypeORM?</summary>

#### NestJS + TypeORM

**Soft delete** significa marcar un registro como eliminado sin borrarlo físicamente.
Esto permite auditoría, restauración y menor riesgo de pérdida accidental.

#### Cómo funciona en TypeORM

TypeORM soporta soft delete con una columna de fecha de borrado (normalmente
`deletedAt`) y métodos dedicados.

#### 1) Definir entidad con `@DeleteDateColumn`

```ts
import { Entity, PrimaryGeneratedColumn, Column, DeleteDateColumn } from 'typeorm';

@Entity('users')
export class UserEntity {
  @PrimaryGeneratedColumn('uuid')
  id: string;

  @Column({ unique: true })
  email: string;

  @DeleteDateColumn({ name: 'deleted_at', type: 'timestamp', nullable: true })
  deletedAt: Date | null;
}
```

#### 2) Marcar como eliminado (soft)

```ts
await this.usersRepo.softDelete(userId);
// o
await this.usersRepo.softRemove(userEntity);
```

#### 3) Restaurar registro

```ts
await this.usersRepo.restore(userId);
```

#### 4) Consultar incluyendo eliminados

Por defecto, TypeORM excluye soft-deleted.
Para incluirlos:

```ts
const all = await this.usersRepo.find({ withDeleted: true });
```

Solo eliminados:

```ts
const deletedOnly = await this.usersRepo.find({
  withDeleted: true,
  where: { deletedAt: Not(IsNull()) },
});
```

#### Buenas prácticas

1. Añadir índices sobre `deleted_at` si hay muchas consultas filtradas.
2. Ajustar constraints únicas considerando soft delete (índices parciales en PostgreSQL).
3. Definir política de purga física periódica si aplica compliance/costos.
4. No olvidar filtrar en queries custom SQL.

#### Riesgos comunes

1. Duplicados por unique key si no modelas índice parcial.
2. Reportes incorrectos por mezclar datos activos y borrados.
3. Acumular "basura" si nunca purgas registros antiguos.

#### Conclusión

Soft delete en TypeORM es simple de activar y muy útil operativamente, siempre
que acompañes con estrategia de índices, unicidad y ciclo de vida de datos.

</details>

<details>
<summary>48. ¿Cómo implementar transacciones en TypeORM con NestJS?</summary>

#### NestJS + TypeORM

Una transacción garantiza que un conjunto de operaciones de DB se ejecute de
forma atómica: o todo se confirma (`commit`) o todo se revierte (`rollback`).

#### Cuándo necesitas transacciones

1. Crear/actualizar varias entidades dependientes entre sí.
2. Transferencias de saldo/inventario.
3. Operaciones con invariantes que no deben quedar a medias.

#### Opción recomendada: `DataSource.transaction(...)`

```ts
import { Injectable } from '@nestjs/common';
import { DataSource } from 'typeorm';

@Injectable()
export class OrdersService {
  constructor(private readonly dataSource: DataSource) {}

  async createOrder(input: CreateOrderInput) {
    return this.dataSource.transaction(async (manager) => {
      const order = manager.create(OrderEntity, {
        customerId: input.customerId,
        status: 'CREATED',
      });
      await manager.save(order);

      for (const item of input.items) {
        const line = manager.create(OrderLineEntity, {
          orderId: order.id,
          productId: item.productId,
          qty: item.qty,
        });
        await manager.save(line);
      }

      return order;
    });
  }
}
```

#### Regla crítica

Dentro de la transacción usa **solo** `manager` transaccional, no repositories
inyectados fuera del callback. Si mezclas ambos, puedes romper atomicidad.

#### Control manual (QueryRunner) cuando necesitas más control

```ts
const qr = this.dataSource.createQueryRunner();
await qr.connect();
await qr.startTransaction();

try {
  // operaciones con qr.manager
  await qr.commitTransaction();
} catch (e) {
  await qr.rollbackTransaction();
  throw e;
} finally {
  await qr.release();
}
```

Útil para ajustar isolation level, locks explícitos o flujos complejos.

#### Buenas prácticas

1. Mantén transacciones cortas para evitar locks largos.
2. No hagas llamadas HTTP externas dentro de transacción DB.
3. Define isolation level cuando el caso lo exige.
4. Maneja retry para deadlocks/transient failures.
5. Instrumenta latencia y tasa de rollback.

#### Conclusión

En NestJS + TypeORM, `DataSource.transaction` cubre la mayoría de casos de forma
limpia; `QueryRunner` se reserva para escenarios avanzados de control transaccional.

</details>

<details>
<summary>49. ¿Qué es el problema N+1 y cómo lo resuelves en NestJS?</summary>

#### NestJS / DB

El problema **N+1** ocurre cuando haces 1 query para obtener una lista (N filas)
y luego ejecutas 1 query adicional por cada fila para cargar datos relacionados.
Resultado: demasiadas consultas y latencia alta.

#### Ejemplo típico

1. Query 1: obtener 100 pedidos.
2. Queries 2..101: obtener cliente para cada pedido.

Total: 101 queries en vez de 1-2.

#### Impacto

1. Más round-trips a DB.
2. p95/p99 peores bajo carga.
3. Escalabilidad pobre al crecer N.

#### Estrategias de solución en NestJS

1. **Eager/explicit joins** (TypeORM QueryBuilder)
2. **Batching/DataLoader** (especialmente en GraphQL)
3. **Preload por IDs (`IN (...)`)**
4. **Caching selectivo** para relaciones muy leídas

#### Solución 1: join en TypeORM

```ts
const orders = await this.ordersRepo
  .createQueryBuilder('o')
  .leftJoinAndSelect('o.customer', 'c')
  .leftJoinAndSelect('o.items', 'i')
  .where('o.createdAt >= :from', { from })
  .getMany();
```

#### Solución 2: DataLoader (GraphQL)

DataLoader agrupa múltiples requests de relación en una sola query por ciclo.

```ts
const users = await this.usersRepo.findBy({
  id: In(userIds),
});
```

Luego mapea resultados por clave y responde batch.

#### Buenas prácticas

1. Detecta N+1 con logs de queries/APM.
2. Evita relaciones `eager: true` globales sin control.
3. Diseña DTO/view-model para traer solo campos necesarios.
4. Usa paginación para limitar cardinalidad.
5. Añade índices a claves de join/filtro.

#### Regla práctica

Si un endpoint crece linealmente en número de queries con el tamaño de la lista,
tienes un N+1. Debe pasar a O(1) o casi constante de queries por request.

#### Conclusión

Resolver N+1 en NestJS es combinar estrategia de carga correcta (join/batch)
con observabilidad de queries para mantener latencia y costo bajo control.

</details>

<details>
<summary>50. ¿Qué es connection pooling y cómo configurarlo correctamente para una base de datos?</summary>

#### NestJS / DB

**Connection pooling** es la reutilización de un conjunto limitado de conexiones
abiertas a la base de datos, en lugar de abrir/cerrar una conexión por cada request.

#### Por qué importa

1. Reduce latencia de conexión.
2. Mejora throughput bajo carga concurrente.
3. Evita agotar recursos de DB y del servidor de aplicación.

#### Conceptos clave

1. `max` (pool size): máximo de conexiones simultáneas.
2. `min`: conexiones mínimas mantenidas.
3. `idleTimeout`: cuándo cerrar conexiones inactivas.
4. `acquireTimeout`: cuánto esperar una conexión libre.

#### Configuración ejemplo (TypeORM + Postgres)

```ts
TypeOrmModule.forRoot({
  type: 'postgres',
  host: process.env.DB_HOST,
  port: Number(process.env.DB_PORT),
  username: process.env.DB_USER,
  password: process.env.DB_PASSWORD,
  database: process.env.DB_NAME,
  synchronize: false,
  extra: {
    max: 20,
    min: 2,
    idleTimeoutMillis: 30000,
    connectionTimeoutMillis: 5000,
  },
});
```

#### Cómo dimensionar el pool (regla práctica inicial)

1. Empieza pequeño-moderado (10-30 por instancia).
2. Considera total global: `pool_por_instancia * número_de_instancias`.
3. Debe ser menor que `max_connections` de DB dejando margen para admin/otros servicios.

#### Errores comunes

1. Pool demasiado grande -> saturación de DB, más contención.
2. Pool demasiado pequeño -> colas y timeouts en app.
3. Ignorar límites cuando escalas horizontalmente.
4. No monitorear tiempo de espera para adquirir conexión.

#### Observabilidad recomendada

1. Métricas de pool: conexiones activas, idle, waiting.
2. Latencia de queries (p95/p99).
3. Errores de timeout/conexión rechazada.
4. Saturación CPU/IO en DB.

#### Buenas prácticas

1. Usa PgBouncer/RDS Proxy cuando la arquitectura lo requiera.
2. Mantén queries eficientes e indexadas (el pool no arregla SQL malo).
3. Separa workloads pesados (jobs/reportes) si compiten con tráfico online.
4. Ajusta pool tras pruebas de carga reales.

#### Conclusión

El pool correcto no es “más grande es mejor”; es equilibrio entre concurrencia,
capacidad real de DB y objetivos de latencia.

</details>

<details>
<summary>51. ¿Cómo protegerse contra SQL injection en TypeORM/Prisma?</summary>

#### NestJS / Seguridad DB

La protección contra **SQL injection** se basa en no concatenar input de usuario
en queries SQL y usar siempre mecanismos parametrizados del ORM/query builder.

#### Principios clave

1. Nunca construir SQL con interpolación directa de strings.
2. Usar APIs seguras de TypeORM/Prisma (param binding).
3. Validar y sanear input en borde de API (DTO + ValidationPipe).
4. Aplicar principio de mínimo privilegio en usuario de DB.

#### TypeORM: patrones seguros

1. `Repository.find({ where: { ... } })`
2. QueryBuilder con parámetros `:name`

```ts
// Seguro
await this.usersRepo
  .createQueryBuilder('u')
  .where('u.email = :email', { email: dto.email })
  .andWhere('u.status = :status', { status: 'active' })
  .getMany();
```

Evitar:

```ts
// Inseguro
await dataSource.query(`SELECT * FROM users WHERE email = '${email}'`);
```

#### Prisma: patrones seguros

Prisma parametriza queries del client por defecto:

```ts
await this.prisma.user.findMany({
  where: {
    email: dto.email,
  },
});
```

Si usas SQL raw, solo forma parametrizada:

```ts
await this.prisma.$queryRaw`SELECT * FROM "User" WHERE email = ${email}`;
```

Evitar `.$queryRawUnsafe(...)` con input no confiable.

#### Endurecimiento adicional

1. Validar tipos/rangos/formatos con `class-validator`.
2. Limitar campos de ordenación/filtro mediante allowlist.
3. Escapar identificadores dinámicos (columnas/tablas) o prohibirlos.
4. Usar roles DB sin permisos de DDL en runtime.
5. Registrar y alertar patrones sospechosos.

#### Error común

Pensar que ORM elimina todo riesgo automáticamente. El riesgo vuelve cuando:

1. usas SQL raw inseguro,
2. permites columnas dinámicas sin control,
3. mezclas input crudo en fragmentos de query.

#### Conclusión

TypeORM y Prisma son seguros por defecto en sus APIs normales, pero la seguridad
real depende de disciplina: parámetros, validación de input y mínimo privilegio
en base de datos.

</details>

<details>
<summary>52. ¿Cómo organizar correctamente la paginación en una API REST? (offset vs cursor-based)</summary>

#### NestJS / REST

La paginación evita respuestas enormes, reduce carga y mejora latencia.
Las dos estrategias principales son **offset-based** y **cursor-based**.

#### 1) Offset pagination

Parámetros típicos: `page`, `limit` o `offset`, `limit`.

Ejemplo:
`GET /users?page=3&limit=20` -> `OFFSET 40 LIMIT 20`

**Ventajas**

1. Simple de implementar y entender.
2. Fácil para UI con número de página.

**Desventajas**

1. Costosa en offsets grandes.
2. Inestable con inserciones/borrados entre requests (saltos/duplicados).

#### 2) Cursor pagination

Parámetros típicos: `cursor`, `limit`.

Ejemplo:
`GET /users?cursor=2026-01-01T10:00:00Z_123&limit=20`

Consulta basada en clave ordenable (ej. `createdAt`, `id`):
`WHERE (createdAt, id) < (:createdAt, :id) ORDER BY createdAt DESC, id DESC LIMIT 20`

**Ventajas**

1. Escala mejor en datasets grandes.
2. Más estable frente a cambios concurrentes.
3. Mejor rendimiento en feeds infinitos.

**Desventajas**

1. Implementación más compleja.
2. No navega tan fácil a “página N”.

#### ¿Cuál elegir?

1. **Offset**: backoffice/listados pequeños/medianos con necesidad de página explícita.
2. **Cursor**: timelines, logs, alta cardinalidad, tráfico alto.

#### Respuesta recomendada

Offset:

```json
{
  "data": [...],
  "meta": {
    "page": 3,
    "limit": 20,
    "total": 1240,
    "totalPages": 62
  }
}
```

Cursor:

```json
{
  "data": [...],
  "meta": {
    "limit": 20,
    "nextCursor": "2026-01-01T10:00:00Z_123",
    "hasNext": true
  }
}
```

#### Buenas prácticas

1. Define `maxLimit` para evitar abuso.
2. Orden estable y determinista (añadir `id` como tie-breaker).
3. Indexar columnas usadas en `ORDER BY`/`WHERE`.
4. Mantener contrato consistente en `meta`.
5. Documentar claramente en Swagger.

#### Conclusión

Offset es simple; cursor escala mejor y ofrece mayor consistencia en sistemas
con alto volumen. Elige según patrón de acceso y tamaño real de datos.

</details>

<details>
<summary>53. ¿Cómo versionar una API en NestJS? (URI, Header, Media type versioning)</summary>

#### NestJS

El versionado de API permite evolucionar endpoints sin romper clientes existentes.
NestJS soporta versionado nativo por URI, headers y media type.

#### Habilitar versionado

```ts
import { VersioningType } from '@nestjs/common';

app.enableVersioning({
  type: VersioningType.URI,
});
```

También puedes usar `HEADER` o `MEDIA_TYPE`.

#### 1) URI versioning

Formato típico: `/v1/users`, `/v2/users`.

```ts
@Controller({ path: 'users', version: '1' })
export class UsersV1Controller {}

@Controller({ path: 'users', version: '2' })
export class UsersV2Controller {}
```

**Pros**
1. Explícito y fácil de cachear/debuggear.
2. Muy claro para clientes y documentación.

**Contras**
1. URLs cambian al migrar versión.

#### 2) Header versioning

Cliente envía header, por ejemplo: `X-API-Version: 2`.

```ts
app.enableVersioning({
  type: VersioningType.HEADER,
  header: 'X-API-Version',
});
```

**Pros**
1. URL limpia y estable.

**Contras**
1. Menos visible para debugging manual.

#### 3) Media type versioning

Versión en `Accept`, por ejemplo:
`Accept: application/vnd.myapp.v2+json`

```ts
app.enableVersioning({
  type: VersioningType.MEDIA_TYPE,
  key: 'v=',
});
```

**Pros**
1. Alineado con content negotiation.

**Contras**
1. Más complejo para clientes y tooling.

#### Buenas prácticas

1. Define una estrategia única para toda la organización.
2. Mantén backward compatibility dentro de la misma versión mayor.
3. Depreca versiones con política y fechas claras.
4. Documenta versiones en Swagger (tags/rutas separadas).
5. Evita duplicación excesiva: comparte servicios, separa solo contratos/controladores.

#### Recomendación práctica

1. Para la mayoría de equipos: **URI versioning** (simple y operativo).
2. Header/media-type cuando necesitas URL estable o estándares HTTP avanzados.

#### Conclusión

Versionar bien en NestJS es tanto decisión técnica como de gobierno de API:
estrategia clara, deprecación controlada y contratos explícitos.

</details>

<details>
<summary>54. ¿Cómo implementar documentación Swagger en NestJS vía @nestjs/swagger?</summary>

#### NestJS

`@nestjs/swagger` genera documentación OpenAPI a partir de tus controllers, DTOs
y decorators. Esto crea contrato API visible y facilita integración frontend/terceros.

#### 1) Instalar paquetes

1. `@nestjs/swagger`
2. `swagger-ui-express`

#### 2) Configurar en `main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  const config = new DocumentBuilder()
    .setTitle('NestJS API')
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

Resultado: UI en `/docs`.

#### 3) Decorar endpoints y DTOs

Controller:

```ts
import { ApiBearerAuth, ApiOperation, ApiResponse, ApiTags } from '@nestjs/swagger';

@ApiTags('users')
@ApiBearerAuth()
@Controller('users')
export class UsersController {
  @Get(':id')
  @ApiOperation({ summary: 'Get user by id' })
  @ApiResponse({ status: 200, description: 'User returned' })
  @ApiResponse({ status: 404, description: 'User not found' })
  findOne() {}
}
```

DTO:

```ts
import { ApiProperty } from '@nestjs/swagger';

export class CreateUserDto {
  @ApiProperty({ example: 'user@example.com' })
  email: string;

  @ApiProperty({ minLength: 8 })
  password: string;
}
```

#### 4) Integrar con validación y auth

1. Usa `class-validator` para reglas que Swagger también reflejará parcialmente.
2. Declara esquemas de auth (`addBearerAuth`, `@ApiBearerAuth()`).
3. Documenta errores estándar (`400/401/403/404/500`).

#### Buenas prácticas

1. Agrupa por tags (`@ApiTags`) por dominio.
2. Mantén DTOs de request/response explícitos (no `any`).
3. Versiona documentación junto con API versioning.
4. Automatiza export OpenAPI JSON en CI para SDK generation.
5. Revisa contrato en PR cuando cambian endpoints.

#### Conclusión

Swagger en NestJS convierte tu API en un contrato operativo: explorable,
consistente y utilizable por equipos cliente y herramientas de automatización.

</details>

<details>
<summary>55. ¿Cómo implementar CORS en NestJS y cuándo se necesitan configuraciones personalizadas?</summary>

#### NestJS

CORS (*Cross-Origin Resource Sharing*) controla qué orígenes pueden invocar tu API
desde el navegador. En NestJS se configura al arrancar la app o por adapter.

#### Configuración básica

```ts
const app = await NestFactory.create(AppModule);

app.enableCors({
  origin: ['https://app.example.com'],
  methods: ['GET', 'POST', 'PUT', 'PATCH', 'DELETE', 'OPTIONS'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  credentials: true,
});
```

#### Cuándo necesitas configuración personalizada

1. Frontend y API en dominios/subdominios distintos.
2. Cookies/sesiones (`credentials: true`).
3. Múltiples orígenes por entorno (dev/staging/prod).
4. Integración con partners externos con políticas específicas.

#### Opciones importantes

1. `origin`
   Lista, regex o función dinámica para validar origen.

2. `credentials`
   Permite cookies/headers de auth entre dominios.
   Si es `true`, no puedes usar `origin: '*'`.

3. `methods`, `allowedHeaders`, `exposedHeaders`
   Controlan métodos y cabeceras permitidas/expuestas.

4. `maxAge`
   Cache del preflight (`OPTIONS`) para reducir overhead.

#### Origen dinámico (allowlist)

```ts
const allowed = new Set([
  'https://app.example.com',
  'https://admin.example.com',
]);

app.enableCors({
  origin: (origin, callback) => {
    if (!origin || allowed.has(origin)) return callback(null, true);
    return callback(new Error('Not allowed by CORS'), false);
  },
  credentials: true,
});
```

#### Buenas prácticas

1. No usar `*` en producción para APIs autenticadas.
2. Mantener allowlist explícita por entorno.
3. Revisar preflight para métodos no simples (`PUT/PATCH/DELETE`).
4. Combinar CORS con CSRF/protecciones de sesión cuando hay cookies.
5. Loguear rechazos CORS para troubleshooting.

#### Errores comunes

1. `credentials: true` con `origin: '*'`.
2. Olvidar `Authorization` en `allowedHeaders`.
3. Romper preflight por middleware/proxy mal configurado.

#### Conclusión

CORS no es "activar y olvidar": debe alinearse con tu modelo de auth, dominios
y entorno de despliegue para evitar bloqueos funcionales o aperturas inseguras.

</details>

<details>
<summary>56. ¿Qué es la idempotencia en el contexto de una API REST y cómo garantizarla?</summary>

#### NestJS / REST

La **idempotencia** significa que repetir la misma operación varias veces produce
el mismo efecto final que ejecutarla una sola vez.

#### Ejemplos rápidos

1. `GET /users/1` -> naturalmente idempotente.
2. `PUT /users/1` con el mismo body -> idempotente.
3. `POST /payments` -> normalmente **no** idempotente si crea cobros duplicados.

#### Por qué importa

1. Reintentos de cliente/red sin duplicar efectos.
2. Mayor resiliencia en integraciones externas.
3. Prevención de operaciones críticas duplicadas (pagos, pedidos, envíos).

#### Cómo garantizar idempotencia

1. **Idempotency-Key** en operaciones no seguras (`POST`).
2. Guardar resultado de la primera ejecución por clave.
3. Si llega la misma clave, devolver la respuesta previa sin repetir lógica.

#### Patrón práctico

1. Cliente envía header: `Idempotency-Key: <uuid>`.
2. Servidor valida y persiste clave + hash de request + estado/respuesta.
3. Si clave nueva: procesa negocio y almacena resultado.
4. Si clave existente con mismo payload: retorna resultado almacenado.
5. Si clave existente con payload distinto: responder `409 Conflict`.

#### Consideraciones técnicas

1. Scope de clave por usuario/tenant + endpoint.
2. TTL para limpiar claves antiguas.
3. Lock transaccional para evitar carrera de doble procesamiento.
4. Persistencia en DB/Redis según criticidad.

#### Buenas prácticas

1. Hacer idempotentes todas las operaciones financieras.
2. Diseñar handlers para tolerar retries.
3. Combinar con outbox/inbox en flujos distribuidos.
4. Documentar contrato de idempotencia en Swagger.

#### Conclusión

La idempotencia no es opcional en operaciones críticas: es una garantía de
consistencia frente a fallos de red, retries y ejecución duplicada.

</details>

<details>
<summary>57. ¿Cómo implementar rate limiting en NestJS? (@nestjs/throttler)</summary>

#### NestJS

En NestJS, el enfoque estándar es `@nestjs/throttler`, que limita cantidad de
requests por ventana de tiempo para proteger la API de abuso y picos.

#### 1) Instalar

1. `@nestjs/throttler`

#### 2) Configuración global

```ts
import { Module } from '@nestjs/common';
import { APP_GUARD } from '@nestjs/core';
import { ThrottlerGuard, ThrottlerModule } from '@nestjs/throttler';

@Module({
  imports: [
    ThrottlerModule.forRoot([
      {
        ttl: 60_000,
        limit: 100,
      },
    ]),
  ],
  providers: [
    {
      provide: APP_GUARD,
      useClass: ThrottlerGuard,
    },
  ],
})
export class AppModule {}
```

Esto aplica 100 requests por 60s por cliente (por defecto, IP).

#### 3) Override por endpoint/controller

```ts
import { Controller, Get } from '@nestjs/common';
import { SkipThrottle, Throttle } from '@nestjs/throttler';

@Controller('auth')
export class AuthController {
  @Throttle({ default: { limit: 5, ttl: 60_000 } })
  @Get('login-attempt')
  loginAttempt() {
    return { ok: true };
  }

  @SkipThrottle()
  @Get('health')
  health() {
    return { ok: true };
  }
}
```

#### 4) Clave de tracking personalizada

En producción suele convenir limitar por `userId`/API key (no solo IP),
especialmente detrás de proxies/NAT.

Puedes extender `ThrottlerGuard` para personalizar `getTracker()`.

#### Buenas prácticas

1. Usa límites distintos por ruta (auth más estricto que lectura pública).
2. Activa `trust proxy` si usas load balancer/reverse proxy.
3. Combina con WAF/CDN rate limiting para defensa en capas.
4. Expón headers de rate-limit cuando sea útil para clientes.
5. Monitorea `429 Too Many Requests` para ajustar umbrales.

#### Errores comunes

1. Un único límite global para todo (rompe UX o deja huecos).
2. Limitar solo por IP en sistemas multi-tenant internos.
3. No excluir health checks internos.

#### Conclusión

`@nestjs/throttler` da protección rápida y efectiva. La clave real está en
ajustar políticas por endpoint y por identidad de cliente.

</details>

<details>
<summary>58. ¿Cómo implementar request tracing (añadir requestId a cada solicitud)?</summary>

#### NestJS

`requestId` permite correlacionar logs, errores y llamadas entre servicios para
troubleshooting rápido en producción.

#### Objetivo

1. Generar/propagar un `requestId` por request.
2. Adjuntarlo al contexto de ejecución y logs.
3. Devolverlo en headers/respuestas para correlación cliente-servidor.

#### Patrón básico (middleware)

```ts
import { Injectable, NestMiddleware } from '@nestjs/common';
import { randomUUID } from 'crypto';
import { Request, Response, NextFunction } from 'express';

@Injectable()
export class RequestIdMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: NextFunction) {
    const incoming = req.header('x-request-id');
    const requestId = incoming?.trim() || randomUUID();

    (req as any).requestId = requestId;
    res.setHeader('x-request-id', requestId);

    next();
  }
}
```

Registrar middleware globalmente en `AppModule`.

#### Logging con requestId

En logger/interceptor:

1. Leer `(req as any).requestId`.
2. Incluirlo en cada log estructurado.
3. Adjuntar también `userId`, `path`, `method`, `status`, `latency`.

#### Propagación entre servicios

Cuando llamas APIs externas/microservicios:

1. Reenviar `x-request-id` en headers.
2. Si usas OpenTelemetry, mapear a `traceId`/`spanId`.

#### Buenas prácticas

1. Aceptar `x-request-id` externo solo si confías en origen; si no, regenéralo.
2. Usar formato UUID (u otro estándar consistente).
3. No mezclar requestId con datos sensibles.
4. Devolver requestId en errores para soporte.

#### Complemento recomendado

1. `requestId` para correlación humana rápida.
2. `traceId/spanId` para tracing distribuido profundo.

Ambos pueden coexistir y mapearse.

#### Conclusión

Request tracing en NestJS empieza con un middleware simple, pero su valor real
aparece cuando se integra en logging, observabilidad y comunicación entre servicios.

</details>

<details>
<summary>59. ¿Cómo manejar multipart/form-data y subida de archivos en NestJS?</summary>

#### NestJS

En NestJS (adapter Express), la subida de archivos se hace normalmente con
**Multer** mediante interceptors (`FileInterceptor`, `FilesInterceptor`, etc.).

#### Casos comunes

1. Subida de un archivo.
2. Subida múltiple.
3. Archivo + campos de formulario.
4. Validación de tipo/tamaño y almacenamiento externo (S3, GCS, etc.).

#### 1) Endpoint básico (un archivo)

```ts
import {
  BadRequestException,
  Controller,
  Post,
  UploadedFile,
  UseInterceptors,
} from '@nestjs/common';
import { FileInterceptor } from '@nestjs/platform-express';

@Controller('uploads')
export class UploadsController {
  @Post('avatar')
  @UseInterceptors(FileInterceptor('file'))
  uploadAvatar(@UploadedFile() file: Express.Multer.File) {
    if (!file) throw new BadRequestException('File is required');

    return {
      filename: file.originalname,
      mimetype: file.mimetype,
      size: file.size,
    };
  }
}
```

#### 2) Validación de archivo

Puedes validar con `ParseFilePipe`:

```ts
@UploadedFile(
  new ParseFilePipe({
    validators: [
      new MaxFileSizeValidator({ maxSize: 2 * 1024 * 1024 }),
      new FileTypeValidator({ fileType: /(jpg|jpeg|png)$/ }),
    ],
  }),
)
file: Express.Multer.File
```

#### 3) Configuración de almacenamiento

Opciones típicas:

1. `memoryStorage` -> útil para enviar a S3 directamente.
2. `diskStorage` -> guardar temporal/local con nombre controlado.

Ejemplo:

```ts
@UseInterceptors(
  FileInterceptor('file', {
    limits: { fileSize: 5 * 1024 * 1024 },
    fileFilter: (_req, file, cb) => {
      if (!file.mimetype.startsWith('image/')) return cb(new Error('Invalid type'), false);
      cb(null, true);
    },
  }),
)
```

#### Buenas prácticas de seguridad

1. Validar mimetype y extensión real.
2. Limitar tamaño y cantidad de archivos.
3. No confiar en nombre original del archivo.
4. Escanear malware si el caso lo requiere.
5. Guardar fuera del contenedor local para producción (S3/GCS).

#### Conclusión

NestJS facilita multipart uploads con interceptors de Multer; la clave en
producción es validación estricta, límites y estrategia segura de almacenamiento.

</details>

<details>
<summary>60. ¿Cómo implementar compresión (gzip/brotli) en NestJS?</summary>

#### NestJS

La compresión reduce tamaño de respuesta y mejora latencia percibida,
especialmente en redes lentas. En NestJS (Express), se habilita con middleware
`compression`.

#### 1) Instalación

1. `compression`

#### 2) Habilitar en `main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import compression from 'compression';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    compression({
      threshold: 1024,
      level: 6,
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

`threshold` evita comprimir respuestas muy pequeñas.

#### Gzip vs Brotli

1. **gzip**: compatibilidad amplia, buen equilibrio CPU/ratio.
2. **brotli**: mejor ratio de compresión, más costo CPU.

En muchos entornos, reverse proxy/CDN negocia automáticamente mejor algoritmo
según `Accept-Encoding` del cliente.

#### Dónde aplicar compresión

1. Respuestas JSON medianas/grandes.
2. Payloads textuales (HTML/CSS/JS si salen por app).
3. No comprimir archivos ya comprimidos (zip, mp4, jpg, png).

#### Buenas prácticas

1. Preferir compresión en edge/proxy (Nginx, CDN) cuando sea posible.
2. Medir costo CPU vs ahorro de ancho de banda.
3. Mantener `threshold` para evitar overhead inútil.
4. No comprimir secretos reflejados junto a input atacante (riesgos tipo BREACH en escenarios específicos).

#### Observabilidad

1. Monitorea tamaño antes/después (`Content-Length` / transfer).
2. Observa impacto en p95 latencia y CPU.
3. Ajusta nivel de compresión según carga real.

#### Conclusión

Compresión en NestJS es simple de activar y suele dar mejora inmediata en red;
la optimización real está en elegir dónde comprimir (app vs proxy) y con qué costo CPU.

</details>

<details>
<summary>61. ¿Cómo implementar helmet y qué headers HTTP establece?</summary>

#### NestJS

`helmet` es un middleware de seguridad que configura múltiples headers HTTP para
reducir riesgos comunes en aplicaciones web/API.

#### 1) Instalación

1. `helmet`

#### 2) Habilitar en `main.ts`

```ts
import { NestFactory } from '@nestjs/core';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.use(
    helmet({
      contentSecurityPolicy: false,
    }),
  );

  await app.listen(3000);
}
bootstrap();
```

`contentSecurityPolicy` a veces se desactiva temporalmente en APIs o durante setup
inicial; en frontend debe configurarse explícitamente.

#### Headers que helmet suele gestionar

Según configuración y versión, típicamente incluye:

1. `X-Content-Type-Options: nosniff`
2. `X-Frame-Options` (anti-clickjacking)
3. `Referrer-Policy`
4. `Cross-Origin-Opener-Policy`
5. `Cross-Origin-Resource-Policy`
6. `Origin-Agent-Cluster`
7. `Strict-Transport-Security` (HSTS, en HTTPS)
8. `Content-Security-Policy` (si está habilitado)

#### Cuándo personalizar

1. Si sirves frontend con scripts externos -> ajustar CSP.
2. Si usas iframes legítimos -> ajustar `frame-ancestors`/`X-Frame-Options`.
3. Si hay recursos cross-origin necesarios -> ajustar CORP/COOP.

#### Buenas prácticas

1. Activa `helmet` por defecto en producción.
2. Configura CSP de forma explícita y testeada.
3. Usa HTTPS + HSTS en edge/proxy.
4. Revisa headers finales con herramientas de seguridad (Mozilla Observatory, etc.).
5. No depender solo de headers: combinar con validación, auth, rate limiting y sanitización.

#### Conclusión

`helmet` aporta un baseline de hardening HTTP rápido y efectivo. El valor real
está en personalizar políticas según tu arquitectura (API pura vs app web completa).

</details>

<details>
<summary>62. ¿Cuáles son las principales vulnerabilidades OWASP y cómo protegerse?</summary>

#### NestJS / Seguridad

OWASP Top 10 resume los riesgos web más críticos. En NestJS, la defensa correcta
es multicapa: validación, auth robusta, hardening HTTP, control de acceso,
monitorización y prácticas seguras de desarrollo.

#### Riesgos OWASP más relevantes (resumen práctico)

1. **Broken Access Control**
   Usuarios acceden a recursos no autorizados.
   Mitigación: guards/policies (RBAC/ABAC), checks por recurso, deny-by-default.

2. **Cryptographic Failures**
   Datos sensibles sin cifrado adecuado.
   Mitigación: HTTPS, secretos en vault, hashing fuerte (`bcrypt/argon2`), rotación de claves.

3. **Injection (SQL/NoSQL/Command)**
   Input malicioso ejecuta comandos/queries.
   Mitigación: queries parametrizadas (ORM), validación estricta DTO, no concatenar SQL.

4. **Insecure Design**
   Lógica de negocio insegura por diseño.
   Mitigación: threat modeling, revisiones de arquitectura, controles de negocio explícitos.

5. **Security Misconfiguration**
   Config por defecto débil.
   Mitigación: `helmet`, CORS estricto, desactivar debug en prod, mínimos permisos.

6. **Vulnerable/Outdated Components**
   Dependencias con CVE.
   Mitigación: `npm audit`, SCA en CI, política de updates/patching.

7. **Identification & Authentication Failures**
   Fallos en login/sesiones/tokens.
   Mitigación: JWT corto + refresh rotation, rate limit en auth, MFA según riesgo.

8. **Software and Data Integrity Failures**
   Supply chain o artefactos no confiables.
   Mitigación: lockfiles, firmas/verificación de imágenes, CI protegido.

9. **Security Logging & Monitoring Failures**
   Falta trazabilidad de incidentes.
   Mitigación: logs estructurados, requestId/traceId, alertas SIEM.

10. **SSRF**
   El servidor accede a destinos internos por input atacante.
   Mitigación: allowlist de destinos, bloquear IPs internas, timeouts estrictos.

#### Checklist mínima en NestJS

1. `ValidationPipe` global con `whitelist` y `forbidNonWhitelisted`.
2. `helmet` + CORS controlado.
3. Guards de authz + políticas por recurso.
4. Rate limiting en endpoints críticos.
5. Gestión segura de secretos (`ConfigModule` + secret manager).
6. Error handling sin filtrar stack/secretos al cliente.
7. Dependencias auditadas y pipeline de seguridad en CI/CD.

#### Conclusión

OWASP no se cubre con una sola librería: en NestJS la protección real viene de
arquitectura segura + controles transversales + disciplina operativa continua.

</details>

<details>
<summary>63. ¿Cómo usar HttpModule (axios) en NestJS para solicitudes a APIs externas?</summary>

#### NestJS

`HttpModule` de `@nestjs/axios` integra Axios en el sistema DI de NestJS y
permite llamar APIs externas con configuración centralizada, interceptores y
observables RxJS.

#### 1) Instalación

1. `@nestjs/axios`
2. `axios`

#### 2) Registro del módulo

```ts
import { Module } from '@nestjs/common';
import { HttpModule } from '@nestjs/axios';

@Module({
  imports: [
    HttpModule.register({
      timeout: 5000,
      maxRedirects: 3,
      baseURL: 'https://api.example.com',
      headers: {
        'User-Agent': 'nestjs-service/1.0',
      },
    }),
  ],
  providers: [ExternalApiService],
  exports: [ExternalApiService],
})
export class ExternalApiModule {}
```

#### 3) Uso en servicio

`HttpService` devuelve `Observable<AxiosResponse<T>>`.
Puedes usar `firstValueFrom` para trabajar con `async/await`.

```ts
import { Injectable, BadGatewayException } from '@nestjs/common';
import { HttpService } from '@nestjs/axios';
import { firstValueFrom } from 'rxjs';

interface UserResponse {
  id: string;
  email: string;
}

@Injectable()
export class ExternalApiService {
  constructor(private readonly http: HttpService) {}

  async getUser(id: string): Promise<UserResponse> {
    try {
      const { data } = await firstValueFrom(
        this.http.get<UserResponse>(`/users/${id}`),
      );
      return data;
    } catch (e) {
      throw new BadGatewayException('Upstream API error');
    }
  }
}
```

#### 4) Configuración asíncrona (recomendada)

Con `registerAsync` + `ConfigService` para secretos/tokens por entorno.

#### Buenas prácticas

1. Define `timeout` siempre.
2. Añade retry/backoff para fallos transitorios.
3. Mapea errores externos a errores internos consistentes.
4. Usa DTOs/interfaces tipadas para respuestas.
5. Propaga `requestId`/tracing headers en llamadas salientes.

#### Conclusión

`HttpModule` convierte llamadas HTTP externas en una capacidad estructurada de
NestJS: tipada, configurable y observable.

</details>

<details>
<summary>64. ¿Cómo agregar interceptores globales a axios en NestJS? (añadir headers, logging)</summary>

#### NestJS

Con `HttpModule` (`@nestjs/axios`), puedes acceder a la instancia Axios y
registrar interceptores globales para todas las llamadas salientes.

#### Objetivos típicos

1. Añadir headers comunes (`Authorization`, `x-request-id`, `x-service-name`).
2. Registrar logs de request/response.
3. Normalizar errores de upstream.
4. Medir latencia de llamadas externas.

#### Implementación en `onModuleInit`

```ts
import { Injectable, OnModuleInit } from '@nestjs/common';
import { HttpService } from '@nestjs/axios';

@Injectable()
export class HttpClientSetupService implements OnModuleInit {
  constructor(private readonly http: HttpService) {}

  onModuleInit() {
    const axios = this.http.axiosRef;

    axios.interceptors.request.use((config) => {
      config.headers = config.headers ?? {};
      config.headers['x-service-name'] = 'nestjs-api';
      config.headers['x-request-id'] = getRequestIdFromContext() ?? 'no-request-id';
      return config;
    });

    axios.interceptors.response.use(
      (response) => {
        // logging de éxito
        return response;
      },
      (error) => {
        // logging + mapeo de error
        return Promise.reject(error);
      },
    );
  }
}
```

#### Propagación de `requestId`

Si quieres pasar `x-request-id` automáticamente:

1. Guarda request context con AsyncLocalStorage/CLS.
2. Léelo en interceptor request de axios.
3. Reenvíalo a servicios downstream.

#### Logging recomendado

1. URL, método, status code.
2. Duración (`Date.now()` start/end).
3. requestId/traceId.
4. Error type (timeout, 4xx, 5xx, network).

#### Buenas prácticas

1. Registra interceptores una sola vez (evita duplicados en hot reload/tests).
2. No loguees secretos/tokens completos.
3. Define timeout/retry/circuit breaker además de interceptores.
4. Mapea errores axios a excepciones internas consistentes.

#### Conclusión

Los interceptores globales de Axios en NestJS son el punto correcto para
estandarizar headers, observabilidad y manejo de errores de APIs externas.

</details>

<details>
<summary>65. ¿Cómo tipar correctamente respuestas de APIs externas en TypeScript?</summary>

#### NestJS / TypeScript

Tipar respuestas externas reduce errores de integración y hace el código más
predecible. La regla clave: nunca confiar ciegamente en el proveedor; combina
**tipado estático** + **validación runtime** en el borde.

#### Estrategia recomendada

1. Definir interfaces/DTOs para contrato esperado.
2. Tipar `HttpService`/axios con genéricos (`get<T>()`).
3. Validar respuesta con zod/io-ts/class-validator cuando el riesgo lo requiera.
4. Mapear payload externo a modelo interno estable.

#### Ejemplo con `HttpService`

```ts
interface ExternalUserDto {
  id: string;
  email: string;
  created_at: string;
}

interface User {
  id: string;
  email: string;
  createdAt: Date;
}

const { data } = await firstValueFrom(
  this.http.get<ExternalUserDto>(`/users/${id}`),
);

const user: User = {
  id: data.id,
  email: data.email,
  createdAt: new Date(data.created_at),
};
```

#### Validación runtime (zod) para robustez

```ts
import { z } from 'zod';

const ExternalUserSchema = z.object({
  id: z.string(),
  email: z.string().email(),
  created_at: z.string(),
});

const parsed = ExternalUserSchema.parse(data);
```

#### Buenas prácticas

1. Separar **External DTO** de **Domain Model**.
2. No propagar payload externo crudo por toda la app.
3. Tratar campos opcionales/nullables explícitamente.
4. Versionar contratos de proveedores críticos.
5. Manejar backward-compat y defaults cuando proveedor cambia.

#### Errores comunes

1. Usar `any` o casteos forzados (`as X`) sin validar.
2. Mezclar naming externo (`snake_case`) con interno (`camelCase`) sin mapeo.
3. Confiar en docs del proveedor sin tests de contrato.

#### Conclusión

En TypeScript, el tipado estático ayuda, pero no basta para datos externos.
La combinación ganadora es: tipos claros + validación runtime + mapeo a modelo interno.

</details>

<details>
<summary>66. ¿Cómo implementar lógica de reintentos para solicitudes HTTP externas en NestJS?</summary>

#### NestJS

Los reintentos ayudan a superar fallos transitorios (timeouts, 5xx, errores de red),
pero deben aplicarse con control para no amplificar incidentes.

#### Principios clave

1. Reintentar solo errores transitorios.
2. Usar backoff (preferible exponencial + jitter).
3. Limitar número máximo de intentos.
4. Definir timeout por intento.
5. Evitar retry ciego en operaciones no idempotentes.

#### Ejemplo con RxJS (`HttpService`)

```ts
import { Injectable, BadGatewayException } from '@nestjs/common';
import { HttpService } from '@nestjs/axios';
import { firstValueFrom, throwError, timer } from 'rxjs';
import { mergeMap, retryWhen } from 'rxjs/operators';

@Injectable()
export class ExternalClient {
  constructor(private readonly http: HttpService) {}

  async getProfile(userId: string) {
    const maxRetries = 3;

    const request$ = this.http.get(`/profiles/${userId}`, { timeout: 3000 }).pipe(
      retryWhen((errors) =>
        errors.pipe(
          mergeMap((error, attempt) => {
            const retryCount = attempt + 1;
            const status = error?.response?.status;
            const transient = !status || status >= 500 || status === 429;

            if (!transient || retryCount > maxRetries) {
              return throwError(() => error);
            }

            const backoffMs = Math.min(1000 * 2 ** attempt, 5000);
            const jitter = Math.floor(Math.random() * 200);
            return timer(backoffMs + jitter);
          }),
        ),
      ),
    );

    try {
      const { data } = await firstValueFrom(request$);
      return data;
    } catch {
      throw new BadGatewayException('Upstream service unavailable');
    }
  }
}
```

#### Qué reintentar y qué no

1. Sí: timeouts, ECONNRESET, 502/503/504, 429 (con respeto a Retry-After).
2. No: 400/401/403/404 (errores de cliente/negocio).
3. POST no idempotente: solo con idempotency-key o semántica segura.

#### Buenas prácticas

1. Combinar retry con circuit breaker.
2. Loggear intentos (`attempt`, `delay`, `cause`).
3. Métricas: tasa de retries, éxito tras retry, retries agotados.
4. Mantener presupuestos de latencia (retry no debe romper SLA).

#### Conclusión

El retry bien diseñado mejora resiliencia; mal diseñado empeora cascadas de fallo.
La clave es selectividad, backoff y límites estrictos.

</details>

<details>
<summary>67. ¿Qué es el patrón Circuit Breaker y cuándo lo necesitas?</summary>

#### NestJS / Resilience

El **Circuit Breaker** protege tu servicio de dependencias inestables (API externa,
DB, broker) cortando temporalmente llamadas cuando detecta tasa alta de fallos.

#### Problema que resuelve

Sin circuit breaker:

1. Sigues llamando a un upstream caído.
2. Aumenta latencia por timeouts.
3. Se consume pool/hilos/CPU.
4. Se produce efecto cascada y caída general.

#### Estados del circuito

1. **Closed**: tráfico normal; se monitorean errores.
2. **Open**: se bloquean llamadas y se responde fallo rápido (fast-fail).
3. **Half-Open**: se permiten pocas llamadas de prueba; si mejoran, vuelve a Closed.

#### Cuándo aplicarlo

1. Llamadas HTTP a servicios externos críticos.
2. Integraciones con latencia/fallo variable.
3. Operaciones remotas con alto costo de timeout.
4. Arquitecturas microservicio con riesgo de fallo en cascada.

#### Integración en NestJS (patrón)

1. Encapsula cliente externo en un service dedicado.
2. Envuelve llamadas con librería de circuit breaker (p.ej. `opossum`) o implementación propia.
3. Define thresholds: error rate, timeout, volume mínimo.
4. Añade fallback controlado (respuesta degradada/cache).

#### Buenas prácticas

1. Combinar con timeout + retry + bulkhead (no usar una sola técnica aislada).
2. Ajustar umbrales con métricas reales, no valores arbitrarios.
3. Exponer estado del circuito en observabilidad/health checks.
4. Evitar retries agresivos cuando el circuito está Open.

#### Riesgos comunes

1. Umbral demasiado sensible -> abre circuito de más (falsos positivos).
2. Umbral demasiado laxo -> abre demasiado tarde.
3. Fallback incoherente que rompe contrato de negocio.

#### Conclusión

Circuit Breaker es un mecanismo de contención: no arregla el upstream, pero evita
que su fallo derribe tu servicio y gana tiempo para recuperación.

</details>

<details>
<summary>68. ¿Cómo implementar caching (in-memory, Redis) y cuándo usar cada enfoque?</summary>

#### NestJS

El caching reduce latencia y carga en DB/servicios externos. En NestJS puedes usar
cache en memoria local o distribuido (Redis), según escala y consistencia requerida.

#### Opciones principales

1. **In-memory cache**
   Vive dentro de la instancia Node.

2. **Redis cache**
   Cache compartida entre instancias/servicios.

#### ¿Cuándo usar in-memory?

1. App simple o una sola instancia.
2. Datos pequeños y no críticos.
3. Necesidad de latencia mínima sin infraestructura extra.

Limitación: no se comparte entre réplicas; se pierde al reiniciar.

#### ¿Cuándo usar Redis?

1. Despliegue horizontal (múltiples pods/instancias).
2. Necesidad de consistencia razonable entre nodos.
3. Cache central para varios servicios.
4. Funciones extra: TTL fino, invalidación por patrón, pub/sub.

#### Implementación básica en NestJS

Con `@nestjs/cache-manager`:

```ts
import { CacheModule } from '@nestjs/cache-manager';

@Module({
  imports: [
    CacheModule.register({
      ttl: 60_000,
      max: 1000,
    }),
  ],
})
export class AppModule {}
```

Uso:

```ts
constructor(@Inject(CACHE_MANAGER) private cache: Cache) {}

const cached = await this.cache.get<UserDto>(key);
if (cached) return cached;

const fresh = await this.repo.findUser(id);
await this.cache.set(key, fresh, 60_000);
return fresh;
```

Para Redis, registras store redis en `CacheModule` (según versión/adapter).

#### Patrones comunes

1. Cache-aside (el más usado): leer cache -> miss -> DB -> set cache.
2. Read-through (menos común en Nest directo).
3. Write-through/write-behind según caso avanzado.

#### Buenas prácticas

1. Definir claves con namespace (`user:${id}`).
2. TTL acorde a volatilidad del dato.
3. Evitar cachear respuestas muy personalizadas sin incluir contexto en clave.
4. Medir hit rate, latencia y tamaño.
5. Plan de invalidación explícito (no confiar solo en TTL).

#### Conclusión

In-memory es rápido y simple para escenarios pequeños; Redis es la opción
correcta para producción distribuida y consistencia entre instancias.

</details>

<details>
<summary>69. ¿Qué es la invalidación de caché y cómo implementarla correctamente?</summary>

#### NestJS / Caching

La **invalidación de caché** es el proceso de eliminar o actualizar entradas
cacheadas cuando cambian los datos fuente. Es la parte más crítica del caching.

#### Problema que resuelve

Sin invalidación correcta:

1. Sirves datos obsoletos.
2. Rompes consistencia de negocio.
3. Generas bugs difíciles de reproducir.

#### Estrategias principales

1. **TTL-based expiration**
   La entrada expira automáticamente tras un tiempo.

2. **Event/Write-based invalidation**
   Al crear/actualizar/borrar datos, invalidas claves relacionadas.

3. **Namespace/versioned keys**
   Cambias versión de clave para “invalidar en bloque”.

4. **Tag/pattern invalidation** (según store)
   Borras por prefijo/patrón cuando una entidad afecta múltiples vistas.

#### Patrón recomendado (cache-aside + write invalidation)

1. Read path:
   1. Busca en cache.
   2. Miss -> lee DB.
   3. Guarda en cache con TTL.

2. Write path:
   1. Escribe DB.
   2. Si commit exitoso -> elimina/actualiza claves dependientes.

#### Ejemplo conceptual

1. Claves:
   1. `user:123`
   2. `users:list:page:1`

2. Update user 123:
   1. invalidar `user:123`
   2. invalidar listas que puedan contenerlo (prefijo/tag o versiones)

#### Buenas prácticas

1. Diseñar claves predecibles desde el inicio.
2. Preferir invalidación explícita en writes críticos.
3. Usar TTL como red de seguridad, no estrategia única.
4. Evitar invalidación excesiva (thundering herd).
5. Añadir jitter al TTL para evitar expiración masiva simultánea.

#### Riesgos comunes

1. Invalidar solo detalle y olvidar agregados/listas.
2. Borrar cache antes de commit (puede rehidratar con datos viejos).
3. No coordinar invalidación en despliegues multi-instancia.

#### Conclusión

Caching sin invalidación correcta crea más problemas que beneficios. Diseña
política de claves + eventos de escritura + TTL de respaldo desde el principio.

</details>

<details>
<summary>70. ¿Cuándo deberías usar Observables en lugar de Promises en NestJS?</summary>

#### NestJS

En NestJS puedes usar tanto `Promise` como `Observable`. La elección depende del
patrón de flujo: valor único vs stream/composición reactiva.

#### Usa `Promise` cuando

1. Esperas **un solo resultado** asíncrono.
2. El flujo es simple request/response.
3. Quieres legibilidad directa con `async/await`.

Ejemplo típico: CRUD en DB, llamada HTTP única.

#### Usa `Observable` cuando

1. Manejas **múltiples valores en el tiempo** (streaming).
2. Necesitas composición reactiva avanzada (retry, debounce, merge, cancelación).
3. Trabajas con WebSockets, eventos, microservicios, SSE.
4. Quieres pipelines declarativos de operadores RxJS.

#### Casos concretos en NestJS

1. `HttpService` devuelve Observables por defecto.
2. `@WebSocketGateway` y event streams encajan natural con RxJS.
3. Microservices transport pueden modelarse con patrones reactivos.

#### Regla práctica

1. Si el handler devuelve una sola respuesta: `Promise`.
2. Si el dominio es stream/event-driven o requiere operadores RxJS: `Observable`.

#### Interoperabilidad

Puedes convertir entre ambos:

1. Observable -> Promise: `firstValueFrom()` / `lastValueFrom()`.
2. Promise -> Observable: `from(promise)`.

#### Riesgos comunes

1. Usar Observables en exceso para casos simples (complejidad innecesaria).
2. No manejar unsubscribe/cancelación en flujos largos.
3. Mezclar estilos sin convención de equipo.

#### Conclusión

`Promise` es el default para casos lineales; `Observable` brilla en flujos
reactivos, streaming y composición avanzada de eventos.

</details>

<details>
<summary>71. ¿Cuál es la diferencia entre async/await y RxJS para manejar lógica asíncrona, y cuándo usar cada enfoque?</summary>

#### NestJS / TypeScript

`async/await` y RxJS resuelven asincronía, pero con modelos mentales distintos:
lineal imperativo vs reactivo por streams.

#### 1) `async/await`

**Qué es**

Sintaxis sobre Promises para escribir flujo asíncrono de forma secuencial.

**Fortalezas**

1. Código simple y legible para request/response.
2. Ideal para operaciones de valor único (DB, HTTP único).
3. Curva de aprendizaje baja para la mayoría de equipos.

**Limitaciones**

1. Composición avanzada (cancelación, retry complejo, streams) más manual.
2. Menos expresivo para eventos continuos.

#### 2) RxJS (Observables)

**Qué es**

Modelo reactivo para flujos de 0..N valores en el tiempo.

**Fortalezas**

1. Composición poderosa (`map`, `switchMap`, `mergeMap`, `retryWhen`, `debounceTime`).
2. Soporte natural para streaming/eventos.
3. Cancelación mediante `unsubscribe`.

**Limitaciones**

1. Mayor complejidad conceptual.
2. Puede sobrecomplicar casos simples.

#### Cuándo usar cada uno

1. **Usa async/await**
   1. CRUD/API tradicional de respuesta única.
   2. Lógica de negocio secuencial simple.

2. **Usa RxJS**
   1. WebSockets/SSE/event streams.
   2. Pipelines con reintentos, timeouts, backpressure, combinación de fuentes.
   3. Integración natural con `HttpService` cuando quieres operadores reactivos.

#### Regla práctica en NestJS

1. Default en services tradicionales: `async/await`.
2. RxJS donde el dominio realmente sea reactivo o de streaming.
3. Evitar mezclar estilos sin convención clara de equipo.

#### Conclusión

`async/await` optimiza simplicidad; RxJS optimiza composición y control avanzado
de flujos. Elige según la naturaleza del problema, no por preferencia personal.

</details>

<details>
<summary>72. ¿Cómo evitar bloquear el event loop en NestJS y mantener rendimiento?</summary>

#### NestJS / Node.js

NestJS corre sobre Node.js y su **event loop**. Si bloqueas el hilo principal,
aumentan latencia, timeouts y caídas de throughput.

#### Qué bloquea el event loop (común)

1. Bucles CPU intensivos en JS puro.
2. Operaciones síncronas (`fs.readFileSync`, crypto sync, zlib sync).
3. Serialización/parsing gigante en request path.
4. N+1 queries o I/O mal optimizado que dispara esperas largas.

#### Estrategias para evitar bloqueo

1. **Usar APIs asíncronas** siempre que existan.
2. **Mover tareas CPU-bound** a workers/colas (`worker_threads`, BullMQ).
3. **Paginar y procesar en chunks** datasets grandes.
4. **Optimizar consultas DB** (índices, joins correctos, evitar N+1).
5. **Cachear** resultados costosos.

#### Ejemplo anti-patrón

```ts
// Malo: bloquea event loop
const content = fs.readFileSync('big.json', 'utf8');
const parsed = JSON.parse(content);
```

Mejor:

```ts
const content = await fs.promises.readFile('big.json', 'utf8');
const parsed = JSON.parse(content);
```

Y si `JSON.parse` es enorme, mover a worker.

#### Herramientas prácticas

1. `clinic.js`, `0x`, `autocannon` para profiling.
2. Métricas p95/p99 + event loop lag.
3. Logs de endpoints lentos.

#### Buenas prácticas de arquitectura

1. No hacer trabajo pesado en controllers.
2. Offload de tareas largas a background jobs.
3. Timeouts y circuit breakers en dependencias externas.
4. Limitar concurrencia en operaciones caras.

#### Conclusión

Rendimiento en NestJS depende de mantener libre el event loop: I/O asíncrono,
CPU pesada fuera del hilo principal y observabilidad continua.

</details>

<details>
<summary>73. ¿Cómo optimizar latencia (p95 / p99) y qué afecta estas métricas?</summary>

#### NestJS / Performance

`p95` y `p99` miden latencia en la cola de peores casos (tail latency).
Optimizar solo promedio no alcanza; en producción importa cómo se comporta el
sistema bajo carga y degradación.

#### Qué afecta p95/p99

1. Queries lentas/N+1/locks en DB.
2. Dependencias externas con timeouts altos.
3. Bloqueo de event loop (CPU/sync I/O).
4. GC pauses y presión de memoria.
5. Saturación de pool (DB/HTTP).
6. Contención en recursos compartidos (colas, locks, disco).

#### Estrategia de optimización (priorizada)

1. **Observabilidad primero**
   1. métricas por endpoint
   2. tracing distribuido
   3. breakdown app vs DB vs upstream

2. **Eliminar outliers de DB**
   1. índices correctos
   2. evitar N+1
   3. paginación
   4. revisar planes de ejecución

3. **Controlar llamadas externas**
   1. timeout estricto
   2. retry selectivo con backoff
   3. circuit breaker

4. **Reducir trabajo por request**
   1. caching
   2. payload más pequeño
   3. serialización eficiente

5. **Aislar trabajo pesado**
   1. colas/background jobs
   2. no CPU-bound en request path

#### Técnicas concretas en NestJS

1. `CacheInterceptor` o cache-aside para lecturas calientes.
2. `ValidationPipe` optimizada (sin trabajo extra por request).
3. Compresión en edge/proxy para payload grande.
4. Throttling en endpoints costosos.
5. Connection pooling bien dimensionado.

#### Buenas prácticas operativas

1. Define SLO por endpoint crítico.
2. Haz load tests con percentiles (no solo RPS medio).
3. Monitorea p95/p99 por versión de deploy.
4. Usa canary rollout para detectar regresiones.

#### Conclusión

Mejorar p95/p99 es reducir variabilidad y colas: menos bloqueos, menos outliers,
menos dependencia de componentes inestables.

</details>

<details>
<summary>74. ¿Cómo usar cluster mode en Node.js junto con NestJS para escalar?</summary>

#### NestJS / Node.js

`cluster` permite ejecutar múltiples procesos worker de Node aprovechando varios
núcleos CPU. Cada worker sirve requests en paralelo sobre el mismo puerto.

#### Cuándo usarlo

1. App monolítica en una sola VM/host.
2. Necesitas aprovechar multicore sin cambiar arquitectura.
3. No usas aún orquestación horizontal (Kubernetes, etc.).

#### Ejemplo básico de cluster bootstrap

```ts
import cluster from 'cluster';
import os from 'os';
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}

if (cluster.isPrimary) {
  const cpuCount = os.cpus().length;

  for (let i = 0; i < cpuCount; i++) {
    cluster.fork();
  }

  cluster.on('exit', () => {
    cluster.fork();
  });
} else {
  bootstrap();
}
```

#### Consideraciones importantes

1. Memoria no compartida entre workers.
2. In-memory cache/sessions no se sincronizan (usar Redis).
3. Jobs internos pueden duplicarse si no coordinas locks.
4. WebSockets requieren estrategia sticky sessions o broker.

#### Cluster vs escalado horizontal

1. **Cluster**: escala dentro de un host.
2. **Horizontal (pods/instancias)**: escala entre hosts, mayor resiliencia.

En producción moderna suele preferirse escalado horizontal + orchestrator;
cluster puede seguir siendo útil en entornos VM simples.

#### Buenas prácticas

1. Mantener app stateless.
2. Externalizar estado (Redis/DB/object storage).
3. Supervisar workers (PM2/systemd/k8s).
4. Medir p95/p99 y throughput antes/después.

#### Conclusión

Cluster mode es una palanca rápida para aprovechar CPUs multicore, pero requiere
arquitectura stateless y coordinación de estado fuera del proceso.

</details>

<details>
<summary>75. ¿Cómo implementar cron jobs en NestJS vía @nestjs/schedule?</summary>

#### NestJS

`@nestjs/schedule` permite ejecutar tareas programadas (cron, interval, timeout)
dentro de tu aplicación NestJS.

#### 1) Instalación

1. `@nestjs/schedule`

#### 2) Activar módulo

```ts
import { Module } from '@nestjs/common';
import { ScheduleModule } from '@nestjs/schedule';

@Module({
  imports: [ScheduleModule.forRoot()],
})
export class AppModule {}
```

#### 3) Crear servicio con `@Cron`

```ts
import { Injectable, Logger } from '@nestjs/common';
import { Cron, CronExpression } from '@nestjs/schedule';

@Injectable()
export class CleanupJob {
  private readonly logger = new Logger(CleanupJob.name);

  @Cron(CronExpression.EVERY_DAY_AT_MIDNIGHT)
  async handleDailyCleanup() {
    this.logger.log('Running daily cleanup');
    // lógica de limpieza
  }
}
```

También puedes usar expresión cron manual:

```ts
@Cron('0 */5 * * * *') // cada 5 minutos
```

#### Otros decorators útiles

1. `@Interval(ms)`
2. `@Timeout(ms)`

#### Consideraciones en producción

1. En múltiples instancias, el mismo job corre en cada instancia (duplicación).
2. Para evitarlo: locks distribuidos (Redis), leader election o scheduler externo.
3. Jobs largos deben ir a cola (Bull/BullMQ) para reintentos y control.

#### Buenas prácticas

1. Idempotencia en cada job.
2. Logs + métricas (inicio, fin, duración, errores).
3. Timeouts y manejo de excepciones.
4. Evitar trabajo pesado en memoria sin límites.
5. Configurar zona horaria explícita cuando aplica.

Ejemplo con zona:

```ts
@Cron('0 0 * * *', { timeZone: 'UTC' })
```

#### Conclusión

`@nestjs/schedule` es ideal para tareas internas simples. Para cargas críticas o
distribuidas, combínalo con locking/colas o mueve scheduling a infraestructura dedicada.

</details>

<details>
<summary>76. ¿Qué es EventEmitter en NestJS y en qué se diferencia de las colas (Bull)?</summary>

#### NestJS

`EventEmitter` en NestJS (`@nestjs/event-emitter`) permite publicar eventos
internos en memoria dentro del mismo proceso.

Las colas como Bull/BullMQ usan backend externo (Redis) para procesamiento
asíncrono persistente y distribuido.

#### Diferencia clave

1. **EventEmitter**
   1. In-process, memoria local.
   2. Baja latencia.
   3. Sin persistencia ni garantía fuerte de entrega.

2. **Bull/BullMQ**
   1. Basado en Redis.
   2. Persistencia, retries, delayed jobs, concurrencia controlada.
   3. Funciona bien en múltiples instancias/workers.

#### Cuándo usar EventEmitter

1. Reacciones internas ligeras al evento (`user.created`).
2. Desacoplar módulos sin introducir infraestructura extra.
3. Casos donde perder evento no rompe negocio crítico.

#### Cuándo usar Bull/BullMQ

1. Tareas pesadas o lentas (emails, PDFs, webhooks).
2. Necesidad de reintentos y durabilidad.
3. Escenarios distribuidos/multi-instancia.
4. Backpressure y control de throughput.

#### Regla práctica

1. Evento local no crítico -> EventEmitter.
2. Trabajo crítico/asíncrono confiable -> Queue (Bull/BullMQ).

#### Conclusión

EventEmitter es mecanismo de orquestación interna rápida; Bull es infraestructura
de ejecución asíncrona robusta para producción distribuida.

</details>

<details>
<summary>77. ¿Cómo implementar comunicación interna event-driven entre módulos vía EventEmitter2?</summary>

#### NestJS

`EventEmitter2` en NestJS permite desacoplar módulos mediante eventos internos:
un módulo publica un evento y otros reaccionan sin dependencia directa.

#### 1) Instalar y configurar

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

#### 2) Definir evento de dominio

```ts
export class UserCreatedEvent {
  constructor(
    public readonly userId: string,
    public readonly email: string,
  ) {}
}
```

#### 3) Publicar evento desde módulo emisor

```ts
import { Injectable } from '@nestjs/common';
import { EventEmitter2 } from '@nestjs/event-emitter';

@Injectable()
export class UsersService {
  constructor(private readonly events: EventEmitter2) {}

  async createUser(input: CreateUserDto) {
    const user = await this.repo.create(input);

    this.events.emit(
      'user.created',
      new UserCreatedEvent(user.id, user.email),
    );

    return user;
  }
}
```

#### 4) Escuchar evento en módulos suscriptores

```ts
import { Injectable, Logger } from '@nestjs/common';
import { OnEvent } from '@nestjs/event-emitter';

@Injectable()
export class WelcomeEmailListener {
  private readonly logger = new Logger(WelcomeEmailListener.name);

  @OnEvent('user.created')
  async handleUserCreated(event: UserCreatedEvent) {
    this.logger.log(`Send welcome email to ${event.email}`);
    // email logic
  }
}
```

#### Buenas prácticas

1. Nombres de eventos consistentes (`entity.action`: `user.created`).
2. Payload mínimo y estable (evitar pasar entidades enormes).
3. Handlers idempotentes para tolerar reintentos/manual replays.
4. No meter lógica crítica que requiera durabilidad estricta (para eso usar colas/broker).

#### Limitaciones importantes

1. Es in-process: no cruza instancias automáticamente.
2. Sin persistencia: eventos pueden perderse en crash.
3. Orden/entrega no garantizados como en sistemas de mensajería durables.

#### Conclusión

EventEmitter2 es ideal para desacoplamiento interno rápido entre módulos dentro
de una instancia NestJS; para garantías fuertes, complementa con colas o broker.

</details>

<details>
<summary>78. ¿Cómo implementar trabajos en background usando Bull o BullMQ?</summary>

#### NestJS

Bull/BullMQ permiten sacar tareas pesadas del request path y procesarlas en
workers asíncronos con retries, delays y control de concurrencia.

#### Cuándo usarlos

1. Envío de emails/notificaciones.
2. Generación de reportes/PDF.
3. Procesamiento multimedia.
4. Integraciones externas lentas.

#### 1) Registrar cola

```ts
import { Module } from '@nestjs/common';
import { BullModule } from '@nestjs/bullmq';

@Module({
  imports: [
    BullModule.forRoot({
      connection: { host: 'localhost', port: 6379 },
    }),
    BullModule.registerQueue({
      name: 'emails',
    }),
  ],
})
export class JobsModule {}
```

#### 2) Producir jobs

```ts
import { InjectQueue } from '@nestjs/bullmq';
import { Queue } from 'bullmq';

@Injectable()
export class NotificationsService {
  constructor(@InjectQueue('emails') private readonly emailsQueue: Queue) {}

  async sendWelcomeEmail(userId: string, email: string) {
    await this.emailsQueue.add(
      'welcome-email',
      { userId, email },
      {
        attempts: 5,
        backoff: { type: 'exponential', delay: 1000 },
        removeOnComplete: 1000,
        removeOnFail: 5000,
      },
    );
  }
}
```

#### 3) Consumir jobs (worker)

```ts
import { Processor, WorkerHost } from '@nestjs/bullmq';
import { Job } from 'bullmq';

@Processor('emails')
export class EmailsProcessor extends WorkerHost {
  async process(job: Job<{ userId: string; email: string }>) {
    switch (job.name) {
      case 'welcome-email':
        // lógica de envío
        return;
      default:
        throw new Error(`Unknown job: ${job.name}`);
    }
  }
}
```

#### Buenas prácticas

1. Jobs idempotentes (pueden reintentarse).
2. Payload pequeño, datos grandes por referencia (id/url).
3. Configurar `attempts`, `backoff`, `timeout`.
4. DLQ/alertas para fallos repetidos.
5. Métricas de cola: waiting, active, failed, completed, latency.

#### Arquitectura recomendada

1. API encola rápidamente y responde.
2. Worker dedicado procesa fuera del request lifecycle.
3. Estado de job consultable si frontend necesita progreso.

#### Conclusión

Bull/BullMQ convierten tareas lentas en procesamiento resiliente y escalable,
protegiendo p95/p99 de la API principal.

</details>

<details>
<summary>79. ¿Cómo diseñar jobs idempotentes (colas de tareas) para evitar ejecución duplicada?</summary>

#### NestJS / Queue Design

Un job idempotente puede ejecutarse varias veces y mantener el mismo resultado
final. Esto es crítico porque en colas reales siempre existen retries, reentregas
y fallos parciales.

#### Por qué hay duplicados

1. Reintentos automáticos por timeout/error.
2. Reentrega tras crash del worker.
3. Race conditions entre workers.
4. Reenvío manual/operativo de jobs.

#### Estrategias de idempotencia

1. **Clave idempotente de negocio**
   Usa un identificador único (`orderId`, `paymentId`, `eventId`) para detectar
   si la acción ya fue aplicada.

2. **Upsert/unique constraints en DB**
   Asegura unicidad a nivel persistencia (`UNIQUE(external_id)`).

3. **Estado de procesamiento**
   Mantén estado (`pending`, `processing`, `done`, `failed`) y valida transición.

4. **Outbox/Inbox pattern**
   Registra eventos procesados para ignorar duplicados.

5. **Locks distribuidos**
   Evita procesamiento concurrente del mismo recurso cuando aplica.

#### Ejemplo conceptual

Job: `send-invoice` con `invoiceId`.

1. Buscar `invoiceId` en tabla `processed_jobs`.
2. Si existe -> salir (`already processed`).
3. Si no existe -> ejecutar acción.
4. Registrar `invoiceId` como procesado en transacción atómica.

#### Buenas prácticas en Bull/BullMQ

1. Usar `jobId` determinístico cuando sea posible.
2. Hacer handlers reentrantes (sin efectos secundarios repetibles).
3. Enviar side effects externos solo tras comprobar estado.
4. Configurar retries con backoff, pero con lógica idempotente real.

#### Errores comunes

1. Confiar solo en “exactly once” del broker (no existe en práctica total).
2. No proteger write side con constraints únicas.
3. Marcar job como hecho antes de completar side effect.

#### Conclusión

En colas, la semántica real es *at-least-once*. La única defensa confiable contra
duplicados es diseñar idempotencia explícita en lógica y persistencia.

</details>

<details>
<summary>80. ¿Cómo implementar WebSockets en NestJS?</summary>

#### NestJS

NestJS implementa WebSockets mediante **Gateways** (`@WebSocketGateway`) con
integración a Socket.IO (por defecto) o ws adapter.

#### 1) Crear Gateway básico

```ts
import {
  MessageBody,
  OnGatewayConnection,
  OnGatewayDisconnect,
  SubscribeMessage,
  WebSocketGateway,
  WebSocketServer,
} from '@nestjs/websockets';
import { Server, Socket } from 'socket.io';

@WebSocketGateway({
  cors: {
    origin: ['https://app.example.com'],
    credentials: true,
  },
})
export class ChatGateway implements OnGatewayConnection, OnGatewayDisconnect {
  @WebSocketServer()
  server: Server;

  handleConnection(client: Socket) {
    // on connect
  }

  handleDisconnect(client: Socket) {
    // on disconnect
  }

  @SubscribeMessage('chat.send')
  handleChatMessage(@MessageBody() payload: { roomId: string; text: string }) {
    this.server.to(payload.roomId).emit('chat.message', payload);
  }
}
```

#### 2) Usar rooms y broadcast

1. `client.join(roomId)` para suscribir cliente a sala.
2. `server.to(roomId).emit(...)` para enviar a grupo.
3. `client.emit(...)` para respuesta individual.

#### 3) Seguridad básica

1. Autenticar en handshake (token/cookie).
2. Aplicar guards/policies para eventos sensibles.
3. Validar payloads con pipes/DTOs.
4. Rate limit para prevenir spam/flood.

#### 4) Escalado

En múltiples instancias necesitas adapter distribuido (p.ej. Redis adapter) para
sincronizar rooms y broadcasts entre nodos.

#### Buenas prácticas

1. Mantén contratos de eventos versionados.
2. Implementa ack/timeouts para operaciones críticas.
3. Maneja reconexión cliente e idempotencia de mensajes.
4. Monitorea conexiones activas, tasa de mensajes y errores.

#### Conclusión

WebSockets en NestJS se construyen con Gateways y eventos tipados. Para producción,
la clave está en auth, validación y estrategia de escalado multi-instancia.

</details>

<details>
<summary>81. ¿Cómo implementar autenticación en un WebSocket Gateway?</summary>

#### NestJS / WebSockets

La autenticación en WebSocket se hace normalmente en el **handshake** (token en
headers/auth/cookie) y luego se valida por evento con guards/policies.

#### Estrategia recomendada

1. Validar token al conectar (`handleConnection`).
2. Adjuntar identidad al `client` (`client.data.user`).
3. Aplicar `WsGuard` para eventos protegidos.
4. Revalidar permisos sensibles por recurso/sala.

#### 1) Validación en conexión

```ts
import {
  OnGatewayConnection,
  WebSocketGateway,
  WebSocketServer,
} from '@nestjs/websockets';
import { Server, Socket } from 'socket.io';

@WebSocketGateway({ cors: { origin: ['https://app.example.com'] } })
export class ChatGateway implements OnGatewayConnection {
  @WebSocketServer() server: Server;

  constructor(private readonly authService: AuthService) {}

  async handleConnection(client: Socket) {
    try {
      const token = client.handshake.auth?.token
        || client.handshake.headers.authorization?.toString().replace('Bearer ', '');

      if (!token) throw new Error('Missing token');

      const user = await this.authService.verifyAccessToken(token);
      client.data.user = user;
    } catch {
      client.disconnect(true);
    }
  }
}
```

#### 2) Guard para eventos WebSocket

```ts
import { CanActivate, ExecutionContext, Injectable, WsException } from '@nestjs/common';

@Injectable()
export class WsAuthGuard implements CanActivate {
  canActivate(context: ExecutionContext): boolean {
    const client = context.switchToWs().getClient<Socket>();
    if (!client.data?.user) {
      throw new WsException('Unauthorized');
    }
    return true;
  }
}
```

Uso:

```ts
@UseGuards(WsAuthGuard)
@SubscribeMessage('chat.send')
handleSendMessage(...) {}
```

#### Consideraciones importantes

1. Token expirado en conexión larga: estrategia de refresh/reconnect.
2. No confiar solo en conexión inicial para acciones de alto riesgo.
3. Revocación de sesión debe poder desconectar sockets activos.
4. En multi-instancia, compartir estado de sesión (Redis/JWT stateless).

#### Buenas prácticas

1. Usar JWT corto + refresh seguro.
2. Propagar `userId/tenantId` en contexto del socket.
3. Auditar eventos sensibles (quién, qué, cuándo).
4. Rate limit por usuario/socket para evitar abuso.

#### Conclusión

Auth en Gateway = validación en handshake + autorización por evento. Ambas capas
son necesarias para seguridad real en tiempo real.

</details>

<details>
<summary>82. ¿Qué enfoques se usan para escalar sistemas en tiempo real?</summary>

#### NestJS / Real-time

Escalar sistemas en tiempo real requiere combinar escalado horizontal,
coordinación de estado y control de fan-out/mensajería.

#### Capas de escalado principales

1. **Escalado de conexiones**
   Más instancias de gateway + balanceador (sticky sessions cuando aplica).

2. **Sincronización entre nodos**
   Adapter pub/sub (Redis, NATS, Kafka según caso) para propagar eventos.

3. **Externalizar estado**
   Presencia, sesiones, rooms y offsets fuera de memoria local.

4. **Control de fan-out**
   Evitar broadcasts globales innecesarios; segmentar por room/topic/tenant.

#### Enfoques concretos

1. WebSocket Gateway horizontal + Redis adapter para Socket.IO.
2. Event backbone (Kafka/NATS) para eventos cross-service.
3. CQRS/read models para lecturas rápidas de estado en tiempo real.
4. Backpressure y rate limits para clientes ruidosos.
5. Sharding por tenant/room en casos de gran volumen.

#### Retos típicos

1. Sticky sessions vs transporte/stateless auth.
2. Orden de mensajes y duplicados.
3. Reconnect storms tras despliegues/fallos.
4. Consistencia eventual entre nodos.

#### Buenas prácticas

1. Diseñar eventos idempotentes y versionados.
2. Medir conexiones activas, msgs/sec, lag, drop rate, p95 delivery.
3. Usar heartbeat/ping para detectar sockets muertos.
4. Aplicar límites por usuario/tenant/canal.
5. Separar plano de control (auth/policies) del plano de datos (broadcast).

#### Conclusión

No existe una única técnica de escalado real-time: el patrón ganador combina
nodos stateless, estado externo, pub/sub distribuido y observabilidad rigurosa.

</details>

<details>
<summary>83. ¿Cuáles son los enfoques para integrar GraphQL en NestJS (code-first vs schema-first) y en qué se diferencian?</summary>

#### NestJS / GraphQL

NestJS soporta dos enfoques principales para GraphQL:

1. **Code-first**: defines esquema mediante clases/decorators TypeScript.
2. **Schema-first**: defines esquema en archivos `.graphql` (SDL) y luego implementas resolvers.

#### 1) Code-first

**Cómo funciona**

1. Decoras clases (`@ObjectType`, `@Field`, `@InputType`).
2. Nest genera schema GraphQL automáticamente.

**Ventajas**

1. Una sola fuente en TypeScript.
2. Tipado fuerte y DX excelente.
3. Menos drift entre código y schema.

**Desventajas**

1. Menos “schema visible” para equipos no TS.
2. Algunos patrones avanzados de SDL son menos directos.

#### 2) Schema-first

**Cómo funciona**

1. Escribes SDL en `.graphql`.
2. Implementas resolvers que cumplan ese contrato.

**Ventajas**

1. Contrato explícito y agnóstico de lenguaje.
2. Colaboración sencilla con frontend/federation teams.
3. Control fino del schema desde diseño.

**Desventajas**

1. Más riesgo de drift código-schema si no hay disciplina.
2. Mayor boilerplate en mapeo/tipos.

#### Configuración típica

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

#### ¿Cuál elegir?

1. Backend TS-centric, velocidad de desarrollo -> **code-first**.
2. Organización contract-first, multi-lenguaje, federación estricta -> **schema-first**.

#### Buenas prácticas comunes

1. Versionar cambios de schema (breaking/non-breaking).
2. Añadir validación/autorización en resolvers.
3. Evitar N+1 con DataLoader.
4. Documentar deprecations (`@deprecated`) y política de retiro.

#### Conclusión

Ambos enfoques son válidos; la elección depende de gobierno de contrato y flujo
de trabajo del equipo. En NestJS, code-first suele ser más rápido para equipos TS.

</details>

<details>
<summary>84. ¿Qué son los resolvers en GraphQL y en qué se diferencian de los controllers REST?</summary>

#### NestJS / GraphQL

Un **resolver** en GraphQL es la función que resuelve campos de `Query`,
`Mutation` o tipos anidados del schema.

En REST, un **controller** maneja rutas HTTP completas (`GET /users/:id`).

#### Diferencia principal

1. **REST Controller**: orientado a endpoint/ruta.
2. **GraphQL Resolver**: orientado a campo del schema.

#### Cómo trabajan

1. REST:
   1. Cliente llama una URL concreta.
   2. Controller retorna respuesta fija de ese endpoint.

2. GraphQL:
   1. Cliente envía una query declarando campos deseados.
   2. Resolver root y resolvers de campos construyen respuesta final.

#### Ejemplo NestJS Resolver

```ts
@Resolver(() => User)
export class UsersResolver {
  constructor(private readonly usersService: UsersService) {}

  @Query(() => User, { name: 'user' })
  getUser(@Args('id') id: string) {
    return this.usersService.findById(id);
  }

  @ResolveField(() => [Post])
  posts(@Parent() user: User) {
    return this.usersService.getPosts(user.id);
  }
}
```

#### Implicaciones arquitectónicas

1. En GraphQL es común riesgo N+1 en `@ResolveField` -> usar DataLoader.
2. Authz puede aplicarse a nivel resolver/campo.
3. Contrato lo define schema GraphQL, no rutas HTTP.

#### Cuándo usar cada enfoque

1. REST: APIs simples por recurso, caché HTTP nativa, integración tradicional.
2. GraphQL: clientes con necesidades de datos variables y agregación flexible.

#### Conclusión

Controller REST responde rutas; resolver GraphQL resuelve campos. El segundo da
más flexibilidad al cliente, pero exige más disciplina en performance y permisos.

</details>

<details>
<summary>85. ¿Cómo trabajar con context en GraphQL e implementar autorización a través de él?</summary>

#### NestJS / GraphQL

En GraphQL, `context` es el objeto compartido por resolvers durante una operación
(request). Se usa para pasar usuario autenticado, loaders, requestId y servicios
auxiliares.

#### 1) Configurar context en GraphQLModule

```ts
GraphQLModule.forRoot({
  autoSchemaFile: true,
  context: ({ req, res }) => ({
    req,
    res,
    requestId: req.headers['x-request-id'],
  }),
});
```

#### 2) Obtener usuario desde context

Con JWT guard en GraphQL, se valida token y se adjunta `user` a `req`.
Luego en resolver:

```ts
@Query(() => Profile)
me(@Context() ctx: any) {
  return this.usersService.getProfile(ctx.req.user.id);
}
```

#### 3) Autorización con Guards + Reflector

1. Define metadata (`@Roles`, `@Policies`).
2. En `GqlAuthGuard` / `RolesGuard`, convierte `ExecutionContext` a `GqlExecutionContext`.
3. Lee `ctx.getContext().req.user` y decide acceso.

Ejemplo base:

```ts
const gqlCtx = GqlExecutionContext.create(context);
const req = gqlCtx.getContext().req;
const user = req.user;
```

#### 4) Autorización por recurso

No basta role global; para datos sensibles:

1. cargar recurso,
2. verificar ownership/tenant,
3. aplicar policy ABAC.

#### Buenas prácticas

1. Mantén `context` pequeño y explícito.
2. Inyecta DataLoaders por request en context para evitar N+1.
3. No confíes en args del cliente para identidad; usa `req.user`.
4. Separa autenticación (quién eres) de autorización (qué puedes hacer).

#### Conclusión

En GraphQL con NestJS, `context` es la columna vertebral de authz: transporta
identidad y metadatos por request para que guards y resolvers apliquen políticas
consistentes.

</details>

<details>
<summary>86. ¿Qué protocolos de transporte y brokers soporta NestJS (Kafka, Redis, gRPC, NATS) y cuáles son sus diferencias?</summary>

#### NestJS / Microservices

NestJS microservices soporta varios transportes. La elección depende de patrón de
comunicación, garantías de entrega, latencia y ecosistema operativo.

#### Opciones principales

1. **TCP**
   Simple request/response entre servicios Nest.

2. **Redis (pub/sub)**
   Mensajería ligera basada en canales; fácil de arrancar, garantías limitadas.

3. **NATS**
   Broker rápido y simple, buen fit para eventos y request/reply liviano.

4. **Kafka**
   Event streaming durable, alto throughput, particiones y replay.

5. **gRPC**
   RPC tipado con Protobuf, eficiente y contract-first.

#### Diferencias rápidas

1. **Kafka**
   1. Pros: durabilidad, orden por partición, replay, escala alta.
   2. Contras: operación más compleja.

2. **NATS**
   1. Pros: baja latencia, simple, muy rápido.
   2. Contras: modelo más simple (durabilidad depende de NATS JetStream).

3. **Redis pub/sub**
   1. Pros: setup sencillo.
   2. Contras: mensajes efímeros, no ideal para crítica durabilidad.

4. **gRPC**
   1. Pros: contratos fuertes, buen rendimiento binario.
   2. Contras: menos flexible para broadcast/eventos desacoplados.

#### ¿Cuándo usar qué?

1. Integración síncrona tipada servicio-a-servicio -> **gRPC**.
2. Event-driven durable y analítica/streaming -> **Kafka**.
3. Mensajería rápida interna con baja complejidad -> **NATS**.
4. Casos simples o entorno ya centrado en Redis -> **Redis transport**.

#### Buenas prácticas

1. Diseñar mensajes versionados y backward-compatible.
2. Implementar idempotencia de consumidores (at-least-once).
3. Monitorizar lag, retries y DLQ.
4. Definir claramente semántica de entrega por caso de uso.

#### Conclusión

No hay transporte universal: gRPC domina RPC tipado; Kafka domina eventos
durables; NATS/Redis cubren mensajería ligera de baja latencia.

</details>

<details>
<summary>87. ¿Cómo diseñar correctamente una arquitectura event-driven y cuáles son sus principios clave?</summary>

#### NestJS / Event-Driven Architecture

Una arquitectura event-driven desacopla productores y consumidores mediante
eventos de dominio. Bien diseñada, mejora escalabilidad y resiliencia; mal
diseñada, crea inconsistencia y caos operacional.

#### Principios clave

1. **Eventos de dominio, no técnicos**
   Nombres semánticos: `order.created`, `payment.failed`.

2. **Contratos versionados**
   Mensajes con esquema estable y evolución backward-compatible.

3. **Idempotencia obligatoria**
   Consumidores preparados para reentregas (at-least-once).

4. **Desacoplamiento temporal**
   Productor no depende de que consumidor esté online ahora.

5. **Observabilidad end-to-end**
   correlationId, tracing, métricas de lag/retry/fail.

#### Building blocks

1. Producer (emite evento tras cambio de estado).
2. Broker/stream (Kafka/NATS/Redis Streams).
3. Consumer(s) (reaccionan y ejecutan side effects).
4. DLQ/retry policy.
5. Schema governance.

#### Patrón crítico: Outbox

Para evitar perder eventos entre DB commit y publish:

1. Escribe cambio de negocio + registro outbox en misma transacción.
2. Proceso relay publica outbox al broker.
3. Marca evento como publicado.

#### Buenas prácticas de diseño

1. Mensajes pequeños, autoexplicativos, con metadata (`eventId`, `occurredAt`, `version`).
2. Evitar payloads gigantes; usar referencia (`entityId`) cuando conviene.
3. Definir ownership por evento y consumidor.
4. Separar comandos (intención) de eventos (hecho ocurrido).
5. Modelar fallos desde inicio (retry, poison message, compensación).

#### Riesgos comunes

1. “Distributed monolith” (servicios fuertemente acoplados por eventos ocultos).
2. Falta de versionado de esquema.
3. Lógica no idempotente en consumidores.
4. No tener DLQ ni observabilidad de lag.

#### Conclusión

EDA efectiva no es solo usar un broker; es disciplina en contratos, idempotencia,
observabilidad y manejo explícito de consistencia eventual.

</details>

<details>
<summary>88. ¿Cómo manejar transacciones distribuidas en microservicios? (Saga pattern, consistencia eventual)</summary>

#### NestJS / Microservices

En microservicios, una transacción ACID global entre varias bases suele ser
inviable. La estrategia práctica es **consistencia eventual** con orquestación/
coreografía de pasos y compensaciones.

#### Patrón principal: Saga

Una **Saga** divide el flujo de negocio en pasos locales:

1. Cada servicio ejecuta su transacción local.
2. Publica evento/resultado.
3. Si falla un paso posterior, se ejecutan acciones compensatorias.

#### Dos estilos de Saga

1. **Orchestrated Saga**
   Un orquestador central decide siguiente paso y compensaciones.

2. **Choreographed Saga**
   Servicios reaccionan a eventos sin coordinador central.

#### Ejemplo (pedido)

1. `OrderService` crea pedido `PENDING`.
2. `PaymentService` intenta cobro.
3. `InventoryService` reserva stock.
4. `ShippingService` programa envío.

Si falla inventario:

1. compensar cobro (refund/cancel payment),
2. marcar pedido `CANCELLED`.

#### Principios clave

1. Idempotencia en comandos/eventos.
2. Mensajes versionados con correlationId/sagaId.
3. Timeouts + retry con límites.
4. Estado explícito de saga (pending, completed, compensating, failed).

#### Implementación en NestJS (patrón)

1. Broker (Kafka/NATS/Rabbit) para eventos.
2. Handlers por paso de saga.
3. Outbox pattern para publicar eventos de forma confiable.
4. Almacenamiento de estado de saga en DB.

#### Riesgos comunes

1. No definir compensaciones reales (solo logs).
2. Duplicados sin idempotencia.
3. Sagas “colgadas” sin timeout/monitoring.
4. Mezclar demasiada lógica de negocio en handlers de mensajería.

#### Conclusión

En distribuidos, no persigas ACID global: diseña Sagas con compensación,
observabilidad e idempotencia para lograr consistencia eventual confiable.

</details>

<details>
<summary>89. ¿Qué es CQRS y cómo implementarlo en NestJS usando @nestjs/cqrs?</summary>

#### NestJS / CQRS

**CQRS** (*Command Query Responsibility Segregation*) separa el modelo de
**escritura** (commands) del modelo de **lectura** (queries).

No significa microservicios por sí solo; es una organización interna para
manejar dominios complejos con reglas y lecturas divergentes.

#### Idea central

1. **Commands** cambian estado (create/update/delete).
2. **Queries** solo leen datos.
3. Handlers distintos para cada tipo.
4. Opcionalmente, modelos de lectura optimizados separados.

#### 1) Instalar y registrar módulo

```ts
import { Module } from '@nestjs/common';
import { CqrsModule } from '@nestjs/cqrs';

@Module({
  imports: [CqrsModule],
  providers: [
    ...CommandHandlers,
    ...QueryHandlers,
  ],
})
export class OrdersModule {}
```

#### 2) Definir Command + Handler

```ts
export class CreateOrderCommand {
  constructor(
    public readonly userId: string,
    public readonly items: Array<{ productId: string; qty: number }>,
  ) {}
}

@CommandHandler(CreateOrderCommand)
export class CreateOrderHandler implements ICommandHandler<CreateOrderCommand> {
  constructor(private readonly repo: OrdersRepository) {}

  async execute(command: CreateOrderCommand) {
    const order = Order.create(command.userId, command.items);
    await this.repo.save(order);
    return { orderId: order.id };
  }
}
```

#### 3) Definir Query + Handler

```ts
export class GetOrderQuery {
  constructor(public readonly orderId: string) {}
}

@QueryHandler(GetOrderQuery)
export class GetOrderHandler implements IQueryHandler<GetOrderQuery> {
  constructor(private readonly readRepo: OrdersReadRepository) {}

  async execute(query: GetOrderQuery) {
    return this.readRepo.findById(query.orderId);
  }
}
```

#### 4) Uso desde Controller

```ts
constructor(
  private readonly commandBus: CommandBus,
  private readonly queryBus: QueryBus,
) {}

@Post()
create(@Body() dto: CreateOrderDto) {
  return this.commandBus.execute(new CreateOrderCommand(dto.userId, dto.items));
}

@Get(':id')
findOne(@Param('id') id: string) {
  return this.queryBus.execute(new GetOrderQuery(id));
}
```

#### Cuándo usar CQRS

1. Dominio complejo con reglas de escritura ricas.
2. Necesidad de modelos de lectura distintos (proyecciones).
3. Auditoría/event sourcing (opcionalmente).

#### Cuándo evitarlo

1. CRUD simple donde añade complejidad innecesaria.

#### Conclusión

CQRS en NestJS aporta separación clara y escalabilidad conceptual en dominios
complejos, pero debe aplicarse donde el beneficio supere el overhead arquitectónico.

</details>

<details>
<summary>90. ¿Qué es Domain-Driven Design y cómo se aplican sus principios en NestJS?</summary>

#### NestJS / DDD

**DDD (Domain-Driven Design)** es un enfoque para construir software complejo
centrado en el dominio de negocio, lenguaje ubicuo y límites claros entre
subdominios.

#### Principios clave de DDD

1. **Ubiquitous Language**
   Código y conversaciones usan el mismo lenguaje de negocio.

2. **Bounded Contexts**
   Cada contexto tiene su propio modelo y reglas.

3. **Entities / Value Objects**
   Modelado explícito de identidad e invariantes.

4. **Aggregates**
   Fronteras de consistencia y reglas transaccionales.

5. **Domain Services**
   Lógica de dominio que no pertenece a una sola entidad.

6. **Repositories (interfaces)**
   Acceso a persistencia abstraído del dominio.

#### Cómo aplicarlo en NestJS

1. Organizar módulos por dominio (`orders`, `billing`, `users`) no por capa técnica global.
2. Separar capas:
   1. `domain` (reglas, entidades, VOs)
   2. `application` (casos de uso)
   3. `infrastructure` (ORM, HTTP, broker)
3. Inyectar puertos (interfaces/tokens) en application/domain.
4. Mantener controllers/gateways delgados, solo transporte.

#### Estructura ejemplo

```text
src/modules/orders/
  domain/
    entities/
    value-objects/
    services/
    ports/
  application/
    commands/
    queries/
    use-cases/
  infrastructure/
    persistence/
    messaging/
  orders.controller.ts
  orders.module.ts
```

#### Beneficios

1. Menor acoplamiento técnico al dominio.
2. Mayor mantenibilidad en sistemas grandes.
3. Facilita evolución por equipos (ownership por contexto).

#### Riesgos comunes

1. “DDD ceremonial” en proyectos CRUD simples.
2. Filtrar detalles ORM al dominio.
3. No definir claramente bounded contexts.

#### Conclusión

DDD en NestJS funciona bien cuando el dominio es complejo: enfoca arquitectura en
reglas de negocio y usa Nest como framework de entrega, no como centro del diseño.

</details>

<details>
<summary>91. ¿Qué es la Arquitectura Hexagonal (Ports & Adapters) y cómo implementarla en NestJS?</summary>

#### NestJS / Hexagonal

La **Arquitectura Hexagonal (Ports & Adapters)** separa el núcleo de negocio de
las tecnologías externas. El dominio define **puertos** (interfaces) y la
infraestructura provee **adaptadores** (implementaciones).

#### Idea central

1. El dominio no conoce ORM, HTTP, broker ni framework.
2. El núcleo depende de abstracciones (ports).
3. Los adapters conectan el mundo externo con esos puertos.

#### Componentes

1. **Core (Domain + Application)**
   Reglas de negocio y casos de uso.

2. **Inbound adapters**
   Entradas: REST controllers, GraphQL resolvers, message handlers.

3. **Outbound adapters**
   Salidas: DB repositories, clients HTTP, publishers de eventos.

4. **Ports**
   Contratos que el core requiere/ofrece.

#### Implementación en NestJS (patrón)

1. Definir puerto en dominio/aplicación:

```ts
export interface PaymentsPort {
  charge(input: ChargeInput): Promise<ChargeResult>;
}
```

2. Caso de uso depende del puerto:

```ts
@Injectable()
export class CheckoutUseCase {
  constructor(@Inject(PAYMENTS_PORT) private readonly payments: PaymentsPort) {}

  async execute(cmd: CheckoutCommand) {
    return this.payments.charge({ orderId: cmd.orderId, amount: cmd.amount });
  }
}
```

3. Adapter de infraestructura implementa puerto:

```ts
@Injectable()
export class StripePaymentsAdapter implements PaymentsPort {
  async charge(input: ChargeInput): Promise<ChargeResult> {
    // llamada a Stripe
    return { success: true, transactionId: 'tx_123' };
  }
}
```

4. Binding en módulo:

```ts
{ provide: PAYMENTS_PORT, useClass: StripePaymentsAdapter }
```

#### Beneficios

1. Testeo fácil del core con mocks de puertos.
2. Cambio de proveedor (Stripe -> Adyen) sin tocar dominio.
3. Menor acoplamiento tecnológico.

#### Riesgos comunes

1. Crear interfaces sin valor real (sobre-abstracción).
2. Meter lógica de negocio en adapters.
3. No mantener límites claros entre core e infraestructura.

#### Conclusión

Hexagonal en NestJS convierte el framework en detalle de entrega: el negocio vive
en el núcleo y los adapters son intercambiables.

</details>

<details>
<summary>92. ¿Cómo implementar logging estructurado y por qué es necesario?</summary>

#### NestJS / Observability

El **logging estructurado** significa emitir logs en formato consistente (JSON)
con campos clave (`level`, `message`, `timestamp`, `requestId`, etc.), en lugar
de texto libre difícil de procesar.

#### Por qué es necesario

1. Búsqueda y filtrado rápido en producción.
2. Correlación entre servicios (requestId/traceId).
3. Alertas y dashboards automáticos.
4. Mejor análisis forense de incidentes.

#### Campos recomendados

1. `timestamp`
2. `level`
3. `message`
4. `service`
5. `requestId` / `traceId`
6. `userId` (si aplica)
7. `path`, `method`, `statusCode`, `latencyMs`
8. `error` (`name`, `message`, `stack`) en fallos

#### Implementación en NestJS (patrón)

1. Elegir logger estructurado (`pino`/`winston`).
2. Integrarlo globalmente (`app.useLogger(...)` o módulo dedicado).
3. Añadir interceptor/middleware para contexto request.
4. Estandarizar formato en toda la app.

#### Ejemplo conceptual de log

```json
{
  "timestamp": "2026-05-08T10:00:00.000Z",
  "level": "info",
  "service": "nestjs-api",
  "message": "HTTP request completed",
  "requestId": "req-123",
  "method": "GET",
  "path": "/users/42",
  "statusCode": 200,
  "latencyMs": 37
}
```

#### Buenas prácticas

1. No loguear secretos (tokens, passwords, PII sensible).
2. Mantener niveles claros (`debug`, `info`, `warn`, `error`).
3. Loggear errores con stack completo en backend (no en respuesta al cliente).
4. Muestreo/ajuste de volumen en endpoints de alto tráfico.

#### Conclusión

Logging estructurado es base de operación confiable en NestJS: sin él, depurar
producción y escalar observabilidad se vuelve costoso y lento.

</details>

<details>
<summary>93. ¿Cómo implementar monitoreo de salud de la aplicación en NestJS? (@nestjs/terminus)</summary>

#### NestJS / Health Monitoring

`@nestjs/terminus` permite exponer endpoints de salud para verificar que la app
esté viva y lista para recibir tráfico, además de comprobar dependencias.

#### Objetivos

1. **Liveness**: proceso está vivo.
2. **Readiness**: servicio listo (dependencias críticas operativas).

#### 1) Instalar y registrar

1. `@nestjs/terminus`

```ts
import { Module } from '@nestjs/common';
import { TerminusModule } from '@nestjs/terminus';

@Module({
  imports: [TerminusModule],
})
export class HealthModule {}
```

#### 2) Crear HealthController

```ts
import { Controller, Get } from '@nestjs/common';
import { HealthCheck, HealthCheckService, HttpHealthIndicator } from '@nestjs/terminus';

@Controller('health')
export class HealthController {
  constructor(
    private readonly health: HealthCheckService,
    private readonly http: HttpHealthIndicator,
  ) {}

  @Get('live')
  live() {
    return { status: 'ok' };
  }

  @Get('ready')
  @HealthCheck()
  ready() {
    return this.health.check([
      () => this.http.pingCheck('docs', 'https://docs.example.com'),
    ]);
  }
}
```

#### Qué debería incluir readiness

1. DB connectivity.
2. Redis/broker/cache.
3. Dependencias externas críticas.
4. Estado de recursos internos esenciales.

#### Buenas prácticas

1. Separar `live` y `ready` (no mezclar).
2. `live` debe ser ultrarrápido y no depender de servicios externos.
3. `ready` sí valida dependencias necesarias para tráfico real.
4. Integrar con Kubernetes probes / load balancer checks.
5. No exponer detalles sensibles en respuesta pública.

#### Conclusión

Health checks en NestJS no son solo endpoint “pong”: son contrato operativo para
orquestadores, despliegues seguros y respuesta rápida a incidentes.

</details>

<details>
<summary>94. ¿Cómo implementar health checks para servicios dependientes (DB, Redis, APIs externas)?</summary>

#### NestJS / Terminus

Los health checks de dependencias validan que componentes críticos estén
operativos antes de aceptar tráfico (`readiness`).

#### Qué dependencias validar

1. Base de datos (conexión/query simple).
2. Redis/cache.
3. Broker (si es crítico para request path).
4. APIs externas esenciales para negocio.

#### Ejemplo con `@nestjs/terminus`

```ts
import { Controller, Get } from '@nestjs/common';
import {
  HealthCheck,
  HealthCheckService,
  HttpHealthIndicator,
  TypeOrmHealthIndicator,
  MicroserviceHealthIndicator,
} from '@nestjs/terminus';

@Controller('health')
export class HealthController {
  constructor(
    private readonly health: HealthCheckService,
    private readonly db: TypeOrmHealthIndicator,
    private readonly http: HttpHealthIndicator,
    private readonly ms: MicroserviceHealthIndicator,
  ) {}

  @Get('ready')
  @HealthCheck()
  readiness() {
    return this.health.check([
      () => this.db.pingCheck('database'),
      () => this.http.pingCheck('payments-api', 'https://payments.example.com/health'),
      // para microservice transport checks cuando aplica
    ]);
  }
}
```

#### Principios de diseño

1. **Liveness** no debe depender de externos.
2. **Readiness** sí depende de recursos críticos para servir requests.
3. Dependencias opcionales no deben tumbar readiness global (o separar endpoint).

#### Timeouts y degradación

1. Usa timeouts cortos en checks externos.
2. Evita que health endpoint se vuelva lento o bloqueante.
3. Define política de degradación (degraded vs down) cuando el negocio lo permita.

#### Buenas prácticas

1. Separar endpoints: `/health/live`, `/health/ready`, opcional `/health/deps`.
2. Exponer detalles mínimos públicamente; detalles completos en red interna.
3. Integrar con Kubernetes readinessProbe/livenessProbe.
4. Alertar por fallos continuos, no por spikes aislados.

#### Conclusión

Health checks de dependencias son parte del control de tráfico seguro: mejor
rechazar temporalmente que aceptar requests que van a fallar en cascada.

</details>

<details>
<summary>95. ¿Cómo usar OpenTelemetry en NestJS?</summary>

#### NestJS / Observability

**OpenTelemetry (OTel)** estandariza trazas, métricas y logs para observar
aplicaciones distribuidas. En NestJS se usa para instrumentar request lifecycle,
DB, HTTP saliente y contexto entre servicios.

#### Objetivos principales

1. Trazar cada request extremo a extremo.
2. Correlacionar spans con logs (`traceId`, `spanId`).
3. Detectar cuellos de botella (DB/upstream/event loop).

#### Implementación (patrón general)

1. Configurar SDK de OpenTelemetry al bootstrap.
2. Habilitar instrumentaciones automáticas (HTTP, Express/Fastify, DB, axios).
3. Exportar a collector/backend (OTLP -> Jaeger/Tempo/Datadog/New Relic).
4. Añadir spans manuales en casos de negocio críticos.

#### Ejemplo conceptual (bootstrap)

```ts
// tracing.ts (inicializar antes de NestFactory)
const sdk = new NodeSDK({
  traceExporter: new OTLPTraceExporter({ url: process.env.OTEL_EXPORTER_OTLP_ENDPOINT }),
  instrumentations: [getNodeAutoInstrumentations()],
});

await sdk.start();
```

Luego iniciar Nest app normalmente.

#### Spans manuales (cuando hace falta)

1. Wrap de operaciones críticas (checkout, payment, saga step).
2. Añadir atributos útiles: `userId`, `orderId`, `tenantId`, `upstream.status`.
3. Registrar eventos de error y estado de retry/circuit breaker.

#### Buenas prácticas

1. Sampling controlado para no saturar costos.
2. Redactar datos sensibles en atributos/logs.
3. Propagar contexto (`traceparent`) en HTTP/mensajería.
4. Unificar nomenclatura de spans (`service.operation`).

#### Conclusión

OpenTelemetry en NestJS convierte observabilidad en lenguaje común entre equipos:
permite entender latencia real y fallos distribuidos con precisión operativa.

</details>

<details>
<summary>96. ¿Qué es distributed tracing y cómo se implementa en arquitectura de microservicios?</summary>

#### Microservices / Observability

**Distributed tracing** rastrea el recorrido completo de una solicitud a través
 de múltiples servicios, mostrando dónde se consume latencia y dónde fallan
 dependencias.

#### Conceptos básicos

1. **Trace**: operación end-to-end (ej. `checkout`).
2. **Span**: segmento dentro del trace (servicio A, DB query, HTTP call).
3. **traceId**: identificador común para todos los spans del flujo.
4. **spanId/parentSpanId**: relación jerárquica entre spans.

#### Cómo se implementa

1. Instrumentar servicios con OpenTelemetry.
2. Propagar contexto entre servicios (`traceparent` en headers).
3. Crear spans automáticos (HTTP, DB, broker) + spans manuales en lógica crítica.
4. Exportar a backend de observabilidad (Jaeger, Tempo, Datadog, etc.).

#### Flujo típico

1. API Gateway recibe request y crea span raíz.
2. Servicio A llama Servicio B/C con contexto propagado.
3. Cada servicio crea spans hijos.
4. Backend de trazas reconstruye el grafo completo.

#### Beneficios

1. Identificar cuellos de botella exactos (no suposiciones).
2. Detectar fallos en cascada y dependencia lenta.
3. Correlacionar traces con logs/métricas.
4. Mejorar p95/p99 con evidencia real.

#### Buenas prácticas

1. Nombres de spans consistentes (`service.operation`).
2. Atributos útiles pero sin datos sensibles.
3. Sampling balanceado (coste vs visibilidad).
4. Propagación obligatoria en HTTP + mensajería asíncrona.

#### Conclusión

Distributed tracing es la “radiografía” de sistemas distribuidos: sin él,
depurar microservicios complejos en producción se vuelve lento e impreciso.

</details>

<details>
<summary>97. ¿Cómo escribir unit tests en NestJS y cuáles son los enfoques básicos de testing?</summary>

#### NestJS / Testing

Los **unit tests** validan una unidad aislada (servicio, guard, pipe, etc.)
sin dependencias reales externas (DB, red, filesystem).

#### Objetivo

1. Verificar lógica de negocio rápidamente.
2. Detectar regresiones temprano.
3. Mantener feedback loop corto en CI.

#### Enfoques básicos en NestJS

1. **Unit tests**
   Aislar clase y mockear dependencias.

2. **Integration tests**
   Probar colaboración entre módulos/DB real o cercana.

3. **E2E tests**
   Probar app completa vía HTTP.

Esta pregunta se enfoca en unit.

#### Patrón típico (TestingModule + mocks)

```ts
import { Test } from '@nestjs/testing';
import { UsersService } from './users.service';
import { UsersRepository } from './users.repository';

describe('UsersService', () => {
  let service: UsersService;
  let repo: jest.Mocked<UsersRepository>;

  beforeEach(async () => {
    const module = await Test.createTestingModule({
      providers: [
        UsersService,
        {
          provide: UsersRepository,
          useValue: {
            findById: jest.fn(),
            save: jest.fn(),
          },
        },
      ],
    }).compile();

    service = module.get(UsersService);
    repo = module.get(UsersRepository);
  });

  it('returns user when found', async () => {
    repo.findById.mockResolvedValue({ id: 'u1', email: 'a@b.com' } as any);

    const result = await service.getUser('u1');

    expect(result.id).toBe('u1');
    expect(repo.findById).toHaveBeenCalledWith('u1');
  });
});
```

#### Qué testear en unit tests

1. Reglas de negocio.
2. Branches de éxito/error.
3. Edge cases (null, límites, estados inválidos).
4. Interacciones con dependencias (llamadas esperadas).

#### Buenas prácticas

1. Tests deterministas (sin tiempo/red reales).
2. Un escenario por test con nombre claro.
3. AAA pattern: Arrange, Act, Assert.
4. Evitar mocks excesivos que oculten fallos reales.

#### Conclusión

Unit tests en NestJS son la base de calidad diaria: rápidos, aislados y enfocados
en comportamiento observable de cada unidad.

</details>

<details>
<summary>98. ¿Cómo mockear dependencias correctamente en NestJS y cuándo hacerlo?</summary>

#### NestJS / Testing

Mockear dependencias significa reemplazar colaboraciones externas (DB, HTTP,
cola, cache) por dobles controlados para probar una unidad de forma aislada.

#### Cuándo mockear

1. En **unit tests** casi siempre.
2. Cuando la dependencia es lenta/no determinista.
3. Cuando quieres forzar escenarios de error difíciles de reproducir.

#### Cuándo NO mockear

1. En integration/e2e donde necesitas validar wiring real.
2. Cuando el comportamiento de la dependencia es parte crítica del test.

#### Patrón recomendado en NestJS

Usa `Test.createTestingModule` y sobrescribe providers:

```ts
const repoMock = {
  findById: jest.fn(),
  save: jest.fn(),
};

const module = await Test.createTestingModule({
  providers: [
    UsersService,
    { provide: UsersRepository, useValue: repoMock },
  ],
}).compile();
```

O con token:

```ts
{ provide: 'PAYMENTS_PORT', useValue: paymentsMock }
```

#### Buenas prácticas de mocking

1. Mockear solo bordes externos, no toda la lógica interna.
2. Definir comportamiento por test (`mockResolvedValue`, `mockRejectedValue`).
3. Resetear mocks en `beforeEach`.
4. Verificar efectos observables, no detalles frágiles.

#### Ejemplo de escenario de error

```ts
repoMock.save.mockRejectedValue(new Error('DB timeout'));
await expect(service.create(dto)).rejects.toThrow('DB timeout');
```

#### Errores comunes

1. Mocks demasiado “inteligentes” que replican producción y esconden fallos.
2. No testear caminos negativos.
3. Acoplar test a número exacto de llamadas irrelevantes.

#### Conclusión

Mockear bien en NestJS acelera tests y mejora foco en comportamiento de la unidad.
Hazlo para aislamiento; evita abuso cuando necesitas validar integración real.

</details>

<details>
<summary>99. ¿Cómo escribir integration tests en NestJS usando TestingModule?</summary>

#### NestJS / Testing

Los **integration tests** verifican que varios componentes reales trabajen juntos
(módulo, providers, repositorios, DB de prueba), sin llegar al nivel full E2E.

#### Qué validan

1. Wiring real de dependencias en módulo.
2. Colaboración service + repository + infraestructura.
3. Errores de configuración que unit tests con mocks no detectan.

#### Patrón con `TestingModule`

1. Crear módulo de prueba con imports reales.
2. Usar DB de test (sqlite/memory/testcontainer).
3. Ejecutar casos sobre providers reales.

#### Ejemplo conceptual

```ts
import { Test } from '@nestjs/testing';
import { TypeOrmModule } from '@nestjs/typeorm';

describe('UsersService (integration)', () => {
  let moduleRef;
  let service: UsersService;

  beforeAll(async () => {
    moduleRef = await Test.createTestingModule({
      imports: [
        TypeOrmModule.forRoot({
          type: 'sqlite',
          database: ':memory:',
          dropSchema: true,
          entities: [UserEntity],
          synchronize: true,
        }),
        TypeOrmModule.forFeature([UserEntity]),
      ],
      providers: [UsersService],
    }).compile();

    service = moduleRef.get(UsersService);
  });

  afterAll(async () => {
    await moduleRef.close();
  });

  it('creates and fetches user', async () => {
    const created = await service.create({ email: 'u@test.com', password: 'secret123' });
    const found = await service.getById(created.id);

    expect(found.email).toBe('u@test.com');
  });
});
```

#### Buenas prácticas

1. Aislar estado entre tests (transacción rollback o reset DB).
2. No mockear capa que quieres validar.
3. Mantener fixtures simples y reproducibles.
4. Correr integration tests en CI.

#### Unit vs Integration (rápido)

1. Unit: rápido, aislado, mocks.
2. Integration: más lento, más real, detecta errores de wiring/persistencia.

#### Conclusión

Integration tests con `TestingModule` cierran la brecha entre unit y E2E,
asegurando que módulos NestJS funcionen correctamente en condiciones cercanas a producción.

</details>

<details>
<summary>100. ¿Qué es testing end-to-end (E2E) en NestJS y en qué se diferencia de unit e integration tests?</summary>

#### NestJS / Testing

Los **E2E tests** validan el sistema completo desde la entrada HTTP hasta la
respuesta final, incluyendo middleware, guards, pipes, controllers, services,
persistencia y configuración realista.

#### Diferencia entre niveles

1. **Unit**
   Prueba una unidad aislada con mocks.

2. **Integration**
   Prueba colaboración entre componentes/módulos reales.

3. **E2E**
   Prueba flujo completo de la app como lo ve un cliente.

#### Qué detecta E2E que otros no

1. Errores de routing/bootstrap global.
2. Problemas de middleware/guard/pipe en cadena real.
3. Contrato HTTP real (status, headers, body).
4. Fallos de configuración entre módulos.

#### Patrón típico en NestJS (`supertest`)

```ts
import { INestApplication } from '@nestjs/common';
import { Test } from '@nestjs/testing';
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

  it('/users (POST) creates user', async () => {
    const res = await request(app.getHttpServer())
      .post('/users')
      .send({ email: 'e2e@test.com', password: 'secret123' })
      .expect(201);

    expect(res.body.email).toBe('e2e@test.com');
  });
});
```

#### Buenas prácticas

1. Ejecutar E2E contra entorno de test aislado.
2. Preparar/limpiar datos por suite.
3. Cubrir flujos críticos (auth, pagos, creación de pedidos).
4. Mantener número razonable (E2E son más lentos).

#### Conclusión

Unit da velocidad, integration valida wiring, E2E asegura comportamiento real del
producto. Los tres niveles son complementarios, no excluyentes.

</details>

<details>
<summary>101. ¿Qué es Nest CLI y qué comandos se usan con más frecuencia?</summary>

#### NestJS

**Nest CLI** (`@nestjs/cli`) es la herramienta oficial para crear, generar y
operar proyectos NestJS de forma estandarizada.

#### Para qué sirve

1. Crear proyecto base.
2. Generar artefactos (module/controller/service/etc.).
3. Ejecutar app en dev/prod.
4. Build y testing workflow.

#### Comandos más usados

1. `nest new <project-name>`
   Crea un nuevo proyecto.

2. `nest generate <schematic> <name>` o `nest g ...`
   Genera código boilerplate.

Ejemplos:

1. `nest g module users`
2. `nest g controller users`
3. `nest g service users`
4. `nest g resource users` (CRUD completo)

3. `nest start`
   Arranca la app.

4. `nest start --watch`
   Modo desarrollo con recarga.

5. `nest build`
   Compila TypeScript a `dist/`.

6. `nest info`
   Muestra versiones y entorno.

#### Relación con scripts npm

En muchos repos se usan scripts equivalentes:

1. `npm run start:dev`
2. `npm run build`
3. `npm run test`

CLI y scripts conviven; scripts suelen ser interfaz estándar de equipo/CI.

#### Buenas prácticas

1. Usar generators para mantener convención de estructura.
2. Revisar boilerplate generado antes de commit.
3. Evitar generación masiva sin diseño de módulos.
4. Mantener CLI y framework en versiones compatibles.

#### Conclusión

Nest CLI acelera desarrollo y uniformiza arquitectura inicial; su mayor valor es
reducir fricción y mantener consistencia en equipos.

</details>

<details>
<summary>102. ¿Cómo organizar correctamente un Dockerfile para una aplicación NestJS (multi-stage build)?</summary>

#### NestJS / Docker

Un **multi-stage Dockerfile** permite construir imagen más pequeña, segura y
rápida para producción, separando etapa de build y etapa de runtime.

#### Objetivos

1. Reducir tamaño final de imagen.
2. Evitar incluir toolchain de build en runtime.
3. Mejorar seguridad (menor superficie de ataque).
4. Acelerar build con cache de dependencias.

#### Ejemplo recomendado (multi-stage)

```dockerfile
# 1) Dependencies + build
FROM node:20-alpine AS builder
WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build

# 2) Production runtime
FROM node:20-alpine AS runner
WORKDIR /app
ENV NODE_ENV=production

COPY package*.json ./
RUN npm ci --omit=dev

COPY --from=builder /app/dist ./dist

# opcional: si usas prisma/migraciones, copiar artefactos necesarios
# COPY --from=builder /app/prisma ./prisma

EXPOSE 3000
CMD ["node", "dist/main.js"]
```

#### Puntos críticos

1. `npm ci` para instalaciones reproducibles.
2. `--omit=dev` en runtime para no llevar dependencias de desarrollo.
3. Copiar solo `dist` y archivos necesarios.
4. Usar `.dockerignore` (`node_modules`, `.git`, logs, etc.).

#### Hardening recomendado

1. Ejecutar como usuario no-root.
2. Pin de versión base (`node:20.12-alpine` si política exige exactitud).
3. Escaneo de vulnerabilidades de imagen en CI.
4. Variables sensibles vía entorno/secret manager, no en imagen.

#### Consideraciones NestJS

1. Si usas archivos estáticos/templates, cópialos explícitamente al runtime.
2. Si usas Prisma/TypeORM migrations, define estrategia de migración en entrypoint/CI.
3. Healthcheck endpoint (`/health/live`) útil para orchestrator.

#### Conclusión

El Dockerfile multi-stage en NestJS es práctica estándar de producción: imagen
ligera, reproducible y segura, con build y runtime claramente separados.

</details>
