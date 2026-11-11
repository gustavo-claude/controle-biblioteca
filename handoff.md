# Handoff — Biblioteca Limoeiro

> Passagem de bastão em 7 de novembro de 2026. Este arquivo descreve o estado do trabalho de Product Ownership. Não substitui `contexto/`. Em conflito, vale o arquivo de contexto mais específico, e a cópia local vale sobre o que ainda não foi commitado.

## 1. O que é este lugar

Workspace de **Product Ownership** do produto **Biblioteca Limoeiro**. Aqui se escreve problema, regra, vocabulário e especificação. Não se escreve código de produção nem decisão técnica (banco, API, framework, tela).

O kit de método está em `AGENTS.md`, `.agents/` e `exemplos/`. O fato do produto está em `contexto/`. A saída formal vai para `entregas/AAAA-MM-DD-assunto.md`.

`AGENTS.md` ainda traz o placeholder `[PREENCHER: Nome do Produto]`. O nome oficial já fechado é Biblioteca Limoeiro.

## 2. Repositório

- Remoto: `https://github.com/gustavo-claude/controle-biblioteca.git` (`origin`).
- Branch de trabalho: `trabalho`, acompanhando `origin/trabalho`.
- Último commit enviado: `10e4fdc` — contexto inicial e lista de funcionalidades.
- A branch `master` local é a base antiga do kit. O remoto no GitHub não é o GitLab de origem. Não reconectar o GitLab sem pedido explícito.
- **Fora do commit:** `contexto/produto.md` está modificado na cópia de trabalho e ainda não foi para o GitHub. Quem abrir só o remoto vê metas e horário antigos, com `[CONFIRMAR]`.

## 3. Produto, em uma frase

Sistema de gestão de acervo e de empréstimos da biblioteca comunitária. O gestor, com usuário e senha, registra livros, exemplares, leitores e empréstimos. O leitor consulta a disponibilidade sem login.

Substitui agendas e fichas catalográficas em papel. Não é loja, não faz automação com IA, não dispensa a pessoa na operação e não compartilha dados dos cadastrados com outras ferramentas da internet.

## 4. O que já foi feito

| Entrega | Onde | Estado |
|---|---|---|
| Fonte bruta | `fontes/sistema-exemplo.md` | Lida e usada. É lista de requisitos, não ata. |
| Briefing | `contexto/briefing.md` | Preenchido. A linha "Dar certo é" não tem número. |
| Ficha do produto | `contexto/produto.md` | Preenchida. A cópia local, não commitada, atualiza metas, horário e segurança. Ver seção 5. |
| Personas | `contexto/personas-usuario.md` | Gestor (usuário primário) e leitor. Sem nome fictício. |
| Regras | `contexto/regras-de-negocio.md` | `[RN-01]` a `[RN-09]`. Nenhuma revogada. |
| Glossário | `contexto/glossario.md` | Termos, sinônimos proibidos e status do exemplar e do empréstimo. |
| Lista de funcionalidades | `entregas/funcionalidades/2026-11-05-lista-funcionalidades.md` | F001–F018 e HU-01–HU-18. Passos e step map **pendentes de validação**. |
| Decisões | `contexto/decisoes.md` | Só o gabarito. Nenhuma decisão ativa. |

## 5. O que a cópia local de `produto.md` já diz e o resto ainda não acompanhou

Estas linhas existem só no arquivo local, depois do commit `10e4fdc`:

- Meta principal: digitalizar o acervo, ultrapassando 100 itens, em **3 meses a partir da implantação**.
- Meta secundária: cadastrar pelo menos **20 leitores e 5 gestores**.
- Métrica de guarda, no texto do arquivo: "O tempo gesto e o esforço percebido dos gestores não deve aumentar." Não há número. A frase está como foi salva.
- Disponibilidade: operação em **24 horas**, em computador, tablet ou celular, para quem administra.
- Segurança: gestores entram com usuário e senha. Os dados dos cadastrados não são compartilhados.

`regras-de-negocio.md` e `glossario.md` ainda dizem "pelo menos 20 usuários" com `[CONFIRMAR]`. A lista de funcionalidades também. Não reescreva esses arquivos para "combinar" sem autorização. O contrato do workspace proíbe alterar `contexto/` sem pedido explícito.

## 6. Vocabulário que não pode escorregar

Use `contexto/glossario.md`. Atalho para quem chega agora:

- **Gestor** administra. **Administrador** está proibido.
- **Leitor** consulta sem login e toma o exemplar emprestado.
- **Usuário** é a credencial (usuário e senha), não a pessoa.
- **Livro** é o registro do título. **Exemplar** é a unidade física, com código único. Chamar o exemplar de livro ou de obra está proibido.
- **Obra** não entrou no glossário. O briefing fala em "demais obras"; a lista só trata de livro e exemplar.
- **Atraso** é do empréstimo. **Suspensão** é condição do leitor, e só se a configuração estiver ligada.
- **Prazo** é configuração do gestor. Não há quantidade fixa de dias.

Status fechados do exemplar: disponível, emprestado, indisponível. Do empréstimo: ativo, atrasado, devolvido. Empréstimo atrasado não volta a ativo. Exemplar que não está disponível não sai. O teto é 3 empréstimos ao mesmo tempo por pessoa; o já devolvido não entra na conta.

## 7. Pendências que bloqueiam detalhe

Não transforme item `[CONFIRMAR]` em regra fechada.

- Quem cria o primeiro usuário, se o cadastro exige um gestor já autenticado.
- Se o gestor corrige ou exclui usuário, leitor ou exemplar sem excluir o livro.
- Situação do exemplar no cadastro, e quem o marca como indisponível, a partir de qual status.
- O que a consulta mostra no exemplar indisponível sem empréstimo, e qual data prevista mostrar quando há mais de um exemplar fora.
- O que acontece ao excluir um livro que ainda tem exemplar emprestado.
- Duração da suspensão e o que o leitor suspenso fica impedido de fazer, inclusive novo empréstimo.
- O sentido de "leitor ativo" e de "devolução pendente" no resumo.
- O recorte do relatório simples.
- Se o acervo inclui item que não é livro.
- Conformidade: o cadastro do leitor tem CPF, telefone e endereço, e nenhuma norma foi nomeada.
- Nomes fictícios das personas: abandonados em 2026-11-11. Gestor e leitor bastam.
- A métrica de guarda da seção 5 não tem número.

## 8. Por onde continuar

1. Ler, nesta ordem: `AGENTS.md`, `contexto/produto.md` (a cópia local), `contexto/personas-usuario.md`, `contexto/glossario.md`, `contexto/regras-de-negocio.md`, `entregas/funcionalidades/2026-11-05-lista-funcionalidades.md`.
2. Tratar a lista como proposta. As linhas "Validação dos passos" e "Step map" continuam pendentes até confirmação explícita, e uma não confirma a outra.
3. Não redigir história de usuário antes dessa validação, salvo pedido explícito. A skill de especificação é `.agents/skills/elaborar-especificacao.md`; a de revisão é `.agents/skills/revisar-criticamente.md`.
4. Personas de trabalho: `@facilitador`, `@analista`, `@escritor`, `@critico`, em `.agents/agents.md`.
5. Não ler arquivo `RECEITA-*.md`. São guias do operador humano.
6. Não inventar número, prazo, status ou sinônimo. Separe fato de suposição. Suposição leva `⚠️ [SUPOSIÇÃO]`.
7. Um passo de cada vez. Artefato novo de entrega entra em `entregas/`, não na raiz e não em `contexto/`, salvo pedido para alterar o contexto.
