# Jusbrasil - Farol Design System

Instruções para construir interfaces Jusbrasil com o Farol Design System.
Para referências detalhadas de componentes, tokens e patterns, consulte `.sabor-farol/references/` se disponível.

## Stack

React + TypeScript + Tailwind CSS v4 + shadcn/ui + Lucide React (ícones fallback)
- Fonte: Inter (Google Fonts)
- Cores: CSS variables Farol mapeadas no Tailwind
- Componentes base: Radix UI (via shadcn)

## Regras Absolutas

### NUNCA use emojis
Emojis são PROIBIDOS em qualquer lugar da interface: headings, body text, botões, labels, badges, listas, cards, placeholders, tooltips, banners, trust badges. Use ícones SVG do set Farol ou Lucide React. Sem exceção.

### Acentuação OBRIGATÓRIA
Todo texto visível DEVE ter acentuação correta em português: á, é, í, ó, ú, â, ê, ô, ã, õ, ç, à. NUNCA gere "voce", "informacao", "juridico". HTML com charset UTF-8 e caracteres diretos.

### NUNCA use em-dash
Substitua "—" por "-" (hífen simples) sempre.

### Botões NUNCA são pill
Botões Farol usam `border-radius: 8px` (`rounded-lg`). NUNCA `border-radius: 100px`, `500px` ou `rounded-full`. Pill é exclusivo de ChipClickable (filtros).

### Botão primary: texto SEMPRE branco
`Button kind="primary"` = fundo `#007A5F` + texto `#FFFFFF`. NUNCA texto escuro sobre primary. Dark mode: fundo `#00A37F` + texto branco.

