# Farol DS — Padrões de Layout e Templates de Página

## Templates de Página

---

### 1. Dashboard (Visão Geral)

```
┌─────────────────────────────────────────┐
│ HEADER (sticky, h-16, border-b)          │
├──────────┬──────────────────────────────┤
│ SIDEBAR  │ MAIN CONTENT                 │
│ w-64     │  ┌─────────────────────────┐ │
│ (lg+)    │  │ Page Header              │ │
│          │  │ (título + ações)         │ │
│ nav      │  ├─────────────────────────┤ │
│ items    │  │ Métricas (grid 4 cols)   │ │
│          │  ├─────────────────────────┤ │
│          │  │ Tabela / Lista           │ │
│          │  └─────────────────────────┘ │
└──────────┴──────────────────────────────┘
```

```tsx
// Layout base do dashboard
<div className="min-h-screen bg-background flex flex-col">
  {/* Header */}
  <header className="sticky top-0 z-50 h-16 border-b border-border bg-background/95 backdrop-blur flex items-center px-6 gap-4">
    <span className="text-xl font-bold text-primary">Jusbrasil</span>
    {/* nav, avatar, etc */}
  </header>

  <div className="flex flex-1">
    {/* Sidebar */}
    <aside className="hidden lg:flex w-64 flex-col border-r border-border bg-card p-4 gap-1">
      {navItems.map(item => (
        <a key={item.href} href={item.href}
          className={`flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm font-semibold transition-colors ${item.active ? 'bg-primary/10 text-primary' : 'text-muted-foreground hover:bg-muted hover:text-foreground'}`}>
          <item.icon className="w-5 h-5" aria-hidden />
          {item.label}
        </a>
      ))}
    </aside>

    {/* Main Content */}
    <main className="flex-1 p-6 lg:p-8 overflow-auto">
      {/* Page Header */}
      <div className="flex items-center justify-between mb-8">
        <div>
          <h1 className="text-[28px] font-bold text-foreground">Dashboard</h1>
          <p className="text-sm text-muted-foreground mt-1">Visão geral dos seus processos</p>
        </div>
        <button className="bg-primary text-primary-foreground ...">Nova ação</button>
      </div>

      {/* Metrics Grid */}
      <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 mb-8">
        {metrics.map(m => <MetricCard key={m.label} {...m} />)}
      </div>

      {/* Content */}
      {/* tabela, lista, etc */}
    </main>
  </div>
</div>
```

---

### 2. Listagem / Resultados de Busca

```
┌─────────────────────────────────────────┐
│ Page Header (título + contador + filtros) │
├─────────────────────────────────────────┤
│ Barra de busca + filtros ativos          │
├─────────────────────────────────────────┤
│ ┌─────────────────────────────────────┐ │
│ │ Card de resultado 1                  │ │
│ │ Card de resultado 2                  │ │
│ │ Card de resultado 3                  │ │
│ └─────────────────────────────────────┘ │
│ Paginação                                │
└─────────────────────────────────────────┘
```

```tsx
<main className="max-w-4xl mx-auto px-4 py-8">
  {/* Page Header */}
  <div className="flex items-center justify-between mb-6">
    <div>
      <h1 className="text-[28px] font-bold text-foreground">Meus Processos</h1>
      <p className="text-sm text-muted-foreground mt-1">{total} processos encontrados</p>
    </div>
    <button className="bg-primary text-primary-foreground ...">Acompanhar novo</button>
  </div>

  {/* Search & Filters */}
  <div className="flex gap-3 mb-6">
    <div className="flex-1 relative">
      <Search className="absolute left-3 top-1/2 -translate-y-1/2 w-4 h-4 text-muted-foreground" aria-hidden />
      <input className="w-full pl-9 pr-4 py-2.5 rounded-lg border border-border bg-background text-base ..." placeholder="Buscar por número, tribunal..." />
    </div>
    <button className="flex items-center gap-2 px-4 py-2.5 border border-border rounded-lg text-sm font-semibold text-foreground hover:bg-muted">
      <Filter className="w-4 h-4" /> Filtros {activeFilters > 0 && <span className="...">{activeFilters}</span>}
    </button>
  </div>

  {/* Active filters */}
  {chips.length > 0 && (
    <div className="flex flex-wrap gap-2 mb-4">
      {chips.map(chip => (
        <span key={chip} className="flex items-center gap-1 px-3 py-1 bg-primary/10 text-primary text-xs font-semibold rounded-full">
          {chip} <button onClick={() => removeFilter(chip)} aria-label={`Remover filtro ${chip}`}><X className="w-3 h-3" /></button>
        </span>
      ))}
    </div>
  )}

  {/* Results */}
  <div className="flex flex-col gap-3">
    {loading ? (
      Array.from({length: 5}).map((_, i) => <SkeletonCard key={i} />)
    ) : results.length === 0 ? (
      <EmptyState />
    ) : (
      results.map(item => <ProcessCard key={item.id} {...item} />)
    )}
  </div>

  {/* Pagination */}
  {totalPages > 1 && (
    <div className="flex justify-center mt-8">
      <Pagination count={totalPages} page={currentPage} onPageChange={setPage} />
    </div>
  )}
</main>
```

