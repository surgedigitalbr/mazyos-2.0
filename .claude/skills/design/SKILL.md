---
name: design
description: >
  Desenha e constrói interfaces premium que NÃO têm cara de IA — sites institucionais,
  landing pages, e-commerce, SaaS, micro-SaaS, dashboards e telas mobile. Define a direção
  visual (estética por tipo de negócio, paleta a partir da logo do cliente, tipografia, tokens,
  motion) e gera o código pronto pra deploy. Extrai o DNA visual de uma referência (link de
  Dribbble/Behance/Awwwards ou print) e aplica nas cores do cliente. Use sempre que for criar,
  redesenhar ou melhorar qualquer interface, site, página, app, dashboard ou identidade visual de
  tela — mesmo que o usuário não diga "design", só "vamos montar o site / a tela / o painel".
---

# /design — Direção de arte + construção de interface (anti-cara-de-IA)

A skill que garante que tudo que a Surge entrega pareça **feito à mão por um estúdio premium**, não cuspido por IA. Vale pra site, landing, e-commerce, SaaS, micro-SaaS, dashboard e mobile. O coração é uma regra só: **decisão deliberada e extrema ANTES de codar** — a IA, sozinha, converge pra média (o "look de Lovable"). Essa skill força sair da média.

## Dependências

- **Marca do CLIENTE:** `identidade/design-guide.md` — ler antes de qualquer visual. É a marca do cliente que vale aqui (não a da Surge).
- **Logo do cliente:** `identidade/logo.*` — fonte da paleta quando existir.
- **Contexto:** `_memoria/empresa.md` (tipo de negócio, público), `_memoria/preferencias.md` (tom).
- **Copy:** quando a tela tiver texto de venda, acionar `/copy` em vez de inventar texto solto.
- **Imagem:** fotos/ilustrações/logo via `/gerar-imagem`.
- **Deploy:** ao terminar, `/deploy` sobe na Vercel.
- **Arsenal de craft (skills globais):** esta skill é a **orquestradora** — define direção, marca e contexto. A execução visual fina puxa a skill de craft certa (ver "Arsenal de craft" abaixo). Sempre passar a marca do cliente + o `DESIGN.md` pra elas; nunca deixar a skill de craft escolher cor/identidade sozinha.

---

## Regra mestra: escolher UMA estética antes de codar

Nunca começar pelo código. Primeiro definir a direção e registrar num `DESIGN.md` na raiz do projeto/site. Sem esse passo, sai genérico.

**Escolher UMA família estética** (não misturar, não fazer a média), casada com o tipo de negócio:

- **Editorial / revista** — tipografia forte, grid suíço, muito respiro. (institucional sério, advocacia, consultoria)
- **Minimalismo refinado** — pouco elemento, espaçamento obsessivo, um detalhe marcante. (premium, clínica estética, arquitetura)
- **Brutalismo premium** — bordas duras, componentes "físicos"/engenhados, cru mas preciso. (tech, dev tools, marca jovem ousada)
- **Maximalismo / aspiracional** — cor dominante forte, motion elaborado, presença. (lançamento, infoproduto, moda)
- **Quente / orgânico** — tons terrosos, formas biomórficas, humano. (gastronomia, bem-estar, marca pessoal)
- **Data-dense pro** — denso, numerais tabulares, alto contraste. (SaaS, dashboard, fintech)

Nomear em uma frase **"a única coisa que a pessoa vai lembrar desse site"**. Se não der pra nomear, a direção ainda está na média — refazer.

## O que está PROIBIDO (impressões digitais de site-de-IA)

Banir, sempre:

- **Fontes:** Inter, Roboto, Arial, system-ui e **Space Grotesk** como fonte principal — são os defaults que entregam IA. (Inter/Roboto podem aparecer só em corpo de UI muito funcional, nunca como assinatura.)
- **Cor:** gradiente roxo/violeta sobre branco ou dark; o "Tailwind blue" (`blue-500/600`) como cor da marca; um mesmo accent reaproveitado em CTA + título + foco.
- **Layout:** a sequência clichê `hero → 3 cards → depoimentos → preço → CTA`; grid de 3 colunas no hero; tudo centralizado.
- **Detalhes:** emoji como ícone; pilha de ícones default do Lucide; bolinha "live" piscando; barrinha de accent à esquerda de todo card; "sopa de container" (pill dentro de card dentro de card, cada um somando padding).
- **Textura:** fundo sólido chapado sem atmosfera; cantos arredondados + sombra suave em tudo (soft-UI corporativo, datado).

## Princípios que substituem o genérico

