# Receita: Criar um Workflow

> 💡 **PAPEL DESTE ARQUIVO:**  
> Guia o operador a criar um comando de barra (`/nome`) em `.agents/workflows/`. Um workflow é um **pipeline com portões humanos**: várias fases, várias personas/skills, e paradas obrigatórias 🛑.  
> 🚫 **DOCUMENTO EXCLUSIVO DO OPERADOR HUMANO (NUNCA DEVE SER LIDO POR IA):**  
> Este arquivo é um guia de referência técnica exclusivo para o usuário. Nenhuma IA deve ler, processar ou carregar este arquivo para a janela de contexto.  
> ⚠️ **REGRA DE OURO:** Sem portão, não é workflow — é skill longa. Se a IA puder ir do início ao fim sem sua aprovação, não crie um comando `/`; crie uma skill.

---

## 1. Quando criar (e quando não criar)

**Crie um workflow quando:**
- O trabalho tem fases que **não podem ser puladas** (diagnosticar → você aprova → redigir → você aprova → auditar).
- Cada fase exige um chapéu diferente (`@analista` depois `@escritor` depois `@critico`).
- Um erro no meio do caminho é caro (documento enviado ao time, contexto sobrescrito, comunicação externa).

**Não crie um workflow quando:**
- É uma tarefa de uma fase só → **skill**.
- É um invariante silencioso → **regra**.
- Você só quer um atalho de prompt → acrescente em `exemplos/prompts-uteis.md`.

**Contraste didático**

| ❌ Não é workflow | ✅ É workflow |
|---|---|
| "Revise este texto com as 7 lentes" | Discovery: roteiro → reunião → extração → proposta de contexto (2 portões) |
| "Escreva a história no padrão X" | Nova funcionalidade: fatia → história → auditoria → gravação (3 portões) |
| Higiene de um único arquivo | Atualizar contexto: varredura → você escolhe o que gravar → gravação |

Referências vivas neste kit: `nova-funcionalidade.md`, `discovery.md`, `atualizar-contexto.md`, `revisar-backlog.md`.

---

## 2. Anatomia e nomenclatura

```
.agents/workflows/
└── [nome-do-comando].md
```

- **Nome do arquivo = nome do comando**, em kebab-case: `nova-funcionalidade.md` → `/nova-funcionalidade`.
- **Sem prefixo numérico** (isso é convenção de `rules/`).
- **Um workflow por arquivo.** Não junte dois pipelines no mesmo comando.

O operador dispara no chat:

```text
/nome-do-comando
```

Opcionalmente na mesma mensagem: o alvo (`@fontes/...`, um parágrafo de demanda, um ID de entrega).

---

## 3. Gabarito para copiar

Crie `.agents/workflows/[nome-do-comando].md` com esta estrutura. Não pule a seção dos portões.

```markdown
# Workflow: `/[nome-do-comando]`

> 💡 **OBJETIVO DO COMANDO:**  
> [PREENCHER: uma frase. De onde parte (insumo) e onde termina (artefato ou decisão).]

---

## Fluxo de Execução com Portões

(Diagrama ASCII — no arquivo real, pode ir em cerca de código)

[Início: PREENCHER o gatilho]
        │
        ▼
[Etapa 1: @persona — verbo da fase]
        │
        ▼
   🛑 PORTÃO 1: [O que o operador precisa julgar]
        │
        ▼
[Etapa 2: @persona — verbo da fase]
        │
        ▼
   🛑 PORTÃO 2: [O que o operador precisa julgar]
        │
        ▼
[Etapa N: [gravação / encerramento]]

---

## Roteiro das Etapas

### Etapa 1: [Nome] (`@[persona]`)
1. A IA lê: [PREENCHER: arquivos `@contexto/...` ou `@fontes/...`].
2. A IA produz: [PREENCHER: o entregável intermediário desta fase].
3. 🛑 **PORTÃO 1 DE VALIDAÇÃO:**  
   > *Pergunte exatamente: "[PREENCHER: pergunta sim/não ou de escolha, em português direto.]"*  
   > **PARE AQUI E AGUARDE APROVAÇÃO.**

---

### Etapa 2: [Nome] (`@[persona]`)
1. Só inicia depois do Portão 1.
2. [PREENCHER: passos]
3. 🛑 **PORTÃO 2:**  
   > *Pergunte: "[PREENCHER]"*  
   > **PARE AQUI E AGUARDE APROVAÇÃO.**

---

### Etapa final: Encerramento
1. Aplique só o que o operador aprovou.
2. Grave em `[PREENCHER: entregas/ ou contexto/ — nunca os dois sem autorização]`.
3. Informe o caminho do arquivo e encerre. Não comece um segundo pipeline.
```

---

## 4. Regras dos portões 🛑

1. **Todo workflow tem no mínimo 1 portão.** Zero portões = skill.
2. **A pergunta do portão é literal.** Escreva a frase que a IA deve usar. Pergunta vaga ("está bom?") gera avanço automático.
3. **A IA não grava `contexto/` nem `entregas/` antes do portão que autoriza a gravação.**
4. **Uma etapa, uma persona.** Se a mesma persona faz duas fases, ainda assim separe se houver portão no meio.
5. **Não despeje o resultado de todas as etapas de uma vez.** O diagrama da seção "Fluxo" não é enfeite: é a ordem obrigatória.

**Contraste de pergunta de portão**

- ❌ *"Posso continuar?"*
- ✅ *"PO, concorda com este fatiamento e com a prioridade da primeira fatia antes de redigirmos a história completa?"*

---

## 5. Passo a passo do operador

1. **Desenhe o pipeline em 4–7 caixas** (início, fases, portões, fim) antes de escrever prosa.
2. **Nomeie o comando pelo resultado**, não pela ferramenta: `/discovery`, `/nova-funcionalidade` — não `/usar-ia`.
3. **Atribua uma persona existente a cada etapa.** Se nenhuma persona servir, crie a persona *antes* (`RECEITA-criar-persona.md`). Não invente `@nome` só no workflow.
4. **Ligue cada etapa a skills existentes** no texto ("usa a skill X"), em vez de copiar o procedimento inteiro para dentro do workflow.
5. **Declare o que o workflow NÃO faz** em uma linha no objetivo, se houver risco de escopo (ex.: não envia e-mail; não altera `contexto/` sem o portão 2).
6. **Teste recusando um portão.** Se a IA continuar mesmo assim, a frase **PARE AQUI E AGUARDE APROVAÇÃO** está fraca ou ausente — corrija.

---

## 6. O que NUNCA colocar num workflow

- ❌ O texto completo de uma skill (aponte; não duplique).
- ❌ Fatos de domínio (status, prazos) — leia `contexto/`.
- ❌ Gravação automática em `contexto/` sem portão (o contrato do workspace proíbe).
- ❌ Um segundo comando escondido no mesmo arquivo.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE WORKFLOW:
[ ] Arquivo = nome do comando em kebab-case?
[ ] Há diagrama de fluxo E pelo menos um 🛑 com pergunta literal?
[ ] Cada etapa cita persona existente e leituras concretas?
[ ] A gravação de arquivos só ocorre depois de portão explícito?
[ ] Recusar o portão impede a etapa seguinte?
-->
