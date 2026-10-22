---
name: "elaborar-especificacao"
description: "Redige uma especificação funcional para um item HU-XX do step map da lista mais recente em entregas/funcionalidades, com cenários Gherkin, regras transcritas e limites de escopo. Antes de gravar, exibe a narrativa e os títulos dos critérios e das regras para validação. Use quando pedirem elaborar, redigir ou reescrever especificação funcional, história de usuário, critérios de aceitação, BDD ou Gherkin."
---

# Skill: Elaborar Especificação Funcional

> 💡 **MECANISMO DE DISPARO:**  
> Use com o `@escritor` para produzir ou reescrever **uma** especificação funcional, de **um** item do step map. O resultado é um markdown que pessoas e outros agentes leiam sem escolher entre versões contraditórias do mesmo comportamento e sem abrir outro arquivo para ler a regra citada.

---

## 1. Objetivo e escopo

Produzir uma especificação verificável de um item do step map: intenção, cenários observáveis, invariantes, anexo visual, fora de escopo e pendências reais.

A unidade de trabalho é o item `HU-XX` da linha **Step map**, não a funcionalidade inteira. A frase da história segue `.agents/rules/02-padrao-historias.md`: **Como / Quero / Para que**. As seções úteis do padrão de especificação permanecem: descrição, narrativa, critérios, regras, outras informações, fora de escopo, suposições e lista de atualizações.

Esta skill **não**:

- investiga a dor (`entender-problema`) nem prepara entrevista (`levantar-requisitos`);
- monta a lista de funcionalidades (`listar-funcionalidades`);
- desenha wireflow (`esbocar-wireframe`) nem diagrama Mermaid (`mapear-fluxo`) — só incorpora o artefato se ele já existir e for legível;
- substitui a auditoria das 7 lentes (`revisar-criticamente` e `.agents/rules/03-revisao-critica.md`);
- altera `contexto/`, `AGENTS.md`, personas, regras, workflows ou exemplos;
- lê arquivo `RECEITA-*.md`;
- grava a especificação da funcionalidade inteira quando o step map já partiu essa funcionalidade em itens;
- abre a Etapa 3 de `/nova-funcionalidade`.

O portão desta skill é o **esboço**, na seção 4, antes de existir arquivo. Ele não substitui os portões do workflow. Dentro de `/nova-funcionalidade`, rode só na Etapa 2, depois do Portão 1: primeiro o esboço, depois o arquivo, e pare no Portão 2. Não abra a Etapa 3.

---

## 2. Leituras

O Passo 0 lê a linha **Step map** da lista mais recente, o suficiente para mostrar o rótulo e o título de cada item. As demais leituras acontecem depois da confirmação do item, antes do esboço. Se o caminho não existir, registre a ausência e siga. Não preencha o buraco com memória ou com o conteúdo “típico” de um arquivo desse nome.

1. O arquivo mais recente em `entregas/funcionalidades/` — fonte principal. A data é o prefixo `AAAA-MM-DD` do nome. Em empate de data, use o arquivo modificado por último. Não misture listas antigas. O item é a entrada `**HU-XX** — [título]. — [descrição]` da linha **Step map**.
2. `exemplos/funcionalidades/funcionalidades-bom.md` — formato da tabela, não a lista do produto. A linha Step map segue `.agents/skills/listar-funcionalidades.md`.
3. `exemplos/especificacoes/especifcacao-boa.md` — forma da especificação pronta: identificador `HU-XX`, seções e cenários. O bloco de regra de catálogo desta skill prevalece sobre o exemplo: a regra citada é transcrita, não apenas apontada.
4. `.agents/rules/02-padrao-historias.md` — frase **Como / Quero / Para que** e gramática do cenário. O título de exemplo dessa regra ainda mostra `US-XX`. Nesta skill o identificador do documento é o `HU-XX` do item. Não grave `US-XX`.
5. `.agents/rules/00-fundacao.md` — fato, suposição e proibição de inventar.
6. `.agents/rules/01-estilo-e-tom.md` — voz e termos subjetivos proibidos.
7. `contexto/produto.md`, `contexto/personas-usuario.md`, `contexto/glossario.md`, `contexto/regras-de-negocio.md`, `contexto/decisoes.md`.
8. `entregas/especificacoes/` — especificações já gravadas, para não sobrescrever o mesmo `HU-XX`.
9. O insumo do pedido: texto no chat, arquivo em `fontes/` ou a especificação que será reescrita.