---

### 3. Tela de Detalhe (Processo / Documento)

```
┌─────────────────────────────────────────┐
│ Breadcrumb                               │
│ Page Header (número + status + ações)    │
├──────────────────────┬──────────────────┤
│ CONTEÚDO PRINCIPAL   │ SIDEBAR DETALHE  │
│ (tabs: Movimentações,│ (partes, tribunal,│
│  Documentos, Partes) │ advogados, datas) │
└──────────────────────┴──────────────────┘
```

```tsx
<main className="max-w-6xl mx-auto px-4 py-8">
  <Breadcrumb /> {/* Home > Processos > Número */}

  {/* Page Header */}
  <div className="flex flex-col lg:flex-row lg:items-center justify-between gap-4 mt-4 mb-8">
    <div>
      <div className="flex items-center gap-3 mb-2">
        <h1 className="text-2xl font-bold text-foreground font-mono">{processNumber}</h1>
        <StatusBadge status={status} />
      </div>
      <p className="text-sm text-muted-foreground">{court}</p>
    </div>
    <div className="flex gap-3">
      <button className="border-2 border-secondary text-secondary ...">Acompanhar</button>
      <button className="bg-primary text-primary-foreground ...">Ver documentos</button>
    </div>
  </div>

  {/* Layout 2 colunas */}
  <div className="grid grid-cols-1 lg:grid-cols-[1fr_320px] gap-6">
    {/* Main: Tabs */}
    <div className="bg-card border border-border rounded-2xl overflow-hidden" style={{boxShadow: 'var(--shadow-2)'}}>
      <Tabs>
        <Tabs.List items={['Movimentações', 'Documentos', 'Partes']} />
        <Tabs.Content>...</Tabs.Content>
      </Tabs>
    </div>

    {/* Sidebar */}
    <div className="flex flex-col gap-4">
      <DetailCard title="Partes" items={parties} />
      <DetailCard title="Advogados" items={lawyers} />
      <DetailCard title="Datas importantes" items={dates} />
    </div>
  </div>
</main>
```

---

### 4. Formulário / Cadastro

```tsx
<div className="min-h-screen bg-muted flex items-center justify-center p-4">
  <div className="w-full max-w-lg bg-card rounded-2xl p-10" style={{boxShadow: 'var(--shadow-2)'}}>
    {/* Logo */}
    <div className="mb-8 flex flex-col gap-2">
      <span className="text-2xl font-bold text-primary">Jusbrasil</span>
      <h1 className="text-2xl font-bold text-foreground">Crie sua conta</h1>
      <p className="text-sm text-muted-foreground">Acesse gratuitamente informações jurídicas</p>
    </div>

    <form className="flex flex-col gap-5">
      <FormControl id="name" label="Nome completo" required>
        <Input id="name" type="text" placeholder="Seu nome" />
      </FormControl>

      <FormControl id="email" label="E-mail" required>
        <Input id="email" type="email" placeholder="seu@email.com" />
      </FormControl>

      <FormControl id="password" label="Senha" required>
        <Input id="password" type="password" placeholder="Mínimo 8 caracteres" />
      </FormControl>

      <div className="flex items-start gap-3">
        <Checkbox id="terms" />
        <label htmlFor="terms" className="text-sm text-foreground">
          Aceito os <Link href="/termos">termos de uso</Link> e a <Link href="/privacidade">política de privacidade</Link>
        </label>
      </div>

      <Button type="submit" kind="primary" block loading={loading}>
        Criar conta
      </Button>
    </form>

    <p className="mt-6 text-center text-sm text-muted-foreground">
      Já tem conta? <Link href="/login" type="primary">Entrar</Link>
    </p>
  </div>
</div>
```

