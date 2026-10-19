> 🌟 **EXEMPLO PADRÃO OURO:**
> Forma de uma especificação funcional. No trabalho real, o número vem da funcionalidade confirmada na lista mais recente de `entregas/funcionalidades/`, com dois algarismos: `F02` gera o documento `HU-02`. Critério, regra e informação colam o número: `HU02-C01`, `HU02-R03`, `HU02-I01`. Não use `HU-02-C01`, `HU-002` nem `US-XX`.

# HU-02 Detalhar atendimento

> Prevalece, nesta ordem: cenário, regra, anexo ilustrativo. A lista de atualizações não altera o corpo.

## 1. Descrição

Contas Médicas consulta um atendimento e vê a identificação do paciente, as AIHs vinculadas e as ações daquele atendimento: prontuário, impressão, nova AIH, exclusão e exportação.

## 2. Narrativa da História

- **Como** Contas Médicas
- **Quero** visualizar os detalhes de um atendimento
- **Para que** eu consulte as informações do paciente e registre as alterações da produção hospitalar daquele atendimento

## 3. Critérios de Aceite

### Contexto compartilhado

Aplica-se a HU02-C05, HU02-C06, HU02-C07, HU02-C08, HU02-C09, HU02-C10, HU02-C11, HU02-C12, HU02-C16, HU02-C17, HU02-C18, HU02-C19, HU02-C20 e HU02-C22.

- **Dado que** Contas Médicas está na tela "Detalhes do Atendimento"

### HU02-C01: [caminho-feliz] — Detalhes a partir de Altas Hospitalares

- **Dado que** Contas Médicas está na lista "Altas Hospitalares" com atendimentos cadastrados
- **Quando** Contas Médicas aciona "Detalhes do Atendimento" de um paciente
- **Então** o sistema exibe a identificação do paciente e a lista de AIHs vinculadas `HU02-R01`
- **E** apresenta, em cada AIH, o número, a data inicial e a data final
- **E** disponibiliza "Imprimir", "Editar" e "Excluir" em cada AIH `HU02-R02`
- **E** disponibiliza "Ver Prontuário", "Criar Nova AIH", "Voltar" e "Exportar para Autorizador"

### HU02-C02: [caminho-feliz] — Detalhes a partir de Em Atendimento

- **Dado que** Contas Médicas está na lista "Em Atendimento" com pacientes listados
- **Quando** Contas Médicas aciona "Detalhes do Atendimento" de um paciente
- **Então** o sistema exibe a identificação do paciente e a lista de AIHs vinculadas `HU02-R01`
- **E** apresenta, em cada AIH, o número, o procedimento, a data e hora iniciais e a data e hora finais
- **E** disponibiliza "Imprimir" em cada AIH `HU02-R02`
- **E** disponibiliza "Ver Prontuário" e "Voltar"

### HU02-C03: [erro] — Falha ao carregar os detalhes

- **Dado que** a comunicação está indisponível na listagem de atendimentos
- **Quando** Contas Médicas aciona "Detalhes do Atendimento" de um paciente
- **Então** o sistema exibe o alerta: "Não foi possível carregar os detalhes do atendimento. Tente novamente em instantes."
- **E** mantém visível o botão "Voltar"
- **E** registra a tentativa malsucedida, com data e hora e a identificação de quem acionou `HU02-R07`

### HU02-C04: [estado-vazio] — Atendimento sem AIH

- **Dado que** Contas Médicas está na lista de atendimentos e o paciente selecionado não tem AIH vinculada
- **Quando** Contas Médicas aciona "Detalhes do Atendimento" desse paciente
- **Então** o sistema exibe a identificação do paciente `HU02-R01`
- **E** exibe na área de AIHs: "Nenhuma AIH vinculada a este atendimento até o momento."
- **E** disponibiliza "Criar Nova AIH" habilitado

### HU02-C05: [caminho-feliz] — Consultar prontuário

- **Dado que** o botão "Ver Prontuário" está disponível
- **Quando** Contas Médicas aciona "Ver Prontuário"
- **Então** o sistema exibe o prontuário do paciente com os dados clínicos e os registros de internação `HU02-R04`
- **E** disponibiliza "Voltar" para a tela de detalhes do atendimento

