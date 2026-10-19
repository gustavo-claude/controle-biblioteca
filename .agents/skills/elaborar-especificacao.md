---
name: "elaborar-especificacao"
description: "Redige uma especificação funcional HU-XX para a funcionalidade confirmada na lista mais recente em entregas/funcionalidades, com cenários Gherkin, regras e limites de escopo. Use quando pedirem elaborar, redigir ou reescrever especificação funcional, história de usuário, critérios de aceitação, BDD ou Gherkin."
---

# Skill: Elaborar Especificação Funcional

> 💡 **MECANISMO DE DISPARO:**  
> Use com o `@escritor` para produzir ou reescrever **uma** especificação funcional. O resultado é um markdown que pessoas e outros agentes leiam sem escolher entre versões contraditórias do mesmo comportamento.

---

## 1. Objetivo e escopo

Produzir uma especificação verificável: intenção, cenários observáveis, invariantes, anexo visual, fora de escopo e pendências reais.

A frase da história segue `.agents/rules/02-padrao-historias.md`: **Como / Quero / Para que**. As seções úteis do padrão de especificação permanecem: descrição, narrativa, critérios, regras, outras informações, fora de escopo, suposições e lista de atualizações.

Esta skill **não**:

- investiga a dor (`entender-problema`) nem prepara entrevista (`levantar-requisitos`);
- monta a lista de funcionalidades (`listar-funcionalidades`);
- desenha wireflow (`esbocar-wireframe`) nem diagrama Mermaid (`mapear-fluxo`) — só incorpora o artefato se ele já existir e for legível;
- substitui a auditoria das 7 lentes (`revisar-criticamente` e `.agents/rules/03-revisao-critica.md`);
- altera `contexto/`, `AGENTS.md`, personas, regras, workflows ou exemplos;
- lê arquivo `RECEITA-*.md`;
- cria portão de aprovação além dos que já existem.

Dentro de `/nova-funcionalidade`, rode só na Etapa 2, depois do Portão 1, e pare no Portão 2 do workflow. Não abra a Etapa 3.

---

## 2. Leituras

O Passo 0 lê só a lista de funcionalidades. As demais leituras acontecem depois da confirmação, antes de redigir. Se o caminho não existir, registre a ausência e siga. Não preencha o buraco com memória ou com o conteúdo “típico” de um arquivo desse nome.

1. O arquivo mais recente em `entregas/funcionalidades/` — fonte principal da funcionalidade. A data é o prefixo `AAAA-MM-DD` do nome. Em empate de data, use o arquivo modificado por último. Não misture listas antigas.
2. `exemplos/funcionalidades/funcionalidades-bom.md` — formato da lista, não a lista do produto. Cada funcionalidade tem um título `FXX` e uma tabela com Funcionalidade, Descrição, Problema que Resolve, Benefícios que Traz e Passos. O arquivo também traz Limites e Não-Escopo, Pendências e confirmações.
3. `exemplos/especificacoes/especifcacao-boa.md` — forma da especificação pronta: identificador `HU-XX`, seções e cenários.
4. `.agents/rules/02-padrao-historias.md` — frase **Como / Quero / Para que** e gramática do cenário. O título de exemplo dessa regra ainda mostra `US-XX`. Nesta skill o identificador do documento é `HU-XX`. Não grave `US-XX`.
5. `.agents/rules/00-fundacao.md` — fato, suposição e proibição de inventar.
6. `.agents/rules/01-estilo-e-tom.md` — voz e termos subjetivos proibidos.
7. `contexto/produto.md`, `contexto/personas-usuario.md`, `contexto/glossario.md`, `contexto/regras-de-negocio.md`, `contexto/decisoes.md`.
8. `entregas/especificacoes/` — especificações já gravadas, para não repetir `HU-XX`.
9. O insumo do pedido: texto no chat, arquivo em `fontes/` ou a especificação que será reescrita.

Não dependa de um documento de análise externo. Os controles já estão nas seções 5 e 8.

---

## 3. Quando parar, marcar ou seguir

**Pare e pergunte** (no máximo 5 perguntas). Não grave arquivo quando:

