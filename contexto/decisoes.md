# Registro de Decisões de Produto (ADRs de Negócio)

> 💡 **PAPEL DESTE ARQUIVO:**  
> Registra o histórico de decisões estratégicas e funcionais tomadas para o produto. Ele impede que debates já superados sejam reabertos semanalmente e orienta a IA sobre escolhas anteriores.  
> 🔄 **A CLÁUSULA ESSENCIAL:** A linha *"Revisitar se..."* é obrigatória. Sem ela, decisões viram dogmas imutáveis mesmo quando o cenário muda.

---

## `[DEC-01]` — Teto de empréstimos fica no cadastro do leitor

- **Data da Decisão:** `2026-11-11` · **Decidido por:** PO, na atualização de `produto.md`
- **Status:** `⚪ Substituída por DEC-04`

### 1. Contexto e Problema
- `[RN-05]` fixava 3 empréstimos ao mesmo tempo para cada pessoa. A ficha passou a tratar o máximo como configuração do cadastro do leitor e a recusar vários exemplares de um mesmo título.

### 2. Decisão Tomada
- Não há número fixo de empréstimos para todos os leitores. O gestor define o máximo em paralelo no cadastro de cada leitor. O leitor não retira mais de um exemplar do mesmo título ao mesmo tempo. Empréstimo já devolvido continua fora dessa conta.

### 3. Alternativas Descartadas e Motivo
- ❌ **Teto fixo de 3 para toda pessoa:** era a regra anterior e foi substituída pela ficha atualizada.
- ❌ **Vários exemplares do mesmo título ao mesmo tempo:** a ficha recusa.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:** a biblioteca passar a exigir o mesmo número para todos os leitores, ou passar a emprestar mais de um exemplar do mesmo título ao mesmo tempo. Esta decisão foi substituída em 2026-11-11 por `[DEC-04]`.

---

## `[DEC-02]` — O acervo registra obra, com tipo

- **Data da Decisão:** `2026-11-11` · **Decidido por:** PO, na atualização de `produto.md`
- **Status:** `🟢 Ativa`

### 1. Contexto e Problema
- O glossário deixava obra de fora e o acervo estava descrito só como livro, com a pergunta aberta se entrava item que não fosse livro.

### 2. Decisão Tomada
- Obra é o registro do item no acervo. O tipo é livro, revista, HQ, brinquedo ou outro. Exemplar continua a unidade física, de qualquer tipo.

### 3. Alternativas Descartadas e Motivo
- ❌ **Acervo somente de livros:** descartado pela ficha atualizada, que nomeia os cinco tipos.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:** um desses tipos deixar de ser emprestado, ou entrar um tipo que não caiba em "outro".

---

## `[DEC-03]` — Duração da suspensão no momento em que ela é aplicada

- **Data da Decisão:** `2026-11-11` · **Decidido por:** PO, na atualização de `glossario.md`
- **Status:** `🟢 Ativa`

### 1. Contexto e Problema
- `[RN-08]` deixava em aberto a duração da suspensão e o que o leitor suspenso ficava impedido de fazer.

### 2. Decisão Tomada
- A duração é informada pelo gestor que recebe o exemplar atrasado. Não há quantidade fixa de dias. A suspensão encerra sozinha ao fim dessa duração. Enquanto valer, o gestor não aceita novo empréstimo para esse leitor. A suspensão continua condicionada à configuração ligada.

### 3. Alternativas Descartadas e Motivo
- ❌ **Quantidade fixa de dias para toda suspensão:** a ficha do glossário não adotou número. A duração sai no instante da aplicação.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:** a biblioteca passar a usar a mesma duração em toda suspensão, ou a suspensão passar a impedir outro ato além do novo empréstimo.

---

## `[DEC-04]` — Padrão de 2 empréstimos e um exemplar por obra

- **Data da Decisão:** `2026-11-11` · **Decidido por:** PO
- **Status:** `🟢 Ativa`

### 1. Contexto e Problema
- `[DEC-01]` deixava o máximo sem número e bloqueava pelo título. O título não distingue a obra.

### 2. Decisão Tomada
- O padrão de empréstimos em paralelo é 2 para todo leitor. O gestor pode aumentar esse número no cadastro do leitor e não pode deixá-lo abaixo de 2. O leitor não empresta dois exemplares da mesma obra ao mesmo tempo. Duas obras podem ter o mesmo título.

### 3. Alternativas Descartadas e Motivo
- ❌ **Máximo sem piso e sem padrão:** substituído pelo padrão 2 e pelo piso 2.
- ❌ **Bloqueio pelo título:** o título não identifica a obra.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:** a biblioteca passar a usar outro padrão que não seja 2, autorizar máximo abaixo de 2, ou voltar a bloquear pelo título.

---

## `[DEC-05]` — Conformidade limitada às regras deste contexto

- **Data da Decisão:** `2026-11-11` · **Decidido por:** PO
- **Status:** `🟢 Ativa`

### 1. Contexto e Problema
- O cadastro do leitor tem nome e CPF, e os dados dos cadastrados não saem para outras ferramentas da internet. Nenhuma norma tinha sido nomeada.

### 2. Decisão Tomada
- Nenhuma norma externa neste ciclo. A conformidade são as regras já escritas: nome e CPF único, sem conferência entre nome e CPF, telefone e endereço opcionais, acesso do gestor com usuário e senha, e nenhum compartilhamento externo dos dados.

### 3. Alternativas Descartadas e Motivo
- ❌ **LGPD como norma nomeada do produto:** não foi a opção escolhida. Os cuidados de acesso e de não compartilhar os dados continuam nas regras, sem citar a lei.
- ❌ **ECA por causa da faixa etária do brinquedo:** a faixa etária é dado do registro, não regra de quem pode tomar o exemplar.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:** a biblioteca passar a exigir uma norma nomeada, ou a faixa etária passar a impedir o empréstimo.

---

## `[DEC-06]` — Log das ações do gestor

- **Data da Decisão:** `2026-11-11` · **Decidido por:** PO
- **Status:** `🟢 Ativa`

### 1. Contexto e Problema
- O log estava restrito à edição do cadastro do gestor e do leitor, sem a lista do que guardar nem o alcance da auditoria.

### 2. Decisão Tomada
- O log registra a ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório. Guarda data e hora, o gestor, a ação, o que mudou, a identificação, o valor anterior e o valor novo. A senha não entra. No relatório, guarda o recorte: todas as obras ou um tipo, e todas as já cadastradas ou apenas as que ainda não foram removidas.

### 3. Alternativas Descartadas e Motivo
- ❌ **Log só da edição de gestor e de leitor:** não cobre prazo, suspensão, status nem relatório.
- ❌ **Log da consulta, da pesquisa, do painel e da recusa que não grava dado:** essas ações não alteram informação.
- ❌ **Log do atraso automático, do fim automático da suspensão e da criação do primeiro gestor:** não são ações de um gestor já em operação.

### 4. Cláusula: Revisitar se...
- 🔄 **Revisitar esta decisão se:** a auditoria passar a exigir o atraso automático, o fim da suspensão ou a criação do primeiro gestor.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todas as decisões possuem contexto, escolha e alternativas descartadas?
[ ] Toda decisão possui a cláusula obrigatória "Revisitar se..."?
[ ] A data e os responsáveis foram identificados?
-->