Não dependa de um documento de análise externo. Os controles já estão nas seções 5 e 8.

---

## 3. Quando parar, marcar ou seguir

**Pare e pergunte** (no máximo 5 perguntas). Não grave arquivo quando:

- a lista não tem linha **Step map**;
- não há persona nomeada no item, na lista nem em `contexto/personas-usuario.md`;
- não há ação principal com resultado observável;
- duas fontes de `contexto/` contradizem o comportamento principal;
- o pedido pede um resultado que ninguém afirmou;
- o esboço da seção 4 ainda não foi aprovado nesta conversa.

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

### Passo 0 — Confirmar o item do step map e parar

1. Leia o arquivo mais recente em `entregas/funcionalidades/`, no critério da seção 2.
2. Se a pasta não tiver lista, pare e registre a ausência. Não trate `exemplos/funcionalidades/funcionalidades-bom.md` como a lista do produto.
3. Se a lista não tiver linha **Step map**, pare. Não especifique a funcionalidade inteira no lugar do item.
4. Apresente cada item pelo rótulo e pelo título ARO, agrupado pela funcionalidade em que aparece. Não cole a descrição do item nesta lista.
5. Pergunte qual item gerar. A resposta aceita é o rótulo (`HU-07`) ou o título ARO correspondente. Se o pedido nomear uma funcionalidade (`F001`), mostre só os itens daquela funcionalidade e pergunte qual deles. Não gere um arquivo para a funcionalidade.
6. **Pare.** Não redija cenários, não monte o esboço e não grave arquivo neste turno.

Se o pedido já nomear um item, mostre o rótulo, o título e a descrição encontrados na linha **Step map** e peça confirmação. Sem confirmação explícita, não avance.

### Passo 1 — Preparar o contexto

Depois da confirmação do item, leia a descrição desse item, os passos que ela cita, a tabela da funcionalidade em que ele está (Funcionalidade, Descrição, Problema que Resolve, Benefícios que Traz, Passos) e os Limites, Pendências e confirmações do mesmo arquivo.

O documento usa o `HU-XX` do item, com hífen e exatamente dois algarismos. Critério, regra e informação colam o número em `HU` e só usam hífen antes da letra:

- item `HU-07` → `HU-07` no título e no nome do arquivo
- cenário `HU07-C01`
- regra local `HU07-R01`
- informação `HU07-I01`

Não use três algarismos (`HU-007`). Não use `US-XX`. Não use `HU-07-C01`. Não escolha o próximo número livre e não use o número da funcionalidade: o número vem do item confirmado. Se `entregas/especificacoes/` já tiver esse `HU-XX`, não sobrescreva; pare e pergunte se a saída é uma versão nova com sufixo no nome do arquivo.

A descrição do item delimita o escopo. Passo da receita que outro item cobre entra na seção 6, com o `HU-XX` desse item. Pendência `[CONFIRMAR]` da lista entra na seção 7 quando altera este item.

Separe o que cada fonte autoriza. Ignore regra marcada `[REVOGADA]`. Use o termo de `contexto/glossario.md`. Se o insumo usa outro termo, não troque pelo vocabulário de outro produto: registre `[CONFIRMAR]`.

### Passo 2 — Verificar os insumos

Liste, em notas suas, fatos, ausências e contradições. Aplique a seção 3 antes de montar o esboço.

### Passo 3 — Organizar

Separe em seis listas, sem redigir o arquivo e sem escrever o Gherkin no chat:

1. intenção (persona, ação, benefício);
2. invariantes — **um por item**, com o título da regra local ou o título da `[RN-XX]` no catálogo;
3. comportamentos — **um evento principal por item**, só o título do critério;
4. exceções e estados vazios que o insumo realmente afirma;
5. material visual e o caráter de cada um (ilustrativo ou normativo);
6. limites de escopo.

Confirmação, cancelamento, falha e nova tentativa são itens próprios na lista 3 quando o usuário age de novo.

### Portão de esboço — Validar antes de escrever

Mostre só isto, nesta ordem, e pare:

