# Lista de Funcionalidades do Produto: Biblioteca Limoeiro

> 📋 **Contexto e Origem:**
> Documento elaborado pelo `@analista` com base nos arquivos de `contexto/` e no formato de `exemplos/funcionalidades/funcionalidades-bom.md`, com as categorias Passos e Step map.
> Revisado em 2026-11-11 com o mapa de telas indicado pelo PO, depois da avaliação dos wireflows.
> Validação dos passos: pendente do @analista.
> Step map: pendente do @analista.
>
> Esta lista substitui, para o trabalho daqui em diante, `entregas/funcionalidades/2026-11-05-lista-funcionalidades.md`. O arquivo de 5 de novembro permanece desatualizado.
>
> `contexto/` não foi alterado. Onde a orientação do PO nesta data diverge do contexto, a divergência está na seção seguinte. Os próximos wireflows seguem esta lista.

## Mapa de telas

O wireflow de cada funcionalidade parte da tela comum do grupo. Cadastro e edição do mesmo item usam a mesma estrutura. Funcionalidade sem tela própria não ganha frame isolado.

| Tela | Quem entra | Funcionalidades que partem dela |
| --- | --- | --- |
| Tela de login | Gestor | F001. Segue para a tela inicial, ou mostra senha errada, ou usuário não cadastrado. |
| Tela inicial | Gestor autenticado | Não é uma das 29. Reúne as quatro áreas: acervo, usuários, empréstimos e relatórios. É o destino de F001. |
| Área de gestão do acervo | Gestor | F005, F006, F007, F008, F009, F010, F022, F023, F027. |
| Área de gestão de usuários | Gestor | F002, F003, F012, F013, F014, F015, F026. |
| Área de gestão de empréstimos | Gestor | F016, F017, F018, F019, F020, F021, F024, F025. |
| Área de relatórios | Gestor | F028, F029, a mesma pesquisa de F010, e o recorte de F025 dos leitores com empréstimo ativo. |
| Página pública de consulta | Leitor, sem login | F011. Mesmas características de F010. |

F004, F018 e F021 não têm tela própria. O efeito de cada uma aparece na tela da ação ou da lista, como descrito na funcionalidade.

### Formulários compartilhados

- **Gestor:** F002 e F003 usam a mesma estrutura, com usuário e senha. Partem da área de gestão de usuários.
- **Leitor:** F012 e F013 usam a mesma estrutura. Os campos são nome, CPF, telefone, endereço, máximo de empréstimos em paralelo (F014) e prazo (F015).
- **Obra:** F006 abre a mesma estrutura do cadastro do tipo daquela obra (F005).

### Divergências em relação a `contexto/`

Orientação do PO em 2026-11-11. O contexto continua com o texto anterior.

1. **Prazo no leitor.** F015 é campo do cadastro do leitor. `[RN-06]` descreve o prazo como configuração da biblioteca, não como dado de cada leitor.
2. **Chave da suspensão no empréstimo.** F016 é uma chave ligada ou desligada na tela de registrar o empréstimo. `[RN-08]` e `[RN-14]` descrevem ligar ou desligar como configuração da biblioteca.
3. **Pesquisa pública.** F011 tem as mesmas características de F010. Antes, a pesquisa na página pública estava em `[CONFIRMAR]`.
4. **Mensagem do log.** A ação que gera log mostra, na própria tela, a mensagem `operação feita com sucesso`. `[RN-14]` não descrevia essa mensagem. O conteúdo do log permanece o de `[RN-14]`.

A suspensão, quando a chave do empréstimo está ligada, inicia na devolução do exemplar atrasado. O gestor informa a duração nesse instante (F020). A passagem automática para atrasado (F018) não suspende o leitor. Confirmado pelo PO em 2026-11-11.

## Lista de Funcionalidades com Problemas, Benefícios, Passos e Step map

### Tela de login

#### Gestor

##### **F001** — Autenticar entrada do gestor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Autenticar entrada do gestor |
| **Descrição** | O gestor informa usuário e senha na tela de login. Se a senha está errada, a tela mostra essa mensagem e permanece no login. Se o usuário não está cadastrado, a tela mostra essa mensagem e permanece no login. Se usuário e senha autorizam a entrada, abre a tela inicial, com as quatro áreas: acervo, usuários, empréstimos e relatórios. Usuário é a credencial. A entrada não gera log. |
| **Problema que Resolve** | A consulta do leitor é aberta. Sem a tela de login, a alteração do cadastro ficaria na mesma condição da consulta. |
| **Benefícios que Traz** | O gestor autenticado chega à tela inicial. Senha errada e usuário não cadastrado permanecem na tela de login, cada um com a sua mensagem. |
| **Passos** | 1. Informar o usuário<br>2. Informar a senha<br>3. Se a senha está errada:<br>3a. Ver a mensagem de senha errada e permanecer na tela de login<br>Senão, se o usuário não está cadastrado:<br>3b. Ver a mensagem de usuário não cadastrado e permanecer na tela de login<br>Senão:<br>3c. Abrir a tela inicial |
| **Step map** | **HU-01** — Autenticar entrada do gestor. — Passos 1, 2, 3a, 3b e 3c: a tela de login leva à tela inicial ou mostra uma das duas mensagens. ⚠️ [SUPOSIÇÃO] A senha errada vale quando o usuário existe. A recusa sem gravação não gera log (HU-04). |

### Área de gestão de usuários

Frame de origem: a área de gestão de usuários, aberta pela tela inicial. Cadastro e edição do gestor compartilham a estrutura. Cadastro e edição do leitor compartilham a estrutura, com máximo e prazo no mesmo formulário.

#### Gestor

##### **F002** — Cadastrar usuário e senha do gestor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar usuário e senha do gestor |
| **Descrição** | A partir da área de gestão de usuários, o gestor cadastra outro gestor com usuário e senha. A estrutura é a mesma da edição (F003). O primeiro gestor já existe e não é criado aqui. Ao concluir, a tela mostra `operação feita com sucesso`. A senha não entra no log. |
| **Problema que Resolve** | A meta do ciclo pede pelo menos 5 gestores, e o controle não pode depender de um único acesso criado fora da rotina. |
| **Benefícios que Traz** | Outro gestor passa a entrar com usuário e senha próprios. A conclusão fica visível na mesma tela. |
| **Passos** | 1. Abrir a área de gestão de usuários<br>2. Escolher cadastrar gestor<br>3. Informar o usuário do novo gestor<br>4. Informar a senha do novo gestor<br>5. Concluir o cadastro do gestor<br>6. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-02** — Cadastrar usuário e senha do gestor. — Passos 1 a 6: o formulário é o mesmo de HU-03. O log da inclusão segue HU-04, com valor anterior vazio e sem a senha. A mensagem do passo 6 representa esse log. |

