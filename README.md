# 🏥 Sistema de Clínica Médica - Infraestrutura & API Gateway

## 👥 Integrantes do Grupo e Papéis
* **Lucas Paris** - Tech Lead / Infra & Gateway (Configuração do Spring Cloud Gateway, Docker, Security JWT)
* **Joao Gabriel** - Dev Microsserviço Agendamento (Spring Boot + JPA, Lógica de Agendamento)
* **Lucas Silveira** - Dev Microsserviço Atendimento (Spring Boot + JPA, Prontuário, Anamnese)
* **Geovani** - Dev Microsserviço Administrativo (Gerenciamento de Funcionários, Médicos, Especialidades, Convênios e validações de dados)
* **Derlan Silva:** QA, Doc & Testes (Criando Collections no Postman, Documentação com OpenAPI/SpringDoc e Testes Unitários com JUnit)

---

## 📌 Sobre o Subprojeto
Este é o coração da infraestrutura do sistema. Ele centraliza todas as requisições através do Spring Cloud Gateway, faz o roteamento inteligente para cada microsserviço, gerencia a segurança de ponta a ponta com autenticação via Tokens JWT e unifica o ambiente utilizando Docker.

### 🛠️ Tecnologias Utilizadas
* **Java 17** (Linguagem base obrigatória)
* **Spring Boot 3.5.15** (Framework base)
* **Spring Cloud Gateway** (Roteamento e segurança da API)
* **Spring Security & JWT** (Autenticação e controle de acesso dos usuários)
* **Docker & Docker Compose** (Containerização e orquestração do ambiente)
* **YAML (`application.yml`)** (Formato de configuração das propriedades de rotas)

---

## ⚙️ Configuração do Gateway

A estrutura base de roteamento configurada no arquivo `src/main/resources/application.yml` direciona o tráfego conforme o padrão abaixo:

```yaml
spring:
  application:
    name: clinica-infra-gateway
  cloud:
    gateway:
      routes:
        - id: administrativo-route
          uri: http://localhost:8081
          predicates:
            - Path=/administrativo/**
        - id: agendamento-route
          uri: http://localhost:8082
          predicates:
            - Path=/agendamento/**
        - id: atendimento-route
          uri: http://localhost:8083
          predicates:
            - Path=/atendimento/**