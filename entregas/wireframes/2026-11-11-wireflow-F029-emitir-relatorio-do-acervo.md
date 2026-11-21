# Wireflow: F029 Emitir relatório do acervo

- **Persona que executa os passos:** Gestor da biblioteca
- **Funcionalidade:** `F029` - Emitir relatório do acervo
- **Passos de origem:** 1. Abrir a área de relatórios. 2. Escolher o recorte de tipo: todas as obras ou um tipo. 3. Escolher o recorte de permanência: todas as obras já cadastradas ou apenas as que ainda não foram removidas. 4. Emitir o relatório do acervo. 5. Ver a data de inclusão de cada obra. 6. Se a obra tem empréstimo: 6a. Ver o último empréstimo e o status desse empréstimo. Senão: 6b. Ver a obra sem último empréstimo. 7. Ver a mensagem operação feita com sucesso.
- **Regras vinculadas:** `[RN-12]`, `[RN-14]`
- **Rodadas com o operador:** 6 de 6, escolhas do orquestrador no papel de operador
- **Arquivo SVG:** `entregas/wireframes/2026-11-11-wireflow-F029-emitir-relatorio-do-acervo.svg`

---

## 1. Wireflow em ASCII

Frame A - Relatório do acervo
Passo 1 - Abrir a área de relatórios
Passo 2 - Escolher o recorte de tipo: todas as obras ou um tipo
Passo 3 - Escolher o recorte de permanência: todas as obras já cadastradas ou apenas as que ainda não foram removidas
Passo 4 - Emitir o relatório do acervo

```text
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| Acervo | Usuários | Empréstimos | [ Relatórios ]            |
|                                                              |
| Recorte de tipo                                              |
| ( ) Todas as obras                                           |
| ( ) Um tipo                                                  |
|                                                              |
| Recorte de permanência                                       |
| ( ) Todas as obras já cadastradas                            |
| ( ) Apenas as que ainda não foram removidas                  |
|                                                              |
| [ Emitir relatório ]                                         |
+--------------------------------------------------------------+
        |
        | O gestor emite o relatório.
        v
```

Frame B - Relatório emitido
Passo 5 - Ver a data de inclusão de cada obra
Passo 6a - Ver o último empréstimo e o status desse empréstimo
Passo 6b - Ver a obra sem último empréstimo
Passo 7 - Ver a mensagem operação feita com sucesso

```text
+--------------------------------------------------------------+
| Biblioteca Limoeiro                                          |
| Acervo | Usuários | Empréstimos | [ Relatórios ]            |
|                                                              |
| +----------------------------------------------------------+ |
| |                                                          | |
| +----------------------------------------------------------+ |
| Data de inclusão                                             |
| Último empréstimo                                            |
| Status desse empréstimo                                     |
|                                                              |
| Sem último empréstimo                                        |
|                                                              |
| operação feita com sucesso                                   |
+--------------------------------------------------------------+
```

Fora do retângulo:

O log guarda o recorte, sem valor anterior e sem valor novo.

---

## 2. Inventário de Componentes e Elementos

