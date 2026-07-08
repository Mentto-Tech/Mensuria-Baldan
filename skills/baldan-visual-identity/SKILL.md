---
name: baldan-visual-identity
description: Guidelines and visual identity tokens (colors, fonts, shapes, and styles) captured from the official Baldan website (https://baldan.com.br/) for building premium interfaces.
---

# Identity & Visual Guidelines: Baldan

This skill file documents and provides the exact visual identity tokens of **Baldan (Máquinas e Implementos Agrícolas)** captured from their official platform. Use this file as a reference to design and implement premium interfaces that align perfectly with Baldan's official brand guidelines.

---

## 🎨 Color Palette

The color system combines a strong agricultural red with soft warm beige backgrounds, deep graphite grays, and precise feedback colors.

### 1. Brand Reds (Primary)
*   **Primary Red (600):** `rgb(203, 10, 38)` / `#CB0A26` (Used for primary actions, highlight elements, and brand accents)
*   **Red Dark (700):** `rgb(175, 15, 42)` / `#AF0F2A` (Hover states and dark brand elements)
*   **Red Light (500):** `rgb(228, 13, 44)` / `#E40D2C`
*   **Red Accent (400):** `rgb(243, 23, 55)` / `#F31737`

### 2. Warm Beiges (Secondary & Backgrounds)
*   **Beige Light (50):** `rgb(245, 237, 227)` / `#F5EDE3` (Primary background tone for premium/editorial look)
*   **Beige Medium (500):** `rgb(236, 227, 214)` / `#ECE3D6` (Card backgrounds and section separators)
*   **Beige Dark (700):** `rgb(232, 223, 209)` / `#E8DFD1`

### 3. Neutral Grays & Graphite
*   **Graphite/Text (Gray 900):** `rgb(46, 46, 46)` / `#2E2E2E` (Primary text color)
*   **Muted Text (Gray 500):** `rgb(130, 130, 130)` / `#828282`
*   **Border Gray (Gray 200):** `rgb(214, 214, 214)` / `#D6D6D6`
*   **Light Gray (Gray 50):** `rgb(248, 248, 248)` / `#F8F8F8` (Table headers or input backgrounds)

### 4. Semantic Feedback
*   **Green (Success):** `rgb(4, 124, 72)` / `#047C48`
*   **Amber (Warning):** `rgb(254, 200, 75)` / `#FEC84B`
*   **Blue (Info):** `rgb(10, 70, 234)` / `#0A46EA`

---

## 🔤 Typography & Fonts

*   **Primary Sans-Serif:** `effra`, `ui-sans-serif`, `system-ui`, `sans-serif` (Clean, corporate, modern)
*   **Editorial Serif / Headings:** `freight-macro-pro`, `ui-serif`, `Georgia` (Used specifically in bold italic styles for headings to project premium heritage and engineering authority)

```css
h1 i, h2 i, h3 i, h4 i, h5 i, h6 i {
  color: rgb(var(--color-primary-600) / 1);
  font-family: freight-macro-pro, Georgia, serif;
  font-weight: 700;
  font-style: italic;
}
```

---

## 📐 Layout, Shapes & Component Stylings

### 1. Chamfered/Angled Containers (Brand Signature)
Baldan's design system features beautiful polygon-clipped containers for cards, headers, and buttons.
```css
.baldan-angled-container {
  border-radius: 4px;
  clip-path: polygon(24px 0, 100% 0, 100% calc(100% - 24px), calc(100% - 24px) 100%, 0 100%, 0 24px);
}
@media (min-width: 1024px) {
  .baldan-angled-container {
    clip-path: polygon(32px 0, 100% 0, 100% calc(100% - 32px), calc(100% - 32px) 100%, 0 100%, 0 32px);
  }
}
```

### 2. Premium Shadows and Glassmorphism
*   **Glassmorphism Panels:** Used for sliders, quick controllers, and dashboard widgets.
    ```css
    .glass-panel {
      background-color: rgba(255, 255, 255, 0.12);
      border: 1px solid rgba(255, 255, 255, 0.18);
      backdrop-filter: blur(8px);
      border-radius: 22px;
    }
    ```
*   **Rich Shadows:**
    ```css
    :root {
      --shadow: 0 18px 44px rgba(15, 20, 22, 0.12);
      --shadow-soft: 0 10px 26px rgba(15, 20, 22, 0.08);
      --radius: 22px;
      --radius-sm: 14px;
    }
    ```

---

## 💻 Implementation: CSS Variables

Copy the code below directly into the `:root` of your CSS stylesheet:

```css
:root {
  /* Brand Reds */
  --color-red-50: 255 241 243;
  --color-red-100: 255 223 228;
  --color-red-200: 255 155 169;
  --color-red-300: 255 97 120;
  --color-red-400: 243 23 55;
  --color-red-500: 228 13 44;
  --color-red-600: 203 10 38;  /* #CB0A26 (Primary) */
  --color-red-700: 175 15 42;
  --color-red-800: 140 26 23;
  --color-red-900: 88 15 14;

  /* Warm Beiges */
  --color-beige-50: 245 237 227; /* #F5EDE3 (Background) */
  --color-beige-100: 243 235 224;
  --color-beige-200: 241 233 221;
  --color-beige-300: 239 231 219;
  --color-beige-400: 237 229 216;
  --color-beige-500: 236 227 214;
  --color-beige-600: 234 225 211;
  --color-beige-700: 232 223 209;
  --color-beige-800: 230 220 206;
  --color-beige-900: 229 219 204;

  /* Neutrals */
  --color-gray-50: 248 248 248;
  --color-gray-100: 242 242 242;
  --color-gray-200: 214 214 214;
  --color-gray-300: 204 204 204;
  --color-gray-400: 174 174 174;
  --color-gray-500: 130 130 130;
  --color-gray-600: 98 98 98;
  --color-gray-700: 74 74 74;
  --color-gray-800: 55 55 55;
  --color-gray-900: 46 46 46;

  /* Mappings */
  --color-primary-600: var(--color-red-600);
  --color-secondary-50: var(--color-beige-50);
  --color-secondary-500: var(--color-beige-500);

  /* Fonts & Shadows */
  --font-family-sans: "effra", ui-sans-serif, system-ui, sans-serif;
  --font-family-serif: "freight-macro-pro", Georgia, serif;
}
```

Use these design parameters to guarantee the consistency, high fidelity, and brand alignment of any system build for Baldan.
