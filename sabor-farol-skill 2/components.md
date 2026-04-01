# Farol DS — Referência Completa de Componentes

Todos os componentes são baseados em **Radix UI** (acessibilidade WAI-ARIA garantida).

---

## Tipografia

### Heading
**Props:** `size` (sm/md/lg/xl/2xl/3xl), `asChild`

```tsx
<h1 className="text-[40px] font-bold leading-tight text-foreground">Título Principal</h1>
<h2 className="text-[28px] font-bold leading-tight text-foreground">Seção</h2>
<h3 className="text-2xl font-semibold leading-tight text-foreground">Subseção</h3>
```

### BodyText / Caption
```tsx
<p className="text-base leading-normal text-foreground">Texto corpo</p>
<p className="text-base leading-normal text-muted-foreground">Texto secundário</p>
<span className="text-xs text-muted-foreground">Caption / metadata</span>
```

---

## Button

**Props:** `kind`, `size`, `block`, `loading`, `disabled`, `leftIcon`, `rightIcon`, `asChild`

### Kinds
- `primary` → fundo verde (`#007A5F`), texto branco — ação principal
- `secondary` → fundo branco, borda cinza (`#B3C0D0`), texto verde (`#007A5F`) — ação alternativa
- `tertiary` → fundo branco, borda cinza (`#B3C0D0`), texto escuro (`#2B3950`) — ação de baixa ênfase
- `plain` → apenas texto verde, sem borda/fundo — links de ação em contextos de texto
- `danger` → fundo vermelho (`#E41E3F`), texto branco — destrutivo
- `dangerSecondary` → fundo branco, borda vermelha, texto vermelho — destrutivo alternativo

### Sizes
- `xs` → min-h 24px · `sm` → min-h 36px · `md` → min-h 44px (padrão) · `lg` → min-h 56px

> **REGRA CRITICA 1 - border-radius:** Botoes Farol usam sempre `rounded-lg` = `border-radius: 8px`. NUNCA use `rounded-full`, `border-radius: 100px`, `border-radius: 500px` ou qualquer valor pill em `<button>` ou `<a>` que funcionem como botao. Formato pill (`border-radius: 100px+`) e **exclusivo de ChipClickable** (filtros interativos) e de toggles de modo de busca.

> **REGRA CRITICA 2 - contraste do texto:** O texto de `Button kind="primary"` e SEMPRE branco (`#FFFFFF` / `color: white`). NUNCA use `color: currentColor`, `color: inherit`, ou qualquer cor escura sobre o fundo verde `#007A5F`. O contraste verde+escuro e ilegivel. Em dark mode (`#00A37F`), o texto tambem e branco. Se o botao tem `background-color` verde (primary), o `color` do texto TEM que ser `white`. Isso vale para TODOS os contextos: heroes dark, landing pages, modais, cards, etc.

### Implementação TSX (Tailwind v4)
```tsx
// kind=primary
<button className="inline-flex items-center justify-center gap-2 bg-primary text-primary-foreground font-semibold text-sm rounded-lg px-4 min-h-[44px] cursor-pointer transition-colors duration-[160ms] hover:bg-primary/90 focus-visible:ring-2 focus-visible:ring-ring disabled:opacity-[0.64] disabled:cursor-not-allowed">
  {loading && <Loader2 className="w-4 h-4 animate-spin" aria-hidden />}
  Confirmar
</button>

// kind=secondary — borda cinza, texto verde (NÃO borda verde!)
<button className="inline-flex items-center justify-center gap-2 bg-white text-primary border border-[#B3C0D0] font-semibold text-sm rounded-lg px-4 min-h-[44px] cursor-pointer transition-colors duration-[160ms] hover:bg-muted">
  Cancelar
</button>

// kind=tertiary — borda cinza, texto escuro (NÃO texto verde!)
<button className="inline-flex items-center justify-center gap-2 bg-white text-foreground border border-[#B3C0D0] font-semibold text-sm rounded-lg px-4 min-h-[44px] cursor-pointer transition-colors duration-[160ms] hover:bg-muted">
  Ver mais
</button>

// kind=plain — só texto, sem borda
<button className="inline-flex items-center justify-center gap-2 text-primary font-semibold text-sm px-4 min-h-[44px] cursor-pointer transition-colors duration-[160ms] hover:underline">
  Ver detalhes
</button>

// kind=danger
<button className="inline-flex items-center justify-center gap-2 bg-destructive text-destructive-foreground font-semibold text-sm rounded-lg px-4 min-h-[44px] cursor-pointer transition-colors duration-[160ms] hover:bg-destructive/90">
  Excluir
</button>
```

---

## Badge

**Props:** `type` (primary/secondary/tertiary), `variant` (label/dot), `overlap` (circular/rectangular), `count`, `showZero`

```tsx
// label variant
<span className="inline-flex items-center gap-1.5 px-2.5 py-1 rounded-[6px] text-xs font-semibold bg-primary/10 text-primary border border-primary/20">
  <span className="w-1.5 h-1.5 rounded-full bg-primary" aria-hidden />
  Em andamento
</span>

// notification badge (dot/count sobre ícone)
<div className="relative">
  <BellIcon className="w-6 h-6 text-foreground" />
  <span className="absolute -top-1.5 -right-1.5 min-w-[18px] h-[18px] px-1 rounded-full bg-primary text-primary-foreground text-[10px] font-semibold leading-none flex items-center justify-center ring-2 ring-background">
    3
  </span>
</div>
```

### Status badges Jusbrasil
```tsx
const statusBadge = {
  "Em andamento":  "bg-secondary/10 text-secondary border-secondary/20",
  "Arquivado":     "bg-muted text-muted-foreground border-border",
  "Suspenso":      "bg-[#FDF0BB] text-[#826A03] border-[#FBD94C]/40",  // warning
  "Encerrado":     "bg-primary/10 text-primary border-primary/20",
  "Aguardando":    "bg-accent/10 text-accent border-accent/20",
}
```

---

## Card

**Props:** `disablePadding`, `disabled`, `highlight` (borda primária), `onClick`

Card usa borda `#CCD5E1` (não `#E2E8F0`) e padding 24px (`p-6`). Highlight usa borda 2px primária.

```tsx
// Card básico — borda #CCD5E1, padding 24px
<div className="bg-card text-card-foreground border border-[#CCD5E1] rounded-2xl p-6">
  Conteúdo
</div>

// Card clicável com highlight (borda primária 2px)
<div className="bg-card border-2 border-primary rounded-2xl p-6 cursor-pointer transition-shadow duration-[160ms] hover:shadow-[var(--shadow-3)]" role="button" tabIndex={0}>
  Conteúdo
</div>

// Card com shadow (overlays/elevação)
<div className="bg-card border border-[#CCD5E1] rounded-2xl p-6" style={{boxShadow: 'var(--shadow-2)'}}>
  Conteúdo
</div>

// Card desabilitado
<div className="bg-card border border-[#CCD5E1] rounded-2xl p-6 opacity-[0.64] pointer-events-none">
  Conteúdo
</div>
```

