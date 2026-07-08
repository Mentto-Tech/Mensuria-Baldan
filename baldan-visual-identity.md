# Identidade Visual Baldan

Este documento descreve e fornece os tokens e diretrizes exatas da identidade visual da **Baldan (Máquinas e Implementos Agrícolas)** capturados do site oficial (https://baldan.com.br/).

---

## 🎨 Paleta de Cores

O sistema combina o vermelho industrial agrícola forte da Baldan com tons quentes de bege para fundo, cinza grafite profundo para leitura e cores claras de feedback.

### 1. Vermelhos da Marca (Primário)
*   **Vermelho Principal (600):** `rgb(203, 10, 38)` / `#CB0A26` (Ações primárias, links destacados e acentos visuais)
*   **Vermelho Escuro (700):** `rgb(175, 15, 42)` / `#AF0F2A` (Hover e detalhes escuros)
*   **Vermelho Claro (500):** `rgb(228, 13, 44)` / `#E40D2C`
*   **Vermelho Destaque (400):** `rgb(243, 23, 55)` / `#F31737`

### 2. Beges Quentes (Secundário e Fundos)
*   **Bege Claro (50):** `rgb(245, 237, 227)` / `#F5EDE3` (Cor de fundo premium da marca)
*   **Bege Médio (500):** `rgb(236, 227, 214)` / `#ECE3D6` (Fundo de cards e divisões de seção)
*   **Bege Escuro (700):** `rgb(232, 223, 209)` / `#E8DFD1`

### 3. Neutros e Cinzas
*   **Grafite (Gray 900):** `rgb(46, 46, 46)` / `#2E2E2E` (Texto principal e leitura)
*   **Cinza Médio (Gray 500):** `rgb(130, 130, 130)` / `#828282`
*   **Bordas (Gray 200):** `rgb(214, 214, 214)` / `#D6D6D6`
*   **Cinza Claro (Gray 50):** `rgb(248, 248, 248)` / `#F8F8F8` (Cabeçalho de tabelas e inputs)

### 4. Cores de Feedback
*   **Verde (Sucesso):** `rgb(4, 124, 72)` / `#047C48`
*   **Amarelo/Âmbar (Atenção):** `rgb(254, 200, 75)` / `#FEC84B`
*   **Azul (Info/Telemetria):** `rgb(10, 70, 234)` / `#0A46EA`

---

## 🔤 Tipografia e Fontes

*   **Fonte Principal (Sans-Serif):** `effra`, `ui-sans-serif`, `system-ui`, `sans-serif` (Moderna, limpa)
*   **Fonte Editorial/Títulos:** `freight-macro-pro`, `ui-serif`, `Georgia`, serif (Utilizada em itálico e negrito para títulos, transmitindo robustez e autoridade de engenharia agrícola)

```css
h1 i, h2 i, h3 i, h4 i, h5 i, h6 i {
  color: rgb(var(--color-primary-600) / 1);
  font-family: freight-macro-pro, Georgia, serif;
  font-weight: 700;
  font-style: italic;
}
```

---

## 📐 Layout, Formas e Estilos

### 1. Cortes Angulares (Canto Chanfrado)
Uma assinatura visual forte nos botões e containers do site da Baldan.
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

### 2. Efeito de Vidro (Glassmorphism)
Muito utilizado nos banners, sliders e pequenos painéis flutuantes sobre imagens:
```css
.glass-panel {
  background-color: rgba(255, 255, 255, 0.12);
  border: 1px solid rgba(255, 255, 255, 0.18);
  backdrop-filter: blur(8px);
  border-radius: 22px;
}
```

### 3. Sombras e Bordas
```css
:root {
  --shadow: 0 18px 44px rgba(15, 20, 22, 0.12);
  --shadow-soft: 0 10px 26px rgba(15, 20, 22, 0.08);
  --radius: 22px;
  --radius-sm: 14px;
}
```

---

## 💻 Implementação: Variáveis CSS

Para aplicar a identidade diretamente em seu projeto, defina as variáveis abaixo no `:root`:

```css
:root {
  /* Vermelhos Brand */
  --color-red-50: 255 241 243;
  --color-red-100: 255 223 228;
  --color-red-200: 255 155 169;
  --color-red-300: 255 97 120;
  --color-red-400: 243 23 55;
  --color-red-500: 228 13 44;
  --color-red-600: 203 10 38;  /* #CB0A26 (Vermelho Principal) */
  --color-red-700: 175 15 42;
  --color-red-800: 140 26 23;
  --color-red-900: 88 15 14;

  /* Beges Brand */
  --color-beige-50: 245 237 227; /* #F5EDE3 (Fundo principal) */
  --color-beige-100: 243 235 224;
  --color-beige-200: 241 233 221;
  --color-beige-300: 239 231 219;
  --color-beige-400: 237 229 216;
  --color-beige-500: 236 227 214;
  --color-beige-600: 234 225 211;
  --color-beige-700: 232 223 209;
  --color-beige-800: 230 220 206;
  --color-beige-900: 229 219 204;

  /* Neutros */
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

  /* Mapeamento de Uso Semântico */
  --color-primary-600: var(--color-red-600);
  --color-secondary-50: var(--color-beige-50);
  --color-secondary-500: var(--color-beige-500);

  /* Fontes */
  --font-family-sans: "effra", ui-sans-serif, system-ui, sans-serif;
  --font-family-serif: "freight-macro-pro", Georgia, serif;
}
```
