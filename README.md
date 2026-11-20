# 🖥️ RP_OS — Sistema Operacional Gráfico para Waveshare RP2350-PiZero

O **RP_OS** é um sistema operacional nativo e experimental escrito em **C/C++**, desenvolvido especificamente para extrair todo o potencial de hardware da placa **Waveshare RP2350-PiZero**. 

Diferente de emuladores tradicionais, o RP_OS roda nativamente no microcontrolador RP2350, oferecendo um ambiente gráfico completo estilo desktop com suporte a múltiplas janelas, periféricos USB simultâneos, rede Wi-Fi e ferramentas de diagnóstico de hardware.

> *Projeto desenvolvido do zero com assistência de Inteligência Artificial e refinamentos manuais.*

---

## ✨ Principais Recursos

### 🪟 Interface Gráfica (GUI) e Desktop
* **Gerenciador de Janelas Completo:** Suporte a múltiplas janelas simultâneas com redimensionamento dinâmico, minimização, movimentação e sobreposição.
* **Barra de Tarefas Inteligente:** Menu iniciar, alternância entre janelas abertas (com adaptação automática de tamanho), relógio e monitoramento de temperatura da CPU em tempo real.
* **Personalização em Tempo Real:** Sistema de temas dinâmicos (*Azul Clássico*, *Dark Cyber*, *Matrix Verde* e *Cinza Retro*) aplicados instantaneamente em toda a interface.
* **Configuração de Mouse:** Ajuste de velocidade/DPI do cursor (0.5x a 2.0x) e opção para inversão de botões.

### 🔌 Hardware, USB e Conectividade
* **Saída de Vídeo DVI/HDMI:** Renderização gráfica nativa pela porta integrada da placa.
* **Pilha USB Host Completa:** Suporte simultâneo via hub USB para **teclado**, **mouse**, **pendrives (Mass Storage)** e **adaptadores de rede**.
* **Suporte a Wi-Fi Atheros (AR9271):** Detecção nativa de adaptadores USB (VID:PID `0CF3:9271`), diagnóstico de status, MAC, DHCP e tráfego RX/TX.
* **Controle de Clock (Overclock / Reclock):** Ajuste dinâmico da frequência de operação do RP2350 diretamente pelo sistema.

---

## 🛠️ Aplicativos Integrados

* **Terminal (Shell):** Linha de comando estilo Unix com suporte a comandos de sistema, arquivos e rede (`ls`, `cd`, `cat`, `mkdir`, `rm`, `cp`, `mv`, `touch`, `df`, `mount`, `lsusb`, `i2cscan`, `ifconfig`, `ping`, `wifi`, `sysinfo`, `free`, `reboot`, `bootsel`).
* **Gerenciador de Arquivos:** Navegação visual unificada entre memória **Flash**, **Cartão microSD (`/sd`)** e **Pendrive USB**, permitindo criar, abrir e apagar arquivos.
* **Editor de Texto:** Editor integrado com suporte a atalhos de teclado (`Ctrl+S` para salvar) e contador de linha/coluna.
* **Controle de GPIO & I2C:** Painel visual para monitoramento e acionamento em tempo real dos pinos (`P00` a `P27`), controle PWM e scanner de barramento I2C.
* **Sysmon (Monitor do Sistema):** Acompanhamento de frequência da CPU (dual-core), temperatura do chip, uptime, dispositivos USB conectados e uso de armazenamento.
* **Gerenciador de Rede:** Ferramenta dedicada para visualizar dispositivos no hub USB, gerenciar DHCP e monitorar o adaptador Wi-Fi.

---

## 📸 Capturas de Tela

*(Dica: Suba suas fotos em uma pasta `assets/` ou `screenshots/` no repositório e substitua os links abaixo)*

| Desktop e Multitarefa | Controle de GPIO e I2C |
| :---: | :---: |
| ![Desktop](screenshots/desktop.png) | ![GPIO](screenshots/gpio.png) |

| Diagnóstico de Rede & USB | Monitor do Sistema (Sysmon) |
| :---: | :---: |
| ![Rede](screenshots/rede.png) | ![Sysmon](screenshots/sysmon.png) |

---

## 🚀 Como Instalar e Testar

1. Baixe o arquivo **`rp_os.uf2`** disponível na raiz deste repositório (ou na aba *Releases*).
2. Segure o botão **BOOT** da sua **Waveshare RP2350-PiZero** e conecte-a ao computador via cabo USB (ou pressione **RESET** enquanto segura **BOOT**).
3. A placa aparecerá como uma unidade de armazenamento removível (`RP2350`).
4. Copie o arquivo `rp_os.uf2` para dentro dessa unidade. A placa reiniciará automaticamente no **RP_OS**.
5. Conecte seu monitor na porta Mini-HDMI/DVI e seus periféricos (teclado, mouse, pendrive ou adaptador Wi-Fi) na porta USB Host.

---

## 🤝 Contribuições e Sugestões

O projeto está em desenvolvimento ativo! Sinta-se à vontade para abrir **Issues** com sugestões de melhorias, relatar bugs ou enviar **Pull Requests**.
