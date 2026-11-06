# Glossário Oficial e Vocabulário Controlado

> 💡 **PAPEL DESTE ARQUIVO:**  
> Elimina ambiguidades e sinônimos no vocabulário do produto. Se a IA não souber a palavra exata da casa, ela inventará termos plausíveis que confundirão os desenvolvedores e usuários.  
> ⚠️ **REGRA DE OURO:** Se um termo tem dois nomes no dia a dia do time, escolha **um só** aqui e proíba o outro.

---

## 1. Termos Canônicos do Domínio

| Termo Oficial | Definição Precisa no Produto | O que NÃO é (Limites) |
|---|---|---|
| **Gestor** | Pessoa que administra a Biblioteca Limoeiro. É o usuário primário. Entra com login, inclui e remove livros, controla empréstimos, cria usuários e configura prazos. | Não é o leitor. Não é um segundo papel ao lado de "administrador". |
| **Leitor** | Pessoa cadastrada que toma exemplares emprestados. Consulta a disponibilidade numa página aberta, sem login. | Não é o gestor. Não opera cadastro, empréstimo nem configuração. |
| **Usuário** | Credencial de acesso (usuário e senha) de quem administra. O gestor cria usuários. | Não é sinônimo de leitor nem de gestor. A meta de "20 usuários" continua [CONFIRMAR]. |
| **Acervo** | Conjunto dos livros e dos exemplares da Biblioteca Limoeiro. | Não é estoque de loja. [CONFIRMAR] se inclui item que não é livro. |
| **Livro** | Registro do título no acervo: título, autor, editora, ISBN, ano, gênero, categoria, assunto e quantidade de exemplares. | Não é a unidade física. Não é item à venda. |
| **Exemplar** | Unidade física de um livro, com código único e uma situação: disponível, emprestado ou indisponível. É o que se empresta. | Não é o registro do livro. Não é o ISBN. |
| **Empréstimo** | Registro da retirada de um exemplar por um leitor, com data de retirada e data prevista de devolução. Cada pessoa pode ter até 3 ao mesmo tempo. | Não é venda, reserva nem doação. |
| **Devolução** | Registro feito pelo gestor que encerra o empréstimo e devolve o exemplar a disponível. | Não é suspensão. Não apaga o histórico do exemplar. |
| **Prazo** | Configuração do gestor usada para calcular a data prevista de devolução. | Não é uma quantidade fixa de dias. Não é a data de retirada. |
| **Atraso** | Empréstimo cuja data prevista de devolução passou sem devolução. | Não é, por si só, a suspensão do leitor. |
| **Suspensão** | Condição do leitor que não cumpriu o prazo, aplicada somente se essa configuração estiver ligada. | Não é status do exemplar nem do empréstimo. Duração e o que fica bloqueado: [CONFIRMAR]. |
| **Código do exemplar** | Identificador único de cada exemplar. | Não é o ISBN do livro. |

**Obra** fica de fora da lista fechada. No briefing nomeia o item do acervo, inclusive além de livro, e isso continua [CONFIRMAR]. Até lá, não substitui livro nem exemplar.

---

## 2. Palavras Proibidas e Sinônimos Banidos

> 🚫 *O assistente NUNCA deve utilizar os termos da coluna esquerda.*

| Termo Proibido (❌ Banido) | Termo Correto (✅ Usar Sempre) | Motivo da Proibição |
|---|---|---|
| *Administrador* | **Gestor** | Os dois nomes foram usados para o mesmo papel. O nome da casa é gestor. |
| *Usuário*, para quem consulta ou toma emprestado | **Leitor** | O leitor não faz login. Usuário é a credencial de quem administra. |
| *Usuário*, para quem administra | **Gestor** | O papel é o gestor. Usuário é a credencial que ele usa. |
| *Livro* ou *obra*, para a unidade física | **Exemplar** | O que se empresta, tem código e tem situação é o exemplar. |
| *Leitor atrasado* | **Empréstimo atrasado**; **leitor suspenso** só se a configuração estiver ligada | O atraso é do empréstimo. A suspensão é condição do leitor. |

---

## 3. Catálogo Fechado de Status Oficiais

> 🔒 *Estes são os ÚNICOS status válidos do exemplar e do empréstimo. A IA está expressamente proibida de inventar outros estados. Suspensão é condição do leitor, não um status destas duas entidades.*

| Status | Significado do Estado | Quem pode mover para cá |
|---|---|---|
| **Exemplar: Disponível** | Exemplar na biblioteca, apto a ser emprestado | Gestor, ao registrar a devolução. Situação no cadastro do exemplar: [CONFIRMAR]. |
| **Exemplar: Emprestado** | Exemplar retirado por um leitor, com empréstimo ativo ou atrasado | Gestor, ao registrar o empréstimo, somente a partir de disponível |
| **Exemplar: Indisponível** | Exemplar que não pode ser emprestado e não está em empréstimo | [CONFIRMAR] quem move para cá e a partir de qual status |
| **Empréstimo: Ativo** | Empréstimo em aberto, dentro do prazo | Sistema, quando o gestor registra o empréstimo |
| **Empréstimo: Atrasado** | A data prevista passou e não houve devolução | Sistema, ao passar a data prevista |
| **Empréstimo: Devolvido** | Devolução registrada; o exemplar volta a disponível | Gestor, ao registrar a devolução |

---

## 4. Matriz de Transições de Estado Permitidas

```
Exemplar
[Disponível] ── gestor registra o empréstimo ──► [Emprestado]
[Emprestado] ── gestor registra a devolução ──► [Disponível]
[Indisponível] ── [CONFIRMAR] quem move, e de qual status

Empréstimo
(registro do gestor) ──► [Ativo] ── sistema, ao vencer a data prevista ──► [Atrasado]
                            │                                                      │
                            └──────────── gestor registra a devolução ────────────┴──► [Devolvido]
```

Não há passagem de empréstimo atrasado de volta para ativo. Não há empréstimo de exemplar que não esteja disponível. Nenhuma destas passagens tem exceção autorizada.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todos os termos chave do domínio foram definidos?
[ ] Há lista explícita de termos proibidos e seus substitutos?
[ ] Os status estão 100% fechados (sem margem para estados inventados)?
-->
