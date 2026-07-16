# 🚀 CRM e Gestão de Leads - Trabalho Prático 5 (PAJ)

![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)
![Vite](https://img.shields.io/badge/vite-%23646CFF.svg?style=for-the-badge&logo=vite&logoColor=white)
![Jakarta EE](https://img.shields.io/badge/jakarta_ee-%23EE4444.svg?style=for-the-badge&logo=jakartaee&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/postgresql-%23316192.svg?style=for-the-badge&logo=postgresql&logoColor=white)
![Hibernate](https://img.shields.io/badge/Hibernate-59666C?style=for-the-badge&logo=Hibernate&logoColor=white)

Este projeto foi desenvolvido como o **Trabalho Prático 5** para a cadeira de Programação Avançada em Java (Curso Acertar o Rumo, FCTUC). Consiste numa aplicação web robusta (Frontend e Backend) para gestão de utilizadores, clientes e leads, incorporando funcionalidades avançadas em tempo real e boas práticas de arquitetura de software.

## 📸 Demonstração

### Versão Desktop
<div style="display: flex; gap: 10px; flex-wrap: wrap;">
  <img src="docs/dashboard.png" alt="Dashboard" width="400"/>
  <img src="docs/leads.png" alt="Leads Kanban" width="400"/>
  <img src="docs/users.png" alt="Gestão de Utilizadores" width="400"/>
  <img src="docs/chat.png" alt="Chat" width="400"/>
</div>

### Versão Mobile
<div style="display: flex; gap: 10px; flex-wrap: wrap;">
  <img src="docs/dashboard-mobile.png" alt="Dashboard Mobile" width="200"/>

</div>

## 🌟 Principais Funcionalidades

- **Segurança e Contas:** 
  - Confirmação de contas via e-mail (links únicos e expirados).
  - Recuperação de passwords (reset via link com token temporal).
  - Session timeout com logout automático após inatividade.
  - Hashes seguros de passwords (BCrypt).
- **Tempo Real (WebSockets):**
  - Chat 1-para-1 com histórico completo.
  - Sistema de notificações globais com contador dinâmico e marcação de "lida".
  - Atualização em tempo real do dashboard e das leads.
- **Gestão de Utilizadores e Perfis:**
  - Perfis detalhados por URL único (`/users/{username}`).
  - Dashboard para o Administrador com estatísticas e gráficos de evolução (utilizando *Recharts*).
  - Listagem de utilizadores filtrável, com paginação e ordenação feitas diretamente no backend para maior eficiência.
- **Auditoria e Logs:**
  - Registo persistente de atividades relevantes (CRUDs, acessos, falhas de segurança), guardando data, hora e token associado.
- **Internacionalização (i18n):**
  - Suporte completo para Português (PT) e Inglês (EN) através de `react-i18next`.
  - Preferências de idioma guardadas por utilizador.
- **Interface Responsiva:**
  - Layout *Mobile-first* garantindo adaptação perfeita a Mobile, Tablet e Desktop.

## 🛠️ Stack Tecnológico

### Backend (Jakarta EE)
- **Framework:** Jakarta EE 10 (JAX-RS, EJBs)
- **Persistência de Dados:** PostgreSQL com JPA (Hibernate)
- **Comunicação:** REST API + WebSockets
- **Segurança:** Autenticação por Tokens e validações (Hibernate Validator)
- **Testes:** JUnit 5, Mockito e integração com Selenium WebDriver

### Frontend (React)
- **Framework:** React 19 com Vite
- **Gestão de Estado:** Zustand
- **Navegação:** React Router v7
- **Estilização e Componentes:** Bootstrap 5, React Bootstrap, CSS (App.css / index.css)
- **Outras Bibliotecas:** Recharts (Gráficos), i18next (Internacionalização), React Responsive.

## 📁 Estrutura do Projeto

O projeto adota uma arquitetura em **Monorepo** para facilitar a visibilidade:

```text
PAJ-PROJETO5/
│
├── BACKEND/                  # Código fonte da API em Java (Jakarta EE)
│   ├── src/main/java         # Lógica de negócio, Serviços, DAOs, Websockets
│   ├── src/main/resources    # Configurações de BD (persistence.xml) e Logs
│   └── pom.xml               # Dependências do Maven
│
├── FRONTEND/                 # Aplicação Cliente (React + Vite)
│   ├── src/                  # Componentes, Páginas, Stores (Zustand), Serviços API
│   ├── public/               # Assets estáticos
│   └── package.json          # Dependências do NPM
│
├── docs/                     # Documentação adicional, enunciados e screenshots
│
└── README.md                 # Documentação do projeto

```

<img width="457" height="838" alt="Captura de ecrã 2026-07-16 155909" src="https://github.com/user-attachments/assets/bac984cf-c2de-4a06-92a2-88d8257caa1a" />
<img width="1918" height="916" alt="Captura de ecrã 2026-07-16 155810" src="https://github.com/user-attachments/assets/c7b59eb4-89d9-45a5-a358-f8eecd557647" />
<img width="1912" height="901" alt="Captura de ecrã 2026-07-16 155801" src="https://github.com/user-attachments/assets/f5006ad6-82d3-4e9f-9acd-e875763071d2" />
<img width="1917" height="871" alt="Captura de ecrã 2026-07-16 155748" src="https://github.com/user-attachments/assets/4054fa01-f58c-440f-ad7a-ddf1c9e53a85" />
<img width="1917" height="907" alt="Captura de ecrã 2026-07-16 155737" src="https://github.com/user-attachments/assets/40c18574-91cf-4a45-96df-b4cfcbc45f2c" />
<img width="1917" height="907" alt="Captura de ecrã 2026-07-16 155719" src="https://github.com/user-attachments/assets/645244b6-2f70-4871-9459-f9bd5cf2e9c1" />


## 🚀 Como Iniciar o Projeto Localmente

### Pré-requisitos
- **Java 21** e **Maven** instalados.
- **Node.js** (v18+) instalado.
- Servidor de Aplicações configurado (ex: WildFly / JBoss) com uma Base de Dados **PostgreSQL** ativa.

### 1. Iniciar o Backend
1. Abra um terminal na pasta `BACKEND`.
2. Configure as credenciais da base de dados PostgreSQL no ficheiro `persistence.xml`.
3. Compile o projeto e gere o ficheiro WAR:
   ```bash
   mvn clean install
   ```
4. Faça o deploy do `.war` gerado (pasta `target/`) no seu servidor de aplicações (ex: WildFly).

### 2. Iniciar o Frontend
1. Abra um terminal na pasta `FRONTEND`.
2. Instale as dependências:
   ```bash
   npm install
   ```
3. Inicie o servidor de desenvolvimento:
   ```bash
   npm run dev
   ```
4. Aceda à aplicação através do endereço local fornecido pelo Vite (por norma, `http://localhost:5173`).

---
*Projeto desenvolvido no âmbito do Curso Acertar o Rumo (Universidade de Coimbra).*
