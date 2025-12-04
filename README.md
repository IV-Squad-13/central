# Squad 13 – Jotanunes

Repositório central da aplicação desenvolvida pelo **Squad 13** durante a Residência de Software IV.  
Aqui estão reunidos todos os artefatos produzidos pela equipe, incluindo os **submódulos** que compõem o ecossistema completo da aplicação.

---

# Descrição Geral

O **Sistema de Especificações e Catálogo da Construtora Jotanunes** é uma plataforma web desenvolvida para a gestão centralizada de **Documentos de Especificação Técnica**.

Seu objetivo é **padronizar, digitalizar e organizar** as informações técnicas das obras, tornando o fluxo entre engenharia, arquitetura e áreas administrativas **mais ágil, seguro e rastreável**.

---

# Principais Funcionalidades

- Login, autenticação e controle de permissões.  
- Gerenciamento do catálogo (ambientes, itens, materiais e marcas).  
- Cadastro e edição de empreendimentos.  
- Administração de usuários e perfis de acesso.

---

# Perfis de Acesso

| Tipo de Usuário | Permissões |
|-----------------|------------|
| **Administrador** | Gerencia usuários, catálogo e especificações. |
| **Gestor**        | Cadastra empreendimentos e materiais. |
| **Redator**       | Cria e edita conteúdos técnicos. |

---

# URLs da Aplicação

- **Frontend**: https://front-drab-eight-75.vercel.app  
- **API Principal (Monolito)**: https://s13.api.br/swagger-ui/index.html  
- **API de Geração de PDF (Kurush)**: https://pdf.s13.api.br  

---

# Docker

A orquestração da infraestrutura local da aplicação é realizada por meio do arquivo `docker-compose.yml`, localizado no submódulo **docker** deste repositório.

Para executar a aplicação via Docker, utilize a estrutura disponível dentro da pasta `/docker`, conforme descrito abaixo.

---

## 1. Clone o repositório central com submódulos

```bash
git clone --recurse-submodules https://github.com/iv-squad-13/central.git
```

Em seguida, acesse o submódulo:

```bash
cd docker
```

---

## 2. Acessando o submódulo de Docker

Caso já tenha clonado o repositório central com submódulos, simplesmente navegue até:

```bash
cd docker
```

---

## 3. Subindo apenas as APIs

Executa os containers essenciais para a API principal e o serviço de geração de PDFs:

```bash
docker compose up -d monolito_api kurush_api
```

---

## 4. Subindo bancos + APIs (setup completo)

Executa toda a stack de infraestrutura, incluindo PostgreSQL, MongoDB e as APIs:

```bash
docker compose up -d mongo_db monolito_db monolito_api kurush_api
```

---

# Build Local (sem Docker)

1. Clone o repositório:  
   ```bash
   git clone --recurse-submodules https://github.com/iv-squad-13/central.git
   ```

2. Entre na pasta `/services` e execute cada serviço:

   **API Monolito (Spring Boot):**
   ```bash
   cd services/api-monolito
   ./mvnw spring-boot:run
   ```

   **API Kurush (Quarkus):**
   ```bash
   cd ../api-kurush
   ./mvnw quarkus:dev
   ```

   *Para instruções adicionais, consulte o README específico de cada serviço.*

---

# Configuração do Frontend

**Requisitos:** Node.js + npm

1. Entre na pasta `FrontEnd-JotaNunes`:
   ```bash
   npm install
   ```

2. Execute o servidor:
   ```bash
   npm run dev
   ```

---

# Tecnologias Utilizadas

| Camada | Tecnologias |
|--------|-------------|
| **Frontend** | React · Vite · Tailwind · TypeScript |
| **Backend** | Java · Spring Boot · Quarkus |
| **Banco de Dados** | PostgreSQL · MongoDB |
| **Ambiente** | Docker · Docker Compose |
| **Versionamento** | Git · GitHub |
| **Documentação API** | Swagger UI |

---

# Estrutura do Projeto

```
/central
 ├── /services
 │      ├── api-monolito       # API principal (Spring Boot)
 │      └── api-kurush         # API de PDFs (Quarkus)
 ├── /FrontEnd-JotaNunes        # Interface Web (React)
 ├── /docker                    # Arquivos Docker Compose
 └── README.md
```

---

# Equipe de Desenvolvimento

- Daniel de Oliveira Mendonça Mota – Front-end  
- Fábio Tarcísio Cardoso Moura – Back-end  
- Rafael Gonçalvez Menezes – Back-end  
- Anthony Yuri Feitosa França – Back-end  
- Marcelo Gomes Alves – Apoio Geral  

---
