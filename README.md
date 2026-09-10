# 🌿 API de Livros

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-2E7D32?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/FastAPI-REST_API-1B5E20?style=for-the-badge&logo=fastapi&logoColor=white" alt="FastAPI" />
  <img src="https://img.shields.io/badge/MySQL%20%2F%20MariaDB-Database-388E3C?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL / MariaDB" />
  <img src="https://img.shields.io/badge/Status-Acadêmico-43A047?style=for-the-badge" alt="Status" />
</p>

> Uma API REST prática e organizada para controlar um catálogo de livros, criada utilizando **Python + FastAPI**.

Este projeto foi desenvolvido com finalidade acadêmica, buscando colocar em prática conhecimentos de back-end. Durante sua construção, são trabalhados conceitos como **APIs REST, métodos HTTP, operações CRUD, validação de informações, integração com banco de dados e documentação automática dos endpoints**.

Para armazenar os dados, a aplicação utiliza **MySQL/MariaDB**. A comunicação com o banco é feita por meio do **SQLAlchemy**, enquanto o **Pydantic** realiza a validação dos dados e o **PyMySQL** funciona como driver de conexão.

---

## 🍃 Funcionalidades

> 🟩 **Objetivo:** disponibilizar uma API simples, educativa e fácil de utilizar nos testes.

A API reúne as principais funções necessárias para gerenciar os livros cadastrados:

* 🔎 Visualizar todos os livros;
* 🔍 Procurar um livro específico usando seu ID;
* ➕ Adicionar novos livros;
* ✏️ Modificar informações de livros já cadastrados;
* 🗑️ Remover livros;
* ❤️ Conferir se a API está funcionando e se existe conexão com o banco.

As operações seguem o modelo tradicional de **CRUD**:

| Operação | Método HTTP | Função                |
| -------- | ----------- | --------------------- |
| Create   | `POST`      | Criar um registro     |
| Read     | `GET`       | Consultar registros   |
| Update   | `PUT`       | Atualizar um registro |
| Delete   | `DELETE`    | Excluir um registro   |

---

## 🎯 Objetivos do projeto

Ao longo do desenvolvimento, são colocados em prática os seguintes conhecimentos:

* Construção de APIs REST;
* Desenvolvimento de endpoints utilizando FastAPI;
* Aplicação dos métodos HTTP;
* Criação das operações CRUD;
* Comunicação entre Python e um banco de dados relacional;
* Uso de ORM através do SQLAlchemy;
* Validação das informações com Pydantic;
* Configuração usando variáveis de ambiente;
* Aplicação dos códigos de status HTTP;
* Geração de documentação automática com Swagger UI;
* Estruturação modular de aplicações de back-end.

---

# 🟢 Tecnologias utilizadas

### Python

É a linguagem principal utilizada para desenvolver a aplicação.

### FastAPI

Framework escolhido para criar e organizar os endpoints REST da API.

Além de facilitar a criação dos endpoints, o FastAPI também oferece recursos integrados para validar dados e gerar automaticamente a documentação da aplicação.

### SQLAlchemy

ORM utilizado para facilitar e organizar a comunicação entre o código Python e o banco de dados.

### Pydantic

Responsável por organizar e verificar os dados recebidos e enviados pela API.

### PyMySQL

Driver utilizado para permitir que o SQLAlchemy estabeleça comunicação com o MySQL/MariaDB.

### Uvicorn

Servidor ASGI utilizado para iniciar e executar a aplicação FastAPI durante o desenvolvimento.

### MySQL / MariaDB

Banco de dados relacional utilizado para guardar as informações dos livros do catálogo.

---

# 🌱 Estrutura do projeto

```text
api-livros/
│
├── app/
│   ├── __init__.py
│   ├── database.py
│   └── main.py
│
├── database/
│   └── biblioteca_db.sql
│
├── .gitignore
├── README.md
└── requirements.txt

```

### 📁 `app/`

Pasta que reúne os arquivos principais utilizados para executar a aplicação.

#### `main.py`

É o arquivo central da API.

Nele ocorre a inicialização do FastAPI e também são definidos os endpoints que poderão ser utilizados.

#### `database.py`

Arquivo responsável por configurar e estabelecer a conexão com o banco de dados através do SQLAlchemy.

