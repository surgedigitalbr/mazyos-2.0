---
name: salvar
description: >
  Salva o trabalho do MazyOS no GitHub (commit + push). Na primeira vez configura o repositório
  remoto. Use quando o usuário disser "salvar", "salva no github", "commit", "push", "/salvar"
  ou pedir backup do trabalho.
---

# /salvar — Salvar no GitHub

Skill de uma função só: garantir que o trabalho do usuário está no GitHub. Fácil pra quem nunca usou git.

## Workflow

### Passo 0 — Detectar o estado do repositório

Rodar:
- `git rev-parse --is-inside-work-tree 2>/dev/null` — é repo git?
- `git remote get-url origin 2>/dev/null` — pra onde aponta?

Três casos:

- **A — Não é repo git** → setup do zero (ver "Primeira vez" abaixo).
- **B — É repo, mas o origin ainda é o MOLDE** (`github.com/mazzeoia/MazyOS`, ou qualquer remote que não seja do usuário) → **desacoplar do molde** antes de salvar. É o caso de todo projeto recém-clonado.
- **C — É repo já apontando pro repo do CLIENTE** (origin é do usuário) → commit + push normal ("Commits seguintes").

### Caso B — Desacoplar do molde (primeira vez de cada cliente)

O projeto foi clonado do MazyOS, então carrega o histórico e o remote do molde. Antes do primeiro salvar, transformar em repo limpo só desse cliente.

1. Avisar e confirmar (é destrutivo — apaga o histórico do molde, que é o que se quer):
   > "Esse projeto ainda aponta pro repositório-molde do MazyOS. Vou desacoplar pra ele virar um repo limpo só desse cliente (apaga o histórico do molde, mantém todos os arquivos). Você já tem um repositório criado no SEU GitHub pra esse cliente?
   > 1. Sim — me passa a URL (ex: https://github.com/surgedigital/cliente-x.git)
   > 2. Não — eu crio agora na sua conta (preciso do `gh` CLI) — me dá um nome (ex: cliente-x)"

2. Desacoplar (mantém os arquivos, zera o histórico):
   ```bash
   rm -rf .git
   git init
   git add .
   git commit -m "Setup inicial — <cliente>"
   git branch -M main
   ```

3. Apontar pro repo do cliente:
   - **Opção 1 (URL):** `git remote add origin <URL>` → `git push -u origin main`
   - **Opção 2 (criar):** conferir `gh --version`; se ok, `gh repo create <nome> --private --source=. --push`. Se não tiver `gh`, instruir a instalar (https://cli.github.com/) ou criar manualmente em github.com/new e voltar com a URL.

Dos próximos `/salvar` em diante, esse projeto é Caso C — vai direto pro repo do cliente.

### Primeira vez (Caso A — repositório não inicializado)

1. Perguntar:
   > "Esse é o primeiro syncar. Você já tem um repositório criado no GitHub pra esse workspace?
   > 1. Sim, me passa a URL (ex: https://github.com/usuario/nome.git)
   > 2. Não, vou criar agora — me dá um nome pro repositório (ex: cliente-x)"

2. **Se opção 1:** rodar `git init`, `git add .`, `git commit -m "Setup inicial"`, `git branch -M main`, `git remote add origin <URL>`, `git push -u origin main`.

3. **Se opção 2:** verificar se o `gh` CLI está instalado (`gh --version`). 
   - Se sim: rodar `git init`, criar commit inicial, e `gh repo create <nome> --private --source=. --push`.
   - Se não: instruir o usuário a instalar `gh` (https://cli.github.com/) ou criar o repo manualmente em github.com/new e voltar com a URL.

### Commits seguintes (já configurado)

1. Rodar `git status`. Se não tiver mudanças, responder "Tá tudo sincronizado, sem mudança nova" e parar.

2. Mostrar o `git status` curto pro usuário e perguntar:
   > "Vou comitar tudo isso. Quer descrever a mudança em uma frase ou usa o resumo automático?"

3. Se o usuário fornecer mensagem, usar. Se não, gerar uma mensagem baseada nos arquivos alterados (1 linha, formato: "Atualiza X" ou "Adiciona Y" ou "Cria proposta pra cliente Z").

4. `git add .` → `git commit -m "<mensagem>"` → `git push`.

5. Confirmar com link do repositório (extrair de `git remote get-url origin`):
   > "Sincronizado. Ver no GitHub: <URL>"

## Regras

- Nunca usar `--force` sem o usuário pedir explicitamente
- Nunca rodar `git reset --hard` ou outras destrutivas sem confirmação clara
- **Nunca empurrar pro repo do molde** (`mazzeoia/MazyOS`). Se o origin ainda for o molde, é Caso B — desacoplar primeiro. Cada cliente vai pro próprio repo no GitHub da Surge, nunca de volta pro molde.
- O `rm -rf .git` do Caso B só roda depois da confirmação do usuário (apaga histórico do molde, preserva os arquivos)
- Se o push falhar por divergência (alguém comitou no remoto), avisar o usuário e oferecer `git pull --rebase` antes de tentar de novo
- Se o usuário ainda não tiver `git` configurado (`user.name` / `user.email`), perguntar e configurar com `git config --global` na primeira vez
