# Blocks - Referencia Visual de Componentes Compostos

Blocos HTML prontos em `blocks/` que servem como referencia visual para prototipacao. Cada arquivo e auto-contido (HTML + CSS inline + tokens Farol). Use como guia de estilo ao construir paginas completas.

---

## Catalogo de Blocks

### block-topbar.html
**Topbar / Header de navegacao**

3 variacoes da barra de topo do produto:
1. **Deslogado** - Logo Jusbrasil + nav links (Seus Direitos, Profissionais, Empresas) + botoes "Entrar" (secondary) e "Criar conta" (primary)
2. **Logado com nav** - Logo + nav + busca + icones (sino, menu) + avatar do usuario
3. **Logado sem nav** - Logo + busca integrada no header + avatar (layout mais compacto, ex: Jus IA)

Inclui botao "Jus IA" com logo colorido sobre fundo escuro (`--foreground`) para contraste. Sticky top com `z-index: 50`, altura 64px.

**Quando usar:** Toda pagina que precise de header de navegacao.

---

### block-sidebar.html
**Sidebar do Jus IA**

Sidebar esquerda do chat Jus IA (280px largura, 720px altura):
- Header: logo colorido Jus IA + texto "Jus IA" + botao hamburguer
- Nav: "Nova conversa" (icone edit) + "Buscar em conversas" (icone search)
- Botao "+ Novo caso" (secondary, bordered)
- Lista de casos com icone de pasta (truncados)
- "Mais casos" com chevron
- Separador
- "Ultimas conversas" - lista com item ativo (bg muted), texto truncado
- Footer: avatar com iniciais, nome, role "Assinante", dot verde de status, menu three-dot

**Quando usar:** Telas do Jus IA que precisem de painel lateral de navegacao de conversas/casos.

---

### block-chat.html
**Interface de chat do Jus IA**

Chat simplificado seguindo o produto real:
- **Mensagem do usuario**: bolha cinza alinhada a direita (`.msg-user`), sem avatar
- **Resposta da IA**: sem bolha, alinhada a esquerda com:
  - Label "Resposta" verde (`.msg-ai-label`)
  - Indicador de ferramenta: "Usou: busca juridica no Jusbrasil" com checkmark (`.msg-ai-tool`)
  - Corpo em markdown (h3, strong, em, ul, p) no `.msg-ai-body`
  - Botoes de acao: thumbs up, thumbs down, copiar
- **Input area**: campo de texto + toolbar com:
  - Botao "+" (`.chat-tool-btn`)
  - Chip "Pesquisa fundamentada" com icone sparkle (`.chat-chip-btn`)
  - Botao microfone
  - Botao enviar (seta para cima, fundo primary)

**Quando usar:** Interfaces de chat com IA, conversas Jus IA.

---

### block-serp-processes.html
**Listagem de processos + SERP de jurisprudencia**

2 secoes:
1. **Listagem de processos** - Cards com numero CNJ, titulo (partes), meta (tribunal + area), botao "Ver processo" (tertiary). Cards com borda `--card-border`, hover verde.
2. **SERP jurisprudencia** - Titulo "Jurisprudencia sobre [termo]" + barra de filtros pill (ChipClickable pattern: pill shape, active = fundo escuro) + chip especial "Teses principais" (fundo primary com logo Jus IA) + botao "Reordenar" + resultados com tribunal linkado, titulo verde clicavel, excerpt com highlight bold no termo buscado, line-clamp 3 linhas.

**Quando usar:** Paginas de busca, listagens de processos, resultados de pesquisa juridica.

---

### block-autocomplete.html
**Busca com autocomplete e filtros**

3 demonstracoes:
1. **Search com historico** - Input com borda primary, icone lupa + botao buscar. Dropdown com secao "Buscas recentes" (icone relogio) + "Sugestoes" (icone lupa). Items com hover muted.
2. **Autocomplete de tribunal** - Input menor com dropdown de tribunais (STF, STJ, TJ-SP, etc.), cada item com nome + sigla.
3. **Filtros dropdown** - Row de botoes dropdown (Tribunal, Data, Tipo) que abrem listas de opcoes com checkboxes (static para demo, sem position absolute).

