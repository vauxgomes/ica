# Inteligência Computacional Aplicada
## Projeto 1

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
Iniciar o aprendizado do pandas.

## Projeto

### Cabeçalho

Crie a pasta `projeto-1` e arquivo `projeto-1.ipynb` dentro da pasta de projetos e abra o arquivo do Colab.

Adicione uma célula de texto e cole o conteúdo abaixo, preenchendo as informações do número do projeto, autor e turma.

```md
# Projeto: X
 - Autor: XXXX
 - Turma: XXXX

## Objetivo
Iniciar o aprendizado do pandas.
```

> Usaremos este padrão de cabeçalho de agora em diante

### Importando o Pandas

**Pandas** é uma biblioteca de software para manipulação e análise de dados. Em particular, oferece estruturas e operações para manipular tabelas numéricas e séries temporais. É software livre sob a licensa licença BSD.

O pandas não é uma biblioteca padrão do Python (isto é, ela não vem instalada por padrão). Seria necessário fazer a instalação da biblioteca no nosso ambiente local, mas o Colab já possui a biblioteca em sua base (isto facilita o trabalho).

Crie uma célula de código e importe o Pandas como segue.

```py
# Pandas
import pandas as pd
```

### Montando o Drive 

Para permitir o acesso do Colab aos dados salvos do Drive, crie uma célula de código como segue.

```py
# Google Drive
from google.colab import drive
drive.mount('/content/drive', force_remount=True)
```

> Na primeira vez que você executar este código, uma caixa de texto e um link devem aparecer na tela. Clique no link e siga até encontrar o código que você deve colar na caixa de texto. 

### Lendo o conjunto de dados

Para ler o conjunto de dados, crie uma célula de código como segue e ajuste os valores das constantes.

```py
# Constantes
ROOT_FOLDER = 'IFCE_ICA_SEUNOME' # Pasta da disciplina
DATA_FILE = 'bcw.data' # Nome do conjunto de dados

DATA_PATH = '/content/drive/My Drive/{}/data/{}'.format(ROOT_FOLDER, DATA_FILE)
```

Crie uma nova célula de código como segue.

```py
# Leitura dos dados
df = pd.read_csv(DATA_PATH, 
    names=['id', 'thickness', 'size', 'shape', 
        'adh', 'epsize', 'barenuclei', 'chromatin',
        'nucleoli', 'mitoses', 'class'])
```

Logo, o nosso conjunto de dados foi carregado na variável `df`.

> Este nome de variável é frequentemente usado por lembrar o tipo de dado DataFrame do Pandas.

Ao ser carregado o conjunto de dados, o Pandas assume que a primeira linha do arquivo informa o nome das colunas, contudo o arquivo `bcw.data` não está neste formato. Por isso preenchemos o valor do atributo `names` como uma lista contendo o nome das colunas.

### Informações sobre os dados

#### Atributo `shape`

O atributo `shape` retorna o formato da matriz que representa os dados. Ou seja, o número de linhas (índice 0) e colunas (índice 1) dos dados. Crie a seguinte célula de código.

```py
print('Este conjunto de dados tem {} linhas e {} colunas'.format(
    df.shape[0], df.shape[1]))
```

#### Atributo `dtype`

O atributo `dtypes` retorna o tipo de dado de cada coluna. 

> Este atributo será relevante quando formos preprocessar dados para ajustar aos algoritmos de aprendizado de máquina

Crie a seguinte célula de código. E observe o tipo de cada coluna.

```py
df.dtype
```

#### Atributo `columns`

O atributo `columns` retorna uma série com o nome de todas as colunas. Crie a seguinte célula de código.

```py
df.columns
```

#### Função `head` e `tail`

As funções `head` e `tail` exibem *x* instâncias (linhas) do começo e do fim do arquivo carregado, respectivamente. Crie a seguinte célula de código.

1. 
    ```py
    # 10 primeiras instâncias
    df.head()
    ```

1. 
    ```py
    # 5 primeiras instâncias
    df.head(5)
    ```

1.
    ```py
    # 10 últimas instâncias
    df.tail()
    ```

1.
    ```py
    # 3 últimas instâncias
    df.tail(3)
    ```

### Função `describe`

A função `describe`, de forma simplificada, exibe alguns dados estatísticos. Crie a seguinte célula de código.

```py
df.describe()
```

Copie a célula de texto a seguir e explique o que é cada informação do describe significa.

```
- **count**:
- **mean**:
- **std**:
- **min**:
- **25%**:
- **50%**:
- **75%**:
- **max**:
```

### Função `corr`

A função `corr`, retorna uma matriz da correlação estatística entre as colunas do conjunto de dados. Podemos usar esta informação para descartar algumas colunas. Crie a seguinte célula de código.

```py
df.corr()
```

## Como submeter o Projeto

Compatilhe **o link da pasta** do projeto na tarefa do Google Salada de Aula relacionada a este projeto.

## Ajuda

- [Google Colab: o que é e como usar?](https://www.alura.com.br/artigos/google-colab-o-que-e-e-como-usar)
 - [Markdown para iniciantes](https://produtive.me/guia/markdown-um-guia-para-iniciantes/)

## Contatos

Em caso de dúvidas procure contato via:
 - Google Sala de Aula
 - Email Institucional

[↑ Topo](#inteligência-computacional-aplicada)