# Wireflow: F002 Cadastrar usuário e senha do gestor

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F002` - Cadastrar usuário e senha do gestor
- **Passos de origem:** 1. Abrir a área de gestão de usuários. 2. Escolher cadastrar gestor. 3. Informar o usuário do novo gestor. 4. Informar a senha do novo gestor. 5. Concluir o cadastro do gestor. 6. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-02]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F002-cadastrar-usuario-e-senha-do-gestor.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Título, passo, seta e nota ficam fora.

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
        | Escolher cadastrar gestor
        v
Frame B - Cadastro do gestor
Passos 3 a 6. Informar o usuário e a senha, concluir e ver a mensagem
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Usuário                                                      |
| [                                                          ] |
| Senha                                                        |
| [                                                          ] |
| [ Concluir cadastro ]                                        |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+

Fora do frame: o primeiro gestor não nasce aqui. A senha não entra no log.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de usuários | Biblioteca Limoeiro | Barra | Topo da página | `F002` | Barra da página. A mesma barra volta no Frame B. |
| Frame A - Área de gestão de usuários | Acervo, Usuários, Empréstimos, Relatórios | Navegação | Na barra, à direita | `F002` | Quatro áreas da tela inicial. Usuários fica em realce: é a área deste wireflow. |
| Frame A - Área de gestão de usuários | Usuários | Título | Abaixo da barra, à esquerda | `F002` | Passo 1. Área de gestão de usuários. |
| Frame A - Área de gestão de usuários | Cadastrar gestor | Botão | Abaixo do título | `F002` | Passo 2. A seta abre o cadastro do gestor. |
| Frame A - Área de gestão de usuários | Cadastrar leitor | Botão | Ao lado de Cadastrar gestor | `F002` | Está na área. O cadastro do leitor é `F012`. |
| Frame A - Área de gestão de usuários | Nome, CPF | Cabeçalho | Abaixo dos botões | `F002` | Lista sem linhas. Não há dado simulado. |
| Seta A para B | Escolher cadastrar gestor | Seta | Faixa entre os frames | `F002` | Passo 2. A ponta toca a borda do Frame B. |
| Frame B - Cadastro do gestor | Usuário | Campo vazio | Abaixo da barra | `F002` | Passo 3. Caixa sem valor. Usuário é a credencial. |
| Frame B - Cadastro do gestor | Senha | Campo vazio | Abaixo de Usuário | `F002` | Passo 4. Caixa sem valor. A senha não entra no log. `[RN-14]` |
| Frame B - Cadastro do gestor | Concluir cadastro | Botão primário | Abaixo dos campos | `F002` | Passo 5. Só o gestor autenticado conclui. `[RN-02]` |
| Frame B - Cadastro do gestor | operação feita com sucesso | Linha | Abaixo do botão | `F002` | Passo 6. A mensagem representa o log da inclusão, com valor anterior vazio e sem a senha. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** A lista da área não traz linhas e as caixas de Usuário e Senha ficam sem valor. `[CONFIRMAR]` como a área aparece quando ainda não há outro gestor além do primeiro.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** O primeiro gestor não nasce aqui. Essa criação não gera log. A senha não entra no log. `[RN-14]` Só o gestor autenticado cadastra outro gestor. `[RN-02]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador. A página é a área de usuários e, em seguida, o cadastro com usuário e senha. A estrutura é a mesma de F003.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Estado da área quando só existe o primeiro gestor, e o carregamento.