**Quando usar:** Campos de busca com sugestoes, filtros complexos, selecao de tribunais.

---

### block-cards-2col.html
**Grid de cards em 2 colunas - 4 variacoes**

1. **Cards com links** - Icone + titulo + descricao + link verde "Saiba mais" com seta
2. **Cards com botoes secondary** - Mesmo layout + botao secondary "Saiba mais" (borda cinza, texto verde)
3. **Cards com 1 primary CTA** - Card destaque com borda verde e botao primary + card normal com secondary. Regra: maximo 1 botao primary por pagina.
4. **Cards horizontais** - Icone a esquerda + conteudo a direita, sem botao

Todos: grid `repeat(2, 1fr)`, icone com fundo `--primary-1`, gap 24px, padding 24px, borda `--card-border`, radius 16px.

**Quando usar:** Secoes de features, beneficios, servicos em landing pages e dashboards.

---

### block-faq.html
**FAQ com Accordion Farol**

Secao centralizada (max-width 760px) com:
- Heading "Perguntas frequentes" + subtitulo
- Accordion com 6 itens, conteudo juridico (Jus IA)
- Padrao: border-bottom entre itens (sem card wrapper), chevron a direita que roda 180deg ao abrir
- Animacao com `grid-template-rows: 0fr → 1fr` e `ease-expressive`
- Modo single (fechar outros ao abrir)
- CTA de rodape com fundo muted: "Ainda tem duvidas?" + botoes secondary e primary
- JavaScript para toggle funcional

**Quando usar:** Secoes de FAQ em landing pages, paginas de produto, paginas de planos.

---

### block-footer.html
**Footer institucional**

Footer de 4 colunas responsivo:
- Colunas: "Para todas as pessoas", "Para profissionais", "Para empresas", "Jusbrasil"
- Links em `--muted-foreground` com hover verde
- Grid responsivo: 1col mobile → 2col sm → 4col lg
- Barra inferior: logo Jusbrasil (SVG com `fill="currentColor"`) + copyright + links legais (Termos, Privacidade, Cookies) + icones sociais (LinkedIn, Instagram, X, YouTube)
- Icones sociais: 36x36px, radius 8px, hover com fundo muted

**Quando usar:** Rodape de qualquer pagina publica/institucional.

---

### block-pricing.html
**Tabela de precos / Planos**

Secao de pricing com:
- Heading centralizado + subtitulo
- Toggle anual/mensal (pill shape, bg muted)
- 3 cards de plano lado a lado:
  - **Basico**: gratuito, features limitadas, botao secondary
  - **Profissional**: plano destaque com borda verde + badge "Mais popular" + botao primary
  - **Escritorio**: preco por usuario, botao secondary
- Cada card: titulo, preco grande + periodo, separador, lista de features com checkmarks verdes
- Responsivo: stack no mobile

**Quando usar:** Paginas de planos e precos, modais de upgrade, comparativos.

---

### block-document-widget.html
**Widgets de sidebar para pagina de documento**

6 widgets tipo card (max-width 380px) para sidebar de detalhe:
1. **Timeline/Movimentacoes** - Lista de datas com descricao, badge "Importante", link "Ver todas"
2. **Documentos do processo** - Lista de arquivos com icone colorido (PDF vermelho, DOC azul), nome + meta, botao download
3. **Dados do processo** - Pares chave-valor (Numero, Area, Tribunal, Juiz, Valor) com grid 2 colunas
4. **Partes do processo** - Polo ativo + passivo com nomes e papeis, chips de identificacao
5. **CTA Jus IA** - Card de conversao com logo colorido, titulo, descricao, botao primary "Perguntar ao Jus IA"
6. **Monitorar processo** - Toggle switch para "Receber alertas" + selecao de frequencia

