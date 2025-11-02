# 8. Relatório
## 8.1 Definição do problema (contexto, atributos, classe):
A usabilidade de interfaces digitais é um fator determinante para a inclusão e permanência de usuários em ambientes online. Quando uma interface é intuitiva e bem estruturada, a navegação em um site ou aplicativo torna-se uma experiência leve e satisfatória. Porém, para usuários com pouca familiaridade digital, até mesmo ações simples (como localizar um produto, reconhecer um botão ou compreender o caminho de navegação) podem representar verdadeiros desafios. Essas dificuldades não apenas comprometem a experiência do usuário, mas também restringem o acesso a serviços importantes, como realizar compras online, agendar atendimentos ou obter informações públicas.

Partindo dessa perspectiva, o presente relatório tem como foco a aplicação de técnicas de classificação supervisionada para avaliar a usabilidade do site da Americanas entre pessoas com baixa familiaridade digital. Para isso, foi construída uma base de dados sintética, elaborada a partir de atributos que representam diferentes maneiras de interação com páginas da web.

A principal motivação deste trabalho está em promover ambientes digitais mais acessíveis e acolhedores, especialmente para quem ainda enfrenta dificuldades com o uso da tecnologia. Diminuir barreiras de navegação, reduzir erros frequentes e evitar que o usuário desista de realizar tarefas são ações fundamentais para fortalecer a inclusão digital.

Diante do crescimento constante do comércio eletrônico, compreender os padrões de dificuldade e transformá-los em melhorias práticas de design é uma estratégia de grande valor. Nesse contexto, foi criada uma base contendo 200 registros simulados, inspirados em atividades típicas de testes de usabilidade (como pesquisar um item ou adicioná-lo ao carrinho) reunindo tanto métricas objetivas quanto subjetivas.
A base de dados utilizada contém registros que representam o comportamento de usuários durante a navegação em sites. Entre os atributos considerados estão:

**Atributos Preditores**

| **Atributo**            | **Tipo**      | **Descrição**                                                                 |
|---------------------------|---------------|------------------------------------------------------------------------------|
| `tempo_navegacao`        | Numérico      | Tempo total (em **minutos**) que o usuário permaneceu navegando no site.     |
| `numero_cliques`         | Numérico      | Quantidade total de interações (cliques) realizadas durante a navegação.     |
| `taxa_sucesso`           | Numérico      | Percentual de tarefas concluídas corretamente pelo usuário.                  |
| `nivel_confusao`         | Nominal `{baixo, medio, alto}` | Grau de confusão relatado pelo usuário durante a navegação.       |
| `familiaridade_digital`  | Nominal `{baixa, media, alta}` | Classificação do nível de experiência digital do usuário.         |
| `numero_erros`           | Numérico      | Quantidade de erros cometidos (ex.: cliques errados, recarregamentos indevidos). |
| `satisfacao_geral`       | Numérico (1–5) | Avaliação subjetiva da experiência geral com o site.                         |

#### **Classe-Alvo**  
- **Nome**: `satisfacao`  
- **Tipo**: Nominal (multiclasse)  
- **Valores possíveis**: `{alta, media, baixa}`  
- **Distribuição**: Balanceada (~70 instâncias por classe)

---

## 8.2 Regras usadas para gerar a classe-alvo:

A classe **“usabilidade percebida”** foi gerada a partir de um conjunto de regras lógicas e heurísticas descritas no prompt de criação da base de dados. Essas regras simulam o julgamento humano sobre a experiência de uso de um site, considerando a relação entre desempenho, erros e satisfação.
As principais diretrizes aplicadas foram:


**Alta Usabilidade:**

Atribuída a casos em que o usuário apresenta alto nível de familiaridade digital, baixo número de erros, alta taxa de sucesso nas tarefas (acima de 80%) e satisfação geral superior a 4. O tempo de navegação tende a ser otimizado e o número de cliques é adequado à complexidade das tarefas.

**Usabilidade Média:**

Ocorre quando o usuário demonstra nível intermediário de familiaridade, taxa de sucesso moderada (entre 50% e 80%), e satisfação entre 3 e 4. Nesses casos, há algumas dificuldades pontuais, mas a interação geral ainda é considerada satisfatória

**Baixa Usabilidade:**

Definida para usuários com baixo nível de familiaridade digital, alto número de erros,  taxa de sucesso inferior a 50%, e satisfação igual ou inferior a 2. Frequentemente, o tempo de navegação é elevado devido à dificuldade em compreender a interface, e o número de cliques é desproporcional à tarefa pretendida.

