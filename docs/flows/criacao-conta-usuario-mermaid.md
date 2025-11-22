# Fluxo de Processo: Criação de Conta de Usuário

```mermaid
flowchart TD
    Start(["Início"]) --> AcessaPagina["Usuário acessa página de cadastro"]
    AcessaPagina --> PreencheForm["Usuário preenche formulário"]
    PreencheForm --> SubmeteForm["Usuário submete formulário"]
    SubmeteForm --> ValidaInfo{"Sistema valida informações"}
    
    ValidaInfo -->|Incorretas ou Incompletas| ExibeErro["Sistema exibe mensagens de erro"]
    ExibeErro --> PermaneceNaPagina["Usuário permanece na página"]
    PermaneceNaPagina --> PreencheForm
    
    ValidaInfo -->|Corretas| CriaConta["Sistema cria conta no banco de dados"]
    CriaConta --> GeraRegistro["Sistema gera registro de confirmação"]
    GeraRegistro --> EnviaEmail["Sistema envia e-mail de confirmação"]
    EnviaEmail --> ExibeSucesso["Sistema exibe mensagem de sucesso"]
    ExibeSucesso --> End(["Fim"])
```

## Legenda

- **Nós Circulares**: Início e Fim do processo
- **Nós Retangulares**: Ações ou processos
- **Nó Losango**: Ponto de decisão/validação
- **Setas com texto**: Condições ou resultados da decisão
