# Documentação do Projeto Urutau

## 🆘 Identificação do Problema
As equipes de segurança gastam muito tempo executando manualmente scripts de análise de vulnerabilidades (LinPEAS, BeRoot, etc.) e correlacionando resultados, sem uma integração eficiente aos pipelines de desenvolvimento.

---

## 💡 Ideia do Projeto
Desenvolver o **Urutau**, uma plataforma de automação de análise de vulnerabilidades e pentest baseada em nuvem. Ela permitirá que equipes de segurança e DevOps detectem, classifiquem e remediem falhas de forma contínua e escalável.

---

## 🔥 Descrição do Problema
- Execução manual de scripts (LinPEAS, BeRoot, etc.).
- Falta de unificação entre varredura, análise contextual e remediação.
- Dificuldade de integração com pipelines de desenvolvimento (**shift-left**).
- Ausência de feedback em tempo real e dashboards consolidados para gestão de riscos.

---

## 👥 Stakeholders
- Equipes de **SecOps / Red Team**
- **DevOps / SRE**
- **Gerentes de TI e CISOs**
- **P&D em Cibersegurança**
- **Auditoria e Compliance**

---

## 🎯 Justificativa
Adotar uma solução que combina:
- Execução automatizada de scripts,
- Análise assistida por IA,
- Remediação guiada,

Isso resulta em:
- Redução no tempo de detecção e correção de falhas,
- Aumento da produtividade,
- Melhoria na postura de segurança corporativa.

---

## 📋 Levantamento de Requisitos

### ✅ Requisitos Funcionais
- **Varredura Automatizada**
  - Execução de LinPEAS, BeRoot, Sherlock, etc., em containers isolados.
  - Agendamento recorrente (cron) ou on-demand.

- **Análise de Vulnerabilidades**
  - Integração com **API OpenAI (GPT-4)** para:
    - Classificação de criticidade,
    - Sugestões de correção.
  - Geração de scripts de remediação (playbooks, Ansible, Terraform).

- **Dashboards e Relatórios**
  - Frontend em **React.js** com:
    - Heatmaps,
    - Gráficos de tendência,
    - Mapa geográfico de ativos vulneráveis.
  - Exportação de relatórios em **PDF e JSON** para S3.

- **API Pública REST**
  - Endpoints para:
    - Iniciar scans,
    - Obter status,
    - Baixar relatórios.
  - Suporte a webhooks (Slack, Jira, GitHub Actions).

- **Modo CTF / Gaming**
  - Leaderboards, conquistas e badges.
  - Ambiente isolado para desafios de pentest com cronômetro e pontuação.

---

### ⚙️ Requisitos Não-Funcionais
- **Escalabilidade**
  - Backend em **ECS/Fargate** com auto-scale.
  - Uso de **Lambda** para eventos (S3 uploads, eventos Git).

- **Segurança**
  - TLS 1.3 (via ACM + CloudFront).
  - IAM Roles granular (least-privilege).
  - Criptografia em repouso (SSE-S3, RDS encryption).

- **Disponibilidade & Confiabilidade**
  - Multi-AZ (RDS, S3).
  - Health checks no ALB.
  - Plano de **Disaster Recovery (DR)** documentado.

- **Desempenho**
  - CDN (**CloudFront**) para frontend.
  - Cache Redis para resultados recentes.

- **Compliance & Auditoria**
  - Logs no **CloudWatch + OpenSearch**.
  - Modo Compliance (LGPD/GDPR) com geração de evidências.

---

## 🚀 MVP (Produto Mínimo Viável)
- Execução on-demand de **LinPEAS/BeRoot** em containers Docker.
- Dashboard básico com:
  - Lista de vulnerabilidades,
  - Classificação via **GPT-4**.
- Exportação de relatório **JSON** para S3.

---

## 🏗️ Planejamento Ágil

### 🔙 Backlog de Tarefas
- Arquitetura de containerização (**Docker + ECS Task**).
- Módulo de varredura (**LinPEAS/BeRoot**).
- Integração com **API OpenAI**.
- Backend em **Django REST**:
  - Endpoints de scan, status e relatório.
- Frontend em **React**:
  - Exibição de resultados.
- Infraestrutura com **Terraform**:
  - EC2/ECS, S3, Lambda, RDS, IAM.
- Geração de relatórios (PDF/JSON) e envio para S3.
- Autenticação (**OAuth2 / SSO/SAML**).
- Pipeline CI/CD (**GitHub Actions → ECR/ECS deploy**).
- Testes de carga e failover.

---

### 🏃‍♂️ Sprints
| Sprint | Entregas Principais                                                   | Duração |
|--------|-----------------------------------------------------------------------|---------|
| Sprint 1 | IaC, Pipeline CI/CD, Varredura Docker                               | 2 semanas |
| Sprint 2 | OpenAI, Backend REST, Exportação JSON                               | 2 semanas |
| Sprint 3 | Frontend básico, Dashboard estático, Deploy em ECS/Fargate          | 2 semanas |
| Sprint 4 | Relatórios PDF, API pública, Webhooks, Testes de Integração         | 2 semanas |
| Sprint 5 | Autenticação SSO, Modo CTF, Gamificação                              | 2 semanas |

---

## 📌 Quadro de Tarefas
Utilizar **Jira** com:
- **Swimlanes**:
  - To Do
  - In Progress
  - Review
  - Done
- Tags por componente:
  - **Infra, Backend, Frontend, Data, Security**

---

## 🎯 Apresentação & Entregáveis

### Estrutura da Apresentação
1. **Introdução**
   - Problema + Objetivos do **Urutau**.
2. **Arquitetura de Solução**
   - Diagramas AWS + Fluxos de Dados.
3. **Demonstração Técnica**
   - Scan on-demand + Análise IA + Relatório.
4. **Roadmap & Próximos Passos**
   - Funcionalidades futuras e cronograma.

---

### Recursos Visuais
- **Diagramas**: UML / C4 (containers, microserviços, integrações).
- **Wireframes**: Frontend (dashboards, vulnerabilidades, gamificação).
- **Gráficos de Métricas**:
  - Tempo médio de scan,
  - Uso de CPU/RAM no Fargate,
  - Taxa de false-positives.

---

### Material de Apoio
- Documento PDF baseado neste template.
- Slides (**PowerPoint ou Google Slides**) com paleta visual **Urutau**.
- **Repositório GitHub** com README técnico e exemplos de uso da API.

---
