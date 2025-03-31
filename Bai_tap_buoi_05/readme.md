# Design System - UI Library & CSS Framework

## 1. Thiết lập dự án

### React + Vite
```sh
npm create vite@latest design-system --template react-ts
cd design-system
npm install
```

### Vue + Vite
```sh
npm create vite@latest design-system --template vue-ts
cd design-system
npm install
```

## 2. Cấu trúc thư mục
```
/design-system
│── /packages
│   ├── /ui (Thư viện UI components)
│   ├── /css (CSS Framework)
│   ├── /tokens (Design Tokens)
│── /apps
│   ├── /docs (Storybook hoặc Next.js document)
│── package.json
│── tsconfig.json
│── turbo.json (nếu dùng Turborepo)
```

## 3. Tạo UI Components

### Button Component (React + Tailwind)
```tsx
// /packages/ui/src/Button.tsx
import React from "react";

interface ButtonProps {
  children: React.ReactNode;
  variant?: "primary" | "secondary";
}

export const Button: React.FC<ButtonProps> = ({ children, variant = "primary" }) => {
  const className = variant === "primary" ? "bg-blue-500 text-white px-4 py-2 rounded" : "bg-gray-300 text-black px-4 py-2 rounded";
  return <button className={className}>{children}</button>;
};
```

### Button Component (Vue + Tailwind)
```vue
<!-- /packages/ui/src/Button.vue -->
<template>
  <button :class="buttonClass">
    <slot></slot>
  </button>
</template>

<script setup>
import { computed } from "vue";

const props = defineProps({
  variant: { type: String, default: "primary" },
});

const buttonClass = computed(() => 
  props.variant === "primary" ? "bg-blue-500 text-white px-4 py-2 rounded" : "bg-gray-300 text-black px-4 py-2 rounded"
);
</script>
```

## 4. Tích hợp Storybook

Cài đặt Storybook:
```sh
npx storybook init
```

Tạo file `Button.stories.tsx`:
```tsx
import { Button } from "../src/Button";

export default {
  title: "Components/Button",
  component: Button,
};

export const Primary = () => <Button variant="primary">Primary Button</Button>;
export const Secondary = () => <Button variant="secondary">Secondary Button</Button>;
```

Chạy Storybook:
```sh
npm run storybook
```

## 5. Xây dựng CSS Framework

### Design Tokens
```scss
// /packages/css/src/tokens.scss
$primary-color: #007bff;
$secondary-color: #6c757d;

$font-family: "Inter", sans-serif;
$font-size-base: 16px;
$line-height-base: 1.5;

$spacing-small: 8px;
$spacing-medium: 16px;
$spacing-large: 24px;
```

### Utility Classes
```scss
// /packages/css/src/grid.scss
.grid {
  display: grid;
  gap: var(--spacing-medium);
}

.grid-cols-2 {
  grid-template-columns: repeat(2, 1fr);
}

.grid-cols-3 {
  grid-template-columns: repeat(3, 1fr);
}
```

### Button Styles
```scss
// /