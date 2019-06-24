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
layout/
├── footer.scss (optional)
├── header.scss (optional)
main.scss
```

#### 2.Naming Classes & Values
- Use lower-case
- Separate class name with dashes
- Use unit-less line-height values (?)
- Colours and any other reusable values should be stored in variables
- Where allowed, avoid specifying units for zero values
- Try to only style the property you are explicitly concerned with to reduce the possibility to overwrite something that wasn’t necessary

```css
/* Bad */
.property {
    color: Red;
    border: 0;
}
```

```css
/* Good */
.property {
    color: $red;
    border: none;
}
```

#### 3.Titles and comments
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
- Elements should be nested in the order of the most relevant information about it.
- Nesting should go no more than 3 levels deep

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
- Avoid using ampersands & for naming nested classes to make them easier to find
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
- Avoid defining a new element inside media query
- Mobile first media queries?