**Essas regras permitem representar de forma coerente a percepção de usabilidade, correlacionando fatores objetivos (como erros e tempo de navegação) e subjetivos (como satisfação e confusão percebida).**

**A partir dessa base, foram aplicados algoritmos de aprendizado de máquina no Weka (*ZeroR*, *OneR*, *Naive Bayes*, *IBK* e *J48*)  para analisar o desempenho preditivo e identificar os atributos mais relevantes para a avaliação da usabilidade em contextos de baixa familiaridade digital.**

---

## 8.3 Descrição da base sintética:
### 8.3.1  Objetivo

A base de dados `usabilidade_americanas` foi construída com o objetivo de avaliar a experiência de usuários durante a interação com a plataforma da Americanas, uma das maiores varejistas online do Brasil. O foco está em identificar padrões que influenciam a **satisfação do usuário** com base em métricas de desempenho, comportamento e percepção durante a navegação.

---

### 8.3.2 Estrutura da Base

- **Total de instâncias**: 210  
- **Total de atributos**: 6 (sendo 5 preditores e 1 classe alvo)

| Atributo               | Tipo       | Descrição                                                                 |
|------------------------|------------|---------------------------------------------------------------------------|
| `tempo_tarefa`         | Numérico   | Tempo (em minutos) que o usuário levou para concluir uma tarefa          |
| `numero_erros`         | Numérico   | Quantidade de erros cometidos durante a tarefa                           |
| `necessitou_ajuda`     | Categórico (`sim`, `nao`) | Indica se o usuário precisou de ajuda para concluir a tarefa         |
| `tempo_reacao`         | Numérico   | Tempo de resposta do sistema durante a interação                         |
| `navegacao_intuitiva`  | Categórico (`sim`, `nao`) | Se o usuário considerou a navegação intuitiva                          |
| `satisfacao`           | Categórico (`alta`, `media`, `baixa`) | **Classe alvo**: nível de satisfação do usuário com a experiência |

---

### 8.3.3 Distribuição da Classe `satisfacao`

A variável alvo `satisfacao` é categórica e representa o nível de contentamento do usuário com a experiência na plataforma. As categorias são:

- `alta`: Usuários altamente satisfeitos
- `media`: Usuários moderadamente satisfeitos
- `baixa`: Usuários insatisfeitos

---

## 8.4 Descrição dos experimentos no Weka;
### 8.4.1 Modelo ZeroR
#### 8.4.1.1 Descrição do Experimento

Este experimento teve como objetivo avaliar a usabilidade da plataforma Americanas por meio de métricas de desempenho e satisfação dos usuários. Para isso, foi utilizado um conjunto de dados com **210 instâncias** e **6 atributos** relacionados à experiência de uso:

- **tempo_tarefa**: duração para completar uma tarefa  
- **numero_erros**: quantidade de erros cometidos  
- **necessitou_ajuda**: se o usuário precisou de assistência  
- **tempo_reacao**: tempo de resposta do sistema  
- **navegacao_intuitiva**: percepção de facilidade na navegação  
- **satisfacao**: nível de satisfação (classe alvo: alta, média, baixa)

---

#### 8.4.1.2 Metodologia

- **Algoritmo utilizado**: ZeroR — um classificador de base que ignora os atributos e sempre prediz a classe mais frequente.  
- **Modo de avaliação**: divisão estratificada de **66% para treino** e **34% para teste**.  
- **Classe majoritária**: `alta`, que foi usada como predição constante pelo ZeroR.

---

#### 8.4.1.3 Informações do Modelo

| Item                  | Valor                         |
|-----------------------|-------------------------------|
| Algoritmo             | ZeroR                         |
| Relação               | usabilidade_americanas        |
| Instâncias            | 210                           |
| Atributos             | 6                             |
| Lista de Atributos    | tempo_tarefa, numero_erros, necessitou_ajuda, tempo_reacao, navegacao_intuitiva, satisfacao |
| Modo de Teste         | 66% treino / 34% teste        |

---

#### 8.4.1.4 Modelo Treinado

| Descrição                     | Valor         |
|------------------------------|---------------|
| Classe Predita               | alta          |
| Tempo para construir modelo  | 0 segundos    |

---

#### 8.4.1.5 Avaliação no Conjunto de Teste

