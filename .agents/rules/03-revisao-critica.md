---
description: "Diretrizes e matriz das 7 lentes para revisão crítica e auditoria de histórias de usuário."
---

# Regra 30 — Protocolo de Revisão Crítica e Auditoria

> 💡 **MODO DE ATIVAÇÃO:** Ativada durante a execução de revisões ou quando a persona `@critico` é invocada.

---

## 1. As 7 Lentes de Auditoria

Todo documento inspecionado deve ser submetido às 7 lentes obrigatórias:

| # | Lente | O que verificar | Sinal de alerta (Perigo) |
|---|---|---|---|
| **1** | **Clareza** | O texto é direto e livre de dupla interpretação? | Uso de "etc", "conforme o caso", "quando apropriado" |
| **2** | **Testabilidade** | O QA/tester consegue criar um teste automatizado ou manual? | Critérios subjetivos ("deve ser fácil", "tempo hábil") |
| **3** | **Completude** | Foram tratados os cenários de erro, falta de dados e limites? | Apenas caminho feliz documentado |
| **4** | **Glossário e Regras** | Os termos batem com o glossário? Fere alguma regra existente? | Uso de termos proibidos ou sinônimos soltos |
| **5** | **Não-Intromissão Técnica** | O PO respeitou a fronteira da engenharia? | Menção a nomes de tabelas, frameworks ou endpoints |
| **6** | **Fatia Vertical** | A entrega tem valor para o usuário ou é fatia horizontal? | Histórias que são só "criar tela" sem salvar ou só "criar API" |
| **7** | **Origem das Afirmações** | Toda regra ou número tem respaldo verificado? | Números e prazos mágicos sem origem documentada |

---

## 2. Classificação de Apontamentos por Severidade

Ao auditar uma história, organize os apontamentos na seguinte taxonomia visual:

- 🔴 **BLOQUEANTE:** Furo grave que impede a engenharia de codificar sem ter que tomar decisões de negócio por conta própria.
- 🟡 **ATENÇÃO:** Ambiguidade, falta de estado vazio ou risco de retrabalho na interface.
- 🟢 **SUGESTÃO:** Oportunidade de melhoria na redação, concisão ou formatação.

---

## 3. O Teste do "Desenvolvedor Irritado"

Ao finalizar a análise das 7 lentes, o revisor deve formular de 2 a 4 perguntas diretas simulando o desenvolvedor que recebeu o card na sprint:
- *"O que acontece se o usuário clicar duas vezes no botão de submeter?"*
- *"Se a conexão cair durante o envio, os dados preenchidos são preservados ou perdidos?"*
- *"Quem tem permissão para cancelar este chamado depois que ele entrou em atendimento?"*

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA REGRA:
[ ] Todas as 7 lentes foram avaliadas?
[ ] Os apontamentos foram categorizados com 🔴, 🟡 e 🟢?
[ ] As perguntas do "Dev Irritado" atacam ambiguidades de borda?
-->
