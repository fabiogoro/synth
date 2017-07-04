# synth
Pure Data Synthesizer

Este é um sintetizador em pure data. A ideia é produzir sons a partir de uma interface com usuário.
O usuário deve ter liberdade para criar seus próprios *pipelines* de processamentos, visando seu interesse particular.
Para isso ele pode combinar entradas de 4 categorias de módulos:

## controle

Esta categoria será responsável pela entrada de notas ou eventos que serão convertidos em som. 
Os módulos definidos nessa categoria são:

### leitor midi

Este é um leitor simples de arquivos midi.
Como usar:
Um botão de leitura permite a escolha de arquivos no computador.
O arquivo escolhido começará a ser executado automáticamente, podendo ser cancelada a execução a qualquer momento através do botão parar.

### sequenciador

Este é um sequenciador de 8 estados. Estados serão tocados em *loop* definido por parâmetros:
* velocidade: define o tempo entre inícios de notas. Em milissegundos.
* duração: define o intervalo entre um início de nota e o final daquela nota. Em milissegundos.
* frequencias: define a frequência que a nota em um exato estado irá ter. Em hertz.
* intensidade: define a intensidade de uma nota em um exato estado irá ter.
Botão on/off permitirá desligar a execução do sequênciador.

## síntese

Esta categoria será responsável por definir sinais a partir de descrições.
Os módulos definidos nessa categoria são:

### oscilador

Este é um oscilador que repetirá um padrão definido por um *radio button*. Os padrões definidos são:
* seno: onda senoidal simples.
* triangular: soma de senoides que tentam aproximar um triangulo.
* quadrado: onda que tenta simular o comportamento de um sinal que vale ou 0 ou 1, utiliza um grande número de harmônicos.
* dente-de-serra: onda que possui comportamento de *phaser*. Também possui uma quantidade alta de harmônicos.
Para utilizá-lo é necessário ativar o on/off.

### aditiva

Este é um oscilador que utilizará um padrão de espectro baseado em um desenho produzido pelo usuário em uma tabela para gerar um sinal.
Uma tabela mostra o sinal resultante. Para utilizá-lo é necessário ativar o on/off.

### formantes

Esté é um oscilador que possui *presets* de filtragens para sinais harmônicos que ressaltam frequências que remetem fonemas.
É possível alternar automaticamente entre fonemas, de forma sequencial ou aletória. Para utilizá-lo é necessário ativar o on/off.

### ruído subtraído

Esté gerador filtrará ruído utilizando como frequência central a nota recebe como *inlet*. O parâmetro Q irá alterar a intensidade de decaimento de intensidade das frequências ao redor do ponto de corte. 

## envelope

Esta categoria será responsável por definir comportamentos de início e final de sinais, evitando (ou gerando) cliques.
Os módulos definidos nessa categoria são:

### adsr

* attack: tempo para sinal partir do 0 para seu pico máximo em milissegundos.
* decay: tempo para sinal partir do pico máximo para pico de sustento em milissegundos.
* release: tempo para sinal partir do sustento para 0 em milissegundos.

### percursivo

Este envelope terá um ataque curto com decaimento exponencial baseado no parâmetro R.

## efeito

Este categoria será responsável por criar comportamentos mais complexos para os sinais modulados e envelopados.
Os módulos definidos nessa categoria são:

### fir

Permite escolha do filtro, realiza a filtragem baseada na resposta em frequência.

### reverberação

Simulação de reverberação.

### wahwah

Rápida alternância da frequência central de um filtro em um sinal, com um padrão senoidal.