| Métrica                        | Valor        |
|--------------------------------|--------------|
| Instâncias Corretas           | 20 (28.169%) |
| Instâncias Incorretas         | 51 (71.831%) |
| Estatística Kappa             | 0            |
| Erro Absoluto Médio           | 0.4458       |
| Raiz do Erro Quadrático Médio | 0.4732       |
| Erro Absoluto Relativo        | 100%         |
| Erro Quadrático Relativo      | 100%         |
| Total de Instâncias Testadas  | 71           |

---

#### 8.4.1.6 Acurácia Detalhada por Classe

| Classe | TP Rate | FP Rate | Precisão | Recall | F-Measure | ROC Area | PRC Area |
|--------|---------|---------|----------|--------|-----------|----------|----------|
| alta   | 0.000   | 0.000   | ?        | 0.000  | ?         | 0.500    | 0.352    |
| media  | 1.000   | 1.000   | 0.282    | 1.000  | 0.440     | 0.500    | 0.282    |
| baixa  | 0.000   | 0.000   | ?        | 0.000  | ?         | 0.500    | 0.366    |
| **Média Ponderada** | 0.282   | 0.282   | ?        | 0.282  | ?         | 0.500    | 0.337    |

---

#### 8.4.1.7 Matriz de Confusão

| Classe Verdadeira | alta | media | baixa |
|-------------------|------|-------|-------|
| alta              | 0    | 25    | 0     |
| media             | 0    | 20    | 0     |
| baixa             | 0    | 26    | 0     |
---

### 8.4.2 Modelo OneR
#### 8.4.2.1 Descrição do experimento

O modelo **OneR (One Rule)** é um algoritmo de classificação simples e interpretável que constrói regras baseadas em um único atributo. Ele seleciona o atributo que gera a menor taxa de erro e cria regras de decisão com base nos seus valores discretizados. Apesar de sua simplicidade, o OneR pode oferecer resultados surpreendentemente eficazes em conjuntos de dados bem estruturados.

---

#### 8.4.2.2 Funcionamento no Experimento

Neste experimento, o OneR escolheu o atributo **`tempo_reacao`** como base para a classificação. A partir dele, foram geradas 11 faixas de valores, cada uma associada a uma classe de satisfação (`alta`, `media`, `baixa`). Isso significa que o tempo de resposta do sistema foi considerado o melhor preditor da satisfação do usuário entre os atributos disponíveis.

**Exemplo de regras geradas:**
- Se `tempo_reacao < 3.05` → classe `alta`
- Se `tempo_reacao >= 6.845` → classe `baixa`

---

#### 8.4.2.3 Desempenho

O modelo apresentou um desempenho significativamente superior ao ZeroR:

- **Acurácia**: 73.24% de classificações corretas no conjunto de teste  
- **Kappa**: 0.5968, indicando boa concordância entre predição e realidade  
- **F-Measure média**: 0.734, refletindo equilíbrio entre precisão e recall  
- **Classes bem discriminadas**: especialmente a classe `baixa`, com 80.8% de acerto

#### 8.4.2.4 Informações do Experimento

| Item                  | Valor                         |
|-----------------------|-------------------------------|
| Algoritmo             | OneR -B 6                     |
| Relação               | usabilidade_americanas        |
| Instâncias            | 210                           |
| Atributos             | 6                             |
| Lista de Atributos    | tempo_tarefa, numero_erros, necessitou_ajuda, tempo_reacao, navegacao_intuitiva, satisfacao |
| Modo de Teste         | 66% treino / 34% teste        |

---

#### 8.4.2.5 Modelo Treinado

| Atributo Base Utilizado | tempo_reacao                |
|-------------------------|-----------------------------|
| Regras Geradas          |                             |
| `< 3.05`                | alta                        |
| `< 3.395`               | media                       |
| `< 3.745`               | alta                        |
| `< 4.035`               | media                       |
| `< 4.27`                | alta                        |
| `< 4.55`                | media                       |
| `< 4.79`                | alta                        |
| `< 6.175`               | media                       |
| `< 6.58`                | baixa                       |
| `< 6.845`               | media                       |
| `>= 6.845`              | baixa                       |
| Instâncias Corretas     | 170 / 210                   |
| Tempo de Construção     | 0.01 segundos               |

---

#### 8.4.2.3 Avaliação no Conjunto de Teste

