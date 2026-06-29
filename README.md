\# 🏥 Sistema de Clínica Médica - Módulo Tech Lead / Infra \& Gateway



\## 👥 Integrantes do Grupo

\* \*\*Lucas Paris\*\* - (Responsável por Tech Lead / Infra \& Gateway)

\* \*\*Lucas Silveira\*\* - (Responsável pelo Módulo de Atendimento)

\* \*\*João Gabriel\*\* - (Responsável pelo Módulo de Agendamento)

\* \*\*Geovani\*\* - (Responsável pelo Módulo Administrativo)



\---



\## 📌 Sobre o Subprojeto

Este módulo é a espinha dorsal da infraestrutura do sistema, atuando como o \*\*API Gateway\*\* centralizador. Ele faz o roteamento das requisições para os microsserviços/módulos independentes da clínica com segurança e resiliência.



\### 🛠️ Tecnologias Utilizadas

\* \*\*Java 17\*\* (Linguagem principal)

\* \*\*Spring Boot 3.5.x\*\* (Framework do projeto)

\* \*\*Spring Cloud Gateway\*\* (Roteamento de API)

\* \*\*Maven\*\* (Gerenciador de dependências)

\* \*\*YAML (`application.yml`)\*\* (Formato de configuração)



\---



\## ⚙️ Configuração do API Gateway



Para que o Gateway roteie as chamadas corretamente para os módulos locais de cada colega, o arquivo `src/main/resources/application.yml` deve seguir a estrutura abaixo:



```yaml

spring:

&#x20; cloud:

&#x20;   gateway:

&#x20;     routes:

&#x20;       - id: agendamento-module

&#x20;         uri: http://localhost:8081

&#x20;         predicates:

&#x20;           - Path=/agendamentos/\*\*

&#x20;       - id: atendimento-module

&#x20;         uri: http://localhost:8082

&#x20;         predicates:

&#x20;           - Path=/atendimentos/\*\*

