# Farol DS — Tokens Completos

## Cores

### Base (Neutros)

| Token | Light | Dark | CSS var / Tailwind |
|-------|-------|------|--------------------|
| base.low.pure | `#0F172A` | `#FFFFFF` | `text-foreground` |
| base.low.1 | `#2B3950` | `#EFF0F0` | |
| base.low.2 | `#455468` | `#CFD1D3` | |
| base.low.3 | `#5C6F8A` | `#AFB2B6` | `text-muted-foreground` |
| base.low.4 | `#788BA5` | `#979BA1` | |
| base.high.pure | `#FFFFFF` | `#1B1C1E` | `bg-background` |
| base.high.1 | `#F1F5F9` | `#292B2E` | `bg-muted` |
| base.high.2 | `#E2E8F0` | `#333538` | `border-border` / `bg-card` (dark) |
| base.high.3 | `#CCD5E1` | `#3F4246` | |
| base.high.4 | `#B3C0D0` | `#4B4E53` | |

### Brand

| Token | Light | Dark | CSS var / Tailwind |
|-------|-------|------|--------------------|
| brand.primary.pure | `#007A5F` | `#00A37F` | `bg-primary` / `text-primary` |
| brand.primary.1 | `#E6F4F0` | `#00291F` | hover bg leve em primary |
| brand.primary.2 | `#C9E9DF` | `#004233` | |
| brand.primary.3 | `#00664F` | `#00B88F` | hover em primary |
| brand.primary.4 | `#004D3B` | `#00E0AF` | active em primary |
| brand.secondary.pure | `#7AB441` | `#8CC256` | `bg-secondary` / `text-secondary` |
| brand.secondary.1 | `#F2F8EC` | `#293919` | |
| brand.secondary.2 | `#D9EBC6` | `#4B692B` | |
| brand.secondary.3 | `#719F41` | `#99C969` | |
| brand.secondary.4 | `#527231` | `#B5D991` | |
| brand.tertiary.pure | `#0474E2` | `#2390FB` | `bg-accent` / `text-accent` |
| brand.tertiary.1 | `#E7F5FD` | `#012950` | |
| brand.tertiary.2 | `#9BCDFF` | `#023B73` | |
| brand.tertiary.3 | `#0077C0` | `#4BA4FC` | |
| brand.tertiary.4 | `#005D95` | `#7ACAFF` | |

### Feedback

| Token | Light | Dark | Uso |
|-------|-------|------|-----|
| negative.pure | `#E41E3F` | `#E94964` | `bg-destructive` — erro, perigo |
| negative.1 | `#FEE2E3` | `#3A030C` | fundo de alerta de erro |
| positive.pure | `#98CC60` | `#98CC60` | sucesso |
| positive.1 | `#F3F8ED` | `#293C16` | fundo de alerta de sucesso |
| info.pure | `#0474E2` | `#379AFB` | informação |
| info.1 | `#EBF5FF` | `#012950` | fundo de alerta info |
| warning.pure | `#FBD94C` | `#FBD94B` | aviso |
| warning.1 | `#FEFAEC` | `#473A00` | fundo de alerta de aviso |
| visited | `#551A8B` | `#A666E1` | links visitados |

### CSS Variables (shadcn/Tailwind v4)

```css
/* Light */
--background: #FFFFFF;        --foreground: #0F172A;
--card: #FFFFFF;               --card-foreground: #0F172A;
--primary: #007A5F;            --primary-foreground: #FFFFFF;
--secondary: #7AB441;          --secondary-foreground: #FFFFFF;
--muted: #F1F5F9;              --muted-foreground: #5C6F8A;
--accent: #0474E2;             --accent-foreground: #FFFFFF;
--destructive: #E41E3F;        --destructive-foreground: #FFFFFF;
--border: #E2E8F0;             --input: #E2E8F0;
--ring: #007A5F;               --radius: 0.5rem;

/* Dark */
--background: #1B1C1E;        --foreground: #FFFFFF;
--card: #292B2E;               --card-foreground: #FFFFFF;
--primary: #00A37F;            --primary-foreground: #FFFFFF;
--secondary: #8CC256;          --secondary-foreground: #000000;
--muted: #333538;              --muted-foreground: #AFB2B6;
--accent: #2390FB;             --accent-foreground: #FFFFFF;
--destructive: #E94964;        --destructive-foreground: #FFFFFF;
--border: #333538;             --input: #333538;
--ring: #00A37F;
```

---

## Tipografia

| Token | Valor | Tailwind equivalente | Uso típico |
|-------|-------|---------------------|-----------|
| font.size.4xs | 10px | `text-[10px]` | Metadata muito pequena |
| font.size.3xs | 12px | `text-xs` | Caption, legenda |
| font.size.2xs | 14px | `text-sm` | Body small, labels |
| font.size.xs | 16px | `text-base` | Body padrão (mínimo) |
| font.size.sm | 18px | `text-lg` | Body large |
| font.size.md | 20px | `text-xl` | Subtítulo |
| font.size.lg | 24px | `text-2xl` | Heading pequeno |
| font.size.xl | 28px | `text-[28px]` | Heading médio |
| font.size.2xl | 32px | `text-[32px]` | Heading grande |
| font.size.3xl | 40px | `text-[40px]` | Display pequeno |
| font.size.4xl | 48px | `text-[48px]` | Display médio |
| font.size.5xl | 56px | `text-[56px]` | Display grande |
| font.size.6xl | 68px | `text-[68px]` | Hero display |

