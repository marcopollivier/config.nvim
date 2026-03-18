# Guia de Atalhos do Neovim

> **Leader key** = `<Space>` (barra de espaço)
> Sempre que ver `<leader>`, pressione Space primeiro.

---

## Navegação Básica (Vim)

| Atalho | Ação |
|--------|------|
| `h j k l` | Mover cursor: esquerda / baixo / cima / direita |
| `w` | Pular para início da próxima palavra |
| `b` | Pular para início da palavra anterior |
| `e` | Pular para fim da próxima palavra |
| `0` | Início da linha |
| `$` | Fim da linha |
| `gg` | Primeira linha do arquivo |
| `G` | Última linha do arquivo |
| `5j` | Descer 5 linhas (usa relativenumber) |
| `3k` | Subir 3 linhas (usa relativenumber) |
| `<C-d>` | Rolar meia página abaixo |
| `<C-u>` | Rolar meia página acima |
| `%` | Pular para o bracket/parêntese correspondente |
| `{` / `}` | Pular para o parágrafo anterior/próximo |

---

## Modos

| Atalho | Ação |
|--------|------|
| `i` | Entrar em Insert antes do cursor |
| `a` | Entrar em Insert após o cursor |
| `o` | Nova linha abaixo e entrar em Insert |
| `O` | Nova linha acima e entrar em Insert |
| `v` | Entrar em Visual (seleção por caractere) |
| `V` | Entrar em Visual Line (seleção por linha) |
| `<C-v>` | Visual Block (seleção retangular) |
| `<Esc>` | Voltar para Normal mode |

---

## Edição

| Atalho | Ação |
|--------|------|
| `dd` | Deletar linha inteira |
| `yy` | Copiar (yank) linha inteira |
| `p` | Colar após o cursor |
| `P` | Colar antes do cursor |
| `u` | Desfazer (undo) |
| `<C-r>` | Refazer (redo) |
| `ciw` | Change inner word (apaga palavra e entra em Insert) |
| `diw` | Delete inner word |
| `yi(` | Yank (copiar) tudo dentro de `()` |
| `di"` | Deletar tudo dentro de `""` |
| `>>` / `<<` | Indentar / des-indentar linha |
| `.` | Repetir último comando |
| `~` | Alternar maiúscula/minúscula do caractere sob cursor |

---

## Busca e Substituição

| Atalho | Ação |
|--------|------|
| `/palavra` | Buscar "palavra" para frente |
| `?palavra` | Buscar "palavra" para trás |
| `n` / `N` | Próxima / anterior ocorrência |
| `*` | Buscar palavra sob o cursor |
| `<Esc>` | Limpar highlights de busca |
| `:%s/old/new/g` | Substituir "old" por "new" no arquivo todo |
| `:%s/old/new/gc` | Substituir com confirmação a cada ocorrência |

---

## Splits (Janelas)

| Atalho | Ação |
|--------|------|
| `<C-w>v` | Dividir verticalmente |
| `<C-w>s` | Dividir horizontalmente |
| `<C-h>` | Mover foco para janela à esquerda |
| `<C-l>` | Mover foco para janela à direita |
| `<C-j>` | Mover foco para janela abaixo |
| `<C-k>` | Mover foco para janela acima |
| `<C-w>=` | Equalizar tamanho de todas as janelas |
| `<C-w>q` | Fechar janela atual |

---

## Telescope — Busca Fuzzy

| Atalho | Ação |
|--------|------|
| `<leader>sf` | **[S]earch [F]iles** — buscar arquivos no projeto |
| `<leader>sg` | **[S]earch [G]rep** — buscar texto em todos os arquivos |
| `<leader>sw` | **[S]earch [W]ord** — buscar palavra sob o cursor |
| `<leader>sh` | **[S]earch [H]elp** — buscar na documentação do nvim |
| `<leader>sk` | **[S]earch [K]eymaps** — ver todos os atalhos |
| `<leader>sd` | **[S]earch [D]iagnostics** — erros e warnings do LSP |
| `<leader>sr` | **[S]earch [R]esume** — reabrir última busca |
| `<leader>s.` | **[S]earch** arquivos recentes |
| `<leader><leader>` | Listar buffers abertos |
| `<leader>/` | Busca fuzzy no buffer atual |
| `<leader>sn` | Buscar nos arquivos de configuração do nvim |

> **Dentro do Telescope:** `<C-n>`/`<C-p>` para navegar, `<CR>` para abrir, `?` para ver todos os atalhos disponíveis.

---

## Neo-tree — Explorador de Arquivos

