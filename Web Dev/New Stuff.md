# NEW STUFF 🗿

# box-sizing:

Box sizing is a property which controls the inclusion of padding and border in the layout. There are 2 priary values for it:
1. `content-box`: 
    * In this model, the width and height of an element only include the content itself. 
    * Padding and border are added outside of these dimensions.
    * It is the default value.
    ```css
    .example {
        width: 200px;
        padding: 20px;
        border: 5px solid black;
    }
    ```
    ```html
    <!--
        Content Width: 200px
        Padding: 20px on each side (total 40px)
        Border: 5px on each side (total 10px)
        Total Width: 200px (content) + 40px (padding) + 10px (border) = 250px
    -->
    ```

2. `border-box`:
    * the width and height of an element include the content, padding, and border. 
    * This means that padding and border are included within the specified width and height.
    ```css
    .example {
        box-sizing: border-box;
        width: 200px;
        padding: 20px;
        border: 5px solid black;
    }
    ```
    ```html
    <!-- Total Width: 200px (includes content, padding, and border) -->
