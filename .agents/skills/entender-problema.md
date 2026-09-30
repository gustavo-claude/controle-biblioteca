---
name: "entender-problema"
description: "Lê os insumos em fontes/ com o briefing.md e grava o contexto arquivo por arquivo. Antes de cada arquivo faz 3 perguntas normalizadoras e só grava depois da resposta do PO. Ordem: produto.md, personas-usuario.md, regras-de-negocio.md, glossario.md. Use quando iniciar um produto, absorver fontes, montar o contexto inicial, entender o sistema ou preencher a ficha do produto."
---

# Skill: Entender o Problema do Sistema

> 💡 **MECANISMO DE DISPARO:**  
> Use no início de um produto ou quando houver material novo em `fontes/`. A skill destila o sistema a partir das fontes e do briefing. Cada arquivo de contexto tem o próprio portão: três perguntas, resposta do PO, então a gravação daquele arquivo. Não grave os quatro de uma vez.

---

## 1. Entradas e Leituras Prévias Obrigatórias

Antes de perguntar ou gravar qualquer arquivo, leia nesta ordem:

1. **Todos os arquivos em `@fontes/`** (exceto `README.md` e `.gitkeep`) — evidência bruta: atas, transcrições, normas, layouts, planilhas, PDFs e imagens. Monte um inventário completo.
2. **`@contexto/briefing.md`** — resumo mínimo do produto. Combine cada fato do briefing com o que as fontes comprovam, contradizem ou deixam em aberto.
3. **Arquivos de saída (formato obrigatório, não inventar seções):**
   - `@contexto/produto.md` — visão, metas numéricas, o que NÃO somos, módulos, restrições.
   - `@contexto/personas-usuario.md` — 2 a 5 personas reais (rotina, objetivo, dor, workaround).
   - `@contexto/regras-de-negocio.md` — catálogo `[RN-XX]` permanente e tabela de números com origem.
   - `@contexto/glossario.md` — termos canônicos, termos proibidos, status fechados e transições.

Se `fontes/` estiver vazia (só README/`.gitkeep`), **pare**. Peça ao usuário depositar os insumos e não avance para as perguntas nem para a gravação.

---

## 2. Procedimento de Execução Passo a Passo

1. **Passo 1 — Inventariar as fontes:**
   - Liste cada arquivo lido, o tipo (ata, norma, layout, planilha) e 2–4 fatos extraídos.
   - Separe **fato** (está no documento) de **lacuna** (não está) e **contradição** (fontes discordam entre si ou com o briefing).
   - Extraia candidatos a: nome do produto, atores/personas, dor, workaround, o que substitui, módulos, regras invariantes, termos e status.

2. **Passo 2 — Cruzar com o briefing:**
   - Para cada uma das 6 linhas fundamentais do briefing (`O que é`, `Para quem`, `Qual a dor`, `O que substitui`, `Dar certo é`, `O que NÃO faz`), anote: confirmado pelas fontes / só no briefing / só nas fontes / em conflito.
   - Não complete placeholder do briefing com invenção. Placeholder vazio = lacuna explícita.

3. **Passo 3 — Ler o gabarito do arquivo da vez:**
   - Releia as seções, callouts e checklists do arquivo que o portão atual vai preencher.
   - A saída **é o preenchimento desse arquivo no formato que ele já propõe**. Não crie seções novas e não apague o bloco "PAPEL DESTE ARQUIVO".

4. **Passo 4 — Visão geral, uma vez, e o primeiro portão:**
   - Entregue no chat o gabarito da seção 3.1.
   - Em seguida, faça **somente** as 3 perguntas de `produto.md` (seção 3.2).
   - **🛑 PORTÃO: pare.** Não grave arquivo nenhum neste turno.

5. **Passo 5 — Um portão por arquivo, nesta ordem:**
   1. `contexto/produto.md`
   2. `contexto/personas-usuario.md`
   3. `contexto/regras-de-negocio.md`
   4. `contexto/glossario.md`

   Em cada portão:
   - Faça **só as 3 perguntas daquele arquivo**, nesta ordem, todas de uma vez. Não antecipe as perguntas do arquivo seguinte.
   - Em cada pergunta, anteponha o que você inferiu das fontes, do briefing e dos arquivos já gravados neste processo. O PO confirma, corrige ou completa. Não pergunte no vazio.
   - **🛑 Não grave o arquivo deste portão antes das três respostas.** Se faltar resposta, pergunte de novo só o que faltou.
   - Com as respostas, preencha **apenas** esse arquivo (seção 3.3).
   - No chat, resuma o que entrou naquele arquivo e o que ficou `[CONFIRMAR]`.
   - Se ainda houver arquivo na fila, faça as 3 perguntas do próximo e **pare**. Não o grave no mesmo turno.

6. **Passo 6 — Regras de preenchimento (valem em todo portão):**
   - Se já houver conteúdo real (não só `[PREENCHER]`), **atualize por mescla**. Em regras, preserve `[RN-XX]`; regra morta vira `[REVOGADA]`; nunca reutilize número. Em personas, mescle pelo papel e mantenha entre 2 e 5; não invente nome, dor ou workaround.
   - Número, prazo ou limite sem origem nas fontes, no briefing ou na resposta do PO: marque `[CONFIRMAR]` ou omita. Nunca invente.

---

## 3. Estrutura do Gabarito de Saída

### 3.1. Visão geral no chat (Passo 4) — uma vez, antes do primeiro portão