As informações de acesso ao banco são carregadas por meio de variáveis de ambiente.

### 📁 `database/`

Diretório destinado aos arquivos relacionados à configuração e estrutura do banco de dados.

#### `biblioteca_db.sql`

Arquivo SQL utilizado para montar a estrutura inicial do banco de dados.

O banco utilizado pela aplicação é:

```text
biblioteca_db

```

### 📄 `requirements.txt`

Arquivo que reúne todas as bibliotecas e dependências necessárias para colocar o projeto em funcionamento.

---

# 🔗 Endpoints

## 📋 Resumo

| Método   | Endpoint       | Descrição                                  |
| -------- | -------------- | ------------------------------------------ |
| `GET`    | `/livros`      | Lista todos os livros                      |
| `GET`    | `/livros/{id}` | Busca um livro pelo ID                     |
| `POST`   | `/livros`      | Cadastra um novo livro                     |
| `PUT`    | `/livros/{id}` | Atualiza um livro                          |
| `DELETE` | `/livros/{id}` | Exclui um livro                            |
| `GET`    | `/health`      | Verifica o funcionamento da API e do banco |

---

## 🔎 Listar livros

```http
GET /livros

```

Essa rota retorna a lista contendo todos os livros que estão cadastrados.

### Exemplo de resposta

```json
[
  {
    "id": 1,
    "titulo": "Dom Casmurro",
    "autor": "Machado de Assis",
    "ano_publicacao": 1899
  },
  {
    "id": 2,
    "titulo": "O Hobbit",
    "autor": "J. R. R. Tolkien",
    "ano_publicacao": 1937
  }
]

```

---

## 🔍 Buscar livro por ID

```http
GET /livros/{id}

```

Essa opção permite encontrar um livro específico informando seu ID.

Exemplo:

```http
GET /livros/1

```

### Resposta

```json
{
  "id": 1,
  "titulo": "Dom Casmurro",
  "autor": "Machado de Assis",
  "ano_publicacao": 1899
}

```

Se o ID informado não corresponder a nenhum livro cadastrado, a API retorna:

```http
404 Not Found

```

---

## ➕ Cadastrar livro

```http
POST /livros

```

Essa requisição é utilizada para inserir um novo livro no catálogo.

### Corpo da requisição

```json
{
  "titulo": "O Pequeno Príncipe",
  "autor": "Antoine de Saint-Exupéry",
  "ano_publicacao": 1943
}

```

### Exemplo de resposta

```json
{
  "id": 3,
  "titulo": "O Pequeno Príncipe",
  "autor": "Antoine de Saint-Exupéry",
  "ano_publicacao": 1943
}

```

Quando o cadastro é concluído corretamente, a API pode responder com:

```http
201 Created

```

---

## ✏️ Atualizar livro

```http
PUT /livros/{id}

```

Essa rota permite alterar as informações de um livro que já existe no banco.

Exemplo:

```http
PUT /livros/3

```

### Corpo da requisição

```json
{
  "titulo": "Harry Potter e a Pedra Filosofal",
  "autor": "J. K. Rowling",
  "ano_publicacao": 1997
}

```

A API utiliza o ID recebido para localizar o registro e, depois disso, modifica as informações correspondentes.

---

## 🗑️ Excluir livro

```http
DELETE /livros/{id}

```

Essa operação serve para retirar um livro do catálogo.

Exemplo:

```http
DELETE /livros/3

```

Quando a exclusão acontece corretamente, a API pode devolver:

```http
204 No Content

```

---

# 💚 Health Check

A aplicação possui uma rota específica para conferir se a API está funcionando normalmente e se a conexão com o banco de dados está disponível.

```http
GET /health

```

### Resposta esperada

```json
{
  "status": "ok",
  "database": "connected"
}

```

Essa rota é útil para verificar rapidamente se existem problemas relacionados ao funcionamento da aplicação ou à conexão com o banco.

---

# ✅ Códigos HTTP

