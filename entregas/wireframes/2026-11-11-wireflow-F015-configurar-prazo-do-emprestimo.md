# Wireflow: F015 Configurar prazo do empréstimo

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F015` - Configurar prazo do empréstimo
- **Passos de origem:** 1. Abrir o formulário do leitor, no cadastro ou na edição. 2. Informar o prazo daquele leitor. 3. Gravar o formulário. 4. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-14]`. A descrição diverge de `[RN-06]`.
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F015-configurar-prazo-do-emprestimo.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Título, passo, seta e nota ficam fora. O formulário é o de F012. O rótulo Prazo fica em realce.

```text
Frame A - Área de gestão de usuários
Passo 1. Abrir o formulário do leitor, no cadastro ou na edição
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Usuários                                                     |
| [ Cadastrar gestor ]  [ Cadastrar leitor ]                   |
| Nome                      CPF                                |
+--------------------------------------------------------------+
        |
        | Abrir o formulário do leitor
        v
Frame B - Formulário do leitor
Passos 2 a 4. Informar o prazo deste leitor, gravar e ver a mensagem
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

Fora do frame: o prazo é deste leitor. Não há quantidade fixa de dias.
A unidade está em [CONFIRMAR]. Diverge de [RN-06].
```

O rótulo Prazo é o que está em realce. Na edição, o botão da mesma estrutura é Concluir a edição, como em F013.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de usuários | Biblioteca Limoeiro | Barra | Topo da página | `F015` | Barra da página. A mesma barra volta no Frame B. |
| Frame A - Área de gestão de usuários | Acervo, Usuários, Empréstimos, Relatórios | Navegação | Na barra, à direita | `F015` | Usuários fica em realce. |
| Frame A - Área de gestão de usuários | Usuários | Título | Abaixo da barra, à esquerda | `F015` | A área de onde o formulário abre, no cadastro ou na edição. |
| Frame A - Área de gestão de usuários | Cadastrar gestor, Cadastrar leitor | Botões | Abaixo do título | `F015` | Estão na área. O formulário do leitor abre no cadastro (`F012`) ou na edição (`F013`). |
| Frame A - Área de gestão de usuários | Nome, CPF | Cabeçalho | Abaixo dos botões | `F015` | Lista sem linhas. Não há dado simulado. |
| Seta A para B | Abrir o formulário do leitor | Seta | Faixa entre os frames | `F015` | Passo 1. Abre o mesmo formulário de F012. |
| Frame B - Formulário do leitor | Nome, CPF, Telefone, Endereço, Máximo de empréstimos em paralelo | Campos vazios | Mesma ordem de F012 | `F015` | Permanecem no formulário. O foco deste wireflow é o prazo. |
| Frame B - Formulário do leitor | Prazo | Campo vazio, rótulo em realce | Terceira linha, à direita | `F015` | Passo 2. Caixa sem valor e sem unidade. O prazo é deste leitor. A data prevista de um empréstimo novo sai deste campo. Não há quantidade fixa de dias. Diverge de `[RN-06]`, que trata o prazo como configuração da biblioteca. |
| Frame B - Formulário do leitor | Concluir cadastro | Botão primário | Abaixo dos campos | `F015` | Passo 3. Botão do formulário de F012. Na edição, F013 usa Concluir a edição na mesma estrutura. |
| Frame B - Formulário do leitor | operação feita com sucesso | Linha | Abaixo do botão | `F015` | Passo 4. A mensagem representa o log. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** A caixa do prazo fica sem unidade e sem número, para não simular um prazo.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Não há quantidade fixa de dias. O passo não define recusa. `[CONFIRMAR]` a unidade do campo e se a mudança recalcula empréstimo ativo ou atrasado.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador. Não há tela de configuração da biblioteca. O prazo é campo do formulário do leitor, com o rótulo em realce. A lista prevalece sobre `[RN-06]`.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` A unidade do campo. A caixa não mostra unidade nem número.
> - [ ] `[CONFIRMAR]` Se a mudança recalcula a data prevista de empréstimo ativo ou atrasado.
> - [ ] `[CONFIRMAR]` Carregamento.
