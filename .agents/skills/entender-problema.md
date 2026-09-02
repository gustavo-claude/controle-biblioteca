---
name: "entender-problema"
description: "Investiga a causa-raiz de uma demanda e separa a solução pedida da dor real do usuário. Use quando receber pedidos de clientes ('quero um botão X', 'preciso de um relatório Y'), novas demandas ou solicitações de discovery."
---

# Skill: Entender o Problema do Cliente

> 💡 **MECANISMO DE DISPARO:**  
> Use esta skill no início de qualquer iniciativa para evitar construir soluções prematuras que não resolvem a dor real.

---

## 1. Princípios de Investigação

1. **Pedido ≠ Problema:** O cliente pede uma furadeira; ele precisa de um furo na parede; na verdade, ele quer o quadro pendurado.
2. **Passado Concreto > Futuro Hipotético:**
   - ❌ *"Você usaria uma funcionalidade que faz X?"* (Gera falso positivo; as pessoas sempre dizem sim).
   - ✅ *"Quando foi a última vez que você precisou fazer isso? O que aconteceu exatamente?"*
3. **Mapear a Gambiarra (Workaround):** Se o problema é grave, as pessoas já encontraram um jeito improvisado de contorná-lo (planilhas paralelas, cadernos, grupos de WhatsApp). O workaround é o requisito validado pelo usuário.

---

## 2. Procedimento Passo a Passo

1. **Passo 1 — Desarmar a Solução Pedida:**
   - Identifique qual é a ação ou tela que estão pedindo.
   - Pergunte: *"Qual situação incômoda aconteceu que fez surgir esse pedido agora?"*

2. **Passo 2 — Quantificar o Impacto da Dor:**
   - Qual o prejuízo atual? (Horas gastas por semana, tickets duplicados, clientes insatisfeitos).
   - Com que frequência esse problema ocorre?

3. **Passo 3 — Mapear o Fluxo Atual (As-Is):**
   - Como a pessoa resolve o problema hoje?
   - Quais ferramentas e planilhas paralelas estão em uso?

4. **Passo 4 — Gerar Três Caminhos de Solução:**
   - **Opção A (Sem software):** Ajuste de processo, treinamento ou eliminação da etapa.
   - **Opção B (Solução Mínima / MVP):** A menor intervenção no sistema que elimina 80% da dor.
   - **Opção C (Solução Estrutural):** Automatização completa de ponta a ponta.

---

## 3. Gabarito de Saída (Diagnóstico do Problema)

```markdown
# Diagnóstico de Problema: [Nome do Desafio]

## 1. O Pedido Inicial vs. A Dor Real
- **O que foi pedido:** [Ex: Relatório diário de chamados exportável em Excel]
- **Qual a dor real por trás:** [Ex: O supervisor precisa identificar chamados parados há mais de 48h sem resposta para não estourar o SLA contratual]

## 2. Evidências Concretas do Passado
- **Frequência da dor:** [Ex: Ocorre diariamente às 17h]
- **Como contornam hoje (Workaround):** [Ex: O supervisor copia manualmente 40 linhas do sistema para uma planilha compartilhada]
- **Custo do problema:** [Ex: 1h30 do supervisor por dia + 5% de quebra de SLA no mês]

## 3. Três Caminhos Possíveis
| Opção | Abordagem | Esforço | Impacto |
|---|---|:--:|:--:|
| **A (Processo)** | Criar aviso automático de SLA sem novo relatório | Baixo | Médio |
| **B (Mínima)** | Filtro rápido de 'Chamados Críticos (>48h)' na tela inicial | Baixo | Alto |
| **C (Completa)** | Módulo de relatórios customizáveis com envio por e-mail | Alto | Médio |

## 4. Próximo Passo Recomendado
- [Recomendação do PO para avanço]
```

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] O problema foi separado da solução pedida?
[ ] Foram documentados os workarounds reais de hoje?
[ ] Foram propostas 3 alternativas com diferentes níveis de esforço?
-->
