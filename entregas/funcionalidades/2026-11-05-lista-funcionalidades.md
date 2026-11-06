# Lista de Funcionalidades do Produto: Biblioteca Limoeiro

> 📋 **Contexto e Origem:**
> Documento elaborado pelo `@analista` com base nos arquivos de `contexto/` e no formato de `exemplos/funcionalidades/funcionalidades-bom.md`, com as categorias Passos e Step map desta skill.
> Validação dos passos: pendente do @analista.
> Step map: pendente do @analista.

## Lista de Funcionalidades com Problemas, Benefícios, Passos e Step map

Onde `produto.md` ainda marca consulta do leitor ou o teto de empréstimos como `[CONFIRMAR]`, valem `personas-usuario.md`, `glossario.md` e `regras-de-negocio.md`: o leitor consulta sem login, e o teto é 3 empréstimos ao mesmo tempo.

### Acesso

O leitor não autentica. Quem altera acervo, empréstimo, usuário e prazo é o gestor.

#### Gestor

##### **F001** — Autenticar acesso do gestor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Autenticar acesso do gestor |
| **Descrição** | O gestor informa usuário e senha. Se conferem, o acesso à gestão é permitido. Se não conferem, o acesso é recusado. `[RN-02]` |
| **Problema que Resolve** | O acervo e os empréstimos são controlados na mão, sem restringir quem altera o registro. |
| **Benefícios que Traz** | Só o gestor autenticado altera acervo, empréstimo, usuário e prazo. |
| **Passos** | 1. Informar o usuário e a senha<br>2. Se o usuário e a senha não conferem:<br>2a. Recusar o acesso e encerre<br>Senão:<br>2b. Permitir o acesso do gestor |
| **Step map** | **HU-01** — Autenticar acesso do gestor. — Passos 1, 2a e 2b: o gestor informa usuário e senha; o acesso é permitido ou recusado. |

##### **F002** — Cadastrar usuário do gestor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar usuário do gestor |
| **Descrição** | O gestor autenticado cadastra um usuário, a credencial de usuário e senha de quem administra. Usuário não é o leitor. |
| **Problema que Resolve** | Sem credencial registrada, a gestão do acervo e dos empréstimos continua na mão. |
| **Benefícios que Traz** | Passa a existir usuário para o gestor entrar e operar o registro único. |
| **Passos** | 1. Informar o usuário e a senha<br>2. Cadastrar o usuário |
| **Step map** | **HU-02** — Cadastrar usuário do gestor. — Passos 1 e 2: o gestor autenticado cria a credencial de acesso. O primeiro usuário, quando ainda não existe gestor autenticado, está [CONFIRMAR]. |

### Acervo

#### Gestor

##### **F003** — Cadastrar livro do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar livro do acervo |
| **Descrição** | O gestor registra o livro com título, autor, editora, ISBN, ano, gênero, categoria e assunto. Livro é o registro do título, não o exemplar. |
| **Problema que Resolve** | As fichas catalográficas em papel não têm padrão e são difíceis de guardar. |
| **Benefícios que Traz** | O livro fica num registro único, com a classificação no lugar da ficha de papel. |
| **Passos** | 1. Informar título, autor, editora, ISBN e ano do livro<br>2. Informar gênero, categoria e assunto do livro<br>3. Cadastrar o livro no acervo |
| **Step map** | **HU-03** — Cadastrar livro do acervo. — Passos 1, 2 e 3: o gestor registra o livro com título, autor, editora, ISBN, ano, gênero, categoria e assunto. |

##### **F004** — Cadastrar exemplar do livro

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar exemplar do livro |
| **Descrição** | O gestor atribui um código único a cada exemplar do livro. Dois exemplares não compartilham o mesmo código. `[RN-09]` A situação do exemplar no cadastro está [CONFIRMAR]. |
| **Problema que Resolve** | Sem código, a retirada e a contagem do exemplar dependem da ficha e da busca manual. |
| **Benefícios que Traz** | Cada exemplar fica identificado por um código único para o controle da retirada. |
| **Passos** | 1. Selecionar o livro do acervo<br>2. Atribuir o código do exemplar<br>3. Se o código já pertence a outro exemplar:<br>3a. Recusar o código e volte ao passo 2<br>Senão:<br>3b. Cadastrar o exemplar do livro<br>4. (opcional) Se houver outro exemplar do mesmo livro para cadastrar, volte ao passo 2 |
| **Step map** | **HU-04** — Cadastrar exemplar do livro. — Passos 1, 2, 3a, 3b e 4: o gestor atribui código único ao exemplar do livro; código repetido é recusado. A situação inicial do exemplar está [CONFIRMAR]. |

