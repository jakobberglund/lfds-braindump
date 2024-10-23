
## What is a component?
A component is a building block used to develop consistent user interfaces. It is separated from application and business logic and as such is generic and reusable.
## Reusability
We strive for components without side effects. For example, they shouldn't make api calls on their own, or expect specific contexts or stores on the outside. Data is passed as props, internal state is kept in the component itself and communication with the outside world is by fire-and-forget events. This allows for a much higher reusability, testability, predictability and robustness.
## Scaffolding
We want to provide CLI-based tools to scaffold out new components quickly, to ensure that we follow te correct design choices in code standards, naming conventions and api:s. This will be handy especially in the beginning when we most likely will have large churn of new components.
## Output targets
We want the component library to expose easy-to-use variants that integrates well with different consuming frameworks. Most of the largest web components frameworks have tools for this out-of-the-box. So, for example we develop a core web components component library, and fro that one create a Reactified version that wraps the individual components in mechanics that make them more Reactlike to work with in a React application. This is distributed separately as its own package:

```ts
import { } from '@lfds/core' // <--- This is for regular use
import { } from '@lfds/react' // <--- React apps would do this instead
```
## Naming conventions
This pattern for naming components is tried and tested and scales really well: `{prefix!}-{category!}-{name?}-{modifier?}` In some rare cases the category and the name is the same. In these cases, it's enough to write the word once.

```html
<ui-form />
<ui-form-input />
<ui-form-input-number />
```
#### Consistency and predictability
This is also reflected in the folder structure inside of the project, where the components are structured according to the same structure: `components/ui/form/form-input-number/ui-form-input-number.ts`.

## Properties

### Naming convention
Properties are name spaced with a short prefix (for example `ds`). This makes it really easy to separate them from html attributes as well as props from third-party libraries.

```html
<!-- In this hypothetical example we can see that "u-variant" is our own property, 
while "to" is not (which would imply an internal usage of something like "next-link") and "title" is a standard html attribute -->
<UiLink 
  ds-variant="secondary"
  to="url"
  title="klaatu verada niktu" 
/>
```

### Types
We use types over interfaces at all times (unless there's a _really really really_ good reason for sidestepping this)

#### Avoid boolean props
An exception to this is props that maps directly to boolean html attributes.  
 
❌ Don't
```ts
type UiFooProps = {
  dsActive: true;
}
```
✅ Do
```ts
type UiFooProps {
  dsState: 'active' | 'inactive';
}
```

#### Avoid Enums in favor of union types
Unless there's a really good reason to use an Enum (for example by adding a more readable type name to something expected form an external api or similar: (`ADMIN = 1`)

❌ Don't
```ts
enum Layout {
  FULL = 'full',
  HALF = 'half'
}
 
type UiFooProps = {
  dsLayout: Layout;
}
```

✅ Do
```ts
type UiFooProps = {
  dsLayout: 'full' | 'half';
}
```
