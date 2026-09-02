# Receita: Criar um Novo Documento em `contexto/`

> 💡 **PAPEL DESTE ARQUIVO:**  
> Guia o operador a acrescentar um arquivo de fatos em `contexto/` quando o conjunto atual não cobre o domínio — ou quando este kit for usado para um trabalho que **não** é produto de software.  
> 🚫 **DOCUMENTO EXCLUSIVO DO OPERADOR HUMANO (NUNCA DEVE SER LIDO POR IA):**  
> Este arquivo é um guia de referência técnica exclusivo para o usuário. Nenhuma IA deve ler, processar ou carregar este arquivo para a janela de contexto.  
> ⚠️ **REGRA DE OURO:** `contexto/` é o cérebro **destilado**. Se a IA precisa da linha para não errar, a linha entra. Se é ata, adjetivo ou manual técnico, fica de fora.

---

## 1. Quando criar um arquivo novo (e quando só editar)

**Crie um arquivo novo quando:**
- O tema tem ciclo de vida próprio (atualiza em momento diferente dos outros).
- Misturar o tema em um arquivo existente faria esse arquivo passar de ~3 páginas.
- Você precisa que a IA *aponte* um único `@contexto/nome.md` no contrato ou numa skill.

**Não crie um arquivo novo quando:**
- É um termo → acrescente em `glossario.md`.
- É uma invariante numerada → `regras-de-negocio.md` (ou o catálogo equivalente do seu domínio).
- É uma decisão com alternativas descartadas → `decisoes.md`.
- É material bruto → `fontes/`.

Os arquivos já existentes (`briefing.md`, `produto.md`, `personas-usuario.md`, etc.) **não devem ser apagados**. Se o workspace deixar de ser um produto de software, você os *repreenche* ou os deixa como modelo e cria irmãos com nomes do novo domínio.

---

## 2. Anatomia de um documento de contexto

Todo arquivo novo copia esta casca. É o mesmo padrão dos documentos atuais da pasta.

```markdown
# [Título do documento]: [Nome do objeto]

> 💡 **PAPEL DESTE ARQUIVO:**  
> [PREENCHER: uma frase. O que a IA ganha ao ler isto. O que este arquivo *não* substitui.]  
> ⚠️ **REGRA DE OURO:** [PREENCHER: o invariante de preenchimento — tamanho, vocabulário fechado, IDs permanentes, etc.]

---

## 1. [Seção de fatos]

- **[Campo]:** [PREENCHER: fato. Sem adjetivo vazio.]
- **[Campo]:** [PREENCHER]

---

## 2. Contraste Didático de Preenchimento

### ❌ Exemplo Fraco:
> [PREENCHER: o tipo de texto que você *não* quer que a IA imite]

### ✅ Exemplo Bom:
> [PREENCHER: o mesmo campo, concreto. Pode ser de um domínio neutro se o real ainda não estiver decidido.]

---

## 3. O que este arquivo NÃO cobre

- ❌ [PREENCHER: para onde vai essa informação — outro contexto, fontes/ ou entregas/]

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] [PREENCHER: 3 critérios objetivos — tamanho, campos obrigatórios, proibições]
-->
```

---

## 3. Nomenclatura e registro

| Item | Convenção |
|---|---|
| Nome do arquivo | kebab-case, sem data (`glossario.md`, não `2026-08-glossario.md`). Data é para `fontes/` e `entregas/`. |
| Tamanho | 1–3 páginas, salvo diários como `decisoes.md`. |
| Idioma | Português do Brasil, fatos, sem marketês. |

Depois de criar o arquivo:

1. Acrescente uma **linha na tabela** de `contexto/README.md` (arquivo, para que serve, tamanho, quando atualizar).
2. Se a IA deve lê-lo **em toda conversa**, acrescente na seção 2 de `AGENTS.md` (e tire outro item se o contrato passar de ~80 linhas).
3. Se só algumas skills precisam dele, cite o `@contexto/nome.md` nas leituras da skill — não no contrato.

---

## 4. A Régua (aplique em cada linha)

> "Se eu apagar esta linha, a IA erra a resposta?"
> - **Sim** → a linha fica.
> - **Não** → apague. É decoração.

Números, prazos e nomes próprios exigem origem. Se a origem ainda não existe, use `[CONFIRMAR]` — nunca um valor inventado.

---

## 5. O que NUNCA entra em `contexto/`

- ❌ Textos promocionais.
- ❌ Atas completas (vão para `fontes/`; o facilitador *propõe* o destilado).
- ❌ Procedimento da IA (vão para `.agents/`).
- ❌ Artefato entregue a terceiros (vão para `entregas/`).
- ❌ A IA gravar sozinha. Alteração nesta pasta exige autorização explícita do operador.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DO NOVO DOCUMENTO:
[ ] Tem bloco PAPEL + REGRA DE OURO no topo?
[ ] Tem contraste ❌/✅ ou equivalente que calibre o preenchimento?
[ ] Foi registrado no README desta pasta?
[ ] Só foi listado em AGENTS.md se for leitura compulsória?
[ ] Passa na régua "se apagar, a IA erra"?
-->