##### **F003** — Editar cadastro do gestor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Editar cadastro do gestor |
| **Descrição** | A partir da área de gestão de usuários, o gestor edita outro gestor na mesma estrutura do cadastro: usuário e senha. Ao concluir, a tela mostra `operação feita com sucesso`. A senha não entra no log. |
| **Problema que Resolve** | O cadastro de quem administra a biblioteca muda, e a agenda em papel não guarda o valor anterior e o valor novo. |
| **Benefícios que Traz** | A edição usa a mesma tela do cadastro e a conclusão fica visível. |
| **Passos** | 1. Abrir a área de gestão de usuários<br>2. Identificar o gestor<br>3. Alterar usuário ou senha na mesma estrutura do cadastro<br>4. Concluir a edição do cadastro<br>5. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-03** — Editar cadastro do gestor. — Passos 1 a 5: a estrutura é a de HU-02. O log segue HU-04, sem a senha. A mensagem do passo 5 representa esse log. |

##### **F012** — Cadastrar leitor da biblioteca

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar leitor da biblioteca |
| **Descrição** | A partir da área de gestão de usuários, o gestor cadastra o leitor no formulário compartilhado com a edição. Campos: nome obrigatório, CPF único e obrigatório, telefone opcional, endereço opcional, máximo de empréstimos em paralelo (F014, nasce em 2) e prazo (F015). O nome pode ser apelido ou nome social e não é conferido com o CPF. Sem nome ou sem CPF, ou com CPF já usado, o cadastro não se conclui. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | O leitor que toma o exemplar emprestado está só na agenda, sem nome e CPF únicos num registro só. |
| **Benefícios que Traz** | Nome, CPF, contato, máximo e prazo ficam no mesmo formulário. A conclusão fica visível na tela. |
| **Passos** | 1. Abrir a área de gestão de usuários<br>2. Escolher cadastrar leitor<br>3. Informar nome, CPF, telefone, endereço, máximo de empréstimos em paralelo e prazo<br>4. Se faltar nome ou CPF, ou o CPF já estiver usado por outro leitor:<br>4a. Recusar o cadastro e permanecer no formulário<br>Senão:<br>4b. Concluir o cadastro do leitor<br>5. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-12** — Cadastrar leitor da biblioteca. — Passos 1 a 5: o formulário é o mesmo de HU-13. O máximo segue HU-14 e o prazo segue HU-15. O log da inclusão segue HU-04, com valor anterior vazio. A mensagem do passo 5 representa esse log. A recusa sem gravação não gera log nem essa mensagem. |

##### **F013** — Editar cadastro do leitor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Editar cadastro do leitor |
| **Descrição** | A edição abre o mesmo formulário do cadastro: nome, CPF, telefone, endereço, máximo de empréstimos em paralelo e prazo. Nome continua obrigatório. CPF continua único. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | Nome, telefone, endereço, máximo ou prazo mudam e a ficha em papel fica com o dado antigo. |
| **Benefícios que Traz** | A edição usa a mesma tela do cadastro, inclusive máximo e prazo. |
| **Passos** | 1. Abrir a área de gestão de usuários<br>2. Identificar o leitor<br>3. Alterar os campos do mesmo formulário do cadastro<br>4. Se faltar nome ou CPF, ou o CPF ficar usado por outro leitor:<br>4a. Recusar a edição e permanecer no formulário<br>Senão:<br>4b. Concluir a edição do cadastro<br>5. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-13** — Editar cadastro do leitor. — Passos 1 a 5: a estrutura é a de HU-12. O máximo segue HU-14 e o prazo segue HU-15. O log segue HU-04. A mensagem do passo 5 representa esse log. |

##### **F014** — Definir máximo de empréstimos em paralelo do leitor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Definir máximo de empréstimos em paralelo do leitor |
| **Descrição** | O máximo é um campo do formulário do leitor (F012 e F013), não uma tela própria. O padrão é 2. O gestor pode aumentar. Valor abaixo de 2 é recusado e não é gravado. Empréstimo devolvido e Encerrado por extravio não entram na conta. Empréstimo ativo ou atrasado entra. Se o gestor reduz o máximo, sem ficar abaixo de 2, e o leitor já tem mais empréstimos em paralelo do que o novo valor, o sistema indica que a mudança só tem efeito depois da devolução de ao menos um exemplar, ou do encerramento de um deles por extravio. Até lá, vale o máximo anterior. A gravação do campo mostra `operação feita com sucesso`. |
| **Problema que Resolve** | A agenda não separa, por leitor, quantos exemplares ainda estão fora. |
| **Benefícios que Traz** | O máximo fica no formulário do leitor, nunca abaixo de 2. A redução que esbarra nos empréstimos em aberto não vale antes da devolução ou do encerramento por extravio. |
| **Passos** | 1. Abrir o formulário do leitor, no cadastro ou na edição<br>2. Informar o máximo de empréstimos em paralelo<br>3. Se o valor é menor que 2:<br>3a. Recusar a mudança e permanecer no formulário<br>Senão, se o leitor já tem mais empréstimos em paralelo do que o novo valor:<br>3b. Manter o máximo anterior e indicar que a mudança só vale depois da devolução ou do encerramento por extravio de ao menos um<br>Senão:<br>3c. Gravar o novo máximo<br>4. Ver a mensagem operação feita com sucesso, quando a mudança é gravada ou fica aguardando |
| **Step map** | **HU-14** — Definir máximo de empréstimos em paralelo do leitor. — Passos 1, 2, 3a, 3b, 3c e 4: o campo está no formulário de HU-12 e HU-13. O log segue HU-04 e guarda o valor anterior, o valor pedido e se passou a valer ou ficou aguardando. A recusa abaixo de 2 não gera log nem a mensagem. |

