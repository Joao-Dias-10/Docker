# Guia Rápido Docker

## Instalação

- Baixe e instale o Docker Desktop:
  - [Instruções oficiais para Windows](https://docs.docker.com/desktop/install/windows-install/)

## Criando e Gerenciando Containers

### Baixando Imagens

- Baixe a imagem desejada no [Docker Hub](https://hub.docker.com/):

```sh
  docker pull postgres      # Baixa a última versão do Postgres
````

* Ou crie um container diretamente a partir da imagem:

  ```sh
  docker run postgres
  ```

### Criando um Container com Nome

```sh
docker run --name meu_ubuntu ubuntu
```

### Definindo Variáveis de Ambiente

```sh
docker run -d -e POSTGRES_PASSWORD=password postgres
```

### Baixando Imagem de Versão Específica

```sh
docker run -d -e POSTGRES_PASSWORD=password postgres:bullseye
```

## Principais Comandos Docker

### Listar Containers

```sh
docker ps           # Lista containers em execução
docker ps -a        # Lista todos os containers (ativos e parados)
docker ps -s        # Mostra também o tamanho dos containers
```

### Listar Imagens

```sh
docker images       # Lista todas as imagens disponíveis localmente
```

### Executar, Renomear e Remover Containers

```sh
docker run -d -e POSTGRES_PASSWORD=password --name bullseye_container postgres:bullseye
docker rename <id_container> NOVO_NOME

docker rm <id_container>                  # Remove container parado
docker rm -f <id_container>               # Força remoção de container em execução
docker rm $(docker ps --filter status=exited -q)  # Remove todos containers parados
```

### Remover Imagens

```sh
docker rmi <id_imagem>                    # Remove imagem (se não estiver em uso)
docker rmi -f <id_imagem>                 # Força remoção da imagem
```

### Pausar, Reiniciar e Iniciar Containers

```sh
docker stop <id_container>
docker start <id_container>
docker restart <id_container>
```

### Executar Comando Dentro de Container

```sh
docker exec -it <id_container> sh    # Acesso ao terminal do container
```

### Visualizar Logs

```sh
docker logs -f <id_container>           # Mostra logs em tempo real
docker logs --tail 10 <id_container>    # Mostra os 10 últimos logs
docker logs -f --since=1s <id_container> # Logs desde 1 segundo atrás
```

### Buscar Imagens no Docker Hub

```sh
docker search postgres
```

### Informações Gerais

```sh
docker info
```

## Salvando e Importando Imagens

### Salvar Imagem em Arquivo Compactado

```sh
docker save redis:latest | gzip > D:\myredis.tar.gz
```

### Carregar Imagem a partir de Arquivo

```sh
docker load < caminho/do/arquivo.tar.gz
```

## Monitoramento de Containers

```sh
docker stats      # Exibe estatísticas em tempo real (CPU, Memória, etc.)
```

## Referências

* [Documentação Oficial Docker](https://docs.docker.com/)
* [Comandos Docker CLI](https://docs.docker.com/engine/reference/commandline/exec/)