##### **F005** — Localizar livro do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Localizar livro do acervo |
| **Descrição** | O gestor pesquisa o livro por título, autor, categoria ou código do exemplar e vê a situação de cada exemplar: disponível, emprestado ou indisponível. |
| **Problema que Resolve** | Achar o livro e a situação do exemplar exige procurar nas fichas, na mão. |
| **Benefícios que Traz** | O gestor encontra o livro e a situação do exemplar no registro único. |
| **Passos** | 1. Informar título, autor, categoria ou código do exemplar<br>2. Ver o livro localizado e a situação de cada exemplar |
| **Step map** | **HU-05** — Localizar livro do acervo. — Passos 1 e 2: o gestor pesquisa por título, autor, categoria ou código e vê a situação de cada exemplar. |

##### **F006** — Corrigir dados do livro

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Corrigir dados do livro |
| **Descrição** | O gestor corrige título, autor, editora, ISBN, ano, gênero, categoria ou assunto de um livro já cadastrado. |
| **Problema que Resolve** | Corrigir a ficha de papel rasura o registro e não garante uma versão só. |
| **Benefícios que Traz** | A correção passa a valer no registro único do livro. |
| **Passos** | 1. Localizar o livro do acervo<br>2. Corrigir os dados do livro |
| **Step map** | **HU-06** — Corrigir dados do livro. — Passo 2: o gestor corrige título, autor, editora, ISBN, ano, gênero, categoria ou assunto. A localização é HU-05. |

##### **F007** — Excluir livro do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Excluir livro do acervo |
| **Descrição** | O gestor exclui o livro do acervo. |
| **Problema que Resolve** | A saída de um livro continua anotada à mão e a ficha antiga segue no maço. |
| **Benefícios que Traz** | O livro deixa de constar do registro único do acervo. |
| **Passos** | 1. Localizar o livro do acervo<br>2. Excluir o livro do acervo |
| **Step map** | **HU-07** — Excluir livro do acervo. — Passo 2: o gestor exclui o livro. A localização é HU-05. O efeito sobre exemplar emprestado está [CONFIRMAR]. |

#### Leitor

##### **F008** — Consultar disponibilidade do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Consultar disponibilidade do exemplar |
| **Descrição** | O leitor consulta a disponibilidade sem login. Pesquisa por título, autor, categoria ou código do exemplar. Se o exemplar está emprestado, vê a data prevista de devolução. `[RN-01]` `[RN-04]` |
| **Problema que Resolve** | Não há como pesquisar. O leitor só investiga manualmente quais livros estão disponíveis. |
| **Benefícios que Traz** | O leitor vê a situação do exemplar sem percorrer o acervo na mão e, se está emprestado, vê a data prevista de devolução. |
| **Passos** | 1. Informar título, autor, categoria ou código do exemplar, sem login<br>2. Ver a situação de cada exemplar do livro<br>3. Se o exemplar está emprestado:<br>3a. Ver a data prevista de devolução e encerre<br>Senão, se o exemplar está disponível:<br>3b. Ver o exemplar disponível e encerre<br>Senão:<br>3c. [CONFIRMAR] o que a consulta mostra para o exemplar indisponível sem empréstimo, e encerre |
| **Step map** | **HU-08** — Consultar disponibilidade do exemplar. — Passos 1, 2, 3a, 3b e 3c: o leitor, sem login, pesquisa e vê a situação do exemplar; no emprestado, vê a data prevista de devolução. Qual data mostrar quando há mais de um exemplar fora, e o que mostrar no indisponível sem empréstimo, estão [CONFIRMAR]. |

### Leitores

#### Gestor

