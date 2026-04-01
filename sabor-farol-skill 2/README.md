# Sabor Farol - Skill Jusbrasil Design System

Skill para construir interfaces Jusbrasil com o Farol Design System.
Compatível com Claude Code, OpenAI Codex e Antigravity.

## Instalacao

### Claude Code

Copie a pasta `claude-code/sabor-farol/` para `.claude/skills/` no seu projeto:

```bash
cp -r claude-code/sabor-farol/ <seu-projeto>/.claude/skills/sabor-farol/
```

A skill sera ativada automaticamente quando voce mencionar Farol, Jusbrasil, ou pedir para construir UI.

### OpenAI Codex

Copie `AGENTS.md` para a raiz do seu projeto:

```bash
cp AGENTS.md <seu-projeto>/AGENTS.md
```

Para ter acesso aos arquivos de referencia detalhados (componentes, tokens, patterns), copie tambem a pasta de referencias:

```bash
cp -r claude-code/sabor-farol/references/ <seu-projeto>/.sabor-farol/references/
cp -r claude-code/sabor-farol/assets/ <seu-projeto>/.sabor-farol/assets/
```

### Antigravity

Copie `INSTRUCTIONS.md` para a raiz do seu projeto:

```bash
cp INSTRUCTIONS.md <seu-projeto>/INSTRUCTIONS.md
```

Ou, se o Antigravity usar outro nome de arquivo de instrucoes, renomeie conforme necessario.

Para referencia detalhada, copie tambem:

```bash
cp -r claude-code/sabor-farol/references/ <seu-projeto>/.sabor-farol/references/
cp -r claude-code/sabor-farol/assets/ <seu-projeto>/.sabor-farol/assets/
```

## Estrutura

```
sabor-farol-dist/
  README.md                           # Este arquivo
  AGENTS.md                           # OpenAI Codex (self-contained)
  INSTRUCTIONS.md                     # Antigravity (self-contained)
  claude-code/
    sabor-farol/
      SKILL.md                        # Arquivo principal Claude Code
      references/
        products.md                   # Produtos, personas, tom de voz
        tokens.md                     # Cores, tipografia, espacamento
        components.md                 # 60+ componentes com props e exemplos
        patterns.md                   # Templates de pagina
        icons.md                      # Icones Farol
        setup.md                      # CSS vars + Tailwind v4 config
      assets/
        logos.md                      # SVGs oficiais Jusbrasil e Jus IA
```

## O que a skill cobre

- Design system Farol DS completo (cores, tipografia, espacamento, sombras, motion)
- 60+ componentes React com props, variantes e exemplos
- Regras visuais aprendidas do produto real (botoes, cards, links, logo)
- Contexto de produto: 2 segmentos (Litigantes e Profissionais do Direito)
- 7 produtos com copy oficial, personas e tom de voz
- Terminologia oficial e dados de mercado
- Templates de pagina e padroes de layout
- Checklist de qualidade pre-entrega
- Stack: React + TypeScript + Tailwind CSS v4 + shadcn/ui
