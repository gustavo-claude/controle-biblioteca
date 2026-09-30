---
name: "listar-funcionalidades"
description: "Monta a lista de funcionalidades de um produto a partir dos arquivos de contexto/, no formato da tabela de exemplos/funcionalidades/funcionalidades-bom.md, com o título de cada Funcionalidade no padrão ARO (Ação, Resultado e Objeto). Use quando o @analista precisar listar as ações do sistema, o que cada uma resolve e o que está fora de escopo."
---

# Skill: Listar Funcionalidades

> 💡 **MECANISMO DE DISPARO:**  
> Use com o `@analista` quando o pedido for a lista de funcionalidades de um produto: todas as ações que o sistema ou uma persona executa, com problema e benefício. Vale para qualquer workspace que tenha `contexto/`. Não use para redigir história de usuário.

---

## 1. Entradas

Leia, nesta ordem, o que existir em `contexto/`. Ignore arquivo ausente. Não leia `RECEITA-*.md`.

1. `contexto/produto.md` — o que o produto é, os módulos e o que ele não é.
2. `contexto/personas-usuario.md` — quem age, a dor e a gambiarra.
3. `contexto/glossario.md` — termo oficial, termo proibido e catálogo de status. Não use sinônimo.
4. `contexto/regras-de-negocio.md` — o que o sistema ou a persona é obrigado a fazer. Ignore regra `[REVOGADA]`.
5. `contexto/decisoes.md` — o que já foi fechado. Não reabra decisão ativa.
6. `contexto/briefing.md` — só o que não contradiz os arquivos acima. Em conflito, vale o arquivo mais específico (`produto`, `glossario`, `regras-de-negocio`, `decisoes`, `personas-usuario`).

Antes de redigir, leia também:

- `exemplos/funcionalidades/funcionalidades-bom.md` — formato da tabela e da seção de limites.
- `exemplos/funcionalidades/funcionalidades-ruim.md` — os sete erros que a lista não pode repetir.

Não altere `contexto/`. Não escreva história de usuário. Não cite tecnologia, tela, banco, API nem framework.

---

## 2. Procedimento

1. **Extrair ações, não módulos soltos.** Percorra personas, transições de status e regras vigentes. Cada ação observável vira uma candidata: quem dispara, o que acontece, em que estado ou momento. Módulo de `produto.md` só entra se corresponder a uma ação. A mesma ação sobre vários itens do mesmo tipo é uma funcionalidade só.
2. **Separar limite de ação.** Proibição, "não somos" e "o que não é" vão para Limites e Não-Escopo, com o arquivo de origem. Não viram linha da tabela.
3. **Completar a linha só com o que o contexto sustenta.**
   - **Funcionalidade:** título no padrão ARO, seção 3. No vocabulário do glossário, quando o projeto tiver glossário.
   - **Descrição:** comportamento visível. Diga quem age. Se o ator é o sistema, escreva "O sistema".
   - **Problema que Resolve:** dor ou gambiarra da persona, ou falha já escrita no contexto. Sem dor observável, não invente: use `[CONFIRMAR]`.
   - **Benefícios que Traz:** efeito concreto ligado a esse problema. Sem adjetivo vazio (`ágil`, `robusto`, `inteligente`, `moderno`, `completo`).
4. **Marcar o que não está fechado.** Hipótese para avançar leva `⚠️ [SUPOSIÇÃO]` na célula, como em `funcionalidades-bom.md`. Item `[CONFIRMAR]` do contexto não vira funcionalidade decidida: fica na seção Pendências.
5. **Ordenar pelo fluxo.** Se houver catálogo de status, a ordem das linhas segue as transições. Fora isso, siga a ordem dos módulos e das personas.
6. **Conferir os sete erros** de `funcionalidades-ruim.md` e o padrão ARO antes de gravar. Corrija a linha ou retire-a.

---

## 3. Padrão ARO do título

Todo artefato novo deste tipo — lista de funcionalidades gravada em `entregas/` — nomeia a coluna **Funcionalidade** no padrão ARO, nesta ordem:

1. **Ação** — verbo no infinitivo: o que se faz.
2. **Resultado** — substantivo: o efeito obtido.
3. **Objeto** — sobre o que o resultado incide.

Forma do título: `[Ação] [resultado] de/do/da [objeto]`.

O título sai da descrição, do problema e do benefício da mesma linha. Mantém o sentido dessas colunas. Não é nome de módulo, nem só o verbo, nem sigla solta.

Referência já no formato: `exemplos/funcionalidades/funcionalidades-bom.md`. Exemplo: "Registrar sinais vitais e queixa principal do paciente" — Registrar (ação), sinais vitais e queixa principal (resultado), paciente (objeto).

---

## 4. Gabarito de Saída

Grave em `entregas/AAAA-MM-DD-lista-funcionalidades.md`. Se esse arquivo já existir na data, acrescente um sufixo curto ao assunto. Não grave em `contexto/`.

```markdown
# Lista de Funcionalidades do Produto: [Nome em produto.md]

> 📋 **Contexto e Origem:**
> Documento elaborado pelo `@analista` com base nos arquivos de `contexto/` e no formato de `exemplos/funcionalidades/funcionalidades-bom.md`.

## Lista de Funcionalidades com Problemas e Benefícios

| ID | Funcionalidade | Descrição | Problema que Resolve | Benefícios que Traz |
| --- | --- | --- | --- | --- |
| **F001** | [Ação] [resultado] de [objeto] | [Quem age e o que o sistema faz de observável] | [Dor ou gambiarra citada no contexto] | [Efeito concreto dessa ação] |

### Limites e Não-Escopo

- ❌ **[Nome curto]:** [Proibição copiada do contexto]. Origem: `[arquivo]`.

### Pendências

- `[CONFIRMAR]` [Lacuna do contexto que impediu uma linha ou um detalhe]
```

IDs seguem `F001`, `F002`, sem pular número. A seção Pendências só aparece se houver lacuna.

---

## 5. O que não entra na tabela

- Solução técnica ou nome de componente.
- Capacidade que o contexto proíbe.
- Área que o contexto deixou de fora.
- Benefício sem problema, ou problema que ninguém no contexto sofre.
- Ação sem fato em `contexto/` e sem pedido do operador. Hipótese, se for preciso discuti-la, fica marcada `⚠️ [SUPOSIÇÃO]`.
- Não-escopo genérico, do tipo "o sistema fará o que for preciso no futuro".
- Título de Funcionalidade fora do padrão ARO.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] Cada linha é uma ação observável, com ID, descrição, problema e benefício?
[ ] O título de cada Funcionalidade está em ARO: ação, resultado e objeto, nesta ordem?
[ ] Os termos batem com o glossário e nenhuma regra [REVOGADA] foi usada?
[ ] Os limites excluem algo e citam o arquivo de origem?
[ ] Não há tecnologia, adjetivo vazio, escopo inflado nem ação inventada sem ⚠️ [SUPOSIÇÃO]?
[ ] O arquivo foi gravado em entregas/ e contexto/ não foi alterado?
-->