---

### 5. Página de Autenticação / Login

Ver example em `neutral-examples.md` do styleguide. Estrutura:
- Card centralizado `max-w-[400px]`
- Logo Jusbrasil no topo
- FormControl + Input + ErrorMessage
- Button `kind="primary" block`
- Link "Esqueci minha senha"
- Link "Criar conta"

---

## Padrões de UI Jusbrasil

### Card de Processo

```tsx
interface ProcessCardProps {
  processNumber: string  // "0001234-56.2023.8.26.0100"
  court: string          // "TJSP — 1ª Vara Cível"
  parties: { role: 'Autor'|'Réu'; name: string }[]
  status: 'Em andamento'|'Arquivado'|'Suspenso'|'Encerrado'|'Aguardando'
  lastUpdate?: string    // "03/03/2026"
  onViewDetails?: () => void
  onFollow?: () => void
  isFollowing?: boolean
}
```

Estrutura visual:
```
┌────────────────────────────────────┐
│ Número processo         [BADGE]    │
│ Tribunal                           │
├────────────────────────────────────┤
│ AUTOR   Nome da parte autora       │
│ RÉU     Nome da parte ré           │
├────────────────────────────────────┤
│ [Ver detalhes]  [Acompanhar]       │
└────────────────────────────────────┘
```

### Card de Documento

```tsx
interface DocumentCardProps {
  title: string
  type: 'Petição'|'Sentença'|'Despacho'|'Acórdão'|'Intimação'|string
  date: string
  processNumber?: string
  fileSize?: string
  onView?: () => void
  onDownload?: () => void
}
```

Estrutura visual:
```
┌────────────────────────────────────┐
│ [PDF ícone]  Título do documento   │
│              Tipo · Data · Tamanho │
├────────────────────────────────────┤
│               [Visualizar] [↓ PDF] │
└────────────────────────────────────┘
```

### Tabela de Movimentações

```tsx
// Listagem vertical de movimentações de processo (timeline)
<div className="divide-y divide-border">
  {movimentacoes.map(mov => (
    <div key={mov.id} className="flex gap-4 py-4">
      {/* Timeline dot */}
      <div className="flex flex-col items-center gap-1 pt-1">
        <div className="w-2 h-2 rounded-full bg-primary flex-shrink-0" />
        <div className="w-px flex-1 bg-border" />
      </div>
      {/* Content */}
      <div className="flex-1 pb-2">
        <div className="flex items-start justify-between gap-4">
          <p className="text-sm font-semibold text-foreground">{mov.descricao}</p>
          <span className="text-xs text-muted-foreground whitespace-nowrap">{mov.data}</span>
        </div>
        {mov.detalhes && <p className="text-sm text-muted-foreground mt-1">{mov.detalhes}</p>}
      </div>
    </div>
  ))}
</div>
```

### Card de Métrica (Dashboard)

```tsx
interface MetricCardProps {
  label: string       // "Processos ativos"
  value: string       // "42"
  change?: string     // "+3 este mês"
  trend?: 'up'|'down'|'neutral'
  icon?: React.ComponentType
}

<div className="bg-card border border-border rounded-2xl p-6" style={{boxShadow: 'var(--shadow-1)'}}>
  <div className="flex items-center justify-between mb-4">
    <span className="text-sm font-semibold text-muted-foreground">{label}</span>
    {icon && <div className="w-9 h-9 rounded-lg bg-primary/10 flex items-center justify-center">
      <Icon className="w-5 h-5 text-primary" aria-hidden />
    </div>}
  </div>
  <p className="text-[32px] font-bold text-foreground leading-none">{value}</p>
  {change && <p className={`text-xs font-semibold mt-2 ${trend === 'up' ? 'text-[#669337]' : trend === 'down' ? 'text-destructive' : 'text-muted-foreground'}`}>
    {change}
  </p>}
</div>
```

### Empty State

