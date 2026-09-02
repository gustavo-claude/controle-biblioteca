# Kit de Arquitetura de Product Ownership com IA

> **Guia do Workspace** · Estrutura completa para gestão de produto assistida por Inteligência Artificial no Antigravity.

---

## 1. O que é este Kit?

Este repositório é um **gabarito arquitetural limpo e reutilizável**. Ele contém todas as pastas, arquivos de contexto, regras inegociáveis, personas, procedimentos operacionais (skills) e fluxos de trabalho (workflows) necessários para operar o papel de Product Owner (PO) em parceria com a IA, garantindo precisão, zero alucinação e alinhamento estratégico.

### O fluxo de informação do Workspace

```
                          ┌───────────────────────┐
                          │   fontes/ (Insumos)   │
                          │ Transcrições / Áudios │
                          └───────────┬───────────┘
                                      │
                                      ▼
┌────────────────────────────────────────────────────────────────────────┐
│                        CÉREBRO DO WORKSPACE                            │
│                                                                        │
│   AGENTS.md (Contrato) ────► .agents/ (Personas, Regras, Workflows)   │
│         ▲                                                              │
│         │                                                              │
│   contexto/ (Fatos do Negócio: produto, personas, glossário, regras)   │
│   exemplos/ (Padrão ouro: histórias boas e ruins)                      │
└─────────────────────────────────────┬──────────────────────────────────┘
                                      │
                                      ▼
                          ┌───────────────────────┐
                          │  entregas/ (Saídas)   │
                          │   Histórias / Épicos  │
                          └───────────────────────┘
```

---

## 2. Mapa das 4 Gavetas de Arquivos

Para saber onde colocar ou buscar cada informação no workspace, use esta regra fundamental:

| Tipo | Onde mora | O que contém | Quando a IA lê |
|---|---|---|---|
| **Contrato** | `AGENTS.md` | Regras da casa, limites inegociáveis, mapa do workspace | **Sempre**, no início de toda conversa |
| **Contexto** | `contexto/*.md` | Fatos sobre o produto, usuários, regras de negócio, NFRs e termos | **Sob demanda** ou apontado via `@contexto/arquivo.md` |
| **Inteligência** | `.agents/` | Personas (`agents.md`), Regras (`rules/`), Skills e Workflows | **Automaticamente** conforme a tarefa ou gatilho |
| **Exemplos** | `exemplos/` | Modelos de referência (o que é bom e o que é ruim) | Quando for necessário calibrar o padrão de saída |
| **Receitas** | `RECEITA-*.md` | Manuais e gabaritos de criação para o operador humano | 🚫 **NUNCA lido por IA** (exclusivo para humanos) |

---

## 3. Passo a Passo para Iniciar um Novo Projeto

Quando for iniciar o trabalho em um novo produto ou funcionalidade usando este kit, siga este roteiro de preenchimento:

1. **Passo 1 — O Contrato (`AGENTS.md`)**:
   - Abra o `AGENTS.md` e preencha o nome do produto e a lista de documentos obrigatórios.
2. **Passo 2 — O Mínimo de Contexto (`contexto/`)**:
   - Preencha `contexto/briefing.md` (6 a 15 linhas essenciais).
   - Preencha `contexto/produto.md` (visão, público e principalmente **o que o produto NÃO é**).
   - Preencha `contexto/personas-usuario.md` (quem usa e seus workarounds atuais).
   - Preencha `contexto/glossario.md` (termos oficiais e status permitidos).
   - Preencha `contexto/regras-de-negocio.md` (restrições numeradas `RN-01`, `RN-02`).
3. **Passo 3 — Organizar Insumos (`fontes/`)**:
   - Salve gravações, atas de reunião e documentos legados na pasta `fontes/`.
4. **Passo 4 — Executar o Trabalho**:
   - Use as personas (`@analista`, `@escritor`, `@critico`) e os comandos de fluxo (ex: `/nova-funcionalidade`).
   - Salve os artefatos finais sempre na pasta `entregas/`.

---

## 4. Estrutura Completa de Pastas