##### **F015** — Configurar prazo do empréstimo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Configurar prazo do empréstimo |
| **Descrição** | O prazo é um campo do formulário do leitor (F012 e F013), junto de nome, CPF, telefone e endereço. Não é uma tela de configuração da biblioteca. A data prevista de devolução de um empréstimo novo desse leitor é calculada por esse prazo. Não há quantidade fixa de dias. [CONFIRMAR] A unidade do campo e se a mudança recalcula empréstimo ativo ou atrasado. Esta descrição diverge de `[RN-06]`, que trata o prazo como configuração da biblioteca. Ao gravar, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | O prazo da devolução precisa acompanhar o leitor, no mesmo cadastro dos outros dados. |
| **Benefícios que Traz** | Cada leitor tem o próprio prazo no formulário, e a data prevista do empréstimo novo sai desse campo. |
| **Passos** | 1. Abrir o formulário do leitor, no cadastro ou na edição<br>2. Informar o prazo daquele leitor<br>3. Gravar o formulário<br>4. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-15** — Configurar prazo do empréstimo. — Passos 1 a 4: o prazo é campo de HU-12 e HU-13, não uma configuração geral. A data prevista de HU-17 usa o prazo desse leitor. [CONFIRMAR] A unidade e o recálculo de empréstimo já aberto. O log segue HU-04. A mensagem do passo 4 representa esse log. |

##### **F026** — Consultar histórico de empréstimos do leitor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Consultar histórico de empréstimos do leitor |
| **Descrição** | Na área de gestão de usuários, o gestor consulta o histórico de empréstimos do leitor. A devolução não apaga esse histórico. A consulta não gera log e não mostra a mensagem de sucesso. |
| **Problema que Resolve** | Os empréstimos já riscados na agenda do leitor somem ou se misturam com o que ainda está fora. |
| **Benefícios que Traz** | O histórico fica na área do leitor, inclusive depois da devolução. |
| **Passos** | 1. Abrir a área de gestão de usuários<br>2. Identificar o leitor<br>3. Ver o histórico de empréstimos do leitor |
| **Step map** | **HU-26** — Consultar histórico de empréstimos do leitor. — Passos 1 a 3: a consulta parte da área de usuários e não gera log. [CONFIRMAR] Quais dados cada empréstimo do histórico mostra. A lista por status é HU-25. |

### Área de gestão do acervo

Frame de origem: a área de gestão do acervo, aberta pela tela inicial. A opção de adicionar obra está nessa área. A escolha do tipo abre a tela seguinte. Cadastro e edição da obra compartilham a estrutura do tipo. Sem escolha de tipo, o gestor volta a esta área. Não há quadro de recusa nessa volta.

#### Gestor

##### **F005** — Cadastrar obra do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar obra do acervo |
| **Descrição** | Na área de gestão do acervo, o gestor escolhe adicionar obra e, na tela seguinte, escolhe o tipo: livro, revista, HQ, brinquedo ou outro. Os dados são os do tipo. Livro: título, autor, editora, ISBN, ano, gênero, categoria, assunto e quantidade de exemplares. HQ: título, autor, ano de publicação, número da edição, editora e quantidade de exemplares. Revista: título, ano de publicação, número da edição, editora e quantidade de exemplares. Brinquedo: nome, descrição, fabricante, faixa etária indicada e quantidade de exemplares. Outro: nome, descrição e quantidade de exemplares. Outro não pede nome livre além de nome e descrição. Sem tipo, o gestor volta à área de acervo e o cadastro não se conclui. A obra guarda a data e a hora da inclusão e o gestor responsável. Esta funcionalidade não cria o exemplar com código. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | As fichas catalográficas em papel não padronizam o registro do item. Revista, HQ, brinquedo e outro não cabem num registro só de livro. |
| **Benefícios que Traz** | A obra entra a partir da área de acervo, com o tipo e os dados desse tipo. A conclusão fica visível na tela. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Escolher adicionar obra<br>3. Se o gestor volta sem escolher o tipo:<br>3a. Voltar à área de gestão do acervo e encerre<br>Senão, se o tipo é livro:<br>3b. Informar título, autor, editora, ISBN, ano, gênero, categoria, assunto e quantidade de exemplares<br>Senão, se o tipo é HQ:<br>3c. Informar título, autor, ano de publicação, número da edição, editora e quantidade de exemplares<br>Senão, se o tipo é revista:<br>3d. Informar título, ano de publicação, número da edição, editora e quantidade de exemplares<br>Senão, se o tipo é brinquedo:<br>3e. Informar nome, descrição, fabricante, faixa etária indicada e quantidade de exemplares<br>Senão:<br>3f. Informar nome, descrição e quantidade de exemplares<br>4. Concluir o cadastro da obra<br>5. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-05** — Cadastrar obra do acervo. — Passos 1 a 5: a área de acervo oferece adicionar obra. A tela seguinte é a escolha do tipo e os dados desse tipo. Voltar sem tipo não é um quadro de recusa. A obra guarda data, hora e gestor responsável. O exemplar com código é HU-08. O log da inclusão segue HU-04. A mensagem do passo 5 representa esse log. |

##### **F006** — Editar dados da obra

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Editar dados da obra |
| **Descrição** | A edição abre a mesma estrutura do cadastro do tipo daquela obra. [CONFIRMAR] O contexto não diz se a edição troca o tipo. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | A ficha em papel da obra fica desatualizada quando um dado do tipo muda. |
| **Benefícios que Traz** | A edição repete a tela do cadastro daquele tipo, e a conclusão fica visível. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Identificar a obra<br>3. Abrir a mesma estrutura do cadastro do tipo dessa obra<br>4. Alterar os dados do tipo<br>5. Concluir a edição da obra<br>6. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-06** — Editar dados da obra. — Passos 1 a 6: a estrutura é a do tipo em HU-05. [CONFIRMAR] Se o tipo pode ser trocado. O log segue HU-04. A mensagem do passo 6 representa esse log. |

