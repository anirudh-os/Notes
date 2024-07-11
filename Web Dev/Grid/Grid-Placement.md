# Grid Placement

* The columns and rows are collectively known as **_tracks_**
    * Rows are **row-tracks**
    * Columns are **columns-tracks**
* The smallest units, so made, are called **_grid cells_**
* The lines seperating these cells are called **_grid lines_**
    * These lines can be controlled by the *gap* property
    * The color and other properties of the grid lines cannot be changed


## Grid Column Property

The grid column property can be used to position the item with respect to two column-tracks.
``` css
grid-column: span 2;
```
Property is a shorthand of `grid-column-start: span 2` and `grid-column-end: auto`.
* This indicates the the item should start at the normal grid position and spans 2 columns.

## Grid Row Property

It orks exacttly the same wasy as the `grid-column` property but affects the row-tracks.
```css
grid-row: span 2;
```

## Grid Area

It is the shorthand for setting the position of the item in a grid.
```css
grid-area: '1' / '2' / '3' / '4';
```
1. `grid-row-start`
2. `grid-column-start`
3. `grid-row-end`
4. `grid-column-end`

## Grid Template

`grid-template` is a shorthand for giving values to `grid-template-rows` and `grid-template-columns`.
```css
grid-template: 'grid-template-rows' / 'grid-template-columns';
```

Practice Website: [here](https://appbrewery.github.io/gridgarden/)