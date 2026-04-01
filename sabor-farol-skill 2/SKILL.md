---
name: sabor-farol
description: "Design system e front-end Jusbrasil com Farol DS. Use esta skill SEMPRE que precisar construir, implementar, revisar ou melhorar qualquer UI para produtos Jusbrasil — landing pages, páginas de busca (SERP), telas de detalhe (processo, doutrina, artigo, modelo jurídico), dashboards, formulários, diretórios, chatbots, newsletters, ferramentas internas. Ativa também quando o usuário mencionar: Farol, Jus IA, Seus Direitos, Jus News, diretório de advogados, protótipo, componente Jusbrasil, design system verde, Farol DS, tokens Farol, botão primário Jusbrasil, qualquer página de produto Jusbrasil. Stack: React + TypeScript + Tailwind CSS v4. Design System: Farol DS (verde #007A5F, Inter, Radix UI)."
---

# sabor-farol — Skill de Protótipos Jusbrasil com Farol DS

Skill completa para construir interfaces Jusbrasil do zero com o Farol Design System. Cobre desde setup até páginas completas.

## Arquivos de Referência

| Arquivo | Quando ler |
|---------|-----------|
| `products.md` | **Ler primeiro** - Produtos, personas, tom de voz, terminologia oficial |
| `tokens.md` | Cores, tipografia, espaçamento, sombras, motion |
| `components.md` | Todos os componentes com props e exemplos |
| `patterns.md` | Templates de página, padrões de layout, padrões jurídicos |
| `icons.md` | Biblioteca de ícones Farol |
| `setup.md` | CSS vars + Tailwind v4 + shadcn config |
| `logos.md` | SVGs oficiais do Jusbrasil e Jus IA prontos para uso |
| `blocks.md` | Catalogo de 13 blocos HTML visuais - topbar, sidebar, chat, SERP, cards, FAQ, footer, pricing, widgets, empty states, banners, timeline |
| `mocks.md` | Dados mock realistas para prototipos (nomes, CPFs, processos, tribunais) |

---

## Princípios Visuais Jusbrasil (aprendidos do produto real)

### Regras absolutas de visual

