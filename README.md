# The Box Model

## Problem Statement

Once we begin using CSS to put elements where we want them on the page, we need
to know how the browser is going to interpret our code and how our page is
ultimately going to display. Understanding the box model will give us a solid
foundation for working with this process.

### Objectives

1. Identify the parts of the box model
2. Explore the box model properties
3. Identify `overflow` properties
4. Identify `display` properties

## Identify the Box Model

The **box model** is how we conceptualize the way HTML elements are displayed in
a browser. Imagine that every element in an HTML document is a box with certain
properties: width, height, padding, margin and a border.

![box model diagram](https://curriculum-content.s3.amazonaws.com/fewds/boxmodel.png)

**Width** and **height** determines the size of the content in the element.
**Padding** expresses the amount of spacing _inside_ the element. **Margin**
expresses the amount of spacing _outside_ of the element. The **border** is the
line around the element, which has its own style properties. All of these work
together to determine the true size of an element on the page.

## Explore the Box Model Properties

### Width and Height

Setting the width and height of an element will affect its content area size.

```
article {
  width: 200px;
  height: 200px;
  }
```

Notice that the width and height applies to the content size only. Adding
padding and margin will increase the element's overall size.

### Padding

Padding creates more space between the content of an element and the element's
border.

```
article {
  width: 200px;
  height: 200px;
  padding: 20px;
}
```

### Margin

Margin creates more space between the element and the other elements around it
on the page.

```
article {
  width: 200px;
  height: 200px;
  padding: 20px;
  margin: 20px;
}
```

A note on setting padding and margin around all four sides of the element
"box"—you can use the same value to apply equally on the top, right, bottom and
left sides or you can set different values for each side. In the example above,
we only wrote a single `20px` as the value for both the padding and margin. That
means the browser will display the same amount of space around each side of the
element.

If we want different amounts of padding or margin, we can set the top and bottom
and the right and left with two corresponding values:

```
article {
  width: 200px;
  height: 200px;
  padding: 10px 20px;
  margin: 30px 40px;
}
```

This will display with 10 pixels of padding on the top and bottom, 20 pixels of
padding on the right and the left, 30 pixels of margin on the top and the bottom
and 40 pixels of margin on the right and the left.

We can also set each side's value individually, moving clockwise around the box
model:

```
article {
  width: 200px;
  height: 200px;
  padding: 10px 20px 30px 40px;
  margin: 10px 20px 30px 40px;
}
```

This will display 10 pixels of padding and margin on the top, 20 pixels on the
right, 30 pixels on the bottom and 40 pixels on the left.

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

Being able to set separate values for each side of the box gives us more control
over how our elements are displayed.

### Border

Whether you see it or not, there is always a border for each HTML element. By
default, its value is set to "0;" however, you can not only set a larger value
but you can also determine its color and style.

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

Here we set our element border to one pixel, as a solid line, in black. For more
control over each of these elements, you can also break them out into their own
specific properties:

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

Something else to note: remember when we said that all of these properties go
together to make the true size of the element? That means if we set our width as
200px and our margin as 20px on each side, plus a 1px border, the total width
our element will take up on the screen is 242px (200px + 20px on the right side
+ 20px on the left side + 1px border on the right + 1px border on the left =
242px). Keep that in mind when you determine what sizes you want.

To get a sense for how these properties work in real time, you can play around
with them here:

<iframe width="100%" height="300" src="//jsfiddle.net/flatiron_school/jtFgzembedded/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

### Legacy Browser Display and `box-sizing`

Back in the early days of the web, most browsers interpreted the box model as we
described it above; but Internet Explorer wanted to do things its own way. The
IE browser displayed an element's padding and border as part of the element's
overall width and height. For example, if we set an element with a width of 200
pixels and a padding of 20 pixels, instead of adding the padding to the original
width, the padding would cut into the original width. The result in this
scenario would be that IE would display the content area width as 160 pixels
(200 - 20 on the right - 20 on the left = 160).

We don't have to worry about this display discrepancy often nowadays (although
if you ever see IE-specific values in older CSS, you'll know that this is why!),
but some would aruge that IE's approach to the box model made more sense. We can
now replicate it with the `box-sizing` property.

The `content-box` value instructs the element to use the default box model,
which is the behavior we described first. The padding and border values will be
added to the specified width, to create an element with the total size of 242px.

```
article {
  box-sizing: content-box;
  width: 200px;
  padding: 20px;
  border: 1px solid #000;
}
```

The `border-box` value, on the other hand, will calcuate the width including the
content, padding and border, but not the margin. So this CSS:

```
article {
  box-sizing: border-box;
  width: 200px;
  padding: 20px;
  border: 1px solid #000;
}
```

... will result in an element with a total width of 158px.

## Overflow

When working with boxes and containers, you might find that the content inside
doesn't follow the rules you thought made for it to follow. For example, you set
a height of 500px on your element, but the text inside of the box stretches
beyond the box's boundaries. This is where you need to turn to the `overflow`
property.

```
article {
  overflow: visible; // This is the default setting and allows the content to, well, flow over.
  overflow: hidden; // This will cut off and hide any content that flows outside the box.
  overflow: scroll; // This will give the box its own scrollbar.
  overflow: auto; // This detects the size of the content and creates a scrollbar if necessary.
}
```

You can see these principles in action over here:

<iframe width="100%" height="300" src="//jsfiddle.net/flatiron_school/sFfw5embedded/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

## Display

Now we need to consider how elements will display by default and how that
affects how we size and display them.

By default, certain elements display `inline`, which means these elements appear
side by side with other elements. They also can't have their own widths or
top/bottom margins. Elements like `span`, `a`, `img`, `input`, `em` and `strong`
are all inline elements.

Other elements come with a built-in `block` display. This means that they
display one after another, take up the entire width of the container (unless
specified otherwise), and they are allowed to have top/bottom margins. Block
elements include `div`, `p`, `h1`, `ol`, `ul` and `table`.

If you want to combine the two properties, there's the handy `inline-block`.
This will display elements side by side and allow for widths and top/bottom
margins as well.

We can also display elements with a value of `table` or `table-cell`. This
mimics the behavior of tables, and lets us place elements next to each other as
if they were cells in a table without writing a table in HTML. True to tables,
these display properties don't allow margins in between elements.

You can experiment with all of these properties, and see all their pros and cons
here:

<iframe width="100%" height="300" src="//jsfiddle.net/flatiron_school/352A6/1/embedded/" allowfullscreen="allowfullscreen" frameborder="0"></iframe>

## Conclusion

We introduced the principles of the box model and described how elements are
displayed in browsers. We covered the various properties we can use to change an
element's appearance, spacing or position in relation to other elements. We also
took a look at how content behaves inside of an element with the `overflow`
property and how we can further determine how an element behaves by changing its
`display` value. We're now prepared to dive deeper into how to arrange elements
on a page in layouts.

## Resources

* [Mozilla Developer Network: Box Model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Introduction_to_CSS/Box_model)
* [CSS Tricks: The CSS Box Model](https://css-tricks.com/the-css-box-model/)
* [Mozilla Developer Network: Box-Sizing](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing)
* [CSS Tricks: Box-Sizing](https://css-tricks.com/box-sizing/)
* [Video demonstration of the `display` property](https://www.youtube.com/embed/bKDs_FQkkEI)

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/Box-Model' title='Box Model'>Box Model</a> on Learn.co and start learning to code for free.</p>
