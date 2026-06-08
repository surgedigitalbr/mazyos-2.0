---
name: copy
description: >
  Escreve copy de conversão de alto nível pra qualquer superfície — site, landing page, hero,
  página de preço, e-commerce, tela de SaaS/micro-SaaS (botões, onboarding, empty states), anúncio,
  email e legenda. Diagnostica os dois diais do Eugene Schwartz (consciência × sofisticação de
  mercado) antes de escrever, escolhe a estrutura e o nível de agressividade certos, e entrega copy
  + alternativas de headline. Voltada ao negócio do cliente e integrada com SEO/GEO. Use sempre que
  precisar escrever ou melhorar qualquer texto que vende ou guia o usuário — mesmo que o pedido seja
  só "escreve o texto do site / do botão / dessa seção".
---

# /copy — Copy de conversão (a estrutura invisível)

A "estrutura invisível" que faz texto vender são os **dois diais do Eugene Schwartz**. Diagnostica os dois primeiro; tudo o resto (headline, estrutura de página, agressividade) decorre disso. Frameworks universais, output em **português do Brasil**, na voz real do público do cliente.

**Nada é cravado — a IA julga por projeto.** O objetivo da copy muda conforme o caso: copy de site pra rankear no Google é uma coisa, copy de Instagram pra chamar atenção é outra, copy de SaaS pra ativar usuário é outra. Não aplicar uma fórmula fixa igual pra todo cliente — entender o que aquela peça precisa (vender? atrair? educar? converter?), em que canal, e calibrar. Quem conduz é o usuário; o Claude pensa junto, sugere o ângulo e aplica o framework certo. Quanto mais sabe do cliente (memória), melhor a copy.

## Dependências

- **Contexto:** `_memoria/empresa.md` (produto, público, diferencial), `_memoria/preferencias.md` (tom).
- **Cliente:** transcrição da call / briefing (`/briefing-cliente`) — fonte de Voz do Cliente (VoC).
- **SEO:** `marketing/seo/` quando existir (keyword/entidade da página).
- **Design:** quando a copy é pra uma tela, alinhar com `/design` (a copy preenche a estrutura, não o contrário).

---

## Passo 0 — Diagnóstico (sempre antes de escrever)

Levantar 4 camadas. Se faltar alguma, perguntar — não inventar:

1. **Propósito** — tipo da peça (hero, landing, preço, ad, email, onboarding…) + a **única** ação que ela deve gerar.
2. **Público** — quem é, qual a dor, quais as objeções, e **as palavras exatas que ele usa** (VoC: minerar reviews, comentários, transcrição de call).
3. **Produto/oferta** — o mecanismo único, o diferencial, a transformação (antes → depois).
4. **Contexto** — fonte do tráfego + **estágio de consciência** + **estágio de sofisticação**.

---

## Os dois diais do Schwartz (o núcleo)

### Dial 1 — Consciência (o que falar primeiro, e quanto explicar)

| Estágio | O público sabe… | Trabalho da copy | Headline começa por… | Tamanho |
|---|---|---|---|---|
| **1. Inconsciente** | nada, nem que tem o problema | nomear o inimigo / contar história / dar um fato | curiosidade, identidade ("Se você tem uma clínica…") | mais longo |
| **2. Consciente do problema** | sente a dor, não sabe que há solução | agitar a dor, revelar que existe solução | o PROBLEMA, na língua dele | longo |
| **3. Consciente da solução** | sabe que há soluções, não conhece a sua | posicionar seu MECANISMO como o melhor caminho | o RESULTADO desejado | médio |
| **4. Consciente do produto** | conhece o seu, não se convenceu | provar: por que você > alternativas, prova, garantia | seu PRODUTO + a vantagem | curto |
| **5. Mais consciente** | quer, só falta empurrão | liderar com a OFERTA, preço, prazo, bônus | a OFERTA / preço / urgência | mais curto |

Regra de landing (Wiebe): o **topo** da página casa com o anúncio e com o estágio atual; o **restante** move pro próximo estágio. Quanto menos consciente, mais longa a copy.

### Dial 2 — Sofisticação (como tornar a promessa crível)

| Estágio | Estado do mercado | O que ainda funciona |
|---|---|---|
| **1. Pioneiro** | ninguém fez essa promessa | **afirmar a promessa direto.** Simples. |
| **2. Segunda onda** | promessa copiada | **amplificar** (maior, mais rápido, garantido) |
| **3. Era do mecanismo** | ninguém crê mais em "maior" | **introduzir um MECANISMO novo** — o *como* |
| **4. Corrida de mecanismo** | todos têm mecanismo | **elaborar/fortalecer** o seu + muita prova |
| **5. Sofisticação máxima** | mercado saturado e cínico | **mudar pra IDENTIDADE / porquê / marca** |

Diagnóstico: quantos concorrentes fazem a mesma promessa? O público revira o olho pra promessa básica? Todo mundo já tem um "método secreto"? Se sim, subir de estágio.

### A matriz (decisão final)

- **Baixa consciência + baixa sofisticação** → educar + promessa direta e ousada, copy longa. *(comum em PME local / serviço novo na cidade — a melhor oportunidade da Surge)*
- **Baixa consciência + alta sofisticação** → educar + mecanismo/identidade, copy longa. *(o combo mais difícil)*
- **Alta consciência + baixa sofisticação** → fechar rápido na promessa, copy curta.
- **Alta consciência + alta sofisticação** → fechar na diferenciação/identidade + prova empilhada. *(SaaS/nicho disputado, retargeting)*

