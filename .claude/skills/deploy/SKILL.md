---
name: deploy
description: >
  Publica um site ou app (Astro ou Next.js) do repositório local pra Vercel — GitHub → Vercel →
  domínio próprio. Conecta o repo, faz o deploy de produção e aponta os registros de DNS do domínio
  do cliente. Use sempre que o usuário quiser publicar, subir, colocar no ar, "deployar", lançar um
  site/app, ou conectar um domínio — e mencione Vercel ou Cloudflare Pages.
---

# /deploy — Publicar na Vercel

Leva o projeto do local pro ar. Padrão: GitHub → Vercel (push-to-deploy) → domínio.

## Pré-requisitos

- Projeto construído (Astro `dist/` ou Next.js) — geralmente vindo de `/design`.
- `gh` CLI autenticado e `vercel` CLI (`npm i -g vercel`).
- Repo do cliente no GitHub da Surge (ver `/salvar`).

## Workflow

### Passo 0 — Tirar onda antes de subir (puxar craft)
Antes do build de produção:
- **Se for Next.js/React:** puxar a skill externa `vercel-react-best-practices` pra auditar performance (waterfalls, bundle, re-render, ISR/Server Components, Image Optimization). Subir sem otimizar é deixar dinheiro na mesa.
- **QA:** puxar `playwright-cli` pra testar os fluxos críticos (formulário envia, checkout abre, links não quebram) **antes** de virar produção, não depois.

### Passo 1 — Build local
Detectar o framework. Astro → `astro build` (saída `dist/`). Next.js → `next build`. Conferir que builda sem erro antes de subir.

### Passo 2 — Repo no GitHub
```bash
git init && git add -A && git commit -m "init"
gh repo create <nome-cliente> --private --source=. --push
```
(Se o repo já existe, só commit + push.)

### Passo 3 — Vercel
Caminho recomendado (integração Git, deploy automático a cada push):
- Importar o repo no painel da Vercel → detecta Astro/Next sozinho.

Ou via CLI:
```bash
vercel login
vercel link
vercel --prod
```

### Passo 4 — Domínio
```bash
vercel domains add exemplo.com.br
vercel domains inspect exemplo.com.br   # mostra os registros A/CNAME exatos
```
Passar pro cliente os registros exatos pra ele apontar no registrador (apex → A; www → CNAME).

### Passo 5 — Confirmar
Validar que o site responde 200 na URL de produção. Entregar a URL.

## Alternativa — Cloudflare Pages
Quando o cliente já usa Cloudflare DNS ou precisa de Workers/edge:
```bash
npm i -g wrangler
wrangler pages deploy ./dist --project-name=<nome>
```

## Regras

- Next.js → preferir Vercel (recursos first-party: ISR, server actions, image opt). Astro → Vercel ou Cloudflare, tanto faz.
- Repo do cliente sempre privado por padrão.
- Variáveis de ambiente (Supabase, Stripe, APIs) configurar na Vercel, nunca commitar `.env`.
- Nunca `--force` sem o usuário pedir.
- Cada cliente = um repo = um projeto Vercel. Não misturar.
