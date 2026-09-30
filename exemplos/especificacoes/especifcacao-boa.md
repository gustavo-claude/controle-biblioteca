> 🌟 **EXEMPLO PADRÃO OURO:**  
> Use este arquivo como modelo de referência para o nível de detalhe, estrutura e precisão esperados de uma história de usuário neste workspace.

---

## **HU002 – Detalhes do Atendimento**

### **1. DESCRIÇÃO**
Essa História serve para dar às contas médicas, acesso rápido às informações detalhadas de um atendimento (dados do paciente, lista de AIH’s, opções de criação de novas AIH’s e geração de arquivo de exportação de informações daquele paciente).

# LISTA DE ATUALIZAÇÕES

| Autor               | Data       | Descrição                                                                                                                                                                                                 |
|---------------------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Angela Maria Amador | --------   | ------------                                                                                                                                                                                               |





### **2. HISTÓRIA DE USUÁRIO**
**COMO** Contas Médicas  
**DEVO** visualizar detalhes de um atendimento  
**PARA** ter acesso às informações do paciente e fazer as modificações necessárias em relação à produção hospitalar.  

---

### **3. CRITÉRIOS DE ACEITAÇÃO**

Cada critério funcional abaixo é estruturado segundo a sequência canônica: **Caminho Feliz**, **Caminhos de Validação e Erro** e **Estado Vazio (Empty State)**, aplicando estritamente a regra BDD/Gherkin:
- **Dado que**: Define o cenário, contexto, estado prévio ou pré-condição do sistema.
- **Quando**: Define a ação voluntária e direta disparada pelo usuário.
- **Então**: Define a ação, resposta observável ou comportamento executado pelo sistema.

---

#### **3.1. CA001: Visualizar Detalhes do Atendimento e Lista de AIHs**

##### **CA001.1: [Caminho Feliz] — Visualização a partir da aba "Altas Hospitalares"**
- **Dado que** estou na lista de atendimentos encerrados ("Altas Hospitalares") com atendimentos cadastrados  
- **Quando** aciono a opção “Detalhes do Atendimento” de um determinado paciente  
- **Então** o sistema exibe a página de detalhes do atendimento com a identificação do paciente e a lista de AIHs vinculadas (IN001)  
- **E** o sistema apresenta para cada AIH listada os campos: Nº da AIH, Data Inicial e Data Final (RN001)  
- **E** o sistema disponibiliza as opções de Imprimir, Editar e Excluir para cada item da listagem (RN002)  
- **E** o sistema disponibiliza os botões de ação: "Ver Prontuário", "Criar Nova AIH", "Voltar" e "Exportar para Autorizador" (RN003, RN004, RN005, RN006)  

##### **CA001.2: [Caminho Feliz] — Visualização a partir da aba "Em Atendimento"**
- **Dado que** estou na lista de pacientes "Em Atendimento" com pacientes listados  
- **Quando** aciono a opção “Detalhes do Atendimento” de um determinado paciente  
- **Então** o sistema exibe a página de detalhes do atendimento com a identificação do paciente e a lista de AIHs vinculadas (IN001)  
- **E** o sistema apresenta para cada AIH listada os campos: Nº da AIH, Procedimento, Data/Hora Inicial e Data/Hora Final (RN001)  
- **E** o sistema disponibiliza a opção de Imprimir para cada item da listagem (RN002)  
- **E** o sistema disponibiliza os botões de ação: "Ver Prontuário" e "Voltar" (RN004, RN005)  

##### **CA001.3: [Caminhos de Validação e Erro] — Falha de comunicação no carregamento dos registros**
- **Dado que** o serviço de banco de dados ou a rede está indisponível na listagem de atendimentos  
- **Quando** aciono a opção “Detalhes do Atendimento” de um determinado paciente  
- **Então** o sistema exibe um alerta orientativo: “Não foi possível carregar os detalhes do atendimento. Tente novamente em instantes.”  
- **E** o sistema mantém visível a opção de retorno à listagem anterior através do botão "Voltar"  
- **E** o sistema registra a falha de comunicação no log de auditoria técnica (RN007)  

##### **CA001.4: [Estado Vazio] — Atendimento sem AIHs cadastradas (Empty State)**
- **Dado que** estou na lista de atendimentos e o paciente selecionado não possui nenhuma AIH vinculada ou cadastrada  
- **Quando** aciono a opção “Detalhes do Atendimento” desse paciente  
- **Então** o sistema exibe normalmente o bloco com os dados de identificação do paciente (RN001)  
- **E** o sistema exibe na área de listagem de AIHs a mensagem orientativa: “Nenhuma AIH vinculada a este atendimento até o momento.”  
- **E** o sistema disponibiliza em destaque o botão “Criar Nova AIH” habilitado para início do faturamento (RN003)  

---