| Métrica                        | Valor        |
|--------------------------------|--------------|
| Instâncias Corretas           | 52 (73.24%)  |
| Instâncias Incorretas         | 19 (26.76%)  |
| Estatística Kappa             | 0.5968       |
| Erro Absoluto Médio           | 0.1784       |
| Raiz do Erro Quadrático Médio | 0.4224       |
| Erro Absoluto Relativo        | 40.02%       |
| Erro Quadrático Relativo      | 89.26%       |
| Total de Instâncias Testadas  | 71           |

---

#### 8.4.2.4 Acurácia Detalhada por Classe

| Classe | TP Rate | FP Rate | Precisão | Recall | F-Measure | MCC   | ROC Area | PRC Area |
|--------|---------|---------|----------|--------|-----------|-------|----------|----------|
| alta   | 0.800   | 0.109   | 0.800    | 0.800  | 0.800     | 0.691 | 0.846    | 0.710    |
| media  | 0.550   | 0.196   | 0.524    | 0.550  | 0.537     | 0.349 | 0.677    | 0.415    |
| baixa  | 0.808   | 0.089   | 0.840    | 0.808  | 0.824     | 0.725 | 0.859    | 0.749    |
| **Média Ponderada** | 0.732   | 0.126   | 0.737    | 0.732  | 0.734     | 0.607 | 0.803    | 0.641    |

---

#### 8.4.2.5 Matriz de Confusão

| Classe Verdadeira | alta | media | baixa |
|-------------------|------|-------|-------|
| alta              | 20   | 5     | 0     |
| media             | 5    | 11    | 4     |
| baixa             | 0    | 5     | 21    |
---

### 8.4.3 Modelo J48
####  8.4.3.1 Descrição do Modelo J48

O **J48** é uma implementação da árvore de decisão C4.5, amplamente utilizada por sua capacidade de gerar modelos interpretáveis e eficazes. Ele constrói uma árvore de decisão com base na divisão recursiva dos dados, escolhendo os atributos que melhor separam as classes com base no ganho de informação.

#### 8.4.3.2 Funcionamento no Experimento

Neste experimento, o J48 construiu uma árvore com base nos atributos `numero_erros` e `tempo_tarefa`. A árvore resultante é simples, com apenas 4 folhas, mas altamente eficaz. As regras de decisão mostram que a combinação entre o número de erros cometidos e o tempo gasto na tarefa é suficiente para prever com precisão o nível de satisfação do usuário.

#### 8.4.3.3 Desempenho

O modelo atingiu **100% de acurácia** no conjunto de teste, classificando corretamente todas as 71 instâncias. Além disso, todas as métricas de avaliação (precisão, recall, F-measure, MCC, ROC e PRC) atingiram o valor máximo de **1.000**, indicando um desempenho perfeito.

#### 8.4.3.4  Informações do Experimento

| Item                  | Valor                         |
|-----------------------|-------------------------------|
| Algoritmo             | J48 (árvore de decisão)       |
| Parâmetros            | -C 0.25 -M 2                   |
| Relação               | usabilidade_americanas        |
| Instâncias            | 210                           |
| Atributos             | 6                             |
| Lista de Atributos    | tempo_tarefa, numero_erros, necessitou_ajuda, tempo_reacao, navegacao_intuitiva, satisfacao |
| Modo de Teste         | 66% treino / 34% teste        |

---

#### 8.4.3.5 Estrutura da Árvore Gerada

| Regra de Decisão                                 | Classe Predita |
|--------------------------------------------------|----------------|
| numero_erros ≤ 1 ∧ tempo_tarefa ≤ 4.94           | alta           |
| numero_erros ≤ 1 ∧ tempo_tarefa > 4.94           | media          |
| numero_erros > 1 ∧ tempo_tarefa ≤ 4.94           | media          |
| numero_erros > 1 ∧ tempo_tarefa > 4.94           | baixa          |

- **Número de folhas**: 4  
- **Tamanho da árvore**: 7 nós  
- **Tempo de construção**: 0.06 segundos

---

#### 8.4.3.6 Avaliação no Conjunto de Teste

| Métrica                        | Valor     |
|--------------------------------|-----------|
| Instâncias Corretas           | 71 (100%) |
| Instâncias Incorretas         | 0 (0%)    |
| Estatística Kappa             | 1.0       |
| Erro Absoluto Médio           | 0.0       |
| Raiz do Erro Quadrático Médio | 0.0       |
| Erro Absoluto Relativo        | 0%        |
| Erro Quadrático Relativo      | 0%        |
| Total de Instâncias Testadas  | 71        |

---

#### 8.4.3.7 Acurácia Detalhada por Classe

