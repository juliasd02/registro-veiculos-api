# API de Registro de Veículos (Minimal API)

Projeto desenvolvido durante o bootcamp da DIO (Digital Innovation One) focado na criação de uma API utilizando o recurso de **Minimal APIs** do .NET, autenticação com **JWT** e testes.

## Sobre o projeto

A proposta do laboratório foi criar uma API para cadastro e gerenciamento de veículos e administradores. 

A aplicação conta com:
- Autenticação e autorização via JWT, dividindo os acessos entre perfis de `Adm` e `Editor`.
- Rotas para cadastro, listagem, atualização e remoção de veículos.
- Documentação interativa via Swagger para testar as requisições enviando o token no cabeçalho `Authorization`.
- Projeto separado de testes unitários e de integração utilizando MSTest e WebApplicationFactory.

## Estrutura da solução

- `Api/`: Código-fonte principal da Minimal API, contendo DTOs, Entidades, Serviços, DbContext e configuração das rotas.
- `Test/`: Testes automatizados cobrindo entidades, serviços e requisições HTTP.

## Tecnologias

- C# / .NET 8
- ASP.NET Core Minimal APIs
- Entity Framework Core / MySQL
- Autenticação JWT Bearer
- Swagger / OpenAPI
- MSTest

## Principais rotas

### Autenticação
- `POST /administradores/login` - Faz login e gera o token JWT

### Administradores (apenas perfil Adm)
- `GET /administradores` - Lista administradores
- `GET /administradores/{id}` - Busca administrador por ID
- `POST /administradores` - Cadastra administrador

### Veículos
- `GET /veiculos` - Lista veículos (requer autenticação)
- `GET /veiculos/{id}` - Busca veículo por ID (requer autenticação)
- `POST /veiculos` - Cadastra veículo (requer Adm ou Editor)
- `PUT /veiculos/{id}` - Atualiza veículo (requer Adm)
- `DELETE /veiculos/{id}` - Remove veículo (requer Adm)

## Como rodar localmente

1. Clone o repositório:
   ```bash
   git clone https://github.com/juliasd02/registro-veiculos-api.git
   cd registro-veiculos-api
   ```

2. Para rodar a API:
   ```bash
   cd Api
   dotnet run
   ```
   Acesse a documentação no navegador: `http://localhost:5000/swagger`

3. Para rodar os testes:
   ```bash
   dotnet test
   ```
