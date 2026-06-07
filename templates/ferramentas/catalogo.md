# Catalogo de Ferramentas

Referencia de APIs, CLIs e conectores que podem ser usados dentro de skills do Claude Code.
Consulte este arquivo antes de criar skills novas pra saber o que ja esta disponivel.

---

## Criar visuais (HTML pra PNG)

### Playwright CLI
**O que faz:** Renderiza qualquer HTML em imagem PNG (carrosseis, slides, propostas, cards)
**Precisa de conta:** Nao, roda local
**Como instalar:**
```bash
npx playwright install chromium
```
**Como usar numa skill:**
```bash
npx playwright screenshot --viewport-size=1080,1350 --full-page "file:///caminho/slide.html" "slide.png"
```
**Tamanhos comuns:**
- Instagram feed: 1080x1350
- Instagram/TikTok story: 1080x1920
- Slide 16:9: 1920x1080
- Card quadrado: 1080x1080

---

## Publicar na web

### Cloudflare Pages API
**O que faz:** Publica arquivos HTML com link publico (propostas, landing pages, estudos)
**Precisa de conta:** Sim, Cloudflare (gratis)
**Configurar:** Salvar `CLOUDFLARE_API_TOKEN` e `CLOUDFLARE_ACCOUNT_ID` no `.env`
**Quando usar:** Sempre que a skill gerar um HTML que precisa ser compartilhado por link

---

## Publicar em redes sociais

### Post for Me API
**O que faz:** Publica posts no Instagram e TikTok direto do Claude Code
**Precisa de conta:** Sim, postforme.dev
**Configurar:** Salvar `POSTFORME_API_KEY` no `.env`
**Como usar numa skill:**
```bash
node --env-file=.env scripts/publish-postforme.js
```
**Quando usar:** Skills de carrossel, conteudo visual, publicacao automatica

---

## Buscar conteudo da web

### WebFetch (nativo)
**O que faz:** Le o conteudo de qualquer URL e traz como texto
**Precisa de conta:** Nao, ja vem no Claude Code
**Quando usar:** Pesquisa de referencias, ler artigos, buscar dados de sites

### WebSearch (nativo)
**O que faz:** Pesquisa no Google e traz resultados
**Precisa de conta:** Nao, ja vem no Claude Code
**Quando usar:** Quando o usuario precisa pesquisar antes de criar conteudo

### Jina Reader
**O que faz:** Converte qualquer URL em markdown limpo (melhor que WebFetch pra artigos longos)
**Precisa de conta:** Nao
**Como usar:** Acessar `https://r.jina.ai/{URL}` via WebFetch
**Quando usar:** Extrair texto de artigos, blog posts, paginas com muito HTML

---

## Extrair conteudo de video

### yt-dlp (CLI)
**O que faz:** Baixa transcricoes/legendas de videos do YouTube
**Precisa de conta:** Nao, roda local
**Como instalar:**
```bash
brew install yt-dlp
```
**Quando usar:** Skills que partem de um video pra criar conteudo (carrossel, newsletter, roteiro)

---

## Gerar imagens com IA (2026)

Skill que usa isso: `/gerar-imagem` (roteia pro melhor modelo por caso). Nao existe modelo unico melhor — escolher pela tarefa:

### GPT Image 2 (OpenAI) — PADRAO
**O que faz:** Gera imagem; melhor do mercado em texto-na-imagem (~99%) e em seguir instrucao
**Precisa de conta:** Sim, OpenAI (pago — `quality` low/med/high controla custo)
**Configurar:** `OPENAI_API_KEY` no `.env` (modelo `gpt-image-1`)
**Quando usar:** Padrao. Criativo de anuncio, post com texto, layout de marca

### Nano Banana (Gemini, Google)
**O que faz:** Gera e edita imagem rapido (1-3s), otimo pra "muda so essa parte" e volume
**Precisa de conta:** Sim, Google AI Studio
**Configurar:** `GEMINI_API_KEY` (modelos `gemini-3-pro-image-preview` / `gemini-2.5-flash-image`)
**Quando usar:** Edicao iterativa, consistencia de produto, alto volume

### Imagen 4 Ultra (Google) / Flux 2 Pro (Black Forest)
**O que faz:** Foto realista de alto nivel (produto, pele, tecido, comida)
**Configurar:** Imagen via `GEMINI_API_KEY`; Flux via `FAL_KEY` (fal.ai)
**Quando usar:** Hero shot e foto de produto realista

### Recraft V4
**O que faz:** Unico que exporta SVG de verdade — logos e icones vetoriais
**Configurar:** `FAL_KEY` (fal.ai)
**Quando usar:** SEMPRE que for logo ou icone. Nunca entregar logo em raster

