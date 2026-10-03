# UCRT — Universal CRT Controller

**Versão atual: v0.1.1**  
**Primeiro alvo:** CCE HPS-2073A — chassis 34BI — CRT de 20"

## 1. Visão do projeto

O UCRT (Universal CRT Controller) é um projeto de engenharia para desenvolver uma arquitetura modular capaz de controlar diferentes CRTs, separando processamento de vídeo, sincronismo, geometria, OSD e, futuramente, os estágios de deflexão e alta tensão.

O objetivo não é simplesmente construir uma placa substituta para uma televisão específica. A meta é criar uma plataforma modular, na qual o CRT e seus estágios elétricos possam ser descritos por um perfil e conectados a módulos compatíveis.

O primeiro equipamento é o CCE HPS-2073A, chassis 34BI, CRT de 20". Ele será o **CRT Profile #001**.

## 2. Estratégia de desenvolvimento

### v0.1 — Caracterização e arquitetura
A primeira versão não substitui toda a eletrônica original.

Serão mantidos inicialmente:
- flyback;
- alta tensão;
- estágio horizontal;
- estágio vertical;
- yoke horizontal;
- yoke vertical;
- neck board;
- alimentação original, quando conveniente.

O UCRT atuará inicialmente como controlador/processador.

### v0.2 — Vídeo/RGB
- entrada de vídeo;
- processamento RGB;
- OSD;
- brilho/contraste;
- blanking;
- sincronismo;
- interface com neck board;
- padrões de teste.

### v0.3 — Deflexão vertical
- módulo vertical;
- geração/controle de deflexão;
- controle de geometria vertical;
- possibilidade futura de substituir o LA78040N.

### v0.4 — Deflexão horizontal
- módulo horizontal;
- drive horizontal;
- estudo de energia recuperativa;
- possibilidade futura de substituir o estágio original.

### v0.5 — Modularização
- Core;
- RGB;
- Vertical;
- Horizontal;
- Power;
- CRT Profile.

### v1.0 — UCRT Universal
Plataforma capaz de trabalhar com diferentes CRTs através de módulos e perfis elétricos específicos.

## 3. Arquitetura

    UCRT CORE
    MCU + vídeo + OSD + sync + geometria
              |
        +-----+-----+-----+
        |           |     |
       RGB       VERTICAL HORIZONTAL
        |           |     |
    Neck board     Yoke V Yoke H
              |
          POWER / HV
        futuro modular

A arquitetura também considera como referência de engenharia o projeto open-source td-crt, de tdaede. O UCRT não será uma cópia dele.

## 4. UCRT Core

Funções previstas:
- microcontrolador;
- processamento de vídeo;
- sincronismo;
- OSD;
- geometria;
- controle de perfil CRT;
- interface de usuário;
- armazenamento de parâmetros;
- comunicação entre módulos;
- diagnóstico;
- padrões de teste.

O MCU definitivo ainda não foi escolhido.

## 5. Módulo RGB

Responsável por:
- entrada de vídeo;
- condicionamento;
- processamento;
- blanking;
- controle de amplitude;
- geração RGB;
- interface com neck board.

No HPS-2073A, a primeira versão deverá aproveitar a interface RGB existente até que os sinais sejam caracterizados fisicamente.

## 6. Módulo vertical

Futuro módulo para controlar/substituir o estágio vertical.

No chassis 34BI foi identificado:
- **LA78040N**;
- yoke vertical original.

Na v0.1 o LA78040N permanece no circuito.

## 7. Módulo horizontal

Futuro módulo para assumir o controle do estágio horizontal.

Na v0.1 permanecem:
- estágio horizontal original;
- flyback;
- yoke horizontal;
- alta tensão original.

## 8. Alta tensão

A alta tensão permanece original na v0.1. A modularização de HV será tratada somente em etapas posteriores.

## 9. CRT Profile

Cada CRT deverá possuir:
- fabricante/modelo;
- chassis;
- tubo;
- código do yoke;
- resistência/indutância do yoke;
- flyback;
- B+;
- interface RGB;
- parâmetros de geometria;
- tensões;
- sinais H/V;
- limitações e proteções.

Primeiro perfil: **CRT Profile #001 — CCE HPS-2073A / chassis 34BI**.

## 10. HPS-2073A / 34BI — dados encontrados

A documentação do chassis 34BI permitiu identificar a arquitetura geral e componentes importantes.

### CIs identificados
- **TDA9570H**
- **LA78040N**
- **TEA1533AT**
- **TDA1013B**
- **TDA1517**
- EEPROM da família **BR24C08 / M24C08**

O TDA9570H é um dos componentes centrais do chassis, associado ao processamento de vídeo/áudio, sincronismo e controle.

Também foram identificados:
- HOUT;
- sinais de drive vertical;
- I²C SDA/SCL;
- caminhos RGB/cátodo;
- yoke horizontal;
- yoke vertical;
- flyback/HV;
- alimentação;
- teclado/controle remoto.

## 11. Parâmetros de geometria encontrados

Valores encontrados na documentação de serviço do 34BI e registrados apenas como referência inicial:

| Parâmetro | Valor |
|---|---:|
| HSh | 45 |
| VSl | 30 |
| VAm | 44 |
| VSh | 32 |
| SC | 14 |
| HzPl | 32 |
| HBow | 32 |
| EW | 34 |
| PW | 35 |
| EWUC | 35 |
| EWLC | 35 |
| TC | 33 |

Esses valores não são universais. Podem variar conforme modelo, revisão da PCB, tubo e configuração.

## 12. O que ainda precisa ser confirmado no aparelho

- código exato do tubo;
- código do yoke;
- resistência dos enrolamentos;
- indutância dos enrolamentos;
- código do flyback;
- B+ real;
- interface física RGB da neck board;
- sincronismo;
- waveform H;
- waveform V;
- tensões relevantes;
- conectores/pinagem;
- revisão da PCB;
- diferenças entre documentação e unidade física.

**Regra:** nenhum pinout, tensão ou waveform será considerado definitivo apenas por documentação genérica. Será marcado como confirmado somente após validação física ou documentação específica da revisão.

## 13. Interface e conectores

Interfaces previstas:
- Core ↔ RGB;
- Core ↔ Vertical;
- Core ↔ Horizontal;
- Core ↔ Power;
- Core ↔ CRT Profile.

O pinout definitivo depende da caracterização elétrica.

## 14. Referência td-crt

O projeto td-crt, de tdaede, foi identificado como referência relevante. Entre os blocos estudados:
- MCU;
- H/V deflection;
- RGB amplifier;
- B+ supply;
- ±12 V;
- heater;
- HV/focus/screen;
- RGB input;
- RGB output.

Também foram observadas técnicas como software PLL, processamento RGB, rampa vertical e estágios de deflexão dedicados.

## 15. Segurança

CRT envolve riscos de alta tensão e energia armazenada.

Áreas críticas:
- flyback/anodo;
- capacitores;
- estágio horizontal;
- estágio vertical;
- fonte chaveada;
- neck board;
- cargas armazenadas após desligamento.

A v0.1 prioriza desenvolvimento em baixa tensão e manutenção dos estágios originais.

Não serão incorporadas instruções casuais para aterramento, curto deliberado ou manipulação de pontos de alta tensão em equipamento energizado.

## 16. Estrutura

    UCRT/
    ├── README.md
    ├── CHANGELOG.md
    ├── docs/
    │   ├── UCRT_Architecture_v0.1.md
    │   ├── HPS-2073A_34BI_Profile.md
    │   ├── Safety.md
    │   ├── Development_Roadmap.md
    │   ├── Measurement_Plan_HPS-2073A_34BI.md
    │   ├── Interface_Matrix_v0.1.md
    │   └── CRT_Profile_Schema.md
    ├── diagrams/
    │   ├── HPS-2073A_34BI.svg
    │   ├── UCRT_Architecture.svg
    │   └── UCRT_Signal_Flow.svg
    ├── hardware/
    │   ├── core/
    │   ├── rgb/
    │   ├── vertical/
    │   ├── horizontal/
    │   ├── power/
    │   └── crt_profiles/
    ├── firmware/
    └── references/
        └── HPS-2073A_34BI/

As pastas foram preparadas para esquemas, PCB, firmware, perfis e referências.

## 17. Estado atual

### Concluído
- [x] Repositório criado.
- [x] Arquitetura modular definida.
- [x] HPS-2073A/34BI escolhido como primeiro alvo.
- [x] CRT Profile #001 iniciado.
- [x] Componentes principais identificados.
- [x] Parâmetros de geometria documentados.
- [x] Estratégia de manter HV/deflexão original na v0.1 definida.
- [x] Diagramas SVG criados.
- [x] Segurança documentada.
- [x] Roadmap definido.
- [x] Estrutura de hardware/firmware/referências preparada.

### Em aberto
- [ ] Identificar tubo exato.
- [ ] Identificar yoke.
- [ ] Confirmar pinagem.
- [ ] Confirmar RGB.
- [ ] Confirmar H/V.
- [ ] Confirmar B+.
- [ ] Mapear conectores.
- [ ] Fechar matriz de interfaces.
- [ ] Definir MCU.
- [ ] Criar esquemático.
- [ ] Criar PCB.
- [ ] Construir protótipo.
- [ ] Validar no aparelho.

## 18. Próximo marco técnico

O próximo marco não é fabricar a PCB.

É:

**Caracterizar eletricamente o HPS-2073A/34BI e transformar a documentação existente em uma especificação de interfaces verificadas.**

Fluxo:

    TV original
       ↓
    levantamento físico
       ↓
    matriz de interfaces
       ↓
    CRT Profile #001
       ↓
    especificação elétrica UCRT v0.1
       ↓
    esquemático
       ↓
    PCB
       ↓
    protótipo
       ↓
    validação

A PCB será projetada a partir dos dados confirmados.

## 19. Filosofia

O UCRT deverá ser:
- modular;
- documentado;
- reparável;
- reproduzível;
- baseado em perfis;
- independente de um único modelo;
- progressivamente substituível;
- seguro para desenvolvimento;
- aberto a diferentes arquiteturas de MCU e vídeo.

A prioridade é construir uma plataforma sólida começando por um CRT real e conhecido.