```tsx
<div className="flex flex-col items-center justify-center py-16 px-4 text-center">
  <div className="w-16 h-16 rounded-2xl bg-muted flex items-center justify-center mb-4">
    <FolderOpen className="w-8 h-8 text-muted-foreground" aria-hidden />
  </div>
  <h3 className="text-lg font-bold text-foreground mb-2">Nenhum processo encontrado</h3>
  <p className="text-sm text-muted-foreground max-w-sm mb-6">
    Você ainda não está acompanhando nenhum processo. Comece buscando pelo número.
  </p>
  <button className="bg-primary text-primary-foreground ...">Buscar processo</button>
</div>
```

### Error State

```tsx
<div className="flex flex-col items-center justify-center py-16 px-4 text-center">
  <div className="w-16 h-16 rounded-2xl bg-destructive/10 flex items-center justify-center mb-4">
    <AlertCircle className="w-8 h-8 text-destructive" aria-hidden />
  </div>
  <h3 className="text-lg font-bold text-foreground mb-2">Erro ao carregar</h3>
  <p className="text-sm text-muted-foreground max-w-sm mb-6">
    Não foi possível carregar os dados. Tente novamente.
  </p>
  <button onClick={retry} className="border border-border rounded-lg ...">Tentar novamente</button>
</div>
```

### Loading State (Skeleton)

```tsx
// Skeleton de card de processo
<div className="bg-card border border-border rounded-2xl p-6 animate-pulse">
  <div className="flex justify-between mb-4">
    <div className="h-5 bg-muted rounded w-2/3" />
    <div className="h-5 bg-muted rounded w-20" />
  </div>
  <div className="h-3 bg-muted rounded w-1/2 mb-6" />
  <div className="space-y-2 mb-6">
    <div className="h-3 bg-muted rounded w-3/4" />
    <div className="h-3 bg-muted rounded w-2/3" />
  </div>
  <div className="flex gap-3">
    <div className="h-10 bg-muted rounded-lg flex-1" />
    <div className="h-10 bg-muted rounded-lg flex-1" />
  </div>
</div>
```

---

## Padrões de UI Reais (produto Jusbrasil)

Estes padrões foram extraídos do produto real — use-os como referência fiel.

### Header — não autenticado

```
┌──────────────────────────────────────────────────────────┐
│  [Logo Jusbrasil]                    [Cadastre-se] [Entrar] │
└──────────────────────────────────────────────────────────┘
```

```tsx
// Header não-autenticado (landing pages, páginas públicas)
<header className="h-16 border-b border-border bg-background flex items-center px-6 justify-between">
  <a href="/" aria-label="Jusbrasil — Página inicial">
    {/* SVG do logo — ver assets/logos.md */}
    <JusbrasilLogo height={32} />
  </a>
  <div className="flex items-center gap-2">
    <a href="/cadastro" className="inline-flex items-center justify-center h-9 px-4 rounded-full border border-border text-sm font-semibold text-foreground hover:bg-muted transition-colors">
      Cadastre-se
    </a>
    <a href="/login" className="inline-flex items-center justify-center h-9 px-4 rounded-full border border-border text-sm font-semibold text-foreground hover:bg-muted transition-colors">
      Entrar
    </a>
  </div>
</header>
```

### Header — autenticado (com busca global e Jus IA)

```
┌───────────────────────────────────────────────────────────────┐
│ [Logo]  [Todos v  |  Pesquisar no Jusbrasil          🔍]  [Jus IA] [Avatar v] │
└───────────────────────────────────────────────────────────────┘
         ↓ Segunda linha (nav secundária):
│ Para você | Consulta processual | Jurisprudência | Jus IA | Doutrina | … │
```

