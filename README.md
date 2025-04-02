# CSS Course Exercises

This repository contains my exercises for **Josh's CSS course**.

---

## 📏 Units in CSS

A common question developers ask is:  
_"Which unit should I use and when?"_

Here's how I approach it:

- **Typography** → I generally use `rem`, because it has important **accessibility benefits**.
- **Box model properties** _(padding, border, margin)_ → I prefer using `px` because it’s **more intuitive** than `rem`, and there’s no significant accessibility advantage.
- **Width/Height** → It depends on whether I want a fixed or relative size:
  - A `div` that should **always be 250px wide** → Use `px`.
  - A `div` that should **be 50% of the available space** → Use `%`.
- **Color** → I prefer using `hsl`, as seen in the last lesson.
- **`em`** → Reserved for rare cases when I want a property to scale **directly** with the font size.

---

## 📦 Box Sizing

The `box-sizing` property in CSS controls how an element's total width and height are calculated.  
By default, `width` and `height` apply only to the content (`content-box`), but with `box-sizing: border-box`, padding and borders are included in the dimensions, making layout calculations easier.

```css
/* Default */
element {
  box-sizing: content-box;
}

/* Recommended */
element {
  box-sizing: border-box;
}
```

---

## ⚖️ CSS Specificity

Specificity determines which styles take precedence when multiple rules apply to the same element.

Here's the **specificity hierarchy**:

1. **`!important`** → Highest priority _(even overrides inline styles)_
2. **Inline styles (`style="..."`)** → Specificity: **1,000**
3. **ID selectors (`#id`)** → Specificity: **100**
4. **Class, Attribute, Pseudo-class (`.class`, `[type="text"]`, `:hover`)** → Specificity: **10**
5. **Tag, Pseudo-element (`div`, `h1`, `::before`)** → Specificity: **1**

---

## 🌍 Logical Properties

Logical properties make layouts more **flexible and adaptive** based on text direction and writing mode.

### **Benefits of Using Logical Properties**

- 🔹 **More responsive & international-friendly**
- 🔹 **No need for separate RTL stylesheets**
- 🔹 **Future-proof & works well with flexbox and grid**

---

## 🔍 CSS Fundamentals

- **Block elements** have a default width value of `auto`, not `100%`.
- **Margin collapse** is unique to Flow layout. If you have children inside a `display: flex` parent, those children's margins will never collapse.
- The **default value** of the `position` property is `static`.

### 📌 Absolute Centering Trick

To center an element absolutely, these four properties are crucial:

1. `position: absolute;`
2. Equal distances from each edge _(ideally `0px`)_
3. A fixed size _(defined `width` and `height` properties)_
4. Hungry margins _(e.g., `margin: auto;`)_

---

## 🎭 Stacking Context in CSS

The **stacking context** determines how elements are layered on top of each other based on their **z-index**, position, and other properties. It is created when an element has:

- A `z-index` value other than `auto` in a positioned element (`relative`, `absolute`, or `fixed`).
- `opacity` less than `1` (`opacity: 0.9` creates a new stacking context).
- `transform`, `filter`, `perspective`, `clip-path`, and certain other properties.
- **Setting opacity** to a value less than `1`.
- **Setting position** to `fixed` or `sticky` _(No `z-index` needed for these values!)_.
- **Applying a `mix-blend-mode`** other than `normal`.
- **Adding a `z-index`** to a child inside a `display: flex` or `display: grid` container.
- **Using `transform`, `filter`, `clip-path`, or `perspective`**.
- **Explicitly creating a context** with `isolation: isolate`.

Each stacking context is **self-contained**, meaning child elements can't be layered above elements outside their parent's stacking context.

---

### 🛑 `isolation: isolate;`

The `isolation: isolate;` property forces an element to create a new stacking context, preventing it from blending with elements outside of it. This is useful when dealing with `mix-blend-mode` or z-index issues in complex layouts.

```css
.element {
  isolation: isolate;
}
```

---

## 📌 Fixed Positioning and the `transform` Property

In general, `fixed` elements are positioned relative to the **viewport**. However, there's an important exception:

> If a **parent** or **grandparent** has the `transform` property applied, it becomes the containing block for the `fixed` element.
> This effectively turns the `fixed` element into an **absolutely positioned** element within that transformed parent.

---

## 🔄 Sticky Positioning & Common Issues

`position: sticky` allows an element to stick within its nearest scrollable ancestor, but it may not work due to:

- ❌ **Parent has `overflow: hidden | auto | scroll`** → Prevents sticking
- ❌ **Missing `top`, `bottom`, `left`, or `right`** → Sticky needs an offset
- ❌ **Ancestor has `height: 100vh` or fixed height** → Limits scroll range
- ❌ **Inside a `flex` or `grid` container** with `overflow: hidden` → Can clip sticky behavior
- ❌ **Parent has `position: relative` (in some cases)** → Affects sticky reference

---

### ✅ **How to Fix Sticky Issues**

✔ Ensure parents **don’t restrict overflow**
✔ Always set **`top`, `bottom`, `left`, or `right`**
✔ Avoid **fixed heights** on parents
✔ Be mindful of **`flex` and `grid` layouts**

---

## 👀 Visually Hidden Content

Use the `.visually-hidden` class to hide elements from visual display while keeping them accessible to screen readers.

### 📌 CSS Snippet:

```css
.visually-hidden {
  position: absolute;
  overflow: hidden;
  clip: rect(0 0 0 0);
  height: 1px;
  width: 1px;
  margin: -1px;
  padding: 0;
  border: 0;
}
```

---

### 📏 `flex-basis` vs. `width`

`flex-basis` and `width` control element sizes but behave differently in Flexbox:

| Property         | Behavior                                                                                                        |
| ---------------- | --------------------------------------------------------------------------------------------------------------- |
| **`flex-basis`** | Sets the initial size of a flex item before `flex-grow` and `flex-shrink` apply. Works only in flex containers. |
| **`width`**      | Sets a fixed size, unless overridden by `flex-basis`. Works in any layout.                                      |

### 🎯 **Why Use `flex-basis`?**

✅ More control in **flexbox layouts**
✅ Better **responsiveness**
✅ Overrides `width` in **flexbox**

### 📝 **Example**

```css
.container {
  display: flex;
}

.item {
  flex-basis: 200px; /* Initial size */
  flex-grow: 1; /* Expands if needed */
}

.item-fixed {
  width: 200px; /* Fixed size */
}
```

✔ Use `flex-basis` for **flexibility**
✔ Use `width` for **fixed sizing**

---

📏 Align Items: Stretch

By default, align-items: stretch; makes flex and grid items expand to fill their container’s height if not set.

---

## 📌 About This Important Meta Tag

```html
<meta name="viewport" content="width=device-width, initial-scale=1" />
```

width=device-width: Ensures the viewport width matches the device's width (e.g., 320px instead of 980px).

initial-scale=1: Starts at a 1x zoom level, preventing unwanted scaling.

This tag is crucial for making web pages responsive and ensuring a better mobile experience! 🚀

---

# 🌍 Access Localhost on Your Phone with Ngrok

## 📌 Steps

1️⃣ **Start Your Local Server** (e.g., Vite on port `5173`):

```sh
npm run dev
```

2️⃣ **Expose with Ngrok**:

```sh
ngrok http 5173
```

This gives a public URL like `https://random.ngrok.io`.

3️⃣ **Access on Your Phone**:

- Open the **ngrok URL** on your phone’s browser.

## ⚠️ Notes

- Use **HTTPS** to avoid browser blocks.
- Free version changes URLs per session.
- For a **fixed URL**, authenticate:
  ```sh
  ngrok authtoken YOUR_AUTH_TOKEN
  ```


---

# 🎨 CSS Variables & Media Queries

## 📌 Why Use CSS Variables?
Store reusable values with `--property-name` and `var()`.

### 🎯 Example:
```css
:root {
  --font-size: 16px;
}
@media (max-width: 600px) {
  :root {
    --font-size: 14px;
  }
}
p {
  font-size: var(--font-size);
}
```
✅ Less repetition ✅ Easy theme changes ✅ Better maintainability

---
