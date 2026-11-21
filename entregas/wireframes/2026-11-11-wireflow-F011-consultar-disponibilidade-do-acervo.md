# Wireflow: F011 Consultar disponibilidade do acervo

- **Persona que executa os passos:** Leitor
- **Funcionalidade:** `F011` - Consultar disponibilidade do acervo
- **Passos de origem:** 1. Abrir a página pública de consulta. 2. Informar um dado do tipo ou o código do exemplar. 3. Se a obra tem exemplar emprestado: 3a. Ver a data prevista mais próxima. Senão, se o exemplar está indisponível e não há empréstimo: 3b. Ver a mensagem de que o exemplar não está disponível para empréstimo, sem data. Senão: 3c. Ver o exemplar disponível.
- **Regras vinculadas:** `[RN-01]`, `[RN-04]`, `[RN-14]`
- **Rodadas com o operador:** 3 de 3, escolhas do orquestrador no papel de operador: Página pública; Campos da pesquisa; Resultados alternativos.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F011-consultar-disponibilidade-do-acervo.svg`

---

## 1. Wireflow em ASCII

Passo 1 - Abrir a página pública de consulta, sem login
Passo 2 - Informar um dado do tipo ou o código do exemplar
Passos 3a, 3b e 3c - alternativas de resultado, não uma sequência

```text
+----------------------------------------------------------+
| Frame A - Página pública                                 |
|                                                          |
| Consulta do acervo                                       |
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

Sem seta: os passos exibem conteúdo nesta janela. A página não tem a barra do gestor.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Página pública | Consulta do acervo | título da página | Topo da página | `F011` | Passo 1. Página pública, sem login. `[RN-01]` |
| Frame A - Página pública | Dado do tipo | campo | Abaixo do título, vazio | `F011` | Passo 2. Mesmo campo da pesquisa de `F010`. Sem valor neste esboço. |
| Frame A - Página pública | Código do exemplar | campo | Abaixo do dado do tipo, vazio | `F011` | Passo 2. Mesmo campo da pesquisa de `F010`. Sem valor neste esboço. |
| Frame A - Página pública | Pesquisar | botão | Abaixo dos campos | `F011` | Mostra a situação. Não gera log e não mostra mensagem de sucesso. `[RN-14]` |
| Frame A - Página pública | Disponível | resultado | Primeira linha, valor vazio | `F011` | Passo 3c. Mesma linha de `F010`. |
| Frame A - Página pública | Emprestado | resultado | Segunda linha | `F011` | Passo 3a. A obra tem exemplar emprestado. |
| Frame A - Página pública | Data prevista mais próxima | resultado | Na linha do emprestado, valor vazio | `F011` | Passo 3a. Data do exemplar que volta primeiro. `[RN-04]` |
| Frame A - Página pública | Indisponível | resultado | Terceira linha | `F011` | Passo 3b. |
| Frame A - Página pública | O exemplar não está disponível para empréstimo. | texto | Na linha do indisponível | `F011` | Passo 3b. Mensagem sem data. `[RN-04]` |

---

## 3. Estados da Interface

- **Estado vazio:** `[CONFIRMAR]` O que a consulta mostra quando não encontra exemplar. Os campos deste esboço ficam vazios porque não há dado simulado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Sem usuário e sem senha. Cadastro, empréstimo e configuração ficam fora desta página. `[RN-01]` A consulta não gera log e não mostra operação feita com sucesso. `[RN-14]` As três linhas são alternativas de resultado, não uma sequência. No emprestado, a data prevista é a mais próxima. No indisponível sem empréstimo, a mensagem não traz data. `[RN-04]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas no frame acima.
>
> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Estado vazio, quando a consulta não encontra exemplar.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] Sem usuário e sem senha. Cadastro e empréstimo ficam de fora. Sem mensagem de sucesso. Sem seta: a pesquisa e o resultado estão na mesma página.
