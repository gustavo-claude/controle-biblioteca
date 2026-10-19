---
name: "mapear-fluxo"
description: "Gera diagramas visuais textuais em Mermaid para máquinas de estado, transições de regras de negócio e fluxogramas de jornada de usuário. Use quando precisar desenhar fluxo, mapear estados, criar diagrama, visualizar transições de status ou ilustrar jornada."
---

# Skill: Mapear Fluxos e Estados em Mermaid

> 💡 **MECANISMO DE DISPARO:**  
> Use esta skill para transformar regras complexas ou jornadas de tela em diagramas Mermaid claros, diretamente legíveis no Markdown e no Antigravity.

---

## 1. Tipos de Diagramas Suportados

1. **State Diagram (Máquina de Estados):** Para status de entidades, transições permitidas e gatilhos.
2. **Flowchart (Fluxograma de Decisão):** Para jornadas de usuário com ramificações de sucesso e erro.
3. **Sequence Diagram (Interação Funcional):** Para interações de ponta a ponta entre Persona, Interface e Sistema.

---

## 2. Procedimento Passo a Passo

1. **Passo 1 — Identificar Estados e Atores:**
   - Consulte `@contexto/glossario.md` para garantir que apenas os status oficiais sejam usados.
2. **Passo 2 — Mapear os Gatilhos de Transição:**
   - Identifique quem dispara cada mudança (Usuário, Atendente, Sistema/Tempo) e as regras `[RN-XX]` vinculadas.
3. **Passo 3 — Mapear os Ramos de Erro / Cancelamento:**
   - Nunca desenhe apenas o fluxo ideal; inclua sempre os nós de bloqueio, erro e cancelamento.
4. **Passo 4 — Gerar a Sintaxe Mermaid Válida:**
   - Renderize o bloco com crases triplas e a tag `mermaid`.

---

## 3. Gabarito de Saída Didático (Exemplo Neutro)

### Exemplo 1: Máquina de Estados de Chamados

```mermaid
stateDiagram-v2
    [*] --> Aberto : Usuário abre chamado [RN-01]
    
    Aberto --> EmAtendimento : Atendente assume o ticket
    Aberto --> Cancelado : Solicitante cancela
    
    EmAtendimento --> PendenteUsuario : Falta informação / evidência
    PendenteUsuario --> EmAtendimento : Usuário responde com anexo
    
    EmAtendimento --> Resolvido : Solução técnica aplicada
    
    Resolvido --> Fechado : Usuário confirma ou 48h sem resposta
    Resolvido --> EmAtendimento : Usuário reabre chamado
    
    Cancelado --> [*]
    Fechado --> [*]
```

### Exemplo 2: Fluxograma de Decisão da Jornada de Abertura

```mermaid
flowchart TD
    Inicio([Início: Rodrigo acessa tela]) --> PreencheForm[Preenche Título e Descrição]
    PreencheForm --> TemAnexo{Deseja anexar arquivo?}
    
    TemAnexo -- Sim --> ValidaAnexo{Formato PDF/PNG/JPG e <= 10MB?}
    TemAnexo -- Não --> ClicaEnviar[Clica em Enviar Chamado]
    
    ValidaAnexo -- Não --> AlertaErro[Exibe erro visual em vermelho e bloqueia envio]
    AlertaErro --> PreencheForm
    
    ValidaAnexo -- Sim --> ClicaEnviar
    ClicaEnviar --> GravaChamado[(Sistema gera protocolo e grava com status Aberto)]
    GravaChamado --> TelaSucesso[Exibe tela de confirmação com protocolo]
    TelaSucesso --> Fim([Fim da jornada])
```

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] Os status batem 100% com o glossário oficial?
[ ] Foram incluídos caminhos de erro e cancelamento?
[ ] A sintaxe Mermaid é válida e sem caracteres incompatíveis?
-->
