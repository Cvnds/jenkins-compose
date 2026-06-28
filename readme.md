# Jenkins - Docker Compose

## O que é

O Jenkins é um servidor de **CI/CD (Continuous Integration / Continuous Delivery)** utilizado para automatizar tarefas do ciclo de desenvolvimento de software, como:

* Compilar projetos;
* Executar testes;
* Gerar artefatos;
* Construir imagens Docker;
* Publicar aplicações;
* Executar deploys.

Essas automações são definidas em um **Pipeline**, normalmente através de um arquivo `Jenkinsfile` versionado junto ao código-fonte.

---

## Instalação

### 1. Clone o repositório

```bash
git clone https://github.com/<usuario>/<repositorio>.git
cd <repositorio>
```

### 2. Configure as variáveis de ambiente

Crie o arquivo `.env` a partir do template:

```bash
cp .env_template .env
```

Edite as variáveis conforme necessário.

### 3. Inicie os containers

```bash
docker compose up -d --build
```

A interface do Jenkins estará disponível em:

```
http://localhost:8080
```

### 4. Configuração inicial

Na primeira execução:

1. Selecione **Install suggested plugins**.
2. Crie o usuário administrador.
3. Faça login.

Após essa etapa, o Jenkins estará pronto para uso.

---

## Docker

Esta imagem possui a Docker CLI instalada e acesso ao Docker do host através do `docker.sock`.

Isso permite que os pipelines criem containers temporários para executar builds, testes e outras tarefas de CI sem a necessidade de executar Docker-in-Docker (DinD).

Essa configuração é recomendada para ambientes em que o Jenkins é executado em um host confiável.
