# [Frontend Guidelines Questionnaire](https://github.com/bradfrost/frontend-guidelines-questionnaire)

> A one-page questionnaire to help our team establish effective frontend guidelines, so that you we can write consistent and cohesive code together.

## HTML

### HTML Principles

- **What are some general principles your team should follow when writing HTML?** (for example, authoring semantic HTML5 markup, accessibility, etc. See [these](http://www.yellowshoe.com.au/standards/#html) [resources](http://codeguide.co/#html) for [inspiration](http://manuals.gravitydept.com/code/html))
    - Use HTML5 doctype
    - ARIA roles are good. Use them for accessibility. 
    - Use `data-` refs for JS hooks, rather than classnames. Eg, `<div data-analytics></div>` rather than `<div class='js-analytics'>`
    - Boolean attributes don't need a value: `<option selected>` rather than `<option selected='selected'>`
    - Tag names in lowercase.

### HTML Tools

- **Are you using an HTML preprocessor** *(such as [HAML](http://haml.info/), [Jade](http://jade-lang.com/), etc)*? 
    - No.

- **Are you using a templating engine** *(such as [Mustache](https://mustache.github.io/), [Handlebars](http://handlebarsjs.com/), etc)*?
    - No. If you need more complexity than raw HTML can provide you, then you should defer to JSX (via React or Preact or similar).
    - Django Templates, Jinja2, Nunjucks, Twig. All smarty-syntax template engines.

    - Django custom tags have to be loaded at the top of a template.
    - Jinja2 requires you to use `iteritems()` to evaluate lists, eg `for item in list.iteritems()`.
    - Django templates forces you to write logic in python.
    - Use 'templatetags' for logic (if required), otherwise use partials via `include "includes/my_partial.html"`

### HTML Style

- **Spaces or Tabs?**
    - Spaces. Refer to our [prettier config](https://github.com/springload/prettier-config-springload/blob/master/lib/index.js).


- **What does HTML commenting look like?** 
    - Use Django's comments unless you really want the comment to be in the markup.
    - `{# Hello, i'm a comment #}` instead of `<!-- Hello, I'm a comment -->`


---------------

## CSS

### CSS Principles

- **What are some general principles your team should follow when writing CSS?** *(For example, modularity, avoiding long selector strings, etc. See [these](http://cssguidelin.es/) [resources](http://www.yellowshoe.com.au/standards/#css) [for](http://manuals.gravitydept.com/code/css) [inspiration](http://codeguide.co/#css))*
    - See our CSS [one pager](https://github.com/springload/frontend-starter-kit/blob/master/docs/css.md)

### CSS Methodology

- **Is your team using a CSS methodology** *(such as [SMACSS](https://smacss.com/), [BEM](https://en.bem.info/method/), or [OOCSS](http://oocss.org/)*? If yes, where is the documentation for that methodology?
    - See our CSS [one pager](https://github.com/springload/frontend-starter-kit/blob/master/docs/css.md)

- **Are you deviating from the methodology in any way?** If so, can you highlight these conventions?
    - Refer to link above


### CSS Tools

- **Is the team using a preprocessor** *(such as [Sass](http://sass-lang.com/) or [Less](http://lesscss.org/))*?
    - Sass. Via libsass.

- **What are the guidelines for using that preprocessor** *(check out [Sass Guidelines](http://sass-guidelin.es/) for inspiration)*?
    - We don't really write vanilla CSS anymore, so the CSS guidelines above are the sass guidelines.

- **Are you using a CSS base** *(such as [Normalize](https://necolas.github.io/normalize.css/) or a [reset](http://meyerweb.com/eric/tools/css/reset/))*?
    - [Normalize](https://github.com/necolas/normalize.css/).

- **Are you using any CSS postprocessors** *(such as Prefixfree or [Autoprefixer](https://github.com/postcss/autoprefixer))*?
    - Pleeease. Mainly for autoprefixing + REM fallbacks for old IE, minification.

- **Are there specific CSS techniques you're utilizing** *(such as [critical CSS](https://www.smashingmagazine.com/2015/08/understanding-critical-css/))*?
    - No


### CSS Frameworks

- **Is the team using a framework** *(such as [Bootstrap](http://getbootstrap.com/) or [Foundation](http://foundation.zurb.com/))*? If yes, where is the documentation for that framework?
    - No.
- **Are you deviating from the framework in any way?** If so, can you highlight these conventions?
    - N/A

### CSS Style

- **Spaces or Tabs?**
    - Spaces. Refer to our [prettier config](https://github.com/springload/prettier-config-springload/blob/master/lib/index.js).


- **Spacing around rules?**
- **[Grouping](https://smacss.com/book/formatting#grouping) properties?**
- **What does CSS commenting look like?** 

---------------

## JavaScript

### JavaScript Principles

- **What are some general principles your team should follow when writing JavaScript?**
    - Airbnb have published [living style guide](https://github.com/airbnb/javascript), upon which Springload’s styles are heavily modelled and extended.
    - Airbnb’s styles are trumped in some areas by our [Springload Eslint config](https://github.com/springload/eslint-plugin-springload) files (most obviously in whitespace/indentation).

### JavaScript tools

- **Are you using a JavaScript framework** *(such as [jQuery](http://jquery.com/), [Ember](http://emberjs.com/), [Angular](https://angularjs.org/), etc)*?
    - We prefer [React](https://reactjs.org/).
    - To scaffold a batteries-included React project we prefer [Create React App](https://github.com/facebook/create-react-app).


- **Do you use JQuery?**
    - We try to avoid using JQuery when possible. Most of what can be achieved with JQuery be achieved just as easily in vanilla Javascript, particularly if you don't have to support legacy browsers.
    - However, you might spot Jquery on a few of our legacy projects, which is fine.


- **Are you using any polyfills or shims** *(such as [any of these](https://github.com/Modernizr/Modernizr/wiki/HTML5-Cross-Browser-Polyfills))*?
    - `babel-polyfill` in combination with `.babelrc` and [`browserslist`](http://browserl.ist/) key in `package.json`.
    - A typical browserslist value might look like this:

```json
{
    "browserslist": [
        "ie >= 11",
        "last 2 Chrome versions",
        "last 2 Firefox versions",
        "last 2 Safari versions",
        "last 2 iOS versions",
        "last 2 Edge versions"
    ]
}
```
    - If a specific polyfill is needed for a particular futuristic feature, then look to [corejs](https://github.com/zloirock/core-js) where possible.
    

### JavaScript Style 

*(See [these](https://github.com/airbnb/javascript) [resources](https://github.com/rwaldron/idiomatic.js) for [inspiration](https://github.com/styleguide/javascript))*

- **Spaces or Tabs?**
- Spaces x 4.
- **What does JS commenting look like?** 
- DocBlockr style (`/** ... */`) for multi-line comments, `// slash-style` for inline.
- [What patterns are you following](https://addyosmani.com/resources/essentialjsdesignpatterns/book/)?
- ES6 modules. > CommonJS.


---------------

## Tooling

- **Are you using a task runner** *(such as [Grunt](http://gruntjs.com/) or [Gulp](http://gulpjs.com/))*?
    - [npm scripts](https://docs.npmjs.com/misc/scripts).
    - Many legacy projects use grunt and gulp, which is fine, though we would migrate these to npm scripts where possible.
    
- **Why not Gulp?**
    - Gulp went two years without so much as a patch release, and most of the community moved on. It provides a largely unncessary layer of abstraction to what can now be done really simply with npm scripts, particularly because our compiler of choice Webpack has its own CLI.

- **Are you using a dependency manager** *(such as [Bower](http://bower.io/) or [Composer](https://getcomposer.org/))*
    - We prefer [Yarn](https://yarnpkg.com/en/).
    - We mandate use of an `.nvmrc` file at the project root, so that all developers are using the same version of Node.
    - We mandate use of a `yarn.lock` file (or `package-lock.json` for npm) so that dependencies are identical across all developers' machines.

- **Are you using any scaffolding tools** *(such as [Yeoman](http://yeoman.io/))*
    - CookieCutter. [Link to cookiecutter repo]

- **Are you using any tools to reinforce frontend style** *(such as [Editor Config](http://editorconfig.org/) or [linters](https://github.com/CSSLint/csslint))*?
    - ESLint, SassLint, EditorConfig.
    - GitHooks on changed files.
    - Projects should have linting and tests.

- **Are any other specific pieces of software that are needed to work on this project?**

---------------

## Version control

- **What version control system are you using for your frontend code** *(such as [Git](https://git-scm.com/) or [Subversion](https://subversion.apache.org/))*?
    - Git
- **Where is your version-controlled code hosted** *(such  as [Github](https://github.com/) or [Bitbucket](https://bitbucket.org/))* ?
    - GitHub
- **Do you use a version control workflow** *(such as [gitflow](http://nvie.com/posts/a-successful-git-branching-model/), [centralized](https://www.atlassian.com/git/tutorials/comparing-workflows/centralized-workflow), [feature-branch](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow), etc)*?
    - Feature branches with pull requests and code reviews

- **Who's responsible for managing and governing the version controlled code?**?
- **Where are issues tracked**?
    - GitHub issues for everything!

-----------

## Support and Optimization

It's important to recognize the difference between ["support" and "optimization"](http://bradfrost.com/blog/mobile/support-vs-optimization/). You should do your best to support as many environments as possible while simultaneously optimizing for the environments that make the most sense for your business and users.

- **What browsers are you *optimizing* for?** 
    - We aim to support browsers over 5% of traffic.

- **What devices are you *optimizinog* for?** 
    - This should be derived from each clients' analytics.
    - For instance, 35% of all pageviews on Red Cross are on iOS. 57% from mobile devices.

- **Are you using a [graded browser support](https://github.com/yui/yui3/wiki/Graded-Browser-Support) system?**
    - For government projects, we have to.
    - (RealMe).
- **Are there specific components that require [more specific grading](https://www.filamentgroup.com/lab/grade-the-components.html)?**
    - Perhaps useful for KB/redcross/RealMe/Airport?

## Documentation

- **Are you using a [pattern library tool](http://styleguides.io/tools.html) to document your front-end architecture**?
    - Projects should have a single page with all the front-end components detailed.

- **Where does your documentation live**? What are the links to the documentation?
    - Should be available ether on staging site or local build of the project. Maybe if DEBUG=true in Django, it gets rendered on `http://localhost:8000/pattern-library/`

- **Who's responsible for maintaining and governing the documentation**?
    - The FED.

*Feel free to modify or extend (such as adding specific sections for performance, accessibility, etc) this document for your own organization's needs. For questions, comments, additions, and corrections, please open an issue on Github and/or reach out to [@brad_frost](https://twitter.com/brad_frost) on Twitter.*
