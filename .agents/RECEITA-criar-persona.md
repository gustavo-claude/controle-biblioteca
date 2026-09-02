# Receita: Criar uma Persona

> 💡 **PAPEL DESTE ARQUIVO:**  
> Guia o operador a acrescentar um chapéu novo no catálogo `.agents/agents.md`. Persona não é "um jeito de falar": é um **papel com missão, momento de entrada, leituras e restrição**.  
> 🚫 **DOCUMENTO EXCLUSIVO DO OPERADOR HUMANO (NUNCA DEVE SER LIDO POR IA):**  
> Este arquivo é um guia de referência técnica exclusivo para o usuário. Nenhuma IA deve ler, processar ou carregar este arquivo para a janela de contexto.  
> ⚠️ **REGRA DE OURO:** Se duas personas responderiam a mesma pergunta do mesmo jeito, a segunda é inútil. Ninguém revisa bem o próprio texto — o valor da persona é o *olhar diferente*.

---

## 1. Quando criar (e quando não criar)

**Crie uma persona quando:**
- O workspace precisa de um modo de trabalho que as atuais **não** cobrem (organizar, analisar, redigir, auditar, negociar, traduzir público, etc.).
- Você percebe a IA misturando papéis (escreve e já se autoaprova; facilita e já decide regra de negócio).
- A restrição é tão importante quanto a missão ("não reescreve", "não grava contexto sozinha", "não propõe tela").

**Não crie uma persona quando:**
- Você só quer um tom de voz → isso é **regra** de estilo.
- Você só quer um procedimento → isso é **skill**.
- O "chapéu" é um usuário real do produto (Carlos, a atendente) → isso é `contexto/personas-usuario.md`, não persona de IA.

Neste kit as quatro atuais são o modelo de separação:
- `@facilitador` organiza contexto e **não grava** sem você.
- `@analista` explora e fatia e **não redige** o artefato formal.
- `@escritor` redige no padrão e **não inventa** regra nova em silêncio.
- `@critico` aponta furos e **não reescreve**.

Mantenha entre **3 e 6** personas ativas. Acima disso, a IA escolhe o chapéu errado.

---

## 2. Anatomia de uma entrada no catálogo

Toda persona em `agents.md` usa o mesmo bloco. Não invente seções extras no lugar destas.

```markdown
## [N]. `@[nome-em-kebab]` — [Apelido de uma linha]

- **Missão:** [PREENCHER: o resultado que esta persona existe para produzir]
- **Quando chamar:** [PREENCHER: situação do operador + 2–3 gatilhos em linguagem natural]
- **O que lê:** [PREENCHER: lista curta de `@contexto/...`, regras e exemplos. Só o que muda a resposta.]
- **Comportamento:**
  - [PREENCHER: 2 a 4 bullets de postura observável]
- **Restrição:** [PREENCHER: uma frase. O que esta persona é expressamente proibida de fazer.]
```

| Campo | Função | Erro comum |
|---|---|---|
| `@nome` | Como o operador aciona no chat | Nome genérico (`@assistente`, `@ia`) ou com espaço |
| Missão | Um resultado, não uma lista de tarefas | "Ajuda no que for preciso" |
| Quando chamar | Gatilhos reais | "Sempre que necessário" |
| O que lê | Âncora contra alucinação | Ler o workspace inteiro |
| Restrição | Impede invasão de outro chapéu | Restrição ausente ou igual à missão |

**Contraste didático**

- ❌ `@revisor` — "Melhora os textos do projeto." (sem restrição; invade o escritor)
- ✅ `@critico` — Missão: achar furos. Restrição: não reescreve; classifica 🔴/🟡/🟢 e pergunta.

---

## 3. Passo a passo do operador

1. **Escreva a restrição primeiro.** Se você não consegue dizer o que a persona *não* faz, ainda não há chapéu — há uma skill disfarçada.
2. **Confira o catálogo atual.** A missão nova é mesmo distinta das 4 (ou N) existentes?
3. **Escolha um `@nome` curto**, só minúsculas e hífen: `@facilitador`, `@analista`, `@auditor-lgpd`.
4. **Copie o gabarito da seção 2** para o final de `agents.md`, *antes* do checklist HTML.
5. **Preencha Missão / Quando / Lê / Comportamento / Restrição.** Sem bullets vazios.
6. **Ligue a persona ao resto do sistema:**
   - Se um workflow deve usá-la, cite `@nome` na etapa correspondente.
   - Se ela precisa de um invariante próprio, crie a regra *sob demanda* e coloque o caminho em "O que lê".
7. **Atualize o checklist** no rodapé de `agents.md` (número de personas, restrições distintas).
8. **Registre no contrato só se o papel do workspace mudar.** Não liste 12 personas em `AGENTS.md` — o contrato aponta para `agents.md`.

---

## 4. Como acionar

No chat:

```markdown
@[nome] [pedido concreto]. Leia @[arquivo-de-contexto-ou-fonte] se o pedido depender de fato.
```

Não peça duas personas na mesma mensagem para o mesmo parágrafo ("@escritor @critico faça os dois"). O workflow existe precisamente para sequenciar chapéus com portão.

---

## 5. O que NUNCA fazer ao criar persona

- ❌ Editar uma persona existente para acumular a missão nova ("o escritor também critica").
- ❌ Criar persona que grava `contexto/` sozinha — o contrato exige autorização explícita.
- ❌ Duplicar `contexto/personas-usuario.md` (pessoas reais) como `@carlos`.
- ❌ Deixar "O que lê" vazio: a persona sem âncora inventa vocabulário.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA PERSONA:
[ ] Missão, momento, leituras e restrição estão preenchidos?
[ ] A restrição impede sobreposição com outra persona do catálogo?
[ ] O @nome é kebab-case e acionável no chat?
[ ] Workflows/skills que deveriam chamá-la foram atualizados?
[ ] O total de personas ativas continua entre 3 e 6?
-->
