---
name: "escrever-historia"
description: "Escreve uma história de usuário completa com critérios de aceite testáveis no padrão oficial. Use quando o usuário pedir para redigir uma história, criar card, fazer user story, detalhar requisito ou converter pedido em especificação."
---

# Skill: Escrever História de Usuário

> 💡 **MECANISMO DE DISPARO:**  
> Esta skill é ativada automaticamente quando você solicita a redação de histórias de usuário ou requisitos no chat. Ela garante que a estrutura siga rigorosamente o padrão formal de qualidade.

---

## 1. Entradas e Leituras Prévias Obrigatórias

Antes de iniciar a redação, a IA deve consultar:
1. `@contexto/produto.md` e `@contexto/personas-usuario.md` (para garantir que a persona é real e nomeada).
2. `@contexto/glossario.md` (para validar termos e status permitidos).
3. `@contexto/regras-de-negocio.md` (para vincular as regras existentes `[RN-XX]`).
4. `.agents/rules/02-padrao-historias.md` (para seguir a estrutura de seções).

---

## 2. Procedimento de Execução Passo a Passo

1. **Passo 1 — Identificar a Persona e a Dor Real:**
   - Resgate o nome da persona em `contexto/personas-usuario.md`. Nunca use termos genéricos como "o usuário" ou "o operador".
   - Defina a ação concreta e o valor de negócio (o que ela ganha ao concluir a ação).

2. **Passo 2 — Levantar as Regras de Negócio Aplicáveis:**
   - Mapeie quais regras existentes impactam essa funcionalidade.
   - Se for identificada uma nova regra invariante, aponte como sugestão para `contexto/regras-de-negocio.md`.

3. **Passo 3 — Redigir os Critérios de Aceite por Cenários:**
   - **Caminho Feliz:** Descreva o fluxo ideal de ponta a ponta.
   - **Caminhos de Validação e Erro:** Detalhe o que acontece quando campos obrigatórios faltam, valores são inválidos ou serviços externos falham.
   - **Estado Vazio (Empty State):** Defina o que a tela/componente mostra quando não há registros cadastrados.
   - **Permissões:** Indique quem tem e quem não tem permissão para disparar a ação.

4. **Passo 4 — Delimitar o Fora de Escopo:**
   - Declare expressamente pelo menos 2 itens que **NÃO** fazem parte desta entrega imediata.

5. **Passo 5 — Salvar o Arquivo:**
   - Salve a história na pasta `entregas/` no padrão `AAAA-MM-DD-US-XX-nome-da-historia.md`.

---

## 3. Estrutura do Gabarito de Saída

```markdown
# [US-XX] [Ação Concreta da Persona]

## 1. Narrativa
- **Como** [Nome da Persona]
- **Quero** [Ação no sistema]
- **Para que** [Benefício real gerado]

## 2. Regras de Negócio Vinculadas
- `[RN-XX]` [Breve descrição da regra]

## 3. Critérios de Aceite

### Cenário 1: [Caminho Feliz]
- **Dado que** [Pré-condição]
- **Quando** [Ação disparada]
- **Então** [Resultado observado]

### Cenário 2: [Validação de Erro]
- **Dado que** [Dado incorreto]
- **Quando** [Submissão da ação]
- **Então** [Mensagem de erro exibida]

### Cenário 3: [Estado Vazio]
- **Dado que** [Nenhum dado cadastrado]
- **Quando** [Visualização acessada]
- **Então** [Orientação exibida]

## 4. Fora de Escopo
- [Item 1 que não faz parte desta história]

## 5. Suposições e Pendências
- ⚠️ `[SUPOSIÇÃO]` [Se houver]
```

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] A história usou uma persona nomeada?
[ ] Há critérios de caminho feliz, erro e estado vazio?
[ ] O arquivo foi preparado para gravação em entregas/?
-->
