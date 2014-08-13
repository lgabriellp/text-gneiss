Referências de RSSF com Monitoramento
=====================================

Octopus
-------

Texto no papel

Gigascope
---------

Gigascope [1] é um mecanismo de consulta SQL que visa monitorar pacotes
recebidos diretamente nas interfaces de rede, proporcionando um uma visão
de tempo real sobre o fluxo de dados. Os dados são organizados e
pré-processados de forma que possam ser consultados de forma agil e precisa.
Segundo Gigascope, as ferramentas pré-existentes tem grandes limitações.
TCP Dump [2] é flexível, mas não é rápido o suficiente para analizar grandes
quantidades de dados de redes Gigabit em hardware barato. SNMP [3], RMON [4]
e NetFlow [5] são rápidos, mas são inflexíveis. Outro problema com essas
ferramentas é a baixa capacidade de fazer consultas. Normalmente, a saída
destas ferramentas é guardada em arquivos para análise posterior. Tendo
que extrair manualmente as informações, o analista precisa tratar toda a
complexidade dos dados, relacionar os valores e agrega-los. Este processo
pode levar a enganos que poderão levar a análises incorretas ou sem a devida
precisão. 

Monitoring Distributed Systems Article
--------------------------------------

Definição: Um objeto administrado [6] é um objeto cujo comportamento pode ser
controlado por um sistema administrativo e deve ter dois tipos de interface. A
primeira dá suporte ao funcionamento normal do objeto, servindo ao propósito 
principal do serviço fornecido por ele. A segunda é administrativa e dá suporte
as ao monitoramento e o controle deste objeto.

Definição: O status de um objeto administrado é uma medida do seu comportamento
em um determinado momento representado pelo conjunto de seus atributos. Um
evento é uma entidade que reflete uma mudança instantânea de status. Existem
três tipos de eventos de interesse em sistemas distribuidos (Sérá que deveríamos
incluir mais algum para RSSF?), de nível de fluxo de controle (quando o processo
atinge um certo ponto no código), de nível de fluxo de dados (quando o processo
muda o valor de uma variável) e de nível de processo (quando processos iniciam,
terminam ou se comunicam). Os níveis de fluxo de dados e de controle, são eventos
internos o nível de processo é externo.

Eventos de nível interno são úteis para fins de depuração (meio óbvio).
Segundo [6], o nível externo é o nível correto para monitoramento de sistemas
distribuídos.

Referências
-----------

[1] Gigascope: High Performance Network Monitoring with an SQL Interface
[2] TCP Dump
[3] SNMP
[4] RMON
[5] NetFlow
[6] Monitoring Distributed Systems