##### **F007** — Remover obra do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Remover obra do acervo |
| **Descrição** | Na área de gestão do acervo, o gestor remove a obra. A remoção não se conclui enquanto houver exemplar emprestado. Depois do empréstimo Encerrado por extravio, a remoção pode ser feita. A obra guarda a data da remoção e o gestor responsável pela remoção. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | A ficha em papel continua no maço depois que o item sai do acervo, ou some sem data e sem quem removeu. |
| **Benefícios que Traz** | A remoção parte da área de acervo. Obra com exemplar emprestado permanece até o encerramento por extravio. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Identificar a obra<br>3. Se a obra tem exemplar emprestado:<br>3a. Recusar a remoção e permanecer na área<br>Senão:<br>3b. Remover a obra<br>4. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-07** — Remover obra do acervo. — Passos 1, 2, 3a, 3b e 4: a remoção parte da área de acervo. Com exemplar emprestado, não se conclui. Depois de HU-24, pode ser feita. O log segue HU-04, com valor novo igual à remoção. A mensagem do passo 4 representa esse log. A recusa não gera log nem a mensagem. |

##### **F008** — Cadastrar exemplar da obra

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Cadastrar exemplar da obra |
| **Descrição** | Na área de gestão do acervo, o gestor cadastra o exemplar de uma obra. O exemplar nasce disponível. O sistema atribui e guarda um código único, sem derivar de ISBN nem de outro dado externo. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | A ficha da obra não distingue a unidade física. Sem código único, duas unidades da mesma obra se confundem na retirada. |
| **Benefícios que Traz** | O exemplar nasce disponível, com código único, a partir da área de acervo. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Identificar a obra<br>3. Cadastrar o exemplar dessa obra<br>4. Ver o exemplar disponível e o código do exemplar<br>5. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-08** — Cadastrar exemplar da obra. — Passos 1 a 5: o exemplar nasce disponível e recebe código único, sem derivar de ISBN. O log da inclusão segue HU-04. A mensagem do passo 5 representa esse log. |

##### **F009** — Remover exemplar da obra

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Remover exemplar da obra |
| **Descrição** | Na área de gestão do acervo, o gestor remove o exemplar. A remoção do exemplar emprestado não se conclui. Depois do encerramento por extravio, a remoção pode ser feita. [CONFIRMAR] Se essa remoção gera log. Se gerar, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | A unidade física sai do acervo e a ficha continua tratada como exemplar que ainda pode ser emprestado. |
| **Benefícios que Traz** | O exemplar que não está emprestado pode ser removido a partir da área de acervo. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Identificar o exemplar<br>3. Se o exemplar está emprestado:<br>3a. Recusar a remoção e permanecer na área<br>Senão:<br>3b. Remover o exemplar<br>4. [CONFIRMAR] Se a remoção gera log, ver a mensagem operação feita com sucesso |
| **Step map** | **HU-09** — Remover exemplar da obra. — Passos 1, 2, 3a, 3b e 4: a remoção parte da área de acervo. Exemplar emprestado não é removido. Depois de HU-24, a remoção pode ser feita. [CONFIRMAR] Se gera log. A recusa não gera a mensagem de sucesso. |

##### **F010** — Pesquisar situação do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Pesquisar situação do acervo |
| **Descrição** | A pesquisa do gestor tem as mesmas características da página pública (F011): dado do tipo, código do exemplar, e a situação disponível, emprestado ou indisponível. No emprestado, a data prevista é a mais próxima. No indisponível sem empréstimo, a mensagem é que o exemplar não está disponível para empréstimo, sem data. O gestor abre essa pesquisa pela área de gestão do acervo e também pela área de relatórios. A pesquisa não gera log e não mostra a mensagem de sucesso. |
| **Problema que Resolve** | Para saber a situação de um item, o gestor percorre ficha e agenda. |
| **Benefícios que Traz** | A mesma pesquisa abre no acervo e nos relatórios. O resultado é o mesmo da página pública. |
| **Passos** | 1. Se a pesquisa parte do acervo:<br>1a. Abrir a área de gestão do acervo e abrir a pesquisa<br>Senão:<br>1b. Abrir a área de relatórios e abrir a pesquisa<br>2. Informar um dado do tipo ou o código do exemplar<br>3. Se a obra tem exemplar emprestado:<br>3a. Ver a data prevista mais próxima<br>Senão, se o exemplar está indisponível e não há empréstimo:<br>3b. Ver a mensagem de que o exemplar não está disponível para empréstimo, sem data<br>Senão:<br>3c. Ver o exemplar disponível |
| **Step map** | **HU-10** — Pesquisar situação do acervo. — Passos 1a, 1b, 2, 3a, 3b e 3c: as duas entradas mostram a mesma pesquisa de HU-11. Não gera log. [CONFIRMAR] O que mostrar quando há, ao mesmo tempo, exemplar emprestado e exemplar indisponível sem empréstimo. |

##### **F022** — Registrar indisponibilidade do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar indisponibilidade do exemplar |
| **Descrição** | Na área de gestão do acervo, o gestor leva o exemplar de disponível a indisponível. Exemplar que não está disponível não entra nesta passagem. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | Exemplar que não pode sair continua na ficha como disponível para retirada. |
| **Benefícios que Traz** | A indisponibilidade é feita na área de acervo, e a conclusão fica visível. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Identificar o exemplar disponível<br>3. Se o exemplar não está disponível:<br>3a. Recusar a indisponibilidade e permanecer na área<br>Senão:<br>3b. Registrar a indisponibilidade do exemplar<br>4. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-22** — Registrar indisponibilidade do exemplar. — Passos 1, 2, 3a, 3b e 4: só a partir de disponível, na área de acervo. O empréstimo não se conclui (HU-17). O log segue HU-04. A mensagem do passo 4 representa esse log. A recusa não gera a mensagem. |

##### **F023** — Registrar retorno a disponibilidade do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar retorno a disponibilidade do exemplar |
| **Descrição** | Na área de gestão do acervo, o gestor registra o retorno a disponibilidade do exemplar indisponível. A devolução de exemplar emprestado não é este retorno: é F019. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | O exemplar que voltou a poder sair continua marcado como indisponível. |
| **Benefícios que Traz** | O retorno a disponibilidade é feito na área de acervo. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Identificar o exemplar indisponível<br>3. Se o exemplar não está indisponível:<br>3a. Recusar o retorno e permanecer na área<br>Senão:<br>3b. Registrar o retorno a disponibilidade<br>4. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-23** — Registrar retorno a disponibilidade do exemplar. — Passos 1, 2, 3a, 3b e 4: a volta do indisponível a disponível parte da área de acervo. A devolução é HU-19. O log segue HU-04. A mensagem do passo 4 representa esse log. |

