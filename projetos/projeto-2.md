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

### Inicialização

Crie a pasta `projeto-2` e arquivo `projeto-2.ipynb` dentro da pasta de projetos e abra o arquivo do Colab.

Crie uma célula de texto e adicione o [cabeçalho do projeto](projeto-1.md#cabeçalho). Copie o objetivo deste arquivo. Adicione ao cabeçalho, o texto abaixo contendo informações sobre o BCW. 

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
 - Mostre as 7 primeiras linhas das colunas `size` e `adh`
 - Mostre as 7 últimas linhas da coluna `misoses`
 - Mostre o tipo da coluna `barenuclei`

### Colunas desnecessárias

Algumas colunas dos dados pode ser redundantes e/ou desnecessárias. Cabe a nós entendermos a natureza dos dados e observar, por meio de métricas, que colunas são estas. Por enquanto, podemos apenas nos livrar da coluna `id` que não traz nenhuma informação relevante.

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