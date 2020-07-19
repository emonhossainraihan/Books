# CSS master

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

# CSS in depth 

When declarations conflict, the cascade considers three things to resolve the difference:

- Stylesheet origin—Where the styles come from. Your styles are applied in conjunction with the browser’s default styles.
- Selector specificity—Which selectors take precedence over which.
- Source order—Order in which styles are declared in the stylesheet.

Each declaration is made up of a property (color) and a value (black). Properties aren’t to be confused with attributes, which are part of the HTML syntax. For example, in the element `<a href="/">`, href is an attribute of the a tag.    

```css
/*Together, the selector and declaration block are called a ruleset*/
/*selector*/ body {
/*declaration*/  color: black;
/*declaration*/  font-family: Helvetica;
}
```

## The exact rules of specificity are:
1. If a selector has more IDs, it wins (that is, it’s more specific).
2. If that results in a tie, the selector with the most classes wins.
3. If that results in a tie, the selector with the most tag names wins.

Pseudo-class selectors (for example, :hover) and attribute selectors (for example, [type="input"]) each have the same specificity as a class selector. The universal selector (*) and combinators (>, +, ~) have no effect on specificity.      

>A helpful mnemonic to remember this order is LoVe/HAte—link, visited, hover, active. 

## Shorthand properties 

- background is a shorthand property for multiple background properties: background-color, background-image, background-size, background-repeat, background-position, background-origin, background-chip, and background-attachment.
- border is a shorthand for border-width, border-style, and border-color, which are each in turn shorthand properties as well.
- border-width is shorthand for the top, right, bottom, and left border widths.

>Remembering this order can keep you out of trouble. In fact, the word TRouBLe is an mnemonic you can use to remember the order: top, right, bottom, left. Another is Horizontal, vertical 

##  The dreaded FOUT and FOIT      