**Quando usar:** Sidebar de paginas de detalhe (processo, documento, artigo).

---

### block-empty-states.html
**Estados vazios - 6 variacoes**

4 estados full-page + 2 inline:
1. **Busca sem resultados** - Ilustracao lupa, titulo, descricao, botoes "Limpar filtros" (secondary) + "Perguntar ao Jus IA" (primary)
2. **Primeiro acesso/onboarding** - Ilustracao check verde, "Bem-vindo ao monitoramento!", botao "Adicionar processo"
3. **Lista vazia** - Ilustracao documento, "Nenhuma peca criada ainda", botoes "Criar nova peca" + "Saiba mais"
4. **Erro/falha** - Ilustracao warning amarelo, "Algo deu errado", botao "Tentar novamente"
5. **Inline - conversas** - Dentro de card, icone menor, "Nenhuma conversa ainda", botao sm
6. **Inline - notificacoes** - Dentro de card, "Tudo em dia!", sem botao

Full-page: centralizado, max-width 640px, ilustracao SVG simplificada. Inline: dentro de demo-card com header.

**Quando usar:** Telas de busca vazia, primeiro acesso, listas sem dados, erros de carregamento, widgets sem conteudo.

---

### block-banners-cta.html
**Banners inline + CTAs + Banner de topo**

3 categorias de componentes:

1. **Banner de topo (promo)** - Barra escura (`--foreground`) full-width com texto + link verde (`--secondary`) + botao fechar. Para promocoes e novidades.

2. **Banners inline** - 5 tipos semanticos seguindo o padrao Farol Banner:
   - `info` (fundo azul claro) - atualizacoes de termos
   - `positive` (fundo verde claro) - confirmacoes de sucesso
   - `warning` (fundo amarelo claro) - avisos de expiracao
   - `critical` (fundo vermelho claro) - erros de pagamento
   - `discovery` (fundo verde primary claro) - novidades de produto
   Todos com: icone + titulo + texto + link de acao + botao fechar

3. **CTAs section** - 4 variacoes:
   - **Centrado cinza**: fundo muted, heading + desc + 2 botoes (primary + secondary)
   - **Centrado verde**: fundo primary, texto branco, botao branco
   - **Split**: texto a esquerda + botao a direita, fundo muted
   - **Card**: borda + icone em fundo tintado + texto + botao, layout horizontal

**Quando usar:** Notificacoes inline, alertas de sistema, secoes de conversao, promocoes.

---

### block-timeline.html
**Timeline de movimentacoes de processo**

Timeline vertical com:
- Linha vertical continua via `::before` (1px, cinza)
- Agrupamento por data com dot verde (15px, borda primary) + data bold + tempo relativo
- Eventos com dot cinza menor (7px) + tipo "Andamento" + badge opcional "Importante" + descricao
- Botao "Mostrar explicacao" com icone sparkle (IA) em verde
- Exemplo de explicacao expandida (fundo muted, radius 8px, texto formatado)
- Botao "Mostrar movimentacoes anteriores" no rodape

**Quando usar:** Paginas de detalhe de processo, historicos de movimentacoes, cronologias.

---

## Regras ao usar blocks como referencia

1. **Tokens**: Todos os blocks usam as mesmas CSS vars Farol. Ao implementar em React, substitua por classes Tailwind equivalentes.
2. **Botoes**: Todos seguem `border-radius: 8px`. Pill shape apenas nos filter chips.
3. **Responsividade**: Blocks sao demonstrativos em largura fixa. Ao implementar, adicione breakpoints mobile-first.
4. **Copy**: Textos nos blocks sao placeholders realistas. Adapte para o contexto do produto.
5. **SVGs**: Icones inline nos blocks vem de Heroicons/Lucide. Em React, use `lucide-react` imports.
6. **Shadows**: Todos usam `rgba(25, 52, 102, ...)` (blue-tinted), nunca preto puro.