##### **F027** — Consultar movimentação do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Consultar movimentação do exemplar |
| **Descrição** | Na área de gestão do acervo, o gestor consulta o histórico de movimentação do exemplar. A devolução não apaga esse histórico. A consulta não gera log e não mostra a mensagem de sucesso. |
| **Problema que Resolve** | A ida e a volta de uma unidade física ficam espalhadas na agenda. |
| **Benefícios que Traz** | A movimentação fica na área de acervo, e a devolução não apaga o histórico. |
| **Passos** | 1. Abrir a área de gestão do acervo<br>2. Identificar o exemplar<br>3. Ver o histórico de movimentação do exemplar |
| **Step map** | **HU-27** — Consultar movimentação do exemplar. — Passos 1 a 3: a consulta parte da área de acervo e não gera log. [CONFIRMAR] Quais dados a movimentação mostra. |

### Página pública de consulta

#### Leitor

##### **F011** — Consultar disponibilidade do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Consultar disponibilidade do acervo |
| **Descrição** | O leitor consulta o acervo em página pública, sem login e sem cadastro preliminar. A página tem as mesmas características da pesquisa do gestor (F010): dado do tipo, código do exemplar, e a situação disponível, emprestado ou indisponível. No emprestado, a data prevista é a mais próxima. No indisponível sem empréstimo, a mensagem é que o exemplar não está disponível para empréstimo, sem data. Cadastro, empréstimo e configuração ficam fora desta página. A consulta não gera log. |
| **Problema que Resolve** | Não há como pesquisar. O leitor só investiga manualmente quais itens do acervo estão disponíveis. |
| **Benefícios que Traz** | O leitor vê, sem login, a mesma pesquisa que o gestor abre no acervo e nos relatórios. |
| **Passos** | 1. Abrir a página pública de consulta<br>2. Informar um dado do tipo ou o código do exemplar<br>3. Se a obra tem exemplar emprestado:<br>3a. Ver a data prevista mais próxima<br>Senão, se o exemplar está indisponível e não há empréstimo:<br>3b. Ver a mensagem de que o exemplar não está disponível para empréstimo, sem data<br>Senão:<br>3c. Ver o exemplar disponível |
| **Step map** | **HU-11** — Consultar disponibilidade do acervo. — Passos 1, 2, 3a, 3b e 3c: a página pública repete a pesquisa de HU-10, sem usuário e sem senha. Não gera log. |

### Área de gestão de empréstimos

Frame de origem: a área de gestão de empréstimos, aberta pela tela inicial. A lista de empréstimos é a base. Registrar a retirada inclui a chave de suspensão e a diferença entre leitor suspenso e leitor cuja suspensão já encerrou. F018 e F021 não têm tela própria.

#### Gestor

##### **F025** — Consultar lista dos empréstimos

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Consultar lista dos empréstimos |
| **Descrição** | Na área de gestão de empréstimos, o gestor vê os empréstimos ativos, devolvidos, atrasados e encerrados por extravio. Quando o sistema passa um empréstimo de ativo a atrasado (F018), a lista passa a mostrar o status atrasado. Na área de relatórios, a mesma lista abre no recorte dos leitores com empréstimo ativo. A consulta não gera log e não mostra a mensagem de sucesso. |
| **Problema que Resolve** | Para saber o que está fora, o que voltou, o que atrasou e o que foi encerrado por extravio, o gestor percorre a agenda. |
| **Benefícios que Traz** | A lista de empréstimos mostra a mudança de status. Os relatórios usam o recorte dos leitores com empréstimo ativo. |
| **Passos** | 1. Se a consulta parte da área de gestão de empréstimos:<br>1a. Ver os empréstimos ativos, devolvidos, atrasados e encerrados por extravio<br>Senão:<br>1b. Abrir a área de relatórios e ver o recorte dos leitores com empréstimo ativo<br>2. Se o sistema passou um empréstimo de ativo a atrasado:<br>2a. Ver esse empréstimo como atrasado na lista |
| **Step map** | **HU-25** — Consultar lista dos empréstimos. — Passos 1a, 1b e 2a: a lista completa fica na área de empréstimos. O recorte de leitores com empréstimo ativo fica na área de relatórios. A mudança de HU-18 aparece nesta lista. A consulta não gera log. |

##### **F017** — Registrar empréstimo do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar empréstimo do exemplar |
| **Descrição** | Na área de gestão de empréstimos, o gestor pesquisa o leitor e identifica o exemplar. A tela mostra se o leitor está suspenso ou se a suspensão já encerrou (F021). Leitor suspenso não recebe empréstimo. Leitor cuja suspensão encerrou se distingue do suspenso, e a tela permite registrar o empréstimo. A mesma tela traz a chave de suspensão daquele empréstimo (F016). Leitor e exemplar são obrigatórios. A data de retirada é a do registro. A data prevista sai do prazo daquele leitor (F015). O exemplar passa a emprestado e o empréstimo nasce ativo. Não se conclui sem leitor e exemplar, nem para exemplar que não está disponível, nem acima do máximo em vigor, nem para o segundo exemplar da mesma obra. O título não identifica a obra. A faixa etária indicada não impede. Empréstimo devolvido e Encerrado por extravio não entram no máximo. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | A retirada é anotada na agenda, sem impedir exemplar que não está disponível, leitor suspenso, máximo em paralelo nem segundo exemplar da mesma obra. |
| **Benefícios que Traz** | A retirada, a chave de suspensão e a condição do leitor ficam na mesma tela da área de empréstimos. |
| **Passos** | 1. Abrir a área de gestão de empréstimos<br>2. Pesquisar o leitor<br>3. Se o leitor está suspenso:<br>3a. Ver o leitor suspenso, recusar o empréstimo e encerre<br>Senão:<br>3b. Ver que a suspensão não está em vigor e seguir<br>4. Identificar o exemplar<br>5. Informar a chave de suspensão daquele empréstimo, ligada ou desligada<br>6. Se o exemplar não está disponível:<br>6a. Se a obra tem exemplar emprestado, recusar o empréstimo e ver a data prevista mais próxima<br>6b. Se o exemplar está indisponível e não há empréstimo, recusar o empréstimo e ver a mensagem sem data<br>Senão, se o empréstimo ultrapassa o máximo em paralelo em vigor:<br>6c. Recusar o empréstimo e encerre<br>Senão, se o leitor já tem empréstimo em paralelo da mesma obra:<br>6d. Recusar o empréstimo e encerre<br>Senão:<br>6e. Registrar o empréstimo<br>7. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-17** — Registrar empréstimo do exemplar. — Passos 1, 2, 3a, 3b, 4, 5, 6a, 6b, 6c, 6d, 6e e 7: a tela distingue leitor suspenso de leitor cuja suspensão encerrou (HU-21) e traz a chave de HU-16. A data prevista usa o prazo do leitor (HU-15). O exemplar fica emprestado e o empréstimo fica ativo. ⚠️ [SUPOSIÇÃO] A ordem das recusas não está no contexto. O log é um só, com os dois resultados, conforme HU-04. A mensagem do passo 7 representa esse log. A recusa não gera a mensagem. |

