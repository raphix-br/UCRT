# Plano de Caracterização — CCE HPS-2073A / 34BI

## Objetivo

Transformar a documentação do chassis 34BI em uma especificação elétrica verificável para o UCRT.

A caracterização deve começar com o aparelho desenergizado sempre que possível.

## 1. Identificação física

Registrar:
- modelo completo;
- revisão da PCB;
- código do CRT;
- código do yoke;
- código do flyback;
- conectores;
- fotografias gerais da PCB;
- fotografias dos conectores e etiquetas.

## 2. Mapeamento desenergizado

Levantar:
- continuidade dos enrolamentos do yoke;
- identificação dos conectores;
- trilhas entre conectores e CIs;
- linhas RGB;
- linhas de sincronismo;
- alimentação;
- correspondência entre PCB e esquema.

Registrar instrumento e condição da medição.

## 3. Mapeamento de sinais

| Sinal | Origem | Destino | Domínio | Documentação | Confirmado |
|---|---|---|---|---|---|
| RGB | a determinar | neck board | analógico | sim | não |
| HOUT | TDA9570H | estágio H | a determinar | sim | não |
| V drive | TDA9570H | LA78040N | a determinar | sim | não |
| SDA | controle | I²C | digital | sim | não |
| SCL | controle | I²C | digital | sim | não |

## 4. Medições energizadas

Somente após o mapeamento básico e utilizando instrumentação apropriada.

Registrar:
- B+;
- alimentações de baixa tensão;
- sinais H/V;
- amplitude;
- frequência;
- forma de onda;
- referência de medição;
- condição do aparelho.

Não presumir que valores da documentação genérica sejam iguais aos da unidade física.

## 5. Resultado esperado

Ao final deverá existir uma tabela de interfaces suficientemente confiável para permitir o primeiro esquemático UCRT.

**Nenhuma PCB deve ser fechada com base exclusivamente em valores não confirmados.**