| Token | Valor | Tailwind |
|-------|-------|---------|
| font.weight.regular | 400 | `font-normal` |
| font.weight.semibold | 600 | `font-semibold` |
| font.weight.bold | 700 | `font-bold` |

| Token | Valor | Tailwind |
|-------|-------|---------|
| line.height.xs | 1 | `leading-none` |
| line.height.sm | 1.3 | `leading-tight` |
| line.height.md | 1.5 | `leading-normal` |
| line.height.lg | 1.7 | `leading-relaxed` |

| Token | Valor | Tailwind |
|-------|-------|---------|
| letter.spacing.sm | -0.4px | `tracking-tight` |
| letter.spacing.md | 0.4px | `tracking-wide` |

---

## Espaçamento

| Token | Valor | Tailwind aproximado | Uso |
|-------|-------|--------------------|----|
| spacing.6xs | 4px | `p-1` / `gap-1` | Ajuste fino |
| spacing.5xs | 8px | `p-2` / `gap-2` | Tight interno |
| spacing.4xs | 12px | `p-3` / `gap-3` | Padding tight |
| spacing.3xs | 16px | `p-4` / `gap-4` | Padding interno padrão |
| spacing.2xs | 24px | `p-6` / `gap-6` | Padding de componente |
| spacing.xs | 32px | `p-8` / `gap-8` | |
| spacing.sm | 40px | `p-10` / `gap-10` | Entre componentes |
| spacing.md | 48px | `p-12` / `gap-12` | Seção |
| spacing.lg | 56px | `p-14` / `gap-14` | |
| spacing.xl | 64px | `p-16` / `gap-16` | Seção maior |
| spacing.2xl | 80px | `p-20` / `gap-20` | Break de seção |
| spacing.3xl | 96px | `p-24` | |
| spacing.4xl | 120px | `p-[120px]` | |
| spacing.5xl | 160px | `p-[160px]` | |
| spacing.6xl | 200px | `p-[200px]` | Hero |

---

## Bordas

| Radius | Valor | Tailwind | Uso típico |
|--------|-------|---------|-----------|
| xs | 6px | `rounded-[6px]` | Inputs, badges, chips |
| sm | 8px | `rounded-lg` | Botões, tags |
| md | 16px | `rounded-2xl` | Cards, modais |
| lg | 24px | `rounded-3xl` | Cards grandes |
| pill | 500px | `rounded-full` | Pills, avatars com borda |
| circle | 50% | `rounded-full` | Avatars circulares |

| Width | Valor | Tailwind |
|-------|-------|---------|
| sm | 1px | `border` |
| md | 2px | `border-2` |
| lg | 4px | `border-4` |

---

## Sombras

```css
--shadow-1: 0px 2px 4px 0px rgba(25, 52, 102, 0.04);   /* hover sutil */
--shadow-2: 0px 2px 8px 0px rgba(25, 52, 102, 0.08);   /* cards */
--shadow-3: 0px 4px 24px 0px rgba(25, 52, 102, 0.08);  /* dropdowns */
--shadow-4: 0px 8px 40px 0px rgba(25, 52, 102, 0.08);  /* modais */
--shadow-5: 0px 16px 56px 0px rgba(25, 52, 102, 0.08); /* overlays */
```

Uso inline: `style={{ boxShadow: 'var(--shadow-2)' }}`

---

## Motion

| Token | Valor | Uso |
|-------|-------|-----|
| duration.fast.1 | 80ms | Feedback imediato (toggle) |
| duration.fast.2 | 160ms | Micro-interações (hover) |
| duration.medium.1 | 240ms | Entrada de elementos |
| duration.medium.2 | 320ms | Saída de elementos |
| duration.slow.1 | 480ms | Transições de página |
| duration.slow.2 | 720ms | Animações expressivas |

| Easing | Valor | Uso |
|--------|-------|-----|
| productive | `cubic-bezier(0, 0, 0.3, 1)` | UI funcional (hover, focus) |
| expressive | `cubic-bezier(0.4, 0.12, 0.4, 1)` | Entrada de overlays |
| loop | `cubic-bezier(0, 0, 1, 1)` | Spinners, loops |

```css
/* Tailwind custom em globals.css */
--ease-productive: cubic-bezier(0, 0, 0.3, 1);
--ease-expressive: cubic-bezier(0.4, 0.12, 0.4, 1);
```

---

## Breakpoints

| Token | Valor | Tailwind prefix |
|-------|-------|----------------|
| xs | 0px | (base) |
| sm | 600px | `sm:` |
| md | 960px | `md:` |
| lg | 1280px | `lg:` |
| xl | 1920px | `xl:` |

---

## Opacidade

| Token | Valor | Uso |
|-------|-------|-----|
| opacity.1 | 0.8 | Levemente transparente |
| opacity.2 | 0.64 | Disabled states |
| opacity.3 | 0.32 | Muito transparente |
| opacity.4 | 0.16 | Overlay sutil |
| opacity.5 | 0.08 | Hover highlight |
