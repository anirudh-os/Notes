# Sizing

The size of the grid items is set by
```css
grid-template-columns: size size;
grid-template-rows: size size;
```

It can be represented by the shorthand:
```css
grid-template: size size / size size;
```
Here rows are given values first and then are columns.

If there are more items than those whose size is defined, we can set their dimensions by this property:

```css
grid-auto-rows: size;
grid-auto-columns: size;
```

## Fixed Sizing

We can give values like ```200px``` or ```2rem``` to the grid template properties. The disadvantage to this is that they are not responsive.

## Auto Sizing

```css
grid-template-columns: size auto;
grid-template-rows: size auto;
```

The ```auto``` keyword changes the responsiveness differently for rows and columns.
* rows: It makes it so that the row extends as much as to be able to fit its content.
* columns: It makes it so that the column takes up the available space on screen.

## Fractional Sizing

We can set the sizes of the grid items in any ratio as required.
```css
grid-template-columns: 1fr 2fr;
grid-template-rows: 1fr 2fr;
```
This sizing works the same way as the Auto Sizing, but all of the item sizes will be responsive.

## MinMax Sizing

The column sizes can be given a range of responsiveness
```css
grid-template-columns: 100px minmax(200px, 400px);
grid-template-rows: 100px 200px;
```
The 2nd column will now be responsive in the range `200px` to `400px`.




Practice website: [here](https://appbrewery.github.io/grid-sizing)