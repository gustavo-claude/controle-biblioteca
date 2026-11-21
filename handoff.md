# Handoff — Biblioteca Limoeiro

> Passagem de bastão em 11 de novembro de 2026. Este arquivo descreve o estado do trabalho de Product Ownership. Não substitui `contexto/`. Em conflito, vale o arquivo de contexto.

## 1. O que é este lugar

Workspace de **Product Ownership** do produto **Biblioteca Limoeiro**. Aqui se escreve problema, regra, vocabulário e especificação. Não se escreve código de produção nem decisão técnica (banco, API, framework, tela).

O kit de método está em `AGENTS.md`, `.agents/` e `exemplos/`. O fato do produto está em `contexto/`. A saída formal vai para `entregas/AAAA-MM-DD-assunto.md`.

`AGENTS.md` ainda traz o placeholder `[PREENCHER: Nome do Produto]`. O nome oficial é Biblioteca Limoeiro.

## 2. Repositório

- Remoto: `https://github.com/gustavo-claude/controle-biblioteca.git` (`origin`).
- Branch de trabalho: `trabalho`, alinhada com `origin/trabalho`.
- Último commit: `ec5321e` — contexto sem `[CONFIRMAR]` aberto, em 11 de novembro de 2026.
- A branch `master` local é a base antiga do kit. O remoto no GitHub não é o GitLab de origem. Não reconectar o GitLab sem pedido explícito.
- Este handoff foi escrito depois desse commit. Se `handoff.md` aparecer modificado, o contexto commitado continua sendo a fonte.

## 3. Produto, em uma frase

Sistema de gestão de acervo e de empréstimos da biblioteca comunitária. O gestor, com usuário e senha, registra obras, exemplares, leitores e empréstimos. O leitor consulta a disponibilidade sem login.

A obra tem tipo: livro, revista, HQ, brinquedo ou outro. O exemplar é a unidade física. Substitui agendas e fichas catalográficas em papel. Não é loja, não faz automação com IA, não dispensa a pessoa na operação e não compartilha dados dos cadastrados com outras ferramentas da internet. Nenhuma norma externa foi adotada (`[DEC-05]`).

## 4. O que já foi feito

| Entrega | Onde | Estado |
|---|---|---|
| Fonte bruta | `fontes/sistema-exemplo.md` | Lida e usada. É lista de requisitos, não ata. |
| Briefing | `contexto/briefing.md` | Preenchido, com as metas e a meia hora. |
| Ficha do produto | `contexto/produto.md` | Fechada. Sem `[CONFIRMAR]`. |
| Personas | `contexto/personas-usuario.md` | Gestor e leitor. Sem nome fictício. |
| Regras | `contexto/regras-de-negocio.md` | `[RN-01]` a `[RN-14]`. Nenhuma revogada. |
| Glossário | `contexto/glossario.md` | Termos, sinônimos proibidos, status e matriz. |
| Decisões | `contexto/decisoes.md` | `[DEC-02]` a `[DEC-06]` ativas. `[DEC-01]` substituída por `[DEC-04]`. |
| Lista de funcionalidades | `entregas/funcionalidades/2026-11-05-lista-funcionalidades.md` | F001–F018 e HU-01–HU-18. **Desatualizada.** Ainda fala em livro e no teto de 3. Não validar aqueles passos. |

## 5. Fatos que a próxima sessão não pode reabrir

- Mais de 100 itens em 3 meses a partir da implantação. Pelo menos 20 leitores e 5 gestores.
- A meia hora vale para o registro do empréstimo, o cadastro da obra e o cadastro do leitor.
- Operação em 24 horas, em computador, tablet ou celular, para quem administra.
- O exemplar nasce disponível. O código é único, guardado no sistema, e não deriva de ISBN.
- O padrão de empréstimos em paralelo é 2. O gestor pode aumentar. Não fica abaixo de 2. Empréstimo devolvido não entra na conta.
- O leitor não empresta dois exemplares da mesma obra ao mesmo tempo. O título não identifica a obra.
- CPF único e obrigatório. Nome obrigatório, sem conferência com o CPF. Telefone e endereço opcionais.
- O primeiro gestor é criado pela equipe de desenvolvimento e isso não gera log. Os gestores criam os demais.
- Quando há exemplar emprestado, a consulta mostra a data prevista mais próxima. No indisponível sem empréstimo, a mensagem é que o exemplar não está disponível para empréstimo, sem data.
- A remoção de obra ou de exemplar emprestado fica bloqueada até o empréstimo ficar Encerrado por extravio.
- O relatório combina dois recortes: todas as obras ou um tipo, e todas as já cadastradas ou apenas as que ainda não foram removidas.
- O log cobre a ação do gestor que altera cadastro, configuração, status ou que emite relatório. A senha não entra. Consulta, pesquisa, painel, recusa sem gravação, atraso automático e fim automático da suspensão não geram log.

## 6. Vocabulário que não pode escorregar

Use `contexto/glossario.md`. Atalho:

- **Gestor** administra. **Administrador** está proibido. **Usuário** é a credencial, não a pessoa.
- **Leitor** consulta sem login e toma o exemplar emprestado.
- **Obra** é o registro do item. **Livro** é um tipo de obra. **Exemplar** é a unidade física. Volume e peça estão proibidos.
- **Autor** é dado do livro e da HQ. Quem remove a obra é o gestor responsável pela remoção.
- **Atraso** é do empréstimo. **Suspensão** é condição do leitor. **Extravio** não é status do exemplar.
- **Prazo** não tem quantidade fixa de dias.

Status do exemplar: disponível, emprestado, indisponível. Do empréstimo: ativo, atrasado, devolvido, encerrado por extravio. Empréstimo atrasado não volta a ativo. Encerrado por extravio não volta a ativo, atrasado ou devolvido.

## 7. Pendências

Não há `[CONFIRMAR]` em `contexto/`.

A lista em `entregas/funcionalidades/2026-11-05-lista-funcionalidades.md` contradiz o contexto atual. Passos e step map continuam sem validação, e o texto antigo não deve ser confirmado como está.

`AGENTS.md` ainda não traz o nome do produto no lugar do placeholder.

## 8. Por onde continuar

1. Ler, nesta ordem: `AGENTS.md`, `contexto/produto.md`, `contexto/personas-usuario.md`, `contexto/glossario.md`, `contexto/regras-de-negocio.md`, `contexto/decisoes.md`.
2. O próximo artefato é uma lista de funcionalidades nova, a partir desse contexto. Não partir de F001–F018 como se ainda valessem.
3. Não redigir história de usuário antes da validação dos passos e do step map da lista nova, salvo pedido explícito. A skill de especificação é `.agents/skills/elaborar-especificacao.md`; a de revisão é `.agents/skills/revisar-criticamente.md`.
4. Personas de trabalho: `@facilitador`, `@analista`, `@escritor`, `@critico`, em `.agents/agents.md`.
5. Não ler arquivo `RECEITA-*.md`. São guias do operador humano.
6. Não inventar número, prazo, status ou sinônimo. Não usar nome fictício. Suposição leva `⚠️ [SUPOSIÇÃO]`.
7. Um passo de cada vez. Artefato novo de entrega entra em `entregas/`, não na raiz e não em `contexto/`, salvo pedido para alterar o contexto.
