# CRT Profile #001 — CCE HPS-2073A / 34BI

## Identificação

- Fabricante: CCE
- Modelo: HPS-2073A
- Família/chassis: 34BI
- CRT: 20"
- Perfil UCRT: #001

## Componentes identificados na documentação 34BI

A documentação da família 34BI identifica, entre outros:

- TDA9570H
- LA78040N
- TEA1533AT
- TDA1013B
- TDA1517
- EEPROM da família 24C08

O TDA9570H atua como elemento central de processamento/controle de áudio e vídeo, sincronismo e microcontrolador do chassis.

## Bloco funcional

```
Entrada RF/AV
     │
     ▼
┌───────────────┐
│   TDA9570H    │
│ vídeo/sync/   │
│ OSD/controle  │
└───┬───────┬───┘
    │ RGB   │ H/V
    │       │
    ▼       ├──────────────► H original
 Neck board │
    │       └──────────────► V / LA78040N
    ▼
   CRT
```

O diagrama é funcional. A pinagem e os pontos elétricos exatos devem ser confirmados na documentação correspondente à revisão da unidade física.

## Geometria documentada

Parâmetros de serviço encontrados para a família 34BI incluem:

| Parâmetro | Valor padrão documentado |
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

Esses valores são **referência inicial de serviço**, não valores universais do tubo. A revisão do chassis e a unidade física devem prevalecer.

## Interfaces de controle

A família 34BI utiliza barramento I²C para elementos de controle/configuração, incluindo SDA/SCL.

## V0.1 — o que permanece original

- flyback/HV;
- estágio horizontal;
- estágio vertical;
- yoke;
- fonte original, quando compatível com a estratégia do protótipo;
- demais circuitos de potência não necessários à primeira prova.

## A confirmar na unidade física

- código exato do tubo CRT;
- código e características do yoke;
- resistência e indutância dos enrolamentos;
- código exato do flyback;
- valor real de B+;
- interface RGB da neck board;
- amplitudes e formas de onda H/V nos pontos relevantes;
- tensões de alimentação relevantes;
- diferenças de revisão da PCB;
- conectores e pinagem efetivamente presentes.

## Observação

Não assumir que todos os televisores 34BI são eletricamente idênticos apenas por compartilharem o número do chassis.