##### **F016** — Alterar configuração da suspensão

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Alterar configuração da suspensão |
| **Descrição** | A suspensão não tem tela própria de configuração da biblioteca. Na tela de registrar o empréstimo (F017), o gestor liga ou desliga a chave daquele empréstimo. Ligada, a devolução do exemplar atrasado pode suspender o leitor pelo prazo informado nesse instante (F020). Desligada, essa devolução não suspende. A suspensão não começa quando o empréstimo passa a atrasado. Esta descrição diverge de `[RN-08]`, que trata ligar ou desligar como configuração da biblioteca. A gravação da chave acompanha o empréstimo e entra no log desse registro. |
| **Problema que Resolve** | O gestor precisa decidir, na retirada, se aquele empréstimo pode suspender o leitor caso a devolução passe do prazo. |
| **Benefícios que Traz** | A chave fica na tela do empréstimo. Cada retirada guarda se a suspensão vale para ela. |
| **Passos** | 1. Na tela de registrar o empréstimo, ver a chave de suspensão daquele empréstimo<br>2. Se o gestor liga a chave:<br>2a. Ligar a suspensão para aquele empréstimo<br>Senão:<br>2b. Desligar a suspensão para aquele empréstimo |
| **Step map** | **HU-16** — Alterar configuração da suspensão. — Passos 1, 2a e 2b: a chave está na tela de HU-17, não numa configuração geral. Ligada, a devolução atrasada segue HU-20. Desligada, essa devolução não suspende. O log é o do empréstimo, HU-04. |

##### **F019** — Registrar devolução do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar devolução do exemplar |
| **Descrição** | Na área de gestão de empréstimos, o gestor registra a devolução de empréstimo ativo ou atrasado. O empréstimo fica devolvido. O exemplar volta a disponível. O histórico permanece. Se o empréstimo está atrasado e a chave de suspensão daquele empréstimo está ligada, a duração é informada nessa devolução (F020). Se a chave está desligada, a devolução não pede duração nem suspende. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | A volta do exemplar é riscada na agenda, e a unidade física continua tratada como fora da biblioteca. |
| **Benefícios que Traz** | A devolução parte da área de empréstimos. O exemplar volta a disponível e o empréstimo sai da conta do máximo. |
| **Passos** | 1. Abrir a área de gestão de empréstimos<br>2. Identificar o empréstimo ativo ou atrasado<br>3. Se o empréstimo está atrasado e a chave de suspensão daquele empréstimo está ligada:<br>3a. Informar a duração da suspensão e seguir<br>Senão:<br>3b. Seguir sem duração<br>4. Registrar a devolução do exemplar<br>5. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-19** — Registrar devolução do exemplar. — Passos 1, 2, 3a, 3b, 4 e 5: a devolução parte da área de empréstimos. O passo 3a só existe quando a chave de HU-16 está ligada. O empréstimo fica devolvido e o exemplar fica disponível. O log é um só, com os dois resultados, conforme HU-04. A mensagem do passo 5 representa esse log. [CONFIRMAR] Se a devolução atrasada, com a chave ligada, se conclui sem a duração. |

##### **F020** — Informar duração da suspensão do leitor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Informar duração da suspensão do leitor |
| **Descrição** | Não há tela própria. Na devolução do exemplar atrasado (F019), se a chave daquele empréstimo está ligada, o gestor informa a duração. Não há quantidade fixa de dias. O leitor fica suspenso por essa duração. Enquanto a suspensão vale, nenhum gestor registra novo empréstimo para esse leitor. Se a chave está desligada, esta funcionalidade não ocorre. O instante confirmado pelo PO é a devolução do exemplar atrasado, não a passagem automática a atrasado. Ao gravar a duração, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | Quem não devolveu no prazo, num empréstimo com a chave ligada, precisa ficar impedido de nova retirada pelo tempo informado na devolução. |
| **Benefícios que Traz** | A suspensão nasce na devolução atrasada, só quando a chave daquele empréstimo estava ligada, e vale para qualquer gestor. |
| **Passos** | 1. Receber o exemplar do empréstimo atrasado, na devolução<br>2. Se a chave de suspensão daquele empréstimo está desligada:<br>2a. Encerrar sem suspensão<br>Senão:<br>2b. Informar a duração da suspensão<br>3. Ver o leitor suspenso por essa duração<br>4. Ver a mensagem operação feita com sucesso, quando a duração é informada |
| **Step map** | **HU-20** — Informar duração da suspensão do leitor. — Passos 1, 2a, 2b, 3 e 4: a duração só é pedida na devolução atrasada de um empréstimo com a chave de HU-16 ligada. Enquanto a suspensão vale, HU-17 não se conclui para esse leitor. Sem quantidade fixa de dias. O log segue HU-04. A mensagem do passo 4 representa esse log. |

