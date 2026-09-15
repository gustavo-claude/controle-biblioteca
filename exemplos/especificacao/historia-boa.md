
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
| Angela Maria Amador | 13/07/2026 | Edição do CA002 para adaptação ao que foi implementado pelo CAIO conforme Nota do Redmine, adiciada à tarefa #33236: HU003 - Criar Nova AIH, no dia:17/06/2026,|




### **2. HISTÓRIA DE USUÁRIO**
**COMO** Contas Médicas  
**DEVO** visualizar detalhes de um atendimento  
**PARA** ter acesso às informações do paciente, para fazer as modificações necessárias em relação à produção hospitalar.  

---

### **3. CRITÉRIOS DE ACEITAÇÃO**

#### **CA001 - Visualizar Detalhes do Atendimento á partir da tela Altas Hospitalres**

**DADO QUE** estou na página atendimentos encerrados  
**QUANDO** aciono a opção “Detalhes do Atendimento” para um determinado atendimento  
**ENTÃO** o sistema deve exibir a página de detalhes do atendimento, contendo a seção de dados de identificação do paciente e uma lista com pelo menos uma AIH (Primeira AIH gerada pelo sistema para aquele atendimento), vinculada àquele atendimento (IN001).  
**E** cada item da lista exibida deve conter os campos: Nº da AIH, Data Inicial e Data Final  
**E** deve disponibilizar a opção de Imprimir, Editar e Excluir para cada item da lista (RN002)  
**E** o sistema deve disponibilizar, na página, as opções: Ver Prontuário, Criar Nova AIH, Voltar e Exportar para Autorizador.  


#### **CA002 - Visualizar Detalhes do Atendimento à partir da tela "Em Atendimento"**

**DADO QUE** estou na página atendimentos encerrados  
**QUANDO** aciono a opção “Detalhes do Atendimento” para um determinado atendimento  
**ENTÃO** o sistema deve exibir a página de detalhes do atendimento, contendo a seção de dados de identificação do paciente e uma lista com pelo menos uma AIH (Primeira AIH gerada pelo sistema para aquele atendimento), vinculada àquele atendimento (IN001).  
**E** cada item da lista exibida deve conter os campos: Nº da AIH, Procedimento, Data/Hora Inicial e Data/Hora Final  
**E** deve disponibilizar a opção de Imprimir (RN002)  
**E** o sistema deve disponibilizar, na página, as opções: Ver Prontuário e Voltar.  


#### **CA003 - Ver Prontuário**

**DADO QUE** estou na tela de “Detalhes do Atendimento”  
**E** visualizo as opções disponíveis nessa página  
**QUANDO** aciono a opção “Ver Prontuário”  
**ENTÃO** o sistema deve exibir o prontuário do paciente contendo os dados clínicos e registros vinculados às internações, conforme modelo disponível na **IN003**
**E** após a consulta, deve disponibilizar opção de retorno à tela de “Detalhes do Atendimento” sem perda de contexto.  

#### **CA004 - Funcionamento do botão Voltar à partir da aba Altas Hospitalares**

**DADO QUE** estou na lista Alta Hospitalar  
**E** visualiso as opções diponíveis na tela "Detalhes do Atendimento"  
**QUANDO** clicar na opção “Voltar”  
**ENTÃO** o sistema deve me redirecionar para a lista de Altas Hospitalares, sem perda de contexto  

#### **CA005 - Funcionamento do botão Voltar à partir da aba Em Atendimento**

**DADO QUE** estou na lista de pacientes "Em Atendimento"  
**E** visualiso as opções diponíveis na tela "Detalhes do Atendimento"  
**QUANDO** clicar na opção “Voltar”  
**ENTÃO** o sistema deve me redirecionar para a lista de pacientes "Em atendimento", sem perda de contexto.


#### **CA006 - Imprimir AIH**
**DADO QUE** estou na tela de Detalhes do Atendimento  
**QUANDO** aciono a opção “Imprimir” de um determinado item da lista  
**ENTÃO** o sistema deve gerar um documento em formato PDF, de acordo com o padrão de formato e informações obrigatórios para documento de AIH definidos pelo Ministério da Saúde, conforme IN002  
**E** após impressão do documento, devo permanecer na lista das AIH’s vinculadas àquele atendimento.  

#### **CA007 - Excluir AIH (RN002, RN009, RN0010, RN0011, RN0012)**
**DADO QUE** estou na tela de Detalhes do Atendimento  
**E** tenho perfil com permissão para exclusão  
**QUANDO** aciono a opção "Excluir AIH"  
**ENTÃO** o sistema deve solicitar confirmação da ação por meio da mensagem:  
“Você deseja realmente excluir a AIH Nº [número da AIH] associada ao procedimento [nome do procedimento]?”  
**E** deve apresentar um campo obrigatório para que o usuário informe o motivo da exclusão (ex.: duplicidade, erro de cadastro, cancelamento administrativo…).  
**E** ao confirmar a exclusão, o sistema deve:  
- Fazer a exclusão lógica da AIH.  
- Registrar em log o usuário, data/hora da exclusão e o motivo informado.  
- Retornar à lista de AIHs com a mensagem:  
“AIH excluída com sucesso. Motivo registrado: [texto informado pelo usuário].”  

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

### **5. OUTRAS INFORMAÇÕES RELEVANTES

**IN001 - Modelo de referência para a tela de Detalhes do Atendimento.**

![Tela Detalhes do Atendimento](hu002_-_tela_detalhes_do_atendimento.png)

**IN002: Modelo de referencia para a nova AIH gerada pelo sistema:**

![Nova AIH](hu002_modelo_nova_aih.png)

**IN003: Modelo de Prontuário Eletrônico Simplificado do Paciente:**
![Prontuário Eletônico Simplificado](hu002_pront_eletron_simplif_paciente.png)


---