- não há persona nomeada no pedido nem em `contexto/personas-usuario.md`;
- não há ação principal com resultado observável;
- duas fontes de `contexto/` contradizem o comportamento principal;
- o pedido pede um resultado que ninguém afirmou.

**Marque e continue o resto** quando a lacuna for localizada:

- texto exato de mensagem ausente → `[CONFIRMAR: texto da mensagem de …]`;
- arquivo de wireflow ou imagem ausente → `[REFERÊNCIA INDISPONÍVEL: caminho relativo]` e não descreva o que ele “deve” conter;
- outra história citada e o arquivo não está no pacote → `[FORA DESTE PACOTE: ID]`, sem resumir o conteúdo dela;
- o próprio insumo se contradiz → `[CONFLITO]`, citando as duas partes e o impacto. Não amplie o cenário para caber na regra nem encolha a regra para caber no cenário.

**Siga sem marcador** só com fato de `contexto/`, decisão ativa, frase explícita do usuário nesta conversa, ou trecho do insumo que não esteja em conflito.

Tags obrigatórias, como na regra 00:

- `⚠️ [SUPOSIÇÃO]` — hipótese para avançar, sempre repetida na seção 7;
- `[CONFIRMAR]` — dado em aberto que altera comportamento, aceite, escopo ou implementação;
- `[CONFLITO]` — duas partes do material não dizem a mesma coisa.

É proibido completar em silêncio mensagem, estado, exceção, prazo, número ou resultado “para a especificação ficar fechada”.

---

## 4. Procedimento

### Passo 0 — Confirmar a funcionalidade e parar

1. Leia o arquivo mais recente em `entregas/funcionalidades/`, no critério da seção 2.
2. Se a pasta não tiver lista, pare e registre a ausência. Não trate `exemplos/funcionalidades/funcionalidades-bom.md` como a lista do produto.
3. Apresente o ID e o título de cada funcionalidade. O título é a linha **Funcionalidade** da tabela.
4. Pergunte para qual funcionalidade gerar a especificação. A resposta aceita é o ID (`F01`) ou o título correspondente.
5. **Pare.** Não leia o restante da lista, não redija cenários e não grave arquivo neste turno.

Se o pedido já nomear uma funcionalidade, mostre a linha encontrada e peça confirmação. Sem confirmação explícita, não grave.

### Passo 1 — Preparar o contexto

Depois da confirmação, leia a linha inteira dessa funcionalidade: Descrição, Problema que Resolve, Benefícios que Traz, Passos, e os Limites, Pendências e confirmações do mesmo arquivo.

O documento novo recebe `HU-` e o mesmo número da funcionalidade, com hífen e exatamente dois algarismos. Critério, regra e informação colam o número em `HU` e só usam hífen antes da letra:

- `F01` → `HU-01` no título e no nome do arquivo
- cenário `HU01-C01`
- regra local `HU01-R01`
- informação `HU01-I01`

Não use três algarismos (`F001`, `HU-001`). Não use `US-XX`. Não use `HU-01-C01`. Não escolha o próximo número livre: o número vem da funcionalidade confirmada. Se `entregas/especificacoes/` já tiver esse `HU-XX`, não sobrescreva; pare e pergunte se a saída é uma versão nova com sufixo no nome do arquivo.

A descrição, os passos e os limites dessa linha delimitam o escopo. Outra funcionalidade da mesma lista só entra na seção 6, com o `HU-` de mesmo número. Pendência `[CONFIRMAR]` da lista entra na seção 7.

Separe o que cada fonte autoriza. Ignore regra marcada `[REVOGADA]`. Use o termo de `contexto/glossario.md`. Se o insumo usa outro termo, não troque pelo vocabulário de outro produto: registre `[CONFIRMAR]`.

### Passo 2 — Verificar os insumos

Liste, em notas suas, fatos, ausências e contradições. Aplique a seção 3 antes de escrever cenários.

### Passo 3 — Organizar

Separe em seis listas, sem redigir ainda:

1. intenção (persona, ação, benefício);
2. invariantes — **um por item**;
3. comportamentos — **um evento principal por item**;
4. exceções e estados vazios que o insumo realmente afirma;
5. material visual e o caráter de cada um (ilustrativo ou normativo);
6. limites de escopo.

