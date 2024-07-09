# Flex Sizing

* Content Width < Width < flex-basis < min-width/max-width
* * **_max-width_**: The complete possible width of text
  * **_min-width_**: The minimum possible width of the text
* We can set the min and max width manually
* But unless the other sizing properties are smaller than min-width or greater than max width, they do not show much of a difference
* **_flex-grow_**: It allows the item to grow till its max-width, which if not set, will grow until the container is occupied
* **_flex-shrink_**: It allows the item to shrink till its min-width, which if not set, till the longest content's length

There exists a short-hand to apply all of these sizinng properties at once,

```css
flex: 1 1 0
```

where:

1. flex-grow
2. flex-shrink
3. flex-basis

* A value '0' to flex-basis keeps makes all items grow/shrink equally.

The above short-hand is so commonly used that a short-hand for it exists:

```css
flex: 1
```

Practice website: [Here](appbrewery.github.io/flexbox-sizing-exercise)