```tsx
// Header autenticado
<header className="border-b border-border bg-background">
  {/* Linha principal */}
  <div className="h-14 flex items-center gap-4 px-6 max-w-[1280px] mx-auto">
    <a href="/" aria-label="Jusbrasil"><JusbrasilLogo height={28} /></a>

    {/* Busca global — pill com seletor */}
    <div className="flex-1 max-w-xl flex items-center h-10 bg-muted rounded-full border border-transparent focus-within:border-primary focus-within:bg-background transition-colors">
      <div className="flex items-center gap-1 pl-4 pr-3 border-r border-border">
        <span className="text-sm font-medium text-foreground">Todos</span>
        <ChevronDown className="w-3.5 h-3.5 text-muted-foreground" aria-hidden />
      </div>
      <input
        type="search"
        className="flex-1 bg-transparent px-3 text-sm text-foreground placeholder:text-muted-foreground outline-none min-w-0"
        placeholder="Pesquisar no Jusbrasil"
        aria-label="Pesquisar no Jusbrasil"
      />
      <button className="pr-4 text-muted-foreground hover:text-foreground" aria-label="Pesquisar">
        <Search className="w-4 h-4" aria-hidden />
      </button>
    </div>

    {/* Jus IA + Avatar */}
    <div className="flex items-center gap-3 ml-auto">
      <a href="/jus-ia" className="inline-flex items-center gap-2 bg-primary text-primary-foreground font-semibold text-sm rounded-full px-4 h-9 hover:bg-primary/90 transition-colors">
        <JusIASymbol height={18} /> {/* Só o símbolo — ver assets/logos.md */}
        Jus IA
      </a>
      <button className="flex items-center gap-1.5" aria-label="Menu do usuário" aria-haspopup="menu">
        <span className="w-8 h-8 rounded-full overflow-hidden bg-muted">
          <img src={user.avatar} alt={user.name} className="w-full h-full object-cover" />
        </span>
        <ChevronDown className="w-3.5 h-3.5 text-muted-foreground" aria-hidden />
      </button>
    </div>
  </div>

  {/* Nav secundária (só em páginas internas) */}
  <nav className="h-10 flex items-center gap-1 px-6 border-t border-border max-w-[1280px] mx-auto" aria-label="Navegação de conteúdo">
    {navItems.map(item => (
      <a key={item.href} href={item.href}
        className={`px-3 h-full flex items-center text-sm font-medium transition-colors border-b-2 ${item.active ? 'text-primary border-primary' : 'text-foreground border-transparent hover:text-primary'}`}
        aria-current={item.active ? 'page' : undefined}>
        {item.label}
      </a>
    ))}
  </nav>
</header>
```

### Toggle de modo / seletor de aba (pill)

Padrão usado para "Consultar Processo | Pesquisa Jurídica", "Pesquisa Jusbrasil | Modo Jus IA", etc.

```tsx
// Toggle pill — ativo: fundo escuro, inativo: borda neutra
<div className="inline-flex items-center p-1 bg-background border border-border rounded-full" role="tablist">
  <button
    role="tab"
    aria-selected={active === 'processo'}
    onClick={() => setActive('processo')}
    className={`px-4 py-1.5 rounded-full text-sm font-semibold transition-all ${
      active === 'processo'
        ? 'bg-foreground text-background shadow-sm'
        : 'text-muted-foreground hover:text-foreground'
    }`}
  >
    Consultar Processo
  </button>
  <button
    role="tab"
    aria-selected={active === 'pesquisa'}
    onClick={() => setActive('pesquisa')}
    className={`px-4 py-1.5 rounded-full text-sm font-semibold transition-all ${
      active === 'pesquisa'
        ? 'bg-foreground text-background shadow-sm'
        : 'text-muted-foreground hover:text-foreground'
    }`}
  >
    Pesquisa Jurídica
  </button>
</div>
```

### Barra de busca — pill (homepage e páginas de conteúdo)

```tsx
// Search pill — estilo real do Jusbrasil
<div className="flex items-center h-14 bg-muted rounded-full px-6 focus-within:bg-background focus-within:border focus-within:border-primary transition-all max-w-2xl">
  <input
    type="search"
    className="flex-1 bg-transparent text-base text-foreground placeholder:text-muted-foreground outline-none"
    placeholder="Digite um CPF, CNPJ, nome ou número do processo"
    aria-label="Buscar processos"
  />
  <button className="w-10 h-10 rounded-full bg-muted-foreground/20 flex items-center justify-center hover:bg-primary hover:text-white transition-colors" aria-label="Pesquisar">
    <Search className="w-4 h-4" aria-hidden />
  </button>
</div>
```

### Card de processo — estilo real

Padrão do produto: número + **Autor x Réu** em negrito + tribunal + classe/assunto + botão "Ver processo".

