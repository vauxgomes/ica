# Projeto: 1

[![Python](https://img.shields.io/badge/-python-gray?logo=python)](https://www.python.org/)
[![Vscode](https://img.shields.io/badge/-pandas-gray?logo=pandas)](https://code.visualstudio.com/)
[![Vscode](https://img.shields.io/badge/-jupyter-gray?logo=jupyter)](https://code.visualstudio.com/)

[← Voltar](../../README.md)

## Sumário

- [Objetivo](#objetivo)
- [Instruções](#instruções)
  - [Dados](#dados)
  - [Projeto](#projeto)
- [Como Submeter o Projeto](#como-submeter-o-projeto)
- [Ajuda](#ajuda)
- [Contatos](#contatos)

## Objetivo
Desenvolver a compreensão da manipulação de colunas com o pandas.

## Instruções

### Dados

1. Acessar o site do [*UCI Machine Learning Repository*](https://archive.ics.uci.edu/ml/datasets.php) e procurar pelo conjunto de dados chamado **Breast Cancer Wisconsin**.
2. Clicar em `Data Folder` e realizar o download do arquivo; `breast-cancer-wisconsin.data`;

### Projeto

#### Parte I

1. Criar uma pasta chamada `IFCE_ICA_SEUNOME` no diretório raiz do seu Google Drive, substituindo `SEUNOME`;
    1. Criar uma subpasta chamada `Projeto 1`;
    2. Fazer o upload do arquivo `.data` e `.names` para o a pasta do projeto;
    3. Criar um novo projeto do tipo Google Colab intitulado **projeto-0-`SEUNOME`**. 
       - [Clique aqui para obter ajuda!](#ajuda)


#### Parte II

1. `[Md]`: Criar e executar a célula abaixo, substituindo `SEUNOME` e o ano da turma:

```md
# Projeto: 1
Autor: SEUMOME
Turma: XXXX.X

## Objetivo
Desenvolver a compreensão da manipulação de colunas com o pandas.

## Dados
BCW é um banco de dados sobre câncer de Mama de Wisconsin (8 de janeiro de 1991) disponibilizado pelo hospital da Universidade de Wisconsin, em Madison, do **Dr. William H. Wolberg**. 

Os dados são suados para fazer uma separação de padrões de diagnóstico médico aplicado à citologia mamária. Para cada instância do dado apenas duas classes são possíveis:
 - Benigna
 - Maligna.

### Colunas
| # | NOME ORIGINAL | DESCRIÇÃO | NOME ESCOLHIDO |
| -- | -- | -- | -- |
| 1. | Sample code number        | Número de identificação | `id` |
| 2. | Clump Thickness           | Espessura do nódulo | `thickness` |
| 3. | Uniformity of Cell Size   | Uniformidade do tamanho do nódulo | `size` |
| 4. | Uniformity of Cell Shape  | Uniformidade do formato do nódulo | `shape` |
| 5. | Marginal Adhesion         | Quantifica a união das células | `adh` |
| 6. | Single Epithelial Cell Size | O tamanho que as células atingem antes da divisão celular | `epsize` |
| 7. | Bare Nuclei               | Degeneração das células | `barenuclei` |
| 8. | Bland Chromatin           | Descreve uma "textura" uniforme do núcleo de células benígnas | `chromatin` |
| 9. | Normal Nucleoli           | Descreve uma parte do núcleo onde ocorre a produção de ribissomos | `nucleoli` |
| 10. | Mitoses                   | Quantifica a mitose | `mitoses` |
| 11. | Class                     | Classes do dados| `class` |

> ***As descrições das colunas estão sujeitas a erros**

#### Classes do conjunto de dados

| Classe | Valor |
| -- | -- |
| Benigno | 2 |
| Maligno | 4 |

## Estudo do conjunto de dados
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
arquivo = '/content/drive/My Drive/IFCE_IAC_SEUNOME/Projeto NUMERODOPROJETO/breast-cancer-wisconsin.data'

# Nome das Colunas
nomes = ['id', 'thickness', 'size', 'shape', 'adh', 'epsize', 'barenuclei', 'chromatin', 'nucleoli', 'mitoses', 'class']

```

4. `[Code]`: Criar e executar a célula abaixo, realizando a leitura do arquivo `.data` por meio do `pandas` em uma variável chamada `df`:

```py
# Leitura dos dados
df = pd.read_csv(arquivo, names=nomes)
```

#### Parte III 

A coluna `barenuclei` está com o tipo `object`. Por isso ela não aparece na saída do método `describe()`. 

1. Copie, execute o código abaixo e preencha o valor de `X`:

```py
# Visualizando contagem de uma coluna
df['barenuclei'].value_counts()

''' A saída deste código mostra que existem X valores '?' que representam valores faltantes. '''
```

2. Copie, execute o código abaixo e preencha o valor de `X`:

```py
# Encontrando quais linhas em barenuclei tem valor '?'
df[(df['barenuclei'] == '?')]

''' A saída deste código mostra que as linhas com valores ? são: 23, 40, X... '''
```

3. Copie e execute o código abaixo e preencha o valores `X` e `Y`:

```py
#
df = df.replace('?', np.NaN) # Trocando ? por NaN
df = df.dropna() # Eliminando linhas que contém NaN

''' Antes os dados continham X linhas e agora contém apenas Y linhas '''
```

> **Atenção**: descubra o total de linhas originais antes de executar a célula acima.

4. Copie e execute o código abaixo e descreva o que ele faz nos comentários

```py
df['class'] = df['class'].replace(2, 0) # Comentário
df['class'] = df['class'].replace(4, 1) # Comentário
```

#### Parte V - Usando os valores das colunas

Podemos fazer buscas nos valores das colunas com pequenas porções de código. O exemplo abaixo mostra todas as linhas do conjunto de dados onde a coluna `size` é maior ou igual a 7 e a coluna `shape` é menor que 3.

1. Copie e execute o código abaixo e preencha o valor de `X`:

```py
# Buscas de colunas
df[(df['size'] >= 7) & (df['shape'] < 3)]

''' X linhas tem size é maior ou igual a 7 e a shape é menor que 3 '''
```

2. Baseado no bloco acima encontre:
   - Quantas linhas tem classe benigna
   - Quantas linhas tem classe maligna
   - Quantas linhas tem classe benigna e mitose maior que 5
   - Quantas linhas tem todas as colunas iguais a 3

> **Dica**: Use o atributo `shape` se necessário.

## Como submeter o Projeto
1. Procure o botão `Compartilhar` no Google Colab e escolha `copiar link`;
2. Envie o link na tarefa do Google Salada de Aula, relacionada ao projeto.

 > **Atenção**: Execute todas as células antes de enviar o link*

## Ajuda
 - [Google Colab para Iniciantes](https://medium.com/machina-sapiens/google-colab-guia-do-iniciante-334d70aad531)
 - [Markdown para Iniciantes](https://produtive.me/guia/markdown-um-guia-para-iniciantes/)
 - [Uma Introdução Simples ao Pandas](https://medium.com/data-hackers/uma-introdu%C3%A7%C3%A3o-simples-ao-pandas-1e15eea37fa1)

## Contatos
Em caso de dúvidas procure contato via:
 - Google Sala de Aula
 - Email Institucional