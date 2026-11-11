# Regras de Negócio Gerais e Invariantes

> 💡 **PAPEL DESTE ARQUIVO:**  
> Centraliza as regras invariantes e restrições lógicas que se aplicam a todo o produto. Toda história de usuário deve referenciar os códigos destas regras (ex: `[RN-01]`, `[RN-02]`).  
> 🔢 **REGRA DE OURO:** O identificador numérico (`RN-XX`) é **permanente**. Se uma regra for revogada, marque-a como `[REVOGADA]` mas nunca reutilize o mesmo número.

---

## 1. Catálogo de Regras de Negócio Gerais

### `[RN-01]` — Consulta aberta da disponibilidade
- **Descrição:** O leitor consulta a disponibilidade do acervo em página pública, sem login e sem cadastro preliminar.
- **Impacto:** A consulta não exige usuário, senha nem cadastro. Cadastro, empréstimo e configuração continuam fora dessa página.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-02]` — Gestão somente com login
- **Descrição:** Só o gestor da biblioteca, autenticado com usuário e senha, altera o acervo, os empréstimos, os usuários, os prazos e o máximo de empréstimos em paralelo do leitor.
- **Impacto:** Leitor sem login não inclui nem remove obra, não registra empréstimo e não muda configuração.
- **Exceção autorizada:** A criação do primeiro gestor, pela equipe de desenvolvimento (`[RN-14]`).

---

### `[RN-03]` — Empréstimo liga leitor e exemplar
- **Descrição:** Um empréstimo registra a retirada de um exemplar por um leitor. Os dois são obrigatórios.
- **Impacto:** Não há empréstimo sem leitor e sem exemplar identificados.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-04]` — Exemplar indisponível não sai
- **Descrição:** Exemplar que não está disponível não é emprestado. Quando a obra tem exemplar emprestado, o sistema informa a data prevista do exemplar que volta primeiro, a mais próxima. Se houver um só, essa é a data informada. Quando o exemplar está indisponível e não há empréstimo, o sistema não informa data prevista: a mensagem é que o exemplar não está disponível para empréstimo.
- **Impacto:** A retirada não se conclui. No exemplar emprestado, a pessoa vê a data prevista mais próxima. No indisponível sem empréstimo, vê só essa mensagem.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-05]` — Teto de empréstimos por pessoa
- **Descrição:** O padrão de empréstimos em paralelo é 2 para todo leitor. O gestor pode aumentar esse máximo no cadastro do leitor. Não pode defini-lo abaixo de 2: valor menor é recusado. Empréstimo devolvido não entra na conta. Empréstimo ativo ou atrasado entra. Se o gestor reduz o máximo, sem ficar abaixo de 2, e o leitor já tem mais empréstimos em paralelo do que o novo valor, o sistema indica ao gestor que a mudança só tem efeito depois da devolução de ao menos um exemplar, ou do encerramento de um deles por extravio. Até lá, vale o máximo anterior.
- **Impacto:** O empréstimo que ultrapassar o máximo em vigor para aquele leitor não se conclui. A redução abaixo de 2 não é gravada.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-06]` — Retirada imediata e prazo configurável
- **Descrição:** A data de retirada é registrada no momento do empréstimo. A data prevista de devolução é calculada pelo prazo configurado pelo gestor. Não há quantidade fixa de dias.
- **Impacto:** Todo empréstimo nasce com data de retirada e data prevista. Mudar o prazo é configuração do gestor, não um número fechado do produto.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-07]` — Devolução libera o exemplar
- **Descrição:** A devolução registrada devolve o exemplar à situação disponível.
- **Impacto:** O exemplar volta a poder ser emprestado. O empréstimo deixa de estar em aberto.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-08]` — Atraso e suspensão configurável
- **Descrição:** Há atraso quando a data prevista de devolução passa e o exemplar não foi devolvido. O sistema pode ser configurado para suspender o leitor que não cumpriu esse prazo. A duração é informada pelo gestor que recebe o exemplar atrasado. Não há quantidade fixa de dias. A suspensão encerra sozinha ao fim dessa duração. Enquanto valer, o gestor não aceita novo empréstimo para esse leitor.
- **Impacto:** O empréstimo atrasado fica identificado. Com a configuração ligada, o novo empréstimo para o leitor suspenso não se conclui. Ao fim da duração, a suspensão deixa de valer sem novo ato do gestor.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-09]` — Código único do exemplar
- **Descrição:** Cada exemplar tem um código único, atribuído e guardado no sistema. O código não é calculado a partir de ISBN nem de outro dado externo.
- **Impacto:** Dois exemplares não compartilham o mesmo código, nem quando são da mesma obra. O código não identifica a obra. O controle da retirada usa esse código.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-10]` — Um exemplar por obra em paralelo
- **Descrição:** O leitor não empresta dois exemplares da mesma obra ao mesmo tempo. O título não identifica a obra: duas obras podem ter o mesmo título, e isso não bloqueia a retirada.
- **Impacto:** A retirada de outro exemplar da mesma obra não se conclui enquanto houver empréstimo em paralelo dessa obra para o mesmo leitor. Exemplares de obras distintas saem, ainda que o título seja igual.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-11]` — CPF obrigatório do leitor
- **Descrição:** O cadastro do leitor exige nome e CPF. O CPF é único entre leitores. O nome não é conferido com o CPF e pode ser apelido ou nome social. Telefone e endereço são opcionais.
- **Impacto:** Sem nome ou sem CPF, o cadastro não se conclui. CPF já usado por outro leitor não se conclui. Telefone e endereço podem ficar em branco.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-12]` — Tipo fechado da obra
- **Descrição:** A obra é classificada em um tipo da lista: livro, revista, HQ, brinquedo ou outro. O tipo é obrigatório. Os dados são os do tipo. Livro: título, autor, editora, ISBN, ano, gênero, categoria, assunto e quantidade de exemplares. HQ: título, autor, ano de publicação, número da edição, editora e quantidade de exemplares. Revista: título, ano de publicação, número da edição, editora e quantidade de exemplares. Brinquedo: nome, descrição, fabricante, faixa etária indicada e quantidade de exemplares. Outro: nome, descrição e quantidade de exemplares.
- **Impacto:** Sem tipo, o cadastro da obra não se conclui. "Outro" não pede nome livre além de nome e descrição. Toda obra guarda a data e a hora da inclusão e o gestor responsável. Na remoção, guarda a data e o gestor responsável pela remoção. A remoção da obra não se conclui enquanto ela tiver exemplar emprestado. A remoção do exemplar emprestado não se conclui. O gestor encerra esse empréstimo como Encerrado por extravio e, depois disso, a remoção pode ser feita (`[RN-13]`).
- **Exceção autorizada:** Nenhuma.

