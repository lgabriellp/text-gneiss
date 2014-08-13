Introdução
==========

<Claudio>
Aqui vc deve falar 1 paragrafo ou dois sobre cada:
1) Sobre redes de sensores sem fio
2) Como eh ainda eh caro adquirir motes e isso eh o problema
3) Existem ambientes de simulacao
4) Destacar a plataforma sun spot e o solarium
5) falar que ele eh instavel 
6) gancho pra o gneiss (de onde saiu esse nome)


</claudio>

*Gneiss* é um gerenciador de emulações de *Redes de Sensores Sem Fio (RSSF)*
que utiliza a plataforma SunSPOT de dispositivos da Oracle. Ele foi criado
com o objetivo de facilitar a emulação de ambientes de *RSSF* com as
seguintes características:

* (1) Grande número de nós na rede;
* (2) Grande heterogêneidade da aplicação dos nós;
* (3) Dificuldade de avaliar o desempenho da rede.

Objetivos
=========

A necessidade de um projeto com essas capacidades é gigantesca.

<Claudio>
Nunca use adjetivos como gigantesco e afins, nao fica bom em trabalhos cientificos
</Claudio>
 Devido a baixa
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