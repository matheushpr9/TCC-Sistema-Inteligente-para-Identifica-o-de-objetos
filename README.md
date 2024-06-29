# Detecção de Objetos com YOLO, Darknet, OpenCV e Python

## Contextualização

- YOLO:
"Yo Only Look Once"
é uma arquitetura de rede neural, para detecção de objetos

- Darcknet:
Framework de deeplearning

- openCV:
biblioteca para trabalhar com visão computacional

**Tudo isso com Python**

## Detecção de objetos

Classificação de objetos:

> Nada mais é do que tentar prever qual objeto a imagem contém 

O ideal é treinar classificadores multi-classe, para identificar duas ou mais classes de objetos dentro de uma imagem.
Assim tambem trassando sua localização (caixa localizadora) - previsão e localização de uma classe

### Caixas limitadoras

Para descrever uma caixa delimitadora(bounding box),são necessárias 4 variáveis, ou 5 contando com o nome da classe:

- coodenada x de início(left x)
- coodenada y de início(topy)
- largura da caixa
- altura da caixa

## YOLO (You Only Look Once )

Tecnica para trabalhar com detecção de objetos de imagens e vídeos.

> Método de detecção de objetos de passada única (single pass) que utiliza uma rede convolucional (Deep learning) como extrator de características(features)

Diferente de outros algoritimos de detecção de objetos (como R-CNN ou Faster R-CNN), ele apenas precisa olhar pela imagem uma única vez para enviar para a rede neural.

Utiliza uma rede neural única usando as características da imagem inteira para detectar múltiplas caixas, cada uma contendo um objeto

As dimenções das caixas são pré-definidas (âncoras) a de objetos anotados no conjuto de treinamento

### YOLO e Darknet

O YOLO usa uma rede neural profunda (Deep learning), cuja arquitetura de rede neural chamada Darknet.

Utilizamos uma biblioteca de mesmo nome para implementar o YOLO, a qual é open source e escrita em C

Antes do YOLO, sistemas de detecção de objetos,como o Haar cascade, faziam a detecção por meio da divisão da imagem em várias partes e depois em cada pedaço executava um classificador para cada pedaço da imagem.

Sendo assim, é necessário executar o mesmo classificador dezenas ou milhares de vezes sobre a mesma imagem

Basicamente, temos alguns padrões pré-definidos que seriam testados a cada partição da imagem.

Portanto se a intenção é implementar essa técnica para ser usada em tempo real então necessitaria de um comutador muito potente para conseguir rodar

Já no cado do YOLO, é treinado uma única rede neural para fazer a detecção completa na imagem

Dessa forma, é capaz de produzir todas as bounding boxes (caixas delimitadoras ao redor do objeto) e todas as probabilidades dessas detecções de uma única vez(single pass)

### Outras Abordagens 

Outra alternativa seria utilizaru, classificador como VGGNET ou inception e transformá-lo em um detector de objetos se usarmos *sliding window*

Percorrendo a imagens milhares de vezes para tentar encontrar alguns dos paterns quadriculados na imagem analizada; Funciona, mas é extremamente lenta.

## YOLO - Funcionamento

O algoritmo divide a imagem em um grid de SxS células
