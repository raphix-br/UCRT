# UCRT v0.1 — Especificação de Arquitetura

## 1. Escopo

A v0.1 define a arquitetura lógica e as fronteiras elétricas do Universal CRT Controller.

O objetivo não é reproduzir imediatamente toda a placa original do televisor. O objetivo é criar uma plataforma controladora que possa evoluir para diferentes CRTs através de módulos e perfis.

## 2. Objetivos

1. Processamento moderno de vídeo.
2. Entrada RGB e, futuramente, outras interfaces.
3. OSD/menu próprio.
4. Controle de geometria.
5. Arquitetura modular.
6. Perfil específico para cada CRT.
7. Separação entre lógica de controle e potência/deflexão.
8. Desenvolvimento incremental e documentado.

## 3. Não-objetivos da v0.1

A v0.1 não pretende:

- substituir o flyback;
- gerar a alta tensão do CRT;
- substituir imediatamente o estágio horizontal;
- substituir imediatamente o estágio vertical;
- definir uma placa universal de potência;
- assumir que dois CRTs possuem o mesmo yoke ou os mesmos parâmetros.

## 4. Arquitetura

### UCRT Core

Responsável por:

- MCU;
- processamento de vídeo;
- sincronismo;
- OSD;
- armazenamento/carregamento do CRT Profile;
- interface de usuário;
- geração dos sinais destinados aos módulos.

### RGB Module

Interface entre o processamento UCRT e o circuito RGB/neck board do CRT.

A topologia final dependerá do CRT Profile.

### Vertical Module

Módulo futuro para geração e amplificação da deflexão vertical.

Na v0.1, a deflexão vertical original permanece no televisor.

### Horizontal Module

Módulo futuro para controle da deflexão horizontal.

Na v0.1, o estágio horizontal original permanece no televisor.

### Power Module

Futuro módulo para alimentação das diferentes seções. Os domínios de tensão serão definidos após caracterização das cargas reais.

## 5. Estratégia de sinais

Os sinais devem ser classificados como:

- vídeo;
- sincronismo;
- controle;
- alimentação;
- deflexão;
- feedback.

Nenhum valor elétrico crítico deve ser considerado definitivo sem medição ou documentação confiável da unidade.

## 6. CRT Profile

Cada CRT terá um perfil contendo, no mínimo:

- fabricante/modelo;
- chassis;
- CRT/tubo;
- yoke;
- flyback;
- características RGB;
- parâmetros de geometria;
- parâmetros de sincronismo;
- limitações elétricas;
- módulos compatíveis;
- valores ainda não confirmados.

## 7. Filosofia de proteção

O UCRT deverá privilegiar:

- limites de corrente;
- proteção contra condições anormais;
- monitoramento de alimentação;
- fail-safe;
- isolamento adequado quando necessário;
- separação física entre lógica e potência;
- conectores chaveados para evitar conexões incorretas.

## 8. Conectores

A pinagem definitiva ainda não está definida.

Cada conector deverá possuir documentação própria contendo:

- nome;
- função;
- direção;
- domínio elétrico;
- tensão esperada;
- proteção;
- origem/destino;
- status de validação.

## 9. Desenvolvimento

### Fase 1
Caracterização do HPS-2073A/34BI.

### Fase 2
Protótipo UCRT de baixa tensão e interface de vídeo.

### Fase 3
Integração RGB.

### Fase 4
Controle/integração vertical.

### Fase 5
Controle/integração horizontal.

### Fase 6
Arquitetura modular de potência e perfis CRT.

### Fase 7
Primeiro controlador universal completo.

## 10. Referência de engenharia

O projeto open-source **td-crt**, de tdaede, é uma referência relevante de arquitetura de chassis CRT moderno. Ele não é uma especificação do UCRT e não deve ser copiado sem análise de licença, arquitetura e diferenças de aplicação.

## 11. Critério de conclusão da v0.1

A v0.1 será considerada especificada quando:

- as interfaces do primeiro protótipo estiverem definidas;
- os pontos de medição estiverem documentados;
- o CRT Profile #001 estiver preenchido com o que foi confirmado;
- os itens ainda desconhecidos estiverem explicitamente marcados;
- os diagramas corresponderem à arquitetura documentada.