```markdown
# Visão geral do sistema (leitura inicial)

## 1. Inventário das fontes
| Arquivo | Tipo | Fatos extraídos |
|---|---|---|
| [nome do arquivo] | [ata / norma / layout / outro] | [2–4 fatos] |

## 2. Cruzamento com o briefing
- **Confirmado:** [fato presente no briefing e nas fontes]
- **Só no briefing:** [fato ainda sem evidência em fontes]
- **Só nas fontes:** [fato relevante ausente do briefing]
- **Conflito:** [onde briefing e fontes (ou fontes entre si) discordam]

## 3. Leitura em uma frase
- **O sistema parece ser:** [1 frase, ainda não gravada]
```

### 3.2. Três perguntas por arquivo — um portão de cada vez

Anteponha a inferência e pergunte só o bloco do arquivo da vez.

#### Portão 1 — `produto.md`

1. **Identidade:** Qual é o **nome oficial** do produto? Em uma frase, o que se **faz nele no dia a dia** e qual é o **resultado imediato** — não a missão institucional?
2. **Substituição e limite:** O que as pessoas usam **hoje** e este produto deve substituir? O que ele **expressamente não fará** neste ciclo?
3. **Meta e restrição:** Que **número** define que o ciclo deu certo? Qual restrição de disponibilidade, segurança ou conformidade é inegociável? O que não tiver número ou origem fica `[CONFIRMAR]`.

#### Portão 2 — `personas-usuario.md`

1. **Quem usa:** Quais papéis **usam o produto no dia a dia** (entre 2 e 5)? Quem é o **usuário primário**? Quem só autoriza, fiscaliza ou recebe resultado fica de fora.
2. **Rotina e objetivo:** Para cada papel, o que essa pessoa **faz na rotina** e o que **busca concluir** no produto?
3. **Dor e gambiarra:** Para cada papel, qual é a **maior frustração de hoje** e **como resolve isso sem o produto**?

#### Portão 3 — `regras-de-negocio.md`

1. **Invariantes:** Quais regras valem para **o produto inteiro** (quem pode, o que é obrigatório, o que é único, qual prazo)?
2. **Números com origem:** Quais prazos, limites ou quantidades já têm **fonte formal**? O que não tiver origem não entra como número fechado.
3. **Quebra e exceção:** O que acontece quando a regra **não se cumpre**? Existe **exceção autorizada**? Se não houver, a exceção é nenhuma.

#### Portão 4 — `glossario.md`

1. **Termo oficial:** Para cada conceito central já usado em `produto.md`, `personas-usuario.md` e `regras-de-negocio.md`, qual é o **único nome da casa** e o que esse termo **não é**?
2. **Sinônimo proibido:** Quais nomes do dia a dia devem ser **banidos**, e qual termo oficial entra no lugar?
3. **Status:** Quais são os **únicos status** da entidade principal, **quem move** cada um e quais **passagens** são permitidas?

### 3.3. Arquivo gravado no portão — formato nativo, sem gabarito paralelo

Preencha só as seções já definidas no arquivo da vez.

| Arquivo | Seções obrigatórias |
|---|---|
| `produto.md` | 1. Visão e proposta de valor (nome, frase, valor) · 2. Objetivos com número (meta principal, secundária, métrica de guarda) · 3. O que NÃO somos / NÃO fazemos / NÃO atendemos (mínimo 3 proibições) · 4. Grandes módulos (responsabilidade + quem utiliza, sem implementação técnica) · 5. Restrições estratégicas (disponibilidade, segurança, conformidade) |
| `personas-usuario.md` | 2 a 5 personas. Cada uma: papel, perfil/rotina, objetivo principal no sistema, maior frustração/dor atual, workaround (gambiarra de hoje). Sem cargo abstrato sem rotina. Nome fictício só se o PO informar. |
| `regras-de-negocio.md` | 1. Catálogo `[RN-XX]` com nome curto, descrição, impacto e exceção autorizada · 2. Tabela de números/parâmetros com valor, origem e onde se aplica. IDs permanentes. |
| `glossario.md` | 1. Termos canônicos (definição + o que NÃO é) · 2. Palavras proibidas e substituto · 3. Catálogo fechado de status · 4. Matriz de transições permitidas |

---

## 4. O que esta skill NÃO faz

- ❌ Diagnosticar uma demanda isolada ("quero um botão X") nem propor 3 caminhos de solução.
- ❌ Atualizar `briefing.md`, `decisoes.md` ou gravar artefatos em `entregas/`.
- ❌ Escrever histórias de usuário, fluxos ou critérios de aceite.
- ❌ Inventar métricas, prazos, regras ou status para "completar" o gabarito.
- ❌ Fazer as perguntas de mais de um arquivo no mesmo turno.
- ❌ Gravar um arquivo antes das 3 respostas do portão dele, ou gravar os quatro arquivos de uma vez.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] Todas as fontes (exceto README/.gitkeep) e o briefing foram lidos?
[ ] A visão geral foi apresentada uma vez, antes do primeiro portão?
[ ] Cada portão fez só 3 perguntas e esperou a resposta do PO antes de gravar aquele arquivo?
[ ] A ordem foi produto.md, personas-usuario.md, regras-de-negocio.md, glossario.md?
[ ] Cada arquivo segue as seções originais, sem seções inventadas?
[ ] Há entre 2 e 5 personas, cada uma com rotina, objetivo, dor e workaround?
[ ] Nenhum número/prazo foi inventado? IDs [RN-XX] existentes foram preservados?
-->
