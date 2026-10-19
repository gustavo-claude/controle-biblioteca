# Receita: Criar uma Regra

> 💡 **PAPEL DESTE ARQUIVO:**  
> Guia o operador a criar uma regra nova em `.agents/rules/`. Uma regra é um **invariante de comportamento**: vale em silêncio, sem o operador lembrar de pedir.  
> 🚫 **DOCUMENTO EXCLUSIVO DO OPERADOR HUMANO (NUNCA DEVE SER LIDO POR IA):**  
> Este arquivo é um guia de referência técnica exclusivo para o usuário. Nenhuma IA deve ler, processar ou carregar este arquivo para a janela de contexto.  
> ⚠️ **REGRA DE OURO:** Se o operador precisa *acionar* o procedimento, é skill. Se a IA precisa *não esquecer* de uma postura, é regra. Regras demais tornam a IA lenta e contraditória — prefira poucas, curtas e inegociáveis.

---

## 1. Quando criar (e quando não criar)

**Crie uma regra quando:**
- A IA erra *mesmo depois* de você corrigir no chat (o erro volta na conversa seguinte).
- O padrão vale para **todo** o workspace ou para **toda** uma família de arquivos.
- É uma proibição ou uma estrutura obrigatória, não um roteiro de trabalho.

**Não crie uma regra quando:**
- É um procedimento com passos e gabarito → **skill**.
- É um fato do domínio (status, prazos, nomes) → **contexto**.
- Só se aplica a um único arquivo pontual → anote no próprio arquivo ou em `decisoes.md`.
- Já existe regra cobrindo o mesmo invariante. Edite a existente; não empilhe outra.

**Contraste didático**

| ❌ Não é regra | ✅ É regra |
|---|---|
| "Como redigir uma ata em 6 passos" | "Toda suposição deve levar `⚠️ [SUPOSIÇÃO]`" |
| Lista de personas reais do cliente | "Nunca usar sinônimo fora do glossário" |
| Pipeline discovery → escrita → revisão | "Critério de aceite subjetivo é inválido" |

Referências vivas neste kit:
- Sempre ligada: `00-fundacao.md`, `01-estilo-e-tom.md`
- Por pasta/arquivo: `02-padrao-historias.md` (`globs: "entregas/**"`)
- Sob demanda (persona/skill aponta): `03-revisao-critica.md`

---

## 2. Anatomia e nomenclatura

```
.agents/rules/
├── 00-fundacao.md
├── 01-estilo-e-tom.md
├── 02-padrao-historias.md
├── 03-revisao-critica.md
└── [NN]-[assunto-em-kebab].md
```

- **Prefixo numérico de 2 dígitos**, sequencial (`00`, `01`, `02`…). O próximo arquivo usa o menor número livre.
- **Assunto em kebab-case**, curto, descrevendo o invariante (`estilo-e-tom`, não `regras-gerais`).
- **Não reutilize um número** se uma regra for revogada: marque `[REVOGADA]` no topo e crie outro arquivo.

| Número | Tipo de invariante (kit atual) |
|---|---|
| `00` | Fundação: integridade, autoridade, o que a IA nunca faz |
| `01` | Tom, idioma, palavras banidas |
| `02` | Padrão de um tipo de artefato (quando aquele tipo for gerado) |
| `03` | Protocolo de revisão / qualidade |
| `04+` | Invariantes novos do *seu* domínio (ética, tom institucional, formato legal, etc.) |

---

## 3. Três modos de ativação (escolha um)

O frontmatter define *quando* a regra entra na janela de contexto. Escolher errado ou infla o contexto ou deixa a regra morta.

| Modo | Frontmatter | Use quando |
|---|---|---|
| **Sempre ligada** | `always_on: true` | Integridade e tom. Máximo 2–3 regras neste modo. |
| **Por arquivos** | `globs: "pasta/**"` | O padrão só importa ao ler/escrever aqueles arquivos. |
| **Sob demanda** | Só `description` (sem `always_on`, sem `globs`) | A persona ou a skill cita o arquivo. Não gasta tokens o tempo todo. |

Não combine `always_on: true` com `globs` na mesma regra — o glob fica sem efeito útil e a intenção fica ambígua.

---

## 4. Frontmatter e gabarito do corpo

**Sempre ligada**

```markdown
---
description: "[PREENCHER: invariante em uma frase, para o seletor de regras]"
always_on: true
---

# Regra [NN] — [Título do invariante]

> 💡 **MODO DE ATIVAÇÃO:** `always_on: true`  
> [PREENCHER: em que tipo de conversa isso vale — em geral: todas.]

---

## 1. [Nome do invariante]

- ✅ **O que FAZER:** [PREENCHER: comportamento observável]
- ❌ **O que NÃO fazer:** [PREENCHER: o erro que esta regra existe para impedir]

---

## 2. Contraste Didático

- ❌ [PREENCHER: frase típica da IA desobedecendo]
- ✅ [PREENCHER: a mesma situação, correta]

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA REGRA:
[ ] O invariante é testável (dá para dizer se foi violado)?
[ ] Há contraste ❌/✅?
[ ] Esta regra precisa ser always_on, ou um glob / skill bastaria?
-->
```

**Por arquivos**

```yaml
---
description: "[PREENCHER]"
globs: "[PREENCHER: ex. entregas/** ou fontes/**/*.md]"
---
```

**Sob demanda** — omita `always_on` e `globs`. No corpo, escreva: *"Ativada quando a persona @X ou a skill Y for invocada."* E **cite o caminho deste arquivo** nessa persona/skill.

---

## 5. Passo a passo do operador

1. **Escreva o invariante em uma frase negativa ou positiva inequívoca.**  
   Ex.: "Não inventar números." / "Critérios de aceite são binários: passou ou falhou."
2. **Escolha o modo de ativação** (tabela da seção 3). Na dúvida, comece sob demanda.
3. **Pegue o próximo número livre** (`04` se `00`–`03` já existem). Não renumere arquivos antigos.
4. **Redija o corpo com FAZER / NÃO fazer e um par ❌/✅.** Sem isso, a IA interpreta a regra como conselho.
5. **Se for sob demanda:** acrescente o `@.agents/rules/NN-assunto.md` na lista de leituras da persona ou da skill correspondente.
6. **Se for `always_on`:** releia `AGENTS.md`. Se o invariante já está lá, não duplique — o contrato deve continuar sendo a fonte curta.

---

## 6. O que NUNCA colocar numa regra

- ❌ Roteiro de 8 passos com gabarito de documento (isso é skill).
- ❌ Portões 🛑 e troca de persona (isso é workflow).
- ❌ Catálogo de termos do domínio (isso é `contexto/glossario.md`).
- ❌ Texto longo: regra `always_on` compete com *toda* conversa. Meta: 1 página.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA REGRA:
[ ] Nome no padrão NN-assunto.md, sequencial?
[ ] Um único modo de ativação, coerente com o custo de tokens?
[ ] Invariante testável, com ❌ e ✅?
[ ] Não duplica AGENTS.md nem uma skill existente?
-->
