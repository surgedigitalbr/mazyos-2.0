---
name: reels
description: >
  Cria reels e criativos de vídeo curto (Reels/TikTok/Shorts e anúncios) — do roteiro à geração por
  IA, com legendas animadas. Escreve o roteiro (hook + beats + CTA), monta o shotlist, gera os
  planos com Veo 3.1 (padrão), Kling, Pika ou Higgsfield, e finaliza com legendas no Submagic.
  Use sempre que o usuário pedir reel, vídeo curto, criativo de vídeo, anúncio em vídeo, TikTok ou
  Shorts — mesmo que só diga "preciso de um vídeo pra isso".
---

# /reels — Reels e criativos de vídeo

Do roteiro ao vídeo pronto pra postar, em 9:16, < 30s.

## Dependências

- **Contexto/tom:** `_memoria/empresa.md`, `_memoria/preferencias.md`.
- **Marca do cliente:** `identidade/design-guide.md` (cores/fonte aplicadas nas legendas).
- **Copy:** roteiro segue a lógica de `/copy` (hook, consciência do público).
- **Craft externo:** o `/reels` produz **um** vídeo. Quando o pedido for a estratégia de conteúdo em vídeo (pauta, frequência, série, pilares pra TikTok/Shorts/Reels ao longo do tempo), puxar a skill externa `content-strategy` — ela monta o plano, o `/reels` executa cada peça.

## Modelos (qual pra quê)

| Caso | Modelo | Nota |
|---|---|---|
| **Padrão — hero shot, áudio nativo, 9:16, 4K** | **Veo 3.1** (Gemini/Vertex) | melhor all-rounder |
| **Custo baixo / muito movimento** | **Kling v3** | top em movimento, barato |
| **Volume diário (Reels/TikTok)** | **Pika** | consistência de personagem |
| **Entrega de cliente com controle fino** | **Runway** | custo previsível |
| **Hub com presets de câmera/movimento** | **Higgsfield** | agrega Veo/Kling/Seedance/Pika |

**Evitar Sora 2 em skill reutilizável** — está sendo descontinuado em 2026.

Clipes saem em planos de ~8s (máximo dos modelos) — gerar por plano e juntar, não esperar um vídeo longo de uma vez.

## Workflow

1. **Roteiro** — hook (3s) + 3–5 beats (problema → solução → CTA), 9:16, < 30s. Seguir tom de `/copy`.
2. **Shotlist** — quebrar em planos de 8s; um prompt por plano (assunto, movimento de câmera, luz, produto).
3. **Gerar** — Veo 3.1 por padrão (ou Kling/Pika por caso) via API/fal/Higgsfield. Mostrar planos pro usuário.
4. **Montar** — juntar os planos (CapCut grátis, ou ffmpeg programático).
5. **Legendas** — **Submagic** (99%+ de acerto, legenda animada, brand kit do cliente: logo/fonte/cor automáticos). CapCut como alternativa grátis.
6. **Exportar** 9:16 e entregar. Oferecer postar (Instagram/TikTok) se integração existir.

## Setup

`.env`: `GEMINI_API_KEY` (Veo), ou `FAL_KEY`/`HIGGSFIELD_API_KEY`. Submagic/CapCut são passos de edição (web). Se faltar chave, parar e guiar.

## Regras

- Padrão Veo 3.1; rotear por custo/volume/controle conforme a tabela.
- Sempre 9:16, < 30s pra reel orgânico (ads podem variar).
- Legenda sempre com brand kit do cliente.
- Gerar em planos de 8s e juntar.
- Roteiro nunca genérico — hook na primeira frase, voltado à dor do público.
