<!-- antes de enviar a versão final, solicitamos que todos os comentários, colocados para orientação ao aluno, sejam removidos do arquivo -->
# Estimativa de geração de energia fotovoltaica a partir da classificação de imagens celeste e Rede Neural Convolucional

#### Aluno: Leonardo Sondermann Christianes(https://github.com/link_do_github)
#### Orientadora: Evelyn Batista(https://github.com/link_do_github) 

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

<!-- para os links a seguir, caso os arquivos estejam no mesmo repositório que este README, não há necessidade de incluir o link completo: basta incluir o nome do arquivo, com extensão, que o GitHub completa o link corretamente -->
- [Link para o código](https://github.com/link_do_repositorio). <!-- caso não aplicável, remover esta linha -->

- [Link para a monografia](https://link_da_monografia.com). <!-- caso não aplicável, remover esta linha -->

- Trabalhos relacionados: <!-- caso não aplicável, remover estas linhas -->
    - [Nome do Trabalho 1](https://link_do_trabalho.com).
    - [Nome do Trabalho 2](https://link_do_trabalho.com).

---

### Resumo

A integra ̧c ̃ao da energia solar na rede el ́etrica est ́a se tornando cada vez mais comum
devido seu crescimento cont ́ınuo. O surgimento de usinas solares, que por usa vez, injetam uma
energia significativa no sistema el ́etrico, vem impulsionando cada vez mais os estudos para
modelos de previs ̃ao de curto prazo. Este trabalho consiste em realizar uma classifica ̧c ̃ao de
imagens do c ́eu em 3 grupos, c ́e limpo, nublado e parcialmente nublado, que foram obtidas
a partir de uma cˆamera na superf ́ıcie terrestre, utilizando uma Redes Neurais Convolucionais
(CNN), que apresentou um  ́otimo resultado, tendo uma precis ̃ao de 99,87% na sua classifica ̧c ̃ao.
Foi poss ́ıvel classificar novas imagens e realizar uma valida ̧c ̃ao e estimativa de potˆencia, atrav ́es
de uma estat ́ıstica da potˆencia gerada feita para cada classe representado pelo gr ́afico de boxplot.
Permitindo assim, para trabalhos futuros, o desenvolvimento de um modelo de estimativa de
gera ̧c ̃ao mais preciso e por fim realizar uma previs ̃ao da cobertura de nuvens sobre uma usina
solar e estimar o tempo em que as nuvens v ̃ao se dissipar ou obscurecer o sol.

### Abstract <!-- Opcional! Caso não aplicável, remover esta seção -->

<!-- trocar o texto abaixo pelo resumo do trabalho, em inglês -->

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Proin pulvinar nisl vestibulum tortor fringilla, eget imperdiet neque condimentum. Proin vitae augue in nulla vehicula porttitor sit amet quis sapien. Nam rutrum mollis ligula, et semper justo maximus accumsan. Integer scelerisque egestas arcu, ac laoreet odio aliquet at. Sed sed bibendum dolor. Vestibulum commodo sodales erat, ut placerat nulla vulputate eu. In hac habitasse platea dictumst. Cras interdum bibendum sapien a vehicula.

Proin feugiat nulla sem. Phasellus consequat tellus a ex aliquet, quis convallis turpis blandit. Quisque auctor condimentum justo vitae pulvinar. Donec in dictum purus. Vivamus vitae aliquam ligula, at suscipit ipsum. Quisque in dolor auctor tortor facilisis maximus. Donec dapibus leo sed tincidunt aliquam.

Donec molestie, ante quis tempus consequat, mauris ante fringilla elit, euismod hendrerit leo erat et felis. Mauris faucibus odio est, non sagittis urna maximus ut. Suspendisse blandit ligula pellentesque tincidunt malesuada. Sed at ornare ligula, et aliquam dui. Cras a lectus id turpis accumsan pellentesque ut eget metus. Pellentesque rhoncus pellentesque est et viverra. Pellentesque non risus velit. Orci varius natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.

### 1. Introdução
A resolu ̧c ̃ao da quest ̃ao clim ́atica no mundo  ́e urgente. 97% dos cientistas especialistas no assunto
atribuem o aquecimento global `a a ̧c ̃ao humana, especialmente a partir da Revolu ̧c ̃ao Industrial.
Houve aumento de 0,9 graus Celsius na temperatura da superf ́ıcie terrestre desde o final do
s ́eculo XIX, bem como maior emiss ̃ao de gases de efeito estufa, especialmente de g ́as carbˆonico
(clique e confira o gr ́afico ao final da mat ́eria). A maior parte do aquecimento global ocorreu
nos  ́ultimos 35 anos e j ́a houve 5 recordes de “anos mais quentes” desde 2010.
Tendo em vista o alto crescimento da gera ̧c ̃ao solar no Brasil devido ao aumento da eficiˆencia
da tecnologia, incentivos e subs ́ıdios dados pelo governo federal,al ́em de um arcabou ̧co regulat ́orio
favor ́avel (Resolu ̧c ̃ao Normativa - REN 482/2012 de 2012 e sua atualiza ̧c ̃ao e REN 687/2015).
Al ́em disso, que o Brasil recebe uma insola ̧c ̃ao (n ́umero de horas de brilho do Sol) superior a
3000 horas por ano, sendo que na regi ̃ao Nordeste h ́a uma incidˆencia m ́edia di ́aria entre 4,5 a 6
kWh, tornando assim o pa ́ıs com a maior taxa de irradia ̧c ̃ao solar do mundo.[9].
O Brasil ter ́a um crescimento de ate 44% na capacidade de energia solar instalada, apenas
para este ano de 2019, isso pode levar o pa ́ıs a atingir a marca de 3,3 gigawatts (GW) da
fonte em opera ̧c ̃ao. Os projetos de gera ̧c ̃ao distribu ́ıda devem somar 628,5 megawatts (MW)
em capacidade solar ao Brasil, um salto de 125%. A Empresa de Pesquisa de Energia (EPE)
apresenta no plano decimal de expans ̃ao uma proje ̧c ̃ao que, em at ́e 2027, o Brasil ter ́a mais de
1 milh ̃ao de sistemas fotovoltaicos em opera ̧c ̃ao. No ano de 2030, a principal meta  ́e chegar aos
25 GW de capacidade instalada sendo a matriz energ ́etica com maior taxa de crescimento em
compara ̧c ̃ao com as demais fontes de gera ̧c ̃ao.
Devido a esse forte crescimento, a Cˆamara de Comercializa ̧c ̃ao de Energia El ́etrica (CCEE)
desenvolveu uma proposta inicial para comercializa ̧c ̃ao da energia excedente da micro e
minigera ̧c ̃ao no Ambiente de Contrata ̧c ̃ao Livre – ACL para estimula ̧c ̃ao do segmento. Registrou
um aumento da competitividade da fonte solar nos leil ̃oes fazendo que o pre ̧co do MWh da energia
fotovoltaica tenha uma des ́agio de 75,6% no leil ̃ao ocorrido em 28/06/2019 [2].
Com a aprova ̧c ̃ao de novos projetos de usinas solares, seja de pequeno porte como a
minigera ̧c ̃ao distribu ́ıda ou das de grande porte, como a Usina Solar Pirapora em Pirapora-
MG cuja potˆencia instalada de 321 Megawatts, sendo a maior usina solar da Am ́erica latina,
possuem uma gera ̧c ̃ao de energia significativa para o sistema el ́etrico. Um alta inser ̧c ̃ao dessa
gera ̧c ̃ao pode causar grades impactos no sistema, e por esta raz ̃ao, vem impulsionando cada vez
mais os estudos sobre aplica ̧c ̃oes de Inteligˆencia Artificial e modelos de previs ̃ao a curto prazo
na gera ̧c ̃ao fotovoltaica.
A chamada Inteligˆencia Artificial (IA) vem tomando espa ̧co no mercado mundial e com
resultados promissores. Reunindo um conjunto de ferramentas computacionais e matem ́aticas,
de forma que os modelos computacionais possam se ajustar aos dados, assim, os modelos possuem
a capacidade de aprender padr ̃oes (Ludermir, 2021). De acordo com o relat ́orio de tendˆencias
estrat ́egicas para 2021 da empresa de consultoria em tecnologia da informa ̧c ̃ao Gartner (Gartner,
2021), o conceito de “Hyperautoma ̧c ̃ao”  ́e indicado como uma tendˆencia e implica na ideia que
tudo que pode ser automatizado em uma organiza ̧c ̃ao deve ser automatizado. A IA pode ser
uma ferramenta fundamental neste processo, uma vez que sua capacidade de adaptar-se a novos
cen ́arios  ́e fundamental para mercados em constante evolu ̧c ̃ao, como  ́e o caso dos mercados de
energia (CCEE, 2022).
O uso de inteligˆencia artificial tem se difundido nas  ́ultimas duas d ́ecadas, e ainda h ́a muitos
campos onde ela pode ser melhor explorada, a previs ̃ao da energia gerada pelas usinas solares,  ́e
uma caracter ́ıstica fundamental para o funcionamento, equil ́ıbrio e qualidade da energia el ́etrica
no sistema, e principalmente, para a tomada de decis ̃ao operacionais que s ̃ao realizadas pelas
Operador Nacional do Sistema El ́etrico (ONS), que realiza agendamento de carga, despacho ou
corte de outras usinas como por exemplos as usinas t ́erminas, que por sua vez, pu ́ıssem uma
contante de inseria maior e precisam de mais tempo para entrar em opera ̧c ̃ao. Em resumo, para
reduzindo os impactos e as incertezas na tomada de decis ̃ao.
Para abordar esta quest ̃ao, duas categorias de m ́etodos de previs ̃ao de curto prazo tˆem
sido propostos na literatura: m ́etodos baseados em terra e m ́etodos baseados em sat ́elites
geoestacion ́arios. A previs ̃ao baseada em sat ́elite  ́e realizada principalmente usando previs ̃ao
num ́erica de tempo e monitoramento de nuvem por sat ́elite. No entanto, essa abordagem
fornece apenas estimativas aproximadas devido `as limita ̧c ̃oes de resolu ̧c ̃ao espacial e temporal
das imagens de sat ́elite [8]. M ́etodos baseados no solo, usando imagens do c ́eu coletadas por
uma cˆamera fotogr ́afica na superf ́ıcie terrestre, que tˆem o potencial de proporcionar um melhor
desempenho, particularmente para a predi ̧c ̃ao do movimentos das nuvens e variabilidade da
irradiˆancia [4]. Esta  ́e a abordagem adotada neste trabalho.

### 2. Objetivo
Este presente trabalho tem por objetivo realizar uma classifica ̧c ̃ao de imagens do c ́eu coletadas
por uma cˆamera fotogr ́afica. Foi utilizado Redes Neurais Convolucionais (CNN) para classificar
um conjunto de amostra de imagens do c ́eu com diferentes condi ̧c ̃oes clim ́aticas em 3 grupos:
nublado, parcialmente nublado e c ́eu limpo. Tendo o dado de potencia medido e registado
para cada imagem da amostra,  ́e poss ́ıvel realizar uma estat ́ıstica de potˆencia gerada de um
painel solar para cada grupo e, portanto, validar e estimar a energia gerada de acordo com a
classifica ̧c ̃ao da imagem feita pela CNN.

### 3. Redes Neurais Convolucionais

Do inglˆes Convolutional Neural Networks (CNNs), as CNNs s ̃ao um tipo espec ́ıfico de ANN,
proposta pelo pesquisador francˆes Yann LeCun (LECUN, et al., 1998). As CNNs se mostraram,
desde a sua cria ̧c ̃ao, serem muito eficazes para resolver problemas de classifica ̧c ̃ao, se mostrando
uma alternativa vi ́avel aos m ́etodos tradicionais para esse tipo de problema. Uma das
desvantagens das CNNs  ́e o fato de existir a necessidade de uma grande quantidade de dados
rotulados para a extra ̧c ̃ao dos padr ̃oes, ou features. Basicamente, para extra ̧c ̃ao dessas features,
podem existir trˆes componentes b ́asicos em uma CNN, camada de convolu ̧c ̃ao, pooling e rede
totalmente conectada. Qualquer arquitetura b ́asica  ́e composta por esses blocos.
3.1. Camadas convolucional
A camada convolucional em uma CNN  ́e respons ́avel por extrair as chamadas features da entrada.
Matematicamente, uma convolu ̧c ̃ao  ́e uma opera ̧c ̃ao linear que a partir de duas fun ̧c ̃oes, gera uma
terceira (normalmente chamada de feature map). No contexto de imagens, podemos entender
esse processo como um filtro/kernel que transforma uma imagem de entrada. Um kernel  ́e uma
matrix utilizada para uma opera ̧c ̃ao de multiplica ̧c ̃ao de matrizes. Esta opera ̧c ̃ao  ́e aplicada
diversas vezes em diferentes regi ̃oes da imagem. A cada aplica ̧c ̃ao, a regi ̃ao  ́e alterada por um
parˆametro conhecido como stride. Normalmente o stride possui o valor 1, o que significa que
a transforma ̧c ̃ao ser ́a aplicada em todos os pixels da imagem. O processo de extra ̧c ̃ao dessas
features se d ́a por meio de filtros convolucionais de tamanhos reduzidos, onde os filtros percorrem
os dados de entrada em largura, altura e profundidade (chamada de dimens ̃ao) realizando
a opera ̧c ̃ao de convolu ̧c ̃ao sobre os dados. A cada processamento de entrada no per ́ıodo de
treinamento da rede, os filtros v ̃ao sendo ajustados de tal modo a disparar quando a entrada
contiver uma determinada caracter ́ıstica comum aos lotes de entrada, como por exemplos,
arestas, cores, dentre outras caracter ́ısticas. Com o andar da entrada na rede, os filtros v ̃ao
aprendendo estruturas cada vez mais complexas, ou seja, quanto mais filtros convolucionais,
mais features extra ́ımos da entrada, por ́em isso tem um custo de mem ́oria e processamento, o
que precisa ser balanceado na hora de definir a arquitetura.
3.2. Camada de ativa ̧c ̃ao
Utiliza-se uma fun ̧c ̃ao de ativa ̧c ̃ao, ao final de uma camada Conv2D e da camada Dense. A
inspira ̧c ̃ao biol ́ogica  ́e que inicialmente acreditava-se que os neurˆonios s ́o conseguiam transmitir
uma informa ̧c ̃ao adiante pelo axˆonio ap ́os receberem um certo n ́ıvel de est ́ımulo (ou de
satura ̧c ̃ao), e nessa situa ̧c ̃ao estariam ativados. Esta fun ̧c ̃ao tentava representar esse cen ́ario.
Na pr ́atica, a fun ̧c ̃ao de ativa ̧c ̃ao insere um comportamento necess ́ario de n ̃ao-linearidade, ap ́os
a fun ̧c ̃ao linear dos pesos com as entradas, do corpo da c ́elula As principais fun ̧c ̃oes de ativa ̧c ̃ao
– Sigm ́oide: muito utilizada para aprendizado de fun ̧c ̃oes l ́ogicas, pois espreme os valores
entre 0 e 1. N ̃ao  ́e centrada em torno de zero, o uso de exponencial  ́e relativamente custoso, e
n ̃ao  ́e boa para reconhecimento de imagens;
– Tangente Hiperb ́olica: utilizada em redes LSTM (um tipo de rede neural recorrente), esta
fun ̧c ̃ao espreme os valores entre -1 e 1, mas n ̃ao  ́e boa para fun ̧c ̃oes bin ́arias (pelo intervalo
negativo);
– ReLU (Unidade Linear Retificada): muito utilizada para imagens, n ̃ao satura na regi ̃ao
positiva, converge bem mais r ́apido do que a sigm ́oide ou tangente hiperb ́olica sobre imagens,
n ̃ao  ́e centrada em zero, por ́em  ́e ruim para fun ̧c ̃oes l ́ogicas, e n ̃ao  ́e utilizada em redes recorrentes;
– Leaky ReLU: esta fun ̧c ̃ao nunca satura,  ́e semelhante a ReLU por ́em faz tratamento para
entradas negativas;
– ELU (Unidade Linear Exponencial): apresenta todos os benef ́ıcios da ReLU, produz sa ́ıdas
com m ́edias pr ́oximas de zero, por ́em necessita de exponencial para seu c ́alculo;
– Softmax: esta fun ̧c ̃ao produz uma distribui ̧c ̃ao das probabilidades para cada classe de
imagem durante uma classifica ̧c ̃ao, diferente da sigm ́oide capaz de lidar com apenas duas classes.
 ́E utilizada na camada de sa ́ıda da CNN.
3.3. A camada de pooling
A camada de pooling consiste basicamente em uma camada destinada a reduzir o tamanho
dos dados de entrada. Normalmente, ap ́os uma camada convoluconal utilizamos uma camada
de pooling, com isso as pr ́oximas camadas de convolu ̧c ̃ao receber ̃ao uma outra forma de
representa ̧c ̃ao dos dados, possibilitando a rede aprender diversas representa ̧c ̃oes dos dados,
evitando com isso o overfitting (KARPATHY).
Existem 3 opera ̧c ̃oes diferentes de Pooling (MaxPooling, SumPooling, AvaragePooling).
Todas elas seguem o mesmo princ ́ıpio e s ́o se diferem na forma como calculam o valor final.
A mais utilizada nos dias de hoje  ́e a MaxPooling.
A opera ̧c ̃ao de MaxPooling retira o maior elemento de determinada regi ̃ao da matrix
(considerando o tamanho do pool aplicado). Posteriormente,  ́e feito um deslizamento
considerando um parˆametro de stride (similar a a opera ̧c ̃ao de convolu ̧c ̃ao) para aplica ̧c ̃ao de
uma nova opera ̧c ̃ao
3.4. Na camada Dropout
Dropout n ̃ao  ́e uma especificidade de uma CNN, por ́em a utilizaremos em nossa implementa ̧c ̃ao
t ́ecnica, portanto abordaremos seu funcionamento.
Em resumo, a camada de Dropout  ́e utilizada para evitar que determinadas partes da
rede neural tenham muita responsabilidade e consequentemente, possam ficar muito sens ́ıveis a
pequenas altera ̧c ̃oes.
Essa camada recebe um hyper-parˆametro que define uma probabilidade de “desligar”
determinada  ́area da rede neural durante o processo de treinamento.
3.5. Na camada Flatten
A matriz resultante das camadas anteriores de convolu ̧c ̃oes e poolings  ́e redimensionada para
se tornar um array linear, de uma  ́unica dimens ̃ao, por exemplo, uma imagem em grayscale de
28x28 ser ́a transformada para um array de 784 posi ̧c ̃oes. Esta etapa  ́e um preparo para se entrar
na camada principal da rede neural totalmente conectada.
3.6. Na camada Dense
 ́E implementada a rede neural totalmente conectada, ou fully connected (conhecido pela sigla
FC em inglˆes), e deve-se informar a dimens ̃ao da sa ́ıda e a fun ̧c ̃ao de ativa ̧c ̃ao a ser utilizada. No
contexto de reconhecimento de imagens  ́e comum se projetar esta camada densa com a fun ̧c ̃ao
de ativa ̧c ̃ao ReLU e, por fim, outra camada densa com a dimens ̃ao igual a quantidade de classes
a serem classificadas com a fun ̧c ̃ao de ativa ̧c ̃ao softmax (para m ́ultiplas classes).

### 4. Modelagem

Redes neurais tˆem sido usadas para Classifica ̧c ̃ao h ́a mais de 20 anos, alcan ̧caram resultados
confi ́aveis com redes neurais perceptron multicamadas (MLP) e abordagens de aprendizagem
profunda de m ́aquina de vetores de suporte (SVM), superiores ao limiar para algumas situa ̧c ̃oes.
Muitos estudos na literatura utilizam redes neurais Auto-Regressiva Com Entradas Ex ́ogenas
(NARX) para classifica ̧c ̃ao de imagens e prever a energia gerada de uma placa fotovoltaica [5, 3].
Neste estudo ser ́a utilizado uma Redes Neurais Convolucionais (CNN) junto com a biblioteca
Keras e tensorflow em Python para torna bastante simples e pr ́atica a constru ̧c ̃ao de uma CNN.
A CNN  ́e instanciada pela classe Sequential (biblioteca Keras) que permite criar uma modelo
camadas por camadas. Basicamente, definimos a convolu ̧c ̃ao, ativa ̧c ̃ao, polling, Flatten, Dense e
Dropout. Na figura 2, mostra a estrutura simplificada das camadas utilizadas para o treinamento
da rede CNN



O fluxograma abaixo ilustra a arquitetura das camadas utilizadas no modelo.
2, mostra a estrutura simplificada das camadas utilizadas para o treinamento da rede CNN



As primeiras camadas s ̃ao chamadas Convolu ̧c ̃oes. Estas s ̃ao camadas de convolu ̧c ̃ao que
lidam com as imagens de entrada, que s ̃ao vistas como matrizes bidimensionais.
Foi utilizado 2 blocos da rede convolucional, onde s ̃ao definimos a convolu ̧c ̃ao, ativa ̧c ̃ao,
polling e o dropout. No primeiro bloco, temos uma camada convolucional de 32 n ́os, e no
segundo bloco uma convolu ̧c ̃ao com 64 n ́os, ambas com kernel de 3x3 seguidas de uma ativa ̧c ̃ao
RELU ou Ativa ̧c ̃ao Linear Retificada, esta fun ̧c ̃ao de ativa ̧c ̃ao provou funcionar bem em redes
neurais [1], e polling de tamanho 2x2 como descrito por [6], que tem como principal objetivo
diminuir a sensibilidade da rede com rela ̧c ̃ao a pequenas altera ̧c ̃oes na imagem. Ela consegue
esse feito combinando as diferentes caracter ́ısticas de uma regi ̃ao em uma  ́unica caracter ́ıstica
ou padr ̃ao. Diminuindo a redundˆancia da rede. Por fim, para fechar cada bloco, uma camada
dropout de 0.5, para desligar randomicamente neurˆonios para evitar overfitting.
Apos o ultimo bloco de conjunto de camadas, foi usado a camada Flatten, que serve como
uma conex ̃ao entre a convolu ̧c ̃ao e a camada Fully-Connected (FC) chamada dense, ou seja,
dense  ́e o tipo de camada utilizada para a sa ́ıda de tamanho 3, que  ́e exatamente o n ́umero de
classes do problema.
Por fim, temos a ativa ̧c ̃ao ’softmax’ que faz com que a sa ́ıda possa ser interpretada como
probabilidades. O modelo far ́a ent ̃ao sua previs ̃ao com base em qual op ̧c ̃ao tem a maior
probabilidade entres as classes. Tendo a estrutura de camadas criada,  ́e ent ̃ao instanciada a
m ́etodo fit() da biblioteca Keras e tensorflow, para realizar o treinamento da rede.

### 5. Criação do Dataset

Inicialmente foi criando um banco de dados de uma amostra de aproximadamente 3000 mil
imagens do c ́eu de tamanho 480x640 pixels e um campo de vis ̃ao de 180 para compor o Dataset.
A aquisi ̧c ̃ao de energia, o painel PV tinha um circuito conectado a dois pinos anal ́ogicos na placa
Arduino. Um pino mediria a voltagem de toda a carga e o outro, a voltagem em uma pequena
resistˆencia, inferindo ent ̃ao a corrente gerada.
O conjunto de dados foi gravada durante um per ́ıodo 12 dias corridos entre 11 h as 17 h,
medindo tens ̃ao,corrente e temperatura a cada 50 segundo para cada imagem desse per ́ıodo.
Mais detalhes sobre este conjunto de dados pode ser encontrado em [7]. Em seguida, foi feita
uma classifica ̧c ̃ao manual das imagem entre as 3 condi ̧c ̃oes clim ́aticas para treinamento da rede:
c ́eu nublado; c ́eu parcialmente nublado e c ́eu limpo. As figuras 3, 4, 5 mostram as amostra das
trˆes imagens do c ́eu que correspondem a diferentes condi ̧c ̃oes clim ́aticas.


Um conjunto de amostras de imagens usados pra treinamento e testes em uma rede neural
deve ser composto por grupo ou classes com um n ́umero consideravelmente grande para que a
rede neural seja capaz de aprender e, portanto, ter uma maior precis ̃ao de classificaçao.

### 6. Treinamento e resultados

O treinamento da rede foi realizado atrav ́es um IntelR CoreT m CPU i5 750 com tempo m ́edio
de 289 segundos por  ́epoca. Para o treinamento foi utilizado o dataset que possui um conjunto
de imagens separadas em 3 classes, a partir do qual 75% do total servem como um conjunto de
treino e as imagens do c ́eu restantes como um conjunto de testes, a sele ̧c ̃ao das imagens  ́e feita
de forma aleat ́oria. Em seguida, foi reformular a entradas de conjunto de dados em 2 vari ́aveis
X train e Y train para treinamento, X test e Y test para teste, para ser processado no conjunto
de camadas detalhado na se ̧c ̃ao anterior.
Na figura 6 mostra uma precis ̃ao de 99,87%, na valida ̧c ̃ao das imagem, j ́a na figura 6 pode
observar que apenas 6 imagens fora classificadas de forma incorreta pela rede. A tabela 1 mostras 
a precis ̃ao e o numero total de imagem por grupo, foi observado que a rede teve uma
maior dificuldade em classificar imagens de clima parcialmente nublado (Figura 4 ) que foram
classificadas como nubladas (Figura 5 ). Vale ressaltar que a precis ̃ao da classifica ̧c ̃ao pode ter
sido degrada por falha na constru ̧c ̃ao do dataset, j ́a que o mesmo foi feita de forma manual e
algumas imagens podem ter sido agrupada de forma equivocadas.

### 7. Resultados finais

Inicialmente foi feita uma estat ́ıstica obtendo media, mediana, valor superior, inferior e
Coeficiente de varia ̧c ̃ao da potencia gera ̧c ̃ao para cada grupo do dataset, como mostrado na tabela 2. Com os valos, foi constru ́ıdo uma gr ́afico boxplot para uma melhor visualiza ̧c ̃ao da
distribui ̧c ̃ao dos dados e seus valores discrepantes (outliers) da potˆencia medida em PU. Para
an ́alise estat ́ıstica, foram removidos dados faltantes e medi ̧c ̃oes inconsistentes como uma gera ̧c ̃ao
pr ́oxima de 0 em condi ̧c ̃oes de c ́eu limpo (figura 3), por exemplo.
Na sequˆencia, foram escolhidas 5 novas imagem aleat ́orias para validar a rede treinada e
comparar a medi ̧c ̃ao da potˆencia registrada da imagem com os valos presentes no gr ́afico Boxplot.
E poss ́ıvel observar na tabela 3 que as 5 amostras foram classificadas corretamente, apenas as
imagem de numero 1 e 2 ficaram com os valores de potencia fora da faixa de concentra ̧c ̃ao do
gr ́afico boxplot. Isso mostra que  ́e poss ́ıvel realizar um estimativa, mesmo que n ̃ao t ̃ao precisa,
da gera ̧c ̃ao a partir da classifica ̧c ̃ao da imagem feita pela rede.

### 8. Conclusões

Neste trabalho foi mostrado um algoritmo para classificar imagens do c ́eu em 3 condi ̧c ̃oes
clim ́aticas, com base na superf ́ıcie terrestre. Foi demonstrado que um classificador de rede
neural convolutiva (CNN) utilizando a biblioteca Keras e tensorflow, foi capaz de realizar a
classifica ̧c ̃ao com uma precis ̃ao de 99,87%, at ́e em condi ̧c ̃oes rotulados como dif ́ıcil onde existem
nuvens em torno do sol ou nuvens muito escuras, e em condi ̧c ̃oes totalmente nubladas e sem nuvens. Sendo assim, o algoritmo tem a capacidade de distinguir bem entres essas 3 diferentes
condi ̧c ̃oes de c ́eu.
Com esta rede treinada foi poss ́ıvel classificar novas imagens e realizar uma valida ̧c ̃ao e
estimativa de potˆencia, atrav ́es de uma estat ́ıstica da potˆencia gerada pelo gr ́afico de boxplot,
que contem as faixas de potencia para cada classe ou condi ̧c ̃ao clim ́atica.
Como trabalho futuro, e com os resultados obtidos neste estudo,  ́e poss ́ıvel atrelar a
classifica ̧c ̃ao da imagem com a estimativa da potˆencia gerada e assim desenvolver modelos de
estimativas mais precisas. Podemos por fim, realizar uma detec ̧c ̃ao de nuvens e rastrear seus
movimentos juntos com outros parˆametros, como vento, temperatura  ́Indice ultravioleta entre
outro, para garantir uma melhor previs ̃ao de cobertura de nuvens sobre uma usina solar e estimar
o tempo em que as nuvens v ̃ao se dissipar ou obscurecer o sol.

### BIBLIOGRAFIA:

[1] Aprendizagem profunda para compreens̃ao visual: uma revis̃ao. Neurocomputing 187 .
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

Matrícula: 123.456.789

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*