| Regra | Como aplicar |
|-------|-------------|
| **NUNCA use emojis** | Emojis são PROIBIDOS em qualquer lugar da interface: headings, body text, botões, labels, badges, listas, cards, placeholders, tooltips, banners, trust badges - NENHUM emoji em nenhum contexto. Use ícones SVG do set Farol ou Lucide React para representação visual. Isso vale para todo conteúdo gerado: HTML, componentes React, dados mock, copy de landing page, tudo. Sem exceção. |
| **Acentuação OBRIGATÓRIA em todo conteúdo** | Todo texto visível ao usuário DEVE ter acentuação correta em português: á, é, í, ó, ú, â, ê, ô, ã, õ, ç, à. NUNCA gere conteúdo sem acentos ("voce" em vez de "você", "informacao" em vez de "informação", "juridico" em vez de "jurídico"). Em HTML, use charset UTF-8 (`<meta charset="UTF-8">`) e escreva os caracteres diretamente - não use entidades HTML. Isso vale para headings, body text, botões, labels, placeholders, alt texts, titles - TUDO. |
| **NUNCA use o caractere "—"** | Substitua sempre por "-" (hífen simples). O em-dash quebra a consistência tipográfica dos produtos Jusbrasil. |
| **Fundo branco por padrão** | `bg-background` (#FFF) na esmagadora maioria das páginas. Evite cinza (#F8FAFC) como background de página inteira. |
| **Evite azul como cor de UI** | O `--accent` (#0474E2) existe mas o produto real quase não o usa em elementos interativos. Links e CTAs são **verdes** (#007A5F). |
| **Verde = interativo** | Links de texto, CTAs, estados ativos, badges de destaque — tudo verde. |
| **Gradientes só em promoções** | Seções de feature do Jus IA usam gradiente verde suave (white → `#F2F8EC`). Nunca em páginas funcionais. |
| **Tipografia escura e pesada** | Headings grandes em `#0F172A` (`text-foreground`), `font-bold`. Muito espaço branco ao redor. |
| **Cards com borda fina** | Cards usam `border border-border` sem shadow excessiva. Shadow só em hover ou overlays. |
| **Links são verdes, não azuis** | `color: var(--primary)` para links, nunca `color: var(--accent)`. Visited usa `#551A8B` (padrão do browser). |
| **Botões NUNCA são pill** | Botões Farol usam `rounded-lg` = `border-radius: 8px`. NUNCA use `border-radius: 100px`, `500px` ou `rounded-full` em `<button>` ou `<a>` funcionando como botão. Formato pill é exclusivo de **ChipClickable** (filtros, seletores de busca). Ao criar qualquer CTA, botão de ação, link-botão ou "Iniciar conversa" - sempre `border-radius: 8px`. |
| **Botão primary: texto SEMPRE branco** | `Button kind="primary"` = fundo `#007A5F` + texto `#FFFFFF`. NUNCA use `color: currentColor`, `color: inherit` ou texto escuro sobre fundo green primary. O contraste verde escuro + texto escuro é ilegivel. Em dark mode: fundo `#00A37F` + texto branco tambem. Esta regra vale para TODOS os botões primary, inclusive em heroes dark, CTAs de landing page, etc. Se o botão tem `background-color: #007A5F` ou `var(--primary)`, o texto TEM que ser branco. |
| **Ícones em cards: cor única** | Quando uma seção tem vários feature cards, todos os ícones devem ter o mesmo fundo (`--primary-1`) e mesma cor (`--primary`). Variar cores entre cards da mesma seção deixa a UI poluída e inconsistente. |
| **Sem badges informativos no nav** | Não adicione chips, tags ou badges ("Novo", "Beta") nos itens de navegação. O nav deve ser limpo e só texto. |
| **Logo: NUNCA mude a cor via SVG** | O texto do logo usa `fill="currentColor"`. A cor vem do CSS `color` no `<a>` container. Fundo claro: `color: var(--foreground)`. Fundo escuro: `color: white`. Nunca use `fill="white"`, `fill="blue"` ou `filter` no SVG. Se esquecer de setar `color` no container, o browser aplica azul de link — logo fica azul. |
| **Logo Jusbrasil: use o SVG correto** | O SVG oficial tem `fill-rule="evenodd"` no path do wordmark + 3 circles coloridos: amarelo `#FFCE00`, azul `#378CC8`, verde `#7AB441`. Use sempre este SVG — nunca reimplemente paths customizados do zero. Veja `logos.md`. |
| **Chatbot/Jus IA: sidebar clara** | A sidebar do chat do Jus IA é **branca** com borda direita — não dark/escura. Mensagens do usuário: bolhas cinzas alinhadas à direita sem avatar. Respostas da IA: label "Resposta" em verde, depois texto limpo, depois icones de acao. Input: bordas arredondadas, placeholder "Faca uma pergunta...", chip "Pesquisa fundamentada", botoes mic + send. |
| **Widget de lista de documentos** | Itens de documento/modelo relacionado usam: borda em volta de toda a lista, cada item com ícone colorido em fundo tintado (verde/azul/laranja), nome + meta, botao download alinhado à direita. Nao use thumbnails/miniatura de documento. |

### Princípios de produto

| Princípio | O que significa na prática |
|-----------|---------------------------|
| **Clareza** | Labels claros, iconografia consistente, layouts previsíveis. Usuário sempre sabe onde está e o que pode fazer |
| **Eficiência** | Minimize cliques e passos. Use defaults inteligentes. Agrupe ações relacionadas |
| **Consistência** | Reutilize componentes e tokens. Mesmos problemas → mesmas soluções |
| **Beleza** | Alinhamento, espaço branco e hierarquia visual. Interfaces que transmitem confiança |

---

## Contexto de Produto (Quick Reference)

Leia `products.md` para detalhes completos de cada produto, personas e tom de voz.

### Dois segmentos, duas linguagens

| Segmento | Público | Produtos | Tom de voz |
|----------|---------|----------|------------|
| **Litigantes** | Cidadãos leigos envolvidos em processos | Consulta Processual, Checagem de Terceiros, Seus Direitos, Monitoramento de CPF | Empático, acolhedor, linguagem simples. "Entenda", "descubra", "acompanhe" |
| **Profissionais do Direito** | Advogados, escritórios, dept. jurídicos | Pesquisa Jurídica, Jus IA, Doutrina, Research Lab | Produtivo, profissional, técnico. "Pesquise", "fundamente", "verifique" |

### Regras de conteúdo

| Regra | Detalhe |
|-------|---------|
| **Identifique o segmento antes de escrever** | O tom e vocabulário mudam completamente entre litigantes e profissionais. Pergunte ou deduza do contexto |
| **Use a terminologia oficial** | "Consulta Processual" (nunca "busca de processos"), "Jus IA" (nunca "JusIA" ou "Jus AI"), "Peças Processuais" (nunca "documentos processuais") |
| **Copy real do produto** | Use os headlines e CTAs oficiais como referência. Ex: "Toda IA responde. O Jus IA entende o Direito." |
| **Trust signals com números** | "100.000+ advogados", "1.2 bilhões de documentos", "1.900+ títulos de doutrina" |
| **Dados mock realistas** | Nomes brasileiros reais, CPFs formatados (XXX.XXX.XXX-XX), processos com número CNJ, datas em pt-BR, tribunais reais (TJ-SP, TRF-3, STJ) |

### Headlines por produto (referência)

| Produto | Headline oficial |
|---------|-----------------|
| Consulta Processual | "Estou em um processo, e agora?" |
| Checagem de Terceiros | "Segurança para suas decisões" |
| Seus Direitos | "Tire suas dúvidas jurídicas rapidamente" |
| Pesquisa Jurídica | "Comece sua pesquisa jurídica no Jusbrasil" |
| Jus IA | "Toda IA responde. O Jus IA entende o Direito." |
| Research Lab | "Delegue suas pesquisas jurídicas para nós" |

---

## Stack Padrão

```
React + TypeScript + Tailwind CSS v4 + shadcn/ui + Lucide React (ícones fallback)
```

- **Fonte**: Inter (via Google Fonts)
- **Ícones**: Farol icon set → fallback Lucide React
- **Cores**: CSS variables Farol (`--primary`, `--foreground`, etc.) mapeadas no Tailwind
- **Componentes base**: Radix UI (via shadcn) para acessibilidade

Para setup completo de um projeto novo, leia `setup.md`.

---

## Cores Essenciais (Quick Reference)

Leia `tokens.md` para tabela completa.

| Tailwind class | Light | Dark | Uso |
|---------------|-------|------|-----|
| `bg-background` / `text-foreground` | `#FFF` / `#0F172A` | `#1B1C1E` / `#FFF` | Base da página |
| `bg-card` / `text-card-foreground` | `#FFF` / `#0F172A` | `#292B2E` / `#FFF` | Cards e painéis |
| `bg-primary` / `text-primary-foreground` | `#007A5F` / `#FFF` | `#00A37F` / `#FFF` | Ação principal |
| `bg-secondary` / `text-secondary-foreground` | `#7AB441` / `#FFF` | `#8CC256` / `#000` | Ação secundária |
| `bg-accent` / `text-accent-foreground` | `#0474E2` / `#FFF` | `#2390FB` / `#FFF` | Destaque / azul |
| `bg-destructive` / `text-destructive-foreground` | `#E41E3F` / `#FFF` | `#E94964` / `#FFF` | Erro / perigo |
| `bg-muted` / `text-muted-foreground` | `#F1F5F9` / `#5C6F8A` | `#333538` / `#AFB2B6` | Fundo atenuado / texto secundário |
| `border-border` | `#E2E8F0` | `#333538` | Bordas |

**Regra de ouro: nunca use hex hardcoded. Sempre CSS vars via Tailwind.**

---

## Tokens Rápidos

### Tipografia
- Fonte: **Inter** (base), Georgia (serif/variant)
- Body mínimo: `text-base` = 16px, line-height 1.5
- Heading: `font-bold` (700), headings usam `leading-tight` (1.3)
- Labels/nav: `font-semibold` (600)

### Espaçamento (t-shirt scale → px)
`6xs`=4 · `5xs`=8 · `4xs`=12 · `3xs`=16 · `2xs`=24 · `xs`=32 · `sm`=40 · `md`=48 · `lg`=56 · `xl`=64 · `2xl`=80

### Radius
`xs`=6px · `sm`=8px · `md`=16px · `lg`=24px · `pill`=500px · `circle`=50%

### Sombras (profundidade crescente)
- `shadow-1` → hover sutil
- `shadow-2` → cards
- `shadow-3` → dropdowns / popovers
- `shadow-4` → modais / drawers
- `shadow-5` → tooltips / overlays

### Motion
- Micro-interações: `duration-[160ms]` (fast.2), `ease-[cubic-bezier(0,0,0.3,1)]` (productive)
- Animações de entrada: `duration-[240ms]` (medium.1), `ease-[cubic-bezier(0.4,0.12,0.4,1)]` (expressive)

---

## Componentes Disponíveis (Quick Reference)

Leia `components.md` para props completas e exemplos.

### Ações
| Componente | Variantes chave |
|------------|-----------------|
| **Button** | `kind`: primary, secondary, tertiary, plain, danger, dangerSecondary · `size`: xs/sm/md/lg · `loading`, `disabled`, `leftIcon`, `rightIcon`, `block` |
| **IconButton** | `label` (obrigatorio, tooltip+aria), `kind`, `size`, `icon` · somente icone |
| **Link** | `type`: primary, secondary, tertiary, ghost · `asChild` |

### Feedback & Status
| Componente | Variantes chave |
|------------|-----------------|
| **Badge** | `type`: primary/secondary/tertiary · `variant`: label/dot · `overlap`: circular/rectangular |
| **Chip** | `kind`: secondary/tertiary/info/negative/warning/positive · `size`: sm(24px)/md(32px) · pill, nao clicavel |
| **ChipClickable** | `selected`, `chevron`, `leftIcon` · `size`: sm/md/lg · pill, interativo (filtros, tabs) |
| **ChipRemovable** | `leftIcon`, `onRemove`, `disabled` · tag removivel com X |
| **RichIcon** | `icon`, `size` (sm/md/lg), `type` (primary/positive/warning/negative/discovery) · icone com fundo semantico |
| **Banner** | `type`: info/positive/warning/critical/discovery · `level`: standard/app · inline persistente |
| **Toast** | `type`: neutral/positive/negative/warning/info · `duration` · flutuante temporario |
| **Spinner** | `size`: xs→3xl · `label` (a11y) |
| **Skeleton** | `width`, `height`, `radius` |
| **ProgressLoader** | `placement` (top/bottom), `visible` · barra de loading de pagina |

### Overlays & Modais
| Componente | Variantes chave |
|------------|-----------------|
| **Modal** | `size`: sm/md/lg/xl/full · Trigger + Content + Header + Body + Footer + Close |
| **Alert** | Modal pre-construido: `title`, `description`, `confirmLabel` · notificacao simples |
| **Confirm** | Modal pre-construido: `title`, `danger`, `confirmLabel`, `cancelLabel` · escolha binaria |
| **Prompt** | Modal pre-construido: `title`, `inputPlaceholder`, `onConfirm(value)` · captura de input |
| **Drawer** | `placement`: right/left/top/bottom · `size`: sm→full |
| **Dropdown** | Trigger + Menu + MenuItem + MenuCheckboxItem + MenuSeparator |
| **ContextMenu** | Root + Trigger + Content + Item (com `leftIcon`) · clique direito |
| **Popover** | Trigger + Content + Close |
| **Tooltip** | `label`, `placement`: top/right/bottom/left |

### Busca
| Componente | Variantes chave |
|------------|-----------------|
| **Search** | `type` (primary/secondary), `size` (md/lg), `onSearch`, `loading` · campo de busca |
| **SearchAutocomplete** | `type`, `size` · Trigger + Menu · busca com autocomplete + historico |
| **Autocomplete** | Root + Trigger + Menu · dropdown de sugestoes com filtro fuzzy |

### Formularios
| Componente | Variantes chave |
|------------|-----------------|
| **FormControl** | `id`, `required`, `error`, `disabled` · Label + Description + ErrorMessage |
| **Input** | `type`, `error`, `loading`, `rightIcon` · password toggle auto |
| **Textarea** | `error`, `onValueChange` |
| **Select** | `value`, `onValueChange`, `placeholder` · Select.Item |
| **Checkbox** | `checked`/`indeterminate` · Group + Item + Name + Description |
| **CheckboxCard** | `orientation` (h/v), `controlHidden` · Icon + Content + Title + Description |
| **Radio** | `value`, `disabled` · Group + Item + Indicator + Name + Description |
| **RadioCard** | `value`, `orientation`, `controlHidden` · Group + Icon + Content + Title + Description |
| **Switch** | `checked`, `disabled`, `loading`, `size`: sm/md |
| **Quantity** | `value`, `minValue`, `maxValue`, `onValueChange` · input numerico +/- |

### Grid (usar sempre para layout de pagina)
| Componente | Variantes chave |
|------------|-----------------|
| **Container** | `type`: default (1280px) / letter (760px, leitura) / fluid (100%) |
| **Row** | wrapper de colunas - filhos devem ser `Col` |
| **Col** | `xs`/`sm`/`md`/`lg`/`xl`: 0-12 · grid 12 colunas |

### Layout & Conteudo
| Componente | Variantes chave |
|------------|-----------------|
| **Card** | `highlight`, `disabled`, `disablePadding`, `onClick` · borda `#CCD5E1`, padding 24px |
| **Snippet** | 14+ subcomps: Container, Cover, Body, Content, Caption, Tags, Title, Header, Tail, Footnote · card rico de resultado de busca |
| **Detail** | `inline` · Icon + Label + Value · display chave-valor |
| **File** | `variant` (neutral/pdf/doc), `selected`, `loading`, `error` · card de documento/download |
| **Tabs** | `value`, `activationMode` · List + Trigger + Content |
| **Avatar** | `size`: xs→3xl · `alt`, `color` |
| **Breadcrumb** | HomeItem + Item (min. 3 itens) |
| **Pagination** | `count`, `page`, `onPageChange` · Item + Button subcomponents |
| **PaginationSimple** | `count`, `page` · apenas prev/next sem numeros |
| **Separator** | `orientation`: horizontal/vertical · `decorative` |
| **Menu** | `orientation`: vertical/horizontal |
| **Accordion** | Item + Header + Title + Content + Text + Icon · `type`: single/multiple |
| **IconList** | `Item` com `icon` prop - listas de beneficios/features |
| **Information** | `label` (tooltip hover), `size` (xs/sm), `placement` |
| **Timeline** | `size` (sm/md), `endless` · Item com `icon`, `highlighted` · cronologia/etapas |
| **TreeView** | List + Item + Checkbox + Link · `defaultExpanded`, `onSelectedChange` · hierarquia |
| **Carousel** | Root + List + Item + Pagination · slider com scroll snap |
| **BookCover** | `size` (xs/sm/md/lg/5xl) · wrapper de capa de livro/revista |
| **Quote** | Cite · blockquote semantico com atribuicao |

### Texto & Conteudo
| Componente | Variantes chave |
|------------|-----------------|
| **Heading** | `size`: sm/md/lg/xl/2xl/3xl · `asChild` |
| **Subtitle** | texto de apoio ao heading |
| **BodyText** | `size`: md/lg · texto corpo |
| **Caption** | texto pequeno/metadata |
| **PrimitiveText** | texto base sem semantica |
| **TruncateText** | `value` (linhas ou array responsivo), `fade` · truncamento com line-clamp |
| **CollapseText** | extends TruncateText + "Ler mais/menos" automatico |
| **RichText** | wrapper CSS para HTML rico (editor, CMS, markdown) |

### Expandir/Colapsar
| Componente | Variantes chave |
|------------|-----------------|
| **Collapse** | `open`, `defaultOpen` · Content · secao colapsavel |
| **CollapseControl** | extends Button + `open`, `showMoreLabel`, `showLessLabel` · botao "Mostrar mais" |
| **CollapseText** | extends TruncateText · "Ler mais" automatico com deteccao de truncamento |

### Marca
| Componente | Variantes chave |
|------------|-----------------|
| **Brand** | `onlySymbol`, `version` (positive/negative) · logo Jusbrasil oficial |
| **BrandJusIa** | `onlySymbol`, `version` (positive/negative) · logo Jus IA oficial |
| **Illustration** | `size` (sm/md/lg) · 60+ ilustracoes SVG pre-feitas (empty states, sucesso, etc.) |

---

## Fluxo de Trabalho para Novos Protótipos

### 0. Identifique o segmento e produto
Antes de qualquer coisa, determine:
- **Segmento**: Litigantes (pessoa leiga) ou Profissionais do Direito?
- **Produto**: Consulta Processual? Jus IA? Pesquisa Jurídica? Seus Direitos?
- Leia `products.md` para tom de voz, copy oficial e terminologia

### 1. Identifique o tipo de página
Leia `patterns.md` para templates prontos:
- **Dashboard** — métricas + tabelas + filtros
- **Listagem** — resultados de busca, processos, documentos
- **Detalhe** — processo, documento, perfil
- **Formulário** — cadastro, edição, upload
- **Autenticação** — login, cadastro, recuperação de senha
- **Landing/Institucional** — apresentação de produto

### 2. Defina layout e grid
- **Use sempre `Container` + `Row` + `Col`** para layout de página — é o padrão do produto
- `Container type="default"` (max 1280px) · `type="letter"` (max 760px, conteúdo de leitura) · `type="fluid"` (full-width)
- Colunas: `<Col xs={12} md={6}>` — mobile-first, breakpoints `xs`/`sm`/`md`/`lg`/`xl`
- Sidebar fixa: `w-64` (256px) + conteúdo `flex-1` (fora do grid, layout estático)
- Header: `h-16` (64px) + `sticky top-0 z-50`
- Breakpoints: mobile-first (xs → sm 600px → md 960px → lg 1280px)

### 3. Aplique os tokens
- Cores via CSS vars: `bg-primary`, `text-foreground`, etc.
- Nunca hex hardcoded
- Sombras via CSS custom properties: `var(--shadow-2)`

### 4. Use componentes Farol
- Prefira sempre componentes Farol sobre implementações custom
- Botões: sempre com `kind` correto, `loading` em operações async
- Formulários: sempre com `FormControl` wrapping e `ErrorMessage`
- Loading states: `Skeleton` para conteúdo estruturado, `Spinner` para ações

### 5. Ícones
- Primário: ícones Farol (leia `icons.md`)
- Fallback: Lucide React (mesmo estilo outline)
- Sempre `aria-hidden="true"` em ícones decorativos
- Nunca emojis como ícones

### 6. Verifique o checklist antes de entregar

---

## Decisao Rapida de Componentes

| Situacao | Componente certo |
|----------|-----------------|
| **Acoes** | |
| Acao principal da tela | `Button kind="primary"` |
| Cancelar / acao secundaria | `Button kind="secondary"` (borda cinza, texto verde) |
| Acao de baixa enfase | `Button kind="tertiary"` (borda cinza, texto escuro) |
| Link de acao em texto | `Button kind="plain"` ou `Link type="primary"` |
| Acao destrutiva | `Button kind="danger"` + confirmacao via `Confirm` |
| Botao somente icone | `IconButton` (label obrigatorio para acessibilidade) |
| Menu de clique direito | `ContextMenu` |
| **Status & Feedback** | |
| Status de processo/documento | `Chip kind="positive"/"negative"/"warning"` |
| Status legado / notificacao | `Badge type="primary"` (ativo) / `type="tertiary"` (inativo) |
| Filtro / selecao compacta | `ChipClickable` (com `selected` e `chevron`) |
| Filtro ativo removivel | `ChipRemovable` (com `onRemove`) |
| Icone com fundo semantico (feature card) | `RichIcon` (type: primary/positive/warning/negative/discovery) |
| Aviso inline persistente | `Banner type="warning"/"info"/"critical"` |
| Feedback de acao bem-sucedida | `Toast type="positive"` |
| Feedback de erro de sistema | `Toast type="negative"` |
| Info contextual inline (i) | `Information` (tooltip ao hover) |
| Info contextual rica | `Popover` |
| Loading de navegacao (barra topo) | `ProgressLoader placement="top"` |
| Carregamento de pagina/secao | `Skeleton` |
| Carregamento de acao pontual | `Spinner` ou `Button loading` |
| **Modais & Overlays** | |
| Aviso simples com "Ok" | `Alert` (modal pre-construido) |
| Confirmacao destrutiva (sim/nao) | `Confirm danger` (modal pre-construido) |
| Captura de input rapido | `Prompt` (modal pre-construido) |
| Dialog complexo customizado | `Modal` full (Header + Body + Footer) |
| Painel de detalhes lateral | `Drawer placement="right"` |
| Lista de acoes contextuais | `Dropdown` |
| **Busca** | |
| Barra de busca simples | `Search` (size md/lg, type primary/secondary) |
| Busca com autocomplete + historico | `SearchAutocomplete` (Trigger + Menu) |
| Campo com sugestoes dropdown | `Autocomplete` (Root + Trigger + Menu) |
| **Formularios** | |
| Selecao multipla (lista) | `Checkbox.Group` |
| Selecao multipla (cards visuais) | `CheckboxCard` (Icon + Content + Title) |
| Selecao unica de grupo (lista) | `Radio.Group` |
| Selecao unica (cards visuais) | `RadioCard.Group` (cards selecionaveis) |
| Toggle on/off | `Switch` |
| Selecao de lista longa | `Select` |
| Quantidade numerica +/- | `Quantity` (minValue/maxValue) |
| **Conteudo & Layout** | |
| Layout de pagina | `Container` + `Row` + `Col` (grid 12 colunas) |
| Card de resultado de busca (SERP) | `Snippet` (14+ subcomponentes compostos) |
| Card generico | `Card` (borda #CCD5E1, padding 24px) |
| Par chave-valor (dashboard) | `Detail` (Icon + Label + Value) |
| Card de documento/download | `File` (variant: neutral/pdf/doc) |
| Navegacao entre secoes | `Tabs` |
| Localizacao na hierarquia | `Breadcrumb` (min. 3 itens) |
| Paginacao completa (numeros) | `Pagination` |
| Paginacao simples (prev/next) | `PaginationSimple` |
| FAQ / secoes colapsaveis | `Accordion` |
| "Mostrar mais" em listas longas | `Collapse` + `CollapseControl` |
| Texto com "Ler mais/menos" | `CollapseText` (deteccao automatica) |
| Truncamento de texto (line-clamp) | `TruncateText` (responsivo) |
| Lista de beneficios/features | `IconList` com `CheckIcon` |
| Historico/etapas cronologicas | `Timeline` (size sm/md, icones custom) |
| Filtro hierarquico (arvore) | `TreeView.Checkbox` |
| Navegacao hierarquica | `TreeView.Link` |
| Slider de cards/imagens | `Carousel` (List + Item + Pagination) |
| Capa de livro/revista | `BookCover` (size xs→5xl) |
| Citacao/ementa juridica | `Quote` + `Quote.Cite` |
| HTML rico (artigo, editor) | `RichText` wrapper |
| Estado vazio / ilustracao | `Illustration` (60+ SVGs, size sm/md/lg) |
| **Chat** | |
| Bolha de mensagem de chat | `ChatMessage` (from: me/other, size: md/lg) |
| Chat com loading de resposta | `ChatMessage loading` + Header + Body + FooterControls |
| **Marca** | |
| Logo Jusbrasil | `Brand` (onlySymbol, version: positive/negative) |
| Logo Jus IA | `BrandJusIa` (onlySymbol, version: positive/negative) |

---

## Padrões de Acessibilidade

- HTML semântico: `<button>` para ações, `<a>` para navegação, headings para hierarquia
- Touch targets: mínimo 44×44px (`min-h-[44px] min-w-[44px]`)
- Focus rings visíveis: `focus-visible:ring-2 focus-visible:ring-ring`
- Contraste WCAG AA: 4.5:1 para texto normal, 3:1 para texto grande
- `aria-label` em botões icon-only
- `aria-live="polite"` em mensagens de erro e atualizações dinâmicas
- `aria-current="page"` no item ativo de navegação
- `prefers-reduced-motion` respeitado em animações
- Inputs sempre com `<label>` associado via `htmlFor`/`id`

---

## Interação e Motion

- Transições de cor/opacidade: `transition-colors duration-[160ms]`
- Hover em cards clicáveis: `hover:shadow-[var(--shadow-3)]`
- Transform só em elementos que não causam layout shift
- Loading de botão: `Button loading` prop (desabilita + spinner)
- `cursor-pointer` em todos os elementos clicáveis/hoverable

---

## Checklist Pré-Entrega

### Farol DS
- [ ] Todas as cores via CSS vars Tailwind (sem hex hardcoded)
- [ ] Tipografia Inter, tamanhos do scale Farol
- [ ] Ícones SVG do set Farol ou Lucide (sem emojis)
- [ ] Sombras adequadas à profundidade do elemento
- [ ] Radius consistente (cards `md`=16px, botões `sm`=8px, inputs `xs`=6px)
- [ ] Tokens de espaçamento do scale t-shirt

### Componentes
- [ ] Buttons com `kind` correto para a hierarquia de ação
- [ ] `Button loading` em todas as ações assíncronas
- [ ] FormControl wrapping todos os campos de formulário
- [ ] `FormControl.ErrorMessage` para todos os erros de validação
- [ ] Toast para feedback de ações (não inline em cabeçalho de página)

### Acessibilidade
- [ ] Todos os inputs com labels associados
- [ ] Ícones decorativos com `aria-hidden="true"`
- [ ] Focus states visíveis
- [ ] Contraste WCAG AA
- [ ] Touch targets ≥ 44px
- [ ] Conteúdo dinâmico com `aria-live`

### Layout
- [ ] Responsivo: 375px (mobile), 768px, 1024px, 1280px
- [ ] Sem scroll horizontal no mobile
- [ ] Conteúdo não escondido atrás de elementos fixos (header/sidebar)
- [ ] Dark mode: testar se as cores adaptam (se usar `.dark`)

### Conteúdo e Copy
- [ ] Acentuação correta em todo texto visível (português completo)
- [ ] Tom de voz adequado ao segmento (litigante vs profissional)
- [ ] Terminologia oficial dos produtos (ver `products.md`)
- [ ] Dados mock realistas: nomes brasileiros, CPFs formatados, números CNJ, datas em pt-BR
- [ ] CTAs claros com verbo de ação + benefício

### Qualidade de Código
- [ ] TypeScript: props tipadas corretamente
- [ ] Componentes com responsabilidade única
- [ ] Estados de loading, erro e vazio implementados
