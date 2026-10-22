# Lista de Funcionalidades do Produto: Classificação de Risco

> 📋 **Contexto e Origem:**  
> Documento elaborado pelo `@facilitador` com base nos documentos de `contexto/` e estruturado conforme o exemplo `exemplos/funcionalidades/funcionalidades-bom.md`.
> Validação dos passos: pendente do @analista.

---

## Lista de Funcionalidades com Problemas, Benefícios e Passos

### Módulo Triagem

#### Enfermeira triadora

##### **F001** — Iniciar triagem de classificação de risco do paciente recepcionado

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Iniciar triagem de classificação de risco do paciente recepcionado |
| **Descrição** | Localizar e selecionar pacientes recepcionados na unidade de pronto atendimento para iniciar a triagem de classificação de risco. |
| **Problema que Resolve** | Falta de integração entre o fluxo de chegada na recepção e o setor de triagem, com risco de desencontro ou atraso na avaliação inicial. |
| **Benefícios que Traz** | Continuidade fluida no fluxo assistencial, agilidade na convocação do paciente e garantia de que todo paciente recepcionado seja avaliado. |
| **Passos** | 1. Localizar os pacientes recepcionados na unidade<br>2. Selecionar o paciente recepcionado<br>3. Iniciar a triagem de classificação de risco |

##### **F002** — Registrar sinais vitais e queixa principal do paciente

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Registrar sinais vitais e queixa principal do paciente |
| **Descrição** | Registrar a queixa principal e os parâmetros de sinais vitais (ex.: pressão arterial, temperatura, frequência cardíaca, frequência respiratória e saturação) do paciente. |
| **Problema que Resolve** | Falta de projeção clínica baseada em evidências objetivas e ausência de dados padronizados para embasar a tomada de decisão assistencial. |
| **Benefícios que Traz** | Padronização dos parâmetros clínicos essenciais, subsídio consistente para estratificação do risco e aumento da segurança do paciente. |
| **Passos** | 1. Registrar a queixa principal do paciente<br>2. Registrar os parâmetros de sinais vitais do paciente |

##### **F003** — Atribuir grau de risco Manchester do paciente

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Atribuir grau de risco Manchester do paciente |
| **Descrição** | Apoiar o enfermeiro na seleção de fluxogramas e discriminadores inspirados no Protocolo de Manchester para atribuição do nível/cor de gravidade, assegurando a autonomia de validação final pelo profissional. |
| **Problema que Resolve** | Atendimento realizado exclusivamente por ordem cronológica de chegada, expondo pacientes com risco de morte ou agravo grave a esperas inadequadas. |
| **Benefícios que Traz** | Priorização do atendimento conforme a gravidade clínica real, redução do risco de eventos adversos na espera e uniformidade na aplicação do protocolo. |
| **Passos** | 1. Selecionar o fluxograma do Protocolo de Manchester<br>2. Selecionar o discriminador do fluxograma<br>3. Validar o nível de gravidade do paciente |

### Módulo Fila de classificados

#### Médico plantonista da sala clínica

##### **F004** — Organizar fila priorizada do atendimento médico

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Organizar fila priorizada do atendimento médico |
| **Descrição** | Disponibilizar e organizar a fila de espera para consultórios médicos em tempo real, ordenada prioritariamente pelo grau de gravidade (nível de risco) e secundariamente pelo tempo de espera. |
| **Problema que Resolve** | Desorganização no fluxo de urgência e dificuldade da equipe médica em identificar imediatamente os casos clínicos mais críticos. |
| **Benefícios que Traz** | Redução drástica do tempo de espera para casos graves, visibilidade imediata da fila para os médicos e otimização dos recursos assistenciais da unidade. |
| **Passos** | 1. Acessar a fila de espera do atendimento médico<br>2. Ver a ordenação pelo grau de gravidade<br>3. Ver a ordenação pelo tempo de espera |

#### Enfermeira triadora

##### **F005** — Atualizar nível de gravidade do paciente em espera

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Atualizar nível de gravidade do paciente em espera |
| **Descrição** | Permitir ao enfermeiro reavaliar parâmetros clínicos e atualizar o nível de gravidade de pacientes que continuam aguardando atendimento médico. ⚠️ [SUPOSIÇÃO] |
| **Problema que Resolve** | Deterioração do estado clínico do paciente durante o tempo de espera sem a respectiva elevação da prioridade na fila médica. |
| **Benefícios que Traz** | Monitoramento contínuo da fila de espera, adaptação imediata da urgência frente a mudanças no quadro clínico e prevenção de agravamentos desassistidos. |
| **Passos** | 1. Reavaliar os parâmetros clínicos do paciente em espera<br>2. Atualizar o nível de gravidade do paciente |

##### **F006** — Restringir execução da classificação de risco ao enfermeiro habilitado

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Restringir execução da classificação de risco ao enfermeiro habilitado |
| **Descrição** | Restringir as permissões de execução, validação e alteração da classificação de risco estritamente a profissionais enfermeiros habilitados e autorizados no sistema. |
| **Problema que Resolve** | Risco ético, legal e assistencial de realização ou alteração de triagem clínica por pessoas ou papéis não qualificados tecnicamente. |
| **Benefícios que Traz** | Estrita conformidade com a regulamentação do exercício profissional da enfermagem, rastreabilidade e segurança jurídica e assistencial. |
| **Passos** | 1. Se o profissional não for enfermeiro habilitado e autorizado:<br>1a. Recusar a execução da classificação de risco e encerre<br>Senão:<br>1b. Permitir a execução da classificação de risco e siga para o passo 2<br>2. Permitir a validação da classificação de risco<br>3. Permitir a alteração da classificação de risco |

#### Coordenador de enfermagem da unidade

##### **F007** — Apresentar indicadores de tempo da triagem e da consulta médica

| Categoria | Conteúdo |
| --- | --- |
| **Funcionalidade** | Apresentar indicadores de tempo da triagem e da consulta médica |
| **Descrição** | Apresentar indicadores em tempo real do tempo decorrido entre recepção e triagem, e do tempo de espera para consulta médica frente aos limites preconizados por cor/risco. ⚠️ [SUPOSIÇÃO] |
| **Problema que Resolve** | Falta de visibilidade operacional sobre o estrangulamento da triagem e risco de descumprimento dos tempos máximos recomendados para atendimento. |
| **Benefícios que Traz** | Suporte direto à meta de redução do tempo de triagem, alerta para casos críticos com tempo limite próximo do estouro e apoio à gestão do fluxo da UPA. |
| **Passos** | 1. Ver o tempo decorrido entre a recepção e a triagem<br>2. Ver o tempo de espera para a consulta médica<br>3. Ver esses tempos frente aos limites preconizados por cor de risco |

---

### Limites e Não-Escopo Respeitados (Conforme `briefing.md`)

- ❌ **Sem Diagnóstico ou Prescrição:** Nenhuma funcionalidade realiza diagnóstico médico, prescrição medicamentosa ou definição de conduta terapêutica.
- ❌ **Sem Substituição Profissional:** O sistema apoia a aplicação de diretrizes (Manchester), mas a decisão final é sempre do Enfermeiro.
- ❌ **Sem Gestão Hospitalar Externa:** Não abrange controle de farmácia/estoque, contas/faturamento, folha de pagamento, internação ou regulação de leitos.
- ❌ **Sem Substituição de Prontuário:** A triagem clínica não elimina a obrigatoriedade de registro e documentação formal no prontuário médico/assistencial.