#### **3.2. CA002: Consultar Prontuário do Paciente e Navegação de Retorno**

##### **CA002.1: [Caminho Feliz] — Consulta ao Prontuário Eletrônico Simplificado**
- **Dado que** estou na tela de “Detalhes do Atendimento” com o botão "Ver Prontuário" disponível  
- **Quando** aciono a opção “Ver Prontuário”  
- **Então** o sistema exibe o prontuário eletrônico simplificado do paciente com os dados clínicos e registros de internação (IN003, RN004)  
- **E** o sistema disponibiliza o botão "Voltar" para retorno à tela de detalhes do atendimento sem perda de contexto (RN005)  

##### **CA002.2: [Caminho Feliz] — Retorno à lista de origem sem perda de contexto**
- **Dado que** estou na tela de “Detalhes do Atendimento” tendo navegado a partir de uma lista de origem ("Altas Hospitalares" ou "Em Atendimento")  
- **Quando** aciono o botão “Voltar”  
- **Então** o sistema redireciona a navegação para a respectiva lista de origem (RN005)  
- **E** o sistema preserva os filtros, paginação e contexto da pesquisa anteriormente efetuada (RN005)  

##### **CA002.3: [Caminhos de Validação e Erro] — Indisponibilidade do serviço de prontuário**
- **Dado que** estou na tela de “Detalhes do Atendimento” e o serviço de prontuário eletrônico encontra-se temporariamente indisponível  
- **Quando** aciono a opção “Ver Prontuário”  
- **Então** o sistema exibe a mensagem de alerta: “Serviço de prontuário temporariamente indisponível. Tente novamente em instantes.”  
- **E** o sistema mantém a navegação na tela de “Detalhes do Atendimento”  
- **E** o sistema registra a falha de comunicação no log de eventos (RN007)  

##### **CA002.4: [Estado Vazio] — Prontuário sem anotações clínicas prévias**
- **Dado que** estou na tela de “Detalhes do Atendimento” de um paciente que não possui anotações clínicas prévias registradas  
- **Quando** aciono a opção “Ver Prontuário”  
- **Então** o sistema exibe os dados cadastrais do paciente (IN003)  
- **E** o sistema exibe na área de registros clínicos a mensagem orientativa de estado vazio: “Nenhum registro clínico vinculado até o momento.”  

---

#### **3.3. CA003: Imprimir AIH em Formato PDF**

##### **CA003.1: [Caminho Feliz] — Geração de PDF conforme padrão do Ministério da Saúde**
- **Dado que** estou na tela de “Detalhes do Atendimento” visualizando uma AIH válida na listagem  
- **Quando** aciono a opção “Imprimir” da AIH selecionada  
- **Então** o sistema gera o documento em formato PDF com os padrões e dados obrigatórios definidos pelo Ministério da Saúde (IN002, RN008)  
- **E** o sistema registra em log o usuário autenticado, data/hora e a ação de impressão efetuada (RN007)  
- **E** o sistema mantém a tela de “Detalhes do Atendimento” aberta com a listagem de AIHs preservada  

##### **CA003.2: [Caminhos de Validação e Erro] — Indisponibilidade do serviço gerador de documentos**
- **Dado que** estou na tela de “Detalhes do Atendimento” e o serviço de geração de relatórios PDF está indisponível  
- **Quando** aciono a opção “Imprimir” de uma das AIHs da lista  
- **Então** o sistema exibe a mensagem de erro orientativa: “Não foi possível gerar a impressão da AIH. Contate o suporte ou tente novamente mais tarde.”  
- **E** o sistema grava os detalhes técnicos da ocorrência no log de erros (RN007)  

##### **CA003.3: [Estado Vazio] — Ausência de AIHs para impressão**
- **Dado que** estou na tela de “Detalhes do Atendimento” de um atendimento que não possui nenhuma AIH cadastrada  
- **Quando** visualizo a seção de AIHs do atendimento  
- **Então** o sistema não exibe botões nem opções para impressão de AIH na tela  
- **E** o sistema exibe a mensagem informando a ausência de registros disponíveis para impressão  

---

#### **3.4. CA004: Excluir AIH com Confirmação e Justificativa Obrigatória**

##### **CA004.1: [Caminho Feliz] — Abertura do modal de confirmação de exclusão**
- **Dado que** estou na tela de “Detalhes do Atendimento” com perfil autorizado ("Contas Médicas" ou "Administrador") visualizando a lista de AIHs (RN009)  
- **Quando** aciono a opção "Excluir" em uma das AIHs listadas (RN002)  
- **Então** o sistema exibe o modal de confirmação com a mensagem: “Você deseja realmente excluir a AIH Nº [número da AIH] associada ao procedimento [nome do procedimento]?” (RN0012)  
- **E** o sistema apresenta um campo de texto obrigatório para que o usuário informe o motivo da exclusão (RN0010)  
- **E** o sistema disponibiliza os botões "Confirmar Exclusão" e "Cancelar"  

