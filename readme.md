# Desafio DevOps
# Instalação e Configuração de Icecast com Docker e Nginx

## Icecast

<p>O Icecast foi instalado usando Dockerfile, que esta disponivél dentro do path <b>icecast-docker</b>, assim como o arquivo de configuração padrão do icecast, adicionando o /stream , também disponibilizado dentro do path.</p>

<p>Feito o build da imagem :
        
        docker build -t icecast-custom .

Criando o container :

        docker run -dit --name icecast-server -p 8000:8000 icecast-custom

</p>

## Nginx

<p>Também instalado usando Dockerfile, no path <b>nginx-proxy</b>, assim como o arquivo de configuração!</p>

<p>Feito o build :

        docker build -t nginx-custom .

Criando o container :

        docker run -dit --name nginx-proxy -p 80:80 --link icecast-server:icecast-server -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro nginx:latest


## Deploy

<p>Optei por fazer o deploy dos containers em instancias EC2 na AWS, onde nela instalei o docker :

        curl -fsSL https://get.docker.com | bash

Configurei o security-group permitindo acesso as portas :

- 80
- 8000

</p>

## BUTT

<p>Em minha máquina local, fiz a instalação do butt :

        apt install butt -y

E fiz as configuraões de conexão :

- main > add
- name : icecast-aws
- type : icecast
- address: ip da ec2:8000
- password : o mesmo do butt do usuario sorce

em Stream :

- Defini para reproduzi as musicas a partir do Rhytnimbox

Salvo as configurações.