Confirmação, cancelamento, falha e nova tentativa são itens próprios na lista 3 quando o usuário age de novo.

### Passo 4 — Elaborar

Grave em `entregas/especificacoes/AAAA-MM-DD-HU-01-assunto.md`, com o `HU-XX` confirmado e o assunto em kebab-case. Se o nome já existir, acrescente um sufixo. Não sobrescreva o arquivo de origem numa reescrita: a origem permanece e a saída é outro arquivo.

Use a estrutura da seção 6 e as regras da seção 5.

### Passo 5 — Validar a consistência

Confira, um por um:

- cada `HUXX-Rnn` tem uma só frase de invariante e uma lista “Demonstrada por” cujos cenários mostram esse invariante no `Então`;
- cada citação de cenário para regra aponta para regra que existe neste arquivo ou em `contexto/regras-de-negocio.md`;
- nenhum `HUXX-Inn` ilustrativo acrescenta campo, botão, ordem ou texto que o cenário não tenha;
- a seção 6 não é desmentida por cenário nem por desenho;
- todo link é relativo ao repositório e o alvo existe, ou está marcado `[REFERÊNCIA INDISPONÍVEL]`;
- a seção 8 não afirma um estado que o corpo não sustenta.

### Passo 6 — Revisão crítica de forma

Execute o checklist da seção 8. Achado que impede programar sem inventar regra é bloqueante: o status não pode ser “Pronta para validação”.

As 7 lentes e o relatório do `@critico` ficam na skill `revisar-criticamente`. Não as repita aqui. No workflow, essa auditoria só começa depois do Portão 2.

### Passo 7 — Entregar

Responda com:

1. caminho do arquivo;
2. status: `Pronta para validação` ou `Requer esclarecimento`;
3. checklist da seção 8, com cada item em conforme ou não conforme;
4. pendências `[CONFIRMAR]`, `[CONFLITO]` e `⚠️ [SUPOSIÇÃO]`, cada uma com o impacto;
5. limitação de leitura (arquivo ausente, exemplo do kit divergente, referência fora do pacote).

`Pronta para validação` exige checklist sem bloqueante, zero `[CONFLITO]` e zero `[CONFIRMAR]` que mude comportamento ou aceite. Suposição marcada impede esse status.

---

## 5. Regras de elaboração

### Hierarquia e leitura

- Um heading 1: o título. Seções em heading 2. Cenários em heading 3. Não use heading 4 ou 5. Não envolva o heading em negrito.
- A lista de atualizações é a **seção 8**, no fim. Ela registra quem alterou a redação. Não interrompe a descrição nem vale como requisito.
- Não repita o mesmo comportamento na descrição, no cenário e na regra. A descrição diz o objetivo em um parágrafo. O cenário mostra o exemplo. A regra enuncia o invariante em uma frase.

### História e cenários

- Persona nomeada, nunca “o usuário”. A mesma persona em todos os passos, salvo cenário de outra persona (permissão).
- Passos em lista, palavra-chave em negrito, como na regra 02. Não gere `.feature` salvo pedido explícito.
- **Dado que** e o **E** que o segue: só contexto. **Quando**: uma ação voluntária de uma persona, ou um único carregamento quando o comportamento é abrir a tela. **Então** e o **E** que o segue: só resposta observável do sistema a esse Quando.
- Proibido um segundo gesto dentro do Então. “E ao clicar em …” abre outro cenário.
- Pré-condição repetida em dois ou mais cenários vai para o bloco **Contexto compartilhado**, uma vez.
- Variação do mesmo comportamento (dados diferentes, mesmo evento) vira **Esquema do cenário** com tabela **Exemplos**. Não empilhe essa variação em vários **E**.
- Rótulo único, no título do cenário: `caminho-feliz`, `alternativa`, `erro`, `estado-vazio`, `permissao`. Sem barra e sem combinação.
- A regra 02 pede as famílias feliz, erro, vazio e permissão. Se o insumo não traz uma delas, não invente o cenário: diga na seção 7 que a família está sem fato.
- Mensagem observável vai entre aspas. Sem o texto, use `[CONFIRMAR: texto da mensagem de …]`.
- Critério binário: passou ou falhou. Sem adjetivo subjetivo e sem solução técnica (tabela, endpoint, framework, cor hexadecimal, “banco de dados”).
- Nome de botão e texto de mensagem ficam no cenário, porque são o que se observa. Não viram regra de negócio.

