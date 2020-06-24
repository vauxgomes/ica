# Inteligência Computacional Aplicada
## Projeto 0

[![Python](https://img.shields.io/badge/-python-gray?logo=python)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/-pandas-gray?logo=pandas)](https://pandas.pydata.org/)
[![Jupyter](https://img.shields.io/badge/-jupyter-gray?logo=jupyter)](https://jupyter.org/)

[← Voltar](../README.md)

## Sumário

- [Objetivo](#objetivo)
- [Ferramentas](#ferramentas)
  - [Google Colab](#google-colaboratory)
  - [UCI Repository](#uci-repository)
- [Dados](#dados)
- [Projeto](#projeto)
- [Como Submeter o Projeto](#como-submeter-o-projeto)
- [Ajuda](#ajuda)
- [Contatos](#contatos)

## Objetivo
Iniciar o aprendizado do Jupyter Notebooks no Google Colab.

## Ferramentas
### Google Colabolatory
O Google Colaboratory, carinhosamente chamado de **Colab**, é um serviço de nuvem gratuito hospedado pelo Google para incentivar a pesquisa de Aprendizado de Máquina e Inteligência Artificial.

É possível acessar o Colab diretamente pelo seguinte https://colab.research.google.com/notebooks/intro.ipynb.

> É necessário possuir uma conta Google fara fazer uso da ferramenta

#### Colab & Drive

Neste projeto e nos demais precisaremos conectar o Colab com o Google Drive. 

Para facilitar, crie uma pasta com esquema de diretórios na pasta **raíz** do seu Drive:

```
.                                 # Pasta raíz do Drive
├── IFCE_ICA_SEUNOME/             # Troque SEUNOME
│   │
│   ├── data/                     # Conjuntos de dados
│   ├── projetos/                 # Projetos
│   │   │
│   │   ├── projeto-0/            # Pasta deste projeto
│   │   └── ...
│   └── ...
└── ...
```

Dentro da pasta `projeto-0/` clique com o botão direito e crie um novo documento Colab. Caso o ícone não apareca, clique em *Conectar mais Apps* e conecte o Colab à sua conta.

![NewColabFile](img/colab-1.png)

#### Ambiente de desenvolvimento

O Colab será o ambiente de desenvolvimento para esta disciplina. Dentre outras vantagens, a ferramenta disponibiliza GPUs para os processamentos de dados que devemos executar durante o decorrer da disciplina.

Na figura abaixo temos dois tipos de células de texto:
 - `+Code`: Onde escrevemos códigos em Python
 - `+Text`: Onde escrevemos textos em Markdown (leia mais na [Seção de Ajuda](#ajuda))

![NewColabFile](img/colab-2.png)

Adicione uma célula de texto e cole o conteúdo abaixo, preenchendo as informações de autor e turma.

```md
# Projeto: 0
 - Autor: XXXX
 - Turma: XXXX

## Objetivo
Iniciar o aprendizado do Jupyter Notebooks no Google Colab.

## Desafio
Criar uma função chamada `perc(a,b)` que:
 - **Recebe**: 2 valores, `a` e `b`
 - **Retorna**: 2 valores, $\frac{a}{a+b}$ e $\frac{b}{a+b}$
```

Adicione uma célula de código e resolva o desafio acima.

## Ajuda
 - [Markdown para Iniciantes](https://produtive.me/guia/markdown-um-guia-para-iniciantes/)

## Contatos
Em caso de dúvidas procure contato via:
 - Google Sala de Aula
 - Email Institucional

[↑ Topo](#inteligência-computacional-aplicada)