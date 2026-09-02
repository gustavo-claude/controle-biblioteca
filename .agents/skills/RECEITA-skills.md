# Receita: Criar uma Skill

> 💡 **PAPEL DESTE ARQUIVO:**  
> Guia o operador a criar uma skill nova em `.agents/skills/`. Uma skill é um **procedimento repetível**: entradas, passos e gabarito de saída para um tipo de tarefa.  
> 🚫 **DOCUMENTO EXCLUSIVO DO OPERADOR HUMANO (NUNCA DEVE SER LIDO POR IA):**  
> Este arquivo é um guia de referência técnica exclusivo para o usuário. Nenhuma IA deve ler, processar ou carregar este arquivo para a janela de contexto.  
> ⚠️ **REGRA DE OURO:** Skill ensina *como executar um trabalho*. Regra ensina *o que nunca violar*. Workflow orquestra *várias skills/personas com portões*. Se não houver passos e um formato de saída, ainda não é skill.

---

## 1. Quando criar (e quando não criar)

**Crie uma skill quando:**
- Você vai pedir o mesmo tipo de trabalho mais de uma vez (redigir, auditar, mapear, comunicar, classificar).
- A qualidade da saída depende de uma ordem de passos e de um gabarito.
- A IA precisa consultar arquivos específicos antes de começar.

**Não crie uma skill quando:**
- O que você quer é uma proibição permanente → isso é **regra**.
- O trabalho tem 3+ fases com aprovação humana no meio → isso é **workflow**.
- O conteúdo é um fato do domínio (prazo, status, persona real) → isso é **contexto**.
- Já existe uma skill que cobre o pedido com outro nome. Amplie a `description` da existente.

**Contraste didático**

| ❌ Não é skill | ✅ É skill |
|---|---|
| "A IA deve escrever em português direto" | Passos para redigir um tipo de documento com seções fixas |
| "Nunca inventar números" | Procedimento de extração de fatos de uma ata |
| Lista de status oficiais do domínio | Procedimento para *atualizar* o glossário a partir de uma reunião |

Referência viva neste kit: `.agents/skills/escrever-historia.md`.

---

## 2. Anatomia de uma skill neste workspace

```
.agents/skills/
├── RECEITA-skills.md
└── [nome-em-kebab].md
```

Mesmo padrão de `rules/` e `workflows/`: **um arquivo por skill**, sem subpasta.

- **Nome do arquivo = `name` no frontmatter** (sem a extensão `.md`). Só minúsculas, números e hífens. Máximo 64 caracteres. Evite `helper`, `utils`, `tools`.
- **Material longo (opcional):** se um anexo for necessário, crie um irmão `[nome]-referencia.md` na mesma pasta e *linke* a partir da skill. Não encadeie referências.
- **Tamanho:** o arquivo da skill deve caber em uma leitura só (meta: < 200 linhas; teto duro: 500).

---

## 3. Frontmatter (obrigatório)

A `description` é o mecanismo de disparo. A IA decide *quando* usar a skill lendo essa frase.

```yaml
---
name: "[PREENCHER: nome-em-kebab igual ao arquivo, sem .md]"
description: "[PREENCHER: O QUE a skill faz, em terceira pessoa. Use quando: gatilhos e sinônimos que o operador diria no chat.]"
---
```

| Campo | Exigência | Erro comum |
|---|---|---|
| `name` | Igual ao arquivo (sem `.md`); kebab-case | `EscreverHistoria` ou nome diferente do arquivo |
| `description` | O QUE + QUANDO; 3ª pessoa; termos de disparo | "Eu ajudo a escrever" / "ajuda com documentos" |

**Contraste de description**

- ❌ `"Ajuda com textos."`
- ✅ `"Escreve uma história de usuário completa com critérios de aceite testáveis no padrão oficial. Use quando o usuário pedir para redigir uma história, criar card, fazer user story, detalhar requisito ou converter pedido em especificação."`

---

## 4. Corpo: seções mínimas

Use exatamente estas seções no arquivo da skill. Apague só se a tarefa realmente não tiver saída gravável.

```markdown
# Skill: [Nome legível da tarefa]

> 💡 **MECANISMO DE DISPARO:**  
> [PREENCHER: 1–2 frases. Quando o operador deve acionar isto e o que a skill garante.]

---

## 1. Entradas e Leituras Prévias Obrigatórias

Antes de executar, a IA deve consultar:
1. [PREENCHER: arquivo de contexto ou regra — e *por quê*]
2. [PREENCHER: segundo arquivo]
3. [PREENCHER: exemplo de qualidade, se existir em exemplos/]

---

## 2. Procedimento de Execução Passo a Passo

1. **Passo 1 — [Verbo + objeto]:**
   - [PREENCHER: ação concreta. Uma decisão por passo.]
   - [O que perguntar se faltar dado. Não inventar.]

2. **Passo 2 — [Verbo + objeto]:**
   - [PREENCHER]

3. **Passo 3 — [Montar a saída no gabarito da seção 3]:**
   - [PREENCHER]

4. **Passo 4 — [Onde gravar, se houver artefato]:**
   - Salve em `[PREENCHER: pasta/padrão-de-nome.md]`.
   - Se não houver autorização para gravar, entregue no chat e pergunte.

---

## 3. Estrutura do Gabarito de Saída

No arquivo da skill, envolva o bloco abaixo em uma cerca de código markdown para a IA copiar o formato:

# [PREENCHER: título do artefato]

## 1. [Seção]
- [PREENCHER]

## 2. [Seção]
- [PREENCHER]

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] As leituras prévias foram feitas?
[ ] O gabarito foi preenchido sem seções vazias silenciosas?
[ ] Lacunas estão marcadas com [CONFIRMAR] ou ⚠️ [SUPOSIÇÃO]?
-->
```

---

## 5. Passo a passo do operador (criar a skill)

1. **Nomear a tarefa em um verbo:** `escrever-parecer`, `classificar-insumo`, `montar-comunicado`.
2. **Escrever a `description` antes do corpo.** Se você não consegue listar 3 frases que o operador diria no chat, a skill ainda está vaga.
3. **Listar o que a IA deve ler.** Só arquivos que mudam a resposta. Cada `@arquivo` custa tokens.
4. **Redigir 3 a 6 passos.** Um passo = uma decisão. Se um passo tiver 8 bullets, quebre.
5. **Colar o gabarito de saída.** A skill sem gabarito produz formato diferente a cada vez.
6. **Declarar o que a skill NÃO faz** (restrição), se houver risco de invadir outra skill ou o papel de engenharia/operação.
7. **Validar com o checklist do final deste arquivo.** Só então peça um teste real no chat.

---

## 6. O que NUNCA colocar numa skill

- ❌ Fatos que mudam (prazos, nomes, IDs de regra de negócio) — aponte para `contexto/`.
- ❌ "Você pode usar o método A, ou B, ou C..." sem um padrão default.
- ❌ Solução técnica de implementação (tabelas, endpoints, bibliotecas) se o workspace for de especificação, não de código.
- ❌ Frontmatter de regra (`always_on`, `globs`) — isso não pertence a skill.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA SKILL:
[ ] Arquivo e name são iguais (kebab-case, sem .md)?
[ ] description tem O QUE + QUANDO, em terceira pessoa, com gatilhos reais?
[ ] Há leituras prévias, passos numerados e gabarito de saída?
[ ] O arquivo tem menos de 200 linhas (ou justifica um [nome]-referencia.md)?
[ ] Não duplica uma regra always_on nem um workflow com portões?
-->
