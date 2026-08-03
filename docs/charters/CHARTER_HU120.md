# 🎯 Test Charter - Sessão Exploratória (HU 120)

**Projeto:** Sistema PDI - Manutenção de Legado 
**Módulo:** PDI > Parte Diária > Procedimentos Diversos > Direitos Humanos e Cidadania
**Timebox:** 45 Minutos
**Sessão / Evidências:** Inserir no Qase
**Ator / Persona:** Agente PRF

---

## 1. 🚀 Missão (Explore...)
**Explorar** a criação e a edição de procedimentos no módulo de Direitos Humanos e Cidadania,
**Com o objetivo de descobrir** falhas na persistência de dados legados (v1.0), quebras de renderização na interface e validações falhas durante a transição para um novo template (v2.0).

## 2. 📋 Regras de Negócios e Validações Chave (Critérios de Aceite)
Durante os 45 minutos, foque em garantir que as seguintes premissas não sejam violadas:
- **RN01 - Blindagem de Legado:** Um procedimento sempre deve ser exibido e editado com a estrutura exata de campos de quando foi criado, ignorando versões posteriores.
- **RN02 - Identidade Visual:** Se o usuário estiver editando um procedimento de uma versão antiga, a interface DEVE apresentar o texto "(Legado)".
- **RN03 - Bloqueio de Alteração:** Não é permitido alterar a estrutura de um template se já houver instâncias (procedimentos preenchidos) vinculadas a ele.
- **RN04 - Vigência Lógica:** A data de início de vigência de uma nova versão deve ser `>=` a data atual do sistema (não é possível vigência retroativa).
- **RN05 - Integridade Estrutural:** Não é possível excluir um template que possua registros vinculados.

## 3. ⚠️ Áreas de Risco 

- **Corrupção de Payload (Risco Alto):** Ao salvar a edição de um documento antigo, o front-end ou back-end tentar injetar/validar os campos exigidos pela nova versão (v2.0), corrompendo o JSON original.
- **Busca e Filtros (Risco Médio):** A busca do sistema pode parar de funcionar se não souber lidar com diferentes formatos de JSON (v1.0 e v2.0 misturados).
- **Relatórios (Risco Médio):** Relatórios que agregam dados podem quebrar ao procurar colunas que só existem no template novo.
- **Carga Inicial / Deploy (Risco Crítico):** O script que associa todos os procedimentos existentes à versão inicial (1.0) falhar, deixando dados órfãos.

## 4. 🗺️ Passo a Passo Sugerido para a Sessão (Guia Tático - Foco Frontend/Caixa Preta)


1. **O Passado (Setup e Validação Inicial):**
   - Acesse um procedimento criado antes do deploy.
   - **Validação de Tela:** Verifique a presença clara do aviso de "(Legado)" na tela.
   - **Validação de Payload:** Abra o F12 (Network). Edite um campo permitido e salve. Verifique se o JSON enviado (Request Payload) e a resposta (Response) mantiveram apenas os campos da versão antiga, sem erros 4xx ou 5xx.

2. **O Futuro (Novos Procedimentos):**
   - Crie um novo procedimento no sistema com o Agente PRF.
   - **Validação:** Confirme visualmente se ele carrega a nova estrutura de campos (v2.0) e não exibe a tag "Legado".

## 5. 📸 Registro no Qase (Coleta de Evidências)
*   **Screenshots:** Print obrigatório da tag "Legado" na interface.
*   **Issues:** Qualquer desvio reportar com rastreabilidade para a HU 120, anexando as evidências acima.