**Sempre imprimir no topo do entregável: estágio de consciência (1–5) + sofisticação (1–5) + nível de agressividade (1–5), com uma linha de justificativa.**

---

## Frameworks de apoio

- **Espinha por consciência:** PAS (consciente do problema) · StoryBrand/AIDA (longo) · oferta-primeiro (mais consciente). No StoryBrand o **cliente é o herói, a marca é o guia**.
- **Direct response / VSL (long-form, baixa consciência ou venda direta):** Hook (para o scroll na 1ª linha) → Validação do problema ("é frustrante porque…") → **Mecanismo único** (o *como* que ninguém tem — casar com sofisticação 3+) → Solução como consequência natural do mecanismo → Prova empilhada → Quebra de objeção ("você deve estar pensando X… a verdade é Y") → CTA específico → Urgência/escassez **real**. É a espinha de VSL, página de venda longa, e-mail de lançamento e anúncio de resposta direta. Casa com o Dial 1 (quanto menos consciente, mais longa) e o Dial 2 (mecanismo forte quando o mercado já não crê em promessa). Nunca urgência/escassez inventada (ver Guardrails).
- **Ogilvy:** pesquisa primeiro; uma big idea; headline com benefício + um específico ("a 100 km/h o mais alto é o relógio"). Específico vence adjetivo.
- **Hopkins:** reason-why (justificar toda promessa); "23 milhões vendidos" > "usado por milhões"; tudo é mensurável.
- **Halbert:** achar a "multidão faminta" primeiro; escrever pra UMA pessoa; ler em voz alta até soar como fala.
- **Caples:** a headline é ~80% do anúncio — gerar 10+, entregar as 2–3 melhores. Auto-interesse > notícia > curiosidade.
- **Proposta de valor (April Dunford):** alternativa concorrente → atributo único → valor → cliente ideal → categoria. Não criar categoria nova (caro demais educar) — usar uma existente.
- **4 U's na headline:** Útil, Urgente, Único, Ultraespecífico — exigir ≥3.
- **VoC (Wiebe):** copy se *encontra*, não se inventa — minerar a língua real do cliente (reviews, call) e usar literal em headline, bullets e depoimento.

## Copy pra web & SaaS

- **Hero:** headline = a proposta de valor em **5–10 palavras**, orientada a resultado (não a feature) + subhead (como entrega, pra quem) + CTA com valor ("Começar agora" descreve o que ganha) + microcopy redutor de atrito ("sem cartão", "leva 30s") + um elemento de prova à vista. Fórmula: `{resultado desejado} sem {dor/objeção}`.
- **Feature → benefício:** "e daí?" três vezes até bater no ganho emocional/financeiro. "economiza tempo" → "de 4 horas pra 15 minutos".
- **Botões:** nomeiam o resultado ("Criar meu painel"), nunca "Enviar/OK".
- **Empty states / erros:** são copy — sempre próxima ação + tranquilizar, nunca tela em branco ou código cru.
- **Prova:** ao lado de cada afirmação grande e de cada CTA. Depoimento = antes → ação → resultado específico → prazo → reação emocional.
- **Preço:** responder "qual plano é meu?"; ancorar um recomendado; nomear por tipo de comprador; redutor de risco + FAQ perto dos botões.
- **Ordem padrão (baixa/média consciência):** Hero → Prova → Dor → Solução/Benefícios → Como funciona → Resultados → Objeções/FAQ → Preço → CTA final. Mais consciente: colapsar pra Oferta + Prova + CTA.

## Integração SEO / GEO

- Uma keyword/entidade principal por página, natural em H1, primeiras 100 palavras, um H2, title, meta, alt — **sem encher linguiça** (legibilidade vence sempre).
- **GEO (ser citado por IA):** responder primeiro, contexto depois; parágrafos de ≤3 frases (extraíveis); bloco de FAQ em **perguntas naturais** como a pessoa fala com a IA; afirmações autônomas e ancoradas em dado; schema (FAQ/Product/Organization). Hero converte em primeiro; profundidade SEO abaixo.

## Calibrar agressividade

- **Agressivo/urgente:** mais consciente + baixa sofisticação + marca de massa/oferta. Contador, escassez, promessa ousada, CTA duro.
- **Calmo/premium/consultivo:** sofisticação máxima OU pouca consciência OU marca premium/autoridade (saúde, advocacia, alto ticket). Clareza, prova, identidade, CTA de transição ("Ver como funciona").
- Regra: consciência define **o timing** do pedido; sofisticação define **o tom** da promessa; posicionamento define **o teto** do hype. Premium nunca usa linguagem de contador piscando.

---

## Guardrails

- Confiança vem de **especificidade**, não de ponto de exclamação. Nunca inventar número, estatística, garantia ou urgência falsa.
- Banir clichê de IA: "mergulhar", "potencializar", "destravar", "game-changer", "no mundo de hoje", excesso de exclamação, voz passiva, elogio genérico.
- Output em pt-BR espelhando a **voz real do cliente** — não traduzir de inglês.
- Entregar sempre: copy + anotação estratégica (estágios + agressividade) + 2–3 alternativas de headline/CTA. Uma ação pedida por seção.
- Em dúvida sobre VoC, gerar a linguagem provável e **sinalizar como suposição** a validar.
