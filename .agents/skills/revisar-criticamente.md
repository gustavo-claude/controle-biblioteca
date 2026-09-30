---
name: "revisar-criticamente"
description: "Audita histórias de usuário e especificações funcionais, caçando lacunas, ambiguidades e contradições com as 7 lentes de revisão. Use quando pedir para revisar história, auditar especificação, achar furos ou simular o teste do desenvolvedor irritado."
---

# Skill: Revisar Criticamente (Auditoria de Especificações)

> 💡 **MECANISMO DE DISPARO:**  
> Use esta skill para submeter qualquer história ou especificação a um crivo rigoroso antes de apresentá-la ao time técnico.

---

## 1. Entradas e Leituras Prévias

1. O documento a ser revisado (em `entregas/` ou texto no chat).
2. `.agents/rules/03-revisao-critica.md` (as 7 lentes de auditoria).
3. `@contexto/glossario.md` e `@contexto/regras-de-negocio.md`.

---

## 2. Procedimento de Revisão Passo a Passo

1. **Passo 1 — Leitura Fria das 7 Lentes:**
   - Avalie o texto buscando termos vagos, critérios não testáveis e falta de caminhos de erro.
2. **Passo 2 — Cruzamento com Regras e Glossário:**
   - Verifique se os nomes dos campos, status e termos batem 100% com o glossário.
   - Verifique se a regra descrita entra em conflito com alguma regra existente.
3. **Passo 3 — Classificação dos Apontamentos:**
   - Separe os achados em 🔴 **Bloqueantes**, 🟡 **Atenção** e 🟢 **Sugestões**.
4. **Passo 4 — O Teste do Desenvolvedor Irritado:**
   - Formule as 3 perguntas mais duras sobre casos de borda e comportamentos não especificados.
5. **Passo 5 — Emitir Parecer:**
   - Declare claramente se o item está **Apto para Refinamento** ou **Requer Correções**.

---

## 3. Gabarito de Saída (Relatório de Auditoria)

```markdown
# Relatório de Auditoria: [Nome da História / Documento]

## 1. Veredito Geral
- **Status:** [ 🔴 REPROVADO (Requer ajustes) | 🟡 APROVADO COM RESSALVAS | 🟢 APROVADO ]
- **Resumo do Parecer:** [Avaliação em 2 linhas sobre a maturidade do documento]

## 2. Apontamentos pelas 7 Lentes

| Severidade | Lente | Localização | Problema Identificado | Correção Sugerida |
|:--:|---|---|---|---|
| 🔴 **Bloqueante** | Testabilidade | Cenário 2 | Critério "deve ser rápido" não dá métrica | Definir tempo máximo (ex: < 2s) |
| 🔴 **Bloqueante** | Completude | Cenário de Erro | Não diz o que ocorre se o anexo passar de 10MB | Adicionar validação de tamanho com mensagem clara |
| 🟡 **Atenção** | Glossário | Narrativa | Usou o termo 'Ticket' em vez de 'Chamado' | Ajustar para o termo oficial do glossário |
| 🟢 **Sugestão** | Clareza | Seção 1 | Dividir a primeira frase para facilitar leitura | Sugestão de redação pontual |

## 3. Perguntas do Teste do "Dev Irritado"
1. *"O que acontece se dois atendentes tentarem assumir o mesmo chamado no mesmo segundo?"*
2. *"Se o usuário fechar a aba do navegador antes de salvar, os dados são guardados em rascunho?"*
3. *"O cancelamento de chamado exige justificativa obrigatória por texto?"*
```

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] As 7 lentes foram inspecionadas?
[ ] Os apontamentos possuem severidade visual (🔴, 🟡, 🟢)?
[ ] As perguntas do Dev Irritado atacam cenários de borda reais?
-->