| Código | Status                | Utilização                       |
| ------ | --------------------- | -------------------------------- |
| `200`  | OK                    | Requisição realizada com sucesso |
| `201`  | Created               | Registro criado com sucesso      |
| `204`  | No Content            | Registro excluído com sucesso    |
| `400`  | Bad Request           | Requisição inválida              |
| `404`  | Not Found             | Recurso não encontrado           |
| `422`  | Unprocessable Entity  | Erro na validação dos dados      |
| `500`  | Internal Server Error | Erro interno da aplicação        |

---

# 🌿 Banco de dados

O banco utilizado neste projeto é:

```text
biblioteca_db

```

A comunicação entre a API e o banco segue esta organização:

```text
FastAPI
   │
   ▼
SQLAlchemy
   │
   ▼
PyMySQL
   │
   ▼
MySQL / MariaDB
   │
   ▼
biblioteca_db

```

As informações de acesso ao banco não devem ficar escritas diretamente dentro do código da aplicação.

Por esse motivo, o projeto utiliza variáveis de ambiente armazenadas em um arquivo `.env`.

### Exemplo

```env
DB_USER=root
DB_PASSWORD=sua_senha
DB_HOST=localhost
DB_PORT=3306
DB_NAME=biblioteca_db

```

> ⚠️ **Importante:** caso o `.env` contenha senhas, tokens ou outros dados privados, ele não deve ser enviado para o GitHub.

Para evitar isso, coloque o arquivo no `.gitignore`:

```gitignore
.env

```

---

# ⚙️ Instalação e configuração

## Pré-requisitos

Antes de começar a executar o projeto, é necessário possuir:

* Python 3.10 ou superior;
* MySQL ou MariaDB;
* Git;
* Pip.

---

## 1. Clone o repositório

Depois, acesse o diretório do projeto:

```bash
cd api-livros

```

---

## 2. Crie um ambiente virtual

### Windows

```bash
python -m venv venv

```

Para ativar o ambiente virtual:

```bash
venv\Scripts\activate

```

### Linux / macOS

```bash
python3 -m venv venv

```

Depois, faça a ativação:

```bash
source venv/bin/activate

```

---

## 3. Instale as dependências

```bash
pip install -r requirements.txt

```

---

## 4. Configure o banco de dados

Verifique primeiro se o MySQL ou MariaDB está funcionando.

Depois, utilize o arquivo:

```text
database/biblioteca_db.sql

```

Esse script será usado para criar a estrutura inicial necessária para o banco.

Em seguida, informe as credenciais no arquivo `.env`:

```env
DB_USER=root
DB_PASSWORD=sua_senha
DB_HOST=localhost
DB_PORT=3306
DB_NAME=biblioteca_db

```

---

# ▶️ Executando a aplicação

Depois de ativar o ambiente virtual, execute o seguinte comando:

```bash
uvicorn app.main:app --reload

```

Por padrão, a API poderá ser acessada em:

```text
http://127.0.0.1:8000

```

O argumento:

```text
--reload

```

faz o servidor reiniciar automaticamente quando alguma alteração for feita no código enquanto o projeto estiver sendo desenvolvido.

---

# 📗 Documentação da API

O FastAPI cria automaticamente uma documentação para facilitar a consulta e os testes da aplicação.

## Swagger UI

Com o servidor ligado, abra:

```text
http://127.0.0.1:8000/docs

```

No Swagger é possível:

* Conferir os endpoints existentes;
* Verificar os parâmetros;
* Consultar os modelos de dados;
* Fazer requisições;
* Conferir as respostas;
* Testar os códigos HTTP.

## ReDoc

Existe também uma segunda opção de documentação:

```text
http://127.0.0.1:8000/redoc

```

---

# 🧪 Testando os endpoints

Uma maneira prática de verificar o funcionamento dos endpoints é utilizando o Swagger UI.

Acesse:

```text
http://127.0.0.1:8000/docs

```

Escolha um endpoint e pressione **Try it out**.

Por exemplo, para adicionar um livro:

```http
POST /livros

```

Use os seguintes dados:

```json
{
  "titulo": "Moby Dick",
  "autor": "Herman Melville",
  "ano_publicacao": 1851
}

```

Depois, consulte os livros cadastrados através de:

```http
GET /livros

```

Também é possível verificar todo o processo CRUD seguindo esta ordem:

```text
POST → Criar
GET → Consultar
PUT → Atualizar
DELETE → Excluir

```