---

## Avatar

**Props:** `size` (xs/sm/md/lg/xl/2xl/3xl), `alt`, `color` (fallback bg)

```tsx
// Com imagem
<span className="inline-flex items-center justify-center w-10 h-10 rounded-full overflow-hidden bg-muted">
  <img src="user.jpg" alt="Nome do Usuário" className="w-full h-full object-cover" />
</span>

// Fallback com iniciais
<span className="inline-flex items-center justify-center w-10 h-10 rounded-full bg-primary text-primary-foreground text-sm font-semibold">
  JD
</span>
```

Sizes: xs=24px · sm=32px · md=40px · lg=48px · xl=56px · 2xl=64px · 3xl=80px

---

## FormControl

**Props:** `id`, `required`, `error`, `disabled`
**Subcomponentes:** Label · Description · ErrorMessage

```tsx
<div className="flex flex-col gap-1.5" role="group" aria-labelledby="email-label">
  {/* FormControl.Label */}
  <label id="email-label" htmlFor="email" className="text-sm font-semibold text-foreground">
    E-mail <span className="text-destructive" aria-hidden>*</span>
  </label>

  {/* FormControl.Description (opcional) */}
  <p className="text-xs text-muted-foreground">Usado para login e notificações</p>

  {/* Input */}
  <input id="email" type="email" aria-describedby="email-error" aria-invalid={!!error}
    className="w-full rounded-[6px] border border-border bg-background px-3 py-2.5 text-base text-foreground placeholder:text-muted-foreground focus:outline-none focus-within:border-primary focus-within:ring-2 focus-within:ring-primary/20" />

  {/* FormControl.ErrorMessage */}
  {error && (
    <span id="email-error" role="alert" aria-live="polite" className="flex items-center gap-1 text-xs text-destructive">
      <AlertCircle className="w-3 h-3" aria-hidden />
      {error}
    </span>
  )}
</div>
```

---

## Input

**Props:** `type`, `error`, `loading`, `rightIcon`, `onValueChange`

```tsx
<div className={`flex items-center rounded-[6px] border bg-background transition-colors ${error ? 'border-destructive' : 'border-border focus-within:border-primary focus-within:ring-2 focus-within:ring-primary/20'}`}>
  <input type="text" className="flex-1 min-w-0 px-3 py-2.5 text-base text-foreground placeholder:text-muted-foreground bg-transparent outline-none" />
  {rightIcon && <div className="pr-3">{rightIcon}</div>}
</div>
```

---

## Select

**Props:** `value`, `onValueChange`, `placeholder`

```tsx
<div className="relative">
  <select className="w-full rounded-[6px] border border-border bg-background px-3 py-2.5 text-base text-foreground appearance-none cursor-pointer focus:outline-none focus:border-primary focus:ring-2 focus:ring-primary/20">
    <option value="">Selecione...</option>
    <option value="sp">São Paulo</option>
  </select>
  <ChevronDown className="absolute right-3 top-1/2 -translate-y-1/2 w-4 h-4 text-muted-foreground pointer-events-none" />
</div>
```

---

## Checkbox

**Subcomponentes:** Group · Item · Name · Description

```tsx
<div className="flex items-start gap-3">
  <button role="checkbox" aria-checked={checked} className="w-5 h-5 rounded border-2 border-border flex items-center justify-center flex-shrink-0 mt-0.5 transition-colors checked:bg-primary checked:border-primary focus-visible:ring-2 focus-visible:ring-ring">
    {checked && <Check className="w-3 h-3 text-primary-foreground" aria-hidden />}
  </button>
  <div className="flex flex-col gap-0.5">
    <label className="text-sm font-semibold text-foreground">Aceitar termos</label>
    <p className="text-xs text-muted-foreground">Li e aceito os termos de uso</p>
  </div>
</div>
```

---

## Switch

**Props:** `checked`, `onCheckedChange`, `disabled`, `loading`, `size` (sm/md)

```tsx
<button role="switch" aria-checked={checked} className={`relative inline-flex h-6 w-11 rounded-full transition-colors duration-[160ms] ${checked ? 'bg-primary' : 'bg-muted'}`}>
  <span className={`absolute top-0.5 left-0.5 w-5 h-5 rounded-full bg-white transition-transform duration-[160ms] ${checked ? 'translate-x-5' : 'translate-x-0'}`}>
    {checked && <Check className="w-3 h-3 text-primary absolute top-1 left-1" aria-hidden />}
  </span>
</button>
```

---

## Tabs

**Props:** `value`, `defaultValue`, `onValueChange`, `activationMode`

```tsx
<div>
  {/* Tabs.List */}
  <div role="tablist" className="flex border-b border-border gap-1">
    {tabs.map(tab => (
      <button key={tab.value} role="tab" aria-selected={active === tab.value} aria-controls={`panel-${tab.value}`}
        className={`px-4 py-2.5 text-sm font-semibold transition-colors border-b-2 -mb-px ${active === tab.value ? 'border-primary text-primary' : 'border-transparent text-muted-foreground hover:text-foreground'}`}>
        {tab.label}
      </button>
    ))}
  </div>
  {/* Tabs.Content */}
  <div role="tabpanel" id={`panel-${active}`} className="pt-6">
    {/* conteúdo */}
  </div>
</div>
```

---

## Modal

**Props:** `size` (sm/md/lg/xl/full), `open`, `onOpenChange`

```tsx
{open && (
  <div className="fixed inset-0 z-50 flex items-center justify-center p-4">
    {/* Overlay */}
    <div className="absolute inset-0 bg-black/50" onClick={() => onOpenChange(false)} aria-hidden />
    {/* Content */}
    <div className="relative bg-card rounded-2xl w-full max-w-lg" style={{boxShadow: 'var(--shadow-4)'}}>
      {/* Modal.Header */}
      <div className="flex items-center justify-between p-6 border-b border-border">
        <h2 className="text-xl font-bold text-foreground">Título</h2>
        <button onClick={() => onOpenChange(false)} aria-label="Fechar" className="text-muted-foreground hover:text-foreground cursor-pointer focus-visible:ring-2 focus-visible:ring-ring rounded">
          <X className="w-5 h-5" />
        </button>
      </div>
      {/* Modal.Body */}
      <div className="p-6">Conteúdo</div>
      {/* Modal.Footer */}
      <div className="flex justify-end gap-3 p-6 border-t border-border">
        <button className="...kind-secondary">Cancelar</button>
        <button className="...kind-primary">Confirmar</button>
      </div>
    </div>
  </div>
)}
```

---

## Drawer

