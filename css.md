# CSS/SASS

#### 1.Folder structure 

```
global/
├── util.scss (all mixins are set here)
├── fonts.scss (add any new font face that will be used in the project)
├── grid.scss (optional – preset  grid using susy and flexbox)
├── normalize.scss (add styles to reset browser pre-set styles on elements)
├── global.scss
├── vars.scss
modules/ (all component styles go here)
layout/ (optional)
├── footer.scss (optional)
├── header.scss (optional)
main.scss
```
Get normalize file from https://github.com/necolas/normalize.css/

#### 2.Naming Classes & Values
- Use lower-case
- Separate class name with dashes
- Use unitless line-height values where possible (https://css-tricks.com/almanac/properties/l/line-height/#article-header-id-0)
- Colours and any other reusable values should be stored in variables

```css
/* Bad */
.property {
    color: red;
}
```

```css
/* Good */
.property {
    color: $red;
}
```

- Don't specifying units for zero values

```css
/*Bad*/
padding-left: 0px;
```

```css
/*Good*/
padding-left: 0;
```

- Try to only style the property you are explicitly concerned with to reduce the possibility to overwrite something that wasn’t necessary


#### 3.Titles and comments (for global files)
- Every new section/module we want to give a title
- Title should be commented out as in example below and capitalised:

```css
/*
    GLOBAL
*/
```

- add a secondary comment in between should be added like this (?)

```css

/*
    This is a comment
*/
```

#### 4.Element Nesting
- Element properties should be ordered alphabetically `@` should go at the top, nested elements shold go below properties
- Nesting should ideally go no more than 3 levels deep

```scss
.element {
    @mixin mixin($var);
    property: value;
    property: value;
  
    @include media-query {
        /* responsive styles go here in the same order*/
    }
    &:hover {
        /* element state styles*/
    }
    &:before {
        /* pseudo element styles*/
    }
    .child-element {
    }
}
```

#### 5.Structuring CSS properties
- There should be one space after the “property: value;”
- CSS properties should be kept in alphabetical order
- Avoid using !important
- Use @extend sparingly
- Avoid styling IDs
- Avoid adding styles to elements
- Use one line per selector

```scss
/* Bad */
table, #property {
    margin-top:1vh !important
    border: 0;
    &-head {
        font-size:2rem
    }
}
```

```scss
/* Good */
.table,
.property {
    margin-top: 1vh;
    border: 0;
}
 
 
.table,
.property-head {
    font-size: 2rem;
}
```

#### 6.Media queries & Breakpoints
- Nested inside elements
- Use specified mixins for breakpoint sizes
```css
small: /* Talk to designers */
medium: /* Talk to designers */
large: /* Talk to designers */
```

If specific media query calues are needed for elements the please use element name for media query.

- Avoid defining a new element inside media query
- Mobile first media queries where applicable
