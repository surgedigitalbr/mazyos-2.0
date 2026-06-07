---
name: atualizar
description: >
  Varre o projeto e atualiza os arquivos de contexto (`_memoria/empresa.md`, `preferencias.md`,
  `estrategia.md`, `CLAUDE.md`, `identidade/design-guide.md`), incluindo gravar ONDE O TRABALHO
  PAROU pra próxima janela retomar sem perder contexto. Use quando o usuário disser "atualiza",
  "/atualizar", "varre o projeto", pedir uma reconciliação geral, ou antes de compactar/limpar o
  contexto (`/compact`, `/clear`) e abrir um chat novo.
---

# /atualizar — Varredura e atualização de contexto

Compara o que está nos arquivos de contexto com o estado real do workspace e propõe atualizações. Também serve de **ponto de salvamento**: grava onde o trabalho parou pra próxima janela de contexto retomar do mesmo lugar.

## O loop de higiene de contexto (importante)

O fluxo do usuário: trabalha conversando → quando o chat fica grande, roda `/atualizar` → depois `/compact` ou `/clear` (comandos **nativos** do Claude Code) → abre janela nova → a próxima IA lê a memória e **já sabe onde o projeto está**, sem perder o fio nem queimar token.

Pra esse loop funcionar, o `/atualizar` tem que deixar registrado em `_memoria/estrategia.md` **o estado atual do trabalho** (Passo 2.5). Se o usuário sinalizar que vai compactar/limpar/abrir chat novo, rodar essa captura sem enrolação.

## Workflow

### Passo 1 — Levantamento

Listar:
- Pastas na raiz (cada uma representa uma área de trabalho)
- Subpastas em `clientes/` (se existir) — cada uma é um cliente
- Skills em `.claude/skills/` — quais existem hoje
- Arquivos recentes (últimos 30 dias) em pastas como `propostas/`, `conteudo/`, `clientes/<x>/`

### Passo 2 — Comparação

Ler os arquivos de contexto e identificar:

- **Em `_memoria/empresa.md`:** lista de clientes / serviços / ferramentas — bate com a realidade do workspace?
- **Em `_memoria/estrategia.md`:** o foco atual ainda faz sentido (datas, prioridades)?
- **Em `CLAUDE.md`:** as regras de organização e a estrutura de pastas listada batem com o que existe?
- **Em `identidade/design-guide.md`:** continua coerente com o que foi gerado nas últimas peças (carrosséis, slides)?

### Passo 2.5 — Capturar onde paramos (continuidade)

Gravar em `_memoria/estrategia.md`, numa seção **"Onde paramos"**, o estado atual do trabalho — pra próxima janela retomar sem reler o chat inteiro:

- **Em andamento:** o que está sendo construído agora (ex: "site do cliente X — seção de serviços, faltam preço e rodapé").
- **Decisões tomadas nessa sessão:** stack escolhido, paleta, ângulo de copy, o que foi aprovado.
- **Próximo passo:** a primeira coisa a fazer ao reabrir.
- **Pendências:** o que está esperando o usuário (aprovar foto, passar dado, mandar logo).

Sobrescrever a seção "Onde paramos" anterior (é um instantâneo do agora, não histórico). Manter curto — 5 a 10 linhas. É isso que faz a próxima IA "já saber onde o projeto tá".

### Passo 3 — Proposta de mudanças

Apresentar pro usuário uma lista curta no formato:

```
Encontrei [N] coisas pra atualizar:

1. _memoria/empresa.md — falta o cliente "Acme" (vi pasta clientes/Acme/ criada em [data])
2. CLAUDE.md — tem regra "propostas vão em propostas/" mas vejo propostas em clientes/<x>/propostas/
3. _memoria/estrategia.md — fala em "fechar 1º cliente em fevereiro", já é abril e tem 3 clientes ativos

Quer que eu aplique essas mudanças? Posso aplicar todas, escolher algumas, ou nenhuma.
```

### Passo 4 — Aplicação

Se o usuário aprovar, editar os arquivos com cirurgia — só a linha relevante, sem reformatar o documento todo. Mostrar o diff de cada mudança aplicada.

## Regras

- Não inventar fatos — só registrar o que tem evidência no workspace
- Se a evidência for ambígua (ex: pasta vazia chamada "Cliente Novo"), perguntar antes de adicionar
- Não apagar conteúdo dos arquivos de contexto — só atualizar e adicionar
- Se nenhuma mudança for necessária, responder "Tá tudo coerente, nada pra atualizar"