**Props:** `placement` (right/left/top/bottom), `size` (sm/md/lg/xl/full), `open`, `onOpenChange`

```tsx
{open && (
  <div className="fixed inset-0 z-50 flex justify-end">
    <div className="absolute inset-0 bg-black/50" onClick={() => onOpenChange(false)} aria-hidden />
    <div className="relative bg-card w-full max-w-sm h-full flex flex-col" style={{boxShadow: 'var(--shadow-4)'}}>
      <div className="flex items-center justify-between p-6 border-b border-border">
        <h2 className="text-xl font-bold text-foreground">Detalhes</h2>
        <button onClick={() => onOpenChange(false)} aria-label="Fechar drawer"><X className="w-5 h-5" /></button>
      </div>
      <div className="flex-1 overflow-auto p-6">Conteúdo</div>
    </div>
  </div>
)}
```

---

## Dropdown

```tsx
<div className="relative">
  <button onClick={() => setOpen(v => !v)} aria-haspopup="menu" aria-expanded={open}>
    Opções
  </button>
  {open && (
    <div role="menu" className="absolute right-0 mt-1 w-48 bg-card border border-border rounded-xl py-1" style={{boxShadow: 'var(--shadow-3)'}}>
      <button role="menuitem" className="w-full text-left px-4 py-2 text-sm text-foreground hover:bg-muted flex items-center gap-2">
        <Edit className="w-4 h-4" aria-hidden /> Editar
      </button>
      <div className="h-px bg-border mx-2 my-1" role="separator" />
      <button role="menuitem" className="w-full text-left px-4 py-2 text-sm text-destructive hover:bg-destructive/10 flex items-center gap-2">
        <Trash className="w-4 h-4" aria-hidden /> Excluir
      </button>
    </div>
  )}
</div>
```

---

## Toast

**Props:** `type` (neutral/positive/negative/warning/info), `duration`, `sensitivity`

```tsx
const toastConfig = {
  positive:  { bg: 'bg-[#F3F8ED]', border: 'border-[#98CC60]', icon: <CheckCircle className="text-[#669337]" /> },
  negative:  { bg: 'bg-[#FEE2E3]', border: 'border-destructive', icon: <XCircle className="text-destructive" /> },
  warning:   { bg: 'bg-[#FEFAEC]', border: 'border-[#FBD94C]', icon: <AlertTriangle className="text-[#826A03]" /> },
  info:      { bg: 'bg-[#EBF5FF]', border: 'border-accent', icon: <Info className="text-accent" /> },
  neutral:   { bg: 'bg-muted', border: 'border-border', icon: <Info className="text-muted-foreground" /> },
}

<div role="alert" aria-live="polite" className={`flex items-start gap-3 p-4 rounded-xl border ${config.bg} ${config.border}`} style={{boxShadow: 'var(--shadow-3)'}}>
  {config.icon}
  <p className="text-sm font-medium text-foreground flex-1">{message}</p>
  <button onClick={dismiss} aria-label="Fechar notificação"><X className="w-4 h-4 text-muted-foreground" /></button>
</div>
```

---

## Pagination

**Props:** `count`, `page`, `onPageChange`, `buildPageUrl`

```tsx
<nav aria-label="Paginação" className="flex items-center gap-1">
  <button disabled={page === 1} onClick={() => onPageChange(page - 1)} aria-label="Página anterior"
    className="w-9 h-9 flex items-center justify-center rounded-lg border border-border text-muted-foreground hover:bg-muted disabled:opacity-[0.64] disabled:cursor-not-allowed">
    <ChevronLeft className="w-4 h-4" />
  </button>
  {pages.map(p => (
    <button key={p} onClick={() => onPageChange(p)} aria-current={p === page ? 'page' : undefined}
      className={`w-9 h-9 flex items-center justify-center rounded-lg text-sm font-semibold ${p === page ? 'bg-primary text-primary-foreground' : 'border border-border text-foreground hover:bg-muted'}`}>
      {p}
    </button>
  ))}
  <button disabled={page === count} onClick={() => onPageChange(page + 1)} aria-label="Próxima página"
    className="w-9 h-9 flex items-center justify-center rounded-lg border border-border text-muted-foreground hover:bg-muted disabled:opacity-[0.64] disabled:cursor-not-allowed">
    <ChevronRight className="w-4 h-4" />
  </button>
</nav>
```

---

## Breadcrumb

Mínimo 3 itens: HomeItem + Items.

```tsx
<nav aria-label="Caminho da página atual">
  <ol className="flex items-center gap-2 text-sm text-muted-foreground">
    <li><a href="/" aria-label="Início" className="hover:text-foreground"><Home className="w-4 h-4" /></a></li>
    <li aria-hidden><ChevronRight className="w-4 h-4" /></li>
    <li><a href="/processos" className="hover:text-foreground">Processos</a></li>
    <li aria-hidden><ChevronRight className="w-4 h-4" /></li>
    <li aria-current="page" className="text-foreground font-semibold">0001234-56.2023.8.26.0100</li>
  </ol>
</nav>
```

---

## Skeleton

```tsx
<div className="animate-pulse">
  <div className="h-6 bg-muted rounded-[6px] w-3/4 mb-3" />
  <div className="h-4 bg-muted rounded-[6px] w-1/2 mb-2" />
  <div className="h-4 bg-muted rounded-[6px] w-2/3" />
</div>
```

---

## Spinner

```tsx
<svg className="animate-spin w-5 h-5 text-primary" fill="none" viewBox="0 0 24 24" aria-label="Carregando">
  <circle className="opacity-25" cx="12" cy="12" r="10" stroke="currentColor" strokeWidth="4" />
  <path className="opacity-75" fill="currentColor" d="M4 12a8 8 0 018-8v4a4 4 0 00-4 4H4z" />
</svg>
```

---

## Grid — Container / Row / Col

**O sistema de grid mais usado no produto** (centenas de ocorrências). Use sempre para layout de página.

**Container** `type`: `default` (max 1280px) · `letter` (max 760px, para artigos/chat) · `fluid` (100%)

**Col** aceita breakpoints: `xs`, `sm`, `md`, `lg`, `xl` (valores 0–12)

```tsx
import { Container, Row, Col } from '@farol-ds/react'

// Layout de página padrão
<Container>             {/* type="default" — 1280px max */}
  <Row>
    <Col xs={12} md={8}>Conteúdo principal</Col>
    <Col xs={12} md={4}>Sidebar</Col>
  </Row>
</Container>

// Seção fluida (full-width background) + conteúdo centrado
<Container type="fluid" className="bg-muted py-16">
  <Container>
    <Row>
      <Col xs={12} md={6}>Esquerda</Col>
      <Col xs={12} md={6}>Direita</Col>
    </Row>
  </Container>
</Container>

// Grid de 3 cards responsivo
<Container>
  <Row>
    {items.map((item, i) => (
      <Col key={i} xs={12} md={4}>
        <Card>...</Card>
      </Col>
    ))}
  </Row>
</Container>

// Container letter — para conteúdo de leitura (artigos, chat)
<Container type="letter">
  <p>Texto com max-width de leitura confortável</p>
</Container>
```

