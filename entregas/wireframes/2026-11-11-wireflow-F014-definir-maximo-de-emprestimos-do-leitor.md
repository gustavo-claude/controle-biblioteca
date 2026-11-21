# Wireflow: F014 Definir máximo de empréstimos em paralelo do leitor

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F014` - Definir máximo de empréstimos em paralelo do leitor
- **Passos de origem:** 1. Abrir o formulário do leitor, no cadastro ou na edição. 2. Informar o máximo de empréstimos em paralelo. 3. Se o valor é menor que 2: 3a. Recusar a mudança e permanecer no formulário. Senão, se o leitor já tem mais empréstimos em paralelo do que o novo valor: 3b. Manter o máximo anterior e indicar que a mudança só vale depois da devolução ou do encerramento por extravio de ao menos um. Senão: 3c. Gravar o novo máximo. 4. Ver a mensagem operação feita com sucesso, quando a mudança é gravada ou fica aguardando.
- **Regras vinculadas:** `[RN-05]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F014-definir-maximo-de-emprestimos-do-leitor.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Título, passo, seta e nota ficam fora. O formulário é o de F012. O rótulo do máximo fica em realce. A recusa e a espera não abrem outra página.

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
Passos 2 a 4. Informar o máximo e ver a mensagem quando grava ou aguarda
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

Fora do frame: o padrão é 2. Abaixo de 2 não grava.
Se a redução esbarra em empréstimos em aberto, vale o máximo anterior
até a devolução ou o encerramento por extravio.
```

O rótulo Máximo de empréstimos em paralelo é o que está em realce. Na edição, o botão da mesma estrutura é Concluir a edição, como em F013.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de usuários | Biblioteca Limoeiro | Barra | Topo da página | `F014` | Barra da página. A mesma barra volta no Frame B. |
| Frame A - Área de gestão de usuários | Acervo, Usuários, Empréstimos, Relatórios | Navegação | Na barra, à direita | `F014` | Usuários fica em realce. |
| Frame A - Área de gestão de usuários | Usuários | Título | Abaixo da barra, à esquerda | `F014` | A área de onde o formulário abre, no cadastro ou na edição. |
| Frame A - Área de gestão de usuários | Cadastrar gestor, Cadastrar leitor | Botões | Abaixo do título | `F014` | Estão na área. O formulário do leitor abre no cadastro (`F012`) ou na edição (`F013`). |
| Frame A - Área de gestão de usuários | Nome, CPF | Cabeçalho | Abaixo dos botões | `F014` | Lista sem linhas. Não há dado simulado. |
| Seta A para B | Abrir o formulário do leitor | Seta | Faixa entre os frames | `F014` | Passo 1. Abre o mesmo formulário de F012. |
| Frame B - Formulário do leitor | Nome, CPF, Telefone, Endereço, Prazo | Campos vazios | Mesma ordem de F012 | `F014` | Permanecem no formulário. O foco deste wireflow é o máximo. |
| Frame B - Formulário do leitor | Máximo de empréstimos em paralelo | Campo vazio, rótulo em realce | Terceira linha, à esquerda | `F014` | Passo 2. Caixa sem valor. O padrão é 2. `[RN-05]` |
| Frame B - Formulário do leitor | Concluir cadastro | Botão primário | Abaixo dos campos | `F014` | Botão do formulário de F012. Na edição, F013 usa Concluir a edição na mesma estrutura. |
| Frame B - Formulário do leitor | operação feita com sucesso | Linha | Abaixo do botão | `F014` | Passo 4. Aparece quando a mudança é gravada ou fica aguardando. O log guarda o valor anterior, o valor pedido e se passou a valer ou ficou aguardando. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** As caixas ficam sem valor neste esboço. O padrão 2 não está desenhado dentro da caixa, para não simular um leitor.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Valor abaixo de 2 é recusado, não é gravado e não mostra a mensagem. `[RN-05]` A recusa sem gravação não gera log. `[RN-14]` Empréstimo devolvido e Encerrado por extravio não entram na conta. Empréstimo ativo ou atrasado entra. Se a redução, sem ficar abaixo de 2, esbarra em empréstimos em aberto, vale o máximo anterior até a devolução ou o encerramento por extravio de ao menos um. `[RN-05]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador. Não há tela própria. O campo está no formulário do leitor, com o rótulo em realce. Padrão, recusa e espera ficam fora da página.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Carregamento.
