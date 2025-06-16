# 1. Introdução


O objetivo deste projeto é prever a duração de uma corrida de táxi em Nova York assim que o passageiro entra no veículo. Essa previsão pode ser utilizada para informar o passageiro sobre o tempo estimado de chegada ao destino, otimizar o planejamento de rotas e melhorar a experiência do usuário. Utilizando dados históricos de corridas, aplicaremos técnicas de aprendizado de máquina para construir modelos capazes de realizar essa estimativa de forma automática e eficiente.

Fonte de dados: https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

O dicionário dos dados fornece a descrição detalhada de cada campo presente no conjunto de dados das corridas de táxi green ou yellow de Nova York. Ele explica o significado, o tipo e possíveis valores de cada coluna, facilitando a compreensão e o uso correto das informações durante a análise e modelagem.  
Acesse o dicionário dos dados aqui: [data_dictionary_trip_records_green](https://data.cityofnewyork.us/api/views/hvrh-b6nb/files/65544d38-ab44-4187-a789-5701b114a754?download=true&filename=data_dictionary_trip_records_green.pdf)


Ambiente de desenvolvimento recomendado: Linux

## 1.1 Introdução

Para facilitar o desenvolvimento, vamos baixar o Visual Studio Code para Linux. Acesse [https://code.visualstudio.com/](https://code.visualstudio.com/) e faça o download do instalador `.deb`. Para instalar via terminal, execute:

```sh
wget https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64 -O code.deb 
sudo apt install ./code.deb
```

## 1.2 Preparação do ambiente


### Passo 1: Baixe e instale a distribuição Anaconda do Python
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda3-Linux-x86_64.sh 
bash miniconda3-Linux-x86_64.sh
```

### Passo 2: Atualize os pacotes existentes

```
sudo apt update
```



### Passo 3: Instale o Docker e o Docker Compose
Siga as instruções aqui:
[install-using-the-repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)  
Configure o repositório apt do Docker.
```sh
# Adicione a chave GPG oficial do Docker:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
# Adicione o repositório ao Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```
Instale os pacotes do Docker.
```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
Para executar o Docker sem `sudo`:

```sh
sudo groupadd docker
sudo usermod -aG docker $USER
```
### Passo 4: Execute o Docker

```sh
docker run hello-world
```

>**Hello from Docker!
This message shows that your installation appears to be working correctly.**


Se você receber o erro `docker: Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Post "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/create": dial unix /var/run/docker.sock: connect: permission denied.`,

**Nota**: Se você receber o erro `It is required that your private key files are NOT accessible by others. This private key will be ignored.`, altere as permissões do arquivo baixado para proteger sua chave privada:

 ```sh
chmod 400 name-of-your-private-key-file.pem
```

### Passo 5: Agora temos que preparar um ambiente isolado do sistema atual.
Para realizar este passo, acesse o diretório [**mlops_eng**](../virtualenv/mlops_eng.md). Siga as instruções contidas nesse arquivo e, após concluir, retorne para continuar com o próximo passo.


## 1.3 Modelo de Maturidade em MLOps

Links: 

* [MLOps Maturity model](https://docs.microsoft.com/en-us/azure/architecture/example-scenario/mlops/mlops-maturity-model)


## Notes

