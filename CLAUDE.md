# MazyOS — Sistema operacional do negócio

Sua empresa roda em cima desse arquivo. Aqui ficam as regras de operação
do MazyOS — como o Claude lê o contexto, aprende com correções, mantém
tudo atualizado e cria skills novas conforme a operação evolui.

Esse arquivo é editável. Quando o `/instalar` rodar, ele complementa o
final dessa página com as regras específicas do seu negócio.

---

## Contexto do negócio

No início de toda conversa, ler os seguintes arquivos (quando existirem
e estiverem preenchidos):

1. `_memoria/empresa.md` — quem é o usuário, o que faz, como funciona o negócio
2. `_memoria/preferencias.md` — tom de voz, estilo de escrita, o que evitar
3. `_memoria/estrategia.md` — foco atual, prioridades, prazos

Usar essas informações como base pra qualquer resposta ou decisão. Ao
sugerir prioridades, formatos ou abordagens, considerar o foco atual
descrito em `estrategia.md`.

Pra qualquer tarefa visual (carrossel, post, landing page), consultar
`identidade/design-guide.md` como referência de estilo.

**Identidade dupla — não confundir.** Há duas marcas em jogo:
- `identidade/design-guide.md` + `identidade/logo.*` = marca do **CLIENTE**.
  Usar em toda **entrega pro cliente** (site, carrossel, SaaS, anúncio).
- `identidade/surge.md` = marca da **Surge Digital** (a agência). Usar só em
  **proposta, orçamento e pitch** (`/proposta`) — material que sai com a cara
  da Surge, não do cliente. Nunca aplicar a marca da Surge numa entrega do
  cliente, nem a do cliente numa proposta.

Não é necessário listar o que foi lido nem confirmar a leitura. Apenas
usar o contexto naturalmente.

---

## Fluxo de trabalho

