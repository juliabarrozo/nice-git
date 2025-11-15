# 🏛️ **Arquitetura de Software – Modelo MVC para o Sistema**

A proposta abaixo consolida o diagrama de classes, os casos de uso e o fluxo de autenticação do agente, estruturando o sistema em uma **arquitetura MVC modular, escalável e orientada ao domínio**.

---

# 1. **Camadas da Arquitetura (Visão Macro)**

A solução é segmentada em três camadas funcionais:

## **1.1. Model (Camada de Domínio e Dados)**

Responsável por:

* Representar as entidades do diagrama de classes.
* Implementar regras de negócio específicas do domínio (restrições, validações, consistência).
* Fazer a ponte com o banco de dados (CRUD).
* Garantir integridade, isolamento e coerência das operações.

**Entidades do Domínio (Modelos):**

* **Usuario**
* **LoginRealizado**
* **Questionario**
* **RespostaQuestionario**
* **Feedback**
* **RespostaFeedback**
* **SituacaoReportada**
* **Dashboard (modelo analítico)**

Cada modelo reflete diretamente as associações e multiplicidades do diagrama de classes.

---

## **1.2. Controller (Camada de Orquestração e Regras de Aplicação)**

Responsável por:

* Controlar o fluxo entre usuário → sistema → banco.
* Aplicar regras de negócio dos casos de uso.
* Realizar controle de acesso por perfil (Administrador, Gestor, Psicólogo e Colaborador).
* Integrar as ações com as Views adequadas.

**Controladores essenciais:**

* **AuthController** — Autenticação, autorização e encerramento de sessão.
* **UsuarioController** — CRUD de colaboradores (Cadastrar, Editar, Excluir, Consultar).
* **QuestionarioController** — Criação, edição, consulta, exclusão, resposta e envio de questionários.
* **FeedbackController** — Criação, consulta, edição, exclusão, envio e resposta de feedbacks.
* **SituacaoController** — Gerenciamento completo de situações reportadas.
* **DashboardController** — Acesso analítico às métricas derivadas dos questionários respondidos.

Cada controller opera alinhado aos fluxos detalhados nas tabelas dos casos de uso.

---

## **1.3. View (Camada de Apresentação)**

Responsável por:

* Exibir interfaces específicas para cada tipo de ator.
* Apresentar formulários, painéis e dashboards.
* Renderizar respostas dos controllers.
* Não conter lógica de negócio — apenas exibição.

**Principais módulos de interface:**

* **Autenticação:** Tela de login.
* **Gestão de Colaboradores:** Listagem, cadastro, edição, exclusão e detalhes.
* **Questionários:** Criação, edição, visualização, aplicação e resposta.
* **Feedbacks:** Criação, histórico, visualização e resposta.
* **Situações Reportadas:** Cadastro, edição, consulta e exclusão.
* **Dashboard:** Interface analítica para gestores e psicólogos.

---

# 2. **Integração entre as Camadas (Fluxo MVC)**

O fluxo operacional segue a lógica:

1. **Usuário realiza ação** (exemplo: clicar em "Novo Questionário").
2. **Controller correspondente é acionado**, valida permissões e encaminha a requisição.
3. **Controller interage com os Models**, aplicando regras de negócio e persistindo dados.
4. **Controller seleciona a View adequada**, declarando o que deve ser exibido.
5. **View apresenta o resultado** ao usuário final.

Esse ciclo se repete de forma consistente em todos os casos de uso documentados.

---

# 3. **Arquitetura Modular por Domínio (Visão Funcional)**

O sistema pode ser organizado em cinco módulos principais:

### **3.1. Módulo de Autenticação e Controle de Acesso**

* Gerencia login, logout e perfis.
* Integra `Usuario`, `LoginRealizado` e regras de segurança.
* Redireciona automaticamente para painéis personalizados.

### **3.2. Módulo de Gestão de Usuários (Colaboradores)**

* Orquestrado pelo `UsuarioController`.
* Atende todos os casos de uso de cadastro, edição, exclusão e consulta.
* Implementa regras: CPF único, não excluir último administrador, auditoria.

### **3.3. Módulo de Questionários**

* Reflete a relação Questionario → RespostaQuestionario.
* Apoia criação por Psicólogos e Gestores.
* Garante regras de edição, exclusão, número mínimo de questões, integridade das respostas.

### **3.4. Módulo de Feedbacks**

* Abrange Feedback e RespostaFeedback.
* Permite envio por Administrador e resposta por Colaborador.
* Trata confidencialidade de feedbacks anônimos.

### **3.5. Módulo de Situações Reportadas**

* Exclusivo para Psicólogos.
* Controla fluxo de criação, consulta, edição e exclusão.
* Valida vínculo com colaborador, data do ocorrido e regras de auditoria.

### **3.6. Módulo de Dashboard**

* Consome dados consolidados de questionários respondidos.
* Permite visão analítica para Psicólogos e Gestores.

---

# 4. **Instrumentação Técnica da Arquitetura**

### **4.1. Repositório de Dados por Modelo**

Cada entidade possui:

* Classe de domínio
* Repositório de persistência (dentro do próprio Model ou DDD-style separado)
* Mapeamento das relações conforme o diagrama

### **4.2. Controle de Acesso Centralizado**

Módulo único responsável por:

* Validar sessão
* Validar tipo de usuário
* Proteger rotas por perfil

### **4.3. Roteamento por Controladores**

Cada funcionalidade tem uma rota declarada, sempre apontando para um controller específico.

### **4.4. Separação Clara entre UI e Regras**

Todas as regras dos casos de uso serão executadas:

* **No Controller** quando forem regras de aplicação
* **No Model** quando forem regras de domínio

---

# 5. **Governança da Arquitetura**

* **Alta coerência interna entre módulos (alta coesão).**
* **Baixo acoplamento** entre Model, Controller e View.
* **Escalabilidade horizontal por funcionalidade** — cada módulo pode crescer isoladamente.
* **Aderência total aos casos de uso documentados.**
* **Compliance LGPD** garantido nos módulos de Feedback, Questionário e Situações.

---

# 6. **Resumo Executivo**

A arquitetura MVC final fica estruturada assim:

**Model** → representa o domínio conforme o diagrama de classes.
**Controller** → implementa todos os casos de uso, respeitando permissões por perfil.
**View** → exibe interfaces diferentes por ator, sem lógica de negócio.

Tudo isso organizado em **módulos funcionais**, usando o MVC como backbone da solução.

---
