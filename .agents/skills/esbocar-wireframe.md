---
name: "esbocar-wireframe"
description: "Conduz, de preferência com o @analista, o wireflow de uma funcionalidade por vez: frames de baixa fidelidade ligados por setas, a partir da coluna Passos da lista mais recente em entregas/funcionalidades/. Consulta o operador em rodadas, com opções e texto livre, antes de gravar Markdown e SVG. Use quando pedirem wireframe, wireflow, esboço de tela, mockup ou o comportamento esperado de uma funcionalidade."
---

# Skill: Esboçar Wireflow (Baixa Fidelidade)

> 💡 **MECANISMO DE DISPARO:**
> Use de preferência com o `@analista`. O resultado é um wireflow de **uma** funcionalidade: os frames que expressam a coluna **Passos**. Seta só liga frames cuja reação muda a tela. Passos que exibem conteúdo na mesma janela permanecem no mesmo frame. O artefato serve para mostrar ao cliente o comportamento esperado, com posição dos elementos e reações. Detalhe estético fica de fora.
> O operador participa das escolhas. Não desenhe o wireflow fechado no primeiro turno. No início das rodadas, nomeie os grupos de cada frame antes de propor elementos, para o operador não antecipar um grupo que ainda será discutido.

---

## 1. Entradas e Leituras Prévias Obrigatórias

1. O arquivo de lista de funcionalidades **mais recente** em `entregas/funcionalidades/` — leitura central. Use o ID, o título, a descrição, os Limites e Não-Escopo e, sobretudo, a coluna **Passos** da funcionalidade escolhida.
2. `@exemplos/wireframes/wireframe-bom.svg` e `@exemplos/wireframes/modelo-de-wireframe-simples-para-wire-flow` — padrão oficial aprovado: priorizar a **marcação de fluxo** (transições, setas e ramificações) e a **estrutura esquemática limpa de blocos** (ex.: `QUEIXA`, `ALERGIA`, `OBSERVAÇÃO`, caixas `[ ]` de métricas, botões de ação e gatilhos de fluxo com destaque), **sem preencher campos com textos ou dados simulados, exceto quando solicitado**.
3. `@exemplos/wireframes/wireframe-ruim.svg` — o que evitar: alta fidelidade precoce, cards de cor forte, pílulas decorativas, excesso de cor, poluição com textos simulados densos.
4. `@contexto/produto.md` e `@contexto/personas-usuario.md` — a persona que executa os passos e a dor que o wireflow atende.
5. `@contexto/glossario.md` — rótulos, status e filtros no termo oficial.
6. `@contexto/regras-de-negocio.md` — travas, ordenação e indicadores (`RN-XX`). Ignore regra `[REVOGADA]`.
7. `.agents/rules/00-fundacao.md` — não invente comportamento. Lacuna fica `[CONFIRMAR]`.

Não altere `contexto/`. Não escreva história de usuário. Não cite tecnologia, banco, API nem framework.

---

## 2. Procedimento

### Passo 0 — Confirmar a funcionalidade e parar

Leia só a lista mais recente o suficiente para obter ID e título de cada linha.

Apresente a lista enxuta (ID e título). Pergunte qual funcionalidade trabalhar. O retorno aceito é o número (`F002` ou `2`) ou o nome correspondente na lista.

**Pare.** Não leia o restante, não proponha elementos, não desenhe ASCII e não grave arquivo neste turno.

Se a resposta não identificar uma linha, pergunte de novo e pare. Se vier mais de uma funcionalidade, peça qual delas vem primeiro e pare. Uma funcionalidade por ciclo.

### Passo 1 — Mapa de frames e parar

Com a linha confirmada, copie os passos na ordem da coluna **Passos**. Confira Limites e Não-Escopo. Resgate a persona que executa os passos.

Separe **frame** de **grupo** antes de consultar elementos.

