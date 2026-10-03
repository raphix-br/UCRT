# UCRT — Roadmap

## v0.1 — Caracterização e arquitetura

- Repositório e documentação.
- Perfil HPS-2073A/34BI.
- Diagramas.
- Definição das interfaces.
- Identificação dos pontos ainda desconhecidos.

## v0.2 — Vídeo/RGB

- Protótipo do UCRT Core.
- Entrada de vídeo.
- Processamento.
- OSD.
- Interface RGB.
- Testes inicialmente fora do CRT quando possível.

## v0.3 — Vertical

- Caracterização completa do estágio LA78040N.
- Definição de interface UCRT.
- Desenvolvimento de módulo vertical.
- Proteções e testes controlados.

## v0.4 — Horizontal

- Caracterização do estágio horizontal.
- Sincronismo/PLL.
- Desenvolvimento do módulo horizontal.
- Proteções.

## v0.5 — Modularização

- Conectores padronizados.
- CRT Profiles.
- Separação Core/RGB/V/H/Power.
- Primeiro desenho de PCB modular.

## v1.0 — Universal CRT Controller

Objetivo de arquitetura:

```
             UCRT CORE
                 │
       ┌─────────┼─────────┐
       ▼         ▼         ▼
      RGB        V         H
       │         │         │
       └─────────┼─────────┘
                 ▼
            CRT PROFILE
                 │
        CRT/Yoke/Flyback
```

A compatibilidade será determinada por perfil e módulos adequados, e não pela tentativa de usar uma única saída de potência para todos os CRTs.
