
The design system consists of a few different key things:
- A component library
- Design tokens
- Tools for working with design and development of UI
- Processes for designer/developer collaboration
- Processes for defining and maintaining requirements of UI, and governance of this
## Component library
The component library is developed as web components. Components are written in such a way that they can be easily reused and tested. They should be as side-effect free as possible, by not making their own api calls and such. They get their data from props, manage their own internal state and emit events when needed.
### Naming convention
Component names follow this convention: `{prefix}-{category}-{name}-{modifier}` . Example: `<ui-form-input>`, `<ui-form-input-number>`. One exception to this rule is when the category and name is the same, in which case it doesn't have to be duplicated (`<ui-form>` and `<ui-button>` for example). 

This is also reflected in the folder structure inside of the project, where the components are structured according to the same structure: `components/ui/form/form-input-number/ui-form-input-number.ts`.

## Design tokens
We want a technology agnostic definition of design tokens, that can be used to generate both css custom properties, Figma variables, iOS and Android assets and documentation from one single source of truth. This can be done by using tools such as [Style dictionary](https://amzn.github.io/style-dictionary/]), and preferably by creating a web app where this can be maintained without the need for coding.

### Naming conventions
Tokens are grouped in different common categories: `color`, `typography`, `layout`, `radii` etc. They are defined as json data, that can be parsed into different consumers (see previous paragraph). The name of the individual tokens should be semantic rather than describe the value (for example `color.background` and not `color.green100`).

## Tools
We use Storybook for developing and testing ui components and design tokens. This becomes an inventory of all the parts that exists in the component library, and becomes the de facto truth. We want ways of syncing stories into Figma to make the developed components the de facto source of truth, and relieves Figma (and designers) from playing catch and having to stay up to date

We use Figma for designing mockups, ideas and exploration. Figma will not be the source of truth for components or tokens (as explained above).
## Processes for designer/developer collaboration
The design system aims to constantly work on and improve the designer/developer process. Generally, the earlier designer and developers start working together the better. We want to actively remove waterfalls, bottlenecks and lengthy feedback loops, and this is primarily done by working together and communicating as much as possible. Some examples:
- Prefer coded prototypes over high fidelity Figma designs
- Create stories for each different state of any given component, to allow for easy import into Figma
## Processes for requirements and governance
Governance is done by a central cross-functional design system team. This is the place for senior representatives and leads from all stakeholders, people with the mandate to say yey or ney.
## Processes for development
We want to make sure that everything we do provides value at every stage. So we tie up our work in close collaboration with product teams and make sure that we only build things that has a real-life right-now impact. This should be the process at least until we have enough velocity in the component library to have teams more or less build anything they need. By doing it like this, we keep super.short feedback loops, don't make early assumptions and don't develop things willy nilly that the teams might not be asking for. We also create trust and happiness in the development teams if we focus on solving their current issues and bring them into the loop early and often.