```tsx
<article className="bg-background border border-border rounded-2xl p-6 hover:border-primary/30 transition-colors">
  {/* Número */}
  <p className="text-xs text-muted-foreground mb-1">Processo nº {process.number}</p>

  {/* Partes — bold com "x" separador em cor */}
  <h3 className="text-base font-bold text-foreground mb-3 leading-snug">
    {process.plaintiff} <span className="text-primary font-bold">x</span> {process.defendant}
  </h3>

  {/* Metadados com ícones */}
  <div className="flex flex-col gap-1.5 mb-4">
    <div className="flex items-center gap-2 text-sm text-muted-foreground">
      <Building2 className="w-4 h-4 flex-shrink-0" aria-hidden />
      <span>{process.court} · {process.city}</span>
    </div>
    <div className="flex items-center gap-2 text-sm text-muted-foreground">
      <Scale className="w-4 h-4 flex-shrink-0" aria-hidden />
      <span className="line-clamp-1">{process.subject}</span>
    </div>
  </div>

  {/* Ação */}
  <button className="inline-flex items-center gap-2 h-9 px-4 rounded-full border border-border text-sm font-semibold text-foreground hover:bg-muted transition-colors">
    <Eye className="w-4 h-4" aria-hidden />
    Ver processo
  </button>
</article>
```

### Sidebar de navegação interna (autenticado)

```tsx
<aside className="w-56 flex-shrink-0">
  <nav aria-label="Navegação lateral">
    {navItems.map(item => (
      <a key={item.href} href={item.href}
        className={`flex items-center gap-3 px-3 py-2.5 rounded-xl text-sm font-medium transition-colors mb-0.5 ${
          item.active
            ? 'bg-primary/10 text-primary font-semibold'
            : 'text-foreground hover:bg-muted'
        }`}
        aria-current={item.active ? 'page' : undefined}>
        <item.icon className="w-4 h-4" aria-hidden />
        <span className="flex-1">{item.label}</span>
        {item.active && <Check className="w-4 h-4 text-primary" aria-hidden />}
      </a>
    ))}
  </nav>
</aside>
```

### Chips de filtro (resultado de busca)

```tsx
// Filtros horizontais — pill com active escuro
<div className="flex flex-wrap gap-2" role="group" aria-label="Filtrar resultados por tipo">
  {filters.map(f => (
    <button
      key={f.value}
      onClick={() => setFilter(f.value)}
      aria-pressed={filter === f.value}
      className={`h-8 px-4 rounded-full text-sm font-semibold border transition-all ${
        filter === f.value
          ? 'bg-foreground text-background border-foreground'
          : 'bg-background text-foreground border-border hover:border-foreground'
      }`}
    >
      {f.label}
    </button>
  ))}
</div>
// Filtros: Todos · Consulta Processual · Jurisprudência · Doutrina · Artigos e Notícias · Diários Oficiais · Peças Processuais · Modelos · Legislação
```

### Resultado de busca de conteúdo (jurisprudência, doutrina, modelos)

```tsx
<article className="py-4 border-b border-border last:border-0">
  {/* Categoria + data */}
  <p className="text-xs text-muted-foreground mb-1">
    {result.category} • publicado em {result.date} • por{' '}
    <a href={result.authorUrl} className="text-primary hover:underline">{result.author}</a>
  </p>

  {/* Título — link verde */}
  <a href={result.url} className="text-base font-semibold text-primary hover:underline leading-snug block mb-2">
    {result.title}
  </a>

  {/* Trecho com destaques em negrito */}
  <p className="text-sm text-foreground leading-relaxed line-clamp-3"
    dangerouslySetInnerHTML={{ __html: result.excerpt }} />
  {/* excerpt usa <strong> para realçar termos buscados */}
</article>
```

### Detalhe de processo — tela completa

