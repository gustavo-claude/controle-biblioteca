# Wireflow: F022 Registrar indisponibilidade do exemplar

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F022` - Registrar indisponibilidade do exemplar
- **Passos de origem:** 1. Abrir a área de gestão do acervo. 2. Identificar o exemplar disponível. 3. Se o exemplar não está disponível: 3a. Recusar a indisponibilidade e permanecer na área. Senão: 3b. Registrar a indisponibilidade do exemplar. 4. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-04]`, `[RN-13]`, `[RN-14]`
- **Rodadas com o operador:** 4 de 4, escolhas do orquestrador no papel de operador: Área de acervo; Identificação e situação; Ação; Mensagem de sucesso.
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F022-registrar-indisponibilidade-do-exemplar.svg`

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
        | Registrar a indisponibilidade a partir de disponível
        v
```

Passo 2 - Identificar o exemplar disponível
Passo 3b - Registrar a indisponibilidade do exemplar
Passo 4 - Ver a mensagem operação feita com sucesso

```text
+----------------------------------------------------------+
| Frame B - Indisponibilidade                              |
| Acervo | Usuários | Empréstimos | Relatórios             |
| Indisponibilidade                                        |
| Código do exemplar      [                              ] |
| Situação                                                 |
| Disponível                                               |
| [Registrar a indisponibilidade]                          |
| operação feita com sucesso                               |
+----------------------------------------------------------+
```

O passo 3a não abre outro frame.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Frame A - Área de gestão do acervo | Biblioteca Limoeiro | barra | Topo da página | `F022` | Barra do gestor. A área atual é Acervo. |
| Frame A - Área de gestão do acervo | Acervo | título da página | Abaixo da barra | `F022` | Passo 1. Área de gestão do acervo. |
| Frame A - Área de gestão do acervo | Tipo | cabeçalho | Lista, coluna esquerda | `F022` | Cabeçalho da lista. Sem dado simulado. |
| Frame A - Área de gestão do acervo | Título ou nome | cabeçalho | Lista, ao lado de Tipo | `F022` | Cabeçalho da lista. Sem dado simulado. |
| Seta A para B | Registrar a indisponibilidade a partir de disponível | seta | Faixa entre A e B | `F022` | Reação do passo 3b. A passagem parte de disponível. `[RN-13]` |
| Frame B - Indisponibilidade | Código do exemplar | campo | Abaixo do título, vazio | `F022` | Passo 2. Identifica o exemplar disponível. Sem valor neste esboço. |
| Frame B - Indisponibilidade | Disponível | situação | Abaixo do código | `F022` | Situação de partida. Só a partir de disponível a ação se conclui. `[RN-13]` |
| Frame B - Indisponibilidade | Registrar a indisponibilidade | botão | Abaixo da situação | `F022` | Passo 3b. O exemplar fica indisponível e não é emprestado. `[RN-04]` `[RN-13]` |
| Frame B - Indisponibilidade | operação feita com sucesso | mensagem | Abaixo do botão | `F022` | Passo 4. A ação concluída gera log. `[RN-14]` |

---

## 3. Estados da Interface

- **Estado vazio:** `[CONFIRMAR]` O que a página mostra quando nenhum exemplar foi identificado. O código deste esboço fica vazio porque não há dado simulado.
- **Carregamento / atualização:** `[CONFIRMAR]`
- **Bloqueios e restrições:** Se o exemplar não está disponível, a ação não se conclui e não há mensagem. A recusa permanece na área e não gera log. `[RN-14]` Exemplar indisponível não é emprestado. `[RN-04]` A passagem desenhada parte de disponível. `[RN-13]`

---

## 4. Notas para o Operador

> Escolhas do orquestrador no papel de operador, já aplicadas nos frames acima.
>
> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` O que a página mostra quando nenhum exemplar foi identificado.
> - [ ] `[CONFIRMAR]` O que a página mostra quando o código não corresponde a um exemplar.
> - [ ] `[CONFIRMAR]` Carregamento e atualização.
> - [ ] Se o exemplar não está disponível, a ação não se conclui e não há mensagem de sucesso.