##### **CA004.2: [Caminho Feliz] — Confirmação da exclusão com registro de motivo**
- **Dado que** estou com o modal de confirmação de exclusão de AIH aberto na tela (RN0012)  
- **Quando** preencho o campo de motivo e aciono o botão "Confirmar Exclusão" (RN0010)  
- **Então** o sistema realiza a exclusão lógica da AIH selecionada (RN0011)  
- **E** o sistema registra em log o usuário autenticado, data/hora da exclusão e o motivo informado (RN007, RN0011)  
- **E** o sistema fecha o modal e exibe na listagem a mensagem de sucesso: “AIH excluída com sucesso. Motivo registrado: [motivo informado].”  

##### **CA004.3: [Caminhos de Validação e Erro] — Confirmação de exclusão com motivo não preenchido**
- **Dado que** estou com o modal de confirmação de exclusão de AIH aberto e o campo de motivo está em branco  
- **Quando** aciono o botão "Confirmar Exclusão"  
- **Então** o sistema bloqueia a confirmação e mantém o modal de exclusão aberto  
- **E** o sistema exibe a mensagem de validação destacada: “O preenchimento do motivo da exclusão é obrigatório.” (RN0010)  
- **E** o sistema não efetua a exclusão lógica nem grava registro de baixa em log  

##### **CA004.4: [Estado Vazio] — Exclusão da única AIH vinculada ao atendimento**
- **Dado que** estou com o modal de confirmação aberto para exclusão da única AIH existente do atendimento (RN009, RN0012)  
- **Quando** preencho o campo de motivo e aciono o botão "Confirmar Exclusão" (RN0010)  
- **Então** o sistema realiza a exclusão lógica da AIH (RN0011)  
- **E** o sistema atualiza a tabela de AIHs exibindo a mensagem orientativa de estado vazio: “Nenhuma AIH vinculada a este atendimento até o momento.”  
- **E** o sistema disponibiliza em destaque o botão “Criar Nova AIH” habilitado (RN003)  

---

#### **3.5. CA005: Exportar Dados do Atendimento para o Autorizador da SESMA**

##### **CA005.1: [Caminho Feliz] — Geração e transmissão de arquivo com sucesso**
- **Dado que** estou na tela de “Detalhes do Atendimento” de um paciente com atendimento encerrado e AIH vinculada  
- **Quando** aciono a opção “Exportar para Autorizador”  
- **Então** o sistema gera o arquivo de integração conforme o layout do Anexo IV e o transmite ao sistema Autorizador da SESMA (RN006)  
- **E** o sistema registra em log o usuário autenticado, data/hora e o status de sucesso da exportação (RN006, RN007)  
- **E** o sistema exibe a mensagem de confirmação: “Dados do atendimento exportados com sucesso para o Autorizador da SESMA.”  

##### **CA005.2: [Caminhos de Validação e Erro] — Indisponibilidade do Autorizador da SESMA**
- **Dado que** estou na tela de “Detalhes do Atendimento” e o serviço externo do Autorizador da SESMA encontra-se indisponível ou inacessível  
- **Quando** aciono a opção “Exportar para Autorizador”  
- **Então** o sistema exibe a mensagem de erro orientativa: “Não foi possível comunicar com o Autorizador da SESMA no momento. Verifique a conexão e tente novamente mais tarde.”  
- **E** o sistema registra no log de erros a tentativa com data/hora, identificação do usuário e status da falha (RN006, RN007)  
- **E** o sistema mantém os dados do atendimento em tela inalterados sem travar a navegação  

##### **CA005.3: [Estado Vazio] — Atendimento sem AIH para exportação**
- **Dado que** estou na tela de “Detalhes do Atendimento” de um paciente que não possui nenhuma AIH vinculada  
- **Quando** visualizo as opções de exportação na tela  
- **Então** o sistema apresenta a opção "Exportar para Autorizador" desabilitada  
- **E** o sistema exibe tooltip orientativo ao posicionar o cursor: “Adicione ao menos uma AIH para habilitar a exportação.”  

---

#### **3.6. CA006: Controle de Acesso e Permissões de Ação**

##### **CA006.1: [Caminho Feliz / Perfil Autorizado] — Disponibilidade de ações restritas para perfis autorizados**
- **Dado que** estou autenticado no sistema com perfil autorizado ("Contas Médicas" ou "Administrador") (RN009)  
- **Quando** visualizo a lista de AIHs na tela de “Detalhes do Atendimento”  
- **Então** o sistema disponibiliza habilitadas as opções de “Editar” e “Excluir” em cada item da listagem (RN002, RN009)  
- **E** o sistema disponibiliza habilitadas as opções “Criar Nova AIH” e “Exportar para Autorizador” (RN003, RN006)  

