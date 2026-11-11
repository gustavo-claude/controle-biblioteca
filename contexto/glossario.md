# Glossário Oficial e Vocabulário Controlado

> 💡 **PAPEL DESTE ARQUIVO:**  
> Elimina ambiguidades e sinônimos no vocabulário do produto. Se a IA não souber a palavra exata da casa, ela inventará termos plausíveis que confundirão os desenvolvedores e usuários.  
> ⚠️ **REGRA DE OURO:** Se um termo tem dois nomes no dia a dia do time, escolha **um só** aqui e proíba o outro.

---

## 1. Termos Canônicos do Domínio

| Termo Oficial | Definição Precisa no Produto | O que NÃO é (Limites) |
|---|---|---|
| **Gestor** | Pessoa que administra a Biblioteca Limoeiro. É o usuário primário. Entra com login, inclui e remove obras, controla empréstimos, cria outros gestores, edita o cadastro de gestor e de leitor, configura prazos e define, no cadastro de cada leitor, o máximo de empréstimos em paralelo. O padrão é 2 e o valor não fica abaixo de 2. Ao receber o exemplar atrasado, informa a duração da suspensão. O primeiro gestor é criado pela equipe de desenvolvimento. | Não é o leitor. Não é um segundo papel ao lado de "administrador". A equipe de desenvolvimento não é um papel do produto. |
| **Leitor** | Pessoa cadastrada que toma exemplares emprestados. Consulta a disponibilidade numa página pública, sem login e sem cadastro preliminar. O cadastro, feito pelo gestor, exige nome e CPF único. Telefone e endereço são opcionais. | Não é o gestor. Não opera cadastro, empréstimo nem configuração. O nome não é conferido com o CPF. |
| **Usuário** | Credencial de acesso (usuário e senha) de quem administra. O gestor cria usuários. A meta do ciclo é 5 gestores e 20 leitores. | Não é sinônimo de leitor nem de gestor. |
| **Acervo** | Conjunto das obras e dos exemplares da Biblioteca Limoeiro. | Não é estoque de loja. |
| **Obra** | Registro do item no acervo. O tipo é obrigatório: livro, revista, HQ, brinquedo ou outro. Os dados são os do tipo. Toda obra guarda a quantidade de exemplares, a data e a hora da inclusão e o gestor responsável. Na remoção, guarda a data e o gestor responsável pela remoção. | Não é a unidade física. Não é item à venda. Gênero, categoria e assunto valem só para o livro. |
| **Livro** | Tipo de obra. Dados: título, autor, editora, ISBN, ano, gênero, categoria, assunto e quantidade de exemplares. | Não é a unidade física. Não nomeia revista, HQ, brinquedo nem outro. |
| **HQ** | Tipo de obra. Dados: título, autor, ano de publicação, número da edição, editora e quantidade de exemplares. | Não é livro. Não traz gênero, categoria, assunto nem ISBN. |
| **Revista** | Tipo de obra. Dados: título, ano de publicação, número da edição, editora e quantidade de exemplares. | Não é livro. Não tem autor, gênero, categoria nem assunto. |
| **Brinquedo** | Tipo de obra. Dados: nome, descrição, fabricante, faixa etária indicada e quantidade de exemplares. | Não é livro. Não tem título nem autor. A faixa etária indicada não bloqueia o empréstimo. |
| **Outro** | Tipo de obra. Dados: nome, descrição e quantidade de exemplares. | Não pede um nome livre além de nome e descrição. |
| **Exemplar** | Unidade física de uma obra, com código único e uma situação: disponível, emprestado ou indisponível. No cadastro, nasce disponível. É o que se empresta. | Não é o registro da obra. Não é o ISBN. |
| **Empréstimo** | Registro da retirada de um exemplar por um leitor, com data de retirada e data prevista de devolução. O padrão em paralelo é 2; o gestor pode aumentar no cadastro daquele leitor e não pode ficar abaixo de 2. O leitor não empresta dois exemplares da mesma obra ao mesmo tempo. | Não é venda, reserva nem doação. O título não identifica a obra para esse limite. |
| **Devolução** | Registro feito pelo gestor que encerra o empréstimo e devolve o exemplar a disponível. | Não é suspensão. Não apaga o histórico do exemplar. Não é extravio. |
| **Prazo** | Configuração do gestor usada para calcular a data prevista de devolução. | Não é uma quantidade fixa de dias. Não é a data de retirada. Não é a duração da suspensão. |
| **Atraso** | Empréstimo cuja data prevista de devolução passou sem devolução. | Não é, por si só, a suspensão do leitor. |
| **Suspensão** | Condição do leitor que não cumpriu o prazo, aplicada somente se essa configuração estiver ligada. A duração é informada pelo gestor que recebe o exemplar atrasado e encerra sozinha ao fim dessa duração. Enquanto valer, o gestor não aceita novo empréstimo para esse leitor. | Não é status do exemplar nem do empréstimo. |
| **Extravio** | Motivo pelo qual o gestor encerra o empréstimo. O empréstimo fica Encerrado por extravio, o exemplar fica indisponível e deixa de contar para o máximo em paralelo. | Não é status do exemplar. Não é devolução. |
| **Log** | Registro da ação do gestor que altera cadastro, configuração, status de exemplar ou de empréstimo, ou que emite relatório. Guarda data e hora, o gestor, a ação, o que mudou, a identificação, o valor anterior e o valor novo. Na inclusão, o valor anterior fica vazio. Na remoção, o valor novo é a remoção. No relatório, guarda o recorte. A senha não entra. | Não é o histórico de empréstimo. Não é a data de inclusão da obra. Consulta, pesquisa, painel, recusa sem gravação, atraso automático, fim automático da suspensão e a criação do primeiro gestor não geram log. |
| **Código do exemplar** | Identificador único de cada exemplar, atribuído e guardado no sistema. Não é calculado a partir de ISBN nem de outro dado externo. | Não é o ISBN. Não é a chave da obra: dois exemplares da mesma obra não compartilham o código. |
| **Título** | Nome usado nos tipos livro, HQ e revista. Duas obras podem ter o mesmo título. | Não é o exemplar. Não distingue a obra no empréstimo. Brinquedo e outro usam nome, não título. |
| **Leitor com empréstimo nos últimos 6 meses** | Leitor com ao menos um empréstimo cuja data de retirada está nos 6 meses anteriores à consulta do painel. | Não é todo leitor cadastrado. Não é a suspensão. |

