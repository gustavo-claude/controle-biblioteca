# Wireflow: F027 Consultar movimentação do exemplar

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F027` - Consultar movimentação do exemplar
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Identificar o exemplar. 3. Ver o histórico de movimentação do exemplar.
- **Regras vinculadas:** `[RN-07]`, `[RN-09]`, `[RN-14]`
- **Rodadas com o operador:** 3 de 3, escolhas do orquestrador no papel de operador: Área de acervo; Identificação; Histórico.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F027-consultar-movimentacao-do-exemplar.svg`

---

## 1. Wireflow em ASCII

Passo 1 - Abrir a área de gestão do acervo

```text
+----------------------------------------------------------+
| Frame A - Área de gestão do acervo                       |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Acervo                                                   |
| Tipo              Título ou nome                         |
| -------------------------------------------------------- |
|                                                          |
+----------------------------------------------------------+
        |
        | Identificar o exemplar
        v
```

Passo 2 - Identificar o exemplar
Passo 3 - Ver o histórico de movimentação do exemplar

```text
+----------------------------------------------------------+
| Frame B - Movimentação do exemplar                       |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Movimentação do exemplar                                 |
| Código do exemplar      [                              ] |
|                                                          |
| Histórico de movimentação                                |
|                                                          |
|                                                          |
+----------------------------------------------------------+
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro | barra | Topo da página | `F027` | Barra do gestor. A área atual é Acervo. |
| Frame A - Área de gestão do acervo | Acervo | título da página | Abaixo da barra | `F027` | Passo 1. Área de gestão do acervo. |
| Frame A - Área de gestão do acervo | Tipo | cabeçalho | Lista, coluna esquerda | `F027` | Cabeçalho da lista. Sem dado simulado. |
| Frame A - Área de gestão do acervo | Título ou nome | cabeçalho | Lista, ao lado de Tipo | `F027` | Cabeçalho da lista. Sem dado simulado. |
| Seta A para B | Identificar o exemplar | seta | Faixa entre A e B | `F027` | Reação do passo 2. |
| Frame B - Movimentação do exemplar | Código do exemplar | campo | Abaixo do título, vazio | `F027` | Passo 2. Código único do exemplar. `[RN-09]` Sem valor neste esboço. |
| Frame B - Movimentação do exemplar | Histórico de movimentação | área | Abaixo do código, vazia | `F027` | Passo 3. A devolução não apaga o histórico. `[RN-07]` A consulta não gera log. `[RN-14]` Sem colunas neste esboço. |

---

## 3. Estados da Interface

- **Estado vazio:** `[CONFIRMAR]` O que a área mostra quando o exemplar não tem movimentação. A área deste esboço fica vazia porque as colunas não estão definidas e não há dado simulado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** A consulta não gera log e não mostra operação feita com sucesso. `[RN-14]` A devolução não apaga o histórico. `[RN-07]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas nos frames acima.
>
> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Quais colunas o histórico de movimentação mostra.
> - [ ] `[CONFIRMAR]` Estado vazio, quando o exemplar não tem movimentação.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] A consulta não gera log. Não há mensagem de sucesso.
