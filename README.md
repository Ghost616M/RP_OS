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


| Desktop e Multitarefa | Controle de GPIO e I2C |
| :---: | :---: |
| ![Desktop](https://private-user-images.githubusercontent.com/140211256/713954576-1283b2f7-6d65-4d64-8f81-6c64f8fcbaf5.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3OTUyMDI1MzksIm5iZiI6MTc5NTIwMjIzOSwicGF0aCI6Ii8xNDAyMTEyNTYvNzEzOTU0NTc2LTEyODNiMmY3LTZkNjUtNGQ2NC04ZjgxLTZjNjRmOGZjYmFmNS5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYxMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MTEyMFQxOTE3MTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMDBjZjg4NmZlY2Y5YWM5ZGUwODUxNmQyZGYwMjc1NGZjMmU0MDY1MjRhODk2ODE3MjRkYTE0ZWRhNzk1OWMwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZqcGVnIn0.di9MXB7j-BNocc5Bi8LC6fZEOJ9yu8AxbVWgpHd_L80) | ![GPIO](https://private-user-images.githubusercontent.com/140211256/713954627-74851fc7-2b0d-48ca-ac19-8f3174177c42.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3OTUzMDg5NTYsIm5iZiI6MTc5NTMwODY1NiwicGF0aCI6Ii8xNDAyMTEyNTYvNzEzOTU0NjI3LTc0ODUxZmM3LTJiMGQtNDhjYS1hYzE5LThmMzE3NDE3N2M0Mi5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYxMTIyJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MTEyMlQwMDUwNTZaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1jMmQ5MjBkZDA4ZmExNWJhYTA3M2RjOTg2NTA2ODFhOWZiNmUxMzhhZjk1M2RhZWFmMjZhN2NlMzlmOTQ5YTRiJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZqcGVnIn0.jzXzi9mUjekm94DfQupreCOJgm4V57DRkKZhg_vKZOM) |

| Diagnóstico de Rede & USB | Monitor do Sistema (Sysmon) |
| :---: | :---: |
| ![Rede](https://private-user-images.githubusercontent.com/140211256/713956296-6d3609d9-9738-4328-8e3b-d0320e108b11.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3OTUyMDI3NDQsIm5iZiI6MTc5NTIwMjQ0NCwicGF0aCI6Ii8xNDAyMTEyNTYvNzEzOTU2Mjk2LTZkMzYwOWQ5LTk3MzgtNDMyOC04ZTNiLWQwMzIwZTEwOGIxMS5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYxMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MTEyMFQxOTIwNDRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1iZGM2ODhhMjc5Yjc5NDIxOGZjYjA1YjFlN2Y5ZDBjNWUxMzBiNGNmYmY1OGM4ZWMyMzQ5MWZhMWYwYTRiOTFjJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZqcGVnIn0.d8O-FuaXV9mhl5fVpxPbpAkXeRk6tbA6Ptuhv21wCW8) | ![Sysmon](https://private-user-images.githubusercontent.com/140211256/713956325-49d51667-1f9d-4a50-b729-f438b2792c25.jpg?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3OTUyMDI3NDQsIm5iZiI6MTc5NTIwMjQ0NCwicGF0aCI6Ii8xNDAyMTEyNTYvNzEzOTU2MzI1LTQ5ZDUxNjY3LTFmOWQtNGE1MC1iNzI5LWY0MzhiMjc5MmMyNS5qcGc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYxMTIwJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MTEyMFQxOTIwNDRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01YzJhZmRmNjY5OTdjMjBlMzNlYzc0YjYyMjNhNzYxNTBlNWIxODQzNmU1YzlmN2RhYmQyNjUxNzE2OTJmYjc3JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZyZXNwb25zZS1jb250ZW50LXR5cGU9aW1hZ2UlMkZqcGVnIn0._3VwyIdeMqPVfAcBj1AGHfEY3ZIQ4Ay3ZSOtLtcXGwM) |

---

## 🚀 Como Instalar e Testar

1. Baixe o arquivo **`rp_os.uf2`** disponível na raiz deste repositório (ou na aba *Releases*).
2. Segure o botão **BOOT** da sua **Waveshare RP2350-PiZero** e conecte-a ao computador via cabo USB (ou pressione **RESET** enquanto segura **BOOT**).
3. A placa aparecerá como uma unidade de armazenamento removível (`RP2350`).
4. Copie o arquivo `rp_os.uf2` para dentro dessa unidade. A placa reiniciará automaticamente no **RP_OS**.
5. Conecte seu monitor na porta Mini-HDMI/DVI e seus periféricos (teclado, mouse, pendrive ou adaptador Wi-Fi) na porta USB Host.

---

## peço desculpas mais eu deixo o resto com vcs, eu não tenho a capacidade, nem acesso a ferramentas, e eu uso o celular pra programar, vcs já devem saber que isso torna as coisas mais limitadas, então eu me despeço e agradeço por vcs esperimentarem esse projeto, o código fonte eu deixei zipado porque foi mais rápido, se quiserem implementar ou usar para criar seus próprios projetos, tem meu total consentimento, esse sistema pertence a todos, até mais.
