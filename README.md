# IT_Talent_Hackathon1

Nextcloud com banco de dados Postgres
Este exemplo define uma das configurações base para Nextcloud. Mais detalhes sobre como Personalize ainda mais a instalação e o arquivo de composição pode ser encontrado na página da imagem oficial.

Estrutura do projeto:

.
├── compose.yaml
└── README.md
compor.yaml

services:
  nc:
    image: nextcloud:apache
    ports:
      - 80:80
    ...
  db:
    image: postgres:alpine
    ...
Ao implantar essa configuração, o docker compose mapeia a porta 80 do contêiner nextcloud para porta 80 do host, conforme especificado no arquivo de composição.

Implantar com a composição do docker
$ docker compose up -d
Creating network "nextcloud-postgres_default" with the default driver
Creating volume "nextcloud-postgres_nc_data" with default driver
Pulling nc (nextcloud:apache)...
....
....
Status: Downloaded newer image for postgres:alpine
Creating nextcloud-postgres_nc_1 ... done
Creating nextcloud-postgres_db_1 ... done
Resultado esperado
Verifique se os contêineres estão em execução e o mapeamento da porta:

$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
9884a9cc0144        postgres:alpine     "docker-entrypoint.s…"   12 minutes ago      Up 12 minutes       5432/tcp             nextcloud-postgres_db_1
bae385bee48b        nextcloud:apache    "/entrypoint.sh apac…"   12 minutes ago      Up 12 minutes       0.0.0.0:80->80/tcp   nextcloud-postgres_nc_1
Navegue até no navegador da Web para acessar o Serviço Nextcloud.http://localhost:80

página

Pare e remova os recipientes

$ docker compose down

 
