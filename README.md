# Josh-Css-Course-Exercises
This is my exercises for Josh's Css course


Units:
A common question I see from developers is "which unit should I use when?". Here's how I think about it:

For typography, I generally use rem, because it has important accessibility benefits.
When it comes to properties that relate to the box model — padding, border, margin — I usually use pixels. It's more intuitive than rem, and there isn't a clear accessibility win.
For width/height, it'll depend on whether I want the element to be a fixed size, or a relative size. I might want one div to always be 250px wide, while another one should be 50% of the available space.
For color, as we saw in the last lesson, I prefer hsl.
I reserve em for the rare cases when I want one property to scale directly with font size.


Css specificity:
!important → Highest priority (even overrides inline styles)
Inline styles (style="...") → Specificity: 1,000
ID selectors (#id) → Specificity: 100
Class, Attribute, Pseudo-class (.class, [type="text"], :hover) → Specificity: 10
Tag, Pseudo-element (div, h1, ::before) → Specificity: 1

Logical properties:
🔹 More responsive & international-friendly
🔹 No need for separate RTL stylesheets
🔹 Future-proof & works well with flexbox and grid