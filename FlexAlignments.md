### ✅ Flexbox Alignment in CSS

**Flexbox** (Flexible Box Layout) is a powerful layout model in CSS that makes aligning elements **easy and responsive**. Flexbox alignment can be controlled in **two directions**:

---

## 📐 Main Concepts

### 📏 1. **Main Axis** – Direction of the items (default: horizontal)

### 📏 2. **Cross Axis** – Perpendicular to main axis (default: vertical)

---

## 🎯 Flexbox Alignment Properties

### 🔹 1. `justify-content` – Aligns **items along the main axis**

| Value           | Description                                         |
| --------------- | --------------------------------------------------- |
| `flex-start`    | Align to the **start** of the main axis             |
| `flex-end`      | Align to the **end** of the main axis               |
| `center`        | Center items along the main axis                    |
| `space-between` | Evenly space items with **first and last at edges** |
| `space-around`  | Equal space around items                            |
| `space-evenly`  | Equal space **between** and **around** items        |

```css
.container {
  display: flex;
  justify-content: center;
}
```

---

### 🔹 2. `align-items` – Aligns **items along the cross axis**

| Value        | Description                                 |
| ------------ | ------------------------------------------- |
| `stretch`    | (default) Stretches items to fill container |
| `flex-start` | Align items to the **start** of cross axis  |
| `flex-end`   | Align items to the **end** of cross axis    |
| `center`     | Center items along cross axis               |
| `baseline`   | Align text baselines of items               |

```css
.container {
  display: flex;
  align-items: center;
}
```

---

### 🔹 3. `align-self` – Align **individual item** on cross axis (overrides `align-items`)

```css
.item {
  align-self: flex-end;
}
```

---

### 🔹 4. `align-content` – Aligns **multiple lines** on the cross axis (only works if items wrap)

| Value           | Description                         |
| --------------- | ----------------------------------- |
| `flex-start`    | Lines at the start of cross axis    |
| `flex-end`      | Lines at the end                    |
| `center`        | Lines in the center                 |
| `space-between` | Even space between lines            |
| `space-around`  | Even space with buffer around lines |
| `stretch`       | Stretch lines to fill container     |

```css
.container {
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
}
```

---

## 🧪 Example:

```css
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
```

```html
<div class="container">
  <div class="item">A</div>
  <div class="item">B</div>
  <div class="item">C</div>
</div>
```

---

Let me know if you want a visual diagram or codepen-style live preview.
