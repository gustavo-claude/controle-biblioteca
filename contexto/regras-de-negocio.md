# Regras de Negócio Gerais e Invariantes

> 💡 **PAPEL DESTE ARQUIVO:**  
> Centraliza as regras invariantes e restrições lógicas que se aplicam a todo o produto. Toda história de usuário deve referenciar os códigos destas regras (ex: `[RN-01]`, `[RN-02]`).  
> 🔢 **REGRA DE OURO:** O identificador numérico (`RN-XX`) é **permanente**. Se uma regra for revogada, marque-a como `[REVOGADA]` mas nunca reutilize o mesmo número.

---

## 1. Catálogo de Regras de Negócio Gerais

### `[RN-01]` — Consulta aberta da disponibilidade
- **Descrição:** O leitor consulta a disponibilidade do acervo em página aberta, sem login.
- **Impacto:** A consulta não exige usuário nem senha. Cadastro, empréstimo e configuração continuam fora dessa página.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-02]` — Gestão somente com login
- **Descrição:** Só o gestor da biblioteca, autenticado com usuário e senha, altera o acervo, os empréstimos, os usuários e os prazos.
- **Impacto:** Leitor sem login não inclui nem remove obra, não registra empréstimo e não muda configuração.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-03]` — Empréstimo liga leitor e exemplar
- **Descrição:** Um empréstimo registra a retirada de um exemplar por um leitor. Os dois são obrigatórios.
- **Impacto:** Não há empréstimo sem leitor e sem exemplar identificados.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-04]` — Exemplar indisponível não sai
- **Descrição:** Exemplar que não está disponível não é emprestado. O sistema informa a data prevista de devolução. A data prevista está no exemplar emprestado. [CONFIRMAR] qual data mostrar quando a mesma obra tiver mais de um exemplar fora, e o que informar quando o exemplar está indisponível sem empréstimo.
- **Impacto:** A retirada não se conclui. A pessoa vê quando a devolução está prevista.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-05]` — Teto de empréstimos por pessoa
- **Descrição:** Cada pessoa pode ter até 3 empréstimos ao mesmo tempo. Empréstimo já devolvido não entra nessa conta.
- **Impacto:** O empréstimo que ultrapassar 3 ativos da mesma pessoa não se conclui.
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
- **Descrição:** Há atraso quando a data prevista de devolução passa e o exemplar não foi devolvido. O sistema pode ser configurado para suspender o leitor que não cumpriu esse prazo. A duração da suspensão e o que o leitor suspenso fica impedido de fazer estão [CONFIRMAR].
- **Impacto:** O empréstimo atrasado fica identificado. Com a configuração ligada, o leitor que falhou o prazo é suspenso.
- **Exceção autorizada:** Nenhuma.

---

### `[RN-09]` — Código único do exemplar
- **Descrição:** Cada exemplar tem um código de identificação único.
- **Impacto:** Dois exemplares não compartilham o mesmo código. O controle da retirada usa esse código.
- **Exceção autorizada:** Nenhuma.

---

## 2. Tabela de Números e Parâmetros com Origem

> 📊 *Todo número, prazo, tamanho de arquivo ou limite que aparecer em uma história deve estar registrado nesta tabela com sua respectiva fonte/origem.*

| Parâmetro / Limite | Valor Oficial | Origem / Fonte da Definição | Onde se Aplica |
|---|:--:|---|---|
| **Empréstimos ao mesmo tempo por pessoa** | 3 | Resposta do PO no portão de regras, sobre o limite de empréstimos ativos citado na fonte | Registro de empréstimo (`[RN-05]`) |
| **Prazo de empréstimo e de devolução** | Configurável; sem quantidade de dias | Fonte (prazo estabelecido pela biblioteca) e respostas do PO nos portões de produto e de regras | Data prevista de devolução (`[RN-06]`) |
| **Duração da suspensão por atraso** | [CONFIRMAR] | O PO autorizou a suspensão configurável e não informou quantidade de dias | Leitor em atraso (`[RN-08]`) |
| **Itens do acervo digitalizados** | Mais de 100 | Resposta do PO no portão de produto; meta de ciclo, não limite de empréstimo | Meta principal em `produto.md` |
| **Usuários cadastrados** | Pelo menos 20 | Resposta do PO no portão de produto; meta de ciclo. [CONFIRMAR] se "usuário" é leitor ou quem opera o sistema | Meta secundária em `produto.md` |

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todas as regras possuem identificadores permanentes [RN-XX]?
[ ] Todos os números e prazos têm origem formal indicada na tabela?
[ ] As exceções autorizadas foram documentadas explicitamente?
-->
