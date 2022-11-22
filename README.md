# LojaApi

* Ruby version
    2.7.0

* Rails version
    7.0.4

* Dependencias
  - ngrok[https://ngrok.com]
  - postgres[https://www.postgresql.org/download/]

* Configuração
- Para iniciar o projeto, devemos instalar o ruby na versão 2.7.0, apos isso para instalar as dependencias locais execute o comando abaixo, isso irá instalar não só o rails mas tambem todas as dependencias do projeto.
```
  bundle install
```
- Devemos tambem configurar o banco local para utilização, para isso, é necessário antes instalar um banco postgres
- uma vez com o banco configurado as credencias de acesso devem ser as seguintes (é possivel alterar as credenciais de acesso ao banco em config/database.yml)
```
database: loja
username: admin
password: 123456
host: localhost
port: 5432
```

* Inicialização do banco
  Para inicializar o banco, dentro da pasta do projeto devemos executar os seguintes comandos:
```
# comando para criação do database (user do postgres deve estar previament configurado com as permissoes de acesso concedidas)
rake db:create 
# comando para criar as tabelas necessarios para o projeto
rake db:migrate
```

* Inicialização do projeto

Depois que o projeto estiver configurado basta subir a aplicação local com o comando abaixo:
```
rails server
```

Isso irá fazer com que o web server do rails inicialize e fique disponivel na posta localhost:3000

* Inicialização do ngrok
Como o app em react native so consegue se comunicar com a API por meio de requisições https em vez de http, precisamos instalar o ngrok na maquina
Apos instala-lo e configura-lo com o token de inicialização, com o web server rodando basta executar o comando abaixo:
```
ngrok http 3000
```

Isso ira abrir um tunnel de conexão http e irá disponibilizar o endpoint da aplicação para consumo
OBS: o endpoint disponibilizado deve ser colocado no projeto para que ele funcione

Exemplo de resposta do ngrok:
```
Web Interface  http://localhost:4040
Forwarding     https://fbad-2804-431-c7d8-120c-e0dd-539a-2df9-922e.sa.ngrok.io -> http://localhost:3000    
```

Copie o conteudo do Forwarding para os arquivos:
src\Products.js:17
src\Products.js:29
src\NewProduct.js:33

* ...