##### **F009** — Cadastrar leitor da biblioteca

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar leitor da biblioteca |
| **Descrição** | O gestor cadastra o leitor com nome completo, telefone, endereço e CPF. O histórico de empréstimo desse leitor fica no registro individual, alimentado pelos empréstimos. |
| **Problema que Resolve** | Na agenda de papel, a pessoa que leva o exemplar não fica num cadastro único. |
| **Benefícios que Traz** | O leitor fica identificado para o empréstimo e para o histórico. |
| **Passos** | 1. Informar nome completo, telefone, endereço e CPF do leitor<br>2. Cadastrar o leitor |
| **Step map** | **HU-09** — Cadastrar leitor da biblioteca. — Passos 1 e 2: o gestor registra nome completo, telefone, endereço e CPF do leitor. |

### Empréstimos

A ordem segue as transições do exemplar e do empréstimo: disponível para emprestado, ativo para atrasado, e ativo ou atrasado para devolvido.

#### Gestor

##### **F010** — Configurar prazo de devolução do empréstimo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Configurar prazo de devolução do empréstimo |
| **Descrição** | O gestor configura o prazo usado para calcular a data prevista de devolução. Não há quantidade fixa de dias. `[RN-06]` |
| **Problema que Resolve** | O prazo combinado na agenda de papel não fica num lugar só. |
| **Benefícios que Traz** | A data prevista dos empréstimos seguintes sai do prazo configurado pelo gestor. |
| **Passos** | 1. Informar o prazo de devolução<br>2. Guardar a configuração do prazo |
| **Step map** | **HU-10** — Configurar prazo de devolução do empréstimo. — Passos 1 e 2: o gestor define o prazo, sem quantidade fixa de dias. O cálculo da data prevista no empréstimo é HU-11. |

##### **F011** — Registrar empréstimo do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar empréstimo do exemplar |
| **Descrição** | O gestor registra a retirada de um exemplar por um leitor. O sistema grava a data de retirada, calcula a data prevista pelo prazo configurado, marca o exemplar como emprestado e o empréstimo como ativo. Se o exemplar não está disponível, a retirada não se conclui e a data prevista de devolução é informada. Se o leitor já tem 3 empréstimos ao mesmo tempo, a retirada não se conclui. Empréstimo já devolvido não entra nessa conta. Não há exceção. `[RN-03]` `[RN-04]` `[RN-05]` `[RN-06]` |
| **Problema que Resolve** | Os empréstimos são controlados na mão, em agenda de papel. |
| **Benefícios que Traz** | A retirada fica registrada com leitor, exemplar, data de retirada e data prevista, e o exemplar deixa de constar como disponível. |
| **Passos** | 1. Selecionar o leitor<br>2. Selecionar o exemplar<br>3. Se o exemplar não está disponível:<br>3a. Ver a recusa do empréstimo e a data prevista de devolução, e encerre<br>Senão:<br>3b. Seguir para o passo 4<br>4. Se o leitor já tem 3 empréstimos ao mesmo tempo:<br>4a. Ver a recusa do empréstimo e encerre<br>Senão:<br>4b. Registrar o empréstimo do exemplar |
| **Step map** | **HU-11** — Registrar empréstimo do exemplar. — Passos 1, 2, 3a, 3b, 4a e 4b: o gestor liga leitor e exemplar. Exemplar que não está disponível é recusado, com a data prevista de devolução. Leitor que já tem 3 empréstimos ao mesmo tempo é recusado. Nos demais casos, o sistema grava a data de retirada, calcula a data prevista pelo prazo de HU-10, marca o exemplar como emprestado e o empréstimo como ativo. Qual data mostrar quando há mais de um exemplar fora está [CONFIRMAR], como em HU-08. |

#### O sistema

##### **F012** — Identificar atraso do empréstimo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Identificar atraso do empréstimo |
| **Descrição** | O sistema marca o empréstimo como atrasado quando a data prevista de devolução passa e não houve devolução. O empréstimo atrasado não volta a ativo. `[RN-08]` |
| **Problema que Resolve** | No controle de papel, o atraso só aparece se alguém confere a agenda à mão. |
| **Benefícios que Traz** | O empréstimo atrasado fica identificado pela data prevista, sem essa conferência. |
| **Passos** | 1. Reconhecer o empréstimo ativo com a data prevista vencida e sem devolução<br>2. Marcar o empréstimo como atrasado |
| **Step map** | **HU-12** — Identificar atraso do empréstimo. — Passos 1 e 2: o sistema marca o empréstimo como atrasado quando a data prevista passa sem devolução. Não há volta para ativo. |

#### Gestor