| Classe | TP Rate | FP Rate | Precisão | Recall | F-Measure | MCC   | ROC Area | PRC Area |
|--------|---------|---------|----------|--------|-----------|-------|----------|----------|
| alta   | 1.000   | 0.000   | 1.000    | 1.000  | 1.000     | 1.000 | 1.000    | 1.000    |
| media  | 1.000   | 0.000   | 1.000    | 1.000  | 1.000     | 1.000 | 1.000    | 1.000    |
| baixa  | 1.000   | 0.000   | 1.000    | 1.000  | 1.000     | 1.000 | 1.000    | 1.000    |
| **Média Ponderada** | 1.000 | 0.000   | 1.000    | 1.000  | 1.000     | 1.000 | 1.000    | 1.000    |

---

#### 8.4.3.8 Matriz de Confusão

| Classe Verdadeira | alta | media | baixa |
|-------------------|------|-------|-------|
| alta              | 25   | 0     | 0     |
| media             | 0    | 20    | 0     |
| baixa             | 0    | 0     | 26    |

---

### 8.4.4 Modelo IBk (KNN)
#### 8.4.4.1 Descrição do Modelo IBk (KNN)

O **IBk** é a implementação do algoritmo **K-Nearest Neighbors (KNN)** no Weka. Neste experimento, foi utilizado com **K=1**, ou seja, a classificação de uma nova instância é baseada na classe do seu **vizinho mais próximo** no conjunto de treinamento, utilizando a **distância Euclidiana** como métrica de similaridade.

#### 8.4.4.2 Funcionamento no Experimento

O modelo não realiza um treinamento tradicional, pois armazena todas as instâncias de treinamento e realiza a classificação no momento da predição, comparando a nova instância com as mais próximas. Isso o torna simples, porém eficaz em muitos contextos.

#### 8.4.4.3 Desempenho

O modelo apresentou um desempenho excelente:

- **Acurácia** de **95.77%**, com apenas 3 erros em 71 instâncias.
- **Kappa** de **0.9364**, indicando forte concordância entre as predições e os valores reais.
- Todas as classes foram bem classificadas, com destaque para a classe `alta`, que teve **100% de acerto**.

#### 8.4.4.4 Informações do Experimento

| Item                  | Valor                                                                 |
|-----------------------|-----------------------------------------------------------------------|
| Algoritmo             | IBk (K-Nearest Neighbors - K=1)                                       |
| Parâmetros            | -K 1 -W 0 -A EuclideanDistance (first-last)                           |
| Relação               | usabilidade_americanas                                                |
| Instâncias            | 210                                                                   |
| Atributos             | 6                                                                     |
| Lista de Atributos    | tempo_tarefa, numero_erros, necessitou_ajuda, tempo_reacao, navegacao_intuitiva, satisfacao |
| Modo de Teste         | 66% treino / 34% teste                                                |

---

#### 8.4.4.5 Avaliação no Conjunto de Teste

| Métrica                        | Valor        |
|--------------------------------|--------------|
| Instâncias Corretas           | 68 (95.77%)  |
| Instâncias Incorretas         | 3 (4.23%)    |
| Estatística Kappa             | 0.9364       |
| Erro Absoluto Médio           | 0.037        |
| Raiz do Erro Quadrático Médio | 0.1664       |
| Erro Absoluto Relativo        | 8.29%        |
| Erro Quadrático Relativo      | 35.15%       |
| Total de Instâncias Testadas  | 71           |

---

#### 8.4.4.6 Acurácia Detalhada por Classe

| Classe | TP Rate | FP Rate | Precisão | Recall | F-Measure | MCC   | ROC Area | PRC Area |
|--------|---------|---------|----------|--------|-----------|-------|----------|----------|
| alta   | 1.000   | 0.022   | 0.962    | 1.000  | 0.980     | 0.970 | 0.989    | 0.962    |
| media  | 0.950   | 0.039   | 0.905    | 0.950  | 0.927     | 0.898 | 0.955    | 0.874    |
| baixa  | 0.923   | 0.000   | 1.000    | 0.923  | 0.960     | 0.940 | 0.962    | 0.951    |
| **Média Ponderada** | 0.958 | 0.019   | 0.960    | 0.958  | 0.958     | 0.939 | 0.970    | 0.933    |

---

#### 8.4.4.7 Matriz de Confusão

| Classe Verdadeira | alta | media | baixa |
|-------------------|------|-------|-------|
| alta              | 25   | 0     | 0     |
| media             | 1    | 19    | 0     |
| baixa             | 0    | 2     | 24    |

