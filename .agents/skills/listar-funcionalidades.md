---
name: "listar-funcionalidades"
description: "Monta a lista de funcionalidades de um produto a partir dos arquivos de contexto/, no formato de exemplos/funcionalidades/funcionalidades-bom.md: uma tabela por funcionalidade, com o título no padrão ARO (Ação, Resultado e Objeto), a categoria Passos e a linha Step map com itens HU-XX. Use quando o @analista precisar listar as ações do sistema, o que cada uma resolve, o que está fora de escopo, a sequência de passos e os itens de backlog."
---

# Skill: Listar Funcionalidades

> 💡 **MECANISMO DE DISPARO:**  
> Use com o `@analista` quando o pedido for a lista de funcionalidades de um produto: todas as ações que o sistema ou uma persona executa, com problema, benefício, a receita de passos e o step map. Vale para qualquer workspace que tenha `contexto/`. Não use para redigir história de usuário.

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

- `exemplos/funcionalidades/funcionalidades-bom.md` — uma tabela por funcionalidade, com as categorias em linhas, inclusive Passos, sob módulo e persona, e a seção de limites. A linha Step map segue a seção 5 desta skill.
- `exemplos/funcionalidades/funcionalidades-ruim.md` — os sete erros que a lista não pode repetir.

Não altere `contexto/`. Não escreva história de usuário. Não cite tecnologia, tela, banco, API nem framework.

---

## 2. Procedimento

1. **Extrair ações, não módulos soltos.** Percorra personas, transições de status e regras vigentes. Cada ação observável vira uma candidata: quem dispara, o que acontece, em que estado ou momento. Módulo de `produto.md` só entra se corresponder a uma ação. A mesma ação sobre vários itens do mesmo tipo é uma funcionalidade só.
2. **Separar limite de ação.** Proibição, "não somos" e "o que não é" vão para Limites e Não-Escopo, com o arquivo de origem. Não viram tabela de funcionalidade.
3. **Completar a tabela só com o que o contexto sustenta.**
   - **Funcionalidade:** título no padrão ARO, seção 3. No vocabulário do glossário, quando o projeto tiver glossário.
   - **Descrição:** comportamento visível. Diga quem age. Se o ator é o sistema, escreva "O sistema".
   - **Problema que Resolve:** dor ou gambiarra da persona, ou falha já escrita no contexto. Sem dor observável, não invente: use `[CONFIRMAR]`.
   - **Benefícios que Traz:** efeito concreto ligado a esse problema. Sem adjetivo vazio (`ágil`, `robusto`, `inteligente`, `moderno`, `completo`).
   - **Passos:** receita da seção 4. O que a persona faz para concluir a tarefa daquela funcionalidade. O `@analista` valida esse texto.
   - **Step map:** itens de backlog da seção 5, derivados dos Passos da mesma tabela, ainda nesta construção. Não deixe a lista sem essa linha para preencher depois.
4. **Marcar o que não está fechado.** Hipótese para avançar leva `⚠️ [SUPOSIÇÃO]` na célula, como em `funcionalidades-bom.md`. Item `[CONFIRMAR]` do contexto não vira funcionalidade decidida: fica na seção Pendências. Passo ou item do step map sem respaldo no contexto leva `[CONFIRMAR]` no próprio texto; não invente elo para alongar a receita nem o mapa.
5. **Ordenar pelas personas que executam ou pelo fluxo.** Agrupe as funcionalidades por módulos, quando houver. Ordene pelas personas que as executam. Se houver catálogo de status, a ordem das funcionalidades segue as transições. Cada funcionalidade é uma tabela. Não reúna várias funcionalidades na mesma tabela. Numere os HU na ordem de leitura do arquivo, sem reiniciar a cada funcionalidade.
6. **Conferir os sete erros** de `funcionalidades-ruim.md`, o padrão ARO, as regras da categoria Passos e as regras do Step map antes de gravar. Corrija a tabela ou retire-a.
7. **Entregar para validação do** `@analista`**.** Grave o arquivo com Passos e Step map preenchidos e com as linhas `Validação dos passos: pendente do @analista.` e `Step map: pendente do @analista.` No chat, mostre por funcionalidade o título, a receita e os itens HU, e peça validação: aceitar, corrigir ou marcar `[CONFIRMAR]`. Só depois da confirmação explícita troque a linha correspondente para `Validação dos passos: confirmada pelo @analista em AAAA-MM-DD.` ou `Step map: confirmado pelo @analista em AAAA-MM-DD.` Confirmar uma linha não confirma a outra.

---

## 3. Padrão ARO do título

Todo artefato novo deste tipo — lista de funcionalidades gravada em `entregas/funcionalidades/` — nomeia a categoria **Funcionalidade** e o título de cada item do Step map no padrão ARO, nesta ordem:

1. **Ação** — verbo no infinitivo: o que se faz.
2. **Resultado** — substantivo: o efeito obtido.
3. **Objeto** — sobre o que o resultado incide.

Forma do título: `[Ação] [resultado] de/do/da [objeto]`.

