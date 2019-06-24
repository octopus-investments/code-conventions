# HTML

#### 1.General
- Don’t use mix tabs and spaces for indentation.
- HTML5 (HTML syntax) is preferred for all HTML documents: <!DOCTYPE html>
- Use valid Html where possible
- Use elements according to their purpose. For example, use <header> tags for headings, <p> tags for paragraphs, <a> elements for anchors, etc

#### 2.Images
Should always provide alternative content for multimedia elements such as for example <img>. Add in an “alt” attribute with description. This is not the case though for elements that have no meaning but are only a design element. For example a video in the background and similar cases.

```html
<!-- Bad -->
<img src="static/global/bear.svg">
```

```html
<!-- Good -->
<img src="static/global/bear.svg" alt="Dancing Bear">
```

#### 3.Formatting
- Use a new line for every block, list or table element
- If an element has a lot of attributes they can be structured in new lines with an indentation of 4 spaces from the element

```html
<!-- Bad -->
<a href="https://octopusinvestments.com/investor/privacy-policy/" target="_blank" rel="noreferrer noopener" className="c-pink fw-b td-n">
```

```html
<!-- Good -->
<a
    href="https://octopusinvestments.com/investor/privacy-policy/"
    target="_blank"
    rel="noreferrer noopener"
    className="c-pink fw-b td-n"
>
```

#### 4.Use double quotes “”

```html
<!-- Bad -->
<div class='content-box blue rounded'>yo!</div>
```

```html
<!-- Good -->
<div class="content-box blue rounded">yo!</div>
```

#### 5.SEO Optimisations
- Use <title> and <meta  name=”description”> where possible
- Use rel=” canonical” to avoid duplicate content where possible