---

### 8.4.5 Modelo Naive Bayes
#### 8.4.5.1 Descrição do Modelo Naive Bayes

O **Naive Bayes** é um classificador probabilístico baseado no Teorema de Bayes, que assume independência entre os atributos. Apesar dessa simplificação, o modelo costuma apresentar bom desempenho em diversas tarefas de classificação.

#### 8.4.5.2 Funcionamento no Experimento

Neste experimento, o Naive Bayes utilizou as distribuições estatísticas dos atributos contínuos (como média e desvio padrão) e as frequências dos atributos categóricos para calcular a probabilidade de cada classe (`alta`, `media`, `baixa`) para cada instância.

#### 8.4.5.3 Desempenho
O modelo obteve uma **acurácia de 91.55%**, com apenas 6 erros em 71 instâncias. A **estatística Kappa de 0.8734** indica forte concordância entre as predições e os valores reais. A classe `baixa` teve **precisão perfeita (1.000)**, enquanto as demais também foram bem classificadas.

---

#### 8.4.5.4 Informações do Experimento

| Item                  | Valor                         |
|-----------------------|-------------------------------|
| Algoritmo             | NaiveBayes                    |
| Relação               | usabilidade_americanas        |
| Instâncias            | 210                           |
| Atributos             | 6                             |
| Lista de Atributos    | tempo_tarefa, numero_erros, necessitou_ajuda, tempo_reacao, navegacao_intuitiva, satisfacao |
| Modo de Teste         | 66% treino / 34% teste        |

---

#### 8.4.5.5 Estatísticas dos Atributos por Classe

| Atributo            | Classe | Média    | Desvio Padrão | Peso | Precisão |
|---------------------|--------|----------|----------------|------|----------|
| tempo_tarefa        | alta   | 3.1138   | 1.216          | 70   | 0.1006   |
|                     | media  | 6.6142   | 4.1622         | 70   | 0.1006   |
|                     | baixa  | 12.2283  | 4.0685         | 70   | 0.1006   |
| numero_erros        | alta   | 0.4      | 0.4899         | 70   | 1.0000   |
|                     | media  | 2.1857   | 1.8539         | 70   | 1.0000   |
|                     | baixa  | 5.6429   | 2.3545         | 70   | 1.0000   |
| tempo_reacao        | alta   | 3.0747   | 1.1986         | 70   | 0.0470   |
|                     | media  | 4.9521   | 1.0965         | 70   | 0.0470   |
|                     | baixa  | 7.5579   | 1.3446         | 70   | 0.0470   |

#### 8.4.5.6 Variáveis Categóricas

| Atributo              | Classe | sim  | não  | Total |
|-----------------------|--------|------|------|-------|
| necessitou_ajuda      | alta   | 21.0 | 51.0 | 72.0  |
|                       | media  | 35.0 | 37.0 | 72.0  |
|                       | baixa  | 53.0 | 19.0 | 72.0  |
| navegacao_intuitiva   | alta   | 65.0 | 7.0  | 72.0  |
|                       | media  | 34.0 | 38.0 | 72.0  |
|                       | baixa  | 16.0 | 56.0 | 72.0  |

---

#### 8.4.5.7 Avaliação no Conjunto de Teste

| Métrica                        | Valor        |
|--------------------------------|--------------|
| Instâncias Corretas           | 65 (91.55%)  |
| Instâncias Incorretas         | 6 (8.45%)    |
| Estatística Kappa             | 0.8734       |
| Erro Absoluto Médio           | 0.0711       |
| Raiz do Erro Quadrático Médio | 0.1865       |
| Erro Absoluto Relativo        | 15.96%       |
| Erro Quadrático Relativo      | 39.40%       |
| Total de Instâncias Testadas  | 71           |

---

#### 8.4.5.8 Acurácia Detalhada por Classe

| Classe | TP Rate | FP Rate | Precisão | Recall | F-Measure | MCC   | ROC Area | PRC Area |
|--------|---------|---------|----------|--------|-----------|-------|----------|----------|
| alta   | 0.960   | 0.022   | 0.960    | 0.960  | 0.960     | 0.938 | 0.998    | 0.997    |
| media  | 0.950   | 0.098   | 0.792    | 0.950  | 0.864     | 0.810 | 0.986    | 0.971    |
| baixa  | 0.846   | 0.000   | 1.000    | 0.846  | 0.917     | 0.882 | 0.997    | 0.996    |
| **Média Ponderada** | 0.915 | 0.035   | 0.927    | 0.915  | 0.917     | 0.881 | 0.995    | 0.989    |