| Atalho | Ação |
|--------|------|
| `\` | Abrir Neo-tree mostrando o arquivo atual |
| `\` | (dentro do Neo-tree) Fechar o painel |
| `a` | Criar arquivo (dentro do neo-tree) |
| `d` | Deletar arquivo/pasta |
| `r` | Renomear arquivo |
| `y` | Copiar arquivo |
| `x` | Recortar arquivo |
| `p` | Colar arquivo |
| `<CR>` | Abrir arquivo selecionado |
| `i` | Abrir em split horizontal |
| `s` | Abrir em split vertical |

---

## LSP — Navegação de Código

> Disponíveis quando um LSP está ativo (ex: arquivo `.go`, `.lua`, etc.)

| Atalho | Ação |
|--------|------|
| `gd` | **Go to Definition** — ir para onde foi definido |
| `gr` | **Go to References** — onde é usado no projeto |
| `gI` | **Go to Implementation** — ir para a implementação |
| `gD` | **Go to Declaration** — ir para a declaração |
| `K` | Mostrar documentação (hover) |
| `<leader>rn` | **[R]e[n]ame** — renomear em todos os arquivos |
| `<leader>ca` | **[C]ode [A]ction** — sugestões (imports, refactor) |
| `<leader>D` | Ir para definição do tipo |
| `<leader>ds` | Símbolos do documento atual |
| `<leader>ws` | Símbolos do workspace inteiro |
| `<leader>th` | Toggle inlay hints (dicas de tipo inline) |
| `<C-t>` | Voltar após um `gd` (jump back) |

---

## Diagnósticos (Erros/Warnings)

| Atalho | Ação |
|--------|------|
| `[d` | Diagnóstico anterior |
| `]d` | Próximo diagnóstico |
| `<leader>q` | Abrir lista de diagnósticos (quickfix) |
| `<leader>sd` | Buscar diagnósticos via Telescope |

---

## Git com Gitsigns

| Atalho | Ação |
|--------|------|
| `]h` | Próximo hunk (bloco de mudança) |
| `[h` | Hunk anterior |
| `<leader>hs` | Stage do hunk sob o cursor |
| `<leader>hr` | Reset do hunk sob o cursor |
| `<leader>hS` | Stage de todo o arquivo |
| `<leader>hR` | Reset de todo o arquivo |
| `<leader>hp` | Preview do hunk (ver diff) |
| `<leader>hb` | Blame da linha atual |
| `<leader>hd` | Diff do arquivo atual |
| `<leader>tb` | Toggle blame inline |

---

## Formatação e Completions

| Atalho | Ação |
|--------|------|
| `<leader>f` | **[F]ormat** o buffer atual |
| `<C-n>` | Próximo item no menu de completion |
| `<C-p>` | Item anterior no completion |
| `<C-y>` | Aceitar o completion selecionado |
| `<C-Space>` | Forçar abertura do menu de completion |
| `<C-l>` | Avançar para o próximo campo do snippet |
| `<C-h>` | Voltar ao campo anterior do snippet |

---

## Surrounds (mini.surround)

| Atalho | Ação |
|--------|------|
| `saiw)` | **Surround Add** inner word com `()` |
| `saiw"` | **Surround Add** inner word com `""` |
| `sd'` | **Surround Delete** `'` ao redor |
| `sr)"` | **Surround Replace** `()` por `""` |

---

## Buffers e Arquivos

| Atalho | Ação |
|--------|------|
| `:w` | Salvar arquivo |
| `:q` | Fechar janela |
| `:wq` | Salvar e fechar |
| `:q!` | Fechar sem salvar |
| `:e arquivo` | Abrir arquivo |
| `<leader><leader>` | Listar buffers abertos (Telescope) |

---

## Utilitários

| Atalho | Ação |
|--------|------|
| `<leader>q` | Abrir quickfix list com diagnósticos |
| `<Esc><Esc>` | Sair do modo terminal integrado |
| `:checkhealth` | Diagnosticar a saúde do nvim e plugins |
| `:Lazy` | Gerenciar plugins (atualizar, ver status) |
| `:Mason` | Gerenciar LSPs e ferramentas instaladas |
| `:Telescope keymaps` | Ver todos os atalhos configurados |

---

## Dicas Rápidas

- **which-key**: ao pressionar `<Space>` e esperar um segundo, aparece um painel mostrando todos os atalhos disponíveis com o prefixo atual
- **Relativenumber**: use os números relativos que aparecem na margem para comandos como `5j` (5 linhas abaixo), `10dd` (deletar 10 linhas)
- **Repeat (`.`)**: execute uma edição, depois pressione `.` para repeti-la em outros lugares
- **Marks**: `ma` marca a posição atual como "a"; `'a` volta para ela
- **Macros**: `qa` começa a gravar macro em "a"; `q` para; `@a` executa

---

*Referência: `:help` dentro do nvim | `<leader>sh` para buscar na documentação*
