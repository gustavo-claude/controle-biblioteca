# Personas de Usuário do Produto

> 💡 **PAPEL DESTE ARQUIVO:**  
> Define as pessoas reais que usam o sistema. A IA usa estas personas para redigir histórias focadas nas dores cotidianas reais, e não em papéis abstratos.  
> ⚠️ **REGRA DE OURO:** Mantenha entre **2 e 5 personas**. Mais de 5 personas pulveriza o foco e gera requisitos contraditórios.  
> O nome da persona é o papel: **gestor** e **leitor**. Não usar nome fictício.

---

## 1. Persona 1: Gestor da biblioteca — usuário primário

- **Perfil e Rotina:** Pessoa que administra a Biblioteca Limoeiro. Entra com login e senha. No dia a dia controla o acervo inteiro, com adições e remoções, marca a indisponibilidade do exemplar, encerra empréstimo por extravio, controla os empréstimos, cria outros gestores, edita o cadastro de gestor e de leitor, configura os prazos e define o máximo de empréstimos em paralelo no cadastro de cada leitor. Cadastro, configuração, mudança de status e emissão de relatório geram log. O padrão é 2 e o valor não fica abaixo de 2. Ao receber o exemplar atrasado, informa a duração da suspensão. O primeiro gestor não nasce nesta rotina: a equipe de desenvolvimento cria esse acesso.
- **Objetivo Principal no Sistema:** Concluir a gestão do acervo e dos empréstimos: incluir e remover obras, registrar e acompanhar empréstimos, criar gestores, editar cadastros, ajustar a configuração de prazos e o máximo de empréstimos em paralelo de cada leitor.
- **A Maior Frustração / Dor Atual:** Não há como gerir automaticamente. O acervo e os empréstimos são controlados na mão.
- **O Workaround (A Gambiarra Atual):** Controle manual do acervo e dos empréstimos. No briefing, esse controle aparece como agendas em papel e fichas catalográficas em papel.

---

## 2. Persona 2: Leitor — consulta aberta

- **Perfil e Rotina:** Pessoa que consulta o acervo disponível. Não faz login nem cadastro preliminar. O acesso é uma página pública para ver a disponibilidade do acervo. Não cadastra obra, não registra empréstimo e não configura prazo.
- **Objetivo Principal no Sistema:** Saber quais obras estão disponíveis, pela página pública de consulta.
- **A Maior Frustração / Dor Atual:** Não há como pesquisar. Só dá para investigar manualmente quais itens do acervo estão disponíveis.
- **O Workaround (A Gambiarra Atual):** Investigação manual dos itens disponíveis.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Há entre 2 e 5 personas documentadas?
[ ] Cada persona possui papel, rotina, objetivo e frustração clara? Sem nome fictício.
[ ] O workaround (a gambiarra que usam hoje) foi identificado para todas as personas?
-->