### Regras e rastreabilidade

- Uma regra local, um invariante, uma frase: `HU01-R01`.
- Invariante já cadastrado: cite só `[RN-XX]` de `contexto/regras-de-negocio.md`. Não reescreva o catálogo e não crie número novo lá.
- A regra não copia o cenário. A rastreabilidade é uma linha: `Demonstrada por: HU01-C02`. Inclua o cenário nessa linha somente se o `Então` dele torna o invariante visível. Caso contrário, `[CONFLITO]`.
- O cenário pode citar o ID da regra uma vez. A regra não cita o cenário no título e de novo no fim do parágrafo.
- O documento se chama `HU-XX`. Critério, regra e informação usam `HUXX-Cnn`, `HUXX-Rnn` e `HUXX-Inn`: `HU01-C01`, `HU01-R01`, `HU12-I01`. Proibido `HU-01-C01`, `US-XX` e reiniciar em `CA001`, `RN01` ou `IN001` sem esse prefixo.
- Toda menção a outro ID é conferida. Citação quebrada ou para o elemento errado é bloqueante.

### Visual e escopo

- Cada item da seção 5 declara `Caráter: Ilustrativo` ou `Caráter: Normativo`.
- ASCII, wireflow e exemplo de tela nascem **Ilustrativo**, salvo frase explícita do usuário dizendo que aquele desenho é aceite.
- Desenho ilustrativo que contradiz o cenário, traz marca ausente da regra ou mostra tela da seção 6: corrija o desenho para parar onde o aceite para, ou retire o desenho e registre `[CONFLITO]`. Não deixe os dois vigentes.
- Link somente relativo ao repositório (`entregas/wireframes/...`). `file:///` e caminho de outra máquina são inválidos: troque por `[REFERÊNCIA INDISPONÍVEL]`.
- Prevalência, escrita de novo em cada documento: cenário vigente, depois regra, depois anexo ilustrativo. A seção 8 não altera o corpo.

### Seção 7

Quatro naturezas, separadas: fato (já está nas seções 2 a 6), decisão aprovada (cite `contexto/decisoes.md`), suposição, desconhecido.

A seção 7 só fica sem itens se o checklist passou sem `[CONFIRMAR]`, `[CONFLITO]` e suposição. Aí escreva: `Nenhuma pendência. Checklist da seção 7 conferido.` Não use a frase pronta “Nenhuma pendência ou dúvida impeditiva em aberto para esta especificação.”

---

## 6. Estrutura do documento

