# UCRT — Universal CRT Controller

**Version: v0.1.0**

Projeto de engenharia para desenvolvimento de um controlador modular e universal para displays CRT, começando pelo **CCE HPS-2073A / chassis 34BI**.

## Objetivo

Desenvolver uma arquitetura moderna e modular capaz de assumir progressivamente o processamento de vídeo, OSD, controle de geometria e, em versões futuras, os estágios de deflexão de diferentes CRTs.

A estratégia inicial é **não substituir toda a eletrônica da TV de uma vez**.

### UCRT v0.1

Na primeira etapa, o UCRT deverá atuar como controlador/processador, mantendo a eletrônica original de:

- alta tensão (HV);
- flyback;
- deflexão horizontal;
- deflexão vertical;
- yoke;
- neck board, conforme necessário.

Isso permite validar a arquitetura sem começar pelo estágio de maior risco e complexidade.

## Arquitetura

```
                 ┌─────────────────────┐
                 │      UCRT CORE      │
                 │ MCU + vídeo + OSD   │
                 │ controle/geometry   │
                 └──────────┬──────────┘
                            │
             ┌──────────────┼──────────────┐
             ▼              ▼              ▼
        ┌─────────┐    ┌─────────┐    ┌─────────┐
        │   RGB   │    │ V-DRIVE │    │ H-DRIVE │
        │ MODULE  │    │ MODULE  │    │ MODULE  │
        └─────────┘    └─────────┘    └─────────┘
             │              │              │
             ▼              ▼              ▼
          Neck CRT         Yoke V         Yoke H
```

Os módulos de deflexão serão desenvolvidos apenas depois que suas interfaces forem suficientemente caracterizadas.

## CRT Profile #001

**CCE HPS-2073A — chassis 34BI — CRT 20"**

A documentação de serviço da família 34BI será utilizada como referência inicial. Valores e interfaces que dependam da revisão física da placa serão marcados como **a confirmar**.

## Estrutura

- `docs/` — especificações e documentação de engenharia
- `diagrams/` — diagramas vetoriais SVG
- `hardware/` — futuras placas e módulos
- `firmware/` — firmware do controlador
- `references/` — documentação de referência

## Segurança

CRT envolve alta tensão, energia armazenada e circuitos capazes de produzir choques perigosos. O UCRT v0.1 deve priorizar desenvolvimento em baixa tensão e preservar os estágios originais de HV/deflexão. Qualquer medição em equipamento energizado deve ser feita com instrumentação apropriada e procedimentos de segurança para CRT.

## Status

**v0.1.0 — Arquitetura inicial definida.**

Este projeto é desenvolvido de forma incremental. Alterações relevantes devem ser registradas no `CHANGELOG.md`.
