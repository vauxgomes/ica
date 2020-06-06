# Projeto: 4

[![Python](https://img.shields.io/badge/-python-gray?logo=python)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/-pandas-gray?logo=pandas)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/-jupyter-gray?logo=jupyter)](https://jupyter.org/)

[← Voltar](../README.md)

## Sumário

- [Objetivo](#objetivo)
- [Instruções](#instruções)
  - [Dados](#dados)
  - [Projeto](#projeto)
- [Como Submeter o Projeto](#como-submeter-o-projeto)
- [Ajuda](#ajuda)
- [Contatos](#contatos)

## Objetivo
Entender correlação estatística por meio da visualização dos dados

## Instruções

### Dados

1. Acessar o site do [*UCI Machine Learning Repository*](https://archive.ics.uci.edu/ml/datasets.php) e procurar pelo conjunto de dados chamado **Iris**.
2. Clicar em `Data Folder` e realizar o download dos arquivos `iris.data` e `iris.names`;

### Projeto

#### Parte I

1. Criar uma pasta chamada `IFCE_ICA_SEUNOME` no diretório raiz do seu Google Drive, substituindo `SEUNOME`;
    1. Criar uma subpasta chamada `Projeto 4`;
    2. Fazer o upload do arquivo `.data` e `.names` para o a pasta do projeto;
    3. Criar um novo projeto do tipo Google Colab intitulado **projeto-4-`SEUNOME`**. 
       - [Clique aqui para obter ajuda!](#ajuda)


#### Parte II

1. `[Md]`: Criar e executar a célula abaixo, substituindo `SEUNOME` e o ano da turma:

```md
# Projeto: 4
Autor: SEUMOME
Turma: XXXX.X

## Objetivo
Entender correlação estatística por meio da visualização dos dados

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

## Importação do conjunto de dados
```

2. `[Code]`: Criar e executar a célula abaixo realizando o `import` das bibliotecas `numpy` e `pandas` e montando o drive do Google:

```py
# Bibliotecas
import numpy as np
import pandas as pd

''' 
Na primeira vez que você executar esta parte do código, 
uma caixa de texto e um link devem aparecer na tela. 
Clique no link e siga até encontrar o código que você 
deve colar na caixa de texto. 
'''

# Google Drive
from google.colab import drive
drive.mount('/content/drive', force_remount=True)

# Caminho do arquivo: Substituia SEUNOME e NUMERODOPROJETO
arquivo = '/content/drive/My Drive/IFCE_IAC_SEUNOME/Projeto NUMERODOPROJETO/iris.data'

# Nome das Colunas
nomes = ['sepal_length', 'sepal_width', 'petal_length', 'petal_width', 'class']
```

4. `[Code]`: Criar e executar a célula abaixo, realizando a leitura do arquivo `.data` por meio do `pandas` em uma variável chamada `df`:
   - Preencha o valor de `X`

```py
# Leitura dos dados
df = pd.read_csv(arquivo, names=nomes)

# 10 Primeiras linhas do dado
df.head(10)
```

1. `[Md]`: Criar e executar a célula abaixo

```md
## Ajuste na coluna `class`
```

### Parte III

A colunas `class` é do tipo `object` e isto dificulta o seu uso no momento de plotar os gráficos. Vamos converter o tipo da coluna em `category` e então sobrepor os códigos das categorias nos valores originais da coluna `class`.

1. `[Code]`: Criar e executar a célula abaixo para observarmos os **valores originais** da coluna

```py
df['class'].unique()
```

2. `[Code]`: Criar e executar a célula abaixo, alterando os valores da coluna

```py
df['class'] = df['class'].astype('category').cat.codes
```

3. `[Code]`: Criar e executar a célula abaixo para observarmos os **novos valores** da coluna

```py
df['class'].unique()
```

### Parte IV

1. `[Md]`: Criar e executar a célula abaixo

```md
## Correlação
A correlação é qualquer relação dentro de uma ampla classe de relações estatísticas que envolva dependência entre duas variáveis (Wikipedia).

### Coeficiente de Correlação Linear
O coeficiente linear mede o grau da correlação (e a direcção dessa correlação - se positiva ou negativa) entre duas variáveis de escala métrica (intervalar ou de rácio/razão) (Wikipedia).

Este coeficiente, normalmente representado por ρ assume apenas valores entre -1 e 1.
  - ρ ≥ 1  → Significa uma correlação positiva entre as duas variáveis.
  - ρ ≤ -1 → Significa uma correlação negativa entre as duas variáveis.
  - ρ = 0  → Significa que as duas variáveis não dependem linearmente uma da outra. No entanto, pode existir uma dependência não linear. Assim, o resultado ρ = 0 deve ser investigado por outros meios.

Quanto mais extremo é o valor de ρ, mas próximo de uma reta é a distribuição dos valores observados.

### Pandas
O método `.corr()` do pandas nos dá a matriz de correlação entre as colunas do nosso conjunto de dados. Por padrão o coeficiente calculado é o de Pearson, mas é possível utilizar outros coeficientes.
```

[Clique aqui para obter ajuda!](#ajuda)

2. `[Code]`: Criar e executar a célula abaixo para observarmos a matriz de correlação:
   - Responda aos comentários

```py
df.corr()

'''
Que tipo de correlação existe entre:
  a.) sepal_length x petal_length? RESPOSTA
  b.) sepal_width x petal_length? RESPOSTA

Que correlação é mais forte?
 ( ) sepal_width x sepal_length
 ( ) sepal_width x petal_length
'''
```

### Parte V

1. `[Md]`: Criar e executar a célula abaixo

```md
## Observando correlação
```

2. `[Code]`: Criar e executar as células abaixo que exibem a correlação entre `petal_length` e `petal_width`; entre `sepal_length` e `petal_width`; e entre `sepal_width` e `petal_length`.

```py
# petal_length × petal_width
df.plot.scatter(x='petal_length', y='petal_width', figsize=(8, 6))
```

```py
# sepal_length × petal_width
df.plot.scatter(x='sepal_length', y='petal_width', figsize=(8, 6))
```

```py
# sepal_width × petal_length
df.plot.scatter(x='sepal_width', y='petal_length', figsize=(8, 6))
```

### Parte VI

Neste momento, também é interessante observar os valores do classe e como eles se distribuem nos gráficos acima. Logo, cada classe do conjunto de dados será representado por uma cor diferente.

1. `[Code]`: Criar e executar as células abaixo que exibem a correlação entre `petal_length` e `petal_width`; entre `sepal_length` e `petal_width`; e entre `sepal_width` e `petal_length`.

```py
# petal_length × petal_width
df.plot.scatter(x='petal_length', y='petal_width', c='class', colormap='viridis', figsize=(8, 6))
```

```py
# sepal_length × petal_width
df.plot.scatter(x='sepal_length', y='petal_width', c='class', colormap='viridis', figsize=(8, 6))
```

```py
# sepal_width × petal_length
df.plot.scatter(x='sepal_width', y='petal_length', c='class', colormap='viridis', figsize=(8, 6))
```

2. `[Md]`: Criar e executar a célula abaixo:
   - Escreva um parágrafo na seção abaixo comentando sobre como os pontos estão distribuídos nos gráficos acima, se eles parecem agrupados de alguma maneira; e fale sobre a linearidade da distribuição dos pontos.

```md
### Considerações pessoais
```

## Como submeter o Projeto
1. Procure o botão `Compartilhar` no Google Colab e escolha `copiar link`;
2. Envie o link na tarefa do Google Salada de Aula, relacionada ao projeto.

 > **Atenção**: Execute todas as células antes de enviar o link

## Ajuda
 - [Uma Introdução Simples ao Pandas](https://medium.com/data-hackers/uma-introdu%C3%A7%C3%A3o-simples-ao-pandas-1e15eea37fa1)
 - [Visualização de Dados no Pandas](https://pandas.pydata.org/pandas-docs/stable/user_guide/visualization.html)
 - [Correlação no Pandas](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.corr.html)

## Contatos
Em caso de dúvidas procure contato via:
 - Google Sala de Aula
 - Email Institucional

[`↑ Topo`](#projeto:-4)