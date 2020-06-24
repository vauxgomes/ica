# Projeto: 0

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
Iniciar o aprendizado do pandas e do jupyter notebooks no Google Colab.

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