```
┌─────────────────────────────────────┬──────────────────────┐
│ ← Voltar                    🔔  ⋮   │  Documentos anexos   │
│                                      │  [Despacho  ↓]       │
│ G. T. R. x A. D. P.                 │  [Certidão  ↓]       │
│ 🏛 TRT10 · Brasília, DF   Nº …      │  [Intimação ↓]       │
│                                      │  ...                 │
│ ┌──────────────────────────────────┐ │  [Mostrar mais]      │
│ │ Situação do processo              │ │                      │
│ │ Uma possível explicação...        │ │  Documentos do       │
│ │ [Verificar situação] [Próximos…]  │ │  processo            │
│ └──────────────────────────────────┘ │  ○ Despacho  >       │
│                                      │  ○ Sentença  >       │
│ Pergunte e entenda                   │  ○ Decisão   >       │
│ ✓ Entenda os próximos passos         └──────────────────────┘
│ ✓ Descubra o prazo
│ [Fazer pergunta]
│
│ ⊙ Histórico  ↓
│ Todas as informações publicadas…
```

```tsx
// Layout principal do detalhe de processo
<div className="max-w-[1280px] mx-auto px-6 py-6 grid grid-cols-1 lg:grid-cols-[1fr_340px] gap-8">
  {/* Coluna principal */}
  <main>
    {/* Voltar + ações */}
    <div className="flex items-center justify-between mb-6">
      <a href="/processos" className="flex items-center gap-1.5 text-sm font-semibold text-primary hover:underline">
        <ArrowLeft className="w-4 h-4" /> Voltar
      </a>
      <div className="flex items-center gap-3">
        <button aria-label="Ativar alertas"><Bell className="w-5 h-5 text-muted-foreground" /></button>
        <button aria-label="Mais opções"><MoreVertical className="w-5 h-5 text-muted-foreground" /></button>
      </div>
    </div>

    {/* Título */}
    <h1 className="text-2xl font-bold text-foreground mb-2">{process.title}</h1>
    <div className="flex items-center gap-4 text-sm text-muted-foreground mb-6">
      <span className="flex items-center gap-1.5"><Building2 className="w-4 h-4" />{process.court} · {process.city}</span>
      <span>Nº · <a href="#" className="text-primary hover:underline">{process.number}</a></span>
    </div>

    {/* Card "Situação do processo" (Jus IA) */}
    <div className="border border-border rounded-2xl p-6 mb-6">
      <h2 className="text-base font-bold text-foreground mb-2">Situação do processo</h2>
      <p className="text-sm text-muted-foreground mb-4">{aiSummary}</p>
      <div className="flex gap-3">
        <button className="h-10 px-5 bg-primary text-primary-foreground rounded-full text-sm font-semibold hover:bg-primary/90 transition-colors">
          Verificar situação
        </button>
        <button className="h-10 px-5 border border-border rounded-full text-sm font-semibold text-foreground hover:bg-muted transition-colors">
          Próximos passos do processo
        </button>
      </div>
    </div>

    {/* Seção "Pergunte e entenda" */}
    <section className="mb-6">
      <h2 className="text-lg font-bold text-foreground mb-1">Pergunte e entenda</h2>
      <p className="text-sm text-muted-foreground mb-4">
        Tire suas dúvidas e acesse respostas <strong>rápidas e específicas</strong> para o seu caso.
      </p>
      <ul className="flex flex-col gap-2 mb-4 text-sm text-foreground">
        {['Entenda os próximos passos do processo', 'Descubra o prazo do próximo acontecimento', 'Faça qualquer pergunta sobre o processo'].map(item => (
          <li key={item} className="flex items-center gap-2">
            <Check className="w-4 h-4 text-primary flex-shrink-0" /> {item}
          </li>
        ))}
      </ul>
      <button className="h-9 px-4 border border-border rounded-full text-sm font-semibold text-foreground hover:bg-muted transition-colors">
        Fazer pergunta
      </button>
    </section>
  </main>

  {/* Sidebar — Documentos */}
  <aside>
    <h2 className="text-base font-bold text-foreground mb-4">Documentos anexos</h2>
    <div className="flex flex-col gap-2">
      {documents.map(doc => (
        <div key={doc.id} className="flex items-center justify-between p-4 border border-border rounded-xl hover:bg-muted transition-colors">
          <div className="flex items-center gap-3">
            <div className="w-8 h-8 flex items-center justify-center">
              <FileText className="w-5 h-5 text-destructive" aria-hidden />
            </div>
            <div>
              <p className="text-sm font-semibold text-foreground">{doc.type}</p>
              <p className="text-xs text-muted-foreground">{doc.date}</p>
            </div>
          </div>
          <button aria-label={`Baixar ${doc.type}`}><Download className="w-4 h-4 text-muted-foreground hover:text-foreground" /></button>
        </div>
      ))}
    </div>
  </aside>
</div>
```