---

### `[RN-13]` — Indisponibilidade do exemplar
- **Descrição:** O gestor leva o exemplar de disponível a indisponível ao registrar a indisponibilidade. O retorno a disponível é o gestor que registra o retorno a disponibilidade. No extravio, o gestor encerra o empréstimo ativo ou atrasado como Encerrado por extravio, e o exemplar emprestado passa a indisponível. O exemplar nasce disponível no cadastro.
- **Impacto:** Exemplar indisponível não é emprestado (`[RN-04]`). O empréstimo Encerrado por extravio deixa de contar para o máximo em paralelo (`[RN-05]`). A remoção do exemplar emprestado fica bloqueada até esse encerramento (`[RN-12]`).
- **Exceção autorizada:** Nenhuma.

---

### `[RN-14]` — Primeiro gestor e log de auditoria
- **Descrição:** O primeiro gestor é criado pela equipe de desenvolvimento. Esse gestor e os demais criam novos gestores, com usuário e senha, e acessam as funcionalidades do sistema. A ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório, gera log. O log guarda data e hora, o gestor, a ação, o que mudou, a identificação, o valor anterior e o valor novo. Na inclusão, o valor anterior fica vazio. Na remoção, o valor novo é a remoção. No relatório, guarda o recorte e não guarda valor anterior nem novo. A senha não entra no log. Uma ação que altera exemplar e empréstimo gera um log, com os dois resultados. As ações são: cadastrar, editar e remover obra; cadastrar exemplar; cadastrar e editar leitor; definir o máximo de empréstimos em paralelo, com o valor anterior, o valor pedido e se passou a valer ou ficou aguardando devolução ou encerramento por extravio; cadastrar e editar gestor; configurar o prazo; ligar ou desligar a suspensão; informar a duração da suspensão; registrar empréstimo; registrar devolução; registrar indisponibilidade; registrar o retorno a disponibilidade; encerrar por extravio; emitir relatório.
- **Impacto:** Sem esse primeiro gestor, não há quem entre. A ação listada não se conclui sem o log. Consulta, pesquisa, painel e recusa que não grava dado não geram log. A passagem do empréstimo a atrasado e o fim da suspensão, feitos pelo sistema, não geram log.
- **Exceção autorizada:** A criação do primeiro gestor, pela equipe de desenvolvimento. Ela não é um papel do produto, não opera o acervo nem o empréstimo, e não gera log.

