# Farol DS — Setup de Projeto

## 1. Instalação das dependências

```bash
# React + TypeScript + Vite
npm create vite@latest meu-projeto -- --template react-ts

# OU Next.js
npx create-next-app@latest meu-projeto --typescript --tailwind --app

# Tailwind CSS v4
npm install tailwindcss@next @tailwindcss/vite@next

# shadcn/ui
npx shadcn@latest init

# Lucide (ícones fallback)
npm install lucide-react
```

## 2. CSS Principal — Farol DS com Tailwind v4

Substitua o conteúdo do seu `src/index.css` (ou `app/globals.css` no Next.js):

```css
@import "tailwindcss";
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');

@theme {
  /* Mapeia CSS vars Farol para classes Tailwind */
  --color-background: var(--background);
  --color-foreground: var(--foreground);
  --color-card: var(--card);
  --color-card-foreground: var(--card-foreground);
  --color-popover: var(--popover);
  --color-popover-foreground: var(--popover-foreground);
  --color-primary: var(--primary);
  --color-primary-foreground: var(--primary-foreground);
  --color-secondary: var(--secondary);
  --color-secondary-foreground: var(--secondary-foreground);
  --color-muted: var(--muted);
  --color-muted-foreground: var(--muted-foreground);
  --color-accent: var(--accent);
  --color-accent-foreground: var(--accent-foreground);
  --color-destructive: var(--destructive);
  --color-destructive-foreground: var(--destructive-foreground);
  --color-border: var(--border);
  --color-input: var(--input);
  --color-ring: var(--ring);

  --radius-lg: var(--radius);
  --radius-md: calc(var(--radius) - 2px);
  --radius-sm: calc(var(--radius) - 4px);

  --font-sans: "Inter", system-ui, -apple-system, sans-serif;
  --font-serif: Georgia, "Times New Roman", serif;
}

/* ── Farol DS Tokens — Light Mode ── */
:root {
  /* Base */
  --background: #FFFFFF;
  --foreground: #0F172A;

  /* Card */
  --card: #FFFFFF;
  --card-foreground: #0F172A;

  /* Popover */
  --popover: #FFFFFF;
  --popover-foreground: #0F172A;

  /* Brand Primary (verde) */
  --primary: #007A5F;
  --primary-foreground: #FFFFFF;

  /* Brand Secondary (verde claro) */
  --secondary: #7AB441;
  --secondary-foreground: #FFFFFF;

  /* Muted */
  --muted: #F1F5F9;
  --muted-foreground: #5C6F8A;

  /* Accent (azul) */
  --accent: #0474E2;
  --accent-foreground: #FFFFFF;

  /* Destructive (vermelho) */
  --destructive: #E41E3F;
  --destructive-foreground: #FFFFFF;

  /* Borders & Input */
  --border: #E2E8F0;
  --input: #E2E8F0;
  --ring: #007A5F;

  /* Radius base */
  --radius: 0.5rem;

  /* Farol Shadows */
  --shadow-1: 0px 2px 4px 0px rgba(25, 52, 102, 0.04);
  --shadow-2: 0px 2px 8px 0px rgba(25, 52, 102, 0.08);
  --shadow-3: 0px 4px 24px 0px rgba(25, 52, 102, 0.08);
  --shadow-4: 0px 8px 40px 0px rgba(25, 52, 102, 0.08);
  --shadow-5: 0px 16px 56px 0px rgba(25, 52, 102, 0.08);

  /* Farol Motion */
  --ease-productive: cubic-bezier(0, 0, 0.3, 1);
  --ease-expressive: cubic-bezier(0.4, 0.12, 0.4, 1);
}

/* ── Farol DS Tokens — Dark Mode ── */
.dark {
  --background: #1B1C1E;
  --foreground: #FFFFFF;

  --card: #292B2E;
  --card-foreground: #FFFFFF;

  --popover: #292B2E;
  --popover-foreground: #FFFFFF;

  --primary: #00A37F;
  --primary-foreground: #FFFFFF;

  --secondary: #8CC256;
  --secondary-foreground: #000000;

  --muted: #333538;
  --muted-foreground: #AFB2B6;

  --accent: #2390FB;
  --accent-foreground: #FFFFFF;

  --destructive: #E94964;
  --destructive-foreground: #FFFFFF;

  --border: #333538;
  --input: #333538;
  --ring: #00A37F;
}

/* ── Base Styles ── */
@layer base {
  * {
    border-color: var(--border);
    box-sizing: border-box;
  }

  body {
    background-color: var(--background);
    color: var(--foreground);
    font-family: var(--font-sans);
    font-size: 16px;
    line-height: 1.5;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  /* Focus rings acessíveis */
  :focus-visible {
    outline: 2px solid var(--ring);
    outline-offset: 2px;
  }
}
```

