# Wireflow: F003 Editar cadastro do gestor

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F003` - Editar cadastro do gestor
- **Passos de origem:** 1. Abrir a área de gestão de usuários. 2. Identificar o gestor. 3. Alterar usuário ou senha na mesma estrutura do cadastro. 4. Concluir a edição do cadastro. 5. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-02]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F003-editar-cadastro-do-gestor.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Título, passo, seta e nota ficam fora. O Frame B é a mesma página do cadastro de F002.

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
        | Identificar o gestor
        v
Frame B - Cadastro do gestor
Passos 3 a 5. Alterar usuário ou senha, concluir e ver a mensagem
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Usuário                                                      |
| [                                                          ] |
| Senha                                                        |
| [                                                          ] |
| [ Concluir a edição ]                                        |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+

Fora do frame: a mesma estrutura de F002. A senha não entra no log.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de usuários | Biblioteca Limoeiro | Barra | Topo da página | `F003` | Barra da página. A mesma barra volta no Frame B. |
| Frame A - Área de gestão de usuários | Acervo, Usuários, Empréstimos, Relatórios | Navegação | Na barra, à direita | `F003` | Usuários fica em realce. |
| Frame A - Área de gestão de usuários | Usuários | Título | Abaixo da barra, à esquerda | `F003` | Passo 1. Área de gestão de usuários. |
| Frame A - Área de gestão de usuários | Cadastrar gestor | Botão | Abaixo do título | `F003` | Está na área. O cadastro novo é `F002`. |
| Frame A - Área de gestão de usuários | Cadastrar leitor | Botão | Ao lado de Cadastrar gestor | `F003` | Está na área. O cadastro do leitor é `F012`. |
| Frame A - Área de gestão de usuários | Nome, CPF | Cabeçalho | Abaixo dos botões | `F003` | Lista sem linhas. A identificação não usa dado simulado. |
| Seta A para B | Identificar o gestor | Seta | Faixa entre os frames | `F003` | Passo 2. Abre a mesma estrutura do cadastro. |
| Frame B - Cadastro do gestor | Usuário | Campo vazio | Abaixo da barra | `F003` | Passo 3. Mesma caixa de F002, sem valor neste esboço. |
| Frame B - Cadastro do gestor | Senha | Campo vazio | Abaixo de Usuário | `F003` | Passo 3. A senha não entra no log. `[RN-14]` |
| Frame B - Cadastro do gestor | Concluir a edição | Botão primário | Abaixo dos campos | `F003` | Passo 4. Só o gestor autenticado conclui. `[RN-02]` |
| Frame B - Cadastro do gestor | operação feita com sucesso | Linha | Abaixo do botão | `F003` | Passo 5. A mensagem representa o log da edição, sem a senha. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** A lista não traz linhas e as caixas ficam sem valor neste esboço. `[CONFIRMAR]`
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** A edição usa a mesma estrutura do cadastro. A senha não entra no log. O primeiro gestor não nasce nesta página. `[RN-14]` Só o gestor autenticado edita. `[RN-02]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador. A página de edição é a do cadastro. Muda o botão: Concluir a edição. A mensagem é a mesma.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Estado vazio e carregamento.
