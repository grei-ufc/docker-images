# Descrição da Imagem

Nome desta imagem: DERCosimul


## Qual sua imagem base?

ubuntu:24.04

## O que esta imagem faz?

- Atualiza os repositórios do ubuntu;
- Instala algumas aplicações necessárias como: wget, bzip2, build-essential e git;
- Faz download do instalador da versão mais atual do *Miniconda*;
- Faz a instalação da distribuição Python Anaconda a partir do instalador Miniconda;
- Apaga os arquivos do instalador Miniconda; e 
- Cria um ambiente virtual com python 3.10 de nome mosaik-env e instala a versão mais atual do mosaik nele.
- Ativa o ambiente virtual mosaik-env como padrão para o container.
- Expõe a porta 8000 do container.

## Qual a aplicação desta imagem?

Esta imagem tem como objetivo criar um ambiente de desenvolvimento preparado para executar as simulações do projeto *DERCosimul*.


## Como fazer para construir essa imagem e lançar um container a partir dela?

Os seguintes comandos devem ser executados na pasta em que o Dockerfile desejado estiver:

```sh
docker image build -t DERCosimul:0.1 . # o nome da imagem será DERCosimul e sua versão é 0.1
```

Para criar o container e executá-lo logo em seguida, o comando a seguir deverá ser executado:

```sh
docker run -it --name dercosimul-1 DERCosimul:0.1
```

Para separar as duas etapas, criação e execução, os dois comandos a seguir precisarão ser executados:

Para criar o container:
```sh
docker create --name dercosimul-1 DERCosimul:0.1
```

Para executar o container:
```sh
docker start -ai dercosimul-1
```

Para adiconar volumes e expor portas no container, utilizar a seguinte linha de comando:

```sh
docker run -it --name dercosimul-1 -v <caminho_host>:<caminho_container> -p <porta_host>:<porta_container> DERCosimul:0.1
```

Caso queira executar o container e mapear um volume local para persistência, basta executar o comando:

```sh
docker run -it --rm -v $(pwd):/app mosaik-dev
```

