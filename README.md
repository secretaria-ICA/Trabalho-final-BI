<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Estimativa de geração de energia fotovoltaica a partir da classificação de imagens celeste e Rede Neural Convolucional

#### Aluno: Leonardo Sondermann Christianes
#### Orientadora: Evelyn Batista

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

- [Link para o código](https://github.com/leosonder/Trabalho-final-BI.git)
- [Link para o Dataset](https://drive.google.com/file/d/1WQV3dYmvrYD6fzExJvCjf1wenFJQ0KuY/view?usp=share_link)
---

### Resumo

A integração da energia solar na rede elétrica está se tornando cada vez mais comum devido seu crescimento contínuo. O surgimento de usinas solares, que por usa vez, injetam uma energia significativa no sistema elétrico, vem impulsionando cada vez mais os estudos para modelos de previsão de curto prazo. Este trabalho consiste em realizar uma classificação de imagens do céu em 3 grupos, cé limpo, nublado e parcialmente nublado, que foram obtidas a partir de uma câmera na superfície terrestre, utilizando uma Redes Neurais Convolucionais (CNN), que apresentou um ótimo resultado, tendo uma precisão de 99,87% na sua classificação. Foi possível classificar novas imagens e realizar uma validação e estimativa de potência, através de uma estatística da potência gerada feita para cada classe representado pelo gráfico de boxplot. Permitindo assim, para trabalhos futuros, o desenvolvimento de um modelo de estimativa de geração mais preciso e por fim realizar uma previsão da cobertura de nuvens sobre uma usina solar e estimar o tempo em que as nuvens vão se dissipar ou obscurecer o sol. 

### 1. Introdução
A resolução da questão climática no mundo é urgente. 97% dos cientistas especialistas no assunto atribuem o aquecimento global à ação humana, especialmente a partir da Revolução Industrial. Houve aumento de 0,9 graus Celsius na temperatura da superfície terrestre desde o final do século XIX, bem como maior emissão de gases de efeito estufa, especialmente de gás carbônico. A maior parte do aquecimento global ocorreu nos últimos 35 anos e já houve 5 recordes de “anos mais quentes” desde 2010.


Tendo em vista o alto crescimento da geração solar no Brasil devido ao aumento da eficiência da tecnologia, incentivos e subsídios dados pelo governo federal,além de um arcabouço regulatório favorável (Resolução  Normativa - REN 482/2012 de 2012 e sua atualização e REN 687/2015). Além disso, que o Brasil recebe uma insolação (número de horas de brilho do Sol) superior a 3000 horas por ano, sendo que na região Nordeste há uma incidência média diária entre 4,5 a 6 kWh, tornando assim o país com a maior taxa de irradiação solar do mundo.[9]. 
 
O Brasil terá um crescimento de ate 44% na capacidade de energia solar instalada, apenas para este ano de 2019, isso pode levar o país a atingir a marca de 3,3 gigawatts (GW) da fonte em operação. Os projetos de geração distribuída devem somar 628,5 megawatts (MW) em capacidade solar ao Brasil, um salto de 125%. A Empresa de Pesquisa de Energia (EPE) apresenta no plano decimal de expansão uma projeção que, em até 2027, o Brasil terá mais de 1 milhão de sistemas fotovoltaicos em operação. No ano de 2030, a principal meta é chegar aos 25 GW de capacidade instalada sendo a matriz energética com maior taxa de crescimento em comparação com as demais fontes de geração.
 
Devido a esse forte crescimento, a  Câmara de Comercialização de Energia Elétrica (CCEE) desenvolveu uma proposta inicial para comercialização da energia excedente da micro e minigeração no Ambiente de Contratação Livre – ACL para estimulação do segmento. Registrou um aumento da competitividade da fonte solar nos leilões fazendo que o preço do MWh da energia fotovoltaica tenha uma deságio de 75,6% no leilão ocorrido em 28/06/2019. [2].

Com a aprovação de novos projetos de usinas solares, seja de pequeno porte como a minigeração distribuída ou das de grande porte, como a Usina Solar Pirapora em Pirapora-MG cuja potência  instalada de 321 Megawatts, sendo a maior usina solar da América latina, possuem uma geração de energia significativa para o sistema elétrico. Um alta inserção dessa geração pode causar grades impactos no sistema, e por esta razão, vem impulsionando cada vez mais os estudos sobre aplicações de Inteligência Artificial e modelos de previsão a curto prazo na geração fotovoltaica.

A chamada Inteligência Artificial (IA) vem tomando espaço no mercado mundial e com resultados promissores. Reunindo um conjunto de ferramentas computacionais e matemáticas, de forma que os modelos computacionais possam se ajustar aos dados, assim, os modelos possuem a capacidade de aprender padrões (Ludermir, 2021). De acordo com o relatório de tendências estratégicas para 2021 da empresa de consultoria em tecnologia da informação Gartner (Gartner, 2021), o conceito de “Hyperautomação” é indicado como uma tendência e implica na ideia que tudo que pode ser automatizado em uma organização deve ser automatizado. A IA pode ser uma ferramenta fundamental neste processo, uma vez que sua capacidade de adaptar-se a novos cenários é fundamental para mercados em constante evolução, como é o caso dos mercados de energia (CCEE, 2022).


O uso de inteligência artificial tem se difundido nas últimas duas décadas, e ainda há muitos campos onde ela pode ser melhor explorada, a previsão da energia gerada pelas usinas solares, é uma característica fundamental para o funcionamento, equilíbrio e qualidade da energia elétrica no sistema,  e principalmente, para a tomada de decisão operacionais que são realizadas pelas Operador Nacional do Sistema Elétrico (ONS), que realiza agendamento de carga, despacho ou corte de outras usinas como por exemplos as usinas términas, que por sua vez, puíssem uma contante de inseria maior e precisam de mais tempo para entrar em operação. Em resumo, para reduzindo os impactos e as incertezas na tomada de decisão.

 Para abordar esta questão, duas categorias de métodos de previsão de curto prazo têm sido propostos na literatura: métodos baseados em terra e métodos baseados em satélites geoestacionários. A previsão baseada em satélite é realizada principalmente usando previsão numérica de tempo e monitoramento de nuvem por satélite. No entanto, essa abordagem fornece apenas estimativas aproximadas devido às limitações de resolução espacial e temporal das imagens de satélite [8]. Métodos baseados no solo, usando imagens do céu coletadas por uma câmera fotográfica na superfície terrestre, que têm o potencial de proporcionar um melhor desempenho, particularmente para a predição do movimentos das nuvens e variabilidade da irradiância [4]. Esta é a abordagem adotada neste trabalho. 

### 2. Objetivo
Este presente trabalho tem por objetivo realizar uma classificação de imagens do céu coletadas por uma câmera fotográfica. Foi utilizado Redes Neurais Convolucionais (CNN) para classificar um conjunto de amostra de imagens do céu com diferentes condições climáticas em 3 grupos: nublado, parcialmente nublado e céu limpo. Tendo o dado de potencia medido e registado para cada imagem da amostra, é possível realizar uma estatística de potência gerada de um painel solar para cada grupo e, portanto, validar e estimar a energia gerada de acordo com a classificação da imagem feita pela CNN.
 

### 3. Redes Neurais Convolucionais

Do inglês Convolutional Neural Networks (CNNs), as CNNs são um tipo
específico de ANN, proposta pelo pesquisador francês Yann LeCun (LECUN, et al.,
1998). As CNNs se mostraram, desde a sua criação, serem muito eficazes para resolver
problemas de classificação, se mostrando uma alternativa viável aos métodos
tradicionais para esse tipo de problema.
Uma das desvantagens das CNNs é o fato de existir a necessidade de uma grande
quantidade de dados rotulados para a extração dos padrões, ou features. Basicamente,
para extração dessas features, podem existir três componentes básicos em uma CNN,
camada de convolução, pooling e rede totalmente conectada. Qualquer arquitetura
básica é composta por esses blocos.

### 3.2. Camada de ativação
Utiliza-se uma função de ativação, ao final de uma camada Conv2D e da camada Dense. A inspiração biológica é que inicialmente acreditava-se que os neurônios só conseguiam transmitir uma informação adiante pelo axônio após receberem um certo nível de estímulo (ou de saturação), e nessa situação estariam ativados. Esta função tentava representar esse cenário. Na prática, a função de ativação insere um comportamento necessário de não-linearidade, após a função linear dos pesos com as entradas, do corpo da célula
As principais funções de ativação 

‒ Sigmóide: muito utilizada para aprendizado de funções lógicas, pois espreme os valores entre 0 e 1. Não é centrada em torno de zero, o uso de exponencial é relativamente custoso, e não é boa para reconhecimento de imagens;

‒ Tangente Hiperbólica: utilizada em redes LSTM (um tipo de rede neural recorrente), esta função espreme os valores entre -1 e 1, mas não é boa para funções binárias (pelo intervalo negativo);

‒  ReLU (Unidade Linear Retificada): muito utilizada para imagens, não satura na região positiva, converge bem mais rápido do que a sigmóide ou tangente hiperbólica sobre imagens, não é centrada em zero, porém é ruim para funções lógicas, e não é utilizada em redes recorrentes;

‒  Leaky ReLU: esta função nunca satura, é semelhante a ReLU porém faz tratamento para entradas negativas;

‒  ELU (Unidade Linear Exponencial): apresenta todos os benefícios da ReLU, produz saídas com médias próximas de zero, porém necessita de exponencial para seu cálculo;

‒ Softmax: esta função produz uma distribuição das probabilidades para cada classe de imagem durante uma classificação, diferente da sigmóide capaz de lidar com apenas duas classes. É utilizada na camada de saída da CNN.
### 3.3. A camada de pooling
A camada de pooling consiste basicamente em uma camada destinada a reduzir
o tamanho dos dados de entrada. Normalmente, após uma camada convoluconal
utilizamos uma camada de pooling, com isso as próximas camadas de convolução
receberão uma outra forma de representação dos dados, possibilitando a rede aprender
diversas representações dos dados, evitando com isso o overfitting (KARPATHY).

Existem 3 operações diferentes de Pooling (MaxPooling, SumPooling, AvaragePooling). Todas elas seguem o mesmo princípio e só se diferem na forma como calculam o valor final. A mais utilizada nos dias de hoje é a MaxPooling.

A operação de MaxPooling retira o maior elemento de determinada região da matrix (considerando o tamanho do pool aplicado). Posteriormente, é feito um deslizamento considerando um parâmetro de stride (similar a a operação de convolução) para aplicação de uma nova operação

### 3.4. Na camada Dropout
DDropout não é uma especificidade de uma CNN, porém a utilizaremos em nossa implementação técnica, portanto abordaremos seu funcionamento.

Em resumo, a camada de Dropout é utilizada para evitar que determinadas partes da rede neural tenham muita responsabilidade e consequentemente, possam ficar muito sensíveis a pequenas alterações.

Essa camada recebe um hyper-parâmetro que define uma probabilidade de “desligar” determinada área da rede neural durante o processo de treinamento.

### 3.5. Na camada Flatten

A matriz resultante das camadas anteriores de convoluções e poolings é redimensionada para se tornar um array linear, de uma única dimensão, por exemplo, uma imagem em grayscale de 28x28 será transformada para um array de 784 posições. Esta etapa é um preparo para se entrar na camada principal da rede neural totalmente conectada.

### 3.6. Na camada Dense

É implementada a rede neural totalmente conectada, ou fully connected (conhecido pela sigla FC em inglês), e deve-se informar a dimensão da saída e a função de ativação a ser utilizada. No contexto de reconhecimento de imagens é comum se projetar esta camada densa com a função de ativação ReLU e, por fim, outra camada densa com a dimensão igual a quantidade de classes a serem classificadas com a função de ativação softmax (para múltiplas classes).

### 4. Modelagem

Redes neurais têm sido usadas para Classificação há mais de 20 anos, alcançaram resultados confiáveis com redes neurais perceptron multicamadas (MLP) e abordagens de aprendizagem profunda de máquina de vetores de suporte (SVM), superiores ao limiar para algumas situações. Muitos estudos na literatura utilizam redes neurais Auto-Regressiva Com Entradas Exógenas (NARX) para classificação de imagens e prever a energia gerada de uma placa fotovoltaica [5, 3].

 Neste estudo será utilizado uma Redes Neurais Convolucionais (CNN) junto com a biblioteca Keras e tensorflow em Python para torna bastante simples e prática a construção de uma CNN.

A CNN é instanciada pela classe Sequential (biblioteca Keras) que permite criar uma modelo camadas por camadas. Basicamente, definimos a convolução, ativação, polling, Flatten, Dense e Dropout. Na figura 1, mostra a estrutura simplificada das camadas utilizadas para o treinamento da rede CNN 

![struct](https://user-images.githubusercontent.com/60608757/212551537-66eda89e-7bbb-413f-a95a-1b02c53d31e6.png)

O fluxograma abaixo ilustra a arquitetura das camadas utilizadas no modelo.

![DiagramaCNN](https://user-images.githubusercontent.com/60608757/212551524-d26c08c2-4085-48c7-a453-437792769c42.png)

As primeiras camadas são chamadas Convoluções. Estas são camadas de convolução que lidam com as imagens de entrada, que são vistas como matrizes bidimensionais.

Foi utilizado 2 blocos da rede convolucional, onde são definimos a convolução, ativação, polling e o dropout. No primeiro bloco, temos uma camada convolucional de 32 nós, e no segundo bloco uma convolução com 64 nós, ambas com kernel de 3x3 seguidas de uma ativação RELU ou Ativação Linear Retificada, esta função de ativação provou funcionar bem em redes neurais  [1], e polling de tamanho 2x2 como descrito por [6], que tem como principal objetivo diminuir a sensibilidade da rede com relação a pequenas alterações na imagem. Ela consegue esse feito combinando as diferentes características de uma região em uma única característica ou padrão. Diminuindo a redundância da rede. Por fim, para fechar cada bloco, uma camada dropout de 0.5, para desligar randomicamente neurônios para evitar overfitting.

Apos o ultimo bloco de conjunto de camadas, foi usado a camada Flatten, que serve como uma conexão entre a convolução e a camada Fully-Connected (FC) chamada dense, ou seja, dense é o tipo de camada utilizada para a saída de tamanho 3, que é exatamente o número de classes do problema.

Por fim, temos a ativação 'softmax' que faz com que a saída possa ser interpretada como probabilidades. O modelo fará então sua previsão com base em qual opção tem a maior probabilidade entres as classes.
Tendo a estrutura de camadas criada, é então instanciada a método fit() da biblioteca Keras e tensorflow, para realizar o treinamento da rede.

### 5. Criação do Dataset

Inicialmente foi criando um banco de dados de uma amostra de aproximadamente 3000 mil imagens do céu de tamanho 480x640 pixels e um campo de visão de 180° para compor o Dataset.
 A aquisição de energia, o painel PV tinha um circuito conectado a dois pinos analógicos na placa Arduino. Um pino mediria a voltagem de toda a carga e o outro, a voltagem em uma pequena resistência, inferindo então a corrente gerada.
 
 O conjunto de dados foi gravada durante um período 12 dias corridos entre 11 h as 17 h, medindo tensão,corrente e temperatura a cada 50 segundo para cada imagem desse período. Mais detalhes sobre este conjunto de dados pode ser encontrado em [7]. Em seguida, foi feita uma classificação manual das imagem entre as 3 condições climáticas para treinamento da rede: céu nublado; céu parcialmente  nublado e  céu  limpo.  As figuras 3,4,5 mostram as
amostra das três imagens do céu que correspondem a diferentes condições climáticas.
O Dataset usando poder ser baixo pelo link (https://drive.google.com/file/d/1WQV3dYmvrYD6fzExJvCjf1wenFJQ0KuY/view?usp=share_link)

![limpo](https://user-images.githubusercontent.com/60608757/212551529-1b49ab93-0659-4daa-aa23-898117f1218e.jpg) ![parcial](https://user-images.githubusercontent.com/60608757/212551535-993f9e0a-6087-4874-a3ac-cdbbc9494056.jpg) ![nublado](https://user-images.githubusercontent.com/60608757/212551534-e16ca17f-c856-4d28-9103-89db8249080d.jpg)


Um conjunto de amostras de imagens usados pra treinamento e testes em uma rede neural deve ser composto por grupo ou classes com um número consideravelmente  grande  para  que  a  rede neural seja capaz de aprender e, portanto, ter uma maior precisão de classificação.

### 6. Treinamento e resultados

O treinamento da rede foi realizado através um IntelR CoreT m CPU i5 750 com tempo  médio de 289 segundos por época.
Para o treinamento foi utilizado o dataset que possui um conjunto de imagens separadas em 3 classes, a partir do qual 75% do total servem como um conjunto de treino e as imagens do céu restantes como um conjunto de testes, a seleção das imagens é feita de forma aleatória.
Em seguida, foi reformular a  entradas de conjunto de dados em 2 variáveis  
X\_train e Y\_train para treinamento, X\_test e Y\_test para teste, para ser processado no conjunto de camadas detalhado na seção anterior.

Na figura 6 mostra uma precisão de 99,87%, na validação das imagem, já na figura 7 pode observar que apenas 6 imagens fora classificadas de forma incorreta pela rede. A tabela \ref{tab:table} mostras a precisão e o numero total de imagem por grupo, foi observado que a rede teve uma maior dificuldade em classificar imagens de clima parcialmente nublado (Figura 4  que foram classificadas como nubladas (Figura 5). Vale ressaltar que a precisão da classificação pode ter sido degrada por falha na construção do dataset, já que o mesmo foi feita de forma manual e algumas imagens podem ter sido agrupada de forma equivocadas.

![matrix](https://user-images.githubusercontent.com/60608757/212551533-165561ce-dff4-4a0f-ba06-e6d48c401dda.png)

![Tabala1](https://user-images.githubusercontent.com/60608757/212551539-640e2adb-2d7d-49fc-8f95-1d3e58fa9aec.PNG)

### 7. Resultados finais

Inicialmente foi feita uma estatística obtendo media, mediana, valor superior, inferior e Coeficiente de variação  da potencia geração para cada grupo do dataset, como mostrado na tabela 1. Com os valos, foi construído uma gráfico boxplot para uma melhor visualização da distribuição dos dados e seus valores discrepantes (outliers)  da potência medida em PU. Para análise estatística, foram removidos dados faltantes e medições inconsistentes como uma geração próxima de 0 em condições de céu limpo (figura 3), por exemplo.


![Tabela2](https://user-images.githubusercontent.com/60608757/212551540-f4079984-d0da-48a9-8604-a7b438740c7c.PNG)

![boxplot](https://user-images.githubusercontent.com/60608757/212551520-36ab279d-6ca5-4339-badc-0ed0cbb69d89.jpg)

Na sequência, foram escolhidas 5 novas imagem aleatórias para validar a rede treinada e comparar a medição da potência registrada da imagem com os valos presentes no gráfico Boxplot. E possível observar na tabela 2 que as 5 amostras foram classificadas corretamente, apenas as imagem de numero 1 e 2 ficaram com os valores de potencia fora da faixa de concentração do gráfico boxplot. Isso mostra que é possível realizar um estimativa, mesmo que não tão precisa, da geração a partir da classificação da imagem feita pela rede. 

![Tabela3](https://user-images.githubusercontent.com/60608757/212551542-d95e3130-aa6e-4e37-894d-bcf621406cf6.PNG)

### 8. Conclusões

Neste trabalho foi mostrado um algoritmo para classificar imagens do céu em 3 condições climáticas, com base na superfície terrestre.
Foi demonstrado que um classificador de rede neural convolutiva (CNN) utilizando a biblioteca Keras e tensorflow, foi capaz de realizar a classificação com uma  precisão de 99,87%, até em condições rotulados como difícil onde existem nuvens em torno do sol ou nuvens muito escuras, e em condições totalmente nubladas e sem nuvens. Sendo assim, o algoritmo tem a capacidade de distinguir bem entres essas 3 diferentes condições de céu.

Com esta rede treinada foi possível classificar novas imagens e realizar uma validação e estimativa de potência, através de uma estatística da potência gerada pelo gráfico de boxplot, que contem as faixas de potencia para cada classe ou condição climática.

Como trabalho futuro, e com os resultados obtidos neste estudo, é possível atrelar a classificação da imagem com a estimativa da potência gerada e assim desenvolver modelos de estimativas mais precisas. Podemos por fim, realizar uma detecção de nuvens e rastrear seus movimentos juntos com outros parâmetros, como vento, temperatura Índice ultravioleta entre outro, para garantir uma melhor previsão de cobertura de nuvens sobre uma usina solar e estimar o tempo em que as nuvens vão se dissipar ou obscurecer o sol.

### BIBLIOGRAFIA:

[1] Aprendizagem profunda para compreens̃ao visual: uma revis̃ao. Neurocomputing 187.

[2] CCEE. Leil̃ao de energia renov́avel tem deságio de 45% e gera investimentos de r$ 1,9 bi, 2019.

[3] Cococcioni, M., D’Andrea, E., and Lazzerini, B. 24-hour-ahead forecasting of energy production in
solar pv systems. In 2011 11th International Conference on Intelligent Systems Design and Applications
(2011), IEEE, pp. 1276–1281.

[4] Diagne, M., David, M., Lauret, P., Boland, J., and Schmutz, N. Review of solar irradiance forecasting
methods and a proposition for small-scale insular grids. Renewable and Sustainable Energy Reviews 27
(2013), 65–76.

[5] El Hendouzi, A., and Bourouhou, A. Forecasting of pv power application to pv power penetration in a
microgrid. In 2016 International Conference on Electrical and Information Technologies (ICEIT) (2016),
IEEE, pp. 468–473.

[6] Fukushima, K. Neocognitron: A self-organizing neural network model for a mechanism of pattern recognition
unaffected by shift in position. Biological cybernetics 36, 4 (1980), 193–202.

[7] Guilherme Bassous, Carlos Hall, M. V. R. C. Cloud detection and photovoltaic power estimation by
using neural networks and sky images.

[8] Lee, J., Weger, R. C., Sengupta, S. K., and Welch, R. M. A neural network approach to cloud
classification. IEEE Transactions on Geoscience and Remote Sensing 28, 5 (1990), 846–855.

[9] Martins, F. R., Pereira, E. B., De Abreu, S. L., and Colle, S. Brazilian atlas for solar energy resource:
Swera results. In Proceedings of ISES World Congress 2007 (Vol. I–Vol. V) (2008), Springer, pp. 2651–2655.

---

Matrícula: 211.100.153 

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