```
kit-esqueleto-po/
├── LEIA-ME.md                         <- Este guia de introdução e manual de uso
├── AGENTS.md                          <- O contrato lido em toda conversa
├── .agents/
│   ├── README.md                      <- Mapa e árvore: skill vs regra vs workflow vs persona
│   ├── RECEITA-contrato.md            <- Como adaptar o AGENTS.md (máx. ~80 linhas)
│   ├── RECEITA-criar-persona.md       <- Como acrescentar um @chapéu em agents.md
│   ├── agents.md                      <- As 4 personas de PO (@facilitador, @analista, @escritor, @critico)
│   ├── rules/                         <- Regras inegociáveis e padrões de saída
│   │   ├── RECEITA-rules.md           <- Como criar uma regra nova
│   │   ├── 00-fundacao.md             <- Regras anti-alucinação e separação fato/suposição
│   │   ├── 01-estilo-e-tom.md         <- Tom de voz direto e sem jargões vazios
│   │   ├── 02-padrao-historias.md     <- Estrutura formal de histórias e critérios BDD
│   │   └── 03-revisao-critica.md      <- As 7 lentes de revisão e autocrítica
│   ├── skills/                        <- Procedimentos operacionais autônomos
│   │   ├── RECEITA-skills.md          <- Como criar uma skill nova
│   │   ├── entender-problema.md       <- Investigação de causa-raiz e dor do usuário
│   │   ├── levantar-requisitos.md     <- Roteiro de levantamento e elicitação de requisitos
│   │   ├── escrever-historia.md       <- Passo a passo para redigir histórias completas
│   │   ├── revisar-criticamente.md    <- O teste do desenvolvedor irritado
│   │   └── mapear-fluxo.md            <- Geração de diagramas Mermaid (estados e jornadas)
│   └── workflows/                     <- Comandos de barra (/) com portões de validação 🛑
│       ├── RECEITA-workflow.md        <- Como criar um comando / com portões
│       ├── nova-funcionalidade.md     <- Pipeline: Diagnóstico & Requisitos -> Escrita -> Revisão
│       ├── discovery.md               <- Pipeline de preparação e pós-reunião
│       └── atualizar-contexto.md      <- Rotina semanal de higiene do workspace
├── contexto/                          <- O cérebro permanente do negócio
│   ├── README.md                      <- Regras de governança e limite de tamanho
│   ├── RECEITA-novo-documento.md      <- Como criar um arquivo de fatos nesta pasta
│   ├── briefing.md                    <- Síntese de 6 linhas do produto
│   ├── produto.md                     <- Ficha técnica e limites de escopo ("O que NÃO somos")
│   ├── personas-usuario.md            <- Dores, rotinas e gambiarras dos usuários reais
│   ├── glossario.md                   <- Termos canônicos e vocabulário proibido
│   ├── regras-de-negocio.md           <- Regras invariantes numeradas [RN-XX]
│   └── decisoes.md                    <- Log de decisões (ADRs) e cláusula "revisitar se"
├── exemplos/                          <- O padrão visual de qualidade (Few-shot prompting)
│   ├── README.md                      <- Como calibrar a IA com exemplos
│   ├── RECEITA.md                     <- Como criar um par exemplo bom/ruim
│   ├── historia-boa.md                <- Referência comentada de história exemplar
│   ├── historia-ruim.md               <- Contra-exemplo comentado com erros típicos
│   └── prompts-uteis.md               <- Coleção de comandos rápidos para o dia a dia
├── fontes/                            <- Depósito de insumos brutos e não processados
│   └── README.md
└── entregas/                          <- Saídas formais geradas para o time de desenvolvimento
    └── README.md
```

---

## 5. Como Usar Este Kit no Dia a Dia (Guia Prático do PO)

O workspace foi desenhado para acompanhar o ciclo de especificação de uma funcionalidade, desde o entendimento do problema até a validação da história. Veja como utilizá-lo nos 4 cenários mais comuns da sua rotina:

---

### 🟢 Cenário 1: Chegou uma Demanda Bruta ou Reunião de Alinhamento

**Objetivo:** Não pular direto para telas ou soluções técnicas. Investigar a dor real, clarificar o problema e levantar os requisitos.

