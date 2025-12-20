# Minimal API de Veículos

Este projeto é uma **Minimal API** desenvolvida em **.NET 7** utilizando **C#**, **Swagger** para documentação e **MySQL** como banco de dados.
A API permite o gerenciamento de veículos e administradores com autenticação via **JWT**.
---

## Funcionalidades
- Autenticação de administradores com JWT
- CRUD de veículos (listar, criar, atualizar e excluir)
- Rotas protegidas por autenticação e autorização por perfil (Adm, Editor)
- Documentação interativa com Swagger
- Conexão com banco de dados MySQL via Entity Framework Core
---

## Introdução
Estas instruções permitirão que você obtenha uma cópia do projeto em operação na sua máquina local para fins de desenvolvimento e teste.

### Pré-requisitos
Antes de rodar o projeto, certifique-se de ter instalado: 
- [.NET 9 SDK](https://dotnet.microsoft.com/download/dotnet/9.0) (recomendado) — compatível a partir da versão mínima 7.0
- [MySQL Server](https://dev.mysql.com/downloads/mysql/)
- [MySQL Workbench](https://dev.mysql.com/downloads/workbench/) (opcional, para gerenciar o banco)
- [Visual Studio Code](https://code.visualstudio.com/) ou [Visual Studio](https://visualstudio.microsoft.com/)

## Como rodar o projeto
### Passos
```BASH
# Clone o repositório
git clone https://github.com/moisesjunior45/minimal-api

# Acesse a pasta do projeto
cd minimal-api

# Restaure as dependências
dotnet restore

# Compile e rode a aplicação
dotnet run
```
A aplicação estará disponível em:
```BASH
http://localhost:5134/swagger
```

### Configuração do Banco de Dados

Este projeto utiliza **MySQL** como banco de dados. Você pode usar o servidor MySQL do **XAMPP** ou gerenciar via **MySQL Workbench** (opcional).

1. Crie o banco.
```SQL
CREATE DATABASE minimal_api_veiculos;
```
2. Configure a connection string no arquivo appsettings.json:
```JSON
{
  "ConnectionStrings": {
    "Mysql": "Server=localhost;Database=minimal_api_veiculos;User=root;Password=suasenha;"
  },
  "Jwt": "minimal-api-secret-key-1234567890-abcdef"
}
```

3. Execute as migrations para criar as tabelas:
```BASH
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## Autenticação JWT
- Para acessar endpoints protegidos, faça login em:
```
POST /administradores/login
```
- O retorno será um token JWT que deve ser usado no Swagger ou nos headers das requisições:
```
Authorization: Bearer {seu_token}
```

## Endpoints Principais

### Home
- GET / → Retorna informações básicas da API

### Administradores
- POST /administradores/login → Login e geração de token JWT
- GET /administradores → Lista administradores (Adm)
- POST /administradores → Cria novo administrador (Adm)

### Veículos
- GET /veiculos → Lista veículos
- POST /veiculos → Cria veículo (Adm, Editor)
- PUT /veiculos/{id} → Atualiza veículo (Adm)
- DELETE /veiculos/{id} → Remove veículo (Adm)

## Tecnologias usadas:
* ![.NET 9](https://img.shields.io/badge/.NET%209-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
* ![C#](https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white)
* ![Minimal API](https://img.shields.io/badge/Minimal%20API-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
* ![Swagger / OpenAPI](https://img.shields.io/badge/Swagger%20%2F%20OpenAPI-85EA2D?style=for-the-badge&logo=swagger&logoColor=black)
* ![Entity Framework Core](https://img.shields.io/badge/Entity%20Framework%20Core-512BD4?style=for-the-badge&logo=dotnet&logoColor=white)
* ![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
* ![JWT Authentication](https://img.shields.io/badge/JWT%20Authentication-000000?style=for-the-badge&logo=jsonwebtokens&logoColor=white)

