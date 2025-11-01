# 8. Relatorio
## 8.1 Definição do problema (contexto, atributos, classe);
## 8.2 Regras usadas para gerar a classe-alvo;
## 8.3 Descrição da base sintética;
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
#### 8.4.2.1 Descrição do Modelo OneR

O modelo **OneR (One Rule)** é um algoritmo de classificação simples e interpretável que constrói regras baseadas em um único atributo. Ele seleciona o atributo que gera a menor taxa de erro e cria regras de decisão com base nos seus valores discretizados. Apesar de sua simplicidade, o OneR pode oferecer resultados surpreendentemente eficazes em conjuntos de dados bem estruturados.

---

### 🔧 Funcionamento no Experimento

Neste experimento, o OneR escolheu o atributo **`tempo_reacao`** como base para a classificação. A partir dele, foram geradas 11 faixas de valores, cada uma associada a uma classe de satisfação (`alta`, `media`, `baixa`). Isso significa que o tempo de resposta do sistema foi considerado o melhor preditor da satisfação do usuário entre os atributos disponíveis.

**Exemplo de regras geradas:**
- Se `tempo_reacao < 3.05` → classe `alta`
- Se `tempo_reacao >= 6.845` → classe `baixa`

---

### 📈 Desempenho

O modelo apresentou um desempenho significativamente superior ao ZeroR:

- **Acurácia**: 73.24% de classificações corretas no conjunto de teste  
- **Kappa**: 0.5968, indicando boa concordância entre predição e realidade  
- **F-Measure média**: 0.734, refletindo equilíbrio entre precisão e recall  
- **Classes bem discriminadas**: especialmente a classe `baixa`, com 80.8% de acerto

#### 8.4.2.1 Informações do Experimento

| Item                  | Valor                         |
|-----------------------|-------------------------------|
| Algoritmo             | OneR -B 6                     |
| Relação               | usabilidade_americanas        |
| Instâncias            | 210                           |
| Atributos             | 6                             |
| Lista de Atributos    | tempo_tarefa, numero_erros, necessitou_ajuda, tempo_reacao, navegacao_intuitiva, satisfacao |
| Modo de Teste         | 66% treino / 34% teste        |

---

#### 8.4.2.2 Modelo Treinado

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


## 8.5 Resultados (tabelas, matrizes de confusão, prints de tela);
## 8.6 Análise crítica dos resultados em relação ao domínio de IHC;.
