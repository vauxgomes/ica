# Inteligência Computacional Aplicada
## Projeto 3

[![Python](https://img.shields.io/badge/-python-gray?logo=python)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/-pandas-gray?logo=pandas)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/-jupyter-gray?logo=jupyter)](https://jupyter.org/)

[← Voltar](../README.md)

## Sumário

- [Objetivo](#objetivo)
- [Projeto](#projeto)
- [Como Submeter o Projeto](#como-submeter-o-projeto)
- [Ajuda](#ajuda)
- [Contatos](#contatos)

## Objetivo
Entender correlação estatística e encontrar colunas redundantes por meio da visualização dos dados

## Projeto

### Cabeçalho & Inicialização

Acesse o site do [UCI Repository](projeto-0.md#uci-repository) e procure pelo conjunto de dados chamado **Iris**. Clique em `Data Folder` e realize o download dos arquivo `iris.data` (que contém o conjunto de dados a ser estudado) e `iris.names` (que contém informações sobre o conjunto de dados). Faça o upload dos arquivos na pasta `data/` no Drive. 

Crie a pasta `projeto-3` e arquivo `projeto-3.ipynb` dentro da pasta de projetos e abra o arquivo do Colab.

Crie uma célula de texto e adicione o cabeçalho do projeto. Copie o objetivo deste arquivo. Adicione o texto abaixo ao cabeçalho. 

```
## Dados
O conjunto de dados Iris  é um conjunto de dados multivariados introduzido pelo estatístico e biólogo britânico Ronald Fisher em seu artigo de 1936. O problema abordade é o de taxonomia de flores.

### Colunas
| # | COLUNA | DESCRIÇÃO |
| -- | -- | -- |
| 1. | `sepal_length` | Comprimento da Sépala 
| 2. | `sepal_width` |  Largura da Sépala |
| 3. | `petal_length` | Comprimento da Pétala 
| 4. | `petal_width` | Largura da Pétala |

> ***As descrições das colunas estão sujeitas a erros**

#### Classes do conjunto de dados
As classes do problema são diferentes tipos de Iris:

 - Iris-setosa,
 - Iris-versicolor,
 - Iris-virginica

## Correlação
A correlação é qualquer relação dentro de uma ampla classe de relações estatísticas que envolva dependência entre duas variáveis (Wikipedia).

### Coeficiente de Correlação Linear
O coeficiente linear mede o grau da correlação (e a direcção dessa correlação - se positiva ou negativa) entre duas variáveis de escala métrica (intervalar ou de rácio/razão) (Wikipedia).

Este coeficiente, normalmente representado por ρ assume apenas valores entre -1 e 1.
  - ρ ≥ 1  → Significa uma correlação positiva entre as duas variáveis.
  - ρ ≤ -1 → Significa uma correlação negativa entre as duas variáveis.
  - ρ = 0  → Significa que as duas variáveis não dependem linearmente uma da outra. No entanto, pode existir uma dependência não linear. Assim, o resultado ρ = 0 deve ser investigado por outros meios.

Quanto mais extremo é o valor de ρ, mas próximo de uma reta é a distribuição dos valores observados.
```

Crie uma célula de código e faça o importe das bibliotecas e a leitura do conjunto de dados. Utilize a lista de nomes das colunas abaixo.

```py
# Nome das Colunas
nomes = ['sepal_length', 'sepal_width', 'petal_length', 'petal_width', 'class']
```

Importe também a biblioteca Matplotlib.

```py
import matplotlib.pyplot as plt
```

### Ajuste na coluna `class`

A coluna `class` é do tipo `object` e isto é um inconveniente no momento do desenho dos gráficos. Neste ponto podemos usar a função `replace` e `astype` para trocar os valores das classes (que são *strings*) por valores inteiros. Crie uma célula de código e escreva o código descrito. 

> Frequentemente, a classe não possui uma ordem, isto é, podemos usar quaisquer números para representar as classes, bastando que estes sejam diferentes entre si.

Para conjuntos de dados com muitas classes, não é viável escrever todos os replaces. Em vez disso, podemos nos aproveitar de algumas funções do Pandas para realizar a troca dos valores.

O código a seguir transforma o tipo da coluna `class` para categoria (lista contendo um código para cada valor diferente na coluna) e substitui os valores original da coluna.

```py
df['class'] = df['class'].astype('category').cat.codes
```

Outra maneira, é usando um dicionário de mapeamento com a função `replace`. Execute a célula que carrega o conjunto de dados.

Copie e execute o código abaixo que mapeia os valores indesejados de coluna `class` para um valor desejado.

```py
mapa = {
    # Nome da coluna
    'class': {
        # Valor indesejado → Valor desejado
        'Iris-setosa': 0,
        'Iris-versicolor': 1,
        'Iris-virginica': 2
    }
}

df.replace(mapa, inplace=True)
```

> É possível ajustar o dicinário para realizar o replace de várias colunas.

### Correlação linear
A correlação é qualquer relação dentro de uma ampla classe de relações estatísticas que envolva dependência entre duas variáveis — no nosso caso, entre duas colunas.

A correlação pode nos auxiliar na simplificação dos dados. Isto é interessante pois facilita o trabalho dos algoritmos de aprendizado. Resumidamente, se duas colunas (que não sejam a classe) possuem uma correlação considerada alta (valor que nós estipularemos), podemos **descartar** uma delas, pois terão um efeito equivalente sobre a **classe** do problema (isto é, do conjunto de dados).

Crie uma célula de código e execute o código abaixo que exibe a correlação entre cada par de variável dos dados.

```py
df.corr()
```

#### Visualização

Uma maneira de visualizar a correlação entre duas variáveis (colunas) é plotando a distribuição dos dados e observando o cruzamento das figuras. Crie as células de código a seguir.

```py
# Correlação próxima de zero
# sepal_length x sepal_width → -0.109369
df['sepal_length'].plot.hist(color='green', alpha=0.8, figsize=(8, 6))
df['sepal_width'].plot.hist(color='red', alpha=0.8, figsize=(8, 6))
```

```py
# Correlação próxima de 1
# petal_length x petal_width → 0.962757
df['petal_length'].plot.hist(color='green', alpha=0.8, figsize=(8, 6))
df['petal_width'].plot.hist(color='red', alpha=0.8, figsize=(8, 6))
```

Enquanto o gráfico de cima apresenta quase nenhum cruzamento, boa parte dos valores da coluna `petal_width` intersecta os valores da coluna `petal_length`. Neste caso, **poderíamos remover `petal_width` ou `petal_length`** sem muita perda de informação.

> Um efeito parecido pode ser encontrado usando a função `plot.kde`

Outra forma de visualizarmos a mesma informação é plotar uma núvem de pontos e verificar se os dados formam uma linha (ascendente ou descendente). Crie as células de código a seguir.

```py
# sepal_length x sepal_width → -0.109369
df.plot.scatter(x='sepal_length', y='sepal_width', color='green', figsize=(8, 6))
```

```py
# petal_length x petal_width → 0.962757
df.plot.scatter(x='petal_length', y='petal_width', figsize=(8, 6))
```

Crie uma célula de texto e tente descrever as diferenças entre estes dois últimos gráficos. Informe qual(is) coluna(s) você removeria deste conjunto de dados.

Crie uma célula de código remova a(s) coluna(s) mencionada(s) acima.

```py
df.drop(columns=['A', 'B', 'C'])
```

#### Extra

Assumindo um `limite = 0.9`, poderíamos criar um código que remove colunas "desnecessárias". Execute a célula Crie o execute a célula de código abaixo.

```py
sel = [True]*df.shape[1] # True para todas as colunas
lim = 0.9 # Limite

for i, x in enumerate(df.columns[:-1]):
  for j, y in enumerate(df.columns[i+1:-1]):
    if abs(corr.iloc[i, i+1+j]) >= lim:
      sel[i] = False # Descarte da coluna

sel = df.columns[sel] # Nomes das colunas
df = df[cols] # Atualização do conjunto de dados

df.head(10)
```

> Se você acredita que eu tentei usar as cores do IF nos gráficos acima comente "acredito" no fórum da semana; ou comente "c-loko", caso contrário.

#### Visualização em relação à classe

Neste momento, também é interessante observar os valores do classe e como eles se distribuem nos gráficos acima. Logo, cada classe do conjunto de dados será representado por uma cor diferente.

Execute novamente a célula que carrega os dados e a que transforma os valores da coluna `class`. Crie e execute as células abaixo:

```py
# petal_length × petal_width
df.plot.scatter(x='petal_length', y='petal_width', c='class', colormap='viridis', figsize=(8, 6))
```

```py
# sepal_length × sepal_width
df.plot.scatter(x='sepal_length', y='sepal_width', c='class', colormap='viridis', figsize=(8, 6))
```

## Como submeter o Projeto

Compatilhe **o link da pasta** do projeto na tarefa do Google Salada de Aula relacionada a este projeto.

## Ajuda

 - [Visualização de Dados no Pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/visualization.html)
 - [How does correlation help in feature selection](https://towardsdatascience.com/feature-selection-correlation-and-p-value-da8921bfb3cf#:~:text=How%20does%20correlation%20help%20in,one%20of%20the%20two%20features.)

## Contatos

Em caso de dúvidas procure contato via:
 - Google Sala de Aula
 - Email Institucional

[↑ Topo](#inteligência-computacional-aplicada)