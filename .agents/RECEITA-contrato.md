# Receita: Adaptar o Contrato (`AGENTS.md`)

> 💡 **PAPEL DESTE ARQUIVO:**  
> Guia o operador a preencher ou reescrever o `AGENTS.md` da raiz — o **único arquivo lido compulsoriamente** no início de toda conversa.  
> 🚫 **DOCUMENTO EXCLUSIVO DO OPERADOR HUMANO (NUNCA DEVE SER LIDO POR IA):**  
> Este arquivo é um guia de referência técnica exclusivo para o usuário. Nenhuma IA deve ler, processar ou carregar este arquivo para a janela de contexto.  
> ⚠️ **REGRA DE OURO:** Máximo ~80 linhas / 1 página. Se o contrato inchar, a IA passa a ignorar o que mais importa. Fatos longos não entram aqui: entram em `contexto/`.

---

## 1. O que o contrato faz (e o que ele não faz)

| Faz | Não faz |
|---|---|
| Declara **onde a IA está** (tipo de trabalho) | Listar todas as regras de domínio |
| Lista **o que se produz** e **o que nunca se produz** | Substituir skills, workflows ou personas |
| Aponta **quais arquivos de contexto** ler antes de responder | Narrar a história da empresa |
| Define postura: perguntar, marcar suposição, uma etapa por vez | Ensinar o procedimento de uma tarefa |

Este workspace já tem um contrato de Product Ownership. Para usá-lo em **outro tipo de trabalho** (parecer jurídico, pesquisa, operação, conteúdo, ensino, etc.), você **substitui o conteúdo das seções**, não a estrutura. Não apague o arquivo; não mova as seções de lugar.

---

## 2. Estrutura obrigatória (não invente uma sexta seção longa)

Mantenha estes 5 blocos, nesta ordem:

```markdown
# AGENTS.md — Contrato de Trabalho do Workspace

> 💡 **PAPEL DESTE ARQUIVO:**  
> Contrato lido em toda conversa. Curto de propósito.

---

## 1. Onde você está

Este workspace é o ambiente de **[PREENCHER: tipo de trabalho — uma frase]**.

Aqui **NÃO se faz:** [PREENCHER: 2–4 proibições de papel, não de domínio].

O que se produz aqui:
- [PREENCHER: tipo de artefato 1]
- [PREENCHER: tipo de artefato 2]
- [PREENCHER: tipo de artefato 3]

> **Local de Saída:** [PREENCHER: pasta e padrão de nome, em geral `entregas/AAAA-MM-DD-assunto.md`]

---

## 2. Antes de responder qualquer coisa, leia

- `@contexto/[arquivo].md` — [PREENCHER: por que este arquivo existe]
- `@contexto/[arquivo].md` — [PREENCHER]
- `@contexto/[arquivo].md` — [PREENCHER]

(Só liste arquivos que *existem* e que, se ignorados, a IA erra. 4 a 8 itens. Nunca "leia a pasta inteira".)

---

## 3. Como você deve se comportar

1. **Pergunte antes de inventar:** no máximo 3 a 5 perguntas objetivas.
2. **Separe Fato de Suposição:** fato = contexto ou fala do operador; hipótese = `⚠️ [SUPOSIÇÃO]`.
3. **Uma etapa por vez:** [PREENCHER: o que não despejar de uma vez no seu domínio].
4. **Tom e Linguagem:** [PREENCHER: idioma e tom. Apontar a regra `01-estilo-e-tom.md` se ela continuar válida].

---

## 4. O que NUNCA fazer

- ❌ [PREENCHER: proibição 1 — a mais cara se for violada]
- ❌ [PREENCHER: proibição 2 — inventar dados / números / normas]
- ❌ **NUNCA alterar `contexto/` sem autorização explícita do operador**
- ❌ [PREENCHER: proibição 4 — critério de qualidade subjetiva, se aplicável]

---

## 5. Personas, Habilidades, Fluxos e Receitas

- **Personas:** `@.agents/agents.md`
- **Skills:** `.agents/skills/` (como criar: `.agents/skills/RECEITA-skills.md`)
- **Workflows:** `.agents/workflows/` (como criar: `.agents/workflows/RECEITA-workflow.md`)
- **Regras:** `.agents/rules/` (como criar: `.agents/rules/RECEITA-rules.md`)
- **Mapa:** `.agents/README.md`
```

A seção 5 é índice, não conteúdo. Se você copiar o texto das skills para o contrato, o contrato morre de tamanho.

---

## 3. Passo a passo do operador

1. **Escreva a frase "Onde você está" primeiro.** Tudo o mais deriva dela.  
   Exemplos de *tipo de trabalho* (não copie se não for o seu): especificação de produto; dossiê de pesquisa; operação de um processo interno; redação institucional.
2. **Preencha "NÃO se faz" com limites de papel.**  
   Ex.: este kit original *não escreve código de produção*. O seu pode ser "não envia mensagem a cliente" ou "não emite opinião jurídica vinculante".
3. **Aponte os arquivos de contexto que de fato existem.** Se ainda estão `[PREENCHER]`, o contrato já pode listá-los — a IA vai ver as lacunas e perguntar.
4. **Mantenha as 4 posturas da seção 3** (perguntar, marcar suposição, uma etapa, tom), adaptando só o exemplo da etapa.
5. **Conte as linhas.** Acima de ~80, corte adjetivos, listas e exceções. Exceções longas vão para `contexto/decisoes.md` ou para uma regra.
6. **Não crie um segundo contrato** em `.agents/`. Um só, na raiz, com este nome: `AGENTS.md`.

---

## 4. Relação com as regras `always_on`

- O contrato diz *o papel*.
- `00-fundacao.md` e `01-estilo-e-tom.md` detalham *integridade e tom*.
- Se a mesma frase estiver nos dois, apague do mais longo. O contrato ganha.

---

## 5. O que NUNCA fazer no contrato

- ❌ Transformá-lo em README do projeto (isso é `LEIA-ME.md`).
- ❌ Colar glossário, lista de RNs ou personas completas.
- ❌ Instruções técnicas de ferramenta (atalhos do editor, versão do modelo).
- ❌ Autorizar a IA a gravar `contexto/` "quando achar necessário".

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DO CONTRATO:
[ ] Cabe em ~80 linhas?
[ ] Seção 1 declara o tipo de trabalho E o que nunca se produz?
[ ] Seção 2 lista só arquivos de contexto reais, com o motivo de cada um?
[ ] Seção 4 tem proibições testáveis, incluindo a de não alterar contexto/ sozinho?
[ ] Seção 5 é só ponteiro, sem copiar skill/regra?
-->
