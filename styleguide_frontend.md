# CSS Styleguide #
## Coding Style ##
* Use hard-tabs.
* Put spaces after `:` in property declarations.
* Put spaces before `{` in rule declarations.
* Use hex color codes `#000` unless using rgba.
* Use `//` for comment blocks (instead of `/* */`).

Here is good example syntax:
```css
// This is a good example!
.styleguide-format {
  border: 1px solid #0f0;
  color: #000;
  background: rgba(0,0,0,0.5);
}
```

##SCSS Style##
* Any `$variable` or `@mixin` that is used in more than one file should be put in `global/`. Others should be put at the top of the file where they're used.
* As a rule of thumb, don't nest further than 3 levels deep. If you find yourself going further, think about reorganizing your rules (either the specificity needed, or the layout of the nesting).

##File Organization##
In general, the CSS file organization should follow something like this:

```
styles
├── _base.scss  /* Base-level tags */
├── global
│   ├── _settings.scss // Constants and variables - colors, sizes, paddings etc.
│   ├── _helpers.scss  // Mixins and function definitions
│   ├── _reset.scss     // Usually this is Normalize.css
│   ├── _animations.scss // Keyframe animations
│   ├── _typo.scss // Base-level typography (colors, fonts)
├── elements
│   ├── _buttons.scss // Button’s definitions
│   ├── _form-elements.scss // Input boxes etc
│   ├── _panels.scss
├── modules
│   ├── _header.scss
│   ├── _footer.scss
│   ├── _forms.scss // Forms’ styling
│   ├── _navigation.scss // All about site navigation
│   ├── _modals.scss // Modal dialogs
└── vendor  // All third party stuff
```

## Measurements ##
Amidst the diversity of CSS measurement systems it can be difficult for web developers to understand which units to use where, and when, on their pages. The instinct is to use just one system for everything, but that decision can severely limit the execution of your designs.

What follows is a list of suggestions, not absolute rules

### Pixels (px) ###
<b>Use for:</b> hairline borders and general elements when creating fixed-width designs; values for CSS shadow displacement. Avoid using in `@media` breakpoints, as doing so breaks pages when they are zoomed: use `rem` or `em` instead.

<b>Don't use for:</b> typography. (Exception: setting a base font-size in a CSS reset).

### Percentage (%) ###
<b>Use for:</b> making responsive images and containers; setting `height` on the body in some cases.

<b>Don't use for:</b> typography. (Exception: `font-size` CSS `reset`.)

### em, ex, rem ###
<b>Use for:</b> typography, and elements related to typography (margins, for example), with the understanding that `em` and `ex` have a subtle “gotchas” when used in complex layouts. Consider using `rem` as an alternative.

### Points ###
<b>Use for:</b> print stylesheets.

<b>Don’t use for:</b> anything else.

### Raw numbers ###
While almost every CSS property requires that the measurement system be specified in the declaration, a few are best used with plain integer or floating-point values. In particular, `line-height` and `border-image` should be used with raw numbers.