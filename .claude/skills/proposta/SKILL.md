---
name: proposta
description: >
  Monta uma proposta comercial / orçamento da Surge Digital pra um cliente ou prospect — um PDF
  bonito com a marca da SURGE (não do cliente), formato "cardápio": diagnóstico da brecha, o que
  a Surge entrega, escopo, bônus, preço e próximo passo. Cobre as três abordagens: proposta antes
  de construir, modelo-isca pra impressionar, e pitch de call. Use quando o usuário disser
  "proposta", "orçamento", "monta a oferta pro cliente X", "vou abordar esse lead", ou pedir um PDF
  comercial.
---

# /proposta — Proposta comercial da Surge

A proposta sai com a cara da **Surge Digital**, não do cliente. É a peça que fecha venda.

## Dependências

- **Marca da SURGE:** `identidade/surge.md` + `identidade/surge-logo.*` — usar ESTA, nunca a do cliente.
- **Contexto do cliente:** `_memoria/empresa.md`, `_memoria/estrategia.md` (a brecha, de `/briefing-cliente`).
- **Formato flexível:** geralmente um `index.html` estilizado (A4) que você salva como PDF, ou PDF direto via Playwright — o que ficar melhor pro caso. Sempre com **CAPA**.
- **Saída:** `propostas/<cliente>-<YYYY-MM-DD>.{html,pdf}`.
- **Craft externo a puxar pela tarefa** (a `/proposta` lidera; essas dão profundidade):
  - `pricing` — quando o "Investimento" tiver múltiplos pacotes ou modelo de preço a validar (ancoragem, value metric, mensal × anual): estruturar o preço antes de escrever a oferta.
  - `sales-enablement` — quando o cliente for da Surge e a venda precisar de material de apoio (one-pager, quebra de objeção, talk track) além do PDF.
  - `pptx` / `pdf` — pra gerar o deck do pitch de call (abordagem 3) ou exportar o documento final com qualidade.

## As três abordagens (perguntar qual, se não estiver claro)

1. **Proposta antes de construir** — você descreve a brecha, eu monto o PDF "cardápio" e você manda no WhatsApp.
2. **Modelo-isca** — antes da proposta, montar algo rápido pra impressionar (um modelo de site/tela com `/design`, ou imagens com `/gerar-imagem`) e anexar/mostrar. "Olha, já fiz um modelo pra você."
3. **Pitch de call** — material enxuto pra apresentar ao vivo numa reunião.

## Estrutura do PDF (formato cardápio)

1. **Capa** — logo Surge, nome do cliente, "Proposta de [serviço]", data.
2. **Diagnóstico** — a brecha do cliente, em 2-3 frases diretas (puxa de `_memoria/estrategia.md`). Mostra que você entendeu o negócio dele.
3. **A solução** — o que a Surge vai fazer e por quê (resultado, não só tarefa). Conectar com `/copy` pra essa parte vender.
4. **Escopo / o cardápio** — itens entregues, claros. Se houver pacotes, ancorar um recomendado.
5. **Bônus** — o que vai junto (ex: GMB, 1 mês de carrossel, ajuste de SEO).
6. **Investimento** — preço por pacote/escopo. Enquadrar contra o valor/ROI, não solto.
7. **Próximo passo** — uma ação clara (responder no WhatsApp, agendar, aprovar) + contato da Surge.

## Workflow

1. Confirmar a abordagem (1/2/3) e ler a marca da Surge + a brecha do cliente.
2. Se faltar dado do cliente, puxar de `/briefing-cliente` ou perguntar o essencial (serviço, preço, prazo).
3. Escrever o conteúdo (diagnóstico + solução + escopo + bônus + preço) — copy que vende, na voz da Surge.
4. Montar `proposta.html` com a identidade da Surge (cores, fonte, logo). Design limpo e premium — aplicar os princípios de `/design`, sem cara de IA.
5. Renderizar em PDF (Playwright). Mostrar pro usuário antes de finalizar.
6. Salvar em `propostas/<cliente>-<data>.pdf`. Oferecer rascunhar a mensagem de WhatsApp de envio (`/email-profissional` adaptado).

## Regras

- Marca da Surge sempre (`identidade/surge.md`). Se estiver em branco, parar e pedir pro Guilherme preencher (cores, logo, contato).
- Preço nunca inventado — perguntar ou usar a faixa que o usuário definir.
- Diagnóstico específico do cliente, não genérico — é o que mostra que a Surge entendeu o negócio.
- PDF premium, não template de IA. Aplicar os princípios anti-genérico de `/design`.
- Uma ação clara no fim. Sem enrolação.
