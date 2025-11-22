# Documento de Concepção do Produto

## 1. Título da Ideia/Projeto

**AgendaLocal** - Plataforma de Agendamento para Profissionais Autônomos

---

## 2. Descrição Geral da Ideia

### Problema que Resolve
Atualmente existe uma dificuldade significativa em **encontrar e agendar profissionais autônomos locais**, especialmente em negócios como barbearias, salões de beleza, personal trainers e outros serviços prestados por profissionais independentes. 

Os principais pontos de fricção são:
- **Para clientes**: Dificuldade em descobrir profissionais próximos, conhecer disponibilidade em tempo real e agendar de forma prática
- **Para profissionais**: Falta de ferramentas simples e acessíveis para organizar agenda, divulgar serviços e gerenciar agendamentos

### Solução Proposta
Uma **aplicação de agendamento de serviços** que conecta profissionais autônomos a clientes locais, onde:

- **Profissionais** podem se registrar, cadastrar os serviços que prestam (com preços e durações) e definir sua disponibilidade de horários
- **Clientes** podem descobrir esses profissionais através de busca por proximidade geográfica, categorias de serviço ou busca textual, visualizar disponibilidade e realizar agendamentos diretamente pela aplicação

A plataforma atua como uma ponte simples e eficiente entre oferta e demanda de serviços locais.

---

## 3. Objetivos da Ideia

### Objetivos Principais

1. **Facilitar o acesso a serviços locais**: Reduzir o tempo e esforço necessários para clientes encontrarem e agendarem profissionais autônomos próximos

2. **Profissionalizar autônomos**: Oferecer uma ferramenta simples e gratuita para que profissionais independentes possam organizar sua agenda e expandir sua base de clientes

3. **Eliminar intermediários ineficientes**: Substituir processos manuais (ligações telefônicas, mensagens no WhatsApp) por um sistema automatizado de agendamento

4. **Garantir experiência fluida**: Proporcionar confirmação imediata de agendamentos, notificações automáticas e histórico organizado para ambos os lados

5. **Aprendizado técnico** (como projeto de estudos): Explorar desafios reais de desenvolvimento como gestão de concorrência, geolocalização, notificações em tempo real e arquitetura escalável

---

## 4. Público-Alvo

### Prestadores de Serviço (Lado da Oferta)

**Perfil Principal**: Profissionais autônomos individuais

**Exemplos de categorias**:
- Barbeiros e cabeleireiros independentes
- Manicures e pedicures
- Personal trainers
- Esteticistas
- Massoterapeutas
- Professores particulares
- Eletricistas e encanadores freelancers

**Características**:
- Trabalham por conta própria (não em estabelecimentos)
- Podem ter local fixo ou atender a domicílio
- Necessitam de ferramenta simples para organizar agenda
- Geralmente possuem disponibilidade variável ao longo da semana
- Buscam aumentar visibilidade e conquistar novos clientes

### Clientes/Usuários Finais (Lado da Demanda)

**Perfil Principal**: Pessoas que buscam serviços locais de forma prática

**Características**:
- Priorizam **proximidade geográfica** (profissionais no seu bairro/região)
- Valorizam **praticidade** e agilidade no agendamento
- Preferem **confirmação imediata** sem necessidade de aprovação manual
- Querem **transparência** sobre disponibilidade, preços e avaliações

**Comportamento de Busca**:
- Por proximidade: "quero um barbeiro perto de mim agora"
- Por categoria: "preciso de um personal trainer"
- Por busca textual: "manicure domiciliar zona sul"

### Stakeholders Secundários

- **Administradores da plataforma**: Gerenciam categorias de serviços e garantem qualidade dos cadastros
- **Comunidade local**: Beneficia-se do fortalecimento da economia local e facilitação de serviços

---

## 5. Contexto de Uso

### Situações Típicas de Uso

#### Para Clientes:

**Cenário 1 - Busca por Proximidade**
> Maria precisa cortar o cabelo com urgência. Abre o app, permite localização, vê barbeiros disponíveis num raio de 3km, escolhe um com boa avaliação e horário disponível em 1 hora, agenda instantaneamente.

**Cenário 2 - Busca por Categoria**
> João quer começar treinos com personal trainer. Navega pela categoria "Fitness", filtra por sua região, compara preços e avaliações, agenda uma aula experimental.

**Cenário 3 - Busca Textual**
> Ana busca "manicure a domicílio Pinheiros". O app retorna profissionais que atendem nessa região, ela escolhe uma com boas avaliações e agenda para o fim de semana.

**Cenário 4 - Agendamento Recorrente**
> Carlos gosta do corte que fez e consulta o histórico para agendar novamente com o mesmo profissional no mês seguinte.

#### Para Profissionais:

**Cenário 1 - Gestão de Disponibilidade**
> Pedro, barbeiro autônomo, todo domingo atualiza sua agenda para a semana seguinte: define seg-sex 8h-12h e 14h-18h, mas bloqueia terça à tarde pois tem compromisso pessoal.

**Cenário 2 - Cadastro de Serviços**
> Juliana, manicure, cadastra seu catálogo: "Manicure Simples - R$35 - 40min", "Pedicure - R$40 - 50min", "Manicure + Pedicure - R$70 - 1h30min".

**Cenário 3 - Recebimento de Agendamento**
> Roberto recebe notificação de um novo agendamento confirmado para amanhã às 10h. Vê os dados do cliente e o serviço solicitado (Corte + Barba).

**Cenário 4 - Gestão de Cancelamentos**
> Um cliente cancela com antecedência. O horário volta a ficar disponível automaticamente e Roberto recebe notificação do cancelamento.

### Ambientes de Uso

- **Mobile**: Principal forma de acesso (tanto para clientes quanto profissionais)
- **Web**: Opção para profissionais gerenciarem agenda de forma mais detalhada
- **Em movimento**: Clientes buscando serviços próximos em tempo real
- **Em casa/trabalho**: Profissionais organizando disponibilidade com calma

---

## 6. Principais Funcionalidades Desejadas

### Para Profissionais (Prestadores)

#### 6.1. Gestão de Perfil
- Cadastro com informações básicas (nome, foto, telefone, descrição)
- Definição de categorias de atuação
- Indicação de localização/área de atendimento
- Opção de marcar se atende em local fixo ou a domicílio

#### 6.2. Catálogo de Serviços
- Cadastro de múltiplos serviços
- Para cada serviço: nome, descrição, preço, duração
- Ativação/desativação temporária de serviços

#### 6.3. Gestão de Disponibilidade
- Marcar dias e horários específicos disponíveis manualmente
- Exemplo: "Segunda 8h-12h e 14h-18h, Terça 8h-14h"
- Flexibilidade para ajustar semanalmente ou diariamente
- Visualização de agenda ocupada vs. disponível

#### 6.4. Gestão de Agendamentos
- Visualizar agendamentos confirmados em calendário
- Receber notificações de novos agendamentos
- Histórico completo de atendimentos realizados
- Visualizar avaliações recebidas dos clientes

#### 6.5. Cancelamento
- Possibilidade de cancelar agendamento (em casos excepcionais)
- Notificação automática ao cliente em caso de cancelamento

### Para Clientes

#### 6.6. Descoberta de Profissionais
- **Busca por proximidade geográfica**: Usar GPS para mostrar profissionais próximos
- **Navegação por categorias**: Listar categorias disponíveis (Barbearia, Beleza, Fitness, etc.)
- **Busca textual livre**: Buscar por nome de serviço, profissional ou localização

#### 6.7. Visualização de Perfis
- Ver informações do profissional (foto, descrição, localização)
- Catálogo de serviços com preços e durações
- Avaliações e comentários de outros clientes
- Disponibilidade em calendário

