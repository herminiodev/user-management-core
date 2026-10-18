# 🤝 Guia de Contribuição

Primeiro, obrigado por demonstrares interesse em contribuir para o **UserManagement.Core**! É a comunidade que torna os projetos *open source* ferramentas incríveis.

Para garantir um processo de revisão fluido e manter a qualidade do código, por favor, segue estas diretrizes.

---

## 🛑 Como Posso Contribuir?

### 1. Reportar Erros (Bugs)
Se encontraste um comportamento inesperado ou uma falha de segurança:
*   Verifica se já não existe uma *Issue* aberta sobre o assunto.
*   Abre uma nova *Issue* utilizando o modelo de **Bug Report**.
*   Inclui passos claros para reproduzir o erro, a versão do .NET utilizada e o comportamento esperado.

### 2. Sugerir Funcionalidades
Tens uma ideia para uma nova funcionalidade (ex: integração com um novo provedor de OAuth)?
*   Abre uma *Issue* do tipo **Feature Request**.
*   Explica o caso de uso e como isso trará valor para outros programadores que usam a biblioteca.

### 3. Enviar Alterações de Código (Pull Requests)
Se queres colocar as mãos na massa e resolver uma *Issue* ou implementar uma melhoria:
1. Faz um **Fork** do repositório.
2. Cria uma ramificação (*branch*) para a tua alteração:
   ```bash
   git checkout -b feature/nome-da-funcionalidade
   # ou para correção de bugs:
   git checkout -b fix/nome-do-bug
   ```
3. Garante que o teu código compila e que todos os testes existentes passam.
4. Submete o teu **Pull Request (PR)** apontando para a branch `main` do projeto original.

---

## 🛠️ Padrões de Código e Desenvolvimento

Para mantermos a base de código limpa e legível (seguindo os padrões da comunidade .NET), pedimos que cumpras as seguintes regras:

*   **Convenção de Nomes:** Segue as diretrizes oficiais de design do C# (PascalCase para métodos e classes, camelCase para variáveis locais e parâmetros).
*   **Clean Architecture:** Respeita a separação de conceitos. Regras de negócio ficam na camada `Core`, acessos a dados no `Infrastructure` e configurações de rotas no `Api`.
*   **Testes Unitários:** Idealmente, qualquer nova funcionalidade ou correção de bug deve vir acompanhada do seu respetivo teste na diretoria de testes.
*   **Formatação:** Executa o comando de formatação do .NET antes de fazer o commit para garantir que o estilo do código está correto:
    ```bash
    dotnet format
    ```

---

## 💬 Padrão de Mensagens de Commit

Preferimos commits limpos e descritivos. Tenta utilizar prefixos lógicos nas tuas mensagens, por exemplo:
*   `feat: adiciona suporte a rotação de refresh tokens`
*   `fix: corrige validação de expiração do token JWT`
*   `docs: atualiza exemplos de configuração no README`
*   `test: adiciona testes para o middleware de auditoria`

---

## ⚖️ Licença

Ao contribuir para este projeto, concordas que as tuas contribuições serão licenciadas sob os mesmos termos da [Licença MIT](LICENSE) do projeto.
