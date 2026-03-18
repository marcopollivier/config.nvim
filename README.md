# config.nvim

Configuração pessoal de Neovim baseada no [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) — enxuta, legível e sem magia escondida. Cada plugin tem um motivo claro de estar aqui.

> **Filosofia:** diferente de distribuições como LazyVim, aqui você lê e entende cada linha. Nada é instalado automaticamente por uma "distribuição" — você controla tudo.

---

## Requisitos

| Ferramenta | Por quê |
|------------|---------|
| [Neovim](https://neovim.io/) ≥ 0.10 | Motor principal |
| [git](https://git-scm.com/) | Clonar plugins via lazy.nvim |
| [ripgrep](https://github.com/BurntSushi/ripgrep) | Busca de texto no Telescope (`<leader>sg`) |
| [make](https://www.gnu.org/software/make/) | Compilar telescope-fzf-native (busca mais rápida) |
| [Nerd Font](https://www.nerdfonts.com/) | Ícones no neo-tree, telescope, statusline |
| [Go](https://golang.org/) | Para usar o gopls (LSP de Go) |

---

## Instalação (macOS)

### 1. Instalar dependências

```sh
brew install neovim ripgrep make
```

### 2. Clonar este repositório

O Neovim lê a config em `~/.config/nvim`. A melhor prática é manter o repo em outro lugar e criar um symlink — assim você tem controle git sem interferir com o diretório de config padrão.

```sh
# Clone onde preferir (ex: ~/dev/config.nvim)
git clone https://github.com/marcopollivier/config.nvim.git ~/dev/config.nvim

# Backup da config anterior (se existir)
mv ~/.config/nvim ~/.config/nvim.bak

# Limpar dados de plugins antigos (se existir)
rm -rf ~/.local/share/nvim ~/.local/state/nvim ~/.cache/nvim

# Criar symlink
ln -s ~/dev/config.nvim ~/.config/nvim
```

### 3. Abrir o Neovim

```sh
nvim
```

Na primeira abertura, o [lazy.nvim](https://github.com/folke/lazy.nvim) vai detectar que os plugins ainda não estão instalados e vai baixar tudo automaticamente. Aguarde ~1 minuto.

### 4. Verificar saúde da instalação

```
:checkhealth
```

Rode este comando dentro do nvim para verificar se tudo está funcionando corretamente — LSPs, dependências externas, etc.

---

## Plugins instalados

### Gerenciamento

| Plugin | Função |
|--------|--------|
| [lazy.nvim](https://github.com/folke/lazy.nvim) | Gerenciador de plugins com lazy-loading |
| [mason.nvim](https://github.com/williamboman/mason.nvim) | Instala LSPs, formatters e linters automaticamente |

### Navegação

| Plugin | Função |
|--------|--------|
| [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim) | Busca fuzzy de arquivos, texto, símbolos, keymaps |
| [telescope-fzf-native](https://github.com/nvim-telescope/telescope-fzf-native.nvim) | Motor de busca mais rápido para o Telescope |
| [neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim) | Explorador de arquivos lateral |

### LSP e Código

| Plugin | Função |
|--------|--------|
| [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig) | Configuração de Language Servers |
| [mason-lspconfig](https://github.com/williamboman/mason-lspconfig.nvim) | Integra Mason com lspconfig |
| [nvim-cmp](https://github.com/hrsh7th/nvim-cmp) | Autocompletion |
| [LuaSnip](https://github.com/L3MON4D3/LuaSnip) | Engine de snippets |
| [conform.nvim](https://github.com/stevearc/conform.nvim) | Formatação de código no save |
| [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter) | Syntax highlighting avançado e text objects |
| [lazydev.nvim](https://github.com/folke/lazydev.nvim) | Autocomplete para a API do Neovim em Lua |

### LSPs ativos (instalados via Mason)

| LSP | Linguagem |
|-----|-----------|
| `gopls` | Go |
| `lua_ls` | Lua (config do nvim) |

> Para adicionar mais linguagens: abra `:Mason`, busque o LSP desejado e instale. Ou adicione em `init.lua` na tabela `servers`.

### Interface

| Plugin | Função |
|--------|--------|
| [tokyonight.nvim](https://github.com/folke/tokyonight.nvim) | Tema de cores |
| [mini.nvim](https://github.com/echasnovski/mini.nvim) | Statusline, surrounds e text objects extras |
| [which-key.nvim](https://github.com/folke/which-key.nvim) | Painel de atalhos ao pressionar `<Space>` |
| [indent-blankline](https://github.com/lukas-reineke/indent-blankline.nvim) | Guias visuais de indentação |

### Git

| Plugin | Função |
|--------|--------|
| [gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim) | Sinais de git no gutter, stage de hunks, blame |

### Qualidade de vida

| Plugin | Função |
|--------|--------|
| [nvim-autopairs](https://github.com/windwp/nvim-autopairs) | Fecha `()`, `{}`, `""` automaticamente |
| [todo-comments.nvim](https://github.com/folke/todo-comments.nvim) | Destaca `TODO`, `FIXME`, `NOTE` nos comentários |
| [vim-sleuth](https://github.com/tpope/vim-sleuth) | Detecta indentação (tabs/spaces) automaticamente |

### Plugins customizados

Qualquer arquivo `.lua` em `lua/custom/plugins/` é carregado automaticamente. Use essa pasta para adicionar plugins sem modificar o `init.lua` principal:

```
lua/custom/plugins/
└── meu-plugin.lua   ← criado por você
```

---

## Atalhos

> **Leader key** = `<Space>`
> Ao pressionar `<Space>` e aguardar, o **which-key** exibe todos os atalhos disponíveis.

### Navegação básica

| Atalho | Ação |
|--------|------|
| `h j k l` | Mover cursor: esquerda / baixo / cima / direita |
| `w` / `b` / `e` | Próxima palavra / palavra anterior / fim da palavra |
| `0` / `$` | Início / fim da linha |
| `gg` / `G` | Primeira / última linha do arquivo |
| `5j` / `3k` | Descer/subir N linhas (usa relativenumber) |
| `<C-d>` / `<C-u>` | Rolar meia página abaixo / acima |
| `%` | Pular para o bracket correspondente |
| `{` / `}` | Pular para parágrafo anterior / próximo |

### Modos

| Atalho | Ação |
|--------|------|
| `i` / `a` | Insert antes / após o cursor |
| `o` / `O` | Nova linha abaixo / acima e entrar em Insert |
| `v` / `V` / `<C-v>` | Visual por caractere / linha / bloco |
| `<Esc>` | Voltar para Normal mode |

### Edição

| Atalho | Ação |
|--------|------|
| `dd` / `yy` | Deletar / copiar linha inteira |
| `p` / `P` | Colar após / antes do cursor |
| `u` / `<C-r>` | Undo / Redo |
| `ciw` / `diw` | Change/Delete inner word |
| `yi(` / `di"` | Yank/Delete dentro de `()` / `""` |
| `>>` / `<<` | Indentar / des-indentar |
| `.` | Repetir último comando |
| `<leader>f` | Formatar o arquivo atual |

### Splits (janelas)

| Atalho | Ação |
|--------|------|
| `<C-w>v` / `<C-w>s` | Dividir verticalmente / horizontalmente |
| `<C-h>` / `<C-l>` | Foco para janela à esquerda / direita |
| `<C-j>` / `<C-k>` | Foco para janela abaixo / acima |
| `<C-w>=` | Equalizar tamanho das janelas |
| `<C-w>q` | Fechar janela atual |

### Busca

| Atalho | Ação |
|--------|------|
| `/palavra` | Buscar para frente |
| `?palavra` | Buscar para trás |
| `n` / `N` | Próxima / anterior ocorrência |
| `*` | Buscar palavra sob o cursor |
| `<Esc>` | Limpar highlights de busca |
| `:%s/old/new/gc` | Substituir com confirmação |

### Telescope — busca fuzzy

| Atalho | Ação |
|--------|------|
| `<leader>sf` | **[S]earch [F]iles** — arquivos do projeto |
| `<leader>sg` | **[S]earch [G]rep** — texto em todos os arquivos |
| `<leader>sw` | **[S]earch [W]ord** — palavra sob o cursor |
| `<leader>sh` | **[S]earch [H]elp** — documentação do nvim |
| `<leader>sk` | **[S]earch [K]eymaps** — todos os atalhos |
| `<leader>sd` | **[S]earch [D]iagnostics** — erros e warnings |
| `<leader>sr` | **[S]earch [R]esume** — reabrir última busca |
| `<leader>s.` | Arquivos recentes |
| `<leader><leader>` | Buffers abertos |
| `<leader>/` | Busca fuzzy no buffer atual |
| `<leader>sn` | Buscar nos arquivos desta config |

> Dentro do Telescope: `<C-n>`/`<C-p>` para navegar, `<CR>` para abrir, `?` para ver todos os atalhos.

### Neo-tree — explorador de arquivos

| Atalho | Ação |
|--------|------|
| `\` | Abrir/fechar neo-tree (revela arquivo atual) |
| `a` | Criar arquivo ou pasta |
| `d` | Deletar |
| `r` | Renomear |
| `y` / `x` / `p` | Copiar / Recortar / Colar |
| `<CR>` | Abrir arquivo |
| `i` / `s` | Abrir em split horizontal / vertical |

### LSP — navegação de código

> Disponíveis em arquivos com LSP ativo (`.go`, `.lua`, etc.)

| Atalho | Ação |
|--------|------|
| `gd` | **Go to Definition** — onde foi definido |
| `gr` | **Go to References** — onde é usado |
| `gI` | **Go to Implementation** |
| `gD` | **Go to Declaration** |
| `K` | Documentação (hover) |
| `<C-t>` | Voltar após um `gd` |
| `<leader>rn` | **Rename** em todos os arquivos do projeto |
| `<leader>ca` | **Code Action** (imports, refactor, fix) |
| `<leader>D` | Definição do tipo |
| `<leader>ds` | Símbolos do arquivo atual |
| `<leader>ws` | Símbolos do workspace |
| `<leader>th` | Toggle inlay hints (dicas de tipo inline) |

### Diagnósticos

| Atalho | Ação |
|--------|------|
| `[d` / `]d` | Diagnóstico anterior / próximo |
| `<leader>q` | Abrir quickfix list com diagnósticos |

### Git com Gitsigns

| Atalho | Ação |
|--------|------|
| `]h` / `[h` | Próximo / anterior hunk (bloco de mudança) |
| `<leader>hs` | Stage do hunk sob o cursor |
| `<leader>hr` | Reset do hunk sob o cursor |
| `<leader>hS` | Stage de todo o arquivo |
| `<leader>hR` | Reset de todo o arquivo |
| `<leader>hp` | Preview do hunk |
| `<leader>hb` | Blame da linha atual |
| `<leader>hd` | Diff do arquivo |
| `<leader>tb` | Toggle blame inline |

### Surrounds (mini.surround)

| Atalho | Ação |
|--------|------|
| `saiw)` | Adicionar `()` ao redor da palavra |
| `saiw"` | Adicionar `""` ao redor da palavra |
| `sd'` | Remover `'` ao redor |
| `sr)"` | Substituir `()` por `""` |

### Autocompletion (nvim-cmp)

| Atalho | Ação |
|--------|------|
| `<C-n>` / `<C-p>` | Próximo / anterior item |
| `<C-y>` | Aceitar completion |
| `<C-Space>` | Forçar abertura do menu |
| `<C-l>` / `<C-h>` | Avançar / voltar campo do snippet |

### Utilitários

| Atalho | Ação |
|--------|------|
| `:Lazy` | Gerenciar plugins |
| `:Mason` | Gerenciar LSPs e ferramentas |
| `:checkhealth` | Diagnóstico geral do nvim |
| `<Esc><Esc>` | Sair do modo terminal integrado |

---

## Estrutura de arquivos

```
~/.config/nvim/          ← symlink para este repo
├── init.lua             ← configuração principal (tudo está aqui)
├── lua/
│   ├── kickstart/
│   │   └── plugins/     ← plugins opcionais desacoplados
│   │       ├── autopairs.lua
│   │       ├── gitsigns.lua
│   │       ├── indent_line.lua
│   │       ├── neo-tree.lua
│   │       ├── debug.lua    ← desativado (DAP)
│   │       └── lint.lua     ← desativado (linting extra)
│   └── custom/
│       └── plugins/     ← seus plugins pessoais (não versionar se quiser)
│           └── init.lua
├── KEYMAPS.md           ← referência rápida de atalhos
└── README.md
```

---

## Adicionando seus próprios plugins

Crie um arquivo em `lua/custom/plugins/`:

```lua
-- lua/custom/plugins/copilot.lua
return {
  'github/copilot.vim',
  event = 'InsertEnter',
}
```

O lazy.nvim vai detectar e carregar automaticamente.

---

## Créditos

Baseado em [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim) de TJ DeVries.