O título da funcionalidade sai da descrição, do problema e do benefício da mesma tabela. O título do item do step map sai da intenção daquele item. Mantém o sentido dessas categorias. Não é nome de módulo, nem só o verbo, nem sigla solta. O mesmo título da funcionalidade aparece no cabeçalho da tabela e na linha **Funcionalidade**.

Referência já no formato: `exemplos/funcionalidades/funcionalidades-bom.md`. Exemplo: "Registrar sinais vitais e queixa principal do paciente" — Registrar (ação), sinais vitais e queixa principal (resultado), paciente (objeto).

---

## 4. Categoria Passos

A categoria **Passos** ocupa uma linha da tabela da funcionalidade. Ela descreve a execução daquela funcionalidade: a sequência do que a pessoa faz para chegar ao resultado, como uma receita — um passo depois do outro, até a tarefa acabar.

O texto dessa categoria é proposta para o `@analista` validar. Não é regra de negócio nova e não entra em `contexto/`.

### 4.1. O que é um passo

- Ação da persona da funcionalidade, no vocabulário do glossário quando houver glossário.
- Um verbo no infinitivo e um objeto. Um passo, uma ação.
- Ordem de execução: o passo N do caminho principal ocorre depois do N−1.
- Só entra passo sustentado pela descrição da funcionalidade, pelo contexto ou pelo que o operador afirmou. Sem isso, `[CONFIRMAR]` no passo ou o passo fica de fora.

### 4.2. Lista numerada

O conteúdo da célula é uma lista numerada. Separe os itens com `<br>`, para a tabela Markdown permanecer válida. Não use quebra de linha crua dentro da célula.

Caminho principal:

```text
1. [Verbo no infinitivo] [objeto]<br>2. [Verbo] [objeto]<br>3. [Verbo] [objeto]
```

### 4.3. Passo que não é linear

Quando a tarefa se divide, repete ou pode ser pulada, a lista continua numerada e o desvio fica explícito. Não esconda dois rumos num único item com "ou".

| Situação | Como escrever |
| --- | --- |
| Decisão com dois ou mais rumos | No passo da condição, escreva `Se [condição]:`. Numere cada ramo `Na`, `Nb`, `Nc`. Cada ramo diz se encerra ou em qual número o fluxo continua. |
| Passo opcional | Número próprio, marca `(opcional)` e a condição em que a persona o executa. |
| Repetição | No passo, `volte ao passo N` e a condição que tira a persona do ciclo. |

Exemplo de formato (ilustra a notação; não é conteúdo de produto):

```text
1. [Ação inicial]<br>2. Se [condição sustentada no contexto]:<br>2a. [Ramo A] e encerre<br>Senão:<br>2b. [Ramo B]<br>3. [Ação que segue só depois de 2b]<br>4. (opcional) Se [condição], [ação extra]; senão, siga para o passo 5<br>5. Se [condição de repetição], volte ao passo 2<br>Senão: [ação final]
```

---

## 5. Categoria Step map

A categoria **Step map** ocupa a linha seguinte a **Passos**, na mesma tabela, e entra durante a construção da funcionalidade. Ela lista os itens de backlog que a técnica de step map do Product Backlog Building (PBB) extrai da receita. Cada item é o escopo de uma especificação futura. A receita permanece na linha Passos.

O texto é proposta para o `@analista` validar. Não é regra de negócio nova, não entra em `contexto/` e não substitui a história de usuário.

### 5.1. Granularidade

Um item é uma intenção, da persona ou do sistema, com um resultado observável.

- Variação do mesmo gesto permanece no mesmo item: confirmação ou recusa, vínculo reconhecido ou ausente, agravo novo ou já existente, ramo `Se` / `Senão` que só muda a resposta daquele gesto. A descrição cita os números dos passos.
- Intenção em outro momento, ou com outro resultado, vira outro item.
- Mensagem, campo isolado e reação do sistema ao mesmo gesto não viram item. A mudança de status que é o resultado do gesto fica na descrição.
- Comportamento que outro item já cobre é citado pelo `HU-XX` dele. A descrição não repete a receita desse vizinho.
- Quando o ator é o sistema, a descrição começa com "O sistema".
- Lacuna `[CONFIRMAR]` do contexto não vira item decidido. Se o passo existir e o detalhe estiver aberto, o `[CONFIRMAR]` fica na descrição daquele item.

### 5.2. Rótulo e forma da linha

O rótulo é `HU-XX`, com hífen e dois algarismos. A numeração é sequencial na ordem de leitura do arquivo: se a primeira funcionalidade tem quatro itens, vão de HU-01 a HU-04; a seguinte continua em HU-05. Não use o número da funcionalidade como número da HU. Não use três algarismos.

Separe os itens com `<br>`. Não use quebra de linha crua dentro da célula.

O título ARO e a descrição ficam separados por um travessão. O título termina com ponto. A forma de cada item é:

```text
**HU-07** — Corrigir campos da ficha da notificação. — Passos 1a, 1b, 2 e 3a: em Em correção, a ficha abre na composição vigente.
```