```markdown
# HU-01 Título orientado à ação

> Prevalece, nesta ordem: cenário, regra, anexo ilustrativo. A lista de atualizações não altera o corpo.

## 1. Descrição

Um parágrafo com o objetivo. Sem repetir os cenários.

## 2. Narrativa da História

- **Como** [persona de contexto/personas-usuario.md, ou a do insumo com CONFIRMAR se não estiver cadastrada]
- **Quero** [ação observável]
- **Para que** [benefício concreto]

## 3. Critérios de Aceite

### Contexto compartilhado

- **Dado que** [só se dois ou mais cenários repetirem a mesma pré-condição]

### HU01-C01: [caminho-feliz] — [um comportamento]

- **Dado que** [contexto que não está no bloco compartilhado]
- **Quando** [a persona] [uma ação]
- **Então** [resultado observável] `[RN-XX]` ou `HU01-R01`
- **E** [outra resposta do mesmo Quando]

### HU01-C02: [alternativa] — [o segundo gesto, se houver]

- **Dado que** [estado deixado pelo cenário anterior]
- **Quando** [a persona] [a segunda ação]
- **Então** [resultado observável]

### HU01-C03: [caminho-feliz] — [variação de dados do mesmo evento]

- **Esquema do cenário**
- **Dado que** o caso é "<caso>"
- **Quando** [a persona] [a mesma ação]
- **Então** o resultado observável é "<resultado>"

Exemplos:

| caso | resultado |
| --- | --- |
| [valor afirmado] | [valor afirmado] |

## 4. Regras de Negócio

### HU01-R01 — [nome do invariante]

[Uma frase, sem widget e sem roteiro de tela.]

Demonstrada por: HU01-C01

### [RN-XX]

Invariante já registrado em `contexto/regras-de-negocio.md`. Não repetir a descrição.

Demonstrada por: HU01-C02

## 5. Outras Informações Relevantes

### HU01-I01 — [nome do anexo]

- **Caráter:** Ilustrativo
- **Alvo:** [caminho relativo] ou `[REFERÊNCIA INDISPONÍVEL: caminho]`

O desenho, se permanecer, só repete o que os cenários já aceitam.

## 6. O que esta História NÃO cobre

- [comportamento] — `HU-02`, alinhado a `F02`, ou `[FORA DESTE PACOTE: HU-02]`

## 7. Suposições e Dúvidas Abertas

- `[CONFLITO]` [parte A] contra [parte B]. Impacto: [o que o desenvolvedor teria de inventar].
- `[CONFIRMAR]` [dado ausente]. Impacto: [aceite, escopo ou implementação].
- ⚠️ `[SUPOSIÇÃO]` [hipótese]. Impacto: [o que muda se cair].

## 8. Lista de atualizações

| Autor | Data | Descrição |
| --- | --- | --- |
| [quem] | [AAAA-MM-DD] | [o que mudou na redação, sem criar requisito novo] |
```

---

## 7. Checklist final

Marque cada item ao concluir o passo 6. Bloqueante reprova o status `Pronta para validação`.

1. Cada cenário tem um único Quando, e nenhum **E** contém clique, confirmação ou cancelamento.
2. Cada regra local é um invariante. Nenhuma regra repete o roteiro do cenário nem junta falha e sucesso no mesmo bloco.
3. O documento é `HU-XX`, com o mesmo número da funcionalidade confirmada (`F01` → `HU-01`). Critério, regra e informação usam `HU01-C01`, `HU01-R01` e `HU01-I01`, sem hífen entre `HU` e o número. Não há `US-XX` nem `HU-01-C01`. Cada ID citado existe no arquivo.
4. Cada “Demonstrada por” foi conferida contra o Então do cenário. Citação quebrada ou cobertura parcial está em `[CONFLITO]`, não foi “corrigida” sozinha.
5. Cenário, regra e anexo ilustrativo não divergem. O anexo não especifica o que a seção 6 exclui.
6. Regra local não contém cor, componente, campo de tela nem nome de botão. Isso está no cenário, ou não está no documento.
7. Mensagem sem texto literal está em `[CONFIRMAR]`. Nenhum texto foi escrito para tapar o buraco.
8. A seção 7 não usa frase pronta de “nenhuma pendência”. Ela lista impacto, ou declara checklist conferido de verdade.
9. Não há `file:///` nem caminho de máquina. Alvo ausente está como `[REFERÊNCIA INDISPONÍVEL]`.
10. A seção 8 não contradiz o corpo. Heading 1 aparece só no título.
11. Não há solução técnica, critério subjetivo, termo fora do glossário sem `[CONFIRMAR]`, nem persona genérica.

---

<!--
CHECKLIST DE VALIDAÇÃO DESTA SKILL:
[ ] Não repete entender-problema, levantar-requisitos, listar-funcionalidades, esbocar-wireframe, mapear-fluxo nem revisar-criticamente?
[ ] Confirma a funcionalidade na lista mais recente antes de redigir, grava HU-XX alinhado a FXX e não usa US-XX?
[ ] Preserva Como / Quero / Para que e as seções 1 a 8?
[ ] Não cria portão além de /nova-funcionalidade?
[ ] O checklist 1 a 11 cobre cenário duplo, regra inchada, ID ambíguo, citação quebrada, desenho divergente, UI na regra, escopo estourado, mensagem inventada, pendência falsa, link absoluto e changelog contraditório?
-->
