# Relatório de execução: wireflows da Biblioteca Limoeiro

Data: 2026-11-11. Segunda geração, depois da avaliação do PO. A primeira versão foi substituída nos mesmos caminhos.

Fonte: `entregas/funcionalidades/2026-11-11-lista-funcionalidades.md`. Destino: `entregas/wireframes/`.

## Resultado

29 funcionalidades. 29 Markdown e 29 SVG. Cada wireflow parte da tela comum do seu grupo. Dentro do retângulo está a página. Título, passo e seta ficam fora.

## Agrupamentos

| Grupo | Funcionalidades | Tela de origem |
| --- | --- | --- |
| Login | F001 | Tela de login e, em seguida, a tela inicial com Acervo, Usuários, Empréstimos e Relatórios |
| Usuários | F002, F003, F012, F013, F014, F015, F026 | Área de gestão de usuários. Cadastro e edição do gestor são a mesma página. O formulário do leitor reúne nome, CPF, telefone, endereço, máximo e prazo |
| Acervo, obras | F005, F006, F007, F008, F009 | Área de gestão do acervo. Adicionar obra abre a escolha do tipo e, depois, o formulário daquele tipo. Sem quadro de recusa |
| Acervo, pesquisa e exemplar | F010, F011, F022, F023, F027 | F010 abre no acervo e nos relatórios. F011 é a mesma pesquisa, em página pública, sem a barra do gestor |
| Empréstimos | F016, F017, F018, F021, F025 | A lista e a tela de retirada. A chave de suspensão fica nessa tela. O atraso muda o status na lista. O fim da suspensão aparece na pesquisa do leitor |
| Devolução e extravio | F019, F020, F024 | Devolução na área de empréstimos. A duração da suspensão entra quando a chave daquele empréstimo estava ligada. O extravio encerra o empréstimo e deixa o exemplar indisponível |
| Relatórios e log | F004, F028, F029 | Painel e relatório na área de relatórios. F004 não é uma tela de log: a página da ação mostra `operação feita com sucesso` |

## Correções desta geração

- O texto explicativo saiu de dentro da página.
- O Frame A de cada grupo passou a ser a área correspondente, não um bloco de regras.
- F009 não mostra a mensagem de sucesso, porque ainda está em aberto se a remoção do exemplar gera log.
- Em F010, o rótulo da seta da direita foi afastado da linha.

## Premissas

- A ordem entre senha errada e usuário não cadastrado não está no contexto.
- A ordem das recusas do empréstimo não está no contexto.
- A edição da obra repete a estrutura do cadastro do tipo. Trocar o tipo continua em aberto.
- O prazo no formulário do leitor e a chave de suspensão no empréstimo divergem de `[RN-06]` e `[RN-08]`. A lista prevalece para estes wireflows. `contexto/` não foi alterado.
- A suspensão, com a chave ligada, começa na devolução do exemplar atrasado. Confirmado pelo PO.

## Pendências que o desenho não fecha

Quantidade de exemplares da obra e exemplares cadastrados. Troca do tipo na edição. Log da remoção do exemplar. Pesquisa com exemplar emprestado e indisponível ao mesmo tempo. Unidade do prazo e recálculo de empréstimo já aberto. Devolução atrasada sem a duração, quando a chave está ligada. Colunas do histórico e da movimentação. Obra removida na quantidade do painel.
