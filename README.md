<div align="center">

> V3 is finally out - check out the changelog [here](https://github.com/glzr-io/GlazeWM/releases) 🔥

  <br>
  <img src="./resources/assets/logo.svg" width="230" alt="GlazeWM logo" />
  <br>

# GlazeWM 
*traduzido em (pt-br)*

**Um gerenciador de janelas do tipo *tiling* para Windows, inspirado no i3wm.**

[![Discord invite][discord-badge]][discord-link]
[![Downloads][downloads-badge]][downloads-link]
[![Good first issues][issues-badge]][issues-link]

GlazeWM permite organizar janelas e ajustar o layout delas rapidamente, utilizando comandos via teclado.

[Instalação](#instalação) •
[Keybindings padrão](#keybindings-padrão) •
[Documentação de configs](#documentação-de-configs) •
[FAQ](#faq) •
[Contribuindo ↗](https://github.com/glzr-io/glazewm/blob/main/Contribuindo.md)

![Demo video][demo-video]

</div>

### 🌟 Principais utilidades

- Configuração simples em YAML
- Suporte a múltiplos monitores
- Regras customizáveis para janelas específicas
- Instalação fácil (um clique)
- Integração com [Zebar](https://github.com/glzr-io/zebar) como barra de status

##  Instalação

A versão mais recente do GlazeWM pode ser baixada via [releases](https://github.com/glzr-io/GlazeWM/releases). O Zebar pode ser instalado opcionalmente marcando uma caixa durante a instalação.

O GlazeWM também está disponível por gerenciadores de pacotes:

**Winget**
```sh
winget install GlazeWM
```

**Chocolatey**
```sh
choco install glazewm
```

**Scoop**
```sh
scoop bucket add extras
scoop install extras/glazewm
```

## 🤝 Contribuindo

Ajude a corrigir algo que te incomoda, ou adicione uma funcionalidade que você queria há tempos! Contribuições são muito bem-vindas.

Guia de desenvolvimento local disponível em: [Contribuindo guide](https://github.com/glzr-io/glazewm/blob/main/Contribuindo.md).

---

##  Keybindings padrão 

> Baseado no `sample-config.yaml` padrão do GlazeWM. Se você usa um config customizado, essas teclas podem estar diferentes.

### Foco e movimentação de janelas

| Keybind | Função |
|---|---|
| `Alt + H` / `Alt + ←` | Focar janela à esquerda |
| `Alt + L` / `Alt + →` | Focar janela à direita |
| `Alt + K` / `Alt + ↑` | Focar janela acima |
| `Alt + J` / `Alt + ↓` | Focar janela abaixo |
| `Alt + Shift + H` / `Alt + Shift + ←` | Mover janela focada para a esquerda |
| `Alt + Shift + L` / `Alt + Shift + →` | Mover janela focada para a direita |
| `Alt + Shift + K` / `Alt + Shift + ↑` | Mover janela focada para cima |
| `Alt + Shift + J` / `Alt + Shift + ↓` | Mover janela focada para baixo |

### Redimensionar janela

| Keybind | Função |
|---|---|
| `Alt + U` | Diminuir largura (-2%) |
| `Alt + P` | Aumentar largura (+2%) |
| `Alt + O` | Aumentar altura (+2%) |
| `Alt + I` | Diminuir altura (-2%) |
| `Alt + R` | Ativar modo de redimensionamento (binding mode "resize") |
| `H` / `←` *(no modo resize)* | Diminuir largura |
| `L` / `→` *(no modo resize)* | Aumentar largura |
| `K` / `↑` *(no modo resize)* | Aumentar altura |
| `J` / `↓` *(no modo resize)* | Diminuir altura |
| `Escape` / `Enter` *(no modo resize)* | Sair do modo resize (voltar ao padrão) |

### Estado e layout da janela

| Keybind | Função |
|---|---|
| `Alt + V` | Alternar direção do tiling (horizontal/vertical) |
| `Alt + Space` | Alternar foco entre janelas floating / tiling |
| `Alt + Shift + Space` | Alternar janela focada entre floating / tiling |
| `Alt + X` | Alternar janela focada entre maximizada / restaurada |
| `Alt + M` | Minimizar janela focada |
| `Alt + Shift + Q` | Fechar janela focada |

### Sistema / geral

| Keybind | Função |
|---|---|
| `Alt + Shift + E` | Encerrar o processo do GlazeWM com segurança |
| `Alt + Shift + R` | Recarregar o arquivo de configuração |
| `Alt + Enter` | Abrir terminal CMD |

### Workspaces (áreas de trabalho)

| Keybind | Função |
|---|---|
| `Alt + 1` … `Alt + 9` | Focar workspace 1 a 9 |
| `Alt + Y` | Focar o workspace usado mais recentemente |
| `Alt + T` | Focar o próximo workspace (definido em `workspaces`) |
| `Alt + Shift + T` | Focar o workspace anterior |
| `Alt + Shift + 1` … `Alt + Shift + 9` | Mover janela focada para o workspace 1–9 e focar nele |

### Monitores

| Keybind | Função |
|---|---|
| `Alt + A` | Mover workspace focado para o monitor à esquerda |
| `Alt + F` | Mover workspace focado para o monitor à direita |
| `Alt + D` | Mover workspace focado para o monitor acima |
| `Alt + S` | Mover workspace focado para o monitor abaixo |

---

![Infographic](/resources/assets/cheatsheet.png)

##  Documentação de configs

O arquivo de [config padrão](https://github.com/glzr-io/glazewm/blob/main/resources/assets/sample-config.yaml) é gerado em `%userprofile%\.glzr\glazewm\config.yaml`.

Para usar um local diferente, inicie o executável do GlazeWM com o argumento de CLI `--config="..."`:

```sh
./glazewm.exe start --config="C:\<PATH_TO_CONFIG>\config.yaml"
```

Ou defina a variável de ambiente `GLAZEWM_CONFIG_PATH`:

```sh
setx GLAZEWM_CONFIG_PATH "C:\<PATH_TO_CONFIG>\config.yaml"
```

A vantagem de usar um caminho customizado é poder escolher um nome diferente para o arquivo, como `glazewm.yaml`.

### Config: General

```yaml
general:
  # Comandos a executar quando o WM iniciar (ex.: rodar um script ou abrir
  # outro aplicativo).
  startup_commands: []

  # Comandos a executar pouco antes do WM ser encerrado.
  shutdown_commands: []

  # Comandos a executar depois que o config do WM for recarregado.
  config_reload_commands: []

  # Se deve focar automaticamente janelas sob o cursor.
  focus_follows_cursor: false

  # Se deve alternar entre o workspace focado anteriormente e o atual
  # ao focar o workspace atual novamente.
  toggle_workspace_on_refocus: false

  cursor_jump:
    # Se deve mover automaticamente o cursor no gatilho especificado.
    enabled: true

    # Gatilho para o salto do cursor:
    # - 'monitor_focus': Salta quando o foco muda entre monitores.
    # - 'window_focus': Salta quando o foco muda entre janelas.
    trigger: "monitor_focus"
```

### Config: Keybindings

Os atalhos de teclado disponíveis podem ser customizados pela opção `keybindings`. Um keybinding consiste em uma ou mais combinações de teclas e um ou mais comandos a executar quando pressionado.

É recomendado usar a tecla `alt` para keybindings. A tecla Windows é, infelizmente, difícil de remapear, já que o sistema operacional reserva certos atalhos (ex.: `lwin+l`).

```yaml
keybindings:
  # Comando(s) a executar.
  - commands: ["focus --workspace 1"]

    # Combinação(ões) de teclas para acionar o keybinding.
    bindings: ["alt+1"]

  # Múltiplos comandos podem ser executados em sequência (ex.: mover uma
  # janela para um workspace + focar o workspace).
  - commands: ["move --workspace 1", "focus --workspace 1"]
    bindings: ["alt+shift+1"]
```

**Lista completa de teclas que podem ser usadas em keybindings:**

| Tecla | Descrição |
|---|---|
| `a` - `z` | Teclas alfabéticas |
| `0` - `9` | Teclas numéricas |
| `numpad0` - `numpad9` | Teclas do teclado numérico |
| `f1` - `f24` | Teclas de função |
| `shift` | Tecla SHIFT (esquerda ou direita) |
| `lshift` | Tecla SHIFT esquerda |
| `rshift` | Tecla SHIFT direita |
| `control` | Tecla CTRL (esquerda ou direita) |
| `lctrl` | Tecla CTRL esquerda |
| `rctrl` | Tecla CTRL direita |
| `alt` | Tecla ALT (esquerda ou direita) |
| `lalt` | Tecla ALT esquerda |
| `ralt` | Tecla ALT direita |
| `lwin` | Tecla Windows ⊞ esquerda |
| `rwin` | Tecla Windows ⊞ direita |
| `space` | Barra de espaço |
| `escape` | Tecla ESC |
| `back` | Tecla BACKSPACE |
| `tab` | Tecla TAB |
| `enter` | Tecla ENTER |
| `left` | Seta ← |
| `right` | Seta → |
| `up` | Seta ↑ |
| `down` | Seta ↓ |
| `num_lock` | Tecla NUM LOCK |
| `scroll_lock` | Tecla SCROLL LOCK |
| `caps_lock` | Tecla CAPS LOCK |
| `page_up` | Tecla PAGE UP |
| `page_down` | Tecla PAGE DOWN |
| `insert` | Tecla INSERT |
| `delete` | Tecla DELETE |
| `end` | Tecla END |
| `home` | Tecla HOME |
| `print_screen` | Tecla PRINT SCREEN |
| `multiply` | Tecla `*` (apenas no numpad) |
| `add` | Tecla `+` (apenas no numpad) |
| `subtract` | Tecla `-` (apenas no numpad) |
| `oem_plus` | Tecla `=`/`+` em teclado padrão US (varia por layout) |
| `oem_comma` | Tecla `,`/`<` em teclado padrão US (varia por layout) |
| `oem_minus` | Tecla `-`/`_` em teclado padrão US (varia por layout) |
| `oem_period` | Tecla `.`/`>` em teclado padrão US (varia por layout) |
| `muhenkan` | Tecla 無変換 (non-convert) para layouts japoneses |
| `henkan` | Tecla 変換 (convert) para layouts japoneses |

> Se uma tecla não estiver na lista acima, ela ainda pode ser suportada usando seu caractere no keybinding (ex.: `alt+å` para o caractere norueguês Å).

> Teclados alemães e US internacionais tratam a tecla alt direita de forma diferente. Para esses layouts, use `ralt+ctrl` em vez de `ralt` para vincular a tecla alt direita.

### Config: Gaps

Os espaçamentos entre janelas podem ser alterados via a propriedade `gaps` no arquivo de config. Gaps internos e externos são configurados separadamente.

```yaml
gaps:
  # Espaço entre janelas adjacentes.
  inner_gap: "20px"

  # Espaço entre janelas e a borda da tela.
  outer_gap:
    top: "20px"
    right: "20px"
    bottom: "20px"
    left: "20px"
```

### Config: Workspaces

Workspaces precisam ser predefinidos via a propriedade `workspaces` no arquivo de config. Um workspace é atribuído automaticamente a cada monitor na inicialização.

```yaml
workspaces:
  # Este é o ID único do workspace. É usado nos comandos de keybinding,
  # e também é o rótulo mostrado em apps de terceiros (ex.: Zebar) caso
  # `display_name` não seja fornecido.
  - name: "1"

    # Override opcional do rótulo do workspace usado em apps de terceiros.
    # Não precisa ser único.
    display_name: "Work"

    # Opcionalmente força o workspace em um monitor específico, se existir.
    # 0 é a tela mais à esquerda, 1 é a próxima à direita, e assim por diante.
    bind_to_monitor: 0

    # Opcionalmente evita que o workspace seja desativado quando vazio.
    keep_alive: false
```

### Config: Window rules

Comandos podem ser executados quando uma janela é aberta pela primeira vez. Isso é útil para adicionar comportamentos específicos, como sempre abrir uma janela em fullscreen ou atribuí-la a um workspace específico.

Janelas podem ser filtradas por processo, classe e título. Múltiplos critérios podem ser combinados para atingir uma janela com mais precisão.

```yaml
window_rules:
  - commands: ["move --workspace 1"]
    match:
      # Move navegadores para o workspace 1.
      - window_process: { regex: "msedge|brave|chrome" }

  - commands: ["ignore"]
    match:
      # Ignora qualquer janela do Zebar.
      - window_process: { equals: "zebar" }

      # Ignora janelas picture-in-picture de navegadores.
      # Note que *ambos* título e classe precisam bater para a regra rodar.
      - window_title: { regex: "[Pp]icture.in.[Pp]icture" }
        window_class: { regex: "Chrome_WidgetWin_1|MozillaDialogClass" }
```

### Config: Window effects

Efeitos visuais podem ser aplicados às janelas via a opção `window_effects`. Atualmente, bordas coloridas são o único efeito disponível, com mais a caminho no futuro.

> Nota: Efeitos de janela são exclusivos do Windows 11.

```yaml
window_effects:
  # Efeitos visuais aplicados à janela focada.
  focused_window:
    # Destaca a janela com uma borda colorida.
    border:
      enabled: true
      color: "#0000ff"

  # Efeitos visuais aplicados às janelas não focadas.
  other_windows:
    border:
      enabled: false
      color: "#d3d3d3"
```

### Config: Window behavior

A opção de config `window_behavior` existe para customizar os estados que uma janela pode assumir (`tiling`, `floating`, `minimized` e `fullscreen`).

```yaml
window_behavior:
  # Novas janelas são criadas nesse estado sempre que possível.
  # Valores permitidos: 'tiling', 'floating'.
  initial_state: "tiling"

  # Define as opções padrão para quando uma nova janela é criada. Isso também
  # muda os padrões para quando comandos de mudança de estado, como
  # `set-floating`, são usados sem flags.
  state_defaults:
    floating:
      # Se deve centralizar janelas floating por padrão.
      centered: true

      # Se deve mostrar janelas floating sempre no topo.
      shown_on_top: false

    fullscreen:
      # Maximiza a janela se possível. Se a janela não tiver botão de
      # maximizar, ela será colocada em fullscreen normalmente.
      maximized: false
```

### Config: Binding modes

Binding modes são usados para modificar keybindings enquanto o GlazeWM está rodando.

Um binding mode pode ser ativado com `wm-enable-binding-mode --name <NAME>` e desativado com `wm-disable-binding-mode --name <NAME>`.

```yaml
binding_modes:
  # Quando ativado, a janela focada pode ser redimensionada via setas ou HJKL.
  - name: "resize"
    keybindings:
      - commands: ["resize --width -2%"]
        bindings: ["h", "left"]
      - commands: ["resize --width +2%"]
        bindings: ["l", "right"]
      - commands: ["resize --height +2%"]
        bindings: ["k", "up"]
      - commands: ["resize --height -2%"]
        bindings: ["j", "down"]
      # Pressione enter/escape para voltar aos keybindings padrão.
      - commands: ["wm-disable-binding-mode --name resize"]
        bindings: ["escape", "enter"]
```

---

##  FAQ

**P: Como faço o GlazeWM rodar na inicialização do Windows?**

Clique com o botão direito no ícone do GlazeWM na bandeja do sistema e selecione "Run on system startup".

**P: Como posso criar `<layout tal>`?**

Você pode criar layouts customizados mudando a direção do tiling com `alt+v`. Isso muda onde a próxima janela será posicionada *em relação à janela atual*. Se a direção da janela atual for horizontal, a nova janela será posicionada à direita dela. Se for vertical, será posicionada abaixo. Isso também se aplica ao mover janelas: a direção de tiling da janela parada afetará onde a janela movida será posicionada.

Scripts feitos pela comunidade como [Dutch-Raptor/GAT-GWM](https://github.com/Dutch-Raptor/GAT-GWM) e [burgr033/GlazeWM-autotiling-python](https://github.com/burgr033/GlazeWM-autotiling-python) podem ser usados para mudar automaticamente a direção do tiling. Suporte nativo para layouts automáticos não está *atualmente* disponível.

**P: Como crio uma regra para `<aplicativo tal>`?**

Para atingir um aplicativo específico, você precisa de um comando para executar e o nome do processo, título ou classe da janela. Por exemplo, se você usa o Flow-Launcher e quer que a janela de configurações abra como floating:

```yaml
window_rules:
  - commands: ["set-floating"]
    match:
      - window_process: { equals: "Flow.Launcher" }
        window_title: { equals: "Settings" }
```

Programas como Winlister ou o Window Spy do AutoHotkey podem ser úteis para obter informações sobre uma janela.

**P: Como posso ignorar os keybindings do GlazeWM quando `<aplicativo tal>` está focado?**

Isso não é suportado atualmente, porém o keybinding `alt+shift+p` no config padrão é usado para desativar todos os outros keybindings até que `alt+shift+p` seja pressionado novamente.

---

## 🔗 Links úteis

- [Releases / Changelog](https://github.com/glzr-io/GlazeWM/releases)
- [Discord](https://discord.gg/ud6z3qjRvM)
- [Config de exemplo (sample-config.yaml)](https://github.com/glzr-io/glazewm/blob/main/resources/assets/sample-config.yaml)
- [Contribuindo guide](https://github.com/glzr-io/glazewm/blob/main/Contribuindo.md)
- [Zebar (barra de status)](https://github.com/glzr-io/zebar)

[discord-badge]: https://img.shields.io/discord/1041662798196908052.svg?logo=discord&colorB=7289DA
[discord-link]: https://discord.gg/ud6z3qjRvM
[downloads-badge]: https://img.shields.io/github/downloads/glzr-io/glazewm/total?logo=github&logoColor=white
[downloads-link]: https://github.com/glzr-io/glazewm/releases
[issues-badge]: https://img.shields.io/badge/good_first_issues-7057ff
[issues-link]: https://github.com/orgs/glzr-io/projects/4/views/1?sliceBy%5Bvalue%5D=good+first+issue
[demo-video]: resources/assets/demo.webp