- **Tipografia com assinatura:** parear um *display distintivo* + um *corpo refinado*. Headline com tracking apertado, tamanho ousado como elemento gráfico. Shortlist premium (Fontshare/variáveis, self-host): display → Clash Display, Syne, Fraunces; corpo/UI → Satoshi, General Sans, DM Sans, Geist, Hanken Grotesk; serif → Fraunces, Spectral, Lora; mono → JetBrains Mono, Geist Mono.
- **Cor disciplinada:** **uma cor dominante + no máximo 2 accents afiados.** Paleta não distribuída por igual. Derivar da **logo do cliente** (ver abaixo).
- **Composição espacial:** assimetria, sobreposição, fluxo diagonal, quebrar o grid centralizado em pelo menos uma seção. Respiro generoso OU densidade controlada — escolher um.
- **Fundo = atmosfera:** grão/noise, mesh gradient, padrão geométrico, transparências em camada, sombra dramática — nunca preenchimento chapado.
- **Motion com intenção:** **um** carregamento de página bem orquestrado (revelação em cascata com `animation-delay`) entrega mais do que micro-interação espalhada. Animar só `transform`/`opacity`. Preferir CSS scroll-driven (`animation-timeline: scroll()/view()`) e View Transitions API antes de puxar JS; GSAP + ScrollTrigger só pra timeline complexa.
- **Complexidade casada com a visão:** maximalista → animação elaborada; minimalista → precisão obsessiva de espaço e tipo.

## Arsenal de craft (skills globais — puxar a certa pelo caso)

A direção e a marca saem desta skill; a **execução fina** delega pra uma skill de craft global já instalada. Não montar "na mão" o que uma dessas faz melhor. **Escolher pela necessidade** (combinam entre si — ex: gerar referência → construir → revisar):

- **`impeccable`** — o cavalo de batalha. Construir/redesenhar/polir qualquer interface premium, dashboard, app, landing, componente. Default da maioria das entregas de front.
- **`taste-skill`** — landing page / portfólio / redesign anti-genérico, com check pré-voo. Quando o medo é "ficar com cara de template".
- **`redesign-skill`** — subir um site/app **existente** pra nível premium sem quebrar função. Usar quando o cliente já tem site.
- **`soft-skill`** — quando precisa parecer **caro/agência de ponta**: fontes, espaçamento, sombras, cards e animações que passam valor; bloqueia os defaults baratos.
- **`gpt-tasteskill`** — **efeitos e motion fortes**: GSAP ScrollTrigger (pin, stack, scrub), tipografia editorial larga, bento gaplessm, micro-imagens inline. Pros sites "mais fodas com efeitos lindos".
- **`brutalist-skill`** — família brutalista/Swiss/terminal (tech, dev tool, marca ousada).
- **`minimalist-skill`** — família editorial limpa, monocromático quente, sem gradiente/sombra pesada.
- **`image-to-code-skill`** — quando vale **ver antes de construir**: gera a imagem do design, analisa e implementa batendo com ela. Bom pra tarefa visualmente crítica.
- **`imagegen-frontend-web`** — gerar **referência visual por seção** (1 imagem por seção) antes de codar a landing/site.
- **`imagegen-frontend-mobile`** — conceito de telas de **app mobile** (iOS/Android) em mockup.
- **`brandkit`** — board de **identidade/brand guidelines**, sistema de logo, deck de marca.
- **`output-skill`** — ligar em **código longo** pra não truncar (página inteira, muitos componentes).

Mapa rápido família estética → skill: *minimalismo refinado* → `minimalist-skill`/`soft-skill`; *brutalismo* → `brutalist-skill`; *maximalismo + efeito* → `gpt-tasteskill`; *redesign de site existente* → `redesign-skill`; *qualquer build premium* → `impeccable` (+ `taste-skill` no pré-voo). Sempre alimentar a skill de craft com a paleta OKLCH do cliente e o `DESIGN.md` — a marca é nossa, o craft é delas.

## Paleta a partir da logo (OKLCH)

1. Ler a logo do cliente (`identidade/logo.*`). Extrair as cores de marca.
2. Construir escalas tonais 0–100 em **OKLCH**, segurando hue/chroma e variando só a Lightness — assim o contraste fica estável e acessível (WCAG 2.2: 4.5:1 corpo, 3:1 grande/UI).
3. Definir uma dominante + 1–2 accents. Se o cliente não tem logo e quer uma, gerar identidade do zero (logo em **SVG via Recraft** pelo `/gerar-imagem`).
4. Emitir tokens (cor/espaço/tipo) e plugar no `@theme` do Tailwind v4. Espaçamento em grid de 8pt; tipo fluido com `clamp()`.

## Extrator de referência (link ou print)

Quando o usuário trouxer uma referência (link de Dribbble/Behance/Awwwards/Pinterest, ou um print colado):

