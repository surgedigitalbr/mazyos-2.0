---
name: gerar-imagem
description: >
  Gera imagens de marketing, produto, marca e logos com o melhor modelo de 2026 pra cada caso.
  Roteia entre GPT Image 2 (padrão, melhor pra texto-na-imagem e criativos), Imagen 4 / Flux 2
  (foto realista de produto), Nano Banana (edição rápida e volume) e Recraft (logo/ícone em SVG).
  Use sempre que precisar de foto de produto, criativo de anuncio, imagem de hero, banner, post,
  ilustração, ícone ou logo — mesmo que o usuário não diga "gerar imagem", só "preciso de uma foto
  pra isso" ou "faz a logo".
---

# /gerar-imagem — Geração de imagem (roteamento por caso)

Não existe "melhor modelo" universal — existe o melhor pra cada tarefa. Esta skill escolhe e chama o certo.

## Quem coordena é o usuário — não gerar sozinho

**Nunca sair gerando imagem por conta própria.** O usuário conduz: às vezes monta o site primeiro e joga as imagens depois, às vezes pede a imagem junto de uma seção, às vezes traz a imagem dele. Esperar ele pedir ou liderar o passo. Sugerir uma ideia de imagem é ótimo ("aqui caberia uma foto de X"), sair gerando sem ele mandar, não.

## Roteamento (qual modelo pra quê)

| Caso | Modelo | Por quê |
|---|---|---|
| **Padrão / criativo com texto, anúncio, post, layout de marca** | **GPT Image 2** (`gpt-image-1`) | ~99% de acerto em texto-na-imagem, melhor seguimento de instrução |
| **Foto realista de produto, hero, pele/tecido/comida** | **Imagen 4 Ultra** ou **Flux 2 Pro** | realismo superior |
| **Edição "muda só essa parte", consistência de personagem/produto, alto volume** | **Nano Banana** (Gemini) | rápido, barato, melhor edição conversacional |
| **Logo, ícone, qualquer coisa vetorial** | **Recraft V4** → **SVG** | único com export vetorial real |

**Regras de roteamento:**
- Padrão é GPT Image 2. Só trocar quando o caso pede (acima).
- **Logo/ícone de cliente = SEMPRE SVG (Recraft).** Nunca entregar raster como "logo".
- Draft em `quality: "low"`, só o final escolhido em `"high"` (controla custo do GPT Image).
- Fotos: nunca rosto/pessoa identificável sem autorização. Prompt em inglês (modelos respondem melhor).

## Setup

`.env` na raiz com a chave do que for usar:
```
OPENAI_API_KEY=sk-...        # GPT Image 2
GEMINI_API_KEY=...           # Nano Banana / Imagen
FAL_KEY=...                  # Flux, Recraft, Ideogram via fal.ai (1 chave, vários modelos)
```

Recomendado usar **fal.ai** como gateway pra Flux/Recraft/Ideogram — uma chave, troca de modelo é uma linha. Se faltar a chave, parar e guiar o setup.

## Scripts esperados

- `scripts/gerar-imagem.js` — recebe `(modelo, prompt, saída.png|svg)`, roteia pra OpenAI/Gemini/fal conforme o modelo. Criar na primeira vez (o `scripts/README.md` documenta).

```bash
node --env-file=.env scripts/gerar-imagem.js gpt-image-2 "PROMPT" "saida.png"
node --env-file=.env scripts/gerar-imagem.js recraft "PROMPT de logo" "logo.svg"
```

## Workflow

1. Entender o caso → escolher o modelo pela tabela.
2. Montar o prompt (inglês, específico: assunto, luz, ângulo, estética, qualidade editorial).
3. Gerar draft (low). Mostrar pro usuário. Ajustar prompt se preciso.
4. Final em high. Salvar na pasta do projeto/conteúdo.

## Regras

- Padrão GPT Image 2; rotear só quando o caso pede.
- Logo sempre SVG (Recraft).
- Aprovar foto antes de usar em peça final.
- Prompts em inglês; sem rostos identificáveis sem autorização.
- Reaproveitar `node_modules` entre pastas (não rodar `npm install` toda vez).
