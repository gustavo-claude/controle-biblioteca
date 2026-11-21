# Wireflow: F005 Cadastrar obra do acervo

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F005` - Cadastrar obra do acervo
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Escolher adicionar obra. 3a. Sem tipo, voltar à área e encerrar. 3b. Livro. 3c. HQ. 3d. Revista. 3e. Brinquedo. 3f. Outro. 4. Concluir o cadastro da obra. 5. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-12]`, `[RN-14]`, `[DEC-05]`
- **Rodadas com o operador:** 7 de 7, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F005-cadastrar-obra-do-acervo.svg`

Escolhas do orquestrador no papel de operador. Frame A é a área de gestão do acervo. Os ramos de C a G são alternativos. Sem tipo, o gestor volta à área: isso fica fora da página, sem quadro de recusa.

---

## 1. Wireflow em ASCII

```text
Passo 1 - Abrir a área de gestão do acervo
+------------------------------------------------------------------+
| Frame A - Área de gestão do acervo                               |
| Biblioteca Limoeiro | Acervo | Usuários | Empréstimos | Relatórios |
| Acervo                                                           |
| [Adicionar obra]  [Pesquisar acervo]                             |
| Tipo | Título ou nome                                            |
| Código do exemplar | Situação                                    |
+------------------------------------------------------------------+
        |
        | Escolher adicionar obra
        v
Passo 2 - Escolher adicionar obra
+------------------------------------------------------------------+
| Frame B - Tipo da obra                                           |
| [Livro] [Revista] [HQ] [Brinquedo] [Outro]                       |
+------------------------------------------------------------------+
Sem tipo, o gestor volta à área de gestão do acervo.

        | Tipo livro          | Tipo HQ           | Tipo revista
        v                     v                   v
+------------------+  +------------------+  +------------------+
| Frame C - Livro  |  | Frame D - HQ     |  | Frame E - Revista|
| campos do livro  |  | campos da HQ     |  | campos da revista|
| [Concluir cadastro] | [Concluir cadastro] | [Concluir cadastro]
| operação feita com sucesso                                    |
+------------------+  +------------------+  +------------------+

        | Tipo brinquedo                         | Tipo outro
        v                                        v
+---------------------------+    +---------------------------+
| Frame F - Brinquedo       |    | Frame G - Outro           |
| [Concluir cadastro]       |    | [Concluir cadastro]       |
| operação feita com sucesso|    | operação feita com sucesso|
+---------------------------+    +---------------------------+

Fora de C a G: a obra guarda a data, a hora e o gestor responsável.
Não cria o exemplar.
Fora de F: a faixa etária não bloqueia o empréstimo.
Fora de G: sem nome livre além desses campos.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro | Barra | Topo da página | `F005` | Barra comum. Acervo em destaque. |
| Frame A - Área de gestão do acervo | Acervo, Usuários, Empréstimos, Relatórios | Áreas | Barra | `F005` | Acervo é a área deste wireflow. |
| Frame A - Área de gestão do acervo | Acervo | Título da página | Abaixo da barra | `F005` | Passo 1. |
| Frame A - Área de gestão do acervo | Adicionar obra | Botão primário | Ações | `F005` | Passo 2. Abre o Frame B. |
| Frame A - Área de gestão do acervo | Pesquisar acervo | Botão | Ao lado de Adicionar obra | `F010` | Permanece na área. Este wireflow não abre a pesquisa. |
| Frame A - Área de gestão do acervo | Tipo, Título ou nome | Cabeçalho de lista | Lista de obras, sem linhas | `F005` | Lista vazia neste esboço. |
| Frame A - Área de gestão do acervo | Código do exemplar, Situação | Cabeçalho de lista | Segunda lista, sem linhas | `F005` | Lista vazia neste esboço. O exemplar é `F008`. |
| Frame B - Tipo da obra | Livro, Revista, HQ, Brinquedo, Outro | Botões iguais | Faixa de tipos | `F005` | Passo 2. Cada um abre o formulário do tipo. `[RN-12]` |
| Frame B - Tipo da obra | Sem tipo, o gestor volta à área de gestão do acervo. | Texto fora da página | Ao lado do Frame B | `F005` | Passo 3a. Não é quadro. Não gera log. `[RN-12]` |
| Frame C - Formulário do livro | Título, Autor, Editora, ISBN, Ano, Gênero, Categoria, Assunto, Quantidade de exemplares | Campo vazio | Formulário | `F005` | Passo 3b. `[RN-12]` |
| Frame D - Formulário da HQ | Título, Autor, Ano de publicação, Número da edição, Editora, Quantidade de exemplares | Campo vazio | Formulário | `F005` | Passo 3c. `[RN-12]` |
| Frame E - Formulário da revista | Título, Ano de publicação, Número da edição, Editora, Quantidade de exemplares | Campo vazio | Formulário | `F005` | Passo 3d. Revista não tem autor. `[RN-12]` |
| Frame F - Formulário do brinquedo | Nome, Descrição, Fabricante, Faixa etária indicada, Quantidade de exemplares | Campo vazio | Formulário | `F005` | Passo 3e. `[RN-12]` |
| Frame F - Formulário do brinquedo | A faixa etária não bloqueia o empréstimo. | Texto fora da página | Abaixo do Frame F | `F005` | `[DEC-05]` |
| Frame G - Formulário de outro | Nome, Descrição, Quantidade de exemplares | Campo vazio | Formulário | `F005` | Passo 3f. `[RN-12]` |
| Frame G - Formulário de outro | Sem nome livre além desses campos. | Texto fora da página | Abaixo do Frame G | `F005` | `[RN-12]` |
| Frames C a G | Concluir cadastro | Botão primário | Abaixo dos campos | `F005` | Passo 4. |
| Frames C a G | operação feita com sucesso | Mensagem | Abaixo do botão | `F005` | Passo 5. Representa o log de inclusão. `[RN-14]` |
| Frames C a G | A obra guarda a data, a hora e o gestor responsável. Não cria o exemplar. | Texto fora da página | Abaixo dos formulários | `F005` | `[RN-12]`. O exemplar com código é `F008`. |

---

## 3. Estados da Interface

- **Estado vazio:** As duas listas da área mostram só o cabeçalho, sem linha de obra nem de exemplar. Os campos dos formulários ficam em branco.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Sem tipo, o gestor volta à área e o cadastro não se conclui. Essa volta não é quadro e não gera log. A faixa etária indicada não bloqueia o empréstimo (`[DEC-05]`). Outro não pede nome livre além de nome e descrição.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Se a quantidade de exemplares informada na obra precisa coincidir com os exemplares cadastrados em `F008`.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] Pesquisar acervo permanece na área. A pesquisa é `F010`.