### HU02-C06: [caminho-feliz] — Voltar à lista de origem

- **Dado que** Contas Médicas chegou a "Detalhes do Atendimento" a partir de "Altas Hospitalares" ou de "Em Atendimento"
- **Quando** Contas Médicas aciona "Voltar"
- **Então** o sistema retorna à lista de origem `HU02-R05`
- **E** preserva os filtros, a paginação e a pesquisa dessa lista

### HU02-C07: [erro] — Prontuário indisponível

- **Dado que** o prontuário está temporariamente indisponível
- **Quando** Contas Médicas aciona "Ver Prontuário"
- **Então** o sistema exibe: "Serviço de prontuário temporariamente indisponível. Tente novamente em instantes."
- **E** permanece em "Detalhes do Atendimento"
- **E** registra a tentativa malsucedida, com data e hora e a identificação de quem acionou `HU02-R07`

### HU02-C08: [estado-vazio] — Prontuário sem anotação clínica

- **Dado que** o paciente não tem anotação clínica prévia
- **Quando** Contas Médicas aciona "Ver Prontuário"
- **Então** o sistema exibe os dados cadastrais do paciente
- **E** exibe na área de registros clínicos: "Nenhum registro clínico vinculado até o momento."

### HU02-C09: [caminho-feliz] — Imprimir AIH

- **Dado que** a listagem tem uma AIH válida
- **Quando** Contas Médicas aciona "Imprimir" dessa AIH
- **Então** o sistema gera o documento no padrão do Ministério da Saúde para AIH `HU02-R08`
- **E** registra quem imprimiu, a data e a hora e a ação de impressão `HU02-R07`
- **E** mantém "Detalhes do Atendimento" aberto, com a listagem preservada

### HU02-C10: [erro] — Impressão indisponível

- **Dado que** a geração do documento está indisponível
- **Quando** Contas Médicas aciona "Imprimir" de uma AIH da lista
- **Então** o sistema exibe: "Não foi possível gerar a impressão da AIH. Contate o suporte ou tente novamente mais tarde."
- **E** não entrega o documento
- **E** registra a tentativa malsucedida, com data e hora e a identificação de quem acionou `HU02-R07`

### HU02-C11: [estado-vazio] — Nenhuma AIH para imprimir

- **Dado que** o atendimento não tem AIH cadastrada
- **Quando** Contas Médicas visualiza a seção de AIHs
- **Então** o sistema não exibe "Imprimir"
- **E** exibe `[CONFIRMAR: texto da mensagem de ausência de AIH para impressão]`

### HU02-C12: [caminho-feliz] — Abrir a confirmação de exclusão

- **Dado que** o perfil é "Contas Médicas" ou "Administrador"
- **E** a lista tem ao menos uma AIH
- **Quando** Contas Médicas aciona "Excluir" em uma AIH
- **Então** o sistema exibe: "Você deseja realmente excluir a AIH Nº [número da AIH] associada ao procedimento [nome do procedimento]?" `HU02-R12`
- **E** apresenta um campo obrigatório para o motivo `HU02-R10`
- **E** disponibiliza "Confirmar Exclusão" e "Cancelar"

### HU02-C13: [caminho-feliz] — Confirmar a exclusão

- **Dado que** a confirmação de exclusão está aberta e o motivo está preenchido
- **Quando** Contas Médicas aciona "Confirmar Exclusão"
- **Então** a AIH deixa de constar na listagem do atendimento `HU02-R11`
- **E** o sistema registra quem excluiu, a data e a hora e o motivo informado `HU02-R07`
- **E** fecha a confirmação e exibe: "AIH excluída com sucesso. Motivo registrado: [motivo informado]."

### HU02-C14: [erro] — Exclusão sem motivo

- **Dado que** a confirmação de exclusão está aberta e o motivo está em branco
- **Quando** Contas Médicas aciona "Confirmar Exclusão"
- **Então** o sistema mantém a confirmação aberta e não exclui a AIH `HU02-R10`
- **E** exibe: "O preenchimento do motivo da exclusão é obrigatório."
- **E** não registra exclusão

### HU02-C15: [caminho-feliz] — Excluir a única AIH

