# Bootstrap

## Introduction

It is a popular CSS framework having a vast collection of styles for various elements of a webpage.

The styles are include into our webpage by adding classes to the elements we wish to style.

### linking

Paste the following in the head section of the html:

```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-QWTKZyjpPEjISv5WaRU9OFeRpok6YctnYmDr5pNlyT2bRjXh0JMhjY6hW+ALEwIH" crossorigin="anonymous">
```

Or paste this right before the end of the body tag:

```html
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-YvpcrYf0tY3lHB60NNkmXc5s9fDVZLESaAA55NDzOxhy9GkcIdslK1eN7N6jIeHz" crossorigin="anonymous"></script>
```

## Bootstrap Layout

### The 12 Column System

There exists a root div with the class `container` in which there are sub divs with class `row` and inside them, divs with class `col` are present. The bootstrap sizes every column equally and spaces them so that they spread across the container (`auto fit`).
* The bootstrap container is responsive
* There can exist a maximum of 12 columns in the bootstrap container

### Sized Columns

The columns can be sized manually by giving them classes like `col-2` or `col-4`.
* col-2: The column would span 2 of the 12 columns
* col-4: The column would span 4 of the 12 columns

### Breakpoints

Breakpoints can be added to the classes to make the elements responsive. For example: 

```html
<div class="col-sm-2">
```

Here `sm` is a breakpoint for values >=576px. It means we want the element to be of that span for the small screen and all screens above that size and below that size, it'll be given 100% of the viewport width.

The available braekpoints are:

| Breakpoint |	Class infix	| Dimensions |
| ---------- | :------------: | ----------: |
| Extra small |	None |	<576px |
| Small	| sm |	≥576px |
| Medium |	md |	≥768px |
| Large	| lg |	≥992px |
| Extra large |	xl |	≥1200px |
| Extra extra large	| xxl |	≥1400px |

#### Multiple Breakpoints

Multiple breakpoints can be added to a single class. Example:

```html
<div class="col-sm-12 col-md-8 col-lg-4">
```

So,
1. For screens of size large and above, the column spans 4
2. For screens of size >= medium and < large, the column spans 8
3. For screens of size >= small and < medium, the column spans 12

Practice Website: [here](https://appbrewery.github.io/bootstrap-layout/)