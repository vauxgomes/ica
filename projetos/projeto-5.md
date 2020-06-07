# Projeto: 5

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
Introduzir o vocabulário de aprendizado de máquina usado no `scikit-learn` e mostrar um exemplo simples.

## Instruções

### Dados

1. Acessar o site do [*UCI Machine Learning Repository*](https://archive.ics.uci.edu/ml/datasets.php) e procurar pelo conjunto de dados chamado **Iris**.
2. Clicar em `Data Folder` e realizar o download dos arquivos `iris.data` e `iris.names`;

### Projeto

#### Parte I

1. Criar uma pasta chamada `IFCE_ICA_SEUNOME` no diretório raiz do seu Google Drive, substituindo `SEUNOME`;
    1. Criar uma subpasta chamada `Projeto 5`;
    2. Fazer o upload do arquivo `.data` e `.names` para o a pasta do projeto;
    3. Criar um novo projeto do tipo Google Colab intitulado **projeto-5-`SEUNOME`**. 
       - [Clique aqui para obter ajuda!](#ajuda)


#### Parte II

1. `[Md]`: Criar e executar a célula abaixo, substituindo `SEUNOME` e o ano da turma:
   - Procure os locais onde estão escritos `PESQUISA`
   - Pesquise na internet e escreva pequenos parágrafos sobre os assuntos relacionados.

```md
# Projeto: 5
 - Autor: SEUMOME
 - Turma: XXXX.X

## Objetivo
Introduzir o vocabulário de aprendizado de máquina usado no `scikit-learn` e mostrar um exemplo simples.

## Scikit-Learn
A scikit-learn é uma biblioteca de aprendizado de máquina de código aberto para a linguagem de programação Python.

## Aprendizado de máquina

### A descrição do problema
Aprendizado de Máquina é uma subárea de Mineração de Dados que busca maneiras de conferir às máquinas a  habilidade de aprender a partir de conjuntos de dados sem que estas sejam explicitamente programadas para tal tarefa. A máquina, então, deve ser capaz de extrair e generalizar informações de dados, e, posteriormente, usar estas informações para compreender dados nunca observados.

### Conjunto de dados
Cada **linha** do conjunto de dados é chamada de **instância** (ou exemplo, observação), e cada **coluna** é chamada de **atributo** (ou característica).

O conjunto de dados é entendido como um núvem de pontos em um espaço *n*-dimensional, onde *n* é o número de colunas dos dados.

#### Tipos de Atributos
  - **Qualitativo** (relativo a categorias): 
    - **Nominal**
    - **Ordinal**
    - **Binário**
  - **Quantitativo** (relativo a quantidades):
    - **Discreto**: Valores inteiros
    - **Contínuo**: Amplitude de valores entre dois intervalos

#### Exemplo de dados

| # | Att 1 | Att 2 | Att 3 | Att 4 | Att 5 |
| -- | -- | -- | -- | -- | -- |
| 1. | 10 | 0.54 | True | low | Maria |
| 2. | 3 | 0.29 | False | medium | José |
| **Tipos** | *Discreto* | *Contínuo* | *Binário* | *Ordinal* | *Nominal* |


### Aprendizado supervisionado
Problema no qual os dados possuem uma coluna adicional que nós queremos prever. Este tipo de problema se subdivide em:

  - `Problema de classificação`: PESQUISA
  - `Problema de regressão`: PESQUISA

### Aprendizado não supervisionado
Problema no qual os dados não possuem um valor alvo a ser previsto pelos algoritmos de aprendizagem. O objetivo aqui é descobrir similaridades entre os grupos de instâncias.

## Carregando e tratando os dados
```

2. `[Code]`: Criar e executar a célula abaixo realizando o `import` das bibliotecas `pandas`, um classificador da biblioteca `sklearn` e montando o drive do Google:

```py
# Bibliotecas
import pandas as pd
from sklearn.svm import SVC

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

3. `[Code]`: Criar e executar a célula abaixo, realizando a leitura do arquivo `.data` e ajustando os valores da coluna `class`:

```py
# Leitura dos dados
df = pd.read_csv(arquivo, names=nomes)

# Ajuste na coluna class
df['class'] = df['class'].astype('category').cat.codes

#
df.head(10)
```

4. `[Md]`: Crie e execute a célula abaixo

```md
## Dividindo os dados
Para este exemplo utilizaremos o conjunto completo de dados (carregado na variável `df`) para **treinar** o algoritmo, mas esta não é uma prática que nos trará bons resultados estatísticos.

Para que o algoritmo de aprendizado de máquina possa processar, precisamos apenas dividir os dados em **atributos** (chamamos de `X`) e **classe** (chamamos de `y`).
```

5. `[Code]`: Crie e execute a célula abaixo

```py
# Assumindo que a classe esteja na última coluna
X = df.iloc[:, :-1] # Da coluna 0 até a penútima
y = df.iloc[:, -1] # Somente a última coluna
```

### Parte III

1. `[Md]`: Criar e executar a célula abaixo

```md
## Utilizando o Scikit Learn
A função `.fit()` dos algoritmos do Scikit Learn dá início ao treinamento do algoritmo. A função `.predict()` realiza a predição com base no que foi treinado.
```

2. `[Code]`: Criar e executar a célula abaixo

```py
# Instanciando o objeto
model = SVC()

# Treinando modelo de aprendizagem
model.fit(X, y)
```

3. `[Code]`: Criar e executar a célula abaixo

```py
''' 
Criando um conjunto de teste composto por uma 
instância de cada classe.
'''

X_hat = X.iloc[[0, 50, 100]]
y_hat = y.iloc[[0, 50, 100]]

print('\nDADOS\n', X_hat)
print('\nCLASSES\n', y_hat)
```

4. `[Code]`: Criar e executar a célula abaixo

```py
# Predizendo dados
pred = model.predict(X_hat)
```

5. `[Code]`: Criar e executar a célula abaixo

```py
for i, p in enumerate(pred):
    print(f'Original: {y_hat.iloc[i]} → Predição: {p}')
```

## Como submeter o Projeto
1. Procure o botão `Compartilhar` no Google Colab e escolha `copiar link`;
2. Envie o link na tarefa do Google Salada de Aula, relacionada ao projeto.

 > **Atenção**: Execute todas as células antes de enviar o link

## Ajuda

 - [Google Colab para Iniciantes](https://medium.com/machina-sapiens/)
 - [Uma Introdução ao Aprendizado de Máquina com Scikit-Learn](https://scikit-learn.org/stable/tutorial/basic/tutorial.html)
 - [Entendendo tipos de dados](https://www.geeksforgeeks.org/understanding-data-attribute-types-qualitative-and-quantitative/)

## Contatos
Em caso de dúvidas procure contato via:
 - Google Sala de Aula
 - Email Institucional

[↑ Topo](#projeto-5)