- **Frame:** uma janela. Abra outro frame somente quando a reação troca o que está na tela: outra janela, caixa que substitui a área, ou `Se / Senão` com arranjos diferentes.
- **Mesmo frame:** o passo só mostra ou lê conteúdo no arranjo já aberto. Um `Se / Senão` que muda o conteúdo de um elemento (nome social ou nome, alerta que aparece quando existe) permanece na mesma célula.
- **Grupo:** conjunto de elementos consultado dentro de um frame já definido. Grupo não é frame. O mínimo de 2 grupos serve para posicionar elementos. Não cria segunda janela.

A seta existe só entre frames. O texto da seta é a reação do passo. Se o passo não disser a reação, marque `[CONFIRMAR]`. Não invente a reação.

Anuncie o mapa e pare. Não proponha elementos, não desenhe ASCII e não grave arquivo neste turno.

```text
Mapa de frames — [F00X]

Frame A — [rótulo da janela] — passos [n a m]
Frame B — [rótulo da janela] — passo [n]

Seta A → B: [reação]
```

Com um frame só, escreva `Sem seta: os passos exibem conteúdo nesta janela.`

Peça confirmação ou o ajuste do mapa. Se a resposta corrigir o mapa, aplique o texto do operador, reapresente o mapa e pare de novo. As rodadas de elementos só começam no turno em que o mapa estiver confirmado.

### Passo 2 — Rodadas com o operador

Só depois do mapa confirmado. Cada grupo é uma rodada, dentro de um frame do mapa. Uma rodada por turno. São de 2 a 10 rodadas nesta funcionalidade. Se os passos pedirem mais de 10 grupos, una grupos até caber em 10. Se couber em um só, separe elementos até chegar a 2, sem abrir frame novo.

Cabeçalho, filtros, área principal e ações são exemplos de grupo. Não são obrigatórios em toda funcionalidade. O grupo existe porque o passo precisa daqueles elementos.

No primeiro turno deste passo, antes das opções do grupo 1, liste o nome de cada grupo de cada frame, na ordem das rodadas. O nome é curto e diz o que o grupo reúne. Sem elementos e sem posição. A lista mostra como cada frame foi cortado. O operador a lê antes de comentar a proposta da vez, e assim não pede agora o que já está reservado a um grupo posterior.

```text
Grupos deste wireflow — [N] rodadas

Frame A — [rótulo da janela]
1. [nome do grupo]
2. [nome do grupo]

Frame B — [rótulo da janela]
3. [nome do grupo]

A rodada de agora trata só do grupo 1. Os outros nomes entram nas rodadas seguintes. Não antecipe esses grupos nesta resposta.
```

A lista sai no mesmo turno da primeira rodada. Não é uma parada nova e não abre grupo futuro. Com um frame só, liste os grupos desse frame. Em cada rodada seguinte, antes das opções, repita os nomes ainda não discutidos daquele frame.

Em cada rodada, proponha o conjunto de elementos **e** a posição deles no frame. As opções cobrem só o grupo da vez. Ofereça mais de uma opção. A última entrada da lista é sempre texto livre.

```text
Grupo [k] de [N] — frame [A] — passos [n a m]
Grupos seguintes deste frame, ainda não discutidos: [nomes]. Não inclua esses elementos nesta escolha.

1. [Elementos e posição na tela, só deste grupo]
2. [Outra composição e outra posição, ainda cobrindo os mesmos passos deste grupo]
3. Outra: descreva em texto os elementos e a posição deste grupo.
```

A lista pode ter mais de duas propostas. Não pode ter só uma. Não omita a entrada "Outra".

**Pare e aguarde.** Não avance ao grupo seguinte no mesmo turno. Não desenhe o wireflow consolidado nem grave arquivo enquanto houver grupo sem escolha. Se a resposta falar de um grupo nomeado que ainda não é o da vez, não abra essa rodada. Avise que aquele nome será discutido na rodada dele. Nesta rodada, vale só o que cabe ao grupo atual.

A opção escolhida vale para aquele grupo. Se a resposta for "Outra", use o texto do operador como está. Não troque por uma proposta anterior. Se a resposta mudar a quantidade de grupos restantes, ajuste N sem passar de 10 nem ficar abaixo de 2. Ao ajustar N, renomeie os grupos restantes e mostre a lista atualizada no turno seguinte, antes das opções.