---

#### 8.4.5.9 Matriz de Confusão

| Classe Verdadeira | alta | media | baixa |
|-------------------|------|-------|-------|
| alta              | 24   | 1     | 0     |
| media             | 1    | 19    | 0     |
| baixa             | 0    | 4     | 22    |

---

## 8.5 Resultados (tabelas, matrizes de confusão, prints de tela):

---

Os resultados a seguir foram extraídos e resumidos dos outputs dos classificadores executados no software Weka. Cada classificador foi avaliado em um split de 66% treino e 34% teste.

### 8.5.1 Tabelas de Métricas

As métricas principais incluem acurácia, Kappa, MAE e RMSE, derivadas diretamente das saídas do WEKA. Os dados foram inserido em uma tabela comparativa para facilitar a visualização.

| Classificador | Acurácia (%) | Kappa  | MAE    | RMSE   | Instâncias Corretas (de 71) |
|---------------|--------------|--------|--------|--------|-----------------------------|
| J48          | 100.00      | 1.0000 | 0.0000 | 0.0000 | 71                         |
| IBK (k=1)    | 95.77       | 0.9364 | 0.0370 | 0.1664 | 68                         |
| NaiveBayes   | 91.55       | 0.8734 | 0.0711 | 0.1865 | 65                         |
| OneR         | 73.24       | 0.5968 | 0.1784 | 0.4224 | 52                         |
| ZeroR        | 28.17       | 0.0000 | 0.4458 | 0.4732 | 20                         |

### 8.5.2 Matrizes de Confusão

Cada matriz de confusão mostra a distribuição de classificações corretas e incorretas por classe (alta, media, baixa).  
Foram extraídas diretamente dos outputs, onde 'a' = alta, 'b' = media, 'c' = baixa.  
As matrizes revelam confusões principalmente entre media e baixa em modelos menos precisos.

- **J48**:
  
  | a | b | c |  <-- classified as |
  |---|---|---|--------------------|
  |25 | 0 | 0 |  a = alta |
  |0 | 20 | 0 |  b = media |
  |0 | 0 | 26 |  c = baixa |

- **IBK (k=1)**:
  
  | a | b | c |  <-- classified as |
  |---|---|---|--------------------|
  | 25 | 0 | 0 |  a = alta |
  | 1 | 19 | 0 |  b = media |
  | 0 | 2 | 24 |  c = baixa |
  
- **NaiveBayes**:
  
  | a | b | c |  <-- classified as |
  |---|---|---|--------------------|
  | 24 | 1 | 0 |  a = alta | 
  | 1 | 19 | 0 |  b = media | 
  | 0 | 4 | 22 |  c = baixa | 

- **OneR**:
  
  | a | b | c |  <-- classified as |
  |---|---|---|--------------------|
  | 20 | 5 | 0 |  a = alta |
  | 5 | 11 | 4 |  b = media |
  | 0 | 5 | 21 |  c = baixa |

- **ZeroR**:
  
  | a | b | c |  <-- classified as |
  |---|---|---|--------------------|
  | 0 | 25 | 0 | a = alta |
  | 0 | 20 | 0 | b = media |
  | 0 | 26 | 0 | c = baixa |
  
### 8.5.3 Prints de Tela

- Print Algoritmo ZeroR
  
  <img width="1044" height="1029" alt="image" src="https://github.com/user-attachments/assets/0c2c32a1-f2ed-42ac-9cfe-16f281b3755c" />

- Print Algoritmo OneR

  <img width="1017" height="1190" alt="image" src="https://github.com/user-attachments/assets/57a4304a-78e0-48f5-93e9-ab66a41da71b" />

- Print Algoritmo J48

  <img width="1043" height="1218" alt="image" src="https://github.com/user-attachments/assets/4449e0fc-0994-4df2-8e81-9434c7a369f2" />

- Print Árvore de Classificação J48

  <img width="1900" height="579" alt="image" src="https://github.com/user-attachments/assets/9d952cb3-258f-4de4-9c83-ca9999c52f54" />


- Print Algoritmo NaiveBayes

  <img width="991" height="1541" alt="image" src="https://github.com/user-attachments/assets/32aa4a1b-117d-4a47-9ff3-7e20748929a3" />

- Print Algoritmo IBk
  
  <img width="971" height="1001" alt="image" src="https://github.com/user-attachments/assets/515dfb48-d09d-4536-902a-8b2e6af8aa56" />