1. **Narrativa** — **Como**, **Quero** e **Para que**, já na forma da seção 2 do documento.
2. **Critérios** — um título por linha: `HU07-C01: [caminho-feliz] — [comportamento]`. Sem **Dado que**, **Quando** nem **Então**.
3. **Regras** — um título por linha: `HU07-R01 — [nome do invariante]` ou `[RN-01] — [título como está em contexto/regras-de-negocio.md]`. Sem transcrever o texto da regra neste portão.

Feche com a pergunta: "Estes critérios e estas regras cobrem o item? Pode ajustar ou retirar algum antes de eu escrever o arquivo."

**Pare.** Não grave arquivo, não escreva cenário e não transcreva a regra neste turno.

Aprovação é frase explícita de que o esboço pode ser escrito. Correção, retirada ou inclusão de critério ou regra não é aprovação: atualize o esboço, mostre de novo e pare outra vez. Pedido que já nomeia o item não dispensa este portão.

### Passo 4 — Elaborar

Só depois da aprovação do esboço nesta conversa.

Grave em `entregas/especificacoes/AAAA-MM-DD-HU-07-assunto.md`, com o `HU-XX` do item e o assunto em kebab-case, tirado do título ARO. Se o nome já existir, acrescente um sufixo. Não sobrescreva o arquivo de origem numa reescrita: a origem permanece e a saída é outro arquivo.

O arquivo cobre o esboço aprovado. Critério ou regra que o usuário retirou no portão não entra. Use a estrutura da seção 6 e as regras da seção 5.

### Passo 5 — Validar a consistência

Confira, um por um:

- cada `HUXX-Rnn` tem uma só frase de invariante e uma lista “Demonstrada por” cujos cenários mostram esse invariante no `Então`;
- cada `[RN-XX]` citada tem, neste arquivo, o título e o texto transcrito de `contexto/regras-de-negocio.md`;
- cada citação de cenário para regra aponta para regra que existe neste arquivo;
- nenhum `HUXX-Inn` ilustrativo acrescenta campo, botão, ordem ou texto que o cenário não tenha;
- a seção 6 não é desmentida por cenário nem por desenho;
- todo link é relativo ao repositório e o alvo existe, ou está marcado `[REFERÊNCIA INDISPONÍVEL]`;
- a seção 8 não afirma um estado que o corpo não sustenta.

### Passo 6 — Revisão crítica de forma

Execute o checklist da seção 7. Achado que impede programar sem inventar regra é bloqueante: o status não pode ser “Pronta para validação”.

As 7 lentes e o relatório do `@critico` ficam na skill `revisar-criticamente`. Não as repita aqui. No workflow, essa auditoria só começa depois do Portão 2.

### Passo 7 — Entregar

Responda com:

1. caminho do arquivo;
2. status: `Pronta para validação` ou `Requer esclarecimento`;
3. checklist da seção 7, com cada item em conforme ou não conforme;
4. pendências `[CONFIRMAR]`, `[CONFLITO]` e `⚠️ [SUPOSIÇÃO]`, cada uma com o impacto;
5. limitação de leitura (arquivo ausente, exemplo do kit divergente, referência fora do pacote).

`Pronta para validação` exige checklist sem bloqueante, zero `[CONFLITO]` e zero `[CONFIRMAR]` que mude comportamento ou aceite. Suposição marcada impede esse status.

---

## 5. Regras de elaboração

### Hierarquia e leitura

- Um heading 1: o título. Seções em heading 2. Cenários em heading 3. Não use heading 4 ou 5. Não envolva o heading em negrito.
- A lista de atualizações é a **seção 8**, no fim. Ela registra quem alterou a redação. Não interrompe a descrição nem vale como requisito.
- Não repita o mesmo comportamento na descrição, no cenário e na regra local. A descrição diz o objetivo em um parágrafo. O cenário mostra o exemplo. A regra local enuncia o invariante em uma frase.
- A regra de catálogo é a exceção: o texto transcrito fica só na seção 4. O cenário cita o `[RN-XX]` e não cola esse texto de novo no **Então**.

### História e cenários

