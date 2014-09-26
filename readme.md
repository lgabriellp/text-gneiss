Gneiss (revisar) 
======

Introdução
----------

### Redes de Sensores Sem Fio

Definição retirada de [Wireless Sensor Networks Survey][1].

São compostas por dezenas a milhares de nós sensores capazes de sendir, medir e
coletar informações sobre o ambiente e baseado em algum processo de decisão, transmitir
essas informações ao usuário final.

Os nós que compõem uma rede de sensores sem fio são dispositivos de baixa potência
com um ou mais sensores, um processador, memória, uma fonte de energia, um rádio e
possivelmente um atuador.

Os sensores podem ser natureza variada: mecânicas, termais, biológicas, químicas,
óticas e mágnéticas, e podem ser acopladas conforme a característica das medidas
a serem coletadas.

Como as *RSSF* podem ser implantadas em terrenos de difícil acesso e possuem pouca
memória, a comunicação por rádio é necessária para que os dadas alcancem uma estação
base. Por sua vez, a estação base irá exibir ao usuário da RSSF os dados coletados.

A bateria é a fonte principal de energia para os nós. Apesar disso, outras fontes
podem ser acopladas. Fontes como paineis solares.

As aplicações podem ser as mais variadas. Detecção de intrusos em áreas militares,
monitoramento de condições climáticas e geológicas, acompanhamendo da produção industrial
e monitoramento de animais em seu habtat são alguns exemplos.

Diferentemente das redes de computadores tradicionais, as *RSSF* tem seus próprios
fatores limitantes. Restrições como limitada oferta de energia, baixa amplitude de
comunicação, pequena largura de banda e limitada capacidade de armazenamento faz com
que a aplicação desejada e o ambiente de implantação tenham papel fundamental em
decisões de projeto tais como tamanho da rede, forma de implantação e topologia.

[1](1-s2.0-S1389128608001254-main.pdf)

* [Redes de Sensores Sem Fio](rssf.md)
* [Monitoramento](monitoramento.md)
* [Trabalhos Relacionados](relacionados.md)

Objetivos
---------

1. Simplificar o estudo de redes de sensores sem fio:

2. Limitar a dependência de dispositivos reais:
    A complexidade comercial e custos elevados impostos na importação dos dispositívos
necessários (Aqui um comentário do Claudio) alargam o tempo desde a primeira iniciativa
de compra até o dispositivo chegar a mão do pesquisador. Esta complexidade amplia o risco
da aquisição de dispositivos que não correspondem ao potencial esperado nas aplicações
envolvidas, aumenta a defasagem dos dispositivos utilizados em relação ao mercado e retarda
pesquisas que necessitam de maior número de dispositivos pois novas remessas precisariam
de mais tempo ainda para serem concretizadas.

3. Entender melhor os dados gerados nos experimentos:

4. Agilizar conclusões e a transferência de conhecimento:

Conceito
--------

Processo contínuo e cíclico contendo as etapas:

### Ponto de vista Matemático

#### Identificação de Hipótese
#### Coleta dos dados
#### Teste da Hipótese
#### Aperfeiçoamento

### Ponto de vista tecnológico

#### Extração de dados sensoriais
#### Manipulação e Persistência
#### Visualização Gráfica

Implementação
-------------

### Node Gneiss
### Java Gneiss
### Java Gneiss Test
### Sunspot Simple

Utilização
----------

### Instalação
### Configuração
### Tutorial
### Extensão

Testes
------

### Rossan
### De terceiros

Apêndice
--------

### Ferramentas Utilizadas

#### MongoDB
#### Node.js
#### Gráficos

### Protocolos Utilizados

#### Http
#### Json

Versão antiga Abaixo
====================

*Gneiss* é um gerenciador de emulações de *Redes de Sensores Sem Fio (RSSF)*
que utiliza a plataforma SunSPOT de dispositivos da Oracle. Ele foi criado
com o objetivo de facilitar a emulação de ambientes de *RSSF* com as
seguintes características:

* (1) Grande número de nós na rede;
* (2) Grande heterogêneidade da aplicação dos nós;
* (3) Dificuldade de avaliar o desempenho da rede.

Objetivos
=========

