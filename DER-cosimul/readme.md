# Descrição da Imagem

Nome desta imagem: DERCosimul


## Qual sua imagem base?

lucassmelo/python-base-image:0.2 (ubuntu 24.04)

## O que esta imagem faz?

- utiliza a imagem lucassmelo/python-base-image:0.2 como base, padrao dos projetos que utilizam Python no GREI.
- Configura o diretorio de trabalho /app.
- Clona o respositorio do projeto para a pasta /app do container.
- Cria o ambiente virtual anaconda `mosaik-env` com python 3.8.
- Inicializa o anaconda no terminal e executa comando de instalacao dos prerrequisitos do projeto.
- Configura o ambiente virtual anaconda `mosaik-env` para ser utilizado como ambiente padrao do container.
- Libera a porta 8000 para ser exposta pelo container.
- Configura o comando `/bin/bash` como padrao na inicializacao do container.

## Qual a aplicação desta imagem?

Esta imagem tem como objetivo criar um ambiente de desenvolvimento preparado para executar as simulações do projeto *DERCosimul*.


## Como fazer para construir essa imagem e lançar um container a partir dela?

Os seguintes comandos devem ser executados na pasta em que o Dockerfile desejado estiver:

```sh
docker image build --build-arg GITHUB_TOKEN=$GITHUB_TOKEN -t lucassmelo/der-cosimul:0.1 .
```
O nome da imagem será lucassmelo/der-cosimul e sua versão é a 0.1.

Para saber o que é um github token, acesse este [link]()

Para criar o container e executá-lo logo em seguida, o comando a seguir deverá ser executado:

```sh
docker container run -it --name cosimul1 -p 8000:8000 lucassmelo/der-cosimul:0.1 
```

O nome do container é cosimul1

Para separar as duas etapas, criação e execução, os dois comandos a seguir precisarão ser executados:

Para criar o container:
```sh
docker container create --name cosimul1 -p 8000:8000 lucassmelo/der-cosimul:0.1
```

Para executar o container:
```sh
docker start -ai cosimul1
```

Para adiconar volumes e expor portas no container, utilizar a seguinte linha de comando:

```sh
docker run -it --name cosimul1 -v <caminho_host>:<caminho_container> -p <porta_host>:<porta_container> DERCosimul:0.1
```

Caso queira executar o container e mapear um volume local para persistência, basta executar o comando:

```sh
docker run -it --rm -v $(pwd):/app mosaik-dev
```

