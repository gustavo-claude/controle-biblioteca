# Ficha Técnica do Produto: Biblioteca Limoeiro

> 💡 **PAPEL DESTE ARQUIVO:**  
> Define a visão, a proposta de valor, as metas numéricas e, principalmente, **os limites do produto**. É o documento consultado pela IA para saber o que faz e o que não faz sentido construir.  
> ⚠️ **SEÇÃO MAIS IMPORTANTE:** A seção *"O que NÃO somos"* evita que a IA (e o time) infle o escopo com funcionalidades fora da estratégia.

---

## 1. Visão Geral e Proposta de Valor

- **Nome Oficial:** Biblioteca Limoeiro
- **Em uma frase:** Sistema de gestão de acervo e de empréstimos da biblioteca, usado por quem tem usuário e senha para registrar obras e empréstimos e consultar a situação de cada exemplar (disponível, emprestado ou indisponível).
- **Proposta de Valor:** Substitui agendas em papel e fichas catalográficas em papel por um registro único do acervo e dos empréstimos, para incluir e remover informações sem depender de listas sem padrão. A situação atual de cada exemplar fica visível no sistema.

---

## 2. Objetivos com Número (Metas do Ciclo)

> 🎯 *Objetivo sem número é apenas intenção. Defina metas quantitativas claras.*

1. **Meta Principal:** Digitalizar o acervo, ultrapassando 100 itens digitalizados. Prazo do ciclo: [CONFIRMAR].
2. **Meta Secundária:** Cadastrar pelo menos 20 usuários. [CONFIRMAR] se "usuário" aqui é o leitor da biblioteca ou a pessoa que opera o sistema.
3. **Métrica de Guarda (O que não pode piorar):** [CONFIRMAR]. O PO não definiu o que não pode piorar.

---

## 3. O que NÃO somos e o que NÃO fazemos

> 🚫 *Esta lista é a ferramenta mais poderosa para conter escopo.*

- ❌ **Não somos um sistema de:** loja de livros.
- ❌ **Não fazemos:** automação com IA, nem compartilhamento dos dados dos cadastrados com outras ferramentas da internet.
- ❌ **Não atendemos:** a operação sem participação humana. O sistema não dispensa a pessoa na gestão do acervo e dos empréstimos. [CONFIRMAR] se há um público que este ciclo deixa de fora.
- ❌ **Não definimos um prazo fixo de empréstimo:** o prazo de empréstimo e de devolução é configurável pela biblioteca. Nenhum número de dias foi fechado.

---

## 4. Grandes Módulos do Sistema

| Módulo | Responsabilidade Principal | Quem Utiliza |
|---|---|---|
| **Acervo** | Cadastrar, consultar, editar e excluir livros; classificar por gênero, categoria e assunto; informar a quantidade de exemplares; atribuir código único a cada exemplar; pesquisar por título, autor, categoria ou código; mostrar se o exemplar está disponível, emprestado ou indisponível. [CONFIRMAR] se o acervo inclui obras que não são livros. | Responsáveis pela administração. A consulta ao catálogo, na fonte, é feita por "usuários". [CONFIRMAR] se o leitor consulta no sistema ou se é apenas um cadastro. |
| **Leitores** | Cadastrar o leitor com nome completo, telefone, endereço e CPF, e manter o registro individual com o histórico de empréstimos. | Responsáveis pela administração. |
| **Empréstimos** | Registrar a retirada do exemplar pelo leitor, gravar a data de retirada, calcular a data prevista de devolução pelo prazo configurado pela biblioteca, impedir o empréstimo de exemplar que não esteja disponível, registrar a devolução e devolver o exemplar a disponível, identificar atraso pela data prevista, consultar empréstimos ativos, devolvidos e atrasados, e manter o histórico de movimentação de cada exemplar. Um leitor pode ter mais de um empréstimo ativo, dentro do limite definido. [CONFIRMAR] o número desse limite. | Responsáveis pela administração. |
| **Painel** | Mostrar a quantidade de livros cadastrados, de leitores ativos e de empréstimos em andamento, além de devoluções pendentes e empréstimos em atraso. | Responsáveis pela administração. |
| **Relatórios** | Emitir relatórios simples sobre o acervo e a movimentação dos livros. | Responsáveis pela administração. |
| **Acesso** | Garantir que só entra quem tem permissão de usuário e senha, e proteger os dados dos cadastrados. Inclui o gerenciamento dos usuários responsáveis pela administração da biblioteca. | Quem possui usuário e senha. |

---

## 5. Restrições Estratégicas Inegociáveis

- **Disponibilidade:** Uso em ambiente web, em computador, tablet ou celular, por quem administra a biblioteca. Horário de operação: [CONFIRMAR].
- **Segurança:** Acesso somente para quem tem permissão de usuário e senha. Os dados dos cadastrados devem permanecer protegidos e não são compartilhados com outras ferramentas da internet.
- **Conformidade:** [CONFIRMAR]. Nenhuma norma foi nomeada. O cadastro do leitor inclui CPF, telefone e endereço.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] As metas possuem números e prazos?
[ ] A seção "O que NÃO somos" contém pelo menos 3 proibições claras?
[ ] Os módulos descrevem responsabilidades sem detalhar implementação técnica?
-->