#### 6.8. Agendamento
- Selecionar serviço desejado
- Escolher data e horário disponível
- **Confirmação automática instantânea** (sem necessidade de aprovação manual)
- Receber confirmação com todos os detalhes

#### 6.9. Gestão de Agendamentos
- Visualizar agendamentos futuros
- Histórico de agendamentos passados
- Cancelar agendamento (com regras de antecedência)

#### 6.10. Avaliações
- Avaliar profissional após o serviço
- Deixar comentários e nota (ex: estrelas de 1 a 5)

### Funcionalidades Transversais (Sistema)

#### 6.11. Sistema de Notificações/Lembretes
- Lembrete para cliente antes do horário agendado (ex: 1 dia antes e 2 horas antes)
- Notificação para profissional de novo agendamento
- Notificação de cancelamentos para ambos os lados
- Canais: push notification, email, SMS/WhatsApp (conforme disponibilidade)

#### 6.12. Histórico de Agendamentos
- Registro completo de todos os agendamentos (para cliente e profissional)
- Filtros por data, status (realizado, cancelado)
- Possibilidade de reagendar com mesmo profissional

#### 6.13. Sistema de Avaliações
- Avaliações mútuas (opcional: profissional também pode avaliar cliente)
- Cálculo de média de avaliações
- Destaque para profissionais bem avaliados

#### 6.14. Painel Administrativo
- Gestão de categorias de serviços (criar, editar, remover)
- Moderação de conteúdo (perfis, avaliações)
- Visualização de métricas da plataforma

---

## 7. Diferenciais e Benefícios

### Diferenciais Competitivos

#### 7.1. Foco em Profissionais Autônomos Individuais
Diferente de plataformas que atendem estabelecimentos ou empresas, o **AgendaLocal** é desenhado especificamente para o profissional independente que trabalha por conta própria, com interface simplificada e sem complexidade desnecessária.

#### 7.2. Confirmação Automática de Agendamentos
Elimina a fricção de esperar aprovação manual. O cliente tem certeza imediata de que seu horário está garantido, aumentando conversão e satisfação.

#### 7.3. Gratuito e Acessível
Como projeto de estudos, a plataforma é 100% gratuita, democratizando acesso a uma ferramenta profissional para autônomos que não podem pagar por soluções comerciais caras.

#### 7.4. Busca Multicanal Inteligente
Combina três formas de descoberta (proximidade, categorias e busca textual) permitindo que diferentes perfis de usuários encontrem o que precisam da forma mais natural para eles.

#### 7.5. Flexibilidade de Disponibilidade
Permite que profissionais com rotinas irregulares gerenciem manualmente seus horários, sem forçar padrões semanais fixos que não se aplicam a todos.

### Benefícios para Profissionais

- ✅ **Visibilidade aumentada**: Aparecer para clientes que não os conheciam antes
- ✅ **Organização**: Agenda centralizada e automatizada
- ✅ **Redução de no-shows**: Lembretes automáticos diminuem faltas
- ✅ **Profissionalização**: Apresentação organizada de serviços e portfólio
- ✅ **Sem custo**: Ferramenta gratuita para começar ou crescer
- ✅ **Reputação**: Sistema de avaliações constrói credibilidade

### Benefícios para Clientes

- ✅ **Praticidade**: Encontrar e agendar em poucos cliques
- ✅ **Transparência**: Preços, horários e avaliações visíveis
- ✅ **Confirmação imediata**: Sem espera ou incerteza
- ✅ **Lembretes**: Não esquecer compromissos agendados
- ✅ **Histórico**: Fácil de retornar ao mesmo profissional
- ✅ **Descoberta local**: Apoiar profissionais da própria comunidade

### Benefícios Sociais

- 🌍 **Fortalecimento da economia local**: Conecta pessoas da mesma região
- 💼 **Empoderamento de autônomos**: Dá ferramentas para competir com estabelecimentos
- ⏱️ **Economia de tempo**: Elimina ligações, mensagens e idas presenciais para agendar

