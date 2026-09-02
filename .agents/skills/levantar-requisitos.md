---
name: "levantar-requisitos"
description: "Prepara roteiros de entrevistas, formula perguntas de discovery e extrai requisitos estruturados a partir de conversas com clientes e stakeholders. Use quando for preparar uma reunião de descoberta ou processar anotações brutas de discovery."
---

# Skill: Levantar Requisitos (O Agente de Reunião)

> 💡 **MECANISMO DE DISPARO:**  
> Use antes de reuniões para gerar o roteiro de perguntas e depois da reunião para transformar anotações soltas em insumos estruturados.

---

## 1. Os Três Momentos do Levantamento

```
┌─────────────────────┐      ┌─────────────────────┐      ┌─────────────────────┐
│  1. ANTES DA REUNIÃO │ ───► │ 2. DURANTE A REUNIÃO│ ───► │  3. APÓS A REUNIÃO  │
│  Roteiro de Perguntas│      │   Escuta & Fatos    │      │ Saneamento de Notas │
└─────────────────────┘      └─────────────────────┘      └─────────────────────┘
```

---

## 2. Procedimento Passo a Passo

### Fase 1: Antes da Reunião (Preparação)
1. Consulte `@contexto/produto.md` e as dores documentadas em `@contexto/personas-usuario.md`.
2. Liste até 5 perguntas essenciais focadas no **passado concreto** (evite perguntas hipotéticas).
3. Identifique termos ou regras existentes que precisam de validação.

### Fase 2: Durante a Reunião (Diretrizes de Condução)
- Foque em entender o fluxo atual (As-Is) e as dores da rotina.
- Pergunte sempre pelos números: *"Quantas vezes por dia?", "Quanto tempo demora?", "Quantas pessoas fazem isso?"*.
- Anote os nomes exatos que os usuários usam para cada conceito.

### Fase 3: Após a Reunião (Processamento e Síntese)
1. Salve o texto bruto ou ata em `fontes/AAAA-MM-DD-reuniao-assunto.md`.
2. Extraia os fatos novos e separe de suposições.
3. Proponha atualizações pontuais para os arquivos da pasta `contexto/`.

---

## 3. Gabarito de Saída (Síntese Pós-Reunião)

```markdown
# Síntese de Levantamento: [Nome do Stakeholder / Setor]

## 1. Dados da Sessão
- **Data e Participantes:** [AAAA-MM-DD] — [Nomes e Cargos]
- **Objetivo da Reunião:** [O que fomos investigar]

## 2. Fatos e Descobertas Principais
- [Fato 1 verificado durante a conversa]
- [Fato 2 com números ou métricas relatadas]

## 3. Workarounds Identificados (Gambiarras Atuais)
- **Como fazem hoje:** [Descrição da planilha, caderno ou troca de mensagens paralela]

## 4. Impactos Propostos no Contexto do Workspace
- **Glossário:** [Novo termo identificado para inclusão em contexto/glossario.md]
- **Regras de Negócio:** [Nova restrição para contexto/regras-de-negocio.md]
- **Decisões:** [Decisão tomada para registro em contexto/decisoes.md]

## 5. Dúvidas Pendentes para a Próxima Rodada
- `[CONFIRMAR]` [Item que ficou em aberto com o cliente]
```

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] As notas brutas foram salvas em fontes/?
[ ] Foram separados fatos concretos de suposições?
[ ] Foram propostas atualizações para os arquivos de contexto?
-->