---

## Padrões de Navegação

### Sidebar Nav Item (ativo/inativo)

```tsx
const navItem = {
  active:   "bg-primary/10 text-primary font-semibold",
  inactive: "text-muted-foreground hover:bg-muted hover:text-foreground font-semibold",
}

<a href={item.href} className={`flex items-center gap-3 px-3 py-2.5 rounded-lg text-sm transition-colors ${item.active ? navItem.active : navItem.inactive}`}
  aria-current={item.active ? 'page' : undefined}>
  <item.icon className="w-5 h-5 flex-shrink-0" aria-hidden />
  {item.label}
  {item.badge && <span className="ml-auto text-xs bg-primary text-primary-foreground rounded-full px-1.5 py-0.5">{item.badge}</span>}
</a>
```

### Header com busca global

```tsx
<header className="sticky top-0 z-50 h-16 bg-background/95 backdrop-blur border-b border-border">
  <div className="max-w-[1280px] mx-auto h-full flex items-center gap-4 px-6">
    {/* Logo */}
    <a href="/" className="text-xl font-bold text-primary flex-shrink-0">Jusbrasil</a>

    {/* Busca global */}
    <div className="flex-1 max-w-xl relative">
      <Search className="absolute left-3 top-1/2 -translate-y-1/2 w-4 h-4 text-muted-foreground" aria-hidden />
      <input className="w-full pl-9 pr-4 py-2 rounded-lg border border-border bg-muted text-sm focus:bg-background focus:border-primary focus:ring-2 focus:ring-primary/20 transition-colors outline-none" placeholder="Buscar processos, tribunais..." />
    </div>

    {/* Ações do header */}
    <div className="flex items-center gap-2">
      <button aria-label="Notificações" className="relative w-10 h-10 flex items-center justify-center rounded-lg hover:bg-muted">
        <Bell className="w-5 h-5 text-foreground" />
        {notifs > 0 && <span className="absolute top-1.5 right-1.5 w-2 h-2 rounded-full bg-primary" />}
      </button>
      <Avatar src={user.avatar} fallback={user.initials} size="md" />
    </div>
  </div>
</header>
```

---

## Dados Mock para Protótipos

```tsx
// Processos
const mockProcessos = [
  { id: '1', number: '0001234-56.2023.8.26.0100', court: 'TJSP — 1ª Vara Cível de São Paulo', status: 'Em andamento', plaintiff: 'João da Silva Santos', defendant: 'Empresa ABC Ltda.', lastUpdate: '03/03/2026' },
  { id: '2', number: '0002345-67.2022.4.03.6100', court: 'TRF 3ª Região — 5ª Turma', status: 'Aguardando', plaintiff: 'Maria Oliveira', defendant: 'Instituto Nacional do Seguro Social (INSS)', lastUpdate: '28/02/2026' },
  { id: '3', number: '0003456-78.2021.8.19.0001', court: 'TJRJ — 3ª Vara Cível', status: 'Suspenso', plaintiff: 'Carla Mendes', defendant: 'Banco Bradesco S.A.', lastUpdate: '15/01/2026' },
]

// Métricas de dashboard
const mockMetrics = [
  { label: 'Processos ativos', value: '42', change: '+3 este mês', trend: 'up' },
  { label: 'Documentos novos', value: '18', change: '+7 esta semana', trend: 'up' },
  { label: 'Audiências', value: '5', change: 'Próxima em 3 dias', trend: 'neutral' },
  { label: 'Prazo vencendo', value: '2', change: 'Ação necessária', trend: 'down' },
]

// Movimentações
const mockMovimentacoes = [
  { id: '1', descricao: 'Despacho proferido', detalhes: 'Cite-se o réu para responder em 15 dias.', data: '03/03/2026' },
  { id: '2', descricao: 'Petição inicial distribuída', data: '15/01/2026' },
  { id: '3', descricao: 'Processo recebido pela vara', data: '10/01/2026' },
]

// Usuário
const mockUser = {
  name: 'Dr. Carlos Eduardo',
  email: 'carlos.eduardo@escritorio.adv.br',
  initials: 'CE',
  role: 'Advogado',
}
```
