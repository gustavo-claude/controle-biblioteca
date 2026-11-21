# Wireflow: F007 Remover obra do acervo

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F007` - Remover obra do acervo
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Identificar a obra. 3a. Com exemplar emprestado, recusar a remoção e permanecer na área. 3b. Remover a obra. 4. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-12]`, `[RN-13]`, `[RN-14]`
- **Rodadas com o operador:** 3 de 3, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F007-remover-obra-do-acervo.svg`

Escolhas do orquestrador no papel de operador. Frame A é a área de gestão do acervo. A recusa com exemplar emprestado fica fora da página, sem quadro. A seta é o ramo em que a obra não tem exemplar emprestado.

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
        | A obra não tem exemplar emprestado
        v
Passos 3b e 4 - Remover a obra
+------------------------------------------------------------------+
| Frame B - Remover obra                                           |
| Remover obra                                                     |
| Identificação da obra   [                                    ]   |
| [Remover obra]                                                   |
| operação feita com sucesso                                       |
+------------------------------------------------------------------+
        A remoção não se conclui com exemplar emprestado.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro e as quatro áreas | Barra | Topo da página | `F007` | Acervo em destaque. |
| Frame A - Área de gestão do acervo | Acervo | Título da página | Abaixo da barra | `F007` | Passo 1. |
| Frame A - Área de gestão do acervo | Adicionar obra | Botão | Ações | `F005` | Permanece na área. Este wireflow não o abre. |
| Frame A - Área de gestão do acervo | Pesquisar acervo | Botão | Ao lado | `F010` | Permanece na área. Este wireflow não abre a pesquisa. |
| Frame A - Área de gestão do acervo | Tipo, Título ou nome | Cabeçalho de lista | Lista de obras, sem linhas | `F007` | Passo 2. Sem linha fictícia. |
| Frame A - Área de gestão do acervo | Código do exemplar, Situação | Cabeçalho de lista | Segunda lista, sem linhas | `F007` | Lista vazia neste esboço. |
| Frame B - Remover obra | Remover obra | Título da página | Abaixo da barra | `F007` | Passo 3b. |
| Frame B - Remover obra | Identificação da obra | Campo vazio | Formulário | `F007` | Passo 2. Campo em branco. |
| Frame B - Remover obra | Remover obra | Botão primário | Abaixo da identificação | `F007` | Passo 3b, quando não há exemplar emprestado. |
| Frame B - Remover obra | operação feita com sucesso | Mensagem | Abaixo do botão | `F007` | Passo 4. Representa o log. O valor novo é a remoção. `[RN-14]` |
| Frame B - Remover obra | A remoção não se conclui com exemplar emprestado. | Texto fora da página | Ao lado do Frame B | `F007` | Passo 3a. Permanece na área. Não gera log nem a mensagem. `[RN-12]` |

---

## 3. Estados da Interface

- **Estado vazio:** As listas da área mostram só o cabeçalho. A identificação da obra fica em branco.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Com exemplar emprestado, a remoção não se conclui e o gestor permanece na área. Depois do empréstimo Encerrado por extravio, a remoção pode ser feita (`[RN-13]`). A obra guarda a data da remoção e o gestor responsável pela remoção (`[RN-12]`).

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` O que compõe a identificação da obra neste campo.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] O encerramento por extravio é `F024`. Esta página não o executa.
