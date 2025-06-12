# MLOps: Machine Learning Operations

**MLOps** é a prática que integra o desenvolvimento, implantação e monitoramento de modelos de Machine Learning (ML) e fluxos de trabalho de Inteligência Artificial (IA), promovendo eficiência, colaboração e automação.

---

## Principais Características

- **Colaboração entre equipes:** Integração entre times de dados, engenharia e operações.
- **Automatização de processos:** Redução de tarefas manuais e aumento da produtividade.
- **Criação de fluxos executáveis:** Estruturação de pipelines de ML de ponta a ponta.
- **Acompanhamento de experimentos:** Registro e comparação de experimentos de modelos.
- **Monitoramento de desempenho:** Observabilidade contínua dos modelos em produção.

---

## Aprendizado Autodirigido

- [**Introdução**](01-intro)
- [**Rastreamento de Experimentos & Gerenciamento de Modelos**](02-rastreamento-de-experimentos)
- [**Orquestração & Pipelines de ML**](03-orquestação)
- [**Implantação 🚢**](04-deployment)
- [**Monitoramento de Modelos**](05-monitoring)

---

## Configuração do Ambiente de Tracking com MLflow

O MLflow oferece suporte a diversos cenários de acompanhamento para fluxos de trabalho de ML. O ambiente de tracking do MLflow é composto por:

- **APIs de Tracking do MLflow**
- **Backend Store**
- **Artifact Store**
- **MLflow Tracking Server**

Ao configurar corretamente esses componentes, é possível criar um ambiente robusto e escalável para o desenvolvimento colaborativo de modelos. O diagrama e a tabela a seguir ilustram algumas arquiteturas comuns para ambientes de tracking com MLflow.

<!-- Substitua o link abaixo pelo URL direto de uma imagem (por exemplo, .png, .jpg) hospedada em um repositório ou serviço de imagens -->
![Arquiteturas de Tracking com MLflow](https://private-user-images.githubusercontent.com/13219648/454181122-db260424-beab-4950-91f4-c72bea104153.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NDk2OTM1MTUsIm5iZiI6MTc0OTY5MzIxNSwicGF0aCI6Ii8xMzIxOTY0OC80NTQxODExMjItZGIyNjA0MjQtYmVhYi00OTUwLTkxZjQtYzcyYmVhMTA0MTUzLnBuZz9YLUFtei1BbGdvcml0aG09QVdTNC1ITUFDLVNIQTI1NiZYLUFtei1DcmVkZW50aWFsPUFLSUFWQ09EWUxTQTUzUFFLNFpBJTJGMjAyNTA2MTIlMkZ1cy1lYXN0LTElMkZzMyUyRmF3czRfcmVxdWVzdCZYLUFtei1EYXRlPTIwMjUwNjEyVDAxNTMzNVomWC1BbXotRXhwaXJlcz0zMDAmWC1BbXotU2lnbmF0dXJlPTA2NzJhZjY1ZmE4OWFlOTVjZjIwNmRkODg1ZDA2Y2I2NTVlMzY4Y2MwMDcwZTE3OWEwOGRmZjRlNjcyODgxNzgmWC1BbXotU2lnbmVkSGVhZGVycz1ob3N0In0.07hLtF20juqJ9U8WN7ujZZp0_RiZgf3vw7cjPymRkJs)

| Cenário         | Localhost (padrão)                                                                                                                                                                                                                                                                                                                                 | Rastreamento local com banco de dados local                                                                                                                                                                                                                                                                                                                                 | Rastreamento remoto com o servidor de rastreamento MLflow                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Desenvolvimento** | Desenvolvimento solo                                                                                                                                                                                                                                                                                                                               | Desenvolvimento solo                                                                                                                                                                                                                                                                          | Desenvolvimento de equipe                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **Caso de uso**     | Por padrão, o MLflow registra metadados e artefatos para cada execução em um diretório local (`mlruns`). Essa é a maneira mais simples de começar a usar o MLflow Tracking, sem configurar nenhum servidor externo, banco de dados e armazenamento.                                                        | O cliente MLflow pode fazer interface com um banco de dados compatível com SQLAlchemy (por exemplo, SQLite, PostgreSQL, MySQL) para o back-end. Salvar metadados em um banco de dados permite que você gerencie os dados do experimento de forma mais limpa, ignorando o esforço de configurar um servidor. | O Servidor de Rastreamento do MLflow pode ser configurado com um proxy HTTP de artefatos, passando solicitações de artefato pelo servidor de rastreamento para armazenar e recuperar artefatos sem precisar interagir com os serviços de armazenamento de objetos subjacentes. Isso é particularmente útil para cenários de desenvolvimento de equipe em que você deseja armazenar artefatos e experimentar metadados em um local compartilhado com controle de acesso adequado. |
|
                

