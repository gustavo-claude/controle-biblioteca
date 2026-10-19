---
description: "Diretrizes de estilo, tom de voz e clareza para documentos de gestão de produto e conversas no workspace."
always_on: true
---

# Regra 10 — Estilo, Tom de Voz e Clareza

> 💡 **MODO DE ATIVAÇÃO:** `always_on: true`  
> Aplica-se a toda comunicação e texto gerado pelo assistente neste workspace.

---

## 1. Princípios de Redação

1. **Português do Brasil (pt-BR):** Linguagem natural, correta e profissional.
2. **Concisão e Densidade:** Vá direto ao ponto. Remova introduções protocolares ("Certamente! Aqui está o que você pediu...") e conclua sem resumos óbvios.
3. **Voz Ativa e Verbos Precisos:** Prefira "O analista aprova o chamado" a "A aprovação do chamado deve ser realizada pelo analista".

---

## 2. Dicionário de Palavras e Expressões Banidas

Evite rigorosamente adjetivos subjetivos que não podem ser testados ou que poluem o texto com "marketês":

| Palavra / Expressão Banida | Por que é proibida | Como substituir |
|---|---|---|
| *"Interface intuitiva e amigável"* | É subjetiva e não testável | Especifique o fluxo exato em passos concretos |
| *"Processamento rápido / em tempo real"* | Não dá métrica aos desenvolvedores | *"Tempo de resposta inferior a 2 segundos"* |
| *"Robusto / Escalável / Estado da arte"* | Jargão vazio sem valor funcional | Explique o volume de dados esperado ou a regra de carga |
| *"Sinergia / Alavancar / Empoderar"* | Prolixidade corporativa | Use verbos objetivos: *integrar, acelerar, permitir* |

---

## 3. Contraste Didático de Redação

- ❌ **Evitar (Prolixo e vago):**  
  > *"O módulo de atendimento deve oferecer uma experiência extremamente fluida e intuitiva para que o atendente consiga de maneira fácil e rápida solucionar os tickets dos clientes com alta performance."*
- ✅ **Bom (Direto e testável):**  
  > *"A tela de atendimento exibe os chamados pendentes ordenados por prioridade [RN-03]. O atendente visualiza o histórico de mensagens e pode alterar o status para 'Em Análise' em até 2 cliques."*

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA REGRA:
[ ] O texto gerado removeu introduções conversacionais vazias?
[ ] Nenhum adjetivo vago ("intuitivo", "rápido") foi utilizado nos critérios?
-->
