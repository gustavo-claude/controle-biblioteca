# Workflow: `/nova-funcionalidade`

> 💡 **OBJETIVO DO COMANDO:**  
> Conduzir uma nova demanda desde o entendimento do problema até a história de usuário formalmente revisada e aprovada, com portões obrigatórios de validação humana (🛑) para manter o PO no controle total.

---

## Fluxo de Execução com Portões

```
[Início: Demanda Bruta]
        │
        ▼
[Etapa 1: @analista — Diagnóstico do Problema & Requisitos]
        │
        ▼
   🛑 PORTÃO 1: PO aprova a dor e o escopo de requisitos
        │
        ▼
[Etapa 2: @escritor — Redação da História Formal]
        │
        ▼
   🛑 PORTÃO 2: PO revisa a narrativa e critérios BDD
        │
        ▼
[Etapa 3: @critico — Auditoria das 7 Lentes & Dev Irritado]
        │
        ▼
   🛑 PORTÃO 3: PO decide sobre correções dos apontamentos
        │
        ▼
[Etapa 4: Gravação final em entregas/]
```

---

## Roteiro das Etapas

### Etapa 1: Diagnóstico do Problema e Levantamento de Requisitos (`@analista`)
1. A IA lê `@contexto/produto.md`, `@contexto/personas-usuario.md` e a demanda enviada.
2. Identifica e lista obrigatoriamente as **personas de usuário associadas** a esta funcionalidade, resgatando as dores e workarounds já documentados em `contexto/personas-usuario.md` como âncora do problema a ser resolvido.
3. Mapeia as entradas/saídas esperadas e as regras de negócio aplicáveis (apoiando-se em `entender-problema.md` e `levantar-requisitos.md`).
4. 🛑 **PORTÃO 1 DE APROVAÇÃO:**  
   > *Apresente as personas associadas, o diagnóstico da dor e os requisitos levantados, perguntando: "PO, as personas e o escopo de requisitos cobrem a necessidade antes de redigirmos a história completa?"*  
   > **PARE AQUI E AGUARDE APROVAÇÃO.**

---

### Etapa 2: Redação Formal da História (`@escritor`)
1. Após a aprovação do Portão 1, a IA assume o papel de `@escritor`.
2. Redige a história completa no padrão oficial (`.agents/rules/02-padrao-historias.md`).
3. Cobre caminho feliz, erros de validação, estado vazio e permissões.
4. 🛑 **PORTÃO 2 DE APROVAÇÃO:**  
   > *Apresente o texto da história e pergunte: "PO, a narrativa e os critérios cobrem a necessidade? Deseja ajustar algum comportamento antes da revisão crítica?"*  
   > **PARE AQUI E AGUARDE APROVAÇÃO.**

---

### Etapa 3: Revisão Crítica e Teste do Dev Irritado (`@critico`)
1. Após a aprovação do Portão 2, a IA assume o papel de `@critico`.
2. Aplica as 7 lentes de auditoria (`.agents/rules/03-revisao-critica.md`).
3. Lista apontamentos classificados por severidade (🔴 Bloqueante, 🟡 Atenção, 🟢 Sugestão) e faz 3 perguntas duras de borda.
4. 🛑 **PORTÃO 3 DE DECISÃO:**  
   > *Pergunte ao PO: "Deseja que eu ajuste automaticamente os pontos apontados ou prefere responder às dúvidas levantadas?"*  
   > **PARE AQUI E AGUARDE DECISÃO.**

---

### Etapa 4: Finalização e Arquivamento
1. A IA aplica os ajustes finais decididos no Portão 3.
2. Salva o documento consolidado em `entregas/AAAA-MM-DD-US-XX-nome-da-historia.md`.
3. Informa o link do arquivo gerado e encerra o fluxo.