---

## 8. Possíveis Desafios ou Limitações Iniciais

### 8.1. Desafios Técnicos

#### Conflitos de Agendamento Simultâneos
**Descrição**: Dois clientes tentam agendar o mesmo horário ao mesmo tempo.

**Risco**: Overbooking (dois agendamentos para o mesmo slot) ou falha no processo de agendamento.

**Estratégias de Mitigação**:
- Implementar **lock pessimista** ou **lock otimista** no banco de dados
- Validação em tempo real da disponibilidade antes de confirmar
- Mensagens claras ao usuário se o horário foi reservado por outro cliente entre a consulta e a confirmação
- Testes de carga para simular concorrência

#### Cálculo Dinâmico de Disponibilidade
**Descrição**: Considerar durações diferentes de serviços ao mostrar horários disponíveis.

**Exemplo**: Se há disponibilidade de 10h-12h e um serviço dura 1h30min, precisa calcular que só pode oferecer horários até 10h30min (para terminar antes das 12h).

**Complexidade**: Lógica de cálculo precisa considerar:
- Duração de cada serviço
- Horários já agendados
- Intervalos entre atendimentos (se houver)

#### Geolocalização e Busca por Proximidade
**Descrição**: Calcular distância entre cliente e profissional e ordenar resultados.

**Desafios**:
- Performance de queries geoespaciais em banco de dados
- Precisão da localização (GPS pode ter margem de erro)
- Profissionais que atendem em múltiplos locais ou a domicílio

#### Sistema de Notificações Confiável
**Descrição**: Garantir que lembretes e notificações cheguem no momento certo.

**Desafios**:
- Infraestrutura para agendar e disparar notificações (cron jobs, filas)
- Múltiplos canais (push, email, SMS/WhatsApp)
- Lidar com falhas de entrega

### 8.2. Desafios de Produto e Experiência

#### Profissionais que Não Mantêm Agenda Atualizada
**Descrição**: Profissional não remove horários quando não pode atender ou esquece de adicionar disponibilidade.

**Impacto**: Clientes tentam agendar horários que na prática não estão disponíveis, gerando frustração.

**Estratégias de Mitigação**:
- **Notificações proativas**: Lembrar profissional de atualizar agenda semanalmente
- **Indicadores visuais**: Mostrar "última atualização da agenda" no perfil
- **Sistema de reputação**: Avaliar profissionais também pela confiabilidade da agenda
- **Confirmação periódica**: Pedir confirmação de agendamentos antigos
- **Modo férias/inativo**: Opção para profissional pausar temporariamente sem perder perfil

#### Adoção e Retenção de Profissionais
**Descrição**: Convencer profissionais a cadastrar e manter perfil atualizado.

**Desafio**: Profissionais ocupados podem não ver valor imediato ou achar trabalhoso.

**Estratégias**:
- Onboarding simplificado (cadastro em menos de 5 minutos)
- Benefícios claros logo no início (primeiros agendamentos)
- Interface mobile-first (gerenciar do celular)

#### Qualidade e Veracidade dos Cadastros
**Descrição**: Garantir que profissionais são reais e prestam os serviços anunciados.

**Risco**: Perfis falsos, informações enganosas.

**Estratégias**:
- Validação de telefone/email no cadastro
- Sistema de denúncias
- Moderação manual de novos cadastros (para projeto de estudos, pode ser manual mesmo)

#### Cold Start Problem (Problema do Início)
**Descrição**: No lançamento, haverá poucos profissionais cadastrados, logo poucos clientes; e vice-versa.

**Impacto**: Dificuldade para ganhar tração inicial.

**Estratégias**:
- Começar com cadastro manual de profissionais conhecidos
- Foco inicial em uma categoria ou região específica
- Divulgação em comunidades locais

### 8.3. Limitações Iniciais Aceitas (MVP)