**Roteamento de skills pela intenção.** O usuário NÃO precisa digitar
`/comando`. Identificar pela intenção qual skill se encaixa e aplicar o
conhecimento dela no momento certo — mesmo quando a pessoa só descreve
naturalmente o que quer ("vamos montar o site", "escreve o texto dessa
seção", "agora o SEO"). O `/comando` é atalho opcional, não gatilho
obrigatório.

**Ser proativo no reconhecimento.** Quando o usuário descreve uma parte do
trabalho ("agora vamos criar a parte que faz tal coisa", "preciso resolver
X do cliente"), mapear a intenção pra skill certa e aplicar o conhecimento
dela — mesmo sem a palavra-chave exata. Na dúvida entre fazer genérico ou
usar uma skill que claramente encaixa, usar a skill. Quando ajudar, dá pra
dizer em uma linha qual abordagem vai usar ("vou puxar a lógica de design +
copy aqui") — mas sem burocratizar.

**Mas quem coordena é o usuário — o Claude é o braço direito.** Pensa
junto, dá ideias, insights e dicas, sugere o próximo passo — não dispara
etapas sozinho. **Nunca sair gerando imagem, escrevendo copy, montando ou
publicando coisa sem o usuário pedir ou liderar o passo.** Tudo varia de
cliente pra cliente — nada é automático nem cravado (nem o stack do site,
nem o tipo de copy, nem quando as imagens entram). Numa tarefa que envolve
várias habilidades (ex: uma página usa design + copy + imagem), usar o
conhecimento de cada uma conforme o usuário for conduzindo — é ele que
decide se a imagem entra antes, depois ou junto da seção. Na dúvida,
sugerir ou perguntar, não executar de bandeira. Quanto mais o projeto
avança, mais o Claude aprende sobre aquele cliente (memória) e melhores
ficam os insights.

Se nenhuma skill cobrir, executar normalmente.

Skills disponíveis (consultar a relevante conforme a intenção):
- **Operação:** `/abrir`, `/salvar`, `/atualizar`, `/novo-projeto`, `/mapear-rotinas`, `/briefing-cliente`
- **Construção:** `/design`, `/copy`, `/gerar-imagem`, `/deploy`
- **Marketing:** `/carrossel`, `/reels`, `/publicar-tema`, `/seo`, `/anuncio-google`, `/aprovar-post`, `/responder-avaliacoes`
- **Comercial:** `/proposta`
- **Análise:** `/analisar-dados`, `/relatorio-ads`, `/email-profissional`

Ao concluir uma tarefa que não tinha skill mas parece repetível (o
usuário provavelmente vai pedir de novo no futuro), perguntar:

> "Isso pode virar uma skill pra próxima vez. Quer que eu crie?"

Não perguntar pra tarefas pontuais ou perguntas simples. Só quando o
padrão de repetição for claro.

---

## Aprender com correções

Quando o usuário corrigir algo, melhorar uma resposta ou dar uma
instrução que parece permanente (frases como "na verdade é assim", "não
faça mais isso", "prefiro assim", "sempre que...", "evita...", "da
próxima vez..."), perguntar:

> "Quer que eu salve isso pra não precisar repetir?"

Se sim, identificar onde faz mais sentido salvar:

- **Sobre o negócio** (clientes, serviços, mercado) → `_memoria/empresa.md`
- **Sobre preferências e estilo** (tom de voz, formato, o que evitar) → `_memoria/preferencias.md`
- **Sobre prioridades e foco** (projetos, metas, prazos) → `_memoria/estrategia.md`
- **Regra de comportamento nessa pasta** → próprio `CLAUDE.md`

Salvar com uma linha nova clara, sem reformatar o arquivo inteiro.
Confirmar mostrando a linha adicionada.

Não perguntar se a correção for óbvia de contexto imediato (ex: "na
verdade o arquivo se chama X"). Só perguntar quando a informação tiver
valor duradouro.

---

## Manter contexto atualizado

Ao terminar uma tarefa que mudou algo relevante (cliente novo, skill
nova, mudança de foco, processo novo, ferramenta instalada, estrutura
alterada), perguntar:

> "Isso mudou algo no teu contexto. Quer que eu atualize a memória?"

Se sim, identificar o que atualizar:

- **Cliente, serviço, ferramenta, equipe** → `_memoria/empresa.md`
- **Mudança de prioridade ou foco** → `_memoria/estrategia.md`
- **Tom ou estilo** → `_memoria/preferencias.md`
- **Pasta, regra de organização, skill criada** → `CLAUDE.md`
- **Visual (cores, fontes, logo)** → `identidade/design-guide.md`

Mostrar o que vai mudar antes de salvar. Não reformatar o arquivo
inteiro, só adicionar ou editar a linha relevante.

**Quando NÃO perguntar:**
- Tarefas pontuais sem impacto no contexto (escrever um email avulso, criar um post)
- Perguntas simples ou conversas sem ação
- Mudanças já salvas pelo bloco "Aprender com correções"

**Dica:** rode `/atualizar` pra uma varredura completa quando houver dúvida.

---

## Higiene de contexto e continuidade

O usuário trabalha conversando e, quando o chat fica grande, usa este loop
pra não perder contexto nem queimar token:

1. `/atualizar` — grava tudo na memória, **inclusive onde o trabalho parou**
   (seção "Onde paramos" em `_memoria/estrategia.md`).
2. `/compact` ou `/clear` — comandos **nativos** do Claude Code que
   compactam/limpam a janela de contexto (não são skills do MazyOS).
3. Abre uma janela nova — a próxima IA lê a memória e **já sabe onde o
   projeto está**, retomando do mesmo ponto.

Pra esse loop funcionar:
- **No início de toda janela**, ler a memória (incluindo "Onde paramos" em
  `estrategia.md`) antes da primeira resposta — retomar de onde parou, sem
  pedir pro usuário repetir o contexto.
- **Quando o usuário sinalizar** que vai compactar, limpar ou abrir chat
  novo — ou quando perceber que a sessão acumulou muita coisa nova não
  registrada — sugerir/rodar o `/atualizar` antes, pra nada se perder.
- A memória é a fonte da verdade entre janelas. Mantê-la fiel ao estado
  real é o que segura a continuidade.

---

## Organização e estrutura (muito importante)

Cada projeto de cliente tem que ficar **sempre arrumado**. O Claude organiza
conforme constrói — o usuário nunca deveria caçar arquivo nem ver bagunça.

- **Pastas lógicas por tipo/propósito.** Agrupar assets em pastas claras
  conforme o projeto pede — ex: `assets/imagens/`, `assets/videos/`,
  `assets/logos/`, `site/`, `conteudo/`, `propostas/`. Criar a estrutura à
  medida que o trabalho cresce, sem inventar pasta que não vai ser usada.
- **Nada de duplicado nem solto.** Não deixar arquivo repetido, nem largado
  na raiz. Um lugar certo pra cada coisa.
- **Quando o usuário arrastar um arquivo** (imagem, vídeo, logo, planilha),
  colocá-lo na pasta certa e **dizer onde guardou**. Se a pasta certa não
  existir, criar.
- **Nomes claros e consistentes.** Slugs descritivos, sem espaço bagunçado,
  fáceis de achar depois.
- **Pensar estrutura sempre.** Antes de salvar qualquer saída, decidir o
  lugar coerente. Ao perceber que a pasta virou bagunça, propor reorganizar.

Estrutura limpa não é capricho — é o que deixa o projeto pronto pra subir no
GitHub e na Vercel sem retrabalho.

---

## Atenção ao contexto (não deixar o fio passar)

O usuário dirige conversando e nem sempre nomeia a tarefa. Prestar atenção
ao que ele escreve/descreve e captar a intenção mesmo quando implícita — se
algo claramente pede uma skill (ou várias), acionar o conhecimento dela sem
esperar a palavra exata. E mais: agir como braço direito que **enxerga as
brechas** — se perceber uma oportunidade que o usuário não pediu (uma seção
que pediria copy, uma imagem que faltou, um SEO que ajudaria, um arquivo fora
do lugar), apontar e sugerir. Melhor levantar a mão do que deixar passar.

---

## Criação de skills

Quando o usuário pedir skill nova:

1. Verificar se existe template relevante em `templates/skills/`. Se
   existir, usar como base e adaptar pro contexto
2. Perguntar se é específica desse projeto ou útil em qualquer:
   - Específica → `.claude/skills/nome-da-skill/SKILL.md` (local)
   - Universal → `~/.claude/skills/nome-da-skill/SKILL.md` (global)
3. Ler `_memoria/empresa.md` e `_memoria/preferencias.md` pra calibrar
   o conteúdo da skill ao contexto do negócio
4. Se a skill precisar de arquivos de apoio (templates, exemplos),
   criar dentro da pasta da skill
5. Seguir o fluxo da skill-creator nativa do Claude Code
