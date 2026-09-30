# [EXEMPLO RUIM] Criação do Módulo de Chamados

> ⚠️ **CONTRA-EXEMPLO ANOTADO (O QUE NÃO FAZER):**  
> Este documento reúne os 7 erros mais comuns cometidos ao escrever requisitos com IA. Leia os balões de alerta para entender por que este padrão é prejudicial e como corrigi-lo.

---

## 1. Narrativa da História

- **Como** um usuário qualquer do sistema  
  > ❌ **ERRO 1 (Persona Genérica):** *"Usuário qualquer"* não existe. Quem é esse usuário? É o atendente N1 ou o diretor financeiro? As dores e permissões são completamente diferentes.  
  > 🛠️ **Como corrigir:** Use a persona formal: *"Como Rodrigo (Solicitante Interno)"*.

- **Quero** uma tela moderna, fluida e intuitiva para mandar tickets  
  > ❌ **ERRO 2 (Adjetivos Vagos e Termo Proibido):** *"Moderna, fluida e intuitiva"* são julgamentos de gosto que nenhum QA consegue testar. Além disso, usou *"ticket"*, que é um termo proibido no glossário.  
  > 🛠️ **Como corrigir:** Descreva ações concretas e use o termo oficial: *"abrir um chamado técnico anexando prints do erro"*.

- **Para que** eu possa usar o sistema.  
  > ❌ **ERRO 3 (Benefício Tautológico / Vazio):** Não declara nenhum valor de negócio real.  
  > 🛠️ **Como corrigir:** *"Para que a equipe de suporte receba as informações completas de primeira, agilizando o atendimento"*.

---

## 2. Detalhes de Implementação

> O sistema deve criar uma tabela no PostgreSQL chamada `tb_tickets_v2` com os campos `id`, `user_id`, `created_at` e chamar uma API REST via endpoint `POST /api/v1/tickets`. Se a conexão cair, deve salvar em Redis.

> ❌ **ERRO 4 (Invasão Técnica Prematura):** O PO está dizendo aos engenheiros como programar o banco e a API. Isso restringe a arquitetura de engenharia e não agrega valor de negócio.  
> 🛠️ **Como corrigir:** Apague essa seção inteira. Foque no comportamento visível do usuário e nas regras de negócio.

---

## 3. Critérios de Aceite

- O envio deve ser muito rápido e em tempo real.  
  > ❌ **ERRO 5 (Critério Não-Testável):** O que é "muito rápido"? 10 milissegundos ou 5 segundos?  
  > 🛠️ **Como corrigir:** *"O sistema deve gravar a solicitação e responder em menos de 2 segundos."*

- Se der erro, mostrar uma mensagem avisando.  
  > ❌ **ERRO 6 (Caminho de Erro Vago):** Qual erro? Qual a mensagem? O que o usuário deve fazer em seguida?  
  > 🛠️ **Como corrigir:** Especifique o gatilho e o texto exato da mensagem de erro esperada.

- O usuário pode fazer tudo o que precisar na tela.  
  > ❌ **ERRO 7 (Falta de Limites e Estado Vazio):** Sem delimitação de permissões, sem tratamento de estado vazio e sem lista de fora de escopo.