### Verde = interativo
Links, CTAs, estados ativos = verde (#007A5F). Evite azul (#0474E2) em elementos interativos.

### Links são verdes, não azuis
`color: var(--primary)` para links, nunca `color: var(--accent)`.

### Logo: NUNCA mude a cor via SVG
Logo usa `fill="currentColor"`. Cor vem do CSS `color` no container. Fundo claro: `color: var(--foreground)`. Fundo escuro: `color: white`.

### Fundo branco por padrão
`bg-background` (#FFF). Evite cinza como background de página inteira.

### Cards com borda fina
Cards usam `border border-border` (#CCD5E1), padding 24px, `border-radius: 16px`. Shadow só em hover/overlays.

### Ícones em cards: cor única
Todos os ícones de uma seção de feature cards devem ter mesmo fundo e cor.

## Cores

| Tailwind class | Light | Dark | Uso |
|---------------|-------|------|-----|
| `bg-background` / `text-foreground` | #FFF / #0F172A | #1B1C1E / #FFF | Base |
| `bg-card` / `text-card-foreground` | #FFF / #0F172A | #292B2E / #FFF | Cards |
| `bg-primary` / `text-primary-foreground` | #007A5F / #FFF | #00A37F / #FFF | Ação principal |
| `bg-secondary` / `text-secondary-foreground` | #7AB441 / #FFF | #8CC256 / #000 | Secundária |
| `bg-accent` / `text-accent-foreground` | #0474E2 / #FFF | #2390FB / #FFF | Destaque azul |
| `bg-destructive` / `text-destructive-foreground` | #E41E3F / #FFF | #E94964 / #FFF | Erro |
| `bg-muted` / `text-muted-foreground` | #F1F5F9 / #5C6F8A | #333538 / #AFB2B6 | Atenuado |
| `border-border` | #E2E8F0 | #333538 | Bordas |

Nunca hex hardcoded. Sempre CSS vars via Tailwind.

## Tipografia
- Fonte: Inter (base), Georgia (serif)
- Body mínimo: 16px, line-height 1.5
- Heading: font-bold (700), leading-tight (1.3)
- Labels/nav: font-semibold (600)

## Espaçamento
6xs=4px, 5xs=8px, 4xs=12px, 3xs=16px, 2xs=24px, xs=32px, sm=40px, md=48px, lg=56px, xl=64px, 2xl=80px

## Radius
xs=6px (inputs), sm=8px (botões), md=16px (cards), lg=24px (cards grandes), pill=500px (chips), circle=50%

## Sombras
```css
--shadow-1: 0px 2px 4px rgba(25,52,102,0.04);   /* hover */
--shadow-2: 0px 2px 8px rgba(25,52,102,0.08);   /* cards */
--shadow-3: 0px 4px 24px rgba(25,52,102,0.08);  /* dropdowns */
--shadow-4: 0px 8px 40px rgba(25,52,102,0.08);  /* modais */
--shadow-5: 0px 16px 56px rgba(25,52,102,0.08); /* overlays */
```

## Componentes Principais

### Ações
- **Button**: kind: primary/secondary/tertiary/plain/danger. size: xs(24px)/sm(36px)/md(44px)/lg(56px). Props: loading, disabled, leftIcon, rightIcon, block
- **IconButton**: label (obrigatório, tooltip+aria), kind, size, icon
- **Link**: type: primary/secondary/tertiary/ghost

### Feedback
- **Chip**: kind: secondary/tertiary/info/negative/warning/positive. Pill, não clicável
- **ChipClickable**: selected, chevron, leftIcon. Pill, interativo (filtros)
- **Banner**: type: info/positive/warning/critical/discovery. Inline persistente
- **Toast**: type: neutral/positive/negative/warning/info. Flutuante temporário
- **RichIcon**: icon, size (sm/md/lg), type (primary/positive/warning/negative/discovery)

### Overlays
- **Modal**: size: sm/md/lg/xl/full. Subcomps: Trigger, Content, Header, Body, Footer, Close
- **Alert/Confirm/Prompt**: Modais pré-construídos
- **Drawer**: placement: right/left/top/bottom
- **Dropdown/Popover/Tooltip/ContextMenu**

### Busca
- **Search**: type (primary/secondary), size (md/lg)
- **SearchAutocomplete**: Trigger + Menu, com histórico
- **Autocomplete**: dropdown de sugestões com filtro fuzzy

### Formulários
- **FormControl**: Label + Description + ErrorMessage
- **Input/Textarea/Select/Checkbox/Radio/Switch/Quantity**
- **CheckboxCard/RadioCard**: seleção visual com cards

### Grid (obrigatório para layout)
- **Container**: type: default(1280px) / letter(760px) / fluid(100%)
- **Row** + **Col**: grid 12 colunas, props xs/sm/md/lg/xl

### Layout
- **Card**: borda #CCD5E1, padding 24px, border-radius 16px
- **Snippet**: card rico de resultado de busca (14+ subcomps)
- **Tabs/Accordion/Breadcrumb/Pagination/Timeline/Carousel**
- **Detail/File/Avatar/Separator/Menu/IconList/TreeView/BookCover/Quote**

### Texto
- **Heading**: size: sm/md/lg/xl/2xl/3xl
- **BodyText**: size: md/lg
- **Caption/Subtitle/TruncateText/CollapseText/RichText**

### Marca
- **Brand**: logo Jusbrasil (onlySymbol, version: positive/negative)
- **BrandJusIa**: logo Jus IA
- **Illustration**: 60+ SVGs pré-feitos

### Chat
- **ChatMessage**: from: me/other, size: md/lg, loading

## Contexto de Produto

### Dois segmentos

| Segmento | Público | Produtos | Tom |
|----------|---------|----------|-----|
| Litigantes | Cidadãos leigos | Consulta Processual, Checagem de Terceiros, Seus Direitos | Empático, simples. "Entenda", "descubra" |
| Profissionais | Advogados, escritórios | Pesquisa Jurídica, Jus IA, Doutrina | Produtivo, técnico. "Pesquise", "fundamente" |

### Terminologia oficial
- "Consulta Processual" (nunca "busca de processos")
- "Jus IA" (nunca "JusIA", "Jus-IA", "Jus AI")
- "Peças Processuais" (nunca "documentos processuais")
- "Jurisprudência" (nunca "decisões" quando referindo ao acervo)

### Headlines oficiais
- Consulta Processual: "Estou em um processo, e agora?"
- Checagem de Terceiros: "Segurança para suas decisões"
- Seus Direitos: "Tire suas dúvidas jurídicas rapidamente"
- Pesquisa Jurídica: "Comece sua pesquisa jurídica no Jusbrasil"
- Jus IA: "Toda IA responde. O Jus IA entende o Direito."

### Dados de mercado
- Maior plataforma de informação jurídica do Brasil
- 1.2 bilhões de documentos jurídicos
- 100.000+ advogados usando Jus IA
- 1.900+ títulos de doutrina
- 4 milhões+ peças criadas com Jus IA

## Decisão Rápida de Componentes

| Situação | Componente |
|----------|-----------|
| Ação principal | Button kind="primary" |
| Ação secundária | Button kind="secondary" (borda cinza, texto verde) |
| Ação destrutiva | Button kind="danger" + Confirm |
| Status processo | Chip kind="positive"/"negative"/"warning" |
| Filtro interativo | ChipClickable (selected, chevron) |
| Aviso inline | Banner type="warning"/"info"/"critical" |
| Feedback de ação | Toast type="positive"/"negative" |
| Modal simples | Alert (ok) / Confirm (sim/não) / Prompt (input) |
| Painel lateral | Drawer placement="right" |
| Busca principal | SearchAutocomplete (Trigger + Menu) |
| Layout de página | Container + Row + Col |
| Card de busca SERP | Snippet |
| FAQ / colapsável | Accordion |
| Lista features | IconList com CheckIcon |
| Logo Jusbrasil | Brand |
| Logo Jus IA | BrandJusIa |

## Acessibilidade
- Touch targets mínimo 44x44px
- Focus rings: focus-visible:ring-2 focus-visible:ring-ring
- Contraste WCAG AA: 4.5:1 texto normal, 3:1 texto grande
- aria-label em botões icon-only
- Inputs com label associado via htmlFor/id

## Checklist
- Cores via CSS vars (sem hex hardcoded)
- Inter font, tamanhos do scale Farol
- Ícones SVG (sem emojis)
- Radius consistente (cards 16px, botões 8px, inputs 6px)
- Buttons com kind correto
- FormControl em todos os campos
- Responsivo: 375px, 768px, 1024px, 1280px
- Acentuação correta em todo texto
- Tom de voz adequado ao segmento
- Dados mock realistas (nomes BR, CPFs, CNJ, datas pt-BR)
