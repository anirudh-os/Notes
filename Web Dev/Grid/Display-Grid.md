# Grid

## Grid v/s Flexbox

| Flexbox            | Grid               |
|---------           |---------           |
|1-dimensional layout|2-dimensional layout|

Developers prefer using combination of both flexbox and grid to create their designs.

## display: grid

HTML code:
```html
<div class="container">
    <p>...</p>
    <p>...</p>
    <p>...</p>
    <p>...</p>
</div>
```
Styling:
```css
.container {
    display: grid;
    grid-template-columns: 1fr 2fr;
    grid-template-rows: 1fr 1fr;
    gap: 10px;
}
```

>display: grid

It changes the display layout to grid.

>grid-template-columns: 1fr 2fr

It sets the width of columns to 1fr[^1] and 2fr respectively

[^1]:fr = fraction ratio. The width of the columns will be in 1:2 ratio.

>grid-template-rows: 1fr 1fr

It sets the width of both columns to 1fr

>gap: 10px

It is the gap between 2 consecutive rows or columns

Practice: [here](https://appbrewery.github.io/grid-vs-flexbox)