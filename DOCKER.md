# API em JavaScript — Docker + CI/CD

API de exemplo em Node/Express + Sequelize (app de matches — usuários,
endereços, fotos, interesses, matches, interações, mensagens), usada como base
para o exercício de Docker + CI/CD. Código original de
[profdiegocbcastro/gerencia-de-config](https://github.com/profdiegocbcastro/gerencia-de-config/tree/main/APIs%20para%20exerc%C3%ADcios/api-js),
sem alterações.

## Rodando localmente

```bash
npm install
node index.js
```

Precisa de um `.env` (veja `.env.example`) apontando pra um Postgres.

## Docker

```bash
docker build -t api-js-cicd .
docker run -p 3000:3000 api-js-cicd
```

## Docker Compose (app + PostgreSQL + pgAdmin)

```bash
docker compose up -d --build
```

- API: `http://localhost:3004`
- pgAdmin: `http://localhost:5052`
- PostgreSQL: `localhost:5437`

A aplicação original não roda migrations nem `sync()` no Sequelize — ela
conecta no banco normalmente, mas endpoints que dependem de tabelas retornam
erro até as tabelas existirem.
