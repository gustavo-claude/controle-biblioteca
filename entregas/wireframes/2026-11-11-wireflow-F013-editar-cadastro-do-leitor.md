# Wireflow: F013 Editar cadastro do leitor

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F013` - Editar cadastro do leitor
- **Passos de origem:** 1. Abrir a área de gestão de usuários. 2. Identificar o leitor. 3. Alterar os campos do mesmo formulário do cadastro. 4. Se faltar nome ou CPF, ou o CPF ficar usado por outro leitor: 4a. Recusar a edição e permanecer no formulário. Senão: 4b. Concluir a edição do cadastro. 5. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-02]`, `[RN-05]`, `[RN-11]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F013-editar-cadastro-do-leitor.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Título, passo, seta e nota ficam fora. O Frame B é o mesmo formulário de F012.

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
        | Identificar o leitor
        v
Frame B - Formulário do leitor
Passos 3 a 5. Alterar os campos, concluir e ver a mensagem
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
| [ Concluir a edição ]                                        |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+

Fora do frame: a mesma estrutura do cadastro.
Sem nome, sem CPF ou com CPF repetido, a edição permanece neste formulário.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de usuários | Biblioteca Limoeiro | Barra | Topo da página | `F013` | Barra da página. A mesma barra volta no Frame B. |
| Frame A - Área de gestão de usuários | Acervo, Usuários, Empréstimos, Relatórios | Navegação | Na barra, à direita | `F013` | Usuários fica em realce. |
| Frame A - Área de gestão de usuários | Usuários | Título | Abaixo da barra, à esquerda | `F013` | Passo 1. Área de gestão de usuários. |
| Frame A - Área de gestão de usuários | Cadastrar gestor | Botão | Abaixo do título | `F013` | Está na área. O cadastro do gestor é `F002`. |
| Frame A - Área de gestão de usuários | Cadastrar leitor | Botão | Ao lado de Cadastrar gestor | `F013` | Está na área. O cadastro novo é `F012`. |
| Frame A - Área de gestão de usuários | Nome, CPF | Cabeçalho | Abaixo dos botões | `F013` | Lista sem linhas. A identificação não usa dado simulado. |
| Seta A para B | Identificar o leitor | Seta | Faixa entre os frames | `F013` | Passo 2. Abre o mesmo formulário do cadastro. |
| Frame B - Formulário do leitor | Nome | Campo vazio | Primeira linha, à esquerda | `F013` | Passo 3. Continua obrigatório. Não é conferido com o CPF. `[RN-11]` |
| Frame B - Formulário do leitor | CPF | Campo vazio | Primeira linha, à direita | `F013` | Passo 3. Continua único. `[RN-11]` |
| Frame B - Formulário do leitor | Telefone | Campo vazio | Segunda linha, à esquerda | `F013` | Passo 3. Opcional. `[RN-11]` |
| Frame B - Formulário do leitor | Endereço | Campo vazio | Segunda linha, à direita | `F013` | Passo 3. Opcional. `[RN-11]` |
| Frame B - Formulário do leitor | Máximo de empréstimos em paralelo | Campo vazio | Terceira linha, à esquerda | `F013` | Passo 3. Campo de `F014`. `[RN-05]` |
| Frame B - Formulário do leitor | Prazo | Campo vazio | Terceira linha, à direita | `F013` | Passo 3. Campo de `F015`. A lista diverge de `[RN-06]`. |
| Frame B - Formulário do leitor | Concluir a edição | Botão primário | Abaixo dos campos | `F013` | Passo 4b. Só o gestor autenticado conclui. `[RN-02]` |
| Frame B - Formulário do leitor | operação feita com sucesso | Linha | Abaixo do botão | `F013` | Passo 5. A mensagem representa o log da edição. A recusa do passo 4a não mostra esta linha e não gera log. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** As caixas deste esboço ficam sem valor e a lista da área não traz linhas. `[CONFIRMAR]` o que a edição mostra antes da alteração, porque o passo não define valor prévio na tela.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Sem nome, sem CPF ou com CPF usado por outro leitor, a edição permanece neste formulário. Telefone e endereço podem ficar em branco. O nome não é conferido com o CPF. `[RN-11]` A recusa sem gravação não gera log. `[RN-14]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador. O formulário é o de F012. Muda o botão: Concluir a edição.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Valor já gravado que a edição reapresenta, estado vazio e carregamento.
> - [ ] `[CONFIRMAR]` A unidade do prazo e se a mudança recalcula empréstimo ativo ou atrasado. O detalhe é o de `F015`.
