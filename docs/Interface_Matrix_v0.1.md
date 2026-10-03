# UCRT v0.1 — Interface Matrix

Status inicial: **não validado fisicamente**

| Interface | Origem | Destino | Tipo | Status |
|---|---|---|---|---|
| RGB | processamento original / futuro UCRT | neck board | vídeo analógico | documental |
| HOUT | TDA9570H | estágio horizontal | drive | documental |
| V DRIVE | TDA9570H | LA78040N | deflexão | documental |
| SDA | controle | dispositivos I²C | digital | documental |
| SCL | controle | dispositivos I²C | digital | documental |
| Yoke H | estágio H | yoke horizontal | potência | não caracterizado |
| Yoke V | LA78040N | yoke vertical | potência | não caracterizado |
| HV | flyback | CRT | alta tensão | original |
| B+ | fonte | estágio H | alimentação | não caracterizado |

## Estados

- **documental:** encontrado na documentação.
- **não caracterizado:** ainda não medido/confirmado na unidade.
- **confirmado:** validado fisicamente.
- **provisório:** útil, mas sujeito a revisão.
