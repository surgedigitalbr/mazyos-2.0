# MazyOS 2.0

> O sistema operacional do seu negócio dentro do Claude Code. Versão Surge Digital.

Você acaba de instalar o MazyOS. Em alguns minutos, o projeto vai ter uma
memória própria, a identidade visual aplicada em tudo que o sistema gerar,
e **47 skills** prontas — 23 da operação MazyOS (design, copy, marketing,
SEO, ads, propostas) **+ um arsenal de craft** que elas puxam sozinhas
(design premium, backend, pagamento, documentos, QA) — pra tudo rodar com
você dirigindo.

Bora voar.

---

## Ligando o sistema

A ideia: **um projeto = uma pasta = um repositório**. Pra cada cliente ou
iniciativa, você cria uma pasta com o nome dele e instala o MazyOS na raiz.

### Pelo Claude (mais rápido)

1. Cria uma pasta com o nome do projeto/cliente e abre ela (vazia) no VS Code.
2. No terminal integrado, roda `claude` e cola:

```
Clona o https://github.com/surgedigitalbr/mazyos-2.0.git na raiz dessa pasta e roda o /instalar.
```

Clonar **na raiz** é o que faz todas as 47 skills funcionarem — tanto no
modo manual (`/design`, `/seo`, `/proposta`...) quanto no roteamento
automático (você só descreve o que quer e ele aciona a skill certa). O molde
já vem **completo**: clonou, tem tudo — em qualquer máquina.

### Pelo terminal (mais previsível)

```bash
# dentro da pasta vazia do projeto:
git clone https://github.com/surgedigitalbr/mazyos-2.0.git .
code .
```

Na janela do VS Code: terminal integrado → `claude` → `/instalar`.

---

O `/instalar` roda uma vez só, no começo de cada projeto. Te entrevista
sobre o cliente/negócio, monta a memória e configura o sistema. Depois
disso, é só conversar e construir.

> Cada projeto é um repositório próprio. O primeiro `/salvar` desacopla do
> molde e manda pro repo daquele cliente no seu GitHub — limpo, isolado,
> pronto pra Vercel puxar e colocar no ar.

---

## O sistema — as 23 skills MazyOS (a linha de frente)

**Você não decora comando.** Conversa. Descreve o que quer e o MazyOS
aciona o que precisa (às vezes várias skills juntas). Os `/comandos`
abaixo são atalho opcional. Rode `/ajuda` a qualquer momento pra ver tudo.

> Essas 23 são a **porta de entrada** de toda entrega: carregam a marca do
> cliente, o contexto do negócio e a regra das duas identidades. Por baixo
> delas roda o **arsenal de craft** (mais abaixo), que elas puxam sozinhas.

**Núcleo** — operar o dia a dia
`/abrir` carrega o contexto e diz onde paramos · `/atualizar` varre o
projeto e grava a memória (inclusive o estado do trabalho, pra próxima
janela retomar) · `/salvar` commit + push no repo do cliente ·
`/novo-projeto` cria pasta isolada · `/briefing-cliente` lê a transcrição
da call e monta o perfil do cliente · `/mapear-rotinas` transforma o que
você repete em skill · `/ajuda` mostra tudo que o sistema faz.

**Construção** — onde o projeto nasce
`/design` cria site, SaaS, micro-SaaS, dashboard e mobile premium, sem
cara de IA (estética por tipo de negócio, paleta a partir da logo do
cliente, extrator de referência por link ou print) · `/copy` escreve
texto que vende com a estrutura certa (Schwartz: consciência ×
sofisticação) · `/gerar-imagem` foto, criativo e logo em SVG com o melhor
modelo por caso · `/deploy` sobe na Vercel + domínio.

**Conteúdo e SEO** — vitrine pública da empresa
`/carrossel` carrosséis 1080×1350 com a marca · `/reels` roteiro + vídeo
curto + legenda · `/publicar-tema` um tema vira artigo de blog + carrossel
+ 3 legendas amarradas · `/seo` fluxo completo de 8 passos (demanda,
concorrência, GMB, on-page, conteúdo, ads, monitoramento, GEO) ·
`/responder-avaliacoes` respostas humanas pras reviews do Google ·
`/aprovar-post` publica blog + Instagram + Facebook num comando.

**Anúncios pagos** — onde o dinheiro entra
`/anuncio-google` monta a campanha inteira em CSV pronto pra importar no
Google Ads Editor · `/relatorio-ads` lê os exports de Google + Meta e
devolve relatório semanal com alertas e recomendações.

