# Josh-CSS-Course-Exercises  
This repository contains my exercises for **Josh's CSS course**.

---

## Units in CSS  
A common question developers ask is:  
*"Which unit should I use and when?"*  

Here's how I approach it:  

- **Typography** → I generally use `rem`, because it has important **accessibility benefits**.  
- **Box model properties** *(padding, border, margin)* → I prefer using `px` because it’s **more intuitive** than `rem`, and there’s no significant accessibility advantage.  
- **Width/Height** → It depends on whether I want a fixed or relative size:  
  - A `div` that should **always be 250px wide** → Use `px`.  
  - A `div` that should **be 50% of the available space** → Use `%`.  
- **Color** → I prefer using `hsl`, as seen in the last lesson.  
- **`em`** → Reserved for rare cases when I want a property to scale **directly** with the font size.  

---

## CSS Specificity  
Specificity determines which styles take precedence when multiple rules apply to the same element.  

Here's the **specificity hierarchy**:  

1. **`!important`** → Highest priority *(even overrides inline styles)*  
2. **Inline styles (`style="..."`)** → Specificity: **1,000**  
3. **ID selectors (`#id`)** → Specificity: **100**  
4. **Class, Attribute, Pseudo-class (`.class`, `[type="text"]`, `:hover`)** → Specificity: **10**  
5. **Tag, Pseudo-element (`div`, `h1`, `::before`)** → Specificity: **1**  

---

## Logical Properties  
Logical properties make layouts more **flexible and adaptive** based on text direction and writing mode.  

### **Benefits of Using Logical Properties**  
- 🔹 **More responsive & international-friendly**  
- 🔹 **No need for separate RTL stylesheets**  
- 🔹 **Future-proof & works well with flexbox and grid**  

---

🎯 *This README is a work in progress as I continue learning!* 🚀  
