# Inteligência Computacional Aplicada
## Projeto 2

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
Desenvolver a compreensão da manipulação de colunas com o pandas.

## Projeto

### Cabeçalho & Inicialização

Crie a pasta `projeto-2` e arquivo `projeto-2.ipynb` dentro da pasta de projetos e abra o arquivo do Colab.

Crie uma célula de texto e adicione o [cabeçalho do projeto](projeto-1.md#cabeçalho). Copie o objetivo deste arquivo. Adicione o texto abaixo contendo informações sobre o BCW ao cabeçalho. 

```
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
```

Faça o [importe o conjunto de dados](projeto-1.md#importando-o-pandas) `bcw.data`.

### Seleção de colunas

O pandas permite a seleção de colunas como atributo

```py
# Acessando a coluna thickness como atributo
df.thickness
```

ou como índices da matríz de dados.

```py
# Acessando a coluna thickness como índice
df['thickness']
```

O segundo segundo formato é preferível por permitir a seleção de mais de uma coluna, como segue.

```py
# Acessando as colunas thickness e id
df[['thickness', 'id']]
```

> Observe os duplo cochete: ``[[]]``

Como o resultado de uma seleção retorna um DataFrame, as funções e atributos que vimos no [projeto-1](projeto-1.md) podem ser utilizadas. Crie uma célula de código para cada desafio abaixo:
 - Mostre as 7 últimas linhas da coluna `mitoses`
 - Mostre as 7 primeiras linhas das colunas `size` e `adh`
 - Mostre o tipo da coluna `barenuclei`
 - Use `describe` nas colunas `chromatin` e `nucleoli`

### Buscando dados à partir dos valores das colunas

Uma maneira de observar os valores presentes em uma coluna é usando a função `unique` ou a função `value_counts` na coluna de interesse. Crie uma célula de código e teste as funções na coluna `barenuclei`. Verifique que um dos valores retornados é `'?'`.

O Pandas permite que possamos realizar buscas nas colunas com pequenas porções de código. Por exemplo, se quisermos observar as instâncias cuja coluna `barenuclei` tem valor `'?'`, utilizamos o código abaixo:

```py
df[df['barenuclei'] == '?']
```

Ou, se quisermos encontrar todas as instâncias do conjunto de dados cuja coluna `size` é maior ou igual a 7 **e** a coluna `shape` é menor que 3, utilizamos:

```
df[(df['size'] >= 7) & (df['shape'] < 3)]
```

> Este tipo de busca não é possível em listas normais do Python

Baseado no bloco acima, crie uma célula de código para cada desafio abaixo: 
 - Encontre as instâncias que têm classe benigna, quantas são?
 - Encontre as instâncias que têm classe maligna, quantas são?
 - Encontre as instâncias que têm classe benigna e mitose maior que 5
 - Encontre as instâncias que têm todas as colunas iguais a 3

> **Dica:** Use o atributo `shape` se necessário.

### Remoção de colunas

Algumas colunas dos dados pode ser redundantes e/ou desnecessárias. Cabe a nós entendermos a natureza dos dados e observar, por meio de métricas, que colunas são estas. Por enquanto, podemos apenas nos livrar da coluna `id` que não traz nenhuma informação relevante.

A função `drop` permite remover uma ou mais colunas e tambem permite remover linhas (instâncias) do nosso conjunto de dados. Desta forma, podemos remover a coluna `id` como segue:

```py
df = df.drop(['id'], axis=1)
```

> `axis=1` implica em dizer que estamos removendo colunas

A função realiza a remoção e retorna **uma novo** DataFrame, resultante da remoção da coluna. Então, para atualizar o nosso DataFrame salvamos o resultado do drop no próprio DataFrame. 

Contudo, esta função (e algumas outras) possuem o parâmetro `inplace` que permite aplicar a mudança no próprio DataFrame quando seu valor é `True`. Então uma outra maneira de escrever o código acima seria:

```py
df.drop(['id'], axis=1, inplace=True)
```

Como a função recebe uma lista como primeiro parâmetro, isso indica para nós que poderíamos remover várias colunas e linhas ao mesmo tempo.

Crie uma célula e cole o código para remover a coluna `id`. Crie uma segunda célula de código e escreva o código para remover a primeira e a última linha do conjunto de dados usando a função `drop`.

### Valores faltantes (*Missing values*)

Apesar do conjunto de dados ser composto por colunas do tipo inteiro, quando usamos `dtypes` vemos que a coluna `barenuclei` foi carregada como objeto (*object*).

Como visto, algumas instâncias apresentam o valor `'?'` na coluna `barenuclei`. Isto simboliza, na maioria das vezes, valores faltantes nos dados. Antes de resolvermos este problema, crie uma célula de texto e escreva um parágrafo sobre "por que os dados têm valores faltantes?".

Temos duas maneiras de nos livrarmos destes valores faltantes. 

1. Remover as linhas que possuem estes valores.
   
   > A desvantagem é que estamos perdendo mais informação que o necessário, pois existem algoritmos que conseguem trabalhar com  instâncias de valores faltantes, mas é aceitável quando a quantidade de instâncias excluídas é pequena.

2. Transformar o valor faltante em um outro valor como:
   1. A média dos valores daquela coluna;
   2. O valor mais frequente daquela coluna;
   3. Um valor 'numérico' mas que ainda representa um valor faltante.
   
   > A terceira alternativa parece ser a mais utilizada

O código a seguir realiza 3 ações
 - Troca de todos os valores '?' por `np.NaN` (*Not a Number*) — este valor é entendido como numérico, mas não é possível realizar computações com ele.
 - Realiza a remoção de todos as linhas que tenham algum valor `NaN`.
 - Transformar a coluna `barenuclei` para inteiro.

> Este último passo é importante pois boa parte dos algoritmos de aprendizado de máquina preferem trabalhar com números,

```py
# Trocando ? por NaN
df.replace('?', np.NaN, inplace=True)

# Eliminando linhas que contém NaN
df.dropna(inplace=True)

# Mudando o tipo da coluna
df['barenuclei'] = df['barenuclei'].astype('int64')
```

#### Desafio
Execute novamente a célula que faz o carregamento dos dados, crie uma célula de código e realize a troca de `'?'` na coluna `barenuclei` pelo valor mais frequente dela.

> Dica: Utilize a função `value_counts`

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