---

## 2. Palavras Proibidas e Sinônimos Banidos

> 🚫 *O assistente NUNCA deve utilizar os termos da coluna esquerda.*

| Termo Proibido (❌ Banido) | Termo Correto (✅ Usar Sempre) | Motivo da Proibição |
|---|---|---|
| *Administrador* | **Gestor** | Os dois nomes foram usados para o mesmo papel. O nome da casa é gestor. |
| *Usuário*, para quem consulta ou toma emprestado | **Leitor** | O leitor não faz login. Usuário é a credencial de quem administra. |
| *Usuário*, para quem administra | **Gestor** | O papel é o gestor. Usuário é a credencial que ele usa. |
| *Livro* ou *obra*, para a unidade física | **Exemplar** | O que se empresta, tem código e tem situação é o exemplar. |
| *Livro*, para revista, HQ, brinquedo ou outro | **Obra**, com o tipo | Livro é um tipo. O registro do item, em qualquer tipo, é a obra. |
| *Volume* ou *peça*, para a unidade física | **Exemplar** | O que se empresta é o exemplar. |
| *Autor da remoção* | **Gestor responsável pela remoção** | Autor é dado do livro e da HQ. Quem remove a obra é o gestor. |
| *Leitor atrasado* | **Empréstimo atrasado**; **leitor suspenso** só se a configuração estiver ligada | O atraso é do empréstimo. A suspensão é condição do leitor. |

---

## 3. Catálogo Fechado de Status Oficiais

> 🔒 *Estes são os ÚNICOS status válidos do exemplar e do empréstimo. A IA está expressamente proibida de inventar outros estados. Suspensão é condição do leitor, não um status destas duas entidades. Extravio não é status do exemplar: no empréstimo, o status é Encerrado por extravio.*

| Status | Significado do Estado | Quem pode mover para cá |
|---|---|---|
| **Exemplar: Disponível** | Exemplar na biblioteca, apto a ser emprestado | Nasce assim no cadastro. Volta para cá quando o gestor registra a devolução ou o retorno a disponibilidade. |
| **Exemplar: Emprestado** | Exemplar retirado por um leitor, com empréstimo ativo ou atrasado | Gestor, ao registrar o empréstimo, somente a partir de disponível |
| **Exemplar: Indisponível** | Exemplar que não pode ser emprestado e não está disponível para retirada | Gestor, ao registrar a indisponibilidade a partir de disponível, ou ao encerrar o empréstimo por extravio a partir de emprestado |
| **Empréstimo: Ativo** | Empréstimo em aberto, dentro do prazo | Sistema, quando o gestor registra o empréstimo |
| **Empréstimo: Atrasado** | A data prevista passou e não houve devolução | Sistema, ao passar a data prevista |
| **Empréstimo: Devolvido** | Devolução registrada; o exemplar volta a disponível | Gestor, ao registrar a devolução, a partir de ativo ou atrasado |
| **Empréstimo: Encerrado por extravio** | Empréstimo encerrado porque o exemplar foi extraviado; o exemplar fica indisponível | Gestor, a partir de ativo ou atrasado |

---

## 4. Matriz de Transições de Estado Permitidas

```
Exemplar
[Disponível] ── gestor registra o empréstimo ──► [Emprestado]
[Emprestado] ── gestor registra a devolução ──► [Disponível]
[Disponível] ── gestor registra a indisponibilidade ──► [Indisponível]
[Indisponível] ── gestor registra o retorno a disponibilidade ──► [Disponível]
[Emprestado] ── gestor encerra o empréstimo por extravio ──► [Indisponível]

Empréstimo
(registro do gestor) ──► [Ativo] ── sistema, ao vencer a data prevista ──► [Atrasado]
                            │                                                      │
                            ├──────────── gestor registra a devolução ────────────┴──► [Devolvido]
                            │                                                      │
                            └────── gestor encerra por extravio ─────────────────┴──► [Encerrado por extravio]
```

Não há passagem de empréstimo atrasado de volta para ativo. Não há passagem de Encerrado por extravio para ativo, atrasado ou devolvido. Não há empréstimo de exemplar que não esteja disponível. A volta do indisponível a disponível é o retorno a disponibilidade, feito pelo gestor. Nenhuma destas passagens tem exceção autorizada.

---

<!--
📋 CHECKLIST DE VALIDAÇÃO DESTE ARQUIVO:
[ ] Todos os termos chave do domínio foram definidos?
[ ] Há lista explícita de termos proibidos e seus substitutos?
[ ] Os status estão 100% fechados (sem margem para estados inventados)?
-->