**Comercial** — fechar
`/proposta` monta a proposta/orçamento premium com a marca da Surge —
formato cardápio, com capa, pronta pra mandar no WhatsApp.

**Produção** — ferramentas do dia a dia
`/analisar-dados` lê CSV/XLSX/PDF e gera resumo executivo ·
`/email-profissional` rascunha email a partir de contexto livre.

---

## O arsenal — +24 skills de craft que o sistema puxa sozinho

As 23 acima são a linha de frente. Por baixo delas roda um **arsenal de
execução** que elas acionam automaticamente conforme a tarefa pede — você
nunca precisa chamar. São **47 skills no total**, e tudo vem no clone.

**Craft de design/front** (o `/design` orquestra) — `impeccable` (build
premium + auditoria, 23 comandos e detector anti-IA), `taste-skill`
(anti-genérico), `redesign-skill` (subir site existente pra nível premium),
`soft-skill` (cara de agência cara), `gpt-tasteskill` (efeitos e motion GSAP
fortes), `brutalist-skill`, `minimalist-skill`, `image-to-code-skill` (ver o
design antes de construir), `imagegen-frontend-web` / `-mobile` (referência
visual por seção), `brandkit` (identidade e deck de marca), `output-skill`
(código longo sem truncar).

**Capacidade de produto** (SaaS, micro-SaaS, loja) — `supabase` (auth, banco,
storage), `supabase-postgres-best-practices` (query, RLS, schema, índices),
`stripe-best-practices` (pagamento e checkout), `vercel-react-best-practices`
(performance React/Next), `playwright-cli` (QA do site antes de subir).

**Documentos** — `pdf`, `docx`, `pptx` pra proposta, contrato, ebook e slides.
**Meta** — `skill-creator` (criar e evoluir as próprias skills do MazyOS),
`find-skills`, `baoyu-youtube-transcript`.

> Regra de ouro: skill de craft **nunca** decide marca, cor ou identidade —
> quem manda é sempre o `design-guide.md` do cliente. E skill genérica de
> copy/imagem/vídeo nunca substitui `/copy`, `/gerar-imagem` ou `/reels`,
> que carregam o contexto do negócio.

---

## A tese

IA não é uma ferramenta que sua empresa usa. É o sistema operacional em
que ela roda.

A diferença não é velocidade. É capacidade nova — uma pessoa com IA
constrói o que antes exigia time inteiro. Cada processo crítico que hoje
roda em open loop (decide → executa → não mede → repete cego) vira
closed loop dentro do MazyOS (decide → executa → captura → realimenta →
ajusta sozinho).

O sistema não substitui você. Vira parte da operação.

---

## Como o MazyOS pensa

`_memoria/` é o cérebro. Tudo que importa do projeto mora aqui — quem é o
cliente, como ele fala, o que tá em foco, e onde o trabalho parou. O Claude
lê isso antes de cada resposta. Quanto melhor a memória, melhor o sistema.

`identidade/` é o rosto, com **duas marcas**: a do **cliente**
(`design-guide.md`) vai em toda entrega (site, carrossel, SaaS); a da
**Surge** (`surge.md`) vai só nas propostas e pitches.

`marketing/`, `saidas/` e `scripts/` são o resultado. O sistema produz,
**organiza tudo em pastas** (sem bagunça, sem duplicata), versiona no seu
GitHub e fica tudo seu.

**Segredos ficam de fora.** Chave de API, token e credencial (Supabase,
Stripe, Meta, Google…) são de cada cliente e moram só no `.env` local — o
`.gitignore` já bloqueia. Vai pro repo só um `.env.example` com os nomes das
variáveis; os valores reais entram nas variáveis de ambiente da Vercel.

---

## O loop do dia a dia

Trabalha conversando → quando o chat encher, `/atualizar` (grava onde
paramos) → `/compact` ou `/clear` (comandos nativos do Claude Code) →
janela nova retoma pela memória, sem perder o fio nem queimar token.
`/salvar` versiona tudo no repo do cliente.

Você dirige, o MazyOS é o braço direito: pensa junto, dá ideia, enxerga as
brechas e constrói com você. Quanto mais o projeto anda, mais ele aprende
sobre o cliente — e melhor fica.

---

## Surge Digital

[surgedigital.com.br](https://surgedigital.com.br) · [@surgedigitalbr](https://instagram.com/surgedigitalbr)

*Construído sobre o MazyOS original ([mazzeoia.com.br](https://mazzeoia.com.br)).*