##### **F024** — Encerrar empréstimo por extravio do exemplar

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Encerrar empréstimo por extravio do exemplar |
| **Descrição** | Na área de gestão de empréstimos, a partir de empréstimo ativo ou atrasado, o gestor encerra por extravio. O empréstimo fica Encerrado por extravio e não volta a ativo, atrasado ou devolvido. O exemplar fica indisponível. Deixa de contar no máximo em paralelo. Depois disso, a remoção da obra e a do exemplar podem ser feitas. Ao concluir, a tela mostra `operação feita com sucesso`. |
| **Problema que Resolve** | O exemplar que não volta continua na agenda como empréstimo em aberto e segue ocupando a conta do leitor. |
| **Benefícios que Traz** | O encerramento por extravio parte da área de empréstimos, libera a vaga no máximo e deixa o exemplar indisponível. |
| **Passos** | 1. Abrir a área de gestão de empréstimos<br>2. Identificar o empréstimo ativo ou atrasado<br>3. Encerrar o empréstimo por extravio<br>4. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-24** — Encerrar empréstimo por extravio do exemplar. — Passos 1 a 4: parte da área de empréstimos. O empréstimo fica Encerrado por extravio e o exemplar fica indisponível. Deixa de contar no máximo (HU-14). A remoção de HU-07 e HU-09 pode seguir. O log é um só, com os dois resultados, conforme HU-04. A mensagem do passo 4 representa esse log. |

#### O sistema

##### **F018** — Registrar atraso do empréstimo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar atraso do empréstimo |
| **Descrição** | Não há tela própria. O sistema, ao passar a data prevista sem devolução, muda o empréstimo de ativo para atrasado. O exemplar permanece emprestado. O empréstimo atrasado não volta a ativo. A mudança aparece na lista de empréstimos (F025). Não gera log e não mostra a mensagem de sucesso. Não suspende o leitor. |
| **Problema que Resolve** | O atraso só aparece se alguém confere a data na agenda. |
| **Benefícios que Traz** | A lista de empréstimos passa a mostrar o empréstimo como atrasado, sem uma tela só para isso. |
| **Passos** | 1. Passar o empréstimo de ativo a atrasado quando a data prevista chega sem devolução<br>2. Mostrar o status atrasado na lista de empréstimos |
| **Step map** | **HU-18** — Registrar atraso do empréstimo. — Passos 1 e 2: o sistema marca o empréstimo como atrasado e a lista de HU-25 mostra esse status. O exemplar segue emprestado. O status não volta a ativo. Não gera log e não suspende o leitor. |

##### **F021** — Encerrar suspensão do leitor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Encerrar suspensão do leitor |
| **Descrição** | Não há tela própria. O sistema encerra a suspensão ao fim da duração informada. Não há novo ato do gestor e não gera log. O efeito aparece quando o gestor pesquisa o leitor para registrar um empréstimo (F017): o leitor cuja suspensão encerrou se distingue do leitor suspenso, e a tela permite registrar o empréstimo. |
| **Problema que Resolve** | A suspensão, uma vez anotada, ficaria valendo até alguém lembrar de tirá-la. O contexto diz que ela encerra sozinha ao fim da duração. |
| **Benefícios que Traz** | Na pesquisa do leitor para um empréstimo novo, quem já cumpriu a suspensão pode ser atendido, e quem ainda está suspenso continua impedido. |
| **Passos** | 1. Encerrar a suspensão do leitor ao fim da duração informada<br>2. Na pesquisa do leitor para novo empréstimo, distinguir esse leitor do leitor suspenso<br>3. Permitir registrar o empréstimo para o leitor cuja suspensão encerrou |
| **Step map** | **HU-21** — Encerrar suspensão do leitor. — Passos 1 a 3: o sistema encerra a suspensão sozinho. Não há tela própria e não gera log. A diferença aparece na pesquisa de HU-17. |

### Área de relatórios

Frame de origem: a área de relatórios, aberta pela tela inicial. Além do painel e do relatório do acervo, esta área abre a pesquisa de F010 e o recorte de F025.

#### Gestor

##### **F028** — Apresentar quantidades do painel

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Apresentar quantidades do painel |
| **Descrição** | Na área de relatórios, o sistema mostra a quantidade de obras cadastradas, de leitores com empréstimo nos últimos 6 meses, de empréstimos ativos e de empréstimos atrasados. Leitor com empréstimo nos últimos 6 meses tem ao menos um empréstimo cuja data de retirada está nos 6 meses anteriores à consulta. Esse número não é a lista de leitores com empréstimo ativo: essa lista é o recorte de F025. O painel não gera log e não mostra a mensagem de sucesso. [CONFIRMAR] Se obra removida entra na quantidade de obras cadastradas. |
| **Problema que Resolve** | Para saber essas quatro quantidades, o gestor conta na agenda. |
| **Benefícios que Traz** | O painel fica na área de relatórios, separado da lista de leitores com empréstimo ativo. |
| **Passos** | 1. Abrir a área de relatórios<br>2. Abrir o painel<br>3. Ver a quantidade de obras cadastradas, de leitores com empréstimo nos últimos 6 meses, de empréstimos ativos e de empréstimos atrasados |
| **Step map** | **HU-28** — Apresentar quantidades do painel. — Passos 1 a 3: as quatro quantidades são o mesmo gesto, na área de relatórios. O leitor dos 6 meses não é o recorte de leitores com empréstimo ativo de HU-25. O painel não gera log. [CONFIRMAR] Se obra removida entra na quantidade de obras cadastradas. |

##### **F029** — Emitir relatório do acervo

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Emitir relatório do acervo |
| **Descrição** | Na área de relatórios, o gestor emite o relatório simples do acervo. A lista combina dois recortes: todas as obras ou um tipo, e todas as obras já cadastradas ou apenas as que ainda não foram removidas. Cada obra mostra a data de inclusão, o último empréstimo e o status desse empréstimo. Obra sem empréstimo mostra a data de inclusão e não traz último empréstimo. Ao emitir, a tela mostra `operação feita com sucesso`. O log guarda o recorte, sem valor anterior e sem valor novo. |
| **Problema que Resolve** | A lista do acervo em papel não separa tipo nem obra já removida, e não mostra, junto da data de inclusão, o último empréstimo. |
| **Benefícios que Traz** | O relatório parte da área de relatórios, no recorte escolhido, e a emissão fica visível na tela. |
| **Passos** | 1. Abrir a área de relatórios<br>2. Escolher o recorte de tipo: todas as obras ou um tipo<br>3. Escolher o recorte de permanência: todas as obras já cadastradas ou apenas as que ainda não foram removidas<br>4. Emitir o relatório do acervo<br>5. Ver a data de inclusão de cada obra<br>6. Se a obra tem empréstimo:<br>6a. Ver o último empréstimo e o status desse empréstimo<br>Senão:<br>6b. Ver a obra sem último empréstimo<br>7. Ver a mensagem operação feita com sucesso |
| **Step map** | **HU-29** — Emitir relatório do acervo. — Passos 1 a 7: a emissão parte da área de relatórios. Obra sem empréstimo traz a data de inclusão e não traz último empréstimo. O log guarda o recorte, sem valor anterior nem novo, conforme HU-04. A mensagem do passo 7 representa esse log. |