- **Dado que** a confirmação está aberta para a única AIH do atendimento e o motivo está preenchido
- **Quando** Contas Médicas aciona "Confirmar Exclusão"
- **Então** a AIH deixa de constar na listagem `HU02-R11`
- **E** a área de AIHs exibe: "Nenhuma AIH vinculada a este atendimento até o momento."
- **E** "Criar Nova AIH" permanece habilitado

### HU02-C16: [caminho-feliz] — Exportar para o Autorizador

- **Dado que** o atendimento está encerrado e tem AIH vinculada
- **Quando** Contas Médicas aciona "Exportar para Autorizador"
- **Então** o sistema envia os dados do atendimento no layout citado como Anexo IV `HU02-R06`
- **E** registra quem exportou, a data e a hora e o resultado de sucesso `HU02-R07`
- **E** exibe: "Dados do atendimento exportados com sucesso para o Autorizador da SESMA."

### HU02-C17: [erro] — Autorizador indisponível

- **Dado que** o Autorizador da SESMA está indisponível
- **Quando** Contas Médicas aciona "Exportar para Autorizador"
- **Então** o sistema exibe: "Não foi possível comunicar com o Autorizador da SESMA no momento. Verifique a conexão e tente novamente mais tarde."
- **E** registra a tentativa, com data e hora, a identificação de quem acionou e o resultado de falha `HU02-R06` `HU02-R07`
- **E** mantém os dados do atendimento inalterados

### HU02-C18: [estado-vazio] — Sem AIH para exportar

- **Dado que** o paciente não tem AIH vinculada
- **Quando** Contas Médicas visualiza as opções de exportação
- **Então** "Exportar para Autorizador" fica desabilitado
- **E** a orientação exibida é: "Adicione ao menos uma AIH para habilitar a exportação."

### HU02-C19: [permissao] — Perfil autorizado

- **Dado que** a pessoa autenticada tem o perfil "Contas Médicas" ou "Administrador"
- **Quando** essa pessoa visualiza a lista de AIHs
- **Então** "Editar" e "Excluir" ficam habilitados em cada AIH `HU02-R02` `HU02-R09`
- **E** "Criar Nova AIH" e "Exportar para Autorizador" ficam habilitados

### HU02-C20: [permissao] — Perfil sem permissão de faturamento

- **Dado que** a pessoa autenticada tem perfil de consulta ou recepção, sem permissão para faturamento
- **Quando** essa pessoa visualiza "Detalhes do Atendimento"
- **Então** o sistema oculta "Editar", "Excluir" e "Criar Nova AIH" `HU02-R09`
- **E** mantém visíveis "Ver Prontuário", "Imprimir" e "Voltar"

### HU02-C21: [permissao] — Ação restrita disparada sem permissão

- **Dado que** a pessoa autenticada não tem permissão para excluir AIH
- **Quando** essa pessoa dispara a exclusão de uma AIH
- **Então** o sistema não executa a exclusão `HU02-R09`
- **E** exibe: "Você não possui permissão para executar esta ação."
- **E** registra a tentativa não autorizada `HU02-R07`

### HU02-C22: [estado-vazio] — Perfil autorizado sem AIH

- **Dado que** a pessoa autenticada tem o perfil "Contas Médicas" ou "Administrador" e a lista de AIHs está vazia
- **Quando** essa pessoa visualiza "Detalhes do Atendimento"
- **Então** "Criar Nova AIH" fica habilitado em destaque
- **E** "Editar" e "Excluir" não aparecem

## 4. Regras de Negócio

### HU02-R01 — Identificação e AIHs do atendimento

A tela de detalhamento mostra a identificação do paciente e as AIHs vinculadas àquele atendimento.

Demonstrada por: HU02-C01, HU02-C02, HU02-C04

### HU02-R02 — Ações da AIH conforme origem e perfil

As ações sobre cada AIH dependem da lista de origem e do perfil de quem visualiza.

Demonstrada por: HU02-C01, HU02-C02, HU02-C19, HU02-C20

### HU02-R03 — Ação de criar nova AIH

O perfil autorizado dispõe da ação de criar nova AIH na tela de detalhamento, inclusive quando a lista de AIHs está vazia.

Demonstrada por: HU02-C01, HU02-C04, HU02-C15, HU02-C22