1. **Se for uma reunião de discovery ou alinhamento com stakeholders:**
   - Salve as notas ou transcrição em `fontes/AAAA-MM-DD-reuniao.md`.
   - Digite no chat:
     ```markdown
     /discovery
     ```
   - A persona `@facilitador` extrairá os fatos, termos novos e regras de negócio para atualizar o `contexto/`.

2. **Se for um pedido direto ou demanda operacional:**
   - Digite no chat:
     ```markdown
     @analista investigue a dor real e levante os requisitos funcionais para a solicitação abaixo:
     [Descrever a demanda/pedido aqui]
     ```

---

### 🟡 Cenário 2: Escrever e Especificar uma História Completa

**Objetivo:** Redigir uma história de usuário pronta para refinamento técnico, com critérios BDD, diagramas visuais e regras vinculadas.

1. **Usando o comando automatizado com portões (Recomendado):**
   - Digite no chat:
     ```markdown
     /nova-funcionalidade
     ```
   - O fluxo passará pelo `@analista` (diagnóstico da dor e requisitos), fará uma pausa no **Portão 1 🛑** para sua aprovação, passará pelo `@escritor` (história formal), pausará no **Portão 2 🛑**, passará pelo `@critico` (auditoria das 7 lentes) e gravará o arquivo final em `entregas/`.

2. **Gerando diagramas visuais para enriquecer o card:**
   - Digite no chat:
     ```markdown
     @escritor use a skill mapear-fluxo para desenhar a máquina de estados em Mermaid para o ciclo de vida desta funcionalidade.
     ```

---

### 🔴 Cenário 3: Auditar a História Antes do Refinamento Técnico (O Teste do Dev Irritado)

**Objetivo:** Encontrar furos, ambiguidades e regras não tratadas antes que a história chegue aos desenvolvedores.

1. **Auditoria das 7 Lentes:**
   - Digite no chat:
     ```markdown
     @critico revise a história @entregas/2026-08-31-US-01-nome.md sob as 7 lentes de auditoria. Aponte itens bloqueantes e faça as 3 perguntas do desenvolvedor irritado.
     ```

---

### 🧹 Cenário 4: Rotina de Higiene de Contexto (Sexta-Feira, 10 Minutos)

**Objetivo:** Evitar que o contexto fique desatualizado e a IA passe a alucinar com regras antigas.

1. **Executar a varredura:**
   - Digite no chat:
     ```markdown
     /atualizar-contexto
     ```
   - A IA verificará se decisões em `decisoes.md` atingiram a cláusula *"Revisitar se..."*, se novos termos surgiram e se regras foram revogadas.

---

### 💡 4 Regras de Ouro para a Interação no Chat

1. **Sempre use `@` para ancorar contexto:** Ao fazer uma pergunta, aponte os arquivos relevantes (ex: `@contexto/produto.md`, `@contexto/glossario.md`). Isso reduz alucinações a zero.
2. **Troque de persona conforme o momento:** Use `@analista` para pensar/fatiar, `@escritor` para redigir e `@critico` para caçar furos.
3. **Respeite os portões 🛑:** Não deixe a IA pular etapas. Revise os passos intermediários antes de autorizar a redação final.
4. **Alimente o `contexto/`:** Toda vez que você corrigir a IA repetidamente sobre a mesma regra, pare e adicione essa regra em `contexto/regras-de-negocio.md` ou `contexto/glossario.md`.

---

## 6. Como estender este kit (receitas de configuração da IA)

Os arquivos de Product Ownership **permanecem**. Para criar skills, regras, workflows, personas ou documentos de contexto novos — inclusive se o workspace deixar de ser só especificação de software — use as receitas (não apague os artefatos atuais):

| Quero criar... | Abra |
|---|---|
| Qualquer artefato (árvore de decisão) | `.agents/README.md` |
| Uma skill | `.agents/skills/RECEITA-skills.md` |
| Uma regra | `.agents/rules/RECEITA-rules.md` |
| Um workflow `/comando` | `.agents/workflows/RECEITA-workflow.md` |
| Uma persona `@nome` | `.agents/RECEITA-criar-persona.md` |
| Adaptar o contrato `AGENTS.md` | `.agents/RECEITA-contrato.md` |
| Um novo fato em `contexto/` | `contexto/RECEITA-novo-documento.md` |
| Um par exemplo bom/ruim | `exemplos/RECEITA.md` |
