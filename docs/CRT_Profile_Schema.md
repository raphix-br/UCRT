# UCRT CRT Profile Schema

Cada CRT suportado pelo UCRT deverá possuir um perfil próprio.

## Identificação
- Profile ID
- fabricante
- modelo
- chassis
- revisão
- tamanho do CRT
- código do tubo

## Yoke
- código
- resistência H
- resistência V
- indutância H
- indutância V
- tipo de conexão
- observações

## Horizontal
- estágio original
- IC
- frequência nominal
- B+
- interface de drive
- flyback
- observações

## Vertical
- estágio original
- IC
- frequência nominal
- interface de drive
- yoke
- observações

## RGB
- interface
- níveis
- impedância
- blanking
- polaridade
- neck board
- observações

## Geometria
- HSh
- VSh
- VAm
- VSl
- SC
- EW
- PW
- HBow
- HzPl
- TC
- parâmetros específicos

## Segurança / limites
- limites conhecidos
- proteções
- condições proibidas
- dados não confirmados

## Estado
Cada campo deve ser marcado como:
- DOCUMENTAL
- MEDIDO
- CONFIRMADO
- PROVISÓRIO
- DESCONHECIDO
