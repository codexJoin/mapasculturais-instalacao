[Voltar para o sumário](https://github.com/edsongs/instal-mapas)

# Instalação Mapas Culturais - Instalação Docker Ubuntu 18.04 e 20.04

  ## 1- Instalando o Docker
  
  #### Atualize os repositórios de referência de sua máquina:
  
  ```
  ubuntu@server$ sudo apt-get update -y
  ```
  ```
  ubuntu@server$ sudo apt-get upgrade -y
  ````
  
  #### Instalação de pacotes que serão utilizados:
  
  ```
  ubuntu@server$ sudo apt-get install curl git -y
  ```
  
  #### Em seguida, instale alguns pacotes de pré-requisitos que permitem que o apt utilize pacotes via HTTPS:
  
  ```
  ubuntu@server$ sudo apt-get install apt-transport-https ca-certificates curl software-properties-common -y
  ```
  
  
  #### Então adicione a chave GPG para o repositório oficial do Docker em seu sistema:
  
  ```
  ubuntu@server$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
  ```
  #### Adicione o repositório do Docker às fontes do APT:
  
  ```
  ubuntu@server$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable" -y
  ```
  
  #### Atualize novamente os repositórios de referência de sua máquina:
  
  ```
  ubuntu@server$ sudo apt-get update -y
  ```
  
  #### Certifique-se de que você irá instalar a partir do repositório do Docker em vez do repositório padrão do Ubuntu:
  
  ```
  ubuntu@server$ sudo apt-cache policy docker-ce
  ```
  
  #### Finalmente, instale o Docker:
  
  ```
  ubuntu@server$ sudo apt-get install docker-ce -y
  ```
  
  #### Iremos habilitar o serviço e criar o link:
  
  ```
  ubuntu@server$ sudo systemctl start docker
  ubuntu@server$ sudo systemctl enable docker
  ```
  
  #### O Docker agora deve ser instalado, o daemon iniciado e o processo ativado para iniciar na inicialização. Verifique se ele está sendo executado:
  
  ```
  ubuntu@server$ docker --version
  output: Docker version 19.03.12, build 48a66213fe
  ```
  
  #### Conferindo a versão do docker instalado:
  
  ```
  ubuntu@server$ sudo systemctl status docker
  ```
  
  #### A saída deve ser semelhante à seguinte, mostrando que o serviço está ativo e executando:
  
  ```
   docker.service - Docker Application Container Engine
   Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
   Active: active (running) since Tue 2020-07-28 22:35:27 UTC; 36s ago
      Docs: https://docs.docker.com
      Main PID: 5833 (dockerd)
      Tasks: 8
   CGroup: /system.slice/docker.service
           └─5833 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
  ```
  
  _Para mais detalhes sobre docker [clique aqui](https://www.digitalocean.com/community/tutorials/como-instalar-e-usar-o-docker-no-ubuntu-18-04-pt) e confira as informações adicionais sobre o assunto_
  
  ## 2- Trabalhando com Imagens Docker:
  
  
  
  _Os containers Docker são construídos a partir de imagens Docker. Por padrão, o Docker extrai essas imagens do Docker Hub, um registro Docker mantido pela Docker, a empresa por trás do projeto Docker. Qualquer pessoa pode hospedar suas imagens do Docker no Docker Hub, portanto, a maioria dos aplicativos e distribuições do Linux que você precisa terá imagens hospedadas lá._

  #### Para verificar se você pode acessar e baixar imagens do Docker Hub, digite:
  
  
  ```
  ubuntu@server$ sudo docker run hello-world
  ```
  
  #### A saída irá indicar que o Docker está funcionando corretamente:
  
  ```
  Unable to find image 'hello-world:latest' locally
  latest: Pulling from library/hello-world
  0e03bdcc26d7: Pull complete 
  Digest: sha256:49a1c8800c94df04e9658809b006fd8a686cab8028d33cfba2cc049724254202
  Status: Downloaded newer image for hello-world:latest

  Hello from Docker!
  This message shows that your installation appears to be working correctly.
  ...
  ```
  
  #### Instalando Docker composer:
  
  ```
  ubuntu@server$  sudo curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  ```
  
  #### Atribuindo a permissão necesária:
  
  ```
  ubuntu@server$  sudo chmod +x /usr/local/bin/docker-compose
  ```
  
  #### Verificado se foi instalado corretamente:
  
  ```
  ubuntu@server$ sudo docker-compose -version
  output: docker-compose version 1.26.2, build eefe0d31
  ```
  #### Instalando o unzip e megatools para baixar e extrair o repositório.
  ```
  ubuntu@server$ sudo apt-get install unzip
  ubuntu@server$ sudo apt-get install megatools
  ```
  
  
  
  ### Baixando o repositórino
  ```
  ubuntu@server$ sudo cd 
  ubuntu@server$ sudo megadl 'https://mega.nz/#!IIs0HQaS!7HyLhAvh8gSaKO6-yUrMZ34XsMPZvyXwGv3IvZnGnk8'
  ubuntu@server$ cd mapasculturais-aldirblanc
  ```
  
  ### Deploy ambiete de produção:
  
  #### Iniciando o script de configuração e inicialização
  
  ```
  ubuntu@server$ sudo ./gerar_crt.sh
  ```
  #### Após iniciar, o script ira perguntar o dominio de destino, digite o dominio sem https ou http. exemplo www.google.com ou google.com e aperte enter.
  #### Logo em seguida, o script vai perguntar o e-mail, digite um e-mail válido e aperte enter, pois é com ele que o script vai registrar o certificado ssl
  #### Após isto, o script ira perguntar se você deseja substituir o certificado x para dominio, digite Y, ou N caso não queira gerar um novo e aperte enter
  #### Aguarde a execução do script.
  #### Após a execução finalizar, você já pode acessar o dominio.
  
  _A partir deste momento você deverá ser capaz de acessar o Mapas com o Plugin para a Lei Aldir Blanc_
 
