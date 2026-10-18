# 🚀 UserManagement.Core

[![Nuget](https://shields.io)](https://nuget.org)
[![License: MIT](https://shields.io)](LICENSE)
[![PRs Welcome](https://shields.io)](CONTRIBUTING.md)

**UserManagement.Core** é uma biblioteca *open-source* de alta performance para **ASP.NET Core** desenhada para eliminar o código repetitivo (*boilerplate*) na criação de sistemas de autenticação, autorização avançada e gestão de utilizadores.

Inspirado na simplicidade e elegância de ferramentas como o *Laravel Sanctum* e *Spatie Permissions*, este ecossistema oferece uma solução avançada "pronta para produção" com configurações mínimas. Insira um sistema completo de gestão de utilizadores no seu projeto com apenas poucas linhas de código.

---

## ✨ Funcionalidades Principais

- 🔑 **Autenticação Híbrida:** Suporte nativo a JWT (com rotação de *Refresh Tokens*) e API Keys customizáveis por utilizador (Estilo Sanctum).
- 🔐 **Autorização Granular (RBAC/ABAC):** Gestão dinâmica de Funções (*Roles*) e Permissões em base de dados com suporte a herança de regras.
- 🛡️ **Segurança Avançada:** Bloqueio automático de contas por força bruta (*Lockout*), gestão de sessões ativas e MFA/2FA via TOTP.
- 📝 **Trilha de Auditoria:** Registo automático de histórico de alterações de dados e ações críticas (Quem, Quando, Onde e O Quê).
- 🐳 **Pronto para o Ecossistema:** Documentação Swagger auto-gerada com filtros de segurança e compatibilidade com Entity Framework Core (PostgreSQL, SQL Server, MySQL).

---

## 🚀 Como Começar

### 1. Instalação

Instale o pacote via NuGet Package Manager (Brevemente):
```bash
dotnet add package UserManagement.Core
```

### 2. Configuração (`Program.cs`)

Adicione o serviço e ative o middleware no pipeline da sua aplicação ASP.NET Core:

```csharp
using UserManagement.Core;

var builder = WebApplication.CreateBuilder(args);

// Configura o ecossistema completo de utilizadores
builder.Services.AddUserManagementCore(options => 
{
    options.UsePostgreSQL(builder.Configuration.GetConnectionString("DefaultConnection"));
    options.EnableAuditLogs = true;
    options.TokenLifespanInMinutes = 60;
});

var app = builder.Build();

// Ativa a documentação Swagger e os endpoints internos de autenticação
app.UseUserManagementCore(); 

app.Run();
```

### 3. Proteger Endpoints

Utilize os atributos nativos e otimizados para validar permissões granulares:

```csharp
[ApiController]
[Route("api/produtos")]
public class ProdutoController : ControllerBase
{
    [HttpPost]
    [AuthorizePermission("produtos.criar")] // Validação baseada em permissões dinâmicas
    public IActionResult CriarProduto([FromBody] CriarProdutoDto dto)
    {
        return Ok();
    }
}
```

---

## 🛠️ Arquitetura do Projeto

O projeto segue os princípios de **Clean Architecture** e **SOLID**, garantindo que a infraestrutura (como a escolha da base de dados) esteja completamente desacoplada das regras de negócio de identidade.

```text
📂 src
 ├── 📂 UserManagement.Core          # Regras de negócio, Entidades (User, Role, Permission) e Interfaces
 ├── 📂 UserManagement.Infrastructure # Implementação do EF Core, Repositórios e Serviços de Token
 └── 📂 UserManagement.Api            # Middlewares, Controladores Internos e Configuração do Swagger
```

---

## 🤝 Como Contribuir

Contribuições são o que fazem a comunidade open-source um lugar incrível para aprender, inspirar e criar. Qualquer contribuição que fizer será **muito apreciada**.

1. Faça um **Fork** do projeto
2. Crie uma **Branch** para a sua Feature (`git checkout -b feature/IncrivelFeature`)
3. Faça **Commit** das suas alterações (`git commit -m 'Add: Alguma IncrivelFeature'`)
4. Faça **Push** para a Branch (`git push origin feature/IncrivelFeature`)
5. Abra um **Pull Request**

*Por favor, leia o arquivo [CONTRIBUTING.md](CONTRIBUTING.md) para detalhes sobre o nosso código de conduta.*

---

## 📄 Licença

Distribuído sob a licença MIT. Veja o arquivo `LICENSE` para mais informações.
