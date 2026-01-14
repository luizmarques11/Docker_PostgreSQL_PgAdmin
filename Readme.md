# Docker_PostgreSQL_PgAdmin

Este repositório fornece uma configuração completa e pronta para uso de **PostgreSQL** e **PgAdmin 4** utilizando **Docker Compose**.

O objetivo é agilizar a criação de um ambiente de desenvolvimento ou estudos, permitindo subir um banco de dados relacional robusto e sua interface de administração web com um único comando, sem a necessidade de instalar nada localmente além do Docker.

---

## 🚀 Tecnologias

- **[Docker](https://www.docker.com/)**
- **[Docker Compose](https://docs.docker.com/compose/)**
- **[PostgreSQL](https://www.postgresql.org/)** (Banco de Dados)
- **[PgAdmin 4](https://www.pgadmin.org/)** (Interface de Gerenciamento)

---

## 📋 Pré-requisitos

Certifique-se de ter instalado em sua máquina:

- [Docker Desktop](https://docs.docker.com/desktop/) (Windows/Mac) ou Docker Engine + Docker Compose (Linux).

---

## ⚙️ Como Executar

Siga os passos abaixo para configurar e rodar o projeto.

### 1. Clonar o repositório

```bash
git clone https://github.com/luizmarques11/Docker_PostgreSQL_PgAdmin.git
cd Docker_PostgreSQL_PgAdmin

```

### 2. Configurar Variáveis de Ambiente

Este projeto utiliza variáveis de ambiente para definir credenciais de forma segura. Existe um arquivo modelo chamado `compose.env.example`.

Crie um arquivo `.env` na raiz do projeto copiando o modelo:

```bash
cp compose.env.example .env

```

> **Atenção:** Abra o arquivo `.env` recém-criado e defina suas próprias senhas, usuários e banco de dados.

### 3. Subir os Containers

Execute o comando abaixo para baixar as imagens e iniciar os serviços em segundo plano (detached mode):

```bash
docker compose up -d

```

---

## 🔌 Acessando os Serviços

### 🐘 PostgreSQL

O banco estará rodando e mapeado para a sua máquina local.

* **Host:** `localhost`
* **Porta:** `5432`
* **Usuário:** (Definido no `.env`)
* **Senha:** (Definida no `.env`)

### 🚀 PgAdmin 4

A interface web estará acessível pelo navegador.

* **URL:** [http://localhost:8085](http://localhost:8085)
* **Email de Login:** (Definido no `.env` em `PGADMIN_DEFAULT_EMAIL`)
* **Senha:** (Definida no `.env` em `PGADMIN_DEFAULT_PASSWORD`)

---

## 🔗 Como conectar o PgAdmin ao Banco (Passo Importante)

Como o PgAdmin está rodando dentro de um container Docker, ele **não** consegue acessar o banco usando `localhost`. Você deve usar o nome do serviço na rede interna do Docker.

1. Acesse o PgAdmin ([http://localhost:8085](http://localhost:8085)) e faça login.
2. Clique em **Add New Server**.
3. Na aba **General**, dê um nome (ex: `Meu Banco Docker`).
4. Na aba **Connection**, preencha exatamente assim:
* **Host name/address:** `postgres`
> *Nota: `postgres` é o nome do serviço definido dentro do arquivo `compose.yml`.*


* **Port:** `5432`
* **Maintenance database:** `postgres`
* **Username:** Seu usuário (definida no `.env`).
* **Password:** Sua senha (definida no `.env`).


5. Clique em **Save**.

---

## 📂 Estrutura do Projeto

```
Docker_PostgreSQL_PgAdmin/
├── compose.yml           # Orquestração dos containers
├── compose.env.example   # Modelo de variáveis de ambiente
├── .gitignore            # Arquivos ignorados pelo Git
└── Readme.md             # Documentação

```

---

## 🛠️ Comandos Úteis

**Verificar status dos containers:**

```bash
docker compose ps

```

**Verificar logs (erros ou inicialização):**

```bash
docker compose logs -f

```

**Parar os serviços:**

```bash
docker compose stop

```

**Parar e remover tudo (containers e redes):**

```bash
docker compose down

```

---

## 📝 Autor

Feito por [Luiz Marques](https://github.com/luizmarques11).