---

## IconButton

Botão somente ícone com tooltip obrigatório (acessibilidade). Sem `label` visível, o tooltip é sempre mostrado.

**Props:** `label` (obrigatório, vai pro tooltip e aria-label) · `kind` (plain/primary/secondary/tertiary/dangerSecondary) · `size` (xs/sm/md/lg) · `icon` · `loading` · `disabled`

```tsx
import { IconButton, EditIcon, TrashIcon } from '@farol-ds/react'

// Botão de ação em tabela/card
<IconButton label="Editar" kind="plain" size="sm" icon={<EditIcon />} onClick={handleEdit} />

// Botão destrutivo
<IconButton label="Excluir" kind="dangerSecondary" size="sm" icon={<TrashIcon />} />

// Como link
<IconButton label="Compartilhar" kind="plain" icon={<ShareIcon />} asChild>
  <a href="/share" />
</IconButton>
```

---

## Chip

Status e categorias — **não é clicável**. Use para exibir estado/categoria de um item.

**Props:** `kind` (secondary/tertiary/info/negative/warning/positive) · `size` (sm=24px / md=32px)

`border-radius: pill` (500px) — formato capsule, diferente de Badge.

```tsx
import { Chip } from '@farol-ds/react'

<Chip kind="positive" size="sm">Ativa</Chip>
<Chip kind="negative" size="sm">Inativa</Chip>
<Chip kind="info" size="md">Novo</Chip>
<Chip kind="warning" size="md">Pendente</Chip>
<Chip kind="secondary" size="md">Profissional</Chip>

// Tailwind equivalente (quando não usar @farol-ds/react)
const chipKinds = {
  positive:  'bg-[#F3F8ED] text-[#669337] border border-[#98CC60]',
  negative:  'bg-[#FEE2E3] text-destructive border border-destructive/30',
  warning:   'bg-[#FEFAEC] text-[#826A03] border border-[#FBD94C]',
  info:      'bg-[#EBF5FF] text-accent border border-accent/30',
  secondary: 'bg-muted text-foreground border border-border',
  tertiary:  'bg-muted text-muted-foreground border border-border',
}
// sempre rounded-full px-2.5 text-xs font-semibold
```

---

## ChipClickable

Chip interativo — filtros, tabs compactas, seleções. Tem estado `selected` e pode ter `chevron`.

**Props:** `size` (sm/md/lg) · `selected` · `loading` · `disabled` · `leftIcon` · `chevron` · `chevronUp`

```tsx
import { ChipClickable } from '@farol-ds/react'

// Filtro de busca
<ChipClickable selected={activeFilter === 'jurisprudencia'} onClick={() => setFilter('jurisprudencia')}>
  Jurisprudência
</ChipClickable>

// Com ícone e chevron (dropdown trigger)
<ChipClickable leftIcon={<FilterIcon />} chevron size="md">
  Filtros
</ChipClickable>

// Como link (asChild)
<ChipClickable asChild selected={isActive}>
  <a href="/jurisprudencia">Jurisprudência</a>
</ChipClickable>

// Tailwind equivalente
<span role="button" tabIndex={0}
  className={`inline-flex items-center gap-1.5 px-3 h-10 rounded-full text-sm font-semibold cursor-pointer transition-colors
    ${selected ? 'bg-primary text-primary-foreground' : 'bg-muted text-foreground hover:bg-muted/80'}`}>
  Filtro
</span>
```

---

## Banner

Notificação inline persistente em nível de página (diferente de Toast que é temporário e flutuante).

**Props:** `type` (info/positive/warning/critical/discovery) · `level` (standard/app)

- `level="standard"` → inline dentro do conteúdo da página
- `level="app"` → full-width no topo da aplicação (acima do header)

```tsx
import { Banner } from '@farol-ds/react'

// Info padrão
<Banner type="info">
  <Banner.Title>Atualização disponível</Banner.Title>
  <Banner.Description>Uma nova versão está pronta para instalar.</Banner.Description>
</Banner>

// Warning com ação
<Banner type="warning">
  <Banner.Title>Assinatura expirando</Banner.Title>
  <Banner.Description>Seu plano vence em 3 dias.</Banner.Description>
  <Banner.Action>
    <Button kind="secondary" size="sm" asChild><a href="/planos">Renovar</a></Button>
  </Banner.Action>
</Banner>

// Tailwind equivalente
const bannerTypes = {
  info:      { bg: 'bg-[#EBF5FF]', border: 'border-accent', icon: 'text-accent' },
  positive:  { bg: 'bg-[#F3F8ED]', border: 'border-[#98CC60]', icon: 'text-[#669337]' },
  warning:   { bg: 'bg-[#FEFAEC]', border: 'border-[#FBD94C]', icon: 'text-[#826A03]' },
  critical:  { bg: 'bg-[#FEE2E3]', border: 'border-destructive', icon: 'text-destructive' },
  discovery: { bg: 'bg-[#F5F0FF]', border: 'border-[#8B5CF6]', icon: 'text-[#8B5CF6]' },
}
// Estrutura: flex items-start gap-3 p-4 rounded-xl border-l-4 + bg + border-color
```

---

## Accordion

Seções colapsáveis com animação. Comum em FAQs e seções de detalhes.

**Subcomponentes:** Item · Header · Title · Content · Text · HelpText · Icon

```tsx
import { Accordion } from '@farol-ds/react'

<Accordion type="single" collapsible>
  <Accordion.Item value="q1">
    <Accordion.Header>
      <Accordion.Title>O que é Jusbrasil?</Accordion.Title>
      <Accordion.Icon />
    </Accordion.Header>
    <Accordion.Content>
      <Accordion.Text>
        Jusbrasil é a maior plataforma jurídica do Brasil...
      </Accordion.Text>
    </Accordion.Content>
  </Accordion.Item>
  <Accordion.Item value="q2">
    <Accordion.Header>
      <Accordion.Title>Como cancelar meu plano?</Accordion.Title>
      <Accordion.Icon />
    </Accordion.Header>
    <Accordion.Content>
      <Accordion.Text>Você pode cancelar nas configurações...</Accordion.Text>
    </Accordion.Content>
  </Accordion.Item>
</Accordion>
```

---

## IconList

Lista com ícones alinhados — muito usado em benefícios de plano e features.

**Subcomponentes:** Item (com prop `icon`)

