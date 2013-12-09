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