1. Ler a referência (WebFetch no link; ou analisar a imagem do print).
2. Extrair o **DNA**, não os pixels: estrutura/grid, ritmo de espaçamento, peso e pareamento tipográfico, uso de motion, densidade, "personalidade".
3. **Aplicar nas cores do CLIENTE** — nunca copiar a paleta da referência. O layout/linguagem pode ser o mesmo; a cor é sempre a do cliente.
4. Registrar no `DESIGN.md`: "referência X → herdamos isto, trocamos aquilo".

Nunca clonar 1:1 um site existente de terceiro. Inspiração estrutural, identidade própria.

## Stack de construção (pensar por projeto, nunca cravar)

**Não existe stack obrigatório.** A IA decide o que fica melhor PRA AQUELE projeto — e pode ser algo fora desta lista. Estas são tendências como ponto de partida, não regras:

- **Site institucional / landing / blog / local** → costuma pedir **Astro** (quase zero JS, LCP rápido, hospedagem barata) ou **HTML puro** numa one-page simples.
- **App / dashboard / SaaS / micro-SaaS com login** → costuma pedir **Next.js + Supabase** (auth, Postgres, storage, realtime) + Stripe.
- **Loja** → **Shopify** (rápido pra PME), **headless Shopify** (front livre + checkout Shopify), **WooCommerce/WordPress** (pesado em conteúdo), ou custom.
- Quando usar framework: **shadcn/ui** re-tokenizado (nunca stock) + toques de Aceternity/Magic UI no hero. Hospedagem geralmente **Vercel**.

Raciocinar a partir do que o negócio precisa: vitrine ou ferramenta com login? orçamento? quem vai manter? o cliente já tem WordPress? Em dúvida, propor uma opção com o porquê e deixar o usuário decidir — ele coordena.

---

## Workflow

### Passo 1 — Direção (DESIGN.md)
Ler marca do cliente + logo + tipo de negócio. Escolher a família estética, a tipografia, a paleta OKLCH (da logo), o stack. Se houver referência, rodar o extrator. Escrever `DESIGN.md` com: estética escolhida + "a única coisa memorável", fontes, tokens de cor/espaço/tipo, decisões de motion, stack. **Mostrar a direção pro usuário antes de codar.**

### Passo 2 — Estrutura
Definir as seções/telas a partir do objetivo (e da intenção de busca, se for página que precisa rankear — alinhar com `/seo` e `/copy`). Fugir da sequência clichê. Wireframe textual rápido.

### Passo 3 — Construção
Codar no stack escolhido aplicando os tokens. Texto de venda vem do `/copy` (não inventar). Imagens via `/gerar-imagem`. Acessibilidade desde o início (contraste, teclado, alt, mobile-first — crítico em saúde/clínica).

### Passo 4 — Revisão
Rodar uma passada de revisão visual + acessibilidade (Playwright/`/webapp-testing` quando disponível): layout em mobile e desktop, contraste, estados (hover/focus/empty/erro). Conferir contra a lista de PROIBIDO — se caiu em qualquer fingerprint de IA, corrigir.

**Lint anti-slop determinístico (sem custo):** rodar `npx impeccable detect <pasta-ou-arquivo>` (ou `npx impeccable detect <url>`) — pega 24 fingerprints de IA (borda lateral em card, gradiente roxo, easing bounce, glow escuro, linha longa demais, padding apertado, touch target pequeno, heading pulado…) sem LLM nem API key. Corrigir o que apontar. Pra revisão de design mais profunda, acionar a skill **`impeccable`** (`/impeccable audit` técnico, `/impeccable critique` de UX, `/impeccable polish` antes de entregar).

### Passo 5 — Entrega
Mostrar telas-chave renderizadas. Salvar o projeto na pasta certa. Oferecer `/deploy` pra subir na Vercel.

---

## Regras

- Sempre escrever `DESIGN.md` antes de codar. Direção primeiro, código depois.
- Marca do cliente sempre (`identidade/design-guide.md` + logo). A marca da Surge (`identidade/surge.md`) é só pra proposta/pitch, nunca pra entrega do cliente.
- Conferir contra a lista de PROIBIDO em toda entrega.
- Cor sempre do cliente, mesmo quando o layout vem de referência.
- Logo/ícone de cliente = SVG (Recraft), nunca raster.
- Não usar a sequência de seções clichê. Quebrar o grid em ao menos uma seção.
- Acessibilidade não é opcional (WCAG 2.2). Mobile-first.
- Animar só `transform`/`opacity`. CSS scroll-timeline/View Transitions antes de JS.
- Nível de capricho proporcional ao projeto: nem todo cliente é Awwwards. Restaurante de bairro = feijão-com-arroz bem-feito e bonito. Tech/premium = pode soltar a mão.