---

# 🔄 Fluxo da aplicação

De forma simplificada, o funcionamento pode ser representado assim:

```text
               CLIENTE
                  │
                  ▼
               FastAPI
                  │
           ┌───────┴───────┐
           │               │
           ▼               ▼
       Validação         Endpoints
        Pydantic           HTTP
           │               │
           └───────┬───────┘
                   │
                   ▼
              SQLAlchemy
                   │
                   ▼
                PyMySQL
                   │
                   ▼
           MySQL / MariaDB
                   │
                   ▼
             biblioteca_db

```

O processo começa quando o cliente faz uma requisição HTTP para algum dos endpoints disponíveis.

O FastAPI recebe essa solicitação e encaminha o processamento. Quando existem informações enviadas no corpo da requisição, o Pydantic verifica e valida esses dados antes que a lógica seja executada.

Nas operações que precisam consultar ou salvar informações, o SQLAlchemy e o PyMySQL realizam a comunicação com o banco de dados.

Depois que o processamento termina, a API envia ao cliente uma resposta HTTP correspondente ao resultado da operação.

---

# 🛡️ Boas práticas

### Variáveis de ambiente

Informações importantes, como credenciais e configurações sensíveis, ficam separadas do código principal da aplicação.

### Validação de dados

Antes de serem utilizados, os dados enviados para a API passam por uma validação.

### Status HTTP

Os códigos HTTP são escolhidos de acordo com o resultado de cada operação realizada.

### Separação de responsabilidades

Cada arquivo da aplicação possui uma função específica, deixando a estrutura do projeto mais organizada.

### Documentação

Os endpoints podem ser consultados e utilizados para testes por meio da documentação automática fornecida pelo FastAPI.

---

# 🚀 Próximos passos

Algumas melhorias que podem ser adicionadas futuramente ao projeto são:

* Implementação completa do CRUD;
* Criação de modelos com SQLAlchemy;
* Desenvolvimento de schemas utilizando Pydantic;
* Tratamento geral de erros;
* Paginação;
* Busca por título;
* Busca por autor;
* Filtros pelo ano de publicação;
* Organização dos resultados;
* Autenticação;
* Gerenciamento de usuários;
* Testes automatizados;
* Docker;
* Deploy;
* Monitoramento;
* Versionamento da API (`/api/v1`);
* Ampliação da documentação.

---

# 🎓 Contexto acadêmico

Este projeto foi criado principalmente para **estudo e aprendizagem**.

A ideia é pegar os conceitos teóricos de back-end e aplicá-los em uma aplicação funcional, ajudando a entender o caminho completo percorrido por uma API:

```text
Cliente
   ↓
Requisição HTTP
   ↓
FastAPI
   ↓
Validação
   ↓
Regra da aplicação
   ↓
Banco de dados
   ↓
Resposta HTTP

```

Entre os principais conteúdos praticados estão:

* APIs REST;
* HTTP;
* CRUD;
* Python;
* FastAPI;
* SQL;
* Bancos relacionais;
* SQLAlchemy;
* Pydantic;
* Variáveis de ambiente;
* Documentação de APIs;
* Arquitetura back-end.

---

---

# 📄 Licença

Este projeto foi criado com finalidade educacional.

Caso futuramente seja adotada uma licença específica para o projeto, esta parte poderá ser modificada para apresentar os respectivos termos.

---

## 🌟 Considerações finais

A **API de Livros** serve como uma aplicação prática para aprender os principais conceitos utilizados atualmente no desenvolvimento de sistemas back-end.

Utilizando **Python, FastAPI, SQLAlchemy e MySQL/MariaDB**, o projeto apresenta todas as etapas básicas de uma requisição, começando pelo recebimento dos dados via HTTP, passando pela validação e processamento, acessando o banco de dados e finalmente retornando uma resposta.

A estrutura criada também pode ser expandida posteriormente com recursos como autenticação, testes automatizados, paginação, filtros, Docker e deploy.

> 🌱 **Estudar APIs ajuda a compreender como diferentes sistemas podem trocar informações e transformar dados em recursos úteis.**

<p align="center"><strong>🌿 Criado para aprender, experimentar e continuar evoluindo.</strong></p>