##### **F013** — Configurar suspensão do leitor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Configurar suspensão do leitor |
| **Descrição** | O gestor liga ou desliga a configuração em que o sistema suspende o leitor que não cumpriu o prazo. A duração da suspensão e o que ela impede estão [CONFIRMAR]. `[RN-08]` |
| **Problema que Resolve** | O descumprimento do prazo, na agenda de papel, não tem consequência registrada. |
| **Benefícios que Traz** | A biblioteca decide, na configuração, se o atraso suspende o leitor. |
| **Passos** | 1. Se o atraso for suspender o leitor:<br>1a. Ligar a suspensão do leitor<br>Senão:<br>1b. Desligar a suspensão do leitor<br>2. Guardar a configuração da suspensão |
| **Step map** | **HU-13** — Configurar suspensão do leitor. — Passos 1a, 1b e 2: o gestor liga ou desliga a suspensão por atraso. Duração e bloqueio estão [CONFIRMAR] e não são decididos neste item. A aplicação é HU-14. |

#### O sistema

##### **F014** — Aplicar suspensão do leitor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Aplicar suspensão do leitor |
| **Descrição** | O sistema suspende o leitor que não devolveu o exemplar até a data prevista, somente se a configuração estiver ligada. Se estiver desligada, não suspende. Duração e o que o leitor suspenso fica impedido de fazer estão [CONFIRMAR]. `[RN-08]` |
| **Problema que Resolve** | Mesmo com o atraso anotado no papel, ninguém registra que o leitor deixou de cumprir o prazo. |
| **Benefícios que Traz** | Com a configuração ligada, o leitor que falhou o prazo fica suspenso. |
| **Passos** | 1. Se a suspensão está ligada e o empréstimo está atrasado:<br>1a. Suspender o leitor e encerre<br>Senão:<br>1b. Manter o leitor sem suspensão por este atraso e encerre |
| **Step map** | **HU-14** — Aplicar suspensão do leitor. — Passos 1a e 1b: o sistema suspende o leitor só quando HU-13 está ligada e o empréstimo está atrasado em HU-12. Duração e o que a suspensão impede estão [CONFIRMAR]. |

#### Gestor

##### **F015** — Registrar devolução do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar devolução do exemplar |
| **Descrição** | O gestor registra a devolução de empréstimo ativo ou atrasado. O empréstimo passa a devolvido e o exemplar volta a disponível. `[RN-07]` |
| **Problema que Resolve** | A devolução anotada na agenda não devolve o exemplar a uma lista única de disponíveis. |
| **Benefícios que Traz** | O exemplar volta a disponível no mesmo registro em que a retirada foi feita. |
| **Passos** | 1. Localizar o empréstimo do exemplar<br>2. Se o empréstimo está ativo:<br>2a. Registrar a devolução do exemplar e encerre<br>Senão, se o empréstimo está atrasado:<br>2b. Registrar a devolução do exemplar e encerre |
| **Step map** | **HU-15** — Registrar devolução do exemplar. — Passos 1, 2a e 2b: o gestor registra a devolução de empréstimo ativo ou atrasado; o empréstimo fica devolvido e o exemplar fica disponível. Os dois ramos têm o mesmo resultado. A consulta da lista é HU-16. |

##### **F016** — Consultar situação de empréstimo do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Consultar situação de empréstimo do exemplar |
| **Descrição** | O gestor consulta empréstimos ativos, devolvidos e atrasados. A mesma consulta mostra o histórico de movimentação do exemplar e o histórico de empréstimo do leitor. |
| **Problema que Resolve** | O histórico em agenda e ficha se perde e não segue um padrão. |
| **Benefícios que Traz** | A movimentação do exemplar e os empréstimos do leitor ficam consultáveis no registro. |
| **Passos** | 1. Informar o exemplar ou o leitor<br>2. Ver os empréstimos ativos, devolvidos e atrasados |
| **Step map** | **HU-16** — Consultar situação de empréstimo do exemplar. — Passos 1 e 2: o gestor vê empréstimo ativo, devolvido e atrasado pelo exemplar ou pelo leitor, com o histórico dos dois. |

### Painel

#### Gestor