### Passo 3 — Layout preliminar em ASCII

Só depois da última rodada, desenhe o wireflow em ASCII.

- Um bloco por frame confirmado no mapa.
- A primeira linha de cada bloco, à esquerda, é o título: `Frame A - [nome do frame]`. O mesmo formato vale para os frames seguintes.
- Seta somente entre frames, com a reação do sistema (`-->` e o texto da reação). O traço não corta texto nem o interior de outro frame.
- Frame único: um bloco. Os passos ficam indicados dentro do bloco, sem seta entre eles.
- Baixa fidelidade: borda, caixa, rótulo e ação. Proporção e agrupamento. Sem tratamento visual.
- O texto de cada botão começa com letra maiúscula.

### Passo 4 — Inventário funcional de componentes

Tabela com cada elemento escolhido: bloco, rótulo, tipo, funcionalidade `[F00X]`, posição escolhida e comportamento (gatilho, bloqueio, trava, regra `[RN-XX]`).

### Passo 5 — Estados e notas para o operador

- Estado vazio, carregamento e bloqueio, só quando o passo, a regra ou o operador os tiver definido. O que faltar fica `[CONFIRMAR]`.
- Notas do que o operador ainda pode ajustar, sem reabrir grupo já escolhido como se estivesse em aberto.

### Passo 6 — Gravar Markdown e SVG

Grave somente ao fim das rodadas e do ASCII.

- `entregas/wireframes/AAAA-MM-DD-wireflow-F00X-assunto.md`
- `entregas/wireframes/AAAA-MM-DD-wireflow-F00X-assunto.svg`

Se o arquivo dessa data e desse `F00X` já existir, acrescente um sufixo curto ao assunto.

O SVG é o mesmo wireflow: um frame por bloco do ASCII. Seta só quando o mapa tiver mais de um frame, no padrão de `wireframe-bom.svg`.

- Traço `#111111`, cantos `rx`, espaço entre frames.
- Cor só como realce funcional (ex.: azul suave `#dbeafe` no frame do passo corrente). A seta usa o mesmo traço, sem enfeite.
- Proibido o que `wireframe-ruim.svg` mostra: card inteiro em cor de alerta, botão em pílula colorida, gradiente, sombra pesada, alta fidelidade.

Leitura do SVG, obrigatória:

- Título de cada frame no canto superior esquerdo, no formato `Frame A - [nome do frame]`. Vale para todos os frames. O título não fica no centro nem no meio do frame.
- O texto de cada botão começa com letra maiúscula (`Descartar`, `Salvar rascunho`, `Confirmar`).
- Conteúdo interno do frame — botão e demais rótulos do sistema: no mínimo 17px.
- Orientações de fluxo e as outras descrições — título do frame, texto da seta, passo e reação: 22px. Sempre maior que o conteúdo interno.
- A seta não passa por cima de texto, de outro rótulo nem do interior de um frame. Corre na faixa entre os frames. O rótulo fica ao lado do traço, com folga, sem encostar em outro texto. A seta só toca a borda do frame de destino. A ponta aponta na direção do último trecho.
- Grave o arquivo em UTF-8. No texto, use hífen (`-`). Não use travessão.

---

## 3. Gabarito de Saída

