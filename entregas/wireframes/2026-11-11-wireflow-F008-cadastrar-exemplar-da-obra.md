# Wireflow: F008 Cadastrar exemplar da obra

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F008` - Cadastrar exemplar da obra
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Identificar a obra. 3. Cadastrar o exemplar dessa obra. 4. Ver o exemplar disponível e o código do exemplar. 5. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-09]`, `[RN-13]`, `[RN-14]`
- **Rodadas com o operador:** 3 de 3, escolhas do orquestrador no papel de operador.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F008-cadastrar-exemplar-da-obra.svg`

Escolhas do orquestrador no papel de operador. Frame A é a área de gestão do acervo. Frame B mostra o exemplar cadastrado. O código fica em branco neste esboço. Disponível é a situação em que o exemplar nasce, não um dado digitado.

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
        | Cadastrar o exemplar
        v
Passos 3 a 5 - Cadastrar o exemplar
+------------------------------------------------------------------+
| Frame B - Exemplar cadastrado                                    |
| Exemplar cadastrado                                              |
| Situação                                                         |
| Disponível                                                       |
| Código do exemplar      [                                    ]   |
| Único, guardado no sistema, não deriva de ISBN.                  |
| operação feita com sucesso                                       |
+------------------------------------------------------------------+
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro e as quatro áreas | Barra | Topo da página | `F008` | Acervo em destaque. |
| Frame A - Área de gestão do acervo | Acervo | Título da página | Abaixo da barra | `F008` | Passo 1. |
| Frame A - Área de gestão do acervo | Adicionar obra | Botão | Ações | `F005` | Permanece na área. Este wireflow não o abre. |
| Frame A - Área de gestão do acervo | Pesquisar acervo | Botão | Ao lado | `F010` | Permanece na área. Este wireflow não abre a pesquisa. |
| Frame A - Área de gestão do acervo | Tipo, Título ou nome | Cabeçalho de lista | Lista de obras, sem linhas | `F008` | Passo 2. Sem linha fictícia. |
| Frame A - Área de gestão do acervo | Código do exemplar, Situação | Cabeçalho de lista | Segunda lista, sem linhas | `F008` | Lista vazia neste esboço. |
| Frame B - Exemplar cadastrado | Exemplar cadastrado | Título da página | Abaixo da barra | `F008` | Passos 3 e 4. |
| Frame B - Exemplar cadastrado | Situação | Rótulo | Abaixo do título | `F008` | Passo 4. |
| Frame B - Exemplar cadastrado | Disponível | Situação | Abaixo do rótulo | `F008` | O exemplar nasce disponível. `[RN-13]` |
| Frame B - Exemplar cadastrado | Código do exemplar | Campo vazio | Abaixo da situação | `F008` | Passo 4. O campo fica em branco neste esboço. `[RN-09]` |
| Frame B - Exemplar cadastrado | Único, guardado no sistema, não deriva de ISBN. | Texto | Abaixo do campo | `F008` | `[RN-09]` |
| Frame B - Exemplar cadastrado | operação feita com sucesso | Mensagem | Abaixo do texto | `F008` | Passo 5. Representa o log de inclusão, com valor anterior vazio. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** As listas da área mostram só o cabeçalho. O código do exemplar fica em branco neste esboço. Disponível é a situação de nascimento do exemplar.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** O código é único, guardado no sistema, e não deriva de ISBN nem de outro dado externo (`[RN-09]`).

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas.
>
> **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Se a quantidade de exemplares informada na obra precisa coincidir com este cadastro.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] O cadastro da obra (`F005`) não cria este exemplar.
