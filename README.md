# Minimal API em .NET - Registro de Veículos

Projeto desenvolvido como parte do laboratório prático da DIO (Digital Innovation One) sobre criação de APIs modernas com **Minimal APIs**, **autenticação JWT** e **testes automatizados**.

## Sobre o projeto

O objetivo foi construir uma API REST para gerenciamento e cadastro de veículos e administradores, utilizando a abordagem enxuta de Minimal APIs no .NET.

A aplicação conta com controle de acesso baseado em perfis (Administrador e Editor) utilizando JSON Web Tokens (JWT), documentação interativa via Swagger e uma suíte de testes com MSTest.

## Principais Funcionalidades

- **Autenticação com JWT**: Geração e validação de tokens com regras de permissão por perfil.
- **Gestão de Administradores**: Cadastro, listagem e busca por ID com restrição de acesso apenas para o perfil Administrador.
- **Gestão de Veículos**: CRUD completo (cadastro, listagem paginada, busca, atualização e exclusão).
- **Documentação com Swagger**: Interface interativa configurada com suporte a envio do token Bearer.
- **Testes Automatizados**: Testes de unidade e de integração para validar entidades, serviços e requisições HTTP.

## Tecnologias utilizadas

- C# / .NET 8
- ASP.NET Core (Minimal APIs)
- Entity Framework Core / Pomelo MySQL
- JWT Bearer Authentication
- Swashbuckle (Swagger)
- MSTest & Microsoft.AspNetCore.Mvc.Testing

## Endpoints da API

### Autenticação
- `POST /administradores/login` - Realiza login e retorna o token JWT

### Administradores (Requer perfil Adm)
- `GET /administradores` - Lista todos os administradores cadastrados (paginado)
- `GET /administradores/{id}` - Busca administrador por ID
- `POST /administradores` - Cadastra um novo administrador

### Veículos
- `GET /veiculos` - Lista veículos cadastrados (requer autenticação)
- `GET /veiculos/{id}` - Busca veículo por ID (requer autenticação)
- `POST /veiculos` - Cadastra um novo veículo (requer perfil Adm ou Editor)
- `PUT /veiculos/{id}` - Atualiza dados de um veículo (requer perfil Adm)
- `DELETE /veiculos/{id}` - Remove um veículo (requer perfil Adm)

## Como rodar o projeto

### Pré-requisitos
- [.NET SDK 8](https://dotnet.microsoft.com/) instalado
- Instância do MySQL ativa (ou ajuste a string de conexão no `appsettings.json`)

### Execução da API
1. Entre na pasta da API e inicie o projeto:
   ```bash
   cd Api
   dotnet run
   ```
2. Acesse a documentação do Swagger pelo navegador:
   ```
   http://localhost:5000/swagger
   ```

### Execução dos Testes
Para rodar a suíte de testes:
```bash
dotnet test
```