- Persona nomeada, nunca “o usuário”. A mesma persona em todos os passos, salvo cenário de outra persona (permissão). Quando o step map diz que o ator é o sistema, a narrativa usa **Como** o sistema.
- Passos em lista, palavra-chave em negrito, como na regra 02. Não gere `.feature` salvo pedido explícito.
- **Dado que** e o **E** que o segue: só contexto. **Quando**: uma ação voluntária de uma persona, ou um único carregamento quando o comportamento é abrir a tela. No item em que o ator é o sistema, o **Quando** é o fato que dispara aquela resposta, um só. **Então** e o **E** que o segue: só resposta observável do sistema a esse Quando.
- Proibido um segundo gesto dentro do Então. “E ao clicar em …” abre outro cenário.
- Pré-condição repetida em dois ou mais cenários vai para o bloco **Contexto compartilhado**, uma vez.
- Variação do mesmo comportamento (dados diferentes, mesmo evento) vira **Esquema do cenário** com tabela **Exemplos**. Não empilhe essa variação em vários **E**.
- Rótulo único, no título do cenário: `caminho-feliz`, `alternativa`, `erro`, `estado-vazio`, `permissao`. Sem barra e sem combinação.
- A regra 02 pede as famílias feliz, erro, vazio e permissão. Se o insumo não traz uma delas, não invente o cenário: diga na seção 7 que a família está sem fato.
- Mensagem observável vai entre aspas. Sem o texto, use `[CONFIRMAR: texto da mensagem de …]`.
- Critério binário: passou ou falhou. Sem adjetivo subjetivo e sem solução técnica (tabela, endpoint, framework, cor hexadecimal, “banco de dados”).
- Nome de botão e texto de mensagem ficam no cenário, porque são o que se observa. Não viram regra de negócio.

### Regras e rastreabilidade

- Uma regra local, um invariante, uma frase: `HU07-R01`.
- Invariante já cadastrado: traga o `[RN-XX]` para dentro da história. Não crie número novo em `contexto/regras-de-negocio.md` e não altere esse arquivo.
- Transcreva o bloco da regra como está no catálogo: título, **Descrição**, **Impacto** e **Exceção autorizada**. Não resuma, não reescreva e não omita a exceção. O leitor da história não precisa abrir o catálogo para saber o que a regra diz.
- Cite só a `[RN-XX]` que este item demonstra. Regra do catálogo que outro item cobre fica na seção 6, sem transcrição.
- A regra local não copia o cenário. A rastreabilidade é uma linha: `Demonstrada por: HU07-C02`. Inclua o cenário nessa linha somente se o `Então` dele torna o invariante visível. Caso contrário, `[CONFLITO]`. Na regra transcrita, a mesma linha lista só os cenários deste item que tornam visível a parte usada aqui. O texto transcrito permanece o bloco inteiro.
- O cenário pode citar o ID da regra uma vez. A regra não cita o cenário no título e de novo no fim do parágrafo.
- O documento se chama `HU-XX`. Critério, regra e informação usam `HUXX-Cnn`, `HUXX-Rnn` e `HUXX-Inn`: `HU07-C01`, `HU07-R01`, `HU15-I01`. Proibido `HU-07-C01`, `US-XX` e reiniciar em `CA001`, `RN01` ou `IN001` sem esse prefixo.
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
# HU-07 Título orientado à ação

> Prevalece, nesta ordem: cenário, regra, anexo ilustrativo. A lista de atualizações não altera o corpo.

## 1. Descrição

Um parágrafo com o objetivo deste item. Sem repetir os cenários.

## 2. Narrativa da História

- **Como** [persona de contexto/personas-usuario.md, o sistema quando o step map diz que o ator é o sistema, ou a do insumo com CONFIRMAR se não estiver cadastrada]
- **Quero** [ação observável deste item]
- **Para que** [benefício concreto deste item]

## 3. Critérios de Aceite

### Contexto compartilhado

- **Dado que** [só se dois ou mais cenários repetirem a mesma pré-condição]

### HU07-C01: [caminho-feliz] — [um comportamento]

- **Dado que** [contexto que não está no bloco compartilhado]
- **Quando** [a persona] [uma ação]
- **Então** [resultado observável] `[RN-XX]` ou `HU07-R01`
- **E** [outra resposta do mesmo Quando]

### HU07-C02: [alternativa] — [o segundo gesto, se houver]

