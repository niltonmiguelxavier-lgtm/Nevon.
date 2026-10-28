# Nevon Pay

Gateway de pagamentos em desenvolvimento para comerciantes e negócios em Moçambique.

## Run & Operate

- `artifacts/nevon-pay: web` — run the Next.js application in the Replit preview
- `pnpm --filter @workspace/nevon-pay run typecheck` — typecheck the imported app
- `pnpm --filter @workspace/nevon-pay run db:push` — apply its Prisma schema to the development database
- `pnpm --filter @workspace/api-server run dev` — run the shared API health endpoint
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- Required env: `DATABASE_URL` — PostgreSQL connection string, provided by Replit

## Stack

- pnpm workspace, Node.js 24, TypeScript
- Aplicação: Next.js 15, React 19
- DB: PostgreSQL + Prisma
- Validação: Zod

## Where things live

- `artifacts/nevon-pay/app/` — páginas Next.js e rotas da API
- `artifacts/nevon-pay/prisma/schema.prisma` — modelo PostgreSQL
- `artifacts/nevon-pay/lib/` — provedores, segurança e acesso à base de dados
- `artifacts/nevon-pay/docs/` — documentação dos capítulos 1–18

## Architecture decisions

- O Nevon Pay mantém a estrutura Next.js entregue no ZIP, em vez de converter a aplicação para React/Vite.
- e-Mola e M-Pesa estão apenas preparados como provedores; não há ligação financeira real sem credenciais, aprovação e validação dos provedores.
- Pagamentos reais não devem ser simulados como concluídos; o provedor incluído é apenas sandbox.

## Product

Base de gateway de pagamentos com checkout, API versionada e arquitetura multi-provedor.

## User preferences

- Importar e executar a aplicação fornecida sem trocar o framework original.

## Gotchas

- `DATABASE_URL` é necessário para as rotas que consultam ou alteram dados; a rota de saúde em `/api/health` verifica também a ligação PostgreSQL.
- Preparar a base local com `pnpm --filter @workspace/nevon-pay run db:push` após gerar o Prisma Client.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
