BEM versus Atomic CSSBEM works best when you have a large number of developers building CSS and HTML modules in parallel. 
It helps to prevent the kind of mistakes and bugs that are created by sizable teams. 
It scales well, in part, because the naming convention is descriptive and predictable. 
BEM isn’t only for large teams, but it works really well for large teams.Atomic CSS works better when there’s a small team or a 
single engineer responsible for developing a set of CSS rules, with full HTML components built by a larger team. With Atomic CSS, 
developers can just look at a style guide—or the CSS source—to determine which set of class names they’ll need for a particular module.

>If BEM is the industry darling, Atomic CSS is its rebellious maverick

- **BEM**: .block__element--modifier
- **Atomic CSS**: In an Atomic CSS system, you can tell what the class name does—but there’s no relationship between class 
names (at least, not those used in the stylesheet) and content types.

## Code-quality Tools

Finally, let’s discuss tools that help you analyze the quality of your CSS. We’ll focus on two:

- stylelint
- UnCSS

## Custom Properties

stom property, select a name and prefix it with two hyphens. Any alphanumeric character can be part of the name. 
Hyphen (-) and underscore (_) characters are also allowed. A broad range of unicode characters can be part of a custom property name, 
including emojis. For the sake of clarity and readability, stick to alphanumeric names.

Custom property names are case-sensitive.

To use a custom property value as a variable, we need to use the var() function.

## Working with Text

- Better-looking Text with @font-face

## Using CSS with SVG

- **Embedding CSS in SVG Documents:**

```html
<svg version="1.1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 200 200" enable-background="new 0 0 200 200">
  <style type="text/css">
    circle {fill: #0c0;}
  </style>
  <circle cx="101.3" cy="96.8" r="79.6" />
</svg>
```
- **Linking from SVG to an External CSS File:** As with HTML, linking to an external CSS file makes it possible to share styles across several SVG documents. 
To link an external CSS file, add `<? xml-stylesheet ?>` to the beginning of your SVG file
