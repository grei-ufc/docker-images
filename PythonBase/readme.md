# Descrição da Imagem

Nome desta imagem: PythonBase


## Qual sua imagem base?

ubuntu:24.04

## O que esta imagem faz?

- Atualiza os repositórios do ubuntu;
- Instala algumas aplicações necessárias como: wget, bzip2 e git;
- Faz download do instalador da versão mais atual do *Miniconda*;
- Faz a instalação da distribuição Python Anaconda a partir do instalador Miniconda;
- Apaga os arquivos do instalador Miniconda; e 
- Executa o comando `conda --version` para testar a instalação.

## Qual a aplicação desta imagem?

A ideia é de que esta imagem sirva como base para os projetos do grupo que utilizam linguagem de programação Python.


## Como fazer para construir essa imagem e lançar um container a partir dela?

Os seguintes comandos devem ser executados na pasta em que o Dockerfile desejado estiver:

```sh
docker image build -t PythonBase:0.1 . # o nome da imagem será PythonBase e sua versão é 0.1
```

Para criar o container e executá-lo logo em seguida, o comando a seguir deverá ser executado:

```sh
docker run -it --name python-base-1 PythonBase:0.1
```
