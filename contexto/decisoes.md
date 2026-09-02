# Registro de Decisões de Produto (ADRs de Negócio)

> 💡 **PAPEL DESTE ARQUIVO:**  
> Registra o histórico de decisões estratégicas e funcionais tomadas para o produto. Ele impede que debates já superados sejam reabertos semanalmente e orienta a IA sobre escolhas anteriores.  
> 🔄 **A CLÁUSULA ESSENCIAL:** A linha *"Revisitar se..."* é obrigatória. Sem ela, decisões viram dogmas imutáveis mesmo quando o cenário muda.

---

## `[DEC-01]` — [Título da Decisão — Ex: Modelo de Notificação de Chamados]

- **Data da Decisão:** `[AAAA-MM-DD]` · **Decidido por:** `[Nome do PO / Stakeholders]`
- **Status:** `[🟢 Ativa | 🟡 Em Revisão | ⚪ Substituída por DEC-XX]`

### 1. Contexto e Problema
- [PREENCHER: Qual era o dilema ou dúvida que precisava de uma escolha formal]  
  *Ex: Usuários reclamavam que não sabiam quando o chamado era atualizado. Havia pressão para criar notificações via SMS, WhatsApp e E-mail simultaneamente.*

### 2. Decisão Tomada
- [PREENCHER: O caminho escolhido de forma direta]  
  *Ex: Adotar exclusivamente notificações via E-mail corporativo no lançamento inicial.*

### 3. Alternativas Descartadas e Motivo
- ❌ **WhatsApp:** Descartado devido ao custo de disparo por mensagem e complexidade de integração com a API oficial no curto prazo.
- ❌ **SMS:** Descartado por baixa adesão dos colaboradores a números de celular corporativo.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:**  
  *Ex: Mais de 30% dos chamados continuarem sem resposta do usuário após 48h do e-mail enviado OU se a empresa contratar um pacote unificado de WhatsApp corporativo.*

---

## `[DEC-02]` — [Título da Decisão — Ex: Triagem Manual vs. Distribuição Automática]

- **Data da Decisão:** `[AAAA-MM-DD]` · **Decidido por:** `[Nome do PO]`
- **Status:** `[🟢 Ativa]`

### 1. Contexto e Problema
- [PREENCHER: O dilema de processo]  
  *Ex: Dúvida sobre implementar um algoritmo de distribuição automática (round-robin) de chamados ou manter a triagem manual por um supervisor.*

### 2. Decisão Tomada
- [PREENCHER: A escolha]  
  *Ex: Manter a triagem manual pelo supervisor N1 nos primeiros 3 meses de operação.*

### 3. Alternativas Descartadas e Motivo
- ❌ **Distribuição automática round-robin:** Descartada porque os chamados possuem complexidades muito desiguais, correndo o risco de sobrecarregar analistas novatos com casos pesados.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:**  
  *Ex: O volume de chamados diários ultrapassar 150 tickets/dia, tornando a triagem manual um gargalo de tempo do supervisor (>2h/dia).*

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todas as decisões possuem contexto, escolha e alternativas descartadas?
[ ] Toda decisão possui a cláusula obrigatória "Revisitar se..."?
[ ] A data e os responsáveis foram identificados?
-->