## 8.6 Análise crítica dos resultados em relação ao domínio de IHC;.
### Esta seção apresenta a análise crítica dos resultados obtidos com modelos de **aprendizado de máquina** aplicados a uma base de dados sintética sobre a **usabilidade do site da Americanas**, focada em **usuários com pouca experiência digital**. O objetivo é relacionar os achados ao campo de **Interação Humano-Computador (IHC)** e indicar pontos práticos para melhoria.

---

## 1. Contextualização dos Resultados

Os modelos foram treinados para prever o nível de **satisfação** (alta, média ou baixa) com base em variáveis como:

- `tempo_tarefa`  
- `numero_erros`  
- `necessitou_ajuda`  
- `tempo_reacao`  
- `navegacao_intuitiva`

Essas variáveis representam medidas comuns em IHC:
- **Eficiência**: tempo para completar uma tarefa.  
- **Precisão**: número de erros cometidos.  
- **Satisfação**: percepção do usuário sobre facilidade e conforto ao usar o site.

### Eficiência e Precisão
O modelo **J48** obteve alta acurácia no conjunto de teste, identificando regras do tipo:
> "Satisfação alta quando número de erros < 2 e tempo de tarefa < 5 minutos."

Isso indica que **reduzir erros e o tempo de execução** tende a aumentar a satisfação, especialmente entre usuários iniciantes.

### Aspectos Subjetivos
Variáveis como **facilidade de navegação** e **necessidade de ajuda** foram menos usadas pelos modelos. Em dados reais, esses fatores costumam mostrar emoções e frustrações que métricas puramente numéricas não revelam.

### Comparação entre Modelos
- Modelos como **IBK** e **NaiveBayes** tiveram bom desempenho, mas confundiram níveis “média” e “baixa”.  
- Modelos simples (OneR, ZeroR) servem como base de comparação e mostram que **um único fator isolado não explica bem a experiência humana**.

---

## 2. Pontos Positivos

### Facilidade de Interpretação
Modelos interpretáveis (como J48) mostram claramente como tempo e erros influenciam a satisfação, o que ajuda designers a identificar limites importantes para melhorias.

### Dados Balanceados
A base usada tinha equilíbrio entre categorias, evitando que o modelo favorecesse um grupo específico e tornando os resultados mais justos.

### Relevância para Usuários Iniciantes
Os resultados apontam problemas típicos de quem tem pouca prática digital, reforçando a necessidade de interfaces simples e com feedback claro.

---

## 3. Pontos Críticos e Limitações

### Dados Sintéticos
Os dados foram gerados artificialmente, sem todo o ruído humano (emoções, distrações, variações contextuais). Por isso, resultados ideais podem não se repetir em testes reais.

### Menos Valorização do Lado Humano
Algumas variáveis importantes para medir aprendizado e memorização foram pouco consideradas. Modelos também podem não capturar como variáveis se influenciam mutuamente.

### Baixa Generalização
Um único conjunto de dados limita a capacidade de aplicar os resultados a outros públicos. A falta de informações sobre idade, escolaridade e contexto social reduz a validade para um público diverso.

### Risco de Confiar Demais em Modelos
A boa performance numérica pode dar falsa sensação de solução completa. Em IHC, sempre é preciso validar com observação direta e entrevistas com usuários.

---

## 4. Aplicações Práticas

### Melhorias no Design
- Priorizar redução de tempo e número de erros nas tarefas.  
- Simplificar fluxos complexos e tornar ações mais óbvias.

### Uso Complementar de Métodos
- Integrar o uso de modelos com entrevistas, observação de uso e testes com usuários reais.  
- Usar resultados do modelo para guiar onde focar estudos qualitativos.

### Acessibilidade para Iniciantes
- Criar tutoriais simples e orientações no próprio site.  
- Usar linguagem clara e ícones autoexplicativos.  
- Projetar telas com menos elementos e ações diretas.

---

## Conclusão

Modelos de aprendizado de máquina, especialmente modelos interpretáveis, podem ajudar a identificar padrões objetivos relacionados à satisfação do usuário. No entanto, por se tratar de dados sintéticos e por conta da complexidade humana, é essencial combinar esses resultados com observações reais e métodos qualitativos. A recomendação é usar uma abordagem mista: **dados + contato direto com usuários**, alinhada às heurísticas de Nielsen, para projetar interfaces que realmente atendam às pessoas.