| Bloco | Elemento / Rótulo | Tipo | Posição | Funcionalidade | Comportamento / Regra |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Fora do retângulo | Frame A - Relatório do acervo | Título do frame | Acima da página, à esquerda | `F029` | Janela dos passos 1 a 4 |
| Fora do retângulo | Passo 1 - Abrir a área de relatórios | Passo | Abaixo do título, fora da página | `F029` | O gestor abre a área de relatórios |
| Fora do retângulo | Passo 2 - Escolher o recorte de tipo: todas as obras ou um tipo | Passo | Abaixo do passo 1, fora da página | `F029` | Primeiro recorte |
| Fora do retângulo | Passo 3 - Escolher o recorte de permanência: todas as obras já cadastradas ou apenas as que ainda não foram removidas | Passo | Abaixo do passo 2, fora da página | `F029` | Segundo recorte |
| Fora do retângulo | Passo 4 - Emitir o relatório do acervo | Passo | Abaixo do passo 3, fora da página | `F029` | O gestor emite o relatório |
| Frame A - Relatório do acervo | Biblioteca Limoeiro | Barra | Topo da página | `F029` | Barra do gestor |
| Frame A - Relatório do acervo | Acervo, Usuários, Empréstimos | Barra | Abaixo do nome | `F029` | Áreas sem destaque |
| Frame A - Relatório do acervo | Relatórios | Barra em destaque | Na barra, à direita de Empréstimos | `F029` | Área de origem do relatório. Realce funcional |
| Frame A - Relatório do acervo | Recorte de tipo | Rótulo | Abaixo da barra | `F029` | Reúne as opções do passo 2 |
| Frame A - Relatório do acervo | Todas as obras | Opção | Primeira opção do recorte de tipo | `F029` | Opção desenhada sem marcação |
| Frame A - Relatório do acervo | Um tipo | Opção | Abaixo de Todas as obras | `F029` | Opção desenhada sem marcação. Tipos fechados em `[RN-12]` |
| Frame A - Relatório do acervo | Recorte de permanência | Rótulo | Abaixo do recorte de tipo | `F029` | Reúne as opções do passo 3 |
| Frame A - Relatório do acervo | Todas as obras já cadastradas | Opção | Primeira opção de permanência | `F029` | Opção desenhada sem marcação |
| Frame A - Relatório do acervo | Apenas as que ainda não foram removidas | Opção | Abaixo da opção anterior | `F029` | Opção desenhada sem marcação. `[RN-12]` |
| Frame A - Relatório do acervo | Emitir relatório | Botão primário | Abaixo do recorte de permanência | `F029` | Passo 4. A emissão gera log com o recorte. `[RN-14]` |
| Entre A e B | O gestor emite o relatório. | Seta | Faixa entre as páginas. A ponta aponta para baixo, antes do título do Frame B | `F029` | Reação do passo 4. Não cruza texto nem o interior da página |
| Fora do retângulo | Frame B - Relatório emitido | Título do frame | Abaixo da seta, à esquerda | `F029` | Janela dos passos 5, 6a, 6b e 7 |
| Fora do retângulo | Passo 5 - Ver a data de inclusão de cada obra | Passo | Abaixo do título do Frame B, fora da página | `F029` | Cada obra mostra a data de inclusão |
| Fora do retângulo | Passo 6a - Ver o último empréstimo e o status desse empréstimo | Passo | Abaixo do passo 5, fora da página | `F029` | Vale quando a obra tem empréstimo |
| Fora do retângulo | Passo 6b - Ver a obra sem último empréstimo | Passo | Abaixo do passo 6a, fora da página | `F029` | Vale quando a obra não tem empréstimo |
| Fora do retângulo | Passo 7 - Ver a mensagem operação feita com sucesso | Passo | Abaixo do passo 6b, fora da página | `F029` | A mensagem representa o log da emissão |
| Frame B - Relatório emitido | Biblioteca Limoeiro | Barra | Topo da página | `F029` | Mesma barra do gestor |
| Frame B - Relatório emitido | Relatórios | Barra em destaque | Na barra | `F029` | A emissão continua na área de relatórios |
| Frame B - Relatório emitido | Obra | Área vazia | Abaixo da barra | `F029` | Uma obra, sem dados preenchidos |
| Frame B - Relatório emitido | Data de inclusão | Rótulo | Abaixo da obra vazia | `F029` | Passo 5. Sem valor neste esboço. `[RN-12]` |
| Frame B - Relatório emitido | Último empréstimo | Rótulo | Abaixo de Data de inclusão | `F029` | Passo 6a. Sem valor neste esboço |
| Frame B - Relatório emitido | Status desse empréstimo | Rótulo | Abaixo de Último empréstimo | `F029` | Passo 6a. Sem valor. Catálogo: Ativo, Atrasado, Devolvido, Encerrado por extravio |
| Frame B - Relatório emitido | Sem último empréstimo | Linha | Abaixo dos três rótulos | `F029` | Passo 6b. A obra mostra a data de inclusão e não traz último empréstimo |
| Frame B - Relatório emitido | operação feita com sucesso | Linha | Abaixo de Sem último empréstimo | `F029` | Passo 7. Linha curta na mesma página |
| Fora do retângulo | O log guarda o recorte, sem valor anterior e sem valor novo | Texto | Abaixo da página do Frame B | `F029` | `[RN-14]`. O recorte é o de tipo e o de permanência |

---

## 3. Estados da Interface

- **Estado vazio:** A obra do relatório emitido fica em branco, sem dados preenchidos. A obra sem empréstimo aparece na linha Sem último empréstimo. `[CONFIRMAR]` O que a página mostra quando o recorte não traz obra.
- **Carregamento / atualização:** `[CONFIRMAR]` O passo e a regra não definem carregamento.
- **Bloqueios e restrições:** A emissão não se conclui sem o log (`[RN-14]`). O log guarda o recorte e não guarda valor anterior nem valor novo.

---

## 4. Notas para o Operador

Escolhas do orquestrador no papel de operador. Rodadas 1 a 4 no Frame A: barra com Relatórios em destaque, recorte de tipo, recorte de permanência, botão Emitir relatório. Rodadas 5 e 6 no Frame B: uma obra vazia com os três rótulos e a linha Sem último empréstimo; a linha curta operação feita com sucesso. Seta: O gestor emite o relatório.

> ✏️ **Ajustes ainda abertos:**
> - [ ] `[CONFIRMAR]` Como a obra é identificada no relatório. Livro, HQ e revista usam título. Brinquedo e outro usam nome.
> - [ ] `[CONFIRMAR]` Se algum recorte já vem marcado antes da escolha do gestor.
> - [ ] `[CONFIRMAR]` O que a página mostra quando o recorte não traz obra, e o carregamento.
