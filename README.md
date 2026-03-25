# 🎨 VSCode Settings

Minhas configurações personalizadas do Visual Studio Code para uma experiência de desenvolvimento otimizada e produtiva.

## 📋 Índice

- [Visão Geral](#-visão-geral)
- [Editor](#-editor)
- [Explorer](#-explorer)
- [Git](#-git)
- [GitHub Copilot](#-github-copilot)
- [Terminal](#-terminal)
- [Workbench](#-workbench)
- [Outras Configurações](#-outras-configurações)
- [Instalação](#-instalação)
- [Fontes Utilizadas](#-fontes-utilizadas)
- [Extensões Recomendadas](#-extensões-recomendadas)

## 🎯 Visão Geral

Este repositório contém minhas configurações do VSCode focadas em:

- ✨ Interface minimalista e limpa
- 🚀 Produtividade maximizada
- 💅 Experiência visual suave
- 🤖 Integração com GitHub Copilot
- 📦 Organização inteligente de arquivos

## ⚙️ Editor

### Aparência e Tipografia

```json
"editor.fontSize": 15
"editor.fontFamily": "Noto Sans Mono"
"editor.fontLigatures": true
"editor.letterSpacing": 1.1
"editor.lineHeight": 1.5
```

- **Fonte**: Noto Sans Mono com ligaduras habilitadas
- **Tamanho**: 15px para melhor legibilidade
- **Espaçamento**: 1.1 entre letras e 1.5 de altura de linha

### Interface Minimalista

```json
"editor.minimap.enabled": false
"editor.lineNumbers": "off"
"editor.stickyScroll.enabled": false
```

- **Minimapa desabilitado**: Mais espaço para código
- **Números de linha ocultos**: Interface mais limpa
- **Sticky scroll desabilitado**: Preferência pessoal

### Comportamento

```json
"editor.cursorBlinking": "smooth"
"editor.smoothScrolling": true
"editor.cursorSmoothCaretAnimation": "on"
"editor.tabSize": 4
"editor.indentSize": "tabSize"
"editor.insertSpaces": false
"editor.detectIndentation": false
```

- **Animações suaves**: Cursor e scroll com transições fluidas
- **Tabulação**: 4 espaços usando tabs (não espaços)
- **Detecção de indentação desabilitada**: Usa configuração fixa ao invés de detectar automaticamente

## 📁 Explorer

### Confirmações Desabilitadas

```json
"explorer.autoReveal": false
"explorer.confirmDelete": false
"explorer.confirmDragAndDrop": false
"explorer.confirmPasteNative": false
```

- **Auto Reveal**: Não revela automaticamente o arquivo aberto no explorer
- Confirmações automáticas desabilitadas para agilizar o fluxo de trabalho.

### File Nesting

```json
"explorer.fileNesting.enabled": true
"explorer.compactFolders": false
```

**Padrões de aninhamento configurados:**

- `.env` → agrupa todos os arquivos `.env*`
- `settings.json` → agrupa `emojis.json`, `emojis.dev.json`
- `package.json` → agrupa:
    - Lock files: `*lock.json`, `*.lock`, `*lock.yaml`, `*.lockb`
    - Configs: `*config.json`, `*config.ts`
    - Linters: `.eslintrc.json`, `biome.json`
    - Outros: `.gitignore`, `.discloudignore`, `.nvmrc`

Isso mantém o explorer organizado agrupando arquivos relacionados.

## 🔀 Git

### Automação

```json
"git.enableSmartCommit": true
"git.confirmSync": false
"git.autofetch": true
"git.postCommitCommand": "sync"
"git.openRepositoryInParentFolders": "always"
```

- **Smart Commit**: Permite commit rápido de todas as alterações
- **Auto Fetch**: Busca atualizações automaticamente
- **Post Commit**: Sincroniza automaticamente após commit
- **Sem confirmações**: Fluxo de trabalho mais rápido

## 🤖 GitHub Copilot

### Modelo e Habilitação

```json
"github.copilot.selectedCompletionModel": "gpt-4o-copilot"
"github.copilot.enable": {
    "*": true,
    "plaintext": false,
    "markdown": false,
    "scminput": true
}
```

- **Modelo**: GPT-4O Copilot para sugestões mais precisas
- **Desabilitado em**: Arquivos de texto puro e Markdown
- **Habilitado em**: Mensagens de commit (scminput)

### Configurações de Chat

```json
"github.copilot.chat.localeOverride": "pt-br"
"github.copilot.nextEditSuggestions.enabled": true
```

- **Idioma**: Português brasileiro
- **Next Edit Suggestions**: Sugestões de próximas edições ativadas

### Mensagens de Commit

```json
"github.copilot.chat.commitMessageGeneration.instructions": [
    { "text": "All commits must be in English. Follow the style: emoji + type(scope): description." },
    { "text": "Use these emojis for the respective types: feat = ✨, fix = 🐛, docs = 📚, style = 💎, refactor = ♻️, perf = ⚡, test = ✅, build = 📦, ci = 🎡, chore = ♻️, revert = ⏪" },
    { "file": "./.github/commit-style-guide.md" }
]
```

Mensagens de commit geradas seguem o padrão:

- 🌟 Formato: `emoji + type(scope): description`
- 🌐 Idioma: Inglês
- 📝 Guia de estilo personalizado em `.github/commit-style-guide.md`

> **⚠️ Nota:** O arquivo `.github/commit-style-guide.md` deve ser criado em cada projeto onde você deseja usar essas instruções personalizadas. Este arquivo deve conter seu guia de estilo específico para mensagens de commit.

<details>
<summary>📄 Exemplo de <code>.github/commit-style-guide.md</code></summary>

```markdown
# Commit Style Guide

## Format

All commit messages must follow this format:
```

emoji type(scope): description

```

## Types
- **feat**: New feature
- **fix**: Bug fix
- **docs**: Documentation changes
- **style**: Code style changes (formatting, semicolons, etc)
- **refactor**: Code refactoring
- **perf**: Performance improvements
- **test**: Adding or updating tests
- **chore**: Maintenance tasks
- **ci**: CI/CD changes
- **build**: Build system changes

## Emojis
- ✨ feat: New feature
- 🐛 fix: Bug fix
- 📝 docs: Documentation
- 💄 style: Styling/formatting
- ♻️ refactor: Code refactoring
- ⚡ perf: Performance
- ✅ test: Tests
- 🔧 chore: Maintenance
- 👷 ci: CI/CD
- 📦 build: Build

## Scope
The scope should indicate the affected module, component, or area of the project.

## Examples
- ✨ feat(auth): add login with Google
- 🐛 fix(api): resolve timeout issue in user endpoint
- 📝 docs(readme): update installation instructions
- ♻️ refactor(database): optimize query performance
- 🔧 chore(deps): update dependencies to latest versions
```

</details>

## 💻 Terminal

### Aparência

```json
"terminal.integrated.fontFamily": "CaskaydiaCove NFM"
"terminal.integrated.fontLigatures.enabled": true
"terminal.integrated.smoothScrolling": true
"terminal.integrated.tabs.defaultIcon": "github"
```

- **Fonte**: CaskaydiaCove Nerd Font Mono
- **Ligaduras**: Habilitadas
- **Scroll suave**: Ativado
- **Ícone padrão**: GitHub

### Perfil Padrão

```json
"terminal.integrated.defaultProfile.windows": "Windows PowerShell"
```

PowerShell como terminal padrão no Windows.

## 🎨 Workbench

### Layout

```json
"workbench.sideBar.location": "right"
"workbench.activityBar.location": "hidden"
"workbench.editor.showTabs": "multiple"
```

- **Sidebar à direita**: Preferência pessoal de layout
- **Activity Bar oculta**: Mais espaço para código
- **Múltiplas abas**: Visualização de vários arquivos

### Tema e Ícones

```json
"workbench.colorTheme": "escook Dark Soft"
"workbench.iconTheme": "material-icon-theme"
```

- **Tema**: escook Dark Soft
- **Ícones**: Material Icon Theme

### Comportamento

```json
"workbench.startupEditor": "none"
"workbench.list.smoothScrolling": true
"workbench.tree.enableStickyScroll": false
```

- **Sem editor na inicialização**: Começa limpo
- **Scroll suave**: Habilitado em listas
- **Sticky scroll**: Desabilitado em árvores

### Janela

```json
"window.menuBarVisibility": "compact"
"window.confirmSaveUntitledWorkspace": false
```

- **Menu bar compacta**: Economiza espaço vertical
- **Sem confirmação**: Para salvar workspaces sem título

## 🔧 Outras Configurações

### Breadcrumbs

```json
"breadcrumbs.enabled": false
```

Desabilitado para interface mais limpa.

### Chat

```json
"chat.viewSessions.orientation": "stacked"
```

Sessões de chat empilhadas verticalmente.

### JavaScript

```json
"js/ts.updateImportsOnFileMove.enabled": "always"
```

Atualiza imports automaticamente ao mover arquivos.

### Lua

```json
"Lua.diagnostics.enable": false
```

Diagnósticos do Lua desabilitados.

### Prettier

```json
"editor.formatOnSave": true
"editor.defaultFormatter": "esbenp.prettier-vscode"
"prettier.tabWidth": 4
"prettier.useTabs": true
"prettier.singleQuote": true
```

- **Format on Save**: Formata automaticamente ao salvar
- **Formatador padrão**: Prettier configurado como formatador principal
- **Tab Width**: 4 espaços
- **Usar Tabs**: Usa tabs ao invés de espaços
- **Single Quotes**: Aspas simples em strings

### Segurança

```json
"security.workspace.trust.enabled": false
```

Trust mode desabilitado para facilitar abertura de projetos.

## 📦 Instalação

### 1. Clonar o Repositório

```bash
git clone https://github.com/seu-usuario/vscode-settings.git
```

### 2. Localizar as Configurações do VSCode

**Windows:**

```
%APPDATA%\Code\User\
```

**macOS:**

```
~/Library/Application Support/Code/User/
```

**Linux:**

```
~/.config/Code/User/
```

### 3. Copiar o Arquivo

Copie o `settings.json` para o diretório de configurações do VSCode.

### 4. Reiniciar o VSCode

Reinicie o editor para aplicar as configurações.

## 🔤 Fontes Utilizadas

### Editor

- **[Noto Sans Mono](https://fonts.google.com/noto/specimen/Noto+Sans+Mono)**: Fonte principal com suporte a ligaduras

### Terminal

- **[CaskaydiaCove Nerd Font](https://www.nerdfonts.com/)**: Fonte com ícones e glifos especiais

### Instalação das Fontes

1. Baixe as fontes dos links acima
2. Instale no seu sistema operacional
3. Reinicie o VSCode

## 🧩 Extensões Recomendadas

Para aproveitar todas as configurações, instale:

- **[Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)**: Ícones do explorer
- **[escook Dark Soft](https://marketplace.visualstudio.com/items?itemName=escook.dark-soft)**: Tema de cores
- **[GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)**: Assistente de código AI
- **[Prettier](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)**: Formatador de código
- **Extensões de linguagem**: Conforme suas necessidades

## 📝 Notas

- Estas configurações são otimizadas para meu fluxo de trabalho pessoal
- Sinta-se livre para adaptar conforme suas preferências
- Algumas configurações podem requerer extensões específicas

## 📄 Licença

Configurações de código aberto - use e modifique como desejar!

---

**Última atualização:** Março 2026
