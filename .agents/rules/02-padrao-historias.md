---
description: "Estrutura formal e obrigatória para redação de Histórias de Usuário e Critérios de Aceite."
globs: "entregas/**"
---

# Regra 20 — Padrão Oficial de Histórias de Usuário

> 💡 **MODO DE ATIVAÇÃO:** Ativada automaticamente para arquivos dentro de `entregas/` ou quando o agente redige histórias de usuário.

---

## 1. Estrutura Canônica da História

Toda história de usuário deve conter obrigatoriamente as seguintes seções estruturadas:

```markdown
# [US-XX] [Título Conciso e Orientado a Ação]

## 1. Narrativa da História
- **Como** [Nome da Persona formalizada em personas-usuario.md — nunca "o usuário"]
- **Quero** [Ação funcional concreta que a persona executa no sistema]
- **Para que** [Benefício ou resultado de negócio mensurável gerado pela ação]

## 2. Regras de Negócio Aplicadas
- Referência obrigatória às regras de `@contexto/regras-de-negocio.md` (Ex: `[RN-02]`, `[RN-05]`).

## 3. Critérios de Aceite (Testáveis)

### Cenário 1: [Caminho Feliz — Ação principal bem-sucedida]
- **Dado que** [estado inicial ou pré-condição válida]
- **E** [contexto adicional, ex: permissão ou dados carregados]
- **Quando** [a persona executa o gatilho da ação]
- **Então** [o sistema altera o estado e exibe o resultado esperado]
- **E** [evento ou registro gerado]

### Cenário 2: [Caminho de Erro / Validação de Entrada]
- **Dado que** [a persona preenche um dado inválido ou fora da regra]
- **Quando** [tenta submeter o formulário/ação]
- **Então** [o sistema bloqueia o avanço e exibe a mensagem de erro específica: "mensagem esperada"]

### Cenário 3: [Estado Vazio / Primeiro Uso]
- **Dado que** [a persona acessa a visualização sem dados cadastrados]
- **Quando** [a tela é carregada]
- **Então** [o sistema exibe mensagem orientativa e botão para iniciar a primeira ação]

### Cenário 4: [Controle de Acesso / Limites de Permissão]
- **Dado que** [uma persona sem permissão tenta acessar o recurso]
- **Quando** [dispara a requisição/ação]
- **Então** [o sistema oculta a ação ou exibe alerta de permissão negada]

## 4. O que esta História NÃO cobre (Limites de Escopo)
- [Listagem explícita de comportamentos que ficam para histórias futuras ou outros épicos]

## 5. Suposições e Dúvidas Abertas
- ⚠️ `[SUPOSIÇÃO]` [Se houver, listar aqui explicitamente]
- `[CONFIRMAR]` [Itens pendentes de validação com stakeholders]
```

---

## 2. Regras de Ouro para os Critérios

1. **Persona Específica:** Nunca escreva "Como usuário". Identifique a persona cadastrada (ex: "Como Atendente Nível 1").
2. **Critérios Binários:** O critério deve permitir apenas duas conclusões: **PASSOU** ou **FALHOU**.
3. **Sem Jargão Técnico:** Não utilize termos como `JSON`, `PostgreSQL`, `endpoint`, `state management` dentro dos critérios de aceite.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTA REGRA:
[ ] A persona usada está registrada em contexto/personas-usuario.md?
[ ] Foram incluídos os 4 tipos de cenários (Feliz, Erro, Vazio e Permissão)?
[ ] Há lista explícita do que NÃO está no escopo?
-->
