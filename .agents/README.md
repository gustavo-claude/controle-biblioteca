# Pasta `.agents/` — Inteligência Configurável da IA

> 💡 **PAPEL DESTA PASTA:**  
> Aqui mora o *como* a IA trabalha: chapéus (personas), invariantes (regras), procedimentos (skills) e pipelines com aprovação humana (workflows).  
> Os fatos do domínio ficam em `contexto/`. O contrato curto fica em `AGENTS.md`. Esta pasta ensina o *método*.

---

## 1. Qual artefato criar? (Árvore de decisão)

Antes de abrir um arquivo novo, responda em uma frase: **o que a IA deveria passar a fazer de diferente?**

| Se a necessidade é... | Crie um(a)... | Receita |
|---|---|---|
| Mudar o papel do workspace, o que a IA **nunca** faz, ou quais fatos ela lê sempre | **Contrato** (`AGENTS.md`) | `RECEITA-contrato.md` |
| Um chapéu distinto (missão, leituras e restrições diferentes de todos os outros) | **Persona** em `agents.md` | `RECEITA-criar-persona.md` |
| Uma postura ou padrão que deve valer **sem o operador pedir** | **Regra** em `rules/` | `rules/RECEITA-rules.md` |
| Um procedimento repetível com passos e gabarito de saída | **Skill** em `skills/` | `skills/RECEITA-skills.md` |
| Um pipeline de várias etapas que **não pode pular** a aprovação humana | **Workflow** em `workflows/` | `workflows/RECEITA-workflow.md` |
| Um fato do domínio que a IA não pode inventar | **Documento em `contexto/`** | `contexto/RECEITA-novo-documento.md` |
| Calibrar o *formato* da saída (foto do prato pronto) | **Exemplo** em `exemplos/` | `exemplos/RECEITA.md` |

> 📏 **REGRA DE OURO:** Um artefato, uma responsabilidade. Se dois arquivos fariam o mesmo trabalho, não crie o segundo.

---

## 2. Mapa desta pasta

| Caminho | O que contém | Quando a IA lê |
|---|---|---|
| `agents.md` | Catálogo de personas (`@nome`) | Quando o operador chama a persona ou um workflow a aciona |
| `rules/` | Invariantes de postura, estilo e padrão | `always_on`, por `globs`, ou quando skill/persona aponta |
| `skills/<nome>.md` | Procedimento de uma tarefa | Quando o pedido casa com a `description` ou o operador cita a skill |
| `workflows/` | Comandos `/` com portões 🛑 | Quando o operador dispara o comando |
| `RECEITA-*.md` | Guias de referência para o **operador humano** | 🚫 **NUNCA lido por nenhuma IA** (exclusivo para humanos) |

---

## 3. O que NUNCA entra nesta pasta

- ❌ Fatos do domínio (nomes de clientes, regras de negócio, status oficiais) — isso é `contexto/`.
- ❌ Atas, transcrições e PDFs brutos — isso é `fontes/`.
- ❌ Artefatos finais entregues a terceiros — isso é `entregas/`.
- ❌ Uma skill que só repete o que uma regra `always_on` já manda.

---

## 4. Ordem sugerida ao montar um workspace novo

1. Preencha o contrato (`AGENTS.md`) — 1 página, o que somos e o que nunca fazemos.
2. Preencha o mínimo de `contexto/` (briefing + o que NÃO somos + vocabulário).
3. Ajuste ou crie personas se os chapéus atuais não cobrirem o trabalho.
4. Crie regras só para o que deve valer em silêncio.
5. Crie skills para tarefas que você vai pedir mais de uma vez.
6. Crie workflows só quando houver fases e portões humanos.
7. Troque os exemplos genéricos pelo primeiro artefato real aprovado.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA PASTA:
[ ] Cada artefato novo passou pela árvore da seção 1?
[ ] Nenhum fato de domínio foi parar em skill/regra no lugar de contexto/?
[ ] AGENTS.md continua com no máximo ~80 linhas?
-->
