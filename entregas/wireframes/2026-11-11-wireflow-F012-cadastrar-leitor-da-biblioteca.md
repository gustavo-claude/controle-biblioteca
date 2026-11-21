# Wireflow: F012 Cadastrar leitor da biblioteca

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F012` - Cadastrar leitor da biblioteca
- **Passos de origem:** 1. Abrir a área de gestão de usuários. 2. Escolher cadastrar leitor. 3. Informar nome, CPF, telefone, endereço, máximo de empréstimos em paralelo e prazo. 4. Se faltar nome ou CPF, ou o CPF já estiver usado por outro leitor: 4a. Recusar o cadastro e permanecer no formulário. Senão: 4b. Concluir o cadastro do leitor. 5. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-02]`, `[RN-05]`, `[RN-11]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F012-cadastrar-leitor-da-biblioteca.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Título, passo, seta e nota ficam fora. A recusa não abre outra página.

```text
Frame A - Área de gestão de usuários
Passo 1. Abrir a área de gestão de usuários
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Usuários                                                     |
| [ Cadastrar gestor ]  [ Cadastrar leitor ]                   |
| Nome                      CPF                                |
+--------------------------------------------------------------+
        |
        | Escolher cadastrar leitor
        v
Frame B - Formulário do leitor
Passos 3 a 5. Informar os campos, concluir e ver a mensagem
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Nome                         CPF                             |
| [                          ] [                            ]  |
| Telefone                     Endereço                        |
| [                          ] [                            ]  |
| Máximo de empréstimos em paralelo    Prazo                  |
| [                          ] [                            ]  |
| [ Concluir cadastro ]                                        |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+

Fora do frame: telefone e endereço são opcionais. O nome não é conferido com o CPF.
Sem nome, sem CPF ou com CPF repetido, o cadastro permanece neste formulário.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de usuários | Biblioteca Limoeiro | Barra | Topo da página | `F012` | Barra da página. A mesma barra volta no Frame B. |
| Frame A - Área de gestão de usuários | Acervo, Usuários, Empréstimos, Relatórios | Navegação | Na barra, à direita | `F012` | Usuários fica em realce. |
| Frame A - Área de gestão de usuários | Usuários | Título | Abaixo da barra, à esquerda | `F012` | Passo 1. Área de gestão de usuários. |
| Frame A - Área de gestão de usuários | Cadastrar gestor | Botão | Abaixo do título | `F012` | Está na área. O cadastro do gestor é `F002`. |
| Frame A - Área de gestão de usuários | Cadastrar leitor | Botão | Ao lado de Cadastrar gestor | `F012` | Passo 2. A seta abre o formulário do leitor. |
| Frame A - Área de gestão de usuários | Nome, CPF | Cabeçalho | Abaixo dos botões | `F012` | Lista sem linhas. Não há dado simulado. |
| Seta A para B | Escolher cadastrar leitor | Seta | Faixa entre os frames | `F012` | Passo 2. Abre o formulário compartilhado com F013. |
| Frame B - Formulário do leitor | Nome | Campo vazio | Primeira linha, à esquerda | `F012` | Passo 3. Obrigatório. Pode ser apelido ou nome social. Não é conferido com o CPF. `[RN-11]` |
| Frame B - Formulário do leitor | CPF | Campo vazio | Primeira linha, à direita | `F012` | Passo 3. Obrigatório e único entre leitores. `[RN-11]` |
| Frame B - Formulário do leitor | Telefone | Campo vazio | Segunda linha, à esquerda | `F012` | Passo 3. Opcional. `[RN-11]` |
| Frame B - Formulário do leitor | Endereço | Campo vazio | Segunda linha, à direita | `F012` | Passo 3. Opcional. `[RN-11]` |
| Frame B - Formulário do leitor | Máximo de empréstimos em paralelo | Campo vazio | Terceira linha, à esquerda | `F012` | Passo 3. Campo de `F014`. Nasce em 2. `[RN-05]` |
| Frame B - Formulário do leitor | Prazo | Campo vazio | Terceira linha, à direita | `F012` | Passo 3. Campo de `F015`. O prazo é deste leitor. A lista diverge de `[RN-06]`. |
| Frame B - Formulário do leitor | Concluir cadastro | Botão primário | Abaixo dos campos | `F012` | Passo 4b. Só o gestor autenticado conclui. `[RN-02]` |
| Frame B - Formulário do leitor | operação feita com sucesso | Linha | Abaixo do botão | `F012` | Passo 5. A mensagem representa o log da inclusão, com valor anterior vazio. A recusa do passo 4a não mostra esta linha e não gera log. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** O formulário abre com as caixas sem valor. A lista da área não traz linhas neste esboço.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Sem nome, sem CPF ou com CPF já usado por outro leitor, o cadastro permanece neste formulário. Telefone e endereço podem ficar em branco. O nome não é conferido com o CPF. `[RN-11]` A recusa sem gravação não gera log. `[RN-14]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador. Os seis campos ficam no mesmo formulário, na ordem nome, CPF, telefone, endereço, máximo de empréstimos em paralelo e prazo. A recusa não troca de página.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Carregamento.
> - [ ] `[CONFIRMAR]` A unidade do prazo e se a mudança recalcula empréstimo ativo ou atrasado. O campo está neste formulário; o detalhe é o de `F015`.
