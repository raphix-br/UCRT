# Segurança — CRT

CRT não deve ser tratado como uma placa eletrônica convencional.

## Riscos principais

- alta tensão no circuito de CRT;
- energia armazenada em capacitores;
- flyback e circuito de foco/screen;
- tensões presentes no neck board;
- correntes elevadas em estágios de deflexão;
- risco de dano ao tubo e aos componentes por conexão incorreta.

## Regra de desenvolvimento

O UCRT v0.1 deve ser desenvolvido preferencialmente com a parte de controle e vídeo em baixa tensão, mantendo os circuitos originais de HV e deflexão.

Não utilizar instruções de aterramento, curto ou manipulação de pinos em placa energizada como procedimento de desenvolvimento.

Medições em equipamento energizado exigem instrumentação apropriada, isolamento quando aplicável, pontas/probes adequadas e experiência específica com CRT.

## Filosofia

Primeiro caracterizar.

Depois especificar.

Depois prototipar.

Só então substituir um estágio de potência.