A necessidade de um projeto com essas capacidades é alta. Devido a baixa
oferta de SunSPOTs, todas as análises de larga escala precisam de emulações. A
dificuldade de exercitar modelos de *RSSF* em larga escala de forma automática
atrasa o aprimoramento das soluções. Ao contrário, a simplicidade e agilidade
experimentação, encurta o ciclo de desenvolvimento e a consequente solidez
estatística dos resultados.  

**Falar Bem do *Solarium*.**  

<Claudio>
Nao precisa falar bem, fale a verdade. Diga que prototipar o sun spot eh rapido e possui apoio da oracle,
mas que o solarium eh instavel e por isso o projeto final
</Claudio>

Quando analisamos o emulador fornecido pela *Oracle* para a plataforma SunSPOT,
o *Solarium*, descobre-se que ele ainda é uma ferramenta carente de funcionalidades.
Os casos de uso para os quais o *Solarium* foi construido, não preveem muita variação
nos tipos de nós. Para cada variação de spot em uma emulação, é necessário criar um
novo diretório, com código e configuração específicos, além de incluir seu path na
configuração da respectiva emulação.
O *Solarium* também é um programa com interface gráfica. Ele toma a frente das outras
janelas frequentemente impedindo que seu usuário faça outras atividades durante as
longas rodadas de emulação.
Cada construção de nó é demorada e repetitiva. O usuário deve observar atentamente
ao processo para identificar possíveis erros de configuração, compilação ou execução.
A sincronização entre nós também não é perfeita. Na troca de mensagens de um nó para
outro não é garantido que o momento de escrita de um seja imediatamente seguida pela
leitura do outro. É comum observar *starvation*, gerando inconsistência no comportamento
esperado.
Para analisar o comportamento dos nós, é necessário fazer a leitura dos logs de todos
os nós que são expostos na saída padrão do emulador.  

Dadas essas circunstâncias, em um ambiente com (1, 2, 3), um emulador baseado no *Solarium*
deve cumprir os seguintes requisitos:

* Configuração automática de um ambiente heterogênio com a escala desejada;
* Execução de rodadas de emulação por linha de comando;
* Notificação e tratamento imediato de erros, com possível reinício da rodada;
* Dificultar o *starvation*;
* Persistir os dados expostos por cada um dos nós para posterior avaliação;
* Facilitar a identificação de inconsistências na execução da rodada.

Funcionamento
=============

<Claudio>

Aqui cabe vc descrever um pouco a arquitetura da sua solucao. Descrever quais os 
procedimentos realizados e como foi implementado de forma que alguem que leia o seu projeto final possa
reproduzir o que vc fez. Esse eh sempre o objetivo final da modelagem.

</Claudio>

Para cumprir estes objetivos, *Gneiss* instrumenta o emulador *Solarium* construindo os
ambientes de emulação a partir de uma api em python. Esta api está dividida em três partes:
Modelo, Emulação e Resultados.

Modelo
------

O Modelo é responsável por descrever as aplicações utilizadas nas rodadas de emulação.
É através dele que são identificados o path para o código fonte, a classe que será utilizada
como ponto de partida do nó e mais alguns metadados. Estes metadados se referem ao modo como
as informações vão ser coletadas.

**Exemplo de código:**

Emulação
--------

A Emulação é onde se define os parâmetros das rodadas, como por exemplo o tipo e o número de
cada aplicação na emulação, a área onde os nós serão espalhados, a frequência com que os nós
se comunicam. Uma instância de Emulation é que pode ser executada, iniciando rodadas, fazendo
análises preliminares, tais quais critério de parada, critério para erro ou inconsistências.

**Exemplo de código:**

Análise
-------

A análise é a etapa posterior a finalização das rodadas de uma emulação. É nela que os dados
serão consultados para esclarecer hipoteses imaginadas no início do processo.

**Exemplo de código:**


<Claudio>

Vamos precisar de uma forma de testar o seu projeto final. Isso vai ser importante pois 
vai permitir que verifiquemos o quao bom eh o Gneiss. O ideal seria vc usar aquele algoritmo de roteamento
que vc implementou com diferentes numeros de nodes e vamos verificar quantas vezes conseguimos realizar a simulacao de forma bem sucedida.

</Claudio>
