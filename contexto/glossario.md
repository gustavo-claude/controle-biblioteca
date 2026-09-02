# Glossário Oficial e Vocabulário Controlado

> 💡 **PAPEL DESTE ARQUIVO:**  
> Elimina ambiguidades e sinônimos no vocabulário do produto. Se a IA não souber a palavra exata da casa, ela inventará termos plausíveis que confundirão os desenvolvedores e usuários.  
> ⚠️ **REGRA DE OURO:** Se um termo tem dois nomes no dia a dia do time, escolha **um só** aqui e proíba o outro.

---

## 1. Termos Canônicos do Domínio

| Termo Oficial | Definição Precisa no Produto | O que NÃO é (Limites) |
|---|---|---|
| **[Termo 1 — Ex: Chamado]** | [Registro formal de uma solicitação de auxílio aberta por um usuário no sistema] | Não é uma tarefa interna de desenvolvimento nem uma mensagem solta |
| **[Termo 2 — Ex: Fila]** | [Agrupamento de chamados pendentes associados a uma especialidade técnica] | Não é a caixa de entrada pessoal do atendente |
| **[Termo 3 — Ex: SLA]** | [Tempo limite acordado entre abertura e primeira resposta técnica] | Não é o tempo total de resolução definitiva |

---

## 2. Palavras Proibidas e Sinônimos Banidos

> 🚫 *O assistente NUNCA deve utilizar os termos da coluna esquerda.*

| Termo Proibido (❌ Banido) | Termo Correto (✅ Usar Sempre) | Motivo da Proibição |
|---|---|---|
| *Ticket / Protocolo / OS* | **Chamado** | Evitar que o time confunda com ordens de serviço de campo |
| *Operador / Agente* | **Atendente N1** | Padronizar com a persona oficial descrita em personas-usuario.md |
| *Finalizar / Matar* | **Resolver** | Padronizar com a lista fechada de status oficiais |

---

## 3. Catálogo Fechado de Status Oficiais

> 🔒 *Estes são os ÚNICOS status válidos para um chamado no sistema. A IA está expressamente proibida de inventar outros estados.*

| Status | Significado do Estado | Quem pode mover para cá |
|---|---|---|
| **Aberto** | Chamado criado pelo solicitante, aguardando triagem inicial | Sistema (Automático na criação) |
| **Em Atendimento** | Atendente assumiu a responsabilidade e iniciou a análise | Atendente N1 / Analista N2 |
| **Pendente Usuário** | Aguardando envio de evidências ou resposta do solicitante | Atendente N1 / Analista N2 |
| **Resolvido** | Solução técnica aplicada; aguardando confirmação do usuário | Atendente N1 / Analista N2 |
| **Cancelado** | Chamado duplicado ou cancelado a pedido do solicitante | Solicitante / Supervisor |

---

## 4. Matriz de Transições de Estado Permitidas

```
[Aberto] ────► [Em Atendimento] ────► [Pendente Usuário]
   │                 │                        │
   │                 ▼                        │
   │           [Resolvido] ◄──────────────────┘
   ▼                 
[Cancelado]
```

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todos os termos chave do domínio foram definidos?
[ ] Há lista explícita de termos proibidos e seus substitutos?
[ ] Os status estão 100% fechados (sem margem para estados inventados)?
-->
