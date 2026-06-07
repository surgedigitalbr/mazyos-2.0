---
name: briefing-cliente
description: >
  Transforma a transcrição de uma call (ou anotações) com o cliente num perfil estruturado e
  atualiza a memória do projeto. Lê o arquivo solto, extrai as dores, o que o cliente quer, o
  negócio, público, prazos e a brecha a resolver, e grava em _memoria/empresa.md e estrategia.md.
  Use quando o usuário jogar uma transcrição/gravação/anotação de reunião na pasta dados/ ou disser
  "tenho a call do cliente", "processa esse briefing", "li a reunião do cliente X", ou no começo de
  um projeto novo.
---

# /briefing-cliente — Da call do cliente pra memória

A porta de entrada de cada projeto. Você grava a call, transcreve, joga em `dados/` — esta skill lê e monta o cérebro do projeto.

## Dependências

- **Entrada:** transcrição/anotação em `dados/` (txt, md, pdf, docx). Aceita também print/áudio transcrito.
- **Saída:** `_memoria/empresa.md`, `_memoria/estrategia.md`, `identidade/design-guide.md` (se cores/logo aparecerem).

## Workflow

### Passo 1 — Ler a entrada
Ler o arquivo em `dados/` (ou o que o usuário apontar). Se for PDF/DOCX, extrair o texto.

### Passo 2 — Extrair
Identificar e organizar:
- **Negócio:** o que o cliente faz, há quanto tempo, porte, região.
- **Público:** quem compra dele, a linguagem que ele e os clientes dele usam (guardar pra `/copy`/VoC).
- **A brecha (o ouro):** o que está pegando — site ruim/inexistente, processo manual pesado, sem tráfego, Instagram fraco, sem dashboard, etc. O que dá pra resolver com IA/tech/marketing.
- **O que o cliente quer** (dito) vs **o que ele precisa** (diagnóstico) — anotar os dois.
- **Ativos:** já tem site? logo? cores? redes? (puxar pra identidade).
- **Restrições:** orçamento, prazo, preferências, o que evitar.
- **Próximos passos / combinados da call.**

### Passo 3 — Gravar na memória
- `_memoria/empresa.md` → negócio, público, ativos, serviços.
- `_memoria/estrategia.md` → a brecha priorizada, o que atacar primeiro, prazos.
- `identidade/design-guide.md` → cores/logo se mencionados.
Editar com cirurgia (só as linhas relevantes), mostrar o que vai gravar antes.

### Passo 4 — Devolver o diagnóstico
Resumo curto pro usuário:
```
Cliente: [nome] — [o que faz]
Dor principal: [a brecha]
Quer: [pedido do cliente] | Precisa: [seu diagnóstico]
Ativos: [site/logo/redes que já tem]
Proposta de ataque: [1-2 frases — o que a Surge faz primeiro]
```
Oferecer o próximo passo: `/proposta` (montar oferta), `/design` (já começar um modelo), ou `/seo`/`/carrossel` conforme a brecha.

## Regras

- Não inventar — registrar só o que está na transcrição. O que for dedução sua, marcar como hipótese.
- Separar sempre "o que o cliente disse que quer" de "o que ele precisa".
- A transcrição é entrada, não artefato final — o que importa vira memória; a transcrição pode ficar em `dados/`.
- Cada cliente = um projeto/pasta. Não misturar contexto de clientes diferentes na mesma memória.