```markdown
# Wireflow: [F00X] [Título ARO da funcionalidade]

- **Persona que executa os passos:** [Nome em contexto/personas-usuario.md]
- **Funcionalidade:** `[F00X]` — [título na lista mais recente de entregas/funcionalidades/]
- **Passos de origem:** [coluna Passos, na ordem]
- **Regras vinculadas:** `[RN-XX]`
- **Rodadas com o operador:** [k de N, entre 2 e 10]
- **Arquivo SVG:** `entregas/wireframes/AAAA-MM-DD-wireflow-F00X-assunto.svg`

---

## 1. Wireflow em ASCII

Passo 1 — [ação da persona]
+------------------------------------------+
| Frame A - [nome do frame]                |
| [elementos na posição escolhida]         |
+------------------------------------------+
        |
        | reação: [o que o sistema faz neste passo]
        v
Passo 2 — [ação da persona]
+------------------------------------------+
| Frame B - [nome do frame]                |
| [elementos na posição escolhida]         |
+------------------------------------------+

Frame único: um bloco só. Liste os passos dentro dele. Não desenhe seta entre esses passos.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| [Frame do passo n] | [rótulo oficial] | [tipo] | [posição escolhida] | `[F00X]` | [reação, trava ou `[RN-XX]`] |

---

## 3. Estados da Interface

- **Estado vazio:** [só se estiver definido; senão `[CONFIRMAR]`]
- **Carregamento / atualização:** [idem]
- **Bloqueios e restrições:** [idem]

---

## 4. Notas para o Operador

> ✏️ **Ajustes ainda abertos:**
> - [ ] [Ponto que a rodada não fechou]
> - [ ] `[CONFIRMAR]` [Lacuna de regra ou de reação]
```

---

## 4. O que não entra no wireflow

- Segunda funcionalidade no mesmo ciclo.
- Elemento ou reação que não esteja no passo, na regra, no glossário ou na escolha do operador.
- Ação listada em Limites e Não-Escopo.
- Detalhe estético: cor de marca, ícone decorativo, tipografia final, espaçamento de produto.
- Opção única na rodada, ou rodada sem a entrada "Outra".
- Rodada aberta sem o operador ter visto os nomes dos grupos daquele frame.
- Proposta da rodada que já inclui elementos de um grupo nomeado para rodada posterior.
- Arquivo gravado antes da confirmação da funcionalidade, antes da confirmação do mapa de frames ou antes do fim das rodadas.
- Frame novo para passo que só exibe ou lê conteúdo no arranjo já aberto.
- Seta entre passos do mesmo frame.
- Seta que cruza texto, outro rótulo ou o interior de um frame.
- Botão cujo texto começa com letra minúscula.
- Título de frame fora do canto superior esquerdo, ou em formato diferente de `Frame A - [nome do frame]`.
- Conteúdo interno do frame abaixo de 17px.
- Orientação de fluxo abaixo de 22px, ou menor que o conteúdo interno.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] A funcionalidade foi confirmada pelo operador (número ou nome) antes de qualquer frame?
[ ] O mapa de frames foi anunciado e confirmado antes das rodadas de elementos?
[ ] Passo que só exibe ou lê conteúdo no arranjo aberto permaneceu no mesmo frame?
[ ] O ciclo cobre uma única linha da lista mais recente em entregas/funcionalidades/?
[ ] Seta só aparece entre frames, com a reação do passo?
[ ] No primeiro turno do passo 2, antes das opções do grupo 1, os grupos de cada frame foram nomeados na ordem das rodadas?
[ ] Cada rodada deixou explícitos os grupos seguintes ainda não discutidos, e a escolha ficou só no grupo da vez?
[ ] Houve de 2 a 10 rodadas, cada uma com mais de uma proposta e a entrada "Outra"?
[ ] Cada rodada esperou a escolha antes da seguinte?
[ ] O ASCII preliminar mostra um bloco por frame confirmado? Seta só entre frames?
[ ] O inventário (passo 4), os estados e as notas (passo 5) e os arquivos Markdown e SVG (passo 6) foram produzidos só depois das rodadas?
[ ] Limites e Não-Escopo foram respeitados? Rótulos batem com o glossário? Regras [RN-XX] vigentes estão citadas?
[ ] O SVG segue wireframe-bom.svg e evita wireframe-ruim.svg?
[ ] Cada frame traz o título `Frame A - [nome do frame]` no canto superior esquerdo?
[ ] O texto de cada botão começa com letra maiúscula?
[ ] O conteúdo interno do frame tem no mínimo 17px, e as orientações de fluxo têm 22px?
[ ] Nenhuma seta cruza texto, outro rótulo ou o interior de um frame? O rótulo da seta fica ao lado do traço, e a ponta segue o último trecho?
[ ] O artefato mostra comportamento (posição e reação), sem detalhe estético?
-->
