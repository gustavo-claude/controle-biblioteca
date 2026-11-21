# Wireflow: F026 Consultar histórico de empréstimos do leitor

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F026` - Consultar histórico de empréstimos do leitor
- **Passos de origem:** 1. Abrir a área de gestão de usuários. 2. Identificar o leitor. 3. Ver o histórico de empréstimos do leitor.
- **Regras vinculadas:** `[RN-14]`
- **Rodadas com o operador:** 3 de 3, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F026-consultar-historico-de-emprestimos-do-leitor.svg`

---

## 1. Wireflow em ASCII

O retângulo é a página. Título, passo, seta e nota ficam fora. Não há mensagem de sucesso.

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
Frame B - Histórico do leitor
Passo 3. Ver o histórico de empréstimos do leitor
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| [ Acervo ] [ Usuários ] [ Empréstimos ] [ Relatórios ]       |
|                                                              |
| Histórico de empréstimos                                     |
|                                                              |
|                                                              |
|                                                              |
+--------------------------------------------------------------+

Fora do frame: a consulta não gera log. Os dados de cada linha estão em [CONFIRMAR].
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão de usuários | Biblioteca Limoeiro | Barra | Topo da página | `F026` | Barra da página. A mesma barra volta no Frame B. |
| Frame A - Área de gestão de usuários | Acervo, Usuários, Empréstimos, Relatórios | Navegação | Na barra, à direita | `F026` | Usuários fica em realce. |
| Frame A - Área de gestão de usuários | Usuários | Título | Abaixo da barra, à esquerda | `F026` | Passo 1. Área de gestão de usuários. |
| Frame A - Área de gestão de usuários | Cadastrar gestor | Botão | Abaixo do título | `F026` | Está na área. O cadastro do gestor é `F002`. |
| Frame A - Área de gestão de usuários | Cadastrar leitor | Botão | Ao lado de Cadastrar gestor | `F026` | Está na área. O cadastro do leitor é `F012`. |
| Frame A - Área de gestão de usuários | Nome, CPF | Cabeçalho | Abaixo dos botões | `F026` | Lista sem linhas. A identificação não usa dado simulado. |
| Seta A para B | Identificar o leitor | Seta | Faixa entre os frames | `F026` | Passo 2. Abre o histórico desse leitor. |
| Frame B - Histórico do leitor | Histórico de empréstimos | Título | Abaixo da barra, à esquerda | `F026` | Passo 3. |
| Frame B - Histórico do leitor | Área do histórico | Área vazia | Abaixo do título | `F026` | Sem linhas neste esboço. A consulta não gera log e não mostra operação feita com sucesso. `[RN-14]` A devolução não apaga este histórico. |

---

## 3. Estados da Interface

- **Estado vazio:** A área sob o título fica sem linhas neste esboço. `[CONFIRMAR]` a mensagem quando o leitor não tem empréstimo.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** A consulta não gera log e não mostra a mensagem de sucesso. `[RN-14]` `[CONFIRMAR]` os dados de cada linha. A lista por status é `F025`.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador. A consulta parte da área de usuários. A página do histórico traz o título e a área vazia. Não há linha de sucesso.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Quais dados cada empréstimo do histórico mostra.
> - [ ] `[CONFIRMAR]` Estado vazio, quando o leitor não tem empréstimo, e carregamento.