### fal.ai (gateway)
**O que faz:** Uma chave (`FAL_KEY`) da acesso a Flux, Recraft, Ideogram, Imagen, etc. Troca de modelo vira uma linha
**Quando usar:** Recomendado como porta unica pros modelos acima

---

## Gerar video / reels com IA (2026)

Skill que usa isso: `/reels`.

### Veo 3.1 (Google) — PADRAO
**O que faz:** Melhor all-rounder de video; audio nativo, 9:16, 4K, planos de ~8s
**Configurar:** `GEMINI_API_KEY` (Gemini/Vertex)
**Quando usar:** Hero shot de reel/anuncio

### Kling v3 / Pika / Runway / Higgsfield
**O que faz:** Kling = barato e muito movimento; Pika = volume diario; Runway = controle fino; Higgsfield = hub com presets de camera (agrega Veo/Kling/Pika)
**Configurar:** API propria, `FAL_KEY`, ou `HIGGSFIELD_API_KEY`
**Quando usar:** Conforme custo/volume/controle. **Evitar Sora 2** (sendo descontinuado em 2026)

### Submagic
**O que faz:** Legenda animada (99%+ de acerto, 100+ idiomas) com brand kit do cliente aplicado automatico
**Precisa de conta:** Sim (CapCut e a alternativa gratis)
**Quando usar:** Finalizacao de todo reel

---

## Conectar com plataformas (MCPs)

MCPs sao conectores que dao acesso direto a plataformas dentro do Claude Code.
O Claude passa a usar esses conectores automaticamente quando fizer sentido.

Pra verificar quais MCPs ja estao instalados: `claude mcp list`
Pra remover um MCP: `claude mcp remove nome-do-mcp`

### Notion
**O que faz:** Acessa projetos, bases de dados, briefings e tarefas do Notion
**Precisa de conta:** Sim, API key em notion.so/my-integrations
**Como instalar:**
```bash
claude mcp add notion -- npx -y @notionhq/notion-mcp-server
```
**Quando usar:** Skills que precisam ler/escrever tarefas, bases de clientes, documentos

### Gmail
**O que faz:** Le e compoe emails sem sair do Claude Code
**Precisa de conta:** Sim, OAuth Google
**Como instalar:**
```bash
claude mcp add gmail -- npx -y @gongrzhe/server-gmail-autoauth-mcp
```
**Quando usar:** Skills de email, follow-up, comunicacao com clientes

### Google Calendar
**O que faz:** Ve agenda, cria eventos e encontra horarios disponiveis
**Precisa de conta:** Sim, OAuth Google
**Como instalar:**
```bash
claude mcp add google-calendar -- npx -y @gongrzhe/server-google-calendar-autoauth-mcp
```
**Quando usar:** Skills de agendamento, planejamento, organizacao de reunioes

### Canva
**O que faz:** Acessa designs, cria novos assets visuais direto pelo Claude
**Precisa de conta:** Sim, Canva Pro
**Como instalar:**
```bash
claude mcp add canva -- npx -y @canva/canva-mcp-server
```
**Quando usar:** Skills de design, criacao visual, materiais de marca

### Facebook Ads (Meta)
**O que faz:** Gerencia campanhas do Meta (Facebook/Instagram Ads)
**Precisa de conta:** Sim, Token Meta Business
**Quando usar:** Skills de gestao de midia paga, relatorios de performance

### Google Ads
**O que faz:** Acessa e edita campanhas, busca dados de performance
**Precisa de conta:** Sim, credenciais Google Ads
**Quando usar:** Skills de gestao de midia paga, relatorios de performance

### N8N
**O que faz:** Dispara automacoes e workflows do N8N
**Precisa de conta:** Sim, instancia N8N + API key
**Como instalar:**
```bash
claude mcp add n8n -- npx -y n8n-mcp
```
**Quando usar:** Skills que precisam disparar automacoes externas

### Supabase
**O que faz:** Banco de dados e backend completo
**Precisa de conta:** Sim, projeto Supabase
**Quando usar:** Skills que precisam guardar dados, autenticacao, backend

### Telegram
**O que faz:** Envia e recebe mensagens via bot do Telegram
**Precisa de conta:** Sim, bot token do BotFather
**Quando usar:** Skills de notificacao, comunicacao automatica

---

## Como adicionar ferramentas novas

Se voce usa uma API ou ferramenta que nao esta nessa lista, adicione aqui seguindo o formato:

```markdown
### Nome da Ferramenta
**O que faz:** [descricao em uma frase]
**Precisa de conta:** [Sim/Nao]
**Configurar:** [o que salvar no .env, se aplicavel]
**Como usar numa skill:** [comando ou instrucao]
**Quando usar:** [em que tipo de skill faz sentido]
```
