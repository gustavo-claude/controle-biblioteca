# Ficha Técnica do Produto: Biblioteca Limoeiro

> 💡 **PAPEL DESTE ARQUIVO:**  
> Define a visão, a proposta de valor, as metas numéricas e, principalmente, **os limites do produto**. É o documento consultado pela IA para saber o que faz e o que não faz sentido construir.  
> ⚠️ **SEÇÃO MAIS IMPORTANTE:** A seção *"O que NÃO somos"* evita que a IA (e o time) infle o escopo com funcionalidades fora da estratégia.

---

## 1. Visão Geral e Proposta de Valor

- **Nome Oficial:** Biblioteca Limoeiro
- **Em uma frase:** Sistema de gestão de acervo e de empréstimos da biblioteca. O gestor, com usuário e senha, registra obras e empréstimos. O leitor consulta, sem login, a situação de cada exemplar: disponível, emprestado ou indisponível.
- **Proposta de Valor:** Substitui agendas em papel e fichas catalográficas em papel por um registro único do acervo e dos empréstimos, para incluir e remover informações sem depender de listas sem padrão. A situação atual de cada exemplar fica visível no sistema.

---

## 2. Objetivos com Número (Metas do Ciclo)

> 🎯 *Objetivo sem número é apenas intenção. Defina metas quantitativas claras.*

1. **Meta Principal:** Digitalizar o acervo, ultrapassando 100 itens digitalizados. Prazo do ciclo: 3 meses a partir da implantação do sistema.
2. **Meta Secundária:** Cadastrar pelo menos 20 leitores e 5 gestores do sistema.
3. **Métrica de Guarda (O que não pode piorar):** O tempo gasto e o esforço percebido dos gestores não deve aumentar. O registro do empréstimo, o cadastro da obra e o cadastro do leitor, que na agenda levam minutos, não podem passar a durar meia hora.

---

## 3. O que NÃO somos e o que NÃO fazemos

> 🚫 *Esta lista é a ferramenta mais poderosa para conter escopo.*

- ❌ **Não somos um sistema de:** loja de livros.
- ❌ **Não fazemos:** automação com IA, nem compartilhamento dos dados dos cadastrados com outras ferramentas da internet.
- ❌ **Não atendemos:** a operação sem participação humana. O sistema não dispensa a pessoa na gestão do acervo e dos empréstimos. Dentro da comunidade que utiliza e gere o ambiente da biblioteca comunitária, não há público que este ciclo deixa de fora.
- ❌ **Não definimos um prazo fixo de empréstimo:** o prazo de empréstimo e de devolução é configurável pela biblioteca. Nenhum número de dias foi fechado.

---

## 4. Grandes Módulos do Sistema

| Módulo          | Responsabilidade Principal                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        | Quem Utiliza                                                                                                                                                                     |
| --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Acervo**      | Cadastrar, consultar, editar e excluir obras. O tipo é obrigatório: livro, revista, HQ, brinquedo ou outro, com os dados desse tipo. Toda obra guarda a data e a hora da inclusão e o gestor responsável; na remoção, guarda a data e o gestor responsável. Atribuir a cada exemplar um código único, guardado no sistema, sem derivar de ISBN nem de outro dado externo. Pesquisar pelos dados do tipo e pelo código do exemplar. Mostrar se o exemplar está disponível, emprestado ou indisponível. | Gestor. O leitor consulta a disponibilidade em página pública, sem login e sem cadastro preliminar. |
| **Leitores**    | Cadastrar o leitor com nome obrigatório e CPF único e obrigatório. O nome pode ser apelido ou nome social e não é conferido com o CPF. Telefone e endereço são opcionais. Editar esse cadastro gera log. Manter o histórico de empréstimos do leitor. | Gestor. |
| **Empréstimos** | Registrar a retirada do exemplar pelo leitor, gravar a data de retirada, calcular a data prevista de devolução pelo prazo configurado pelo gestor, impedir o empréstimo de exemplar que não esteja disponível, registrar a devolução e devolver o exemplar a disponível, identificar atraso pela data prevista, encerrar o empréstimo por extravio e consultar empréstimos ativos, devolvidos, atrasados e encerrados por extravio. Manter o histórico de movimentação de cada exemplar. O padrão em paralelo é 2; o gestor pode aumentar no cadastro do leitor e não pode ficar abaixo de 2. O leitor não empresta dois exemplares da mesma obra ao mesmo tempo. | Gestor. |
| **Painel**      | Mostrar a quantidade de obras cadastradas, de leitores com empréstimo nos últimos 6 meses, de empréstimos ativos e de empréstimos atrasados. | Gestor. |
| **Relatórios**  | Emitir relatório simples do acervo. A lista combina dois recortes: todas as obras ou um tipo, e todas as obras já cadastradas ou apenas as que ainda não foram removidas. Cada obra mostra a data de inclusão, o último empréstimo e o status desse empréstimo. Obra sem empréstimo mostra a data de inclusão e não traz último empréstimo. A emissão gera log, com esse recorte. | Gestor. |
| **Acesso**      | O primeiro gestor é criado pela equipe de desenvolvimento. Os gestores entram com usuário e senha e criam novos gestores. A ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório, gera log. Os dados dos cadastrados permanecem protegidos. | Gestor, com usuário e senha. A equipe de desenvolvimento só cria o primeiro gestor. |

---

## 5. Restrições Estratégicas Inegociáveis

- **Disponibilidade:** Uso em ambiente web, em computador, tablet ou celular, por quem administra a biblioteca. Horário de operação: 24 horas.
- **Segurança:** O gestor entra somente com usuário e senha. Os dados dos cadastrados permanecem protegidos e não são compartilhados com outras ferramentas da internet.
- **Conformidade:** Nenhuma norma externa. Valem as regras deste contexto: nome e CPF único do leitor, sem conferência entre nome e CPF, telefone e endereço opcionais, acesso do gestor com usuário e senha, e nenhum compartilhamento dos dados dos cadastrados com outras ferramentas da internet.

---
