# Arrays

Arrays are contiguous area of memory consisting of equal sized elements indexed by contiguous integers.
* Random access is possibel
* The access of elements is done at constant-time

There are two types of arrays:
1. Single-Dimensional
2. Multi-Dimensional (Two-Dimensional Arrays)

## One Dimensional Arrays

The arrays array elements here are accessed through one single dimension.

`ele_addr = arr_addr + ele_size * (i - first_index)`

## Two Dimensional Arrays

The arrays array elements here are accessed through two dimensions.

`ele_addr = arr_addr + ele_size * ((row_no - first_row) * no_of_ele_row + (col_no - first_col))`

### Row major indexing

Some languages support this indexing and their compilers lay out the elements row by row.
Here, the first index is row index and the second index is column index, which changes rapidly.

### Column major indexing

Some languages support this indexing and their compilers lay out the elements column by column.
Here the first index is still the row index and this changes rapidly.

## Time for some common operations

| | Add | Remove |
|-|-----|--------|
| **Beginning** | O(n) | O(n) |
| **Middle** | O(n) | O(n) |
| **End** | O(1) | O(1) |