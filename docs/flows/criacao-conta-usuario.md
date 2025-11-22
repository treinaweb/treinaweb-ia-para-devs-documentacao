# Fluxo de Processo: Criação de Conta de Usuário

## Processo Principal

1. O usuário acessa a página de cadastro
2. O usuário preenche o formulário com suas informações pessoais
3. O usuário submete o formulário
4. O sistema valida as informações fornecidas

### Condição: Validação das Informações

**SE** as informações estiverem **INCORRETAS** ou **INCOMPLETAS**:
   - 5a. O sistema exibe mensagens de erro específicas
   - 6a. O usuário permanece na página de cadastro
   - 7a. Retornar ao passo 2

**SE** as informações estiverem **CORRETAS**:
   - 5b. O sistema cria a conta do usuário no banco de dados
   - 6b. O sistema gera um registro de confirmação
   - 7b. O sistema envia um e-mail de confirmação para o endereço fornecido
   - 8b. O sistema exibe uma mensagem de sucesso ao usuário

## Fim do Processo

---

## Dados Necessários
- Informações pessoais do usuário (nome, e-mail, senha, etc.)

## Saídas
- Conta criada no sistema
- E-mail de confirmação enviado

## Exceções
- Informações inválidas ou incompletas
- Erro no envio do e-mail (tratamento adicional pode ser necessário)