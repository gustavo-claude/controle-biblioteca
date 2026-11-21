# Wireflow: F009 Remover exemplar da obra

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F009` - Remover exemplar da obra
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Identificar o exemplar. 3a. Se o exemplar está emprestado, recusar a remoção e permanecer na área. 3b. Remover o exemplar. 4. [CONFIRMAR] Se a remoção gera log, ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-12]`, `[RN-13]`
- **Rodadas com o operador:** 3 de 3, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F009-remover-exemplar-da-obra.svg`

Escolhas do orquestrador no papel de operador. Frame A é a área de gestão do acervo. A recusa do exemplar emprestado fica fora da página, sem quadro. A mensagem de sucesso não entra na página: a lista ainda não fecha se a remoção gera log. `[RN-14]` nomeia cadastrar exemplar e não nomeia remover exemplar.

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
        | O exemplar não está emprestado
        v
Passo 3b - Remover o exemplar
+------------------------------------------------------------------+
| Frame B - Remover exemplar                                       |
| Remover exemplar                                                 |
| Código do exemplar      [                                    ]   |
| [Remover exemplar]                                               |
+------------------------------------------------------------------+
        A remoção não se conclui se o exemplar está emprestado.
        [CONFIRMAR] Se a remoção gera log.
        Se gerar, a tela mostra operação feita com sucesso.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro e as quatro áreas | Barra | Topo da página | `F009` | Acervo em destaque. |
| Frame A - Área de gestão do acervo | Acervo | Título da página | Abaixo da barra | `F009` | Passo 1. |
| Frame A - Área de gestão do acervo | Adicionar obra | Botão | Ações | `F005` | Permanece na área. Este wireflow não o abre. |
| Frame A - Área de gestão do acervo | Pesquisar acervo | Botão | Ao lado | `F010` | Permanece na área. Este wireflow não abre a pesquisa. |
| Frame A - Área de gestão do acervo | Tipo, Título ou nome | Cabeçalho de lista | Lista de obras, sem linhas | `F009` | Lista vazia neste esboço. |
| Frame A - Área de gestão do acervo | Código do exemplar, Situação | Cabeçalho de lista | Segunda lista, sem linhas | `F009` | Passo 2. Sem linha fictícia. |
| Frame B - Remover exemplar | Remover exemplar | Título da página | Abaixo da barra | `F009` | Passo 3b. |
| Frame B - Remover exemplar | Código do exemplar | Campo vazio | Formulário | `F009` | Passo 2. Campo em branco. |
| Frame B - Remover exemplar | Remover exemplar | Botão primário | Abaixo do código | `F009` | Passo 3b, quando o exemplar não está emprestado. |
| Frame B - Remover exemplar | A remoção não se conclui se o exemplar está emprestado. | Texto fora da página | Ao lado do Frame B | `F009` | Passo 3a. Permanece na área. Não mostra a mensagem de sucesso. `[RN-12]` |
| Frame B - Remover exemplar | [CONFIRMAR] Se a remoção gera log. Se gerar, a tela mostra operação feita com sucesso. | Texto fora da página | Ao lado do Frame B | `F009` | Passo 4. A mensagem não foi desenhada dentro da página. |

---

## 3. Estados da Interface

- **Estado vazio:** As listas da área mostram só o cabeçalho. O código do exemplar fica em branco.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Exemplar emprestado não é removido. Depois do encerramento por extravio, a remoção pode ser feita (`[RN-13]`). A recusa não mostra a mensagem de sucesso.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Se a remoção do exemplar gera log. Se gerar, a mensagem operação feita com sucesso entra na página.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] O encerramento por extravio é `F024`. Esta página não o executa.