Para o escopo de projeto de estudos e MVP, algumas limitações são esperadas e aceitáveis:

- **Sem sistema de pagamento integrado**: Pagamento é tratado diretamente entre cliente e profissional
- **Sem chat/mensagens**: Comunicação acontece fora da plataforma (telefone/WhatsApp)
- **Moderação manual**: Sem sistema automatizado de detecção de fraudes
- **Notificações básicas**: Apenas push e email, sem integração avançada com WhatsApp/SMS
- **Sem agendamento recorrente automático**: Cliente precisa agendar manualmente cada vez
- **Sem controle de múltiplos fusos horários**: Assume horário local do dispositivo

---

## 9. Próximos Passos Sugeridos

### Fase 1: Planejamento e Arquitetura (1-2 semanas)

#### 1.1. Definição de Stack Tecnológica
**Decisões a tomar**:
- **Frontend**: React/Next.js, Vue/Nuxt, Flutter, React Native?
- **Backend**: Node.js/Express, Python/Django, Java/Spring?
- **Banco de dados**: PostgreSQL, MongoDB, Firebase?
- **Infraestrutura**: Cloud (AWS, Google Cloud, Vercel) ou local?

**Critérios de decisão**:
- Tecnologias que você quer aprender
- Facilidade de implementação de geolocalização e notificações
- Comunidade e documentação

#### 1.2. Modelagem de Dados
**Entidades principais**:
- Usuário (Cliente / Profissional / Admin)
- Categoria de Serviço
- Profissional (estende Usuário)
- Serviço (pertence a Profissional)
- Disponibilidade (slots de tempo do Profissional)
- Agendamento
- Avaliação

**Relacionamentos a mapear**:
- Profissional → Serviços (1:N)
- Profissional → Disponibilidades (1:N)
- Profissional → Agendamentos (1:N)
- Cliente → Agendamentos (1:N)
- Agendamento → Serviço (N:1)
- Agendamento → Avaliação (1:1)

#### 1.3. Arquitetura do Sistema
**Componentes principais**:
- API REST ou GraphQL
- Sistema de autenticação e autorização
- Serviço de geolocalização
- Worker para notificações agendadas
- Storage para imagens de perfil

**Diagrama sugerido**: Criar diagrama de arquitetura mostrando fluxo de dados

### Fase 2: Desenvolvimento do MVP (4-8 semanas)

#### Iteração 1: Fundação (Semana 1-2)
- [ ] Setup do projeto e repositório
- [ ] Configuração de banco de dados
- [ ] Sistema de autenticação básico (registro/login)
- [ ] CRUD de perfil de usuário

#### Iteração 2: Profissionais e Serviços (Semana 3-4)
- [ ] Cadastro de perfil profissional
- [ ] CRUD de serviços
- [ ] Gestão de disponibilidade (marcação manual de horários)
- [ ] Visualização de agenda do profissional

#### Iteração 3: Busca e Descoberta (Semana 4-5)
- [ ] Sistema de categorias (CRUD admin)
- [ ] Busca por proximidade (geolocalização)
- [ ] Busca por categoria
- [ ] Busca textual
- [ ] Listagem de profissionais com filtros

#### Iteração 4: Agendamento (Semana 5-6)
- [ ] Visualização de disponibilidade do profissional
- [ ] Cálculo de slots disponíveis considerando duração de serviços
- [ ] Fluxo de agendamento com confirmação automática
- [ ] Tratamento de conflitos (lock de horário)

#### Iteração 5: Notificações e Histórico (Semana 6-7)
- [ ] Sistema de notificações push
- [ ] Lembretes automáticos antes de agendamentos
- [ ] Histórico de agendamentos para cliente
- [ ] Histórico de agendamentos para profissional
- [ ] Cancelamento de agendamentos