### HU02-R04 — Consulta ao prontuário

A tela de detalhamento oferece a consulta ao prontuário do paciente.

Demonstrada por: HU02-C05

### HU02-R05 — Retorno sem perder a lista

O retorno à lista de origem preserva filtros, paginação e pesquisa.

Demonstrada por: HU02-C06

### HU02-R06 — Exportação ao Autorizador

A exportação envia os dados do atendimento ao Autorizador da SESMA e registra o resultado.

Demonstrada por: HU02-C16, HU02-C17

### HU02-R07 — Registro das tentativas observadas

O sistema registra identificação, data e hora na impressão, na exclusão confirmada, na exportação e nas tentativas bloqueadas por falha de comunicação ou por falta de permissão.

Demonstrada por: HU02-C03, HU02-C07, HU02-C09, HU02-C10, HU02-C13, HU02-C16, HU02-C17, HU02-C21

### HU02-R08 — Padrão de impressão da AIH

A AIH impressa segue o padrão de formato e conteúdo do Ministério da Saúde para esse documento.

Demonstrada por: HU02-C09

### HU02-R09 — Quem exclui

Somente "Contas Médicas" ou "Administrador" exclui uma AIH.

Demonstrada por: HU02-C12, HU02-C19, HU02-C20, HU02-C21

### HU02-R10 — Motivo obrigatório

A exclusão só se conclui com o motivo preenchido.

Demonstrada por: HU02-C12, HU02-C13, HU02-C14

### HU02-R11 — Efeito da exclusão confirmada

A exclusão confirmada retira a AIH da listagem do atendimento e guarda o motivo informado.

Demonstrada por: HU02-C13, HU02-C15

### HU02-R12 — Confirmação antes de excluir

Nenhuma exclusão de AIH ocorre sem a confirmação explícita.

Demonstrada por: HU02-C12

## 5. Outras Informações Relevantes

### HU02-I01 — Tela de detalhes do atendimento

- **Caráter:** Ilustrativo
- **Alvo:** `[REFERÊNCIA INDISPONÍVEL: hu002_-_tela_detalhes_do_atendimento.png]`

### HU02-I02 — Modelo de AIH impressa

- **Caráter:** Ilustrativo
- **Alvo:** `[REFERÊNCIA INDISPONÍVEL: hu002_modelo_nova_aih.png]`

O padrão exigido no aceite está em HU02-R08 e em HU02-C09. Esta imagem não substitui esse padrão.

### HU02-I03 — Prontuário

- **Caráter:** Ilustrativo
- **Alvo:** `[REFERÊNCIA INDISPONÍVEL: hu002_pront_eletron_simplif_paciente.png]`

### HU02-I04 — Layout de exportação

- **Caráter:** Ilustrativo
- **Alvo:** `[REFERÊNCIA INDISPONÍVEL: Anexo IV]`

HU02-C16 cita esse layout. O arquivo não está no pacote e o conteúdo dele não foi presumido.

## 6. O que esta História NÃO cobre

- Criação e edição do conteúdo de uma AIH nova. O botão "Criar Nova AIH" aparece no aceite; o preenchimento da AIH fica fora.
- Edição dos campos de uma AIH já listada. "Editar" aparece para o perfil autorizado; o formulário de edição fica fora.

## 7. Suposições e Dúvidas Abertas

- `[CONFIRMAR]` Texto da mensagem quando não há AIH para impressão, em HU02-C11. Impacto: o aceite da seção vazia de impressão não tem frase verificável.
- `[CONFIRMAR]` A criação de nova AIH depende de existirem procedimentos além do gerador da AIH inicial, ou o botão fica disponível sempre que o perfil é autorizado. Os cenários mostram o botão sem esse dado. Impacto: o desenvolvedor teria de decidir quando habilitar "Criar Nova AIH".

## 8. Lista de atualizações

| Autor | Data | Descrição |
| --- | --- | --- |
| Angela Maria Amador | — | Versão de origem, com os comportamentos deste exemplo. |
| Alinhamento de forma | 2026-10-19 | Identificador `HU-02`, seções 1 a 8, um evento por cenário, regras sem roteiro de tela e referências visuais marcadas como ilustrativas. Nenhuma mensagem nova foi escrita. |
