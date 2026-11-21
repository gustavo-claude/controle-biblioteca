# Wireflow: F010 Pesquisar situação do acervo

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F010` - Pesquisar situação do acervo
- **Passos de origem:** 1. Se a pesquisa parte do acervo: 1a. Abrir a área de gestão do acervo e abrir a pesquisa. Senão: 1b. Abrir a área de relatórios e abrir a pesquisa. 2. Informar um dado do tipo ou o código do exemplar. 3. Se a obra tem exemplar emprestado: 3a. Ver a data prevista mais próxima. Senão, se o exemplar está indisponível e não há empréstimo: 3b. Ver a mensagem de que o exemplar não está disponível para empréstimo, sem data. Senão: 3c. Ver o exemplar disponível.
- **Regras vinculadas:** `[RN-04]`, `[RN-14]`
- **Rodadas com o operador:** 7 de 7, escolhas do orquestrador no papel de operador: Barra na área de acervo; Título e ação na área de acervo; Lista do acervo; Barra na área de relatórios; Título e ação nos relatórios; Campos da pesquisa; Resultados alternativos.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F010-pesquisar-situacao-do-acervo.svg`

---

## 1. Wireflow em ASCII

Passo 1a - Abrir a área de gestão do acervo e abrir a pesquisa

```text
+----------------------------------------------------------+
| Frame A - Área de gestão do acervo                       |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Acervo                                                   |
| [Pesquisar acervo]                                       |
| Tipo              Título ou nome                         |
| -------------------------------------------------------- |
|                                                          |
|                                                          |
+----------------------------------------------------------+
```

Passo 1b - Abrir a área de relatórios e abrir a pesquisa

```text
+----------------------------------------------------------+
| Frame B - Área de relatórios                             |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Relatórios                                               |
| [Pesquisar acervo]                                       |
+----------------------------------------------------------+
```

As setas saem de A e de B e tocam a borda de C. Não há seta entre A e B.

```text
        | Abrir a pesquisa          | Abrir a pesquisa
        v                           v
```

Passo 2 - Informar um dado do tipo ou o código do exemplar
Passos 3a, 3b e 3c - alternativas de resultado, não uma sequência

```text
+----------------------------------------------------------+
| Frame C - Pesquisa do acervo                             |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Pesquisa do acervo                                       |
| Dado do tipo            [                              ] |
| Código do exemplar      [                              ] |
| [Pesquisar]                                              |
|                                                          |
| Disponível              [                              ] |
| Emprestado                                               |
| Data prevista mais próxima   [                         ] |
| Indisponível                                             |
| O exemplar não está disponível para empréstimo.         |
+----------------------------------------------------------+
```

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro | barra | Topo da página | `F010` | Barra do gestor. A área atual é Acervo. |
| Frame A - Área de gestão do acervo | Acervo | área da barra | Barra, primeira área, realce | `F010` | Passo 1a. Área de gestão do acervo. |
| Frame A - Área de gestão do acervo | Usuários | área da barra | Barra, segunda área | `F010` | Área de gestão de usuários. Não é o leitor. |
| Frame A - Área de gestão do acervo | Empréstimos | área da barra | Barra, terceira área | `F010` | Área de gestão de empréstimos. |
| Frame A - Área de gestão do acervo | Relatórios | área da barra | Barra, quarta área | `F010` | Não é a área atual neste frame. |
| Frame A - Área de gestão do acervo | Acervo | título da página | Abaixo da barra | `F010` | Nome da área aberta. |
| Frame A - Área de gestão do acervo | Pesquisar acervo | botão | Abaixo do título | `F010` | Abre a pesquisa. Realce do botão primário. |
| Frame A - Área de gestão do acervo | Tipo | cabeçalho | Lista, coluna esquerda | `F010` | Cabeçalho da lista. Sem dado simulado. |
| Frame A - Área de gestão do acervo | Título ou nome | cabeçalho | Lista, ao lado de Tipo | `F010` | Cabeçalho da lista. Sem dado simulado. |
| Frame B - Área de relatórios | Biblioteca Limoeiro | barra | Topo da página | `F010` | Mesma barra do gestor. A área atual é Relatórios. |
| Frame B - Área de relatórios | Relatórios | área da barra | Barra, quarta área, realce | `F010` | Passo 1b. Área de relatórios. |
| Frame B - Área de relatórios | Relatórios | título da página | Abaixo da barra | `F010` | Nome da área aberta. |
| Frame B - Área de relatórios | Pesquisar acervo | botão | Abaixo do título | `F010` | Abre a mesma pesquisa do acervo. |
| Frame C - Pesquisa do acervo | Dado do tipo | campo | Abaixo do título, vazio | `F010` | Passo 2. Um dado do tipo da obra. Sem valor neste esboço. |
| Frame C - Pesquisa do acervo | Código do exemplar | campo | Abaixo do dado do tipo, vazio | `F010` | Passo 2. Alternativa ao dado do tipo. Sem valor neste esboço. |
| Frame C - Pesquisa do acervo | Pesquisar | botão | Abaixo dos campos | `F010` | Mostra a situação. Não gera log e não mostra mensagem de sucesso. `[RN-14]` |
| Frame C - Pesquisa do acervo | Disponível | resultado | Primeira linha, valor vazio | `F010` | Passo 3c. Status oficial do exemplar. |
| Frame C - Pesquisa do acervo | Emprestado | resultado | Segunda linha | `F010` | Passo 3a. A obra tem exemplar emprestado. |
| Frame C - Pesquisa do acervo | Data prevista mais próxima | resultado | Na linha do emprestado, valor vazio | `F010` | Passo 3a. Data do exemplar que volta primeiro. `[RN-04]` |
| Frame C - Pesquisa do acervo | Indisponível | resultado | Terceira linha | `F010` | Passo 3b. Status oficial do exemplar. |
| Frame C - Pesquisa do acervo | O exemplar não está disponível para empréstimo. | texto | Na linha do indisponível | `F010` | Passo 3b. Mensagem sem data. `[RN-04]` |
| Seta A para C | Abrir a pesquisa | seta | Faixa entre A e C | `F010` | Reação do passo 1a. |
| Seta B para C | Abrir a pesquisa | seta | Faixa entre B e C | `F010` | Reação do passo 1b. A pesquisa é a mesma. |

---

## 3. Estados da Interface

- **Estado vazio:** `[CONFIRMAR]` O que a pesquisa mostra quando não encontra exemplar. Os campos deste esboço ficam vazios porque não há dado simulado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** A pesquisa não gera log e não mostra operação feita com sucesso. `[RN-14]` As três linhas são alternativas de resultado, não uma sequência. No emprestado, a data prevista é a mais próxima. `[RN-04]` No indisponível sem empréstimo, a mensagem não traz data. `[RN-04]` `[CONFIRMAR]` O que mostrar quando há, ao mesmo tempo, exemplar emprestado e exemplar indisponível sem empréstimo.

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas nos frames acima.
>
> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` O que mostrar quando os casos de emprestado e de indisponível sem empréstimo ocorrem juntos.
> - [ ] `[CONFIRMAR]` Estado vazio, quando a pesquisa não encontra exemplar.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] As três linhas de resultado são alternativas, não uma sequência. Não há mensagem de sucesso. A pesquisa não gera log.
