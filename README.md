# basic-schema-docker-django-postgres-node-nginx
Estrutura básica Dockerizada PostgreSQL + Django + Node + Nginx

Este schema fornece uma estrutura básica de containers frontend e backend. Utilizando Docker + Docker Compose. 
Este schema cria uma estrutura básica com Postgres, Django, Node e Nginx. 

Contem também um Makefile com comandos básicos .

### Requisitos

  * Docker
  * Docker Compose
  
### Makefile
  Arquivo contendo comandos básicos para execução nos containers Django e Node
    
  **make set_env_development**
   
    Configura gerendo um arquivo docker-compose.override.yml com o script para subir os containers 
    em ambiente de desenvolvimento
    
    
  **make set_env_production**
   
    Configura gerendo um arquivo docker-compose.override.yml com o script para subir os containers 
    em ambiente de produção 
    
  
  **make makemigrations**
   
    Executa o comando ```python manage.py makemigrations``` no container Django

  
  **make migrate**
   
    Executa o comando ```python manage.py migrate``` no container Django
    
    
  **make createsuperuser**
   
    Executa o comando ```python manage.py createsuperuser``` no container Django

  **make startapp app=seu_novo_app**
   
    Executa o comando ```python manage.py startapp seu_novo_app``` no container Django

  **make build-install-modules**
   
    Executa o comando ```npm install``` no container Node
    

  **make build-frontend**
   
    Executa o comando ```npm build``` no container Node
    
### Building das imagens

  1 - Configurando ambiente de desenvolvimento:
  ```shell
     make set_env_development
  ```
  2 - Build das imagens:
  ```shell
     docker-compose build
  ```
### Subindo as imagens

  1 - Subindo as imagens:
   ```shell
       docker-compose up -d
   ```

### Observações

  * O container Django irá subir na porta 0:8000
  * O projeto frontend deverá está no diretório frontend
  * Deverá ser configurado o docker-compose.yml para o frontend ajustando as linhas comentadas de acordo com o seu projeto:
    ``` 
    # command: sh -c "cd /app/frontend/ && npm run serve"
    # ports:
    #   - "8087:8080"
    ```
  * Pacotes python e django deverão ser configurados nos arquivos **production.txt** e **develpment.txt** contidos na pasta **requirements**
    
  * Configuração dos arquivos **default.conf** do **Nginx** estão definidas nos arquivos **develpment.conf** e **production.conf** que ficam no diretório `containers/nginx/conf.d/` 
  
    