Leitura: `HU-XX`, travessão, título ARO, ponto, travessão, descrição. A descrição diz quais passos o item cobre e, quando houver, qual `HU-XX` fica com o comportamento vizinho.

---

## 6. Gabarito de Saída

Grave em `entregas/funcionalidades/AAAA-MM-DD-lista-funcionalidades.md`. Se esse arquivo já existir na data, acrescente um sufixo curto ao assunto. Não grave em `contexto/` nem na raiz de `entregas/`.

```markdown
# Lista de Funcionalidades do Produto: [Nome em produto.md]

> 📋 **Contexto e Origem:**
> Documento elaborado pelo `@analista` com base nos arquivos de `contexto/` e no formato de `exemplos/funcionalidades/funcionalidades-bom.md`, com as categorias Passos e Step map desta skill.
> Validação dos passos: pendente do @analista.
> Step map: pendente do @analista.

## Lista de Funcionalidades com Problemas, Benefícios, Passos e Step map

### [Módulo, quando houver]

#### [Persona que executa, quando houver]

##### **F001** — [Ação] [resultado] de [objeto]

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | [Ação] [resultado] de [objeto] |
| **Descrição** | [Quem age e o que o sistema faz de observável] |
| **Problema que Resolve** | [Dor ou gambiarra citada no contexto] |
| **Benefícios que Traz** | [Efeito concreto dessa ação] |
| **Passos** | 1. [Ação da persona]<br>2. Se [condição]:<br>2a. [Ramo] e encerre<br>Senão:<br>2b. [Ramo]<br>3. [Ação seguinte] |
| **Step map** | **HU-01** — [Título ARO]. — [Passos que este item cobre e o HU do comportamento vizinho]<br>**HU-02** — [Título ARO]. — [Passos que este item cobre] |

### Limites e Não-Escopo

- ❌ **[Nome curto]:** [Proibição copiada do contexto]. Origem: `[arquivo]`.

### Pendências

- `[CONFIRMAR]` [Lacuna do contexto que impediu uma funcionalidade ou um detalhe]
```

IDs de funcionalidade seguem `F001`, `F002`, sem pular número. A seção Pendências só aparece se houver lacuna.

Uma funcionalidade, uma tabela. As categorias são linhas, nesta ordem: Funcionalidade, Descrição, Problema que Resolve, Benefícios que Traz, Passos, Step map. O identificador e o título ARO ficam no cabeçalho, acima da tabela.

O nível desse cabeçalho acompanha o agrupamento. Com módulo e persona, como em `funcionalidades-bom.md`, use `###` para o módulo, `####` para a persona e `#####` para a funcionalidade. Sem módulo nem persona, o cabeçalho da funcionalidade fica em `###`. Notas de módulo ou de persona ficam em parágrafo, fora da tabela.

---

## 7. O que não entra na tabela

- Solução técnica ou nome de componente.
- Capacidade que o contexto proíbe.
- Área que o contexto deixou de fora.
- Benefício sem problema, ou problema que ninguém no contexto sofre.
- Ação sem fato em `contexto/` e sem pedido do operador. Hipótese, se for preciso discuti-la, fica marcada `⚠️ [SUPOSIÇÃO]`.
- Não-escopo genérico, do tipo "o sistema fará o que for preciso no futuro".
- Título de Funcionalidade, ou título de item do step map, fora do padrão ARO.
- Passo que não seja ação da persona, passo interno de processamento, ou dois rumos no mesmo número sem `Na` / `Nb`.
- Receita só linear quando o contexto já descreve alternativa, retorno ou passo que pode não ocorrer.
- Categoria Passos vazia, em parágrafo corrido, ou com quebra de linha crua dentro da célula.
- Step map ausente, item que junta duas intenções, item que é só mensagem ou reação do mesmo gesto, ou numeração de HU reiniciada a cada funcionalidade.
- Título de HU sem o travessão entre o título ARO e a descrição.
- História de usuário (Como / Quero / Para que, cenário) escrita dentro do step map.
- Várias funcionalidades na mesma tabela, ou as categorias lado a lado numa linha só.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO:
[ ] Cada tabela é uma ação observável, com descrição, problema, benefício, passos e step map?
[ ] O título da funcionalidade e o de cada item HU estão em ARO: ação, resultado e objeto, nesta ordem?
[ ] Cada item do step map é uma intenção, e a variação do mesmo gesto ficou no mesmo item?
[ ] O rótulo HU-XX é sequencial no arquivo, e a forma é `**HU-XX** — [Título]. — [Descrição]`?
[ ] Os termos batem com o glossário e nenhuma regra [REVOGADA] foi usada?
[ ] Os limites excluem algo e citam o arquivo de origem?
[ ] Não há tecnologia, adjetivo vazio, escopo inflado nem ação inventada sem ⚠️ [SUPOSIÇÃO]?
[ ] O arquivo foi gravado em entregas/funcionalidades/ e contexto/ não foi alterado?
-->
