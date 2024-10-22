
## What is a design token?
A design token is a reusable piece of ui that is smaller than a component. Things like colors, font sizes, gutters, etc.
## Define once, consume everywhere
We want a technology agnostic definition of design tokens, that can be used to generate both css custom properties, Figma variables, iOS and Android assets and documentation from one single source of truth. This can be done by using tools such as [Style dictionary](https://amzn.github.io/style-dictionary/]), and preferably by creating a web app where this can be maintained without the need for coding.
## Theming
By adopting the techniques described above, we make theming easier as well, especially if we allow exporting css custom props from the design tokens web app, or provide programmatic ways to do it in code.
```css
--lfds--color--background: #ff0000; /* Standard theme */
--lfds--color--background: #00ff00; /* Custom theme */
```
### Naming conventions
Tokens are grouped in different common categories: `color`, `typography`, `layout`, `radii` etc. They are defined as json data, that can be parsed into different consumers (see previous paragraph). The name of the individual tokens should be semantic rather than describe the value (for example `color.background` and not `color.green100`).
## Naming conventions
We prefer semantic names to our design tokens over names that describes their values.

❌ Don't
```ts
color.gray200
```
✅ Do
```ts
color.backgroundSecondary
```
## Distribution
Tokens should be distributed in a way that they can be used without the component library. This allows us to use them even in places where we can not provide the full-on components for some reason or another. By ensuring that we generate standardized outputs from the shared data set (that is, we generate css custom properties that can easily travel across most environments because it is standards and gets in everywhere), we also make theming and such easy.