```tsx
import { IconList, CheckIcon } from '@farol-ds/react'

// Lista de benefícios de plano
<IconList>
  <IconList.Item icon={<CheckIcon />}>
    <strong>Acesso ilimitado</strong> a jurisprudências
  </IconList.Item>
  <IconList.Item icon={<CheckIcon />}>
    Alertas de movimentação processual
  </IconList.Item>
  <IconList.Item icon={<CheckIcon />}>
    Jus IA incluso
  </IconList.Item>
</IconList>
```

---

## Information

Ícone de informação (ⓘ) que abre um tooltip/popover ao hover. Para dicas contextuais inline.

**Props:** `label` (texto do tooltip) · `size` (xs/sm) · `placement` (top/right/bottom/left) · `onColor`

```tsx
import { Information } from '@farol-ds/react'

// Ao lado de um label de formulário
<div className="flex items-center gap-1">
  <label>Taxa de conversão</label>
  <Information label="Percentual de visitantes que realizaram uma ação" />
</div>

// Em fundo colorido
<Information label="Disponível apenas no plano Pro" onColor />
```

---

## Link (Farol)

Componente de link tipado — diferente do `<a>` nativo, tem variantes de cor.

**Props:** `type` (primary/secondary/tertiary/ghost) · `href` · `asChild`

- `primary` → verde (`--primary`) — link padrão do produto
- `secondary` → foreground com underline
- `ghost` → sem decoração visual, herdando cor do contexto

```tsx
import { Link } from '@farol-ds/react'

<Link href="/processos" type="primary">Ver processos</Link>
<Link href="/ajuda" type="secondary">Central de ajuda</Link>

// Como Next.js Link
<Link type="primary" asChild>
  <NextLink href="/planos">Ver planos</NextLink>
</Link>
```

---

## Autocomplete

Campo de busca com sugestoes dropdown, filtro fuzzy e historico.

**Subcomponentes:** Root . Trigger . Menu . Item . ItemContent . ItemRemove

**Trigger Props:** `loading`, `onValueChange`, `defaultOpenOnFocus`, `defaultCloseOnBlur`
**Menu Props:** `options: T[]`, `filterOptions`, `onOptionSelect`, `onOptionRemove`, `onOpenChange`

**AutocompleteOption:** `{ value: string, id?, label?, history?, leftIcon?, helpText? }`

```tsx
import { Autocomplete } from '@farol-ds/react'

<Autocomplete.Root>
  <Autocomplete.Trigger
    placeholder="Buscar..."
    loading={isSearching}
    onValueChange={(e, val) => handleSearch(val)}
  />
  <Autocomplete.Menu
    options={suggestions}
    onOptionSelect={(e, opt) => handleSelect(opt)}
  />
</Autocomplete.Root>
```

**Quando usar:** Campos de busca com sugestoes, historico de pesquisa, autocomplete de termos juridicos.

---

## Search

Campo de busca com botao de busca e limpar integrados.

**Props:** `type` (primary/secondary), `size` (md/lg), `disabled`, `loading`, `onSearch(evt, value)`, `onValueChange(evt, value)`, `onValueClear(evt)`

**Subcomponentes:** Filter (opcional, filtro de categoria)

```tsx
import { Search } from '@farol-ds/react'

// Busca simples
<Search size="lg" type="primary" onSearch={(e, val) => doSearch(val)} placeholder="Pesquisar..." />

// Busca secundaria (menor)
<Search size="md" type="secondary" loading={isSearching} />
```

**Quando usar:** Barra de busca principal de pagina, campos de pesquisa em headers.

---

## SearchAutocomplete

Busca com autocomplete integrado. No mobile (type primary), abre fullscreen com overlay.

**Props:** `type` (primary/secondary), `size` (md/lg), `onFocusedChange`, `rootRef`
**Subcomponentes:** Trigger . Menu

```tsx
import { SearchAutocomplete } from '@farol-ds/react'

// Busca principal do Alabama (produto real)
<SearchAutocomplete type="secondary" size="lg" rootRef={searchRef}>
  <SearchAutocomplete.Trigger
    placeholder="Pesquisar jurisprudencia, legislacao..."
    onValueChange={debounce(handleSearch, 250)}
  />
  <SearchAutocomplete.Menu
    options={suggestions}
    onOptionSelect={handleSelect}
  />
</SearchAutocomplete>
```

**Quando usar:** Busca principal de produto (SERP), quando precisa de autocomplete + historico. `type="primary"` para busca hero, `type="secondary"` para headers.

---

## ChatMessage

Bolhas de chat com direcao (me/other), loading e controles de rodape.

**Props:** `size` (md/lg), `from` (me/other), `loading`
**Subcomponentes:** Header . HeaderLabel . Content . Body . FooterControls

```tsx
import { ChatMessage } from '@farol-ds/react'

// Mensagem do usuario
<ChatMessage from="me" size="md">
  <ChatMessage.Content>
    <ChatMessage.Body>Qual o prazo para recurso?</ChatMessage.Body>
  </ChatMessage.Content>
</ChatMessage>

// Resposta da IA com loading
<ChatMessage from="other" size="md" loading={isGenerating}>
  <ChatMessage.Header>
    <ChatMessage.HeaderLabel>Resposta</ChatMessage.HeaderLabel>
  </ChatMessage.Header>
  <ChatMessage.Content>
    <ChatMessage.Body>O prazo para recurso de apelacao...</ChatMessage.Body>
  </ChatMessage.Content>
  <ChatMessage.FooterControls>
    {/* botoes de acao: copiar, curtir, etc */}
  </ChatMessage.FooterControls>
</ChatMessage>
```

**Quando usar:** Interfaces de chat do Jus IA, conversas, threads de perguntas.

---

## Snippet

Card rico de conteudo para resultados de busca, artigos e previews. O componente mais composto do Farol.

**Subcomponentes (14+):** Container . Cover . Body . Content . Caption . CaptionItem . Tags . TagsItem . Title . Header . Tail . Footnote . FootnoteContainer . FootnoteCover . FootnoteCaption . FootnoteTitle . FootnoteBody

```tsx
import { Snippet } from '@farol-ds/react'

// Card de resultado de busca
<Snippet>
  <Snippet.Container>
    <Snippet.Cover>{/* imagem/icone */}</Snippet.Cover>
    <Snippet.Body>
      <Snippet.Header>
        <Snippet.Title>Recurso Especial n. 1.234.567</Snippet.Title>
      </Snippet.Header>
      <Snippet.Content>
        <p>Ementa do processo...</p>
      </Snippet.Content>
      <Snippet.Caption>
        <Snippet.CaptionItem>STJ</Snippet.CaptionItem>
        <Snippet.CaptionItem>2024</Snippet.CaptionItem>
      </Snippet.Caption>
      <Snippet.Tags>
        <Snippet.TagsItem>Direito Civil</Snippet.TagsItem>
      </Snippet.Tags>
    </Snippet.Body>
  </Snippet.Container>
  <Snippet.Tail>{/* acoes */}</Snippet.Tail>
</Snippet>

// Com Footnote (citacao/referencia)
<Snippet>
  <Snippet.Container>...</Snippet.Container>
  <Snippet.Footnote>
    <Snippet.FootnoteContainer>
      <Snippet.FootnoteCover>{/* icone */}</Snippet.FootnoteCover>
      <Snippet.FootnoteBody>
        <Snippet.FootnoteTitle>Referencia</Snippet.FootnoteTitle>
        <Snippet.FootnoteCaption>Fonte citada</Snippet.FootnoteCaption>
      </Snippet.FootnoteBody>
    </Snippet.FootnoteContainer>
  </Snippet.Footnote>
</Snippet>
```

**Quando usar:** Cards de resultado de busca (SERP), previews de artigos/jurisprudencia, listagens de documentos.

---

## Detail

Display de par chave-valor com icone opcional. Usado em dashboards e fichas de dados.

**Props:** `inline` (layout horizontal)
**Subcomponentes:** Icon . Label . Value

```tsx
import { Detail } from '@farol-ds/react'

// Ficha de dados (CPro Admin - uso real)
<Detail>
  <Detail.Icon>{/* icone opcional */}</Detail.Icon>
  <Detail.Label>Receita mensal</Detail.Label>
  <Detail.Value>R$ 45.000,00</Detail.Value>
</Detail>

// Inline (horizontal)
<Detail inline>
  <Detail.Label>Status</Detail.Label>
  <Detail.Value>Ativo</Detail.Value>
</Detail>
```

**Quando usar:** Dashboards admin, fichas de organizacao, metadata de documentos, propriedades de processos.

---

## File

Card de arquivo/documento com estados de download, loading e erro.

**Props:** `variant` (neutral/pdf/doc), `selected`, `loading`, `disabled`, `error`, `leftIcon`, `rightIcon`
**Subcomponentes:** Content . Label . HelpText

```tsx
import { File } from '@farol-ds/react'

// Documento PDF para download
<File variant="pdf" onClick={handleDownload}>
  <File.Content>
    <File.Label>Peticao_inicial.pdf</File.Label>
    <File.HelpText>2.4 MB</File.HelpText>
  </File.Content>
</File>

// Com loading
<File variant="doc" loading>
  <File.Content>
    <File.Label>Contrato.docx</File.Label>
  </File.Content>
</File>

// Com erro
<File variant="neutral" error>
  <File.Content>
    <File.Label>Documento.pdf</File.Label>
    <File.HelpText>Ocorreu um erro inesperado</File.HelpText>
  </File.Content>
</File>
```

**Quando usar:** Listas de documentos para download, anexos de processo, upload de identidade. Icone automatico por variante (PDF vermelho, DOC azul, neutral cinza).

---

## Carousel

Slider com scroll snap, paginacao integrada e suporte responsivo.

**Subcomponentes:** Root . List . Item . Pagination
**List Props:** `gap` (tokens de espacamento)
**Item Props:** `snapPoint` (start/end)

```tsx
import { Carousel, Card, BookCover } from '@farol-ds/react'

// Carrossel de artigos recomendados (Alabama - uso real)
<Carousel.Root>
  <Carousel.List gap="xs">
    {articles.map(article => (
      <Carousel.Item key={article.id}>
        <Card>{/* conteudo */}</Card>
      </Carousel.Item>
    ))}
  </Carousel.List>
  <Carousel.Pagination />
</Carousel.Root>

// Carrossel de capas de livros (Journal - uso real)
<Carousel.Root>
  <Carousel.List gap="3xs">
    {books.map(book => (
      <Carousel.Item key={book.id}>
        <BookCover size="md">
          <img src={book.cover} alt={book.title} />
        </BookCover>
      </Carousel.Item>
    ))}
  </Carousel.List>
  <Carousel.Pagination />
</Carousel.Root>
```

**Quando usar:** Recomendacoes de artigos, catalogo de livros/revistas, depoimentos, cards promocionais.

---

## BookCover

Wrapper para capas de livros/revistas com mascara decorativa e tamanhos padronizados.

**Props:** `size` (xs/sm/md/lg/5xl), `asChild`

```tsx
import { BookCover } from '@farol-ds/react'

<BookCover size="md">
  <img src="/capa-revista.jpg" alt="Revista Juridica n. 42" />
</BookCover>
```

**Quando usar:** Catalogo de revistas juridicas, capas de e-books, biblioteca digital.

---

## Timeline

Visualizacao cronologica de etapas/historico com icones customizaveis.

**Props:** `size` (sm/md), `endless` (omite linha final)
**Subcomponentes:** Item (props: `icon`, `highlighted`, `highlightedDelay`)

```tsx
import { Timeline, CheckIcon, ShareIcon, ListUnorderedIcon, ReplyIcon } from '@farol-ds/react'

// Guia de etapas (Research Lab - uso real)
<Timeline size="md">
  <Timeline.Item icon={<ShareIcon />}>
    <Heading size="sm">Compartilhe sua pesquisa</Heading>
    <BodyText>Envie o link do tema para o Jusbrasil...</BodyText>
  </Timeline.Item>
  <Timeline.Item icon={<ListUnorderedIcon />}>
    <Heading size="sm">Receba os resultados</Heading>
    <BodyText>O sistema analisa automaticamente...</BodyText>
  </Timeline.Item>
  <Timeline.Item icon={<CheckIcon />}>
    <Heading size="sm">Valide e utilize</Heading>
    <BodyText>Revise os resultados encontrados...</BodyText>
  </Timeline.Item>
</Timeline>

// Timeline sem fim (historico em progresso)
<Timeline size="sm" endless>
  <Timeline.Item highlighted>Movimentacao recente</Timeline.Item>
  <Timeline.Item>Distribuicao em 01/03/2024</Timeline.Item>
</Timeline>
```

**Quando usar:** Historico de movimentacoes processuais, guia passo-a-passo, progresso de tarefa.

---

## TreeView

Navegacao hierarquica com suporte a checkbox, links e lazy loading.

**Props:** `defaultExpanded`, `defaultSelected`, `onExpandedChange`, `onSelectedChange`, `isSelected`, `getItemProps`, `getTogglerProps`
**Subcomponentes:** List . Item . Checkbox . Link

```tsx
import { TreeView } from '@farol-ds/react'

// Filtro hierarquico (LGPD Panel - uso real)
<TreeView.List>
  <TreeView.Checkbox
    defaultExpanded={['cat-1']}
    onSelectedChange={handleFilter}
  >
    <TreeView.Item nodeId="cat-1" label="Direito Civil">
      <TreeView.Item nodeId="cat-1-1" label="Contratos" />
      <TreeView.Item nodeId="cat-1-2" label="Responsabilidade" />
    </TreeView.Item>
    <TreeView.Item nodeId="cat-2" label="Direito Penal">
      <TreeView.Item nodeId="cat-2-1" label="Crimes contra pessoa" />
    </TreeView.Item>
  </TreeView.Checkbox>
</TreeView.List>
```

**Quando usar:** Filtros hierarquicos (areas do direito, tribunais), navegacao de categorias, file browsers.

---

## SelectionCard / CheckboxCard / RadioCard

Cards selecionaveis que combinam checkbox/radio com layout de card visual.

### CheckboxCard

**Props:** extends CheckboxProps + `orientation` (horizontal/vertical), `controlHidden`
**Subcomponentes:** Icon . Content . ContentTitle . ContentDescription

```tsx
import { CheckboxCard } from '@farol-ds/react'

<CheckboxCard orientation="horizontal" onCheckedChange={setSelected}>
  <CheckboxCard.Icon>{/* icone */}</CheckboxCard.Icon>
  <CheckboxCard.Content>
    <CheckboxCard.ContentTitle>Plano Pro</CheckboxCard.ContentTitle>
    <CheckboxCard.ContentDescription>Acesso completo ao Jus IA</CheckboxCard.ContentDescription>
  </CheckboxCard.Content>
</CheckboxCard>
```

### RadioCard

**Props:** `value` (obrigatorio), `orientation`, `controlHidden`
**Subcomponentes:** Group . Icon . Content . ContentTitle . ContentDescription

```tsx
import { RadioCard } from '@farol-ds/react'

<RadioCard.Group defaultValue="monthly" onValueChange={setPlan}>
  <RadioCard value="monthly">
    <RadioCard.Content>
      <RadioCard.ContentTitle>Mensal</RadioCard.ContentTitle>
      <RadioCard.ContentDescription>R$ 49,90/mes</RadioCard.ContentDescription>
    </RadioCard.Content>
  </RadioCard>
  <RadioCard value="annual">
    <RadioCard.Content>
      <RadioCard.ContentTitle>Anual</RadioCard.ContentTitle>
      <RadioCard.ContentDescription>R$ 39,90/mes</RadioCard.ContentDescription>
    </RadioCard.Content>
  </RadioCard>
</RadioCard.Group>
```

**Quando usar:** Selecao de plano/pricing, escolha de opcoes visuais, formularios com opcoes ricas.

---

## RichIcon

Icone com fundo semantico colorido e tamanhos padronizados.

**Props:** `icon` (IconComponent, obrigatorio), `size` (sm/md/lg), `type` (primary/positive/warning/negative/discovery), `disabled`

```tsx
import { RichIcon, CheckCircleIcon, AlertIcon } from '@farol-ds/react'

// Feature card (Plans - uso real)
<RichIcon icon={CheckCircleIcon} size="lg" type="positive" />

// Status de erro
<RichIcon icon={AlertIcon} size="md" type="negative" />

// Icone desabilitado
<RichIcon icon={LockIcon} size="sm" type="primary" disabled />
```

**Quando usar:** Feature cards com icones coloridos, indicadores de status, listas de beneficios. Tipos: primary (azul), positive (verde), warning (amarelo), negative (vermelho), discovery (roxo).

---

## Quantity

Input numerico com botoes +/- para incremento/decremento.

**Props:** `value`, `defaultValue`, `minValue`, `maxValue`, `onValueChange`, `disabled`

```tsx
import { Quantity } from '@farol-ds/react'

// Seletor de usuarios no plano (Landing pages - uso real)
<Quantity
  defaultValue={1}
  minValue={1}
  maxValue={50}
  onValueChange={(e, val) => setUserCount(val)}
/>
```

**Quando usar:** Quantidade de licencas/usuarios, carrinho de compras, seletores numericos com limites.

---

## Quote

Blockquote semantico com atribuicao.

**Subcomponentes:** Cite

```tsx
import { Quote } from '@farol-ds/react'

<Quote>
  A justica atrasada nao e justica, senao injustica qualificada e manifesta.
  <Quote.Cite>Rui Barbosa</Quote.Cite>
</Quote>

// Tailwind equivalente
<blockquote className="border-l-4 border-primary pl-4 py-2 italic text-foreground">
  <p>Texto da citacao...</p>
  <cite className="text-sm text-muted-foreground not-italic block mt-2">- Autor</cite>
</blockquote>
```

**Quando usar:** Citacoes de jurisprudencia, ementas, trechos de doutrina, depoimentos.

---

## Brand / BrandJusIa

Componentes oficiais de logo Jusbrasil e Jus IA.

**Props (ambos):** `onlySymbol` (default false), `version` (positive/negative), + SVGProps (width, height)

```tsx
import { Brand, BrandJusIa } from '@farol-ds/react'

// Logo Jusbrasil no header (CPro Admin - uso real)
<Brand width={140} />

// Apenas simbolo (compacto)
<Brand onlySymbol width={32} />

// Logo Jus IA em card de plano (Landing pages - uso real)
<BrandJusIa width={95} height={27} />

// Versao negativa (fundo escuro)
<Brand version="negative" width={140} />
<BrandJusIa version="negative" />
```

**Quando usar:** Headers, footers, cards de plano, paginas de marketing. `positive` para fundo claro, `negative` para fundo escuro.

---

## Collapse / CollapseText / CollapseControl

Componentes para expandir/colapsar conteudo.

### Collapse

**Props:** `open`, `defaultOpen`, `onOpenChange`
**Subcomponentes:** Content

```tsx
import { Collapse } from '@farol-ds/react'

// Mostrar mais itens (Alabama - uso real)
<Collapse defaultOpen={false}>
  <Collapse.Content>
    {/* conteudo colapsavel - items extras */}
  </Collapse.Content>
</Collapse>
```

### CollapseText

Texto com "Ler mais/menos" automatico. Detecta truncamento via ResizeObserver.

**Props:** extends TruncateTextProps + `onOpenChange`, `onTruncateChange`, `defaultOpen`

```tsx
import { CollapseText } from '@farol-ds/react'

<CollapseText value={3} defaultOpen={false}>
  Texto longo que sera truncado em 3 linhas com botao de expandir automatico...
</CollapseText>
```

### CollapseControl

Botao "Mostrar mais/menos" standalone.

**Props:** extends ButtonProps + `open`, `showMoreLabel` ("Mostrar mais"), `showLessLabel` ("Mostrar menos")

```tsx
import { CollapseControl } from '@farol-ds/react'

<CollapseControl open={isExpanded} onClick={toggle} showMoreLabel="Ver todos" showLessLabel="Ocultar" />
```

**Quando usar:** Listas longas com "ver mais" (Collapse), descricoes truncadas (CollapseText), FAQs e detalhes colapsaveis.

---

## ContextMenu

Menu de contexto acionado por clique direito, baseado em Radix.

**Subcomponentes:** Root . Trigger . Content . Item