## 3. Classes Tailwind disponíveis

Com a configuração acima, use sempre estas classes (não hex):

```tsx
// Cores
bg-background      text-foreground
bg-card            text-card-foreground
bg-primary         text-primary-foreground
bg-secondary       text-secondary-foreground
bg-accent          text-accent-foreground
bg-destructive     text-destructive-foreground
bg-muted           text-muted-foreground
border-border
ring-ring

// Sombras (via style prop)
style={{ boxShadow: 'var(--shadow-1)' }}  // hover sutil
style={{ boxShadow: 'var(--shadow-2)' }}  // cards
style={{ boxShadow: 'var(--shadow-3)' }}  // dropdowns
style={{ boxShadow: 'var(--shadow-4)' }}  // modais
style={{ boxShadow: 'var(--shadow-5)' }}  // overlays

// Motion (via style prop)
style={{ transitionTimingFunction: 'var(--ease-productive)', transitionDuration: '160ms' }}
```

## 4. tailwind.config (v3 — legado)

Se o projeto usa Tailwind v3 ainda:

```js
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: ['./src/**/*.{ts,tsx}'],
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        background: 'var(--background)',
        foreground: 'var(--foreground)',
        card: { DEFAULT: 'var(--card)', foreground: 'var(--card-foreground)' },
        primary: { DEFAULT: 'var(--primary)', foreground: 'var(--primary-foreground)' },
        secondary: { DEFAULT: 'var(--secondary)', foreground: 'var(--secondary-foreground)' },
        muted: { DEFAULT: 'var(--muted)', foreground: 'var(--muted-foreground)' },
        accent: { DEFAULT: 'var(--accent)', foreground: 'var(--accent-foreground)' },
        destructive: { DEFAULT: 'var(--destructive)', foreground: 'var(--destructive-foreground)' },
        border: 'var(--border)',
        input: 'var(--input)',
        ring: 'var(--ring)',
      },
      borderRadius: {
        xs: '6px', sm: '8px', md: '16px', lg: '24px',
      },
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
        serif: ['Georgia', 'Times New Roman', 'serif'],
      },
    },
  },
  plugins: [],
}
```

## 5. Estrutura recomendada de projeto

```
src/
├── components/
│   ├── ui/           # Componentes base Farol (Button, Badge, Card, etc.)
│   ├── layout/       # Header, Sidebar, Layout wrappers
│   └── features/     # Componentes de domínio (ProcessCard, DocumentCard, etc.)
├── pages/ (ou app/)  # Páginas/rotas
├── hooks/            # Custom hooks
├── types/            # TypeScript interfaces
├── mocks/            # Dados mock para protótipos
└── index.css         # CSS com tokens Farol
```

## 6. Fonts no Next.js

```tsx
// app/layout.tsx
import { Inter } from 'next/font/google'

const inter = Inter({
  subsets: ['latin'],
  variable: '--font-sans',
  display: 'swap',
})

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="pt-BR" className={inter.variable}>
      <body>{children}</body>
    </html>
  )
}
```

## 7. Verificação rápida do setup

Após configurar, verifique que estas classes funcionam:

```tsx
// Teste em qualquer componente
<div className="p-8 bg-background">
  <div className="bg-card border border-border rounded-2xl p-6" style={{boxShadow: 'var(--shadow-2)'}}>
    <h1 className="text-2xl font-bold text-foreground">Jusbrasil</h1>
    <p className="text-muted-foreground mt-2">Farol DS configurado corretamente</p>
    <button className="mt-4 bg-primary text-primary-foreground px-4 py-2.5 rounded-lg font-semibold">
      Botão primário verde
    </button>
  </div>
</div>
```

Se o botão aparecer verde (#007A5F), o setup está correto.