---

## 2. Tabela de Números e Parâmetros com Origem

> 📊 *Todo número, prazo, tamanho de arquivo ou limite que aparecer em uma história deve estar registrado nesta tabela com sua respectiva fonte/origem.*

| Parâmetro / Limite | Valor Oficial | Origem / Fonte da Definição | Onde se Aplica |
|---|:--:|---|---|
| **Empréstimos em paralelo por leitor** | Padrão 2. O gestor pode aumentar no cadastro do leitor. Não fica abaixo de 2. O valor 3 foi substituído em 2026-11-11. | PO, em 2026-11-11 | Registro de empréstimo (`[RN-05]`) |
| **Exemplares da mesma obra em paralelo** | No máximo um | PO, em 2026-11-11 | Retirada (`[RN-10]`) |
| **Prazo de empréstimo e de devolução** | Configurável; sem quantidade de dias | Fonte (prazo estabelecido pela biblioteca) e respostas do PO nos portões de produto e de regras | Data prevista de devolução (`[RN-06]`) |
| **Duração da suspensão por atraso** | Informada pelo gestor que recebe o exemplar atrasado. Encerra sozinha ao fim. Sem quantidade fixa de dias | PO, em 2026-11-11 | Leitor suspenso (`[RN-08]`) |
| **Código do exemplar** | Único, guardado no sistema, sem derivar de ISBN nem de outro dado externo | PO, em 2026-11-11, sobre o uso exclusivo no sistema | Identificação do exemplar (`[RN-09]`) |
| **Duração do registro no sistema** | Não chega a meia hora, no empréstimo, no cadastro da obra e no cadastro do leitor. Na agenda, a ação é de minutos. | PO, em 2026-11-11 | Métrica de guarda |
| **Leitor no painel** | Com empréstimo cuja data de retirada está nos últimos 6 meses | PO, em 2026-11-11, módulo Painel | Painel |
| **Itens do acervo digitalizados** | Mais de 100, em 3 meses a partir da implantação | `produto.md`, meta principal | Meta de ciclo |
| **Leitores cadastrados** | Pelo menos 20 | `produto.md`, meta secundária | Meta de ciclo |
| **Gestores cadastrados** | Pelo menos 5 | `produto.md`, meta secundária | Meta de ciclo. Gestor é a pessoa; usuário é a credencial |
| **Tipos de obra** | Livro, revista, HQ, brinquedo, outro | `produto.md`, módulo Acervo | Cadastro da obra (`[RN-12]`) |

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todas as regras possuem identificadores permanentes [RN-XX]?
[ ] Todos os números e prazos têm origem formal indicada na tabela?
[ ] As exceções autorizadas foram documentadas explicitamente?
-->
