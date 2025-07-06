# Projeto Final - AED II (Parte 1)

## Apresentação
[Link para a apresentação](LINK_PARA_A_SUA_APRESENTACAO_AQUI)

## Integrantes do Grupo
- Gustavo Pereira de Carvalho
- André Luiz Lima Souza
- Celine Helena Abrantes de Andrade

## Contextualização
Este projeto tem como objetivo principal aplicar conceitos de Grafos e Análise de Redes para explorar e visualizar as propriedades estruturais de uma rede complexa. Através da implementação e análise de diferentes métricas de centralidade e outras técnicas de avaliação de grafos, buscamos identificar nós cruciais e padrões de conexão que revelam a dinâmica e a organização interna da rede em estudo. O trabalho abrange desde a preparação dos dados até a visualização interativa dos resultados.

## Requisitos

### Requisito #01: Análise de Centralidades

No primeiro requisito, foram gerados quatro grafos diferentes expondo diferentes tipos de centralidade: a centralidade de grau (Degree Centrality), centralidade de proximidade (Closeness Centrality), centralidade de intermediação (Betweenness Centrality) e centralidade de autovetor (Eigenvector Centrality).

A centralidade de grau representa o número de conexões que um vértice possui. Um nó com alto grau é diretamente conectado a muitos outros, sugerindo uma alta influência e visibilidade.

A centralidade de intermediação representa o quanto um nó está no caminho mais curto até outros pares de nós. Um nó com betweenness alto atua como ponte ou nó intermediário entre outros nós, podendo controlar o fluxo na rede, sendo importante para ligar comunidades ou regiões separadas do grafo.

A centralidade de proximidade mede o quão próximo um nó está de todos os outros na rede, baseado no menor caminho. Um nó com closeness alto pode alcançar outros nós rapidamente, indicando sua importância para difundir informação pela rede.

Por fim, a centralidade de autovetor considera, além do número de conexões, a importância dos vizinhos de um nó. Por exemplo, um nó com alta centralidade está ligado a outros com alta importância, representando sua importância estrutural, como uma celebridade que se conecta a outras pessoas igualmente famosas, mas é seguida por milhares de pessoas comuns.

### Requisito #02
O segundo requisito tem o objetivo de destacar o k-core e k-shell da rede, uma métrica importante para determinar o “núcleo” mais importante, conectado e influente, saber quais elementos são mais resilientes a falhas ou entender os superespalhadores em uma rede de contatos, em diferentes aplicações.

O k-shell representa o conjunto de nós que pertencem ao k-core, mas não ao k+1-core, como uma “casca” que envolve o núcleo mais conectado. Dessa forma, cada camada removida com número de nós menor que k é o k-shell daquela etapa k.

O k-core de um grafo é o subgrafo máximo no qual todos os nós têm grau maior ou igual a k. Isso significa que você inclui o maior conjunto possível de nós que satisfaça a condição. Essa operação é chamada de decomposição e começa com a remoção de todos os nós com grau menor que k, atualizando os graus restantes até que só restem apenas nós com grau maior ou igual a k no subgrafo.

### Requisito #03
O terceiro requisito consiste em gerar uma rede exportada no formato HTML através de um plugin disponível no próprio Gephi, organizada com cores diferentes relacionadas ao critério de comunidade. Para isso, a métrica de modularidade foi usada para separar os nós em comunidades e posteriormente colorir cada uma.

Em grafos, uma comunidade representa um grupo de nós densamente conectados entre si, como por exemplo, grupos de família ou colegas de trabalho em uma rede social, refletindo estruturas latentes dentro do grafo.

Além disso, modularidade é uma métrica que quantifica a qualidade da divisão da rede em comunidades, comparando a densidade de arestas dentro das comunidades com a densidade esperada caso as arestas fossem distribuídas aleatoriamente. Dessa forma, a rede é comparada com uma aleatória com mesmo grau médio. Valores altos de modularidade indicam que há mais arestas dentro das comunidades do que o esperado.

## Metodologia
A rede utilizada foi gerada através de um notebook Jupyter disponibilizado no repositório da disciplina **[código](src/Final_Project.ipynb)** e dois arquivos contendo informações sobre os nós e arestas da rede **[nodes](src/GraphTest_nodes.txt)** e **[edges](src/GraphTest_edges.txt)**. Após a execução, o programa gerou a rede utilizada no trabalho **[network](src/final_network.gexf)**, cujo processamento foi feito utilizando a ferramenta Gephi, um software open-source para processamento e visualização de grafos, gerando as figuras e gráficos solicitados no trabalho.

## Organização do Repositório
O repositório contém todos os arquivos e códigos utilizados, além de todas as figuras geradas e o código-fonte da página necessária no requisito 3. Os códigos e arquivos utilizados para gerar a rede se encontram na pasta **[src](src/)**, enquanto as imagens geradas estão na pasta **[img](img/)**. Na pasta **[docs](docs/)** estão os arquivos exportados pelo Gephi para criação da página HTML.

## Resultados

### Requisito #01: Análise das Centralidades

A análise de centralidade em redes nos permite identificar os nós mais importantes ou influentes dentro de uma estrutura, sob diferentes perspectivas. Ao examinarmos os grafos apresentados, podemos observar as nuances de quatro métricas-chave: Degree, Closeness, Betweenness e Eigenvector Centrality.

