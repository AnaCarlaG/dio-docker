# 🐳 Estudo: Primeiro Projeto com Docker Compose

Este repositório é um projeto de **estudo prático** para entender os fundamentos do Docker e Docker Compose, criando um ambiente simples com **Apache** que serve uma página **HTML e CSS**.

---

## 📌 Objetivo

Aprender, na prática:

- O que é Docker Compose
- Como criar containers com serviços prontos (Apache)
- Como servir arquivos estáticos (HTML e CSS) usando Docker
- Como mapear volumes e portas entre a máquina local e o container

---

## 📚 O que foi feito

Criamos um projeto básico com:

- Um container com o servidor **Apache HTTP** (`httpd:latest`)
- Um volume que mapeia arquivos locais (HTML/CSS) para o servidor
- Um container acessível via `http://localhost` na porta 80

Tudo isso com um único comando: `docker-compose up`.

---

## 📁 Estrutura do Projeto

```
.
├── docker-compose.yml # Arquivo de configuração do Docker Compose
└── website # Diretório com os arquivos estáticos do site
├── index.html # Página principal
└── style.css # Estilo da página
```
---

## 🔧 Explicando o `docker-compose.yml`

```yaml
version: '3.9'
services:
  apache:
    image: httpd:latest
    container_name: my-apache-app
    ports:
      - '8080:80'
    volumes:
      - ./site:/usr/local/apache2/htdocs
```

| Campo                                         | Explicação                                                                              |
| --------------------------------------------- | --------------------------------------------------------------------------------------- |
| `version: '3.9'`                              | Define a versão do Docker Compose usada                                                 |
| `services`                                    | Define os serviços que serão criados (neste caso, apenas `apache`)                      |
| `image: httpd:latest`                         | Usa a imagem oficial do Apache HTTP Server                                              |
| `container_name: my-apache-app`               | Nome fixo para o container criado                                                       |
| `ports: - '80:80'`                            | Mapeia a porta 80 do container para a 80 da máquina local (acesso via navegador)        |
| `volumes: - ./site:/usr/local/apache2/htdocs` | Mapeia os arquivos locais da pasta `site/` para o diretório padrão de páginas no Apache |


##▶️ Como Rodar o Projeto
- Pré-requisitos
	Docker instalado
	Docker Compose instalado (ou o Docker Desktop com suporte ao docker compose)
	Terminal configurado no Ubuntu, WSL ou sistema Linux/Mac

##Inicie o container com:
```bash
docker-compose up -d
```

##Como Parar e Remover
```bash
docker-compose down
```


