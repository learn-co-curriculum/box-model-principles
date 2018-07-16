# Box Model

## Problem Statement




### Objectives

1. Identify the parts of the box model
2. Explore the box model properties
3. Identify `overflow` properties
4. Identify `display` properties

## Identify the Box Model

The **box model** is how we conceptualize the way HTML elements are displayed in a browser. Imagine that every element in an HTML document is a box with certain properties: width, height, padding, margin and a border.

(box model graphic)

**Width** and **height** determines the size of the content in the element. **Padding** expresses the amount of spacing _inside_ the element. **Margin** expresses the amount of spacing _outside_ of the element. The **border** is the line around the element, which has its own style properties. All of these work together to determine the true size of an element on the page.

## Explore the Box Model Properties

### Width and Height

Setting the width and height of an element will affect its content area size.

```
article {
  width: 200px;
  height: 200px;
}
```
Notice that the width and height applies to the content size only. Adding padding and margin will increase the element's overall size.

### Padding

Padding creates more space between the content of an element and the element's border.

```
article {
  width: 200px;
  height: 200px;
  padding: 20px;
}
```

### Margin

Margin creates more space between the element and the other elements around it on the page.

```
article {
  width: 200px;
  height: 200px;
  padding: 20px;
  margin: 20px;
}
```

A note on setting padding and margin around all four sides of the element "box"—you can use the same value to apply equally on the top, right, bottom and left sides or you can set different values for each side. In the example above, we only wrote a single `20px` as the value for both the padding and margin. That means the browser will display the same amount of space around each side of the element.

If we want different amounts of padding or margin, we can set the top and bottom and the right and left with two corresponding values:

```
article {
  width: 200px;
  height: 200px;
  padding: 10px 20px;
  margin: 30px 40px;
}
```

This will display with 10 pixels of padding on the top and bottom, 20 pixels of padding on the right and the left, 30 pixels of margin on the top and the bottom and 40 pixels of margin on the right and the left.

We can also set each side's value individually, moving clockwise around the box model:

```
article {
  width: 200px;
  height: 200px;
  padding: 10px 20px 30px 40px;
  margin: 10px 20px 30px 40px;
}
```

This will display 10 pixels of padding and margin on the top, 20 pixels on the right, 30 pixels on the bottom and 40 pixels on the left.

You can also set each side's value as its own property:

```
article {
  width: 200px;
  height: 200px;
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 30px;
  padding-left: 40px;
}
```

Being able to set separate values for each side of the box gives us more control over how our elements are displayed.

### Border

Whether you see it or not, there is always a border for each HTML element. By default, its value is set to "0;" however, you can not only set a larger value but you can also determine its color and style.

Typically you will see border properties combined on a single line like this:

```
article {
  width: 200px;
  height: 200px;
  padding: 20px;
  margin: 20px;
  border: 1px solid #000;
}
```

Here we set our element border to one pixel, as a solid line, in black. For more control over each of these elements, you can also break them out into their own specific properties:

```
article {
  border-width: 1px;
  border-style: solid;
  border-color: #000;
}
```

You can also set each border's side individually:

```
article {
  border-top: 1px solid #000;
  border-right: 2px solid #666;
  border-bottom: 1px solid #000;
  border-left: 2px solid #666;
}
```
Or you can even set the property for each side individually!

```
article {
  border-top-width: 1px;
  border-right-width: 2px;
  border-bottom-width: 1px;
  border-left-width: 2px;
  border-right-style: solid;
  border-left-style: dashed;
  border-top-color: #000;
  border-bottom-color: #666;
}
```

The possibilities are (almost) endless.

### Legacy Browser display and `box-sizing`

Back in the early days of the web, most browsers interpreted the box model as we described it above; but Internet Explorer wanted to do things its own way. The IE browser displayed an element's padding and margin as part of the element's overall width and height. For example, if we set an element with a width of 200 pixels and a padding of 20 pixels, instead of adding the padding to the original width, the padding would cut into the original width. The result in this scenario would be that IE would display the content area as 160 pixels (200 - 20 on the right - 20 on the left = 160).

We don't have to worry about this display discrepancy nowadays (although if you ever see IE-specific values in older CSS, you'll know that this is why!), but some would aruge that IE's approach to the box model made more sense. We can now replicate it with the `box-sizing` property.



## Overflow

visible
hidden
scroll
auto


## Display

how elements will display by default and how that affects how we size and display elements

inline - appears side-by-side, does not accept width or top/bottom margins
block - displays one after another, takes up the entire width of container unless specified otherwise, can specify width and top/bottom margin
inline-block - displays side-by-side, accepts width and top/bottom margins
(video demonstration)
div
span
table
table-cell
* sets up floating

### Resources

https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model
https://css-tricks.com/the-css-box-model/
https://css-tricks.com/box-sizing/
https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing

box model demo - https://jsFiddle.net/flatiron_school/jtFgz
overflow - https://jsFiddle.net/flatiron_school/sFfw5
display demo - http://jsfiddle.net/flatiron_school/352A6/1/

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/Box-Model' title='Box Model'>Box Model</a> on Learn.co and start learning to code for free.</p>