#### 1. Degree Centrality (Centralidade de Grau)
Como podemos analisar na figura abaixo, a codificação das cores segue a seguinte lógica: quanto mais próximo de azul, menor a centralidade de grau do nó; e quanto mais próximo de vermelho, maior sua centralidade. Observamos a presença de quatro nós de cor vermelha intensa (e possivelmente maior tamanho), indicando uma centralidade de grau muito alta, ou seja, eles possuem um número significativamente elevado de ligações (ou conexões) diretas com outros nós. Embora existam vários nós com centralidade intermediária (em tons de laranja), a concentração dos pontos de maior centralidade nesta rede está justamente nesses poucos nós vermelhos, que atuam como hubs conectando diversas partes da estrutura.
<div align="center">
<img src="img/DegreeCentrality.png" alt="Gráfico 1 - Degree Centrality" width="600">
<p><strong>Figura 1:</strong> Degree Centrality.</p>
</div>

#### 2. Closeness Centrality (Centralidade de Proximidade)
No grafo que representa a Closeness Centrality, a coloração dos nós indica a distância média de um nó para todos os outros na rede. Nós em tons de vermelho possuem uma distância média menor, significando que são facilmente acessíveis e estão "próximos" de todos os outros pontos. Por outro lado, nós em tons de azul indicam uma distância média maior. No nosso grafo, os poucos nós vermelhos observados são, na verdade, "ilhas" ou componentes desconectados da rede principal e que acessam todos os componentes da ilha com facilidade. Quanto a nós que não possuem ligação, a inacessibilidade ao restante do grafo eleva drasticamente sua distância média para o conjunto total de nós, configurando uma baixa centralidade de proximidade.
<div align="center">
<img src="img/ClosenessCentrality.png" alt="Gráfico 2 - Closeness Centrality" width="600">
<p><strong>Figura 2:</strong> Closeness Centrality.</p>
</div>

#### 3. Betweenness Centrality (Centralidade de Intermediação)
O grafo de Betweenness Centrality destaca os nós que atuam como "pontes" ou intermediários no fluxo de informação da rede. Nós com alta centralidade de intermediação são representados por cores mais intensas (vermelho/laranja), indicando sua importância estratégica na conexão entre diferentes partes do grafo. É crucial diferenciar esta métrica da centralidade de grau: enquanto o grau mede apenas o número de conexões diretas, a intermediação avalia a frequência com que um nó se encontra no caminho mais curto entre outros pares de nós. No nosso grafo, percebemos claramente que os nós mais vermelhos, embora não necessariamente os de maior grau, são vitais para ligar diversos conjuntos de nós, confirmando seu papel como conectores essenciais e validando a singularidade da Betweenness Centrality em relação à contagem simples de ligações.
<div align="center">
<img src="img/BetweennessCentrality.png" alt="Gráfico 3 - Betweenness Centrality" width="600">
<p><strong>Figura 3:</strong> Betweenness Centrality.</p>
</div>

#### 4. Eigenvector Centrality (Centralidade de Autovetor)
Por fim, o grafo de Eigenvector Centrality ilustra a influência de um nó na rede, considerando não apenas a quantidade, mas a "qualidade" de suas conexões. Esta métrica reflete o princípio de que estar conectado a nós já influentes aumenta a própria influência. Como na analogia de ter um amigo influente (CR7) em vez de muitos amigos não influentes, a importância aqui deriva das conexões com nós bem conectados e relevantes. No grafo, o nó proeminentemente vermelho demonstra possuir uma alta centralidade de autovetor. Isso indica que, mesmo que seu número de conexões diretas não seja o maior, ele está estrategicamente ligado a outros nós que são, por sua vez, altamente influentes, propagando sua própria importância através dessas conexões de alto valor e estabelecendo-o como um nó de grande influência na rede.
<div align="center">
<img src="img/EigenvectorCentrality.png" alt="Gráfico 4 - Eigenvector Centrality" width="600">
<p><strong>Figura 4:</strong> Eigenvector Centrality.</p>
</div>

### Requisito #02: K-core e K-shell

O gráfico gerado representa a estrutura da rede em termos de k-core e k-shell, sendo o k-core a região central mais conectada e o k-shell, as camadas periféricas.
Os nós vermelhos fazem parte do 3-core, ou seja, pertencem a um subgrafo onde todos os nós têm pelo menos 3 conexões dentro do próprio núcleo, sendo assim um centro mais coeso e resiliente.
Ao mesmo tempo, os nós azuis representam o 2-shell, ou seja, pertencem ao 2-core, mas não ao 3-core, sendo uma casca intermediária da rede, conectados de forma menos densa.
Por fim, os nós pretos foram removidos nas etapas anteriores da decomposição e representam a periferia da rede.
Essa análise nos permite identificar os nós mais relevantes e mais importantes estruturalmente.

<div align="center">
<img src="img/Kcore.png" alt="Gráfico 5 - K-core" width="600">
<p><strong>Figura 5:</strong> K-core e K-shell.</p>
</div>


### Requisito #03: Página HTML Interativa

A figura a seguir ilustra a página HTML exportada pelo Gephi, com suporte à navegação, busca e filtros. A rede foi colorida com base nas comunidades detectadas utilizando a métrica de modularidade.
Cada cor representa uma comunidade detectada, e os nós são agrupados com base na densidade das conexões internas.

A rede possui múltiplas comunidades distintas, como pode ser visto pela diversidade de cores. Além disso, a divisão em cores compactas indica uma separação coesa entre os grupos, sugerindo que a rede não é homogênea, mas sim composta por subestruturas bem definidas.

<div align="center">
<img src="img/page.png" alt="Gráfico 6 - HTML page" width="600">
<p><strong>Figura 6:</strong> Página HTML.</p>
</div>
**Link para página:** [Link](https://gustavo2h.github.io/Final_Project_AED2/)
</div>
