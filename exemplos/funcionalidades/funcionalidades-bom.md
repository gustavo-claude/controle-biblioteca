# Lista de Funcionalidades do Produto: Classificação de Risco

> 📋 **Contexto e Origem:**  
> Documento elaborado pelo `@facilitador` com base nos documentos de `contexto/` e estruturado conforme o exemplo `exemplos/funcionalidades/funcionalidades-bom.md`.

---

## 4. Lista de Funcionalidades com Problemas e Benefícios


| ID       | Funcionalidade                                            | Descrição                                                                                                                                                                                                      | Problema que Resolve                                                                                                                               | Benefícios que Traz                                                                                                                                      |
| -------- | --------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **F001** | Iniciar triagem de classificação de risco do paciente recepcionado | Localizar e selecionar pacientes recepcionados na unidade de pronto atendimento para iniciar a triagem de classificação de risco.                                                                              | Falta de integração entre o fluxo de chegada na recepção e o setor de triagem, com risco de desencontro ou atraso na avaliação inicial.            | Continuidade fluida no fluxo assistencial, agilidade na convocação do paciente e garantia de que todo paciente recepcionado seja avaliado.               |
| **F002** | Registrar sinais vitais e queixa principal do paciente | Registrar a queixa principal e os parâmetros de sinais vitais (ex.: pressão arterial, temperatura, frequência cardíaca, frequência respiratória e saturação) do paciente.                                      | Falta de projeção clínica baseada em evidências objetivas e ausência de dados padronizados para embasar a tomada de decisão assistencial.          | Padronização dos parâmetros clínicos essenciais, subsídio consistente para estratificação do risco e aumento da segurança do paciente.                   |
| **F003** | Atribuir grau de risco Manchester do paciente | Apoiar o enfermeiro na seleção de fluxogramas e discriminadores inspirados no Protocolo de Manchester para atribuição do nível/cor de gravidade, assegurando a autonomia de validação final pelo profissional. | Atendimento realizado exclusivamente por ordem cronológica de chegada, expondo pacientes com risco de morte ou agravo grave a esperas inadequadas. | Priorização do atendimento conforme a gravidade clínica real, redução do risco de eventos adversos na espera e uniformidade na aplicação do protocolo.   |
| **F004** | Organizar fila priorizada do atendimento médico | Disponibilizar e organizar a fila de espera para consultórios médicos em tempo real, ordenada prioritariamente pelo grau de gravidade (nível de risco) e secundariamente pelo tempo de espera.                 | Desorganização no fluxo de urgência e dificuldade da equipe médica em identificar imediatamente os casos clínicos mais críticos.                   | Redução drástica do tempo de espera para casos graves, visibilidade imediata da fila para os médicos e otimização dos recursos assistenciais da unidade. |
| **F005** | Atualizar nível de gravidade do paciente em espera | Permitir ao enfermeiro reavaliar parâmetros clínicos e atualizar o nível de gravidade de pacientes que continuam aguardando atendimento médico. ⚠️ [SUPOSIÇÃO]                                                 | Deterioração do estado clínico do paciente durante o tempo de espera sem a respectiva elevação da prioridade na fila médica.                       | Monitoramento contínuo da fila de espera, adaptação imediata da urgência frente a mudanças no quadro clínico e prevenção de agravamentos desassistidos.  |
| **F006** | Restringir execução da classificação de risco ao enfermeiro habilitado | Restringir as permissões de execução, validação e alteração da classificação de risco estritamente a profissionais enfermeiros habilitados e autorizados no sistema.                                           | Risco ético, legal e assistencial de realização ou alteração de triagem clínica por pessoas ou papéis não qualificados tecnicamente.               | Estrita conformidade com a regulamentação do exercício profissional da enfermagem, rastreabilidade e segurança jurídica e assistencial.                  |
| **F007** | Apresentar indicadores de tempo da triagem e da consulta médica | Apresentar indicadores em tempo real do tempo decorrido entre recepção e triagem, e do tempo de espera para consulta médica frente aos limites preconizados por cor/risco. ⚠️ [SUPOSIÇÃO]                      | Falta de visibilidade operacional sobre o estrangulamento da triagem e risco de descumprimento dos tempos máximos recomendados para atendimento.   | Suporte direto à meta de redução do tempo de triagem, alerta para casos críticos com tempo limite próximo do estouro e apoio à gestão do fluxo da UPA.   |


---



### Limites e Não-Escopo Respeitados (Conforme `briefing.md`)

- ❌ **Sem Diagnóstico ou Prescrição:** Nenhuma funcionalidade realiza diagnóstico médico, prescrição medicamentosa ou definição de conduta terapêutica.
- ❌ **Sem Substituição Profissional:** O sistema apoia a aplicação de diretrizes (Manchester), mas a decisão final é sempre do Enfermeiro.
- ❌ **Sem Gestão Hospitalar Externa:** Não abrange controle de farmácia/estoque, contas/faturamento, folha de pagamento, internação ou regulação de leitos.
- ❌ **Sem Substituição de Prontuário:** A triagem clínica não elimina a obrigatoriedade de registro e documentação formal no prontuário médico/assistencial.

