# Wireflow: F006 Editar dados da obra

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F006` - Editar dados da obra
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Identificar a obra. 3. Abrir a mesma estrutura do cadastro do tipo dessa obra. 4. Alterar os dados do tipo. 5. Concluir a edição da obra. 6. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-12]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F006-editar-dados-da-obra.svg`

Escolhas do orquestrador no papel de operador. Frame A é a área de gestão do acervo. Frame B repete a estrutura visual de um formulário de cadastro. Os rótulos dos campos ficam fora da página: são os do tipo, iguais ao cadastro.

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
        | Identificar a obra
        v
Passos 3 a 6 - Editar a obra
+------------------------------------------------------------------+
| Frame B - Editar obra                                            |
| Editar obra                                                      |
| Dados do tipo                                                    |
| [                    ]                                           |
| [Concluir a edição]                                              |
| operação feita com sucesso                                       |
+------------------------------------------------------------------+
        Os campos são os do tipo, iguais ao cadastro.
        [CONFIRMAR] Se o tipo pode ser trocado.
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro e as quatro áreas | Barra | Topo da página | `F006` | Acervo em destaque. |
| Frame A - Área de gestão do acervo | Acervo | Título da página | Abaixo da barra | `F006` | Passo 1. |
| Frame A - Área de gestão do acervo | Adicionar obra | Botão | Ações | `F005` | Permanece na área. Este wireflow não o abre. |
| Frame A - Área de gestão do acervo | Pesquisar acervo | Botão | Ao lado | `F010` | Permanece na área. Este wireflow não abre a pesquisa. |
| Frame A - Área de gestão do acervo | Tipo, Título ou nome | Cabeçalho de lista | Lista de obras, sem linhas | `F006` | Passo 2 parte desta lista. Sem linha fictícia. |
| Frame A - Área de gestão do acervo | Código do exemplar, Situação | Cabeçalho de lista | Segunda lista, sem linhas | `F006` | Lista vazia neste esboço. |
| Frame B - Editar obra | Editar obra | Título da página | Abaixo da barra | `F006` | Passo 3. Mesma estrutura visual do cadastro do tipo. |
| Frame B - Editar obra | Dados do tipo | Grupo de campos vazios | Formulário | `F006` | Passo 4. Os rótulos são os do tipo em `F005`. A quantidade de caixas não fixa o tipo. `[RN-12]` |
| Frame B - Editar obra | Concluir a edição | Botão primário | Abaixo dos campos | `F006` | Passo 5. |
| Frame B - Editar obra | operação feita com sucesso | Mensagem | Abaixo do botão | `F006` | Passo 6. Representa o log, com valor anterior e valor novo. `[RN-14]` |
| Frame B - Editar obra | Os campos são os do tipo, iguais ao cadastro. | Texto fora da página | Ao lado do Frame B | `F006` | `[RN-12]` |
| Frame B - Editar obra | [CONFIRMAR] Se o tipo pode ser trocado. | Texto fora da página | Ao lado do Frame B | `F006` | A lista deixa esta lacuna. O seletor de tipo não foi desenhado. |

---

## 3. Estados da Interface

- **Estado vazio:** As listas da área mostram só o cabeçalho. As caixas do formulário ficam em branco.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** `[CONFIRMAR]` Se a edição pode trocar o tipo da obra. O contexto não fecha essa troca.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Se o tipo pode ser trocado. O seletor de tipo não entra neste wireflow.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] Os campos desenhados são a estrutura. Os rótulos são os do tipo daquela obra, iguais a `F005`.
