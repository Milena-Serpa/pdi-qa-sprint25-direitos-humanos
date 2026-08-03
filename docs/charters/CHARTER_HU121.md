# 🎯 Test Charter - Sessão Exploratória (HU 121)

**Projeto:** Sistema PDI - Remoção de Itens do Campo "Temas" (OTRS_06549189)
**Módulo:** PDI > Parte Diária > Procedimentos Diversos > Direitos Humanos e Cidadania
**Timebox:** 45 Minutos
**Ator / Persona:** Agente PRF

---

## 1. 🚀 Missão (Explore...)
**Explorar** o formulário do procedimento de Direitos Humanos e Cidadania,
**Com o objetivo de descobrir** falhas na remoção dos temas obsoletos, impactos indevidos em procedimentos históricos e efeitos colaterais em outros módulos do sistema.

## 2. 📋 Pré-condições (Setup)
Para que esta sessão seja executada com sucesso, garanta que:
1. O usuário tenha acesso ao sistema homologação.
2. Um procedimento prévio "Legado" (criado antes do deploy) que possua os temas "Ações para o Público Interno" ou "Ações para o Público Externo" já selecionados.
3. O analista saiba utilizar a aba Network (F12) do navegador para inspecionar requisições.

## 3. ⚠️ Regras de Negócios e Riscos (Critérios de Aceite)
- **RN01 (Nova Interface):** Ao criar um novo procedimento de Direitos Humanos, os itens "Ações para o Público Interno" e "Ações para o Público Externo" NÃO podem estar visíveis no campo "Temas".
- **RN02 (Proteção Histórica):** Registros criados antes da alteração devem manter os temas selecionados originalmente (para fins de histórico e integridade de dados).
- **RN03 (Segurança Backend):** Se um usuário tentar injetar via requisição (POST/PUT) os IDs dos temas removidos em um formulário novo, o backend deve rejeitar a requisição com erro de validação.
- **RN04 (Isolamento Global):** A remoção dos temas não apaga o tema do banco de dados global, apenas desassocia deste procedimento específico. Outros procedimentos não devem ser impactados.

## 4. 🗺️ Guia Tático da Sessão (Passo a Passo - Caixa Preta)
1. **O Novo (Caminho Feliz):** Inicie a criação de um novo procedimento. Valide visualmente que os dois temas sumiram do campo multiseleção "Temas".
2. **O Passado (Integridade):** Acesse a edição do procedimento antigo mapeado nas pré-condições. Confirme que os temas descontinuados continuam lá e são exibidos corretamente na tela.
3. **O Teste de Regressão (Salvamento do Legado):** No procedimento antigo, edite um campo de texto livre (ex: observação). Abra o F12 (Network) e salve. Confirme se o sistema salvou com sucesso (HTTP 200) e NÃO bloqueou a requisição por conter um tema legado.
4. **O Teste de Isolamento:** Valide a lista de temas em um procedimento de outro tipo (se aplicável). Os temas devem continuar existindo lá.

## 5. 📸 Evidências Mínimas para o Qase
- Print do dropdown "Temas" no formulário novo (provando a ausência dos itens).
- Print do formulário antigo (provando a presença dos itens históricos).
- Qualquer erro (Status 4xx ou 5xx) capturado na aba Network ao tentar salvar um documento legado.