- **Dado que** [estado deixado pelo cenário anterior]
- **Quando** [a persona] [a segunda ação]
- **Então** [resultado observável]

### HU07-C03: [caminho-feliz] — [variação de dados do mesmo evento]

- **Esquema do cenário**
- **Dado que** o caso é "<caso>"
- **Quando** [a persona] [a mesma ação]
- **Então** o resultado observável é "<resultado>"

Exemplos:

| caso | resultado |
| --- | --- |
| [valor afirmado] | [valor afirmado] |

## 4. Regras de Negócio

### HU07-R01 — [nome do invariante]

[Uma frase, sem widget e sem roteiro de tela.]

Demonstrada por: HU07-C01

### [RN-01] — [título como está no catálogo]

- **Descrição:** [texto transcrito de contexto/regras-de-negocio.md]
- **Impacto:** [texto transcrito]
- **Exceção autorizada:** [texto transcrito]

Demonstrada por: HU07-C02

## 5. Outras Informações Relevantes

### HU07-I01 — [nome do anexo]

- **Caráter:** Ilustrativo
- **Alvo:** [caminho relativo] ou `[REFERÊNCIA INDISPONÍVEL: caminho]`

O desenho, se permanecer, só repete o que os cenários já aceitam.

## 6. O que esta História NÃO cobre

- [comportamento] — `HU-08`, ou `[FORA DESTE PACOTE: HU-08]`

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
2. Cada regra local é um invariante. Nenhuma regra local repete o roteiro do cenário nem junta falha e sucesso no mesmo bloco.
3. O documento é o `HU-XX` do item do step map. Critério, regra e informação usam `HU07-C01`, `HU07-R01` e `HU07-I01`, sem hífen entre `HU` e o número. Não há `US-XX` nem `HU-07-C01`. Cada ID citado existe no arquivo. O arquivo não cobre outro item do mesmo step map.
4. Cada “Demonstrada por” foi conferida contra o Então do cenário. Citação quebrada ou cobertura parcial está em `[CONFLITO]`, não foi “corrigida” sozinha.
5. Cenário, regra e anexo ilustrativo não divergem. O anexo não especifica o que a seção 6 exclui.
6. Regra local não contém cor, componente, campo de tela nem nome de botão. Isso está no cenário, ou não está no documento.
7. Mensagem sem texto literal está em `[CONFIRMAR]`. Nenhum texto foi escrito para tapar o buraco.
8. A seção 7 não usa frase pronta de “nenhuma pendência”. Ela lista impacto, ou declara checklist conferido de verdade.
9. Não há `file:///` nem caminho de máquina. Alvo ausente está como `[REFERÊNCIA INDISPONÍVEL]`.
10. A seção 8 não contradiz o corpo. Heading 1 aparece só no título.
11. Não há solução técnica, critério subjetivo, termo fora do glossário sem `[CONFIRMAR]`, nem persona genérica.
12. Cada `[RN-XX]` referenciada traz, neste arquivo, título, descrição, impacto e exceção autorizada transcritos de `contexto/regras-de-negocio.md`. Remeter o leitor ao catálogo sem esse texto é bloqueante. O texto transcrito não foi resumido nem reescrito.

---

<!--
CHECKLIST DE VALIDAÇÃO DESTA SKILL:
[ ] Não repete entender-problema, levantar-requisitos, listar-funcionalidades, esbocar-wireframe, mapear-fluxo nem revisar-criticamente?
[ ] Confirma um item do step map, para no portão de esboço antes de gravar, usa o HU-XX desse item e não usa US-XX?
[ ] Preserva Como / Quero / Para que e as seções 1 a 8?
[ ] O portão de esboço mostra narrativa, títulos de critérios e títulos de regras, e não grava arquivo nesse turno?
[ ] A regra [RN-XX] é transcrita na história, com descrição, impacto e exceção, sem alterar o catálogo?
[ ] Não abre a Etapa 3 de /nova-funcionalidade?
[ ] O checklist 1 a 12 cobre cenário duplo, regra inchada, ID ambíguo, citação quebrada, desenho divergente, UI na regra, escopo estourado, mensagem inventada, pendência falsa, link absoluto, changelog contraditório e regra de catálogo sem transcrição?
-->