##### **F017** — Apresentar quantidades do acervo e do empréstimo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Apresentar quantidades do acervo e do empréstimo |
| **Descrição** | O gestor vê a quantidade de livros cadastrados, de leitores ativos, de empréstimos ativos, de devoluções pendentes e de empréstimos atrasados. O sentido de "leitor ativo" e de "devolução pendente" está [CONFIRMAR]: esses nomes não estão no glossário. |
| **Problema que Resolve** | As listas de papel não mostram, de uma vez, livros, leitores e empréstimos. |
| **Benefícios que Traz** | Essas quantidades ficam visíveis num único resumo, sem folhear as listas. |
| **Passos** | 1. Ver a quantidade de livros cadastrados<br>2. Ver a quantidade de leitores ativos<br>3. Ver a quantidade de empréstimos ativos<br>4. Ver a quantidade de devoluções pendentes<br>5. Ver a quantidade de empréstimos atrasados |
| **Step map** | **HU-17** — Apresentar quantidades do acervo e do empréstimo. — Passos 1 a 5: o gestor vê essas quantidades no mesmo resumo. "Leitor ativo" e "devolução pendente" estão [CONFIRMAR]. "Em andamento", nome de `produto.md`, corresponde aqui ao empréstimo ativo. |

### Relatórios

#### Gestor

##### **F018** — Emitir relatório do acervo e da movimentação

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Emitir relatório do acervo e da movimentação |
| **Descrição** | O gestor emite relatório simples do acervo e da movimentação dos livros. |
| **Problema que Resolve** | Acervo e movimentação só existem nas fichas, sem um relato reunido. |
| **Benefícios que Traz** | O gestor obtém um relatório do acervo e da movimentação a partir do registro. |
| **Passos** | 1. Solicitar o relatório do acervo e da movimentação<br>2. Ver o relatório emitido |
| **Step map** | **HU-18** — Emitir relatório do acervo e da movimentação. — Passos 1 e 2: o gestor emite o relatório simples do acervo e da movimentação. O recorte do relatório está [CONFIRMAR]. |

### Limites e Não-Escopo

- ❌ **Loja de livros:** o produto não vende livro nem exemplar. Origem: `produto.md`.
- ❌ **Automação com IA:** nenhuma funcionalidade decide empréstimo, classificação ou suspensão por conta própria. Origem: `produto.md`.
- ❌ **Compartilhamento externo:** os dados dos cadastrados não são compartilhados com outras ferramentas da internet. Origem: `produto.md`.
- ❌ **Operação sem pessoa:** o sistema não dispensa o gestor na gestão do acervo e dos empréstimos. Origem: `produto.md`.
- ❌ **Prazo fixo:** não há quantidade fechada de dias. O prazo é configuração do gestor. Origem: `produto.md` e `[RN-06]`.
- ❌ **Venda, reserva e doação:** empréstimo não é nenhuma das três. Origem: `glossario.md`.
- ❌ **Leitor operador:** o leitor não cadastra livro, não registra empréstimo e não configura prazo. Origem: `personas-usuario.md` e `[RN-01]`.
- ❌ **Exceção de retirada:** exemplar que não está disponível não sai, e o quarto empréstimo ao mesmo tempo não se conclui. Origem: `[RN-04]` e `[RN-05]`.

### Pendências

- `[CONFIRMAR]` Quem cria o primeiro usuário, se o cadastro de usuário exige um gestor já autenticado.
- `[CONFIRMAR]` Se o gestor corrige ou exclui usuário, leitor ou exemplar sem excluir o livro.
- `[CONFIRMAR]` A situação do exemplar no momento do cadastro, e quem o marca como indisponível, a partir de qual status.
- `[CONFIRMAR]` O que a consulta e a recusa de empréstimo mostram quando o exemplar está indisponível sem empréstimo, e qual data prevista mostrar quando há mais de um exemplar fora.
- `[CONFIRMAR]` O efeito de excluir um livro que ainda tem exemplar emprestado.
- `[CONFIRMAR]` A duração da suspensão e o que o leitor suspenso fica impedido de fazer, inclusive se pode receber novo empréstimo.
- `[CONFIRMAR]` O sentido de "leitor ativo" e de "devolução pendente" no resumo.
- `[CONFIRMAR]` O recorte do relatório simples do acervo e da movimentação.
- `[CONFIRMAR]` Se o acervo inclui item que não é livro. Enquanto obra não estiver no glossário, esta lista só trata de livro e exemplar.