##### **CA006.2: [Caminhos de Validação e Erro / Perfil Não Autorizado] — Ocultação de ações restritas**
- **Dado que** estou autenticado no sistema com perfil de consulta ou recepção, sem permissão para faturamento (RN009)  
- **Quando** visualizo a tela de “Detalhes do Atendimento”  
- **Então** o sistema oculta os botões “Editar”, “Excluir” e “Criar Nova AIH” (RN002, RN009)  
- **E** o sistema mantém visíveis apenas as ações de consulta e navegação (“Ver Prontuário”, “Imprimir” e “Voltar”)  

##### **CA006.3: [Caminhos de Validação e Erro / Bloqueio] — Tentativa de disparo de ação restrita por perfil não autorizado**
- **Dado que** estou autenticado no sistema com perfil sem permissão para exclusão de AIHs (RN009)  
- **Quando** tento disparar o comando de exclusão de uma AIH por atalho de teclado ou requisição direta  
- **Então** o sistema bloqueia a execução da operação  
- **E** o sistema exibe a mensagem de alerta: “Você não possui permissão para executar esta ação.”  
- **E** o sistema registra a tentativa de acesso não autorizado no log de auditoria (RN007)  

##### **CA006.4: [Estado Vazio] — Perfil autorizado em tela sem AIHs**
- **Dado que** estou autenticado com perfil autorizado ("Contas Médicas" ou "Administrador") e a lista de AIHs do paciente está vazia  
- **Quando** visualizo a tela de “Detalhes do Atendimento”  
- **Então** o sistema exibe em destaque o botão “Criar Nova AIH” habilitado (RN003)  
- **E** o sistema não apresenta ações individuais de “Editar” ou “Excluir” por inexistência de registros na tabela  

---

### **4. REGRAS DE NEGÓCIO**

#### **RN001 - Exibição de dados**
O sistema deve exibir, na tela de detalhamento, os dados de identificação do paciente e a lista de AIHs vinculadas ao atendimento. Cada AIH exibida deve conter obrigatoriamente: Nº da AIH, Procedimento vinculado àquela AIH, Data Inicial e Data Final.  

#### **RN002 - Ações disponíveis**
Para cada AIH listada, o sistema deve disponibilizar as opções: Imprimir, Editar e Excluir. As ações devem respeitar as permissões de perfil do usuário.  

#### **RN003 - Criação de nova AIH**
Sempre que em uma internação forem realizados procedimentos além do gerador da AIH inicial, o sistema deve disponibilizar a opção para criação de nova AIH.  

#### **RN004 - Consulta ao prontuário**
O sistema deve disponibilizar, na tela de detalhamento, opção para consulta ao Prontuário do Paciente.  

#### **RN005 - Navegação sem perda de contexto**
O sistema deve permitir ao usuário navegação com possibilidade de retorno à lista de atendimentos encerrados sem perda de contexto.  

#### **RN006 - Exportação de arquivo**
O sistema deve disponibilizar a opção de exportação de arquivo para o sistema Autorizador da SESMA, para envio dos dados do atendimento conforme layout definido (Anexo IV), com registro. Após exportação, deve registrar em log usuário, data/hora e status da operação.  

#### **RN007 - Registro em log**
Todas as ações realizadas na tela de detalhamento (visualização, impressão, edição, exclusão, criação de nova AIH, exportação) devem ser registradas em log.  

#### **RN008 - Padrão de impressão**
Toda AIH a ser impressa pelo sistema deve obedecer ao padrão de formato e conteúdo estabelecido pelo Ministério da Saúde para esse tipo de documento, devendo estar de acordo com IN002.  

#### **RN009 - Permissão de exclusão**
Apenas usuários com perfil autorizado (Contas Médicas ou Administrador) podem excluir uma AIH.  

#### **RN0010 - Motivo obrigatório**
Toda exclusão de nova AIH criada deve ser acompanhada de um motivo informado pelo usuário.  

#### **RN0011 - Registro de exclusão**
O sistema deve registrar em log: usuário, data/hora da exclusão e motivo informado.  

#### **RN0012 - Confirmação de exclusão**
O sistema deve sempre solicitar confirmação antes de excluir uma AIH.  

---

### **5. OUTRAS INFORMAÇÕES RELEVANTES**

**IN001 - Modelo de referência para a tela de Detalhes do Atendimento.**

![Tela Detalhes do Atendimento](hu002_-_tela_detalhes_do_atendimento.png)

**IN002: Modelo de referencia para a nova AIH gerada pelo sistema:**

![Nova AIH](hu002_modelo_nova_aih.png)

**IN003: Modelo de Prontuário Eletrônico Simplificado do Paciente:**
![Prontuário Eletônico Simplificado](hu002_pront_eletron_simplif_paciente.png)


---

