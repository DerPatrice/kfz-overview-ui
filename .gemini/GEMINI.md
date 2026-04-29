
You are an expert in TypeScript, Angular, and scalable web application development. You write functional, maintainable, performant, and accessible code following Angular and TypeScript best practices.

## Angular 21 Folder Structure Rules
This project follows a modern, domain-driven folder structure for Angular 21 standalone applications.

## Critical Rules
- **No "component" in filenames**: Do not use the word `component` inside the naming of files (e.g., use `login.ts` instead of `login.component.ts`).

## Structure Overview
### `src/app/core/`
App-wide, singleton-level logic.
- `guards/`: Route guards.
- `interceptors/`: HTTP interceptors.
- `services/`: Global services (Auth, API, Storage, etc.).
- `config/`: Constants, tokens, configs.
- `core.providers.ts`: Global providers.

### `src/app/shared/`
Reusable UI & utilities.
- `components/`: Reusable standalone UI components (Button, Card, etc.).
- `directives/`: Shared directives.
- `pipes/`: Shared pipes.
- `services/`: Shared services.
- `utils/`: Helper functions (date utils, validators, etc.).
- `index.ts`: Barrel export for shared pieces.

### `src/app/features/`
Feature-based structure (domain-driven).
- `auth/`: Authentication feature.
- `dashboard/`: Dashboard feature.
- Each feature contains its own components, services, and routes.

### `src/app/layout/`
Global layouts (wrappers around features).
- `header/`: Header component.
- `footer/`: Footer component.
- `layout.ts`: Main layout with router-outlet.

### `src/app/state/`
Global state (signals, NgRx, or simple stores).

## Root Files
- `src/app/app.ts`: Root standalone component.
- `src/app/app.routes.ts`: Root routing config.
- `src/app/app.config.ts`: Root app config.


## TypeScript Best Practices

- Use strict type checking
- Prefer type inference when the type is obvious
- Avoid the `any` type; use `unknown` when type is uncertain

## Angular Best Practices

- Always use standalone components over NgModules
- Must NOT set `standalone: true` inside Angular decorators. It's the default in Angular v20+.
- Use signals for state management
- Implement lazy loading for feature routes
- Do NOT use the `@HostBinding` and `@HostListener` decorators. Put host bindings inside the `host` object of the `@Component` or `@Directive` decorator instead
- Use `NgOptimizedImage` for all static images.
  - `NgOptimizedImage` does not work for inline base64 images.

## Accessibility Requirements

- It MUST pass all AXE checks.
- It MUST follow all WCAG AA minimums, including focus management, color contrast, and ARIA attributes.

### Components

- Keep components small and focused on a single responsibility
- Use `input()` and `output()` functions instead of decorators
- Use `computed()` for derived state
- Set `changeDetection: ChangeDetectionStrategy.OnPush` in `@Component` decorator
- Prefer inline templates for small components
- Prefer Reactive forms instead of Template-driven ones
- Do NOT use `ngClass`, use `class` bindings instead
- Do NOT use `ngStyle`, use `style` bindings instead
- When using external templates/styles, use paths relative to the component TS file.

## State Management

- Use signals for local component state
- Use `computed()` for derived state
- Keep state transformations pure and predictable
- Do NOT use `mutate` on signals, use `update` or `set` instead

## Templates

- Keep templates simple and avoid complex logic
- Use native control flow (`@if`, `@for`, `@switch`) instead of `*ngIf`, `*ngFor`, `*ngSwitch`
- Use the async pipe to handle observables
- Do not assume globals like (`new Date()`) are available.
- Do not write arrow functions in templates (they are not supported).

## Services

- Design services around a single responsibility
- Use the `providedIn: 'root'` option for singleton services
- Use the `inject()` function instead of constructor injection