### Sem tela própria

#### O sistema

##### **F004** — Registrar log da ação do gestor

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar log da ação do gestor |
| **Descrição** | Não há tela de log. O sistema grava o log quando o gestor conclui uma ação que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório. Na tela dessa ação, o sistema mostra `operação feita com sucesso`. Essa mensagem representa que os dados foram salvos no log. O log guarda data e hora, o gestor, a ação, o que mudou, a identificação, o valor anterior e o valor novo. Na inclusão, o valor anterior fica vazio. Na remoção, o valor novo é a remoção. No relatório, guarda o recorte e não guarda valor anterior nem novo. Uma ação que altera exemplar e empréstimo gera um log, com os dois resultados. A senha não entra. Consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim automático da suspensão e a criação do primeiro gestor não geram log e não mostram essa mensagem. A ação listada não se conclui sem o log. |
| **Problema que Resolve** | O gestor conclui uma alteração e a tela não mostra que a ação ficou registrada. |
| **Benefícios que Traz** | A ação que gera log mostra `operação feita com sucesso` na própria tela. Consulta, pesquisa, painel, recusa, atraso automático e fim da suspensão não mostram essa mensagem. |
| **Passos** | 1. Concluir uma ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório<br>2. Se a ação é consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim da suspensão ou criação do primeiro gestor:<br>2a. Encerrar sem log e sem a mensagem<br>Senão:<br>2b. Registrar o log da ação, sem a senha<br>3. Mostrar, na tela da ação, a mensagem operação feita com sucesso |
| **Step map** | **HU-04** — Registrar log da ação do gestor. — Passos 1, 2a, 2b e 3: não há tela de log. A mensagem `operação feita com sucesso` aparece na tela da ação que gerou log. O log guarda data e hora, gestor, ação, o que mudou, identificação, valor anterior e valor novo. Na inclusão, o valor anterior fica vazio. Na remoção, o valor novo é a remoção. No relatório, guarda o recorte, sem valor anterior nem novo. Ação que altera exemplar e empréstimo gera um log com os dois resultados. A senha não entra. |

### Limites e Não-Escopo

- ❌ **Loja:** não é loja de livros e o acervo não é estoque de venda. Origem: `produto.md`, `glossario.md`.
- ❌ **Automação com IA:** não faz automação com IA. Origem: `produto.md`.
- ❌ **Compartilhamento externo:** não compartilha os dados dos cadastrados com outras ferramentas da internet. Origem: `produto.md`, `[DEC-05]`.
- ❌ **Operação sem pessoa:** não dispensa a pessoa na gestão do acervo e dos empréstimos. Origem: `produto.md`.
- ❌ **Prazo fixo:** não há quantidade fixa de dias para o prazo do leitor nem para a duração da suspensão. Origem: `produto.md`, `[RN-06]`, `[RN-08]`.
- ❌ **Multa:** o contexto não tem multa. O impedimento de novo empréstimo é a suspensão do leitor. Origem: `glossario.md`, `[RN-08]`.
- ❌ **Venda, reserva e doação:** empréstimo não é venda, reserva nem doação. Origem: `glossario.md`.
- ❌ **Norma externa:** nenhuma norma externa neste ciclo. A faixa etária indicada do brinquedo não impede o empréstimo. Origem: `[DEC-05]`.
- ❌ **Papel da equipe de desenvolvimento:** a equipe cria o primeiro gestor, não opera acervo nem empréstimo, e essa criação não gera log. Não é papel do produto. Origem: `[RN-14]`, `glossario.md`.
- ❌ **Página pública:** a consulta do leitor não inclui cadastro, empréstimo nem configuração. Origem: `[RN-01]`.
- ❌ **Volta de status:** empréstimo atrasado não volta a ativo. Encerrado por extravio não volta a ativo, atrasado ou devolvido. Origem: `glossario.md`.
- ❌ **Log que o contexto exclui:** consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim automático da suspensão e criação do primeiro gestor não geram log e não mostram `operação feita com sucesso`. A senha não entra no log. Origem: `[RN-14]`.
- ❌ **Tela de log, tela de atraso e tela de fim da suspensão:** F004, F018 e F021 não têm frame próprio. Origem: PO, em 2026-11-11.
- ❌ **Meia hora:** o registro do empréstimo, o cadastro da obra e o cadastro do leitor não podem passar a durar meia hora. Origem: `produto.md`.
- ❌ **Ações não nomeadas:** editar exemplar, remover leitor e remover gestor não constam das ações de `[RN-14]` e não entraram como funcionalidade. A remoção do exemplar entrou por `[RN-12]`, com a pendência do log.

### Pendências

- `[CONFIRMAR]` Se a quantidade de exemplares informada na obra precisa coincidir com os exemplares cadastrados em HU-08.
- `[CONFIRMAR]` Se a edição da obra pode trocar o tipo. HU-06.
- `[CONFIRMAR]` Se a remoção do exemplar gera log. HU-09.
- `[CONFIRMAR]` O que a pesquisa mostra quando a obra tem, ao mesmo tempo, exemplar emprestado e exemplar indisponível sem empréstimo. HU-10 e HU-11.
- `[CONFIRMAR]` A unidade do prazo no formulário do leitor, e se a mudança recalcula a data prevista de empréstimo ativo ou atrasado. HU-15.
- `[CONFIRMAR]` Se a devolução atrasada, com a chave de suspensão ligada, se conclui sem a duração. HU-19 e HU-20.
- `[CONFIRMAR]` Quais dados o histórico do leitor e a movimentação do exemplar mostram. HU-26 e HU-27.
- `[CONFIRMAR]` Se obra removida entra na quantidade de obras cadastradas do painel. HU-28.
- `⚠️ [SUPOSIÇÃO]` A ordem das mensagens de login e a ordem das recusas do empréstimo não estão no contexto. HU-01 e HU-17.