#### Iteração 6: Avaliações e Refinamentos (Semana 7-8)
- [ ] Sistema de avaliações (cliente avalia profissional)
- [ ] Exibição de média de avaliações
- [ ] Melhorias de UX baseadas em testes
- [ ] Ajustes de performance

### Fase 3: Testes e Validação (1-2 semanas)

#### 3.1. Testes Técnicos
- Testes de concorrência (agendamentos simultâneos)
- Testes de geolocalização com dados reais
- Testes de notificações
- Testes de carga (quantos usuários simultâneos o sistema suporta)

#### 3.2. Testes com Usuários Reais (Opcional)
- Convidar 5-10 profissionais conhecidos para cadastrar
- Pedir para amigos/familiares testarem como clientes
- Coletar feedback sobre usabilidade
- Identificar bugs e pontos de melhoria

#### 3.3. Documentação
- README com instruções de instalação
- Documentação da API
- Guia de uso para profissionais e clientes
- Documentação de arquitetura e decisões técnicas

### Fase 4: Aprendizados e Evoluções Futuras

#### 4.1. Retrospectiva Técnica
- Quais foram os maiores desafios?
- Que tecnologias/padrões funcionaram bem?
- O que você faria diferente?
- Que conceitos você dominou melhor?

#### 4.2. Possíveis Evoluções (Pós-MVP)
- Sistema de pagamento integrado
- Chat entre cliente e profissional
- Agendamento recorrente automatizado
- Programa de fidelidade/cupons
- Analytics para profissionais (quantos clientes, horários mais procurados)
- App mobile nativo
- Integração com Google Calendar
- Sistema de pacotes/assinaturas
- Múltiplos idiomas
- Modo escuro

---

## 📊 Resumo Executivo

**AgendaLocal** é uma plataforma de agendamento focada em conectar **profissionais autônomos individuais** a **clientes locais** que buscam serviços de forma prática e transparente.

### Proposta de Valor

| Para Profissionais            | Para Clientes                      |
| ----------------------------- | ---------------------------------- |
| Visibilidade e novos clientes | Praticidade e rapidez              |
| Organização de agenda         | Transparência de preços e horários |
| Ferramenta gratuita           | Confirmação imediata               |
| Profissionalização            | Avaliações confiáveis              |

### Modelo de Operação

1. Profissional se cadastra e define serviços + disponibilidade
2. Cliente descobre profissional (proximidade/categoria/busca)
3. Cliente escolhe serviço e horário
4. **Agendamento confirmado automaticamente**
5. Ambos recebem notificações/lembretes
6. Após o serviço, cliente pode avaliar

### Diferenciais-Chave

✨ Foco em **autônomos individuais** (não estabelecimentos)  
✨ **Confirmação automática** (sem aprovação manual)  
✨ **100% gratuito** (projeto de estudos)  
✨ Busca **multicanal** (proximidade + categoria + texto)

### Desafios Priorizados

⚠️ Conflitos de agendamento simultâneos (concorrência)  
⚠️ Agendas desatualizadas (engajamento de profissionais)

### Meta do MVP

Aplicação funcional com:
- Cadastro de profissionais e serviços
- Busca e descoberta
- Agendamento com confirmação automática
- Notificações básicas
- Histórico e avaliações

**Tempo estimado**: 6-8 semanas de desenvolvimento

---

## 🎯 Conclusão

Este documento estabelece uma **visão clara e estruturada** para o desenvolvimento do AgendaLocal. Com escopo bem definido, desafios mapeados e próximos passos planejados, o projeto está pronto para sair do papel e se tornar realidade.

O foco em **profissionais autônomos individuais** e **experiência simplificada** diferencia a plataforma e torna o MVP viável como projeto de estudos, ao mesmo tempo que resolve um problema real do mercado.

**Próxima ação recomendada**: Definir stack tecnológica e iniciar modelagem de dados.

---

**Documento gerado em**: 21 de novembro de 2025  
**Versão**: 1.0  
**Status**: Pronto para desenvolvimento