```tsx
import { ContextMenu } from '@farol-ds/react'

<ContextMenu.Root>
  <ContextMenu.Trigger>
    <div>Clique com botao direito aqui</div>
  </ContextMenu.Trigger>
  <ContextMenu.Content>
    <ContextMenu.Item leftIcon={<CopyIcon />}>Copiar</ContextMenu.Item>
    <ContextMenu.Item leftIcon={<EditIcon />}>Editar</ContextMenu.Item>
    <ContextMenu.Item leftIcon={<TrashIcon />}>Excluir</ContextMenu.Item>
  </ContextMenu.Content>
</ContextMenu.Root>
```

**Quando usar:** Menus de contexto em tabelas, cards de documento, areas de edicao.

---

## ChipRemovable

Tag com botao de remocao integrado. Diferente de Chip (status) e ChipClickable (filtro).

**Props:** `leftIcon`, `onRemove`, `disabled`, `unstable_truncate`, `title`

```tsx
import { ChipRemovable } from '@farol-ds/react'

// Filtros ativos removiveis
<ChipRemovable leftIcon={<FilterIcon />} onRemove={handleRemove}>
  Direito Civil
</ChipRemovable>

// Com truncamento
<ChipRemovable unstable_truncate title="Tribunal de Justica do Estado de Sao Paulo" onRemove={handleRemove}>
  Tribunal de Justica do Estado de Sao Paulo
</ChipRemovable>
```

**Quando usar:** Tags de filtro ativo que podem ser removidos, chips de busca selecionados, inputs de tag.

---

## Modal Alerts (Alert / Confirm / Prompt)

Modais pre-construidos para cenarios comuns. Mais simples que Modal full.

### Alert (notificacao simples)
```tsx
import { Alert } from '@farol-ds/react'

<Alert title="Acao concluida" description="O documento foi salvo com sucesso." confirmLabel="Ok">
  <Button>Salvar</Button>
</Alert>
```

### Confirm (escolha binaria)
```tsx
import { Confirm } from '@farol-ds/react'

// Confirmacao destrutiva
<Confirm
  title="Excluir documento?"
  description="Esta acao nao pode ser desfeita."
  danger
  confirmLabel="Excluir"
  cancelLabel="Cancelar"
  onConfirm={handleDelete}
  confirmProps={{ loading: isDeleting }}
>
  <Button kind="danger">Excluir</Button>
</Confirm>
```

### Prompt (input do usuario)
```tsx
import { Prompt } from '@farol-ds/react'

<Prompt
  title="Renomear pasta"
  description="Digite o novo nome:"
  inputPlaceholder="Nome da pasta"
  confirmLabel="Renomear"
  onConfirm={(value) => handleRename(value)}
>
  <Button>Renomear</Button>
</Prompt>
```

**Quando usar:** Alert para avisos simples, Confirm para acoes destrutivas/binarias, Prompt para captura de input rapido. Preferir estes sobre Modal customizado quando o cenario for simples.

---

## ProgressLoader

Barra de progresso no topo/fundo da pagina para loading de navegacao.

**Props:** `placement` (none/top/bottom), `visible`, `on`/`off` (event callbacks)

```tsx
import { ProgressLoader } from '@farol-ds/react'

// Barra de loading no topo da pagina
<ProgressLoader placement="top" visible={isNavigating} />
```

**Quando usar:** Loading de navegacao entre paginas (Next.js route changes), requisicoes longas de API.

---

## PaginationSimple

Paginacao simplificada com apenas prev/next (sem numeros de pagina).

**Props:** `count`, `page`, `defaultPage`, `onPageChange`, `buildPageUrl`

```tsx
import { PaginationSimple } from '@farol-ds/react'

<PaginationSimple count={10} page={currentPage} onPageChange={setPage} />
// Exibe: "< 3 of 10 >"
```

**Quando usar:** Listas com poucas paginas, carroseis com controles simples, quando Pagination completo e excessivo.

---

## TruncateText

Truncamento de texto com line-clamp responsivo e fade opcional.

**Props:** `value` (numero de linhas ou array responsivo), `fade` (md), `asChild`

```tsx
import { TruncateText } from '@farol-ds/react'

// Truncar em 2 linhas
<TruncateText value={2}>
  Texto muito longo que sera cortado...
</TruncateText>

// Responsivo: 2 linhas mobile, 3 desktop
<TruncateText value={[2, 2, 3, 3, 4]}>
  Texto adaptativo por breakpoint...
</TruncateText>

// Com fade gradient
<TruncateText value={3} fade="md">
  Texto com gradiente de desaparecimento...
</TruncateText>
```

**Quando usar:** Cards de resultado de busca, previews de artigos, descricoes em listas. Use `fade` para texto longo onde elipsis nao fica bom.

---

## RichText

Wrapper CSS para conteudo HTML rico (editor, CMS, markdown renderizado).

```tsx
import { RichText } from '@farol-ds/react'

// Conteudo de artigo juridico
<RichText>
  <div dangerouslySetInnerHTML={{ __html: articleContent }} />
</RichText>

// Como classe CSS (fora do React)
import { richTextStyles } from '@farol-ds/react'
<div className={richTextStyles.richtext}>{/* HTML */}</div>
```

**Quando usar:** Artigos juridicos, conteudo de doutrina, output de editor rich text, markdown renderizado.

---

## List

Lista semantica com estilo resetado por padrao.

**Props:** `unstyled` (default true), `asChild`
**Subcomponentes:** Item

```tsx
import { List } from '@farol-ds/react'

<List>
  <List.Item>Item 1</List.Item>
  <List.Item>Item 2</List.Item>
</List>

// Com estilo customizado
<List unstyled={false}>
  <List.Item>Item com bullet</List.Item>
</List>
```

**Quando usar:** Estrutura semantica de listas, base para componentes de lista customizados. Produto real usa em FAQs e queries.

---

## Illustration

Wrapper para ilustracoes SVG com tamanhos padronizados. 60+ ilustracoes pre-feitas.

**Props:** `size` (sm/md/lg)

```tsx
import { BulbIllu, DocFlatIllu, PaymentSucceededIllu } from '@farol-ds/react'

// Estado vazio
<BulbIllu size="lg" />

// Sucesso de pagamento
<PaymentSucceededIllu size="md" />
```

**Quando usar:** Empty states, paginas de sucesso/erro, onboarding, walkthroughs. Tamanhos: sm para inline, md para secoes, lg para paginas inteiras.

---

## Overlay

Backdrop semi-transparente para modais e drawers. Gerencia animacao de entrada.

**Props:** `visible`, `disableEnterAnimation`

```tsx
import { Overlay } from '@farol-ds/react'

<Overlay visible={isModalOpen} />
```

**Quando usar:** Componente interno - usado automaticamente por Modal, Drawer, etc. Raramente instanciado diretamente.
