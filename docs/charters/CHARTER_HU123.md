# 🎯 Test Charter - Sessão Exploratória (HU 123)

**Projeto:** Sistema PDI - Omissão do Campo "Houve Pessoa Resgatada?" (OTRS_06549189)
**Módulo:** PDI > Parte Diária > Procedimentos Diversos > Direitos Humanos e Cidadania
**Timebox:** 45 Minutos
**Ator / Persona:** Agente PRF

---

## 1. 🚀 Missão (Explore...)
**Explorar** o comportamento dinâmico (visibilidade e persistência) do campo "Houve Pessoa Resgatada?",
**Com o objetivo de descobrir** falhas de renderização no Front-end ao alternar opções de Público Alvo e vazamento de dados inconsistentes (payload) enviados ao Back-end.

## 2. 📋 Pré-condições (Setup)
1. Estar logado no sistema com perfil de Agente PRF (permissão para cadastrar/editar procedimentos).
2. O formulário de "Direitos Humanos e Cidadania" deve estar aberto em modo de criação ou edição.
3. Ferramenta de desenvolvedor (F12 - Aba Network) aberta para inspeção de Caixa Preta.

## 3. ⚠️ Regras de Negócios e Riscos (Critérios de Aceite)
- **RN01 (Ocultação):** Selecionar "Ações para o Público Interno" deve ocultar o checkbox "Houve Pessoa Resgatada?" imediatamente.
- **RN02 (Reexibição):** Alterar a seleção de "Público Interno" para qualquer outro valor deve fazer o checkbox reaparecer imediatamente.
- **RN03 (Persistência Limpa):** Ao salvar o procedimento com o campo oculto, o sistema não deve dar erro e deve persistir o valor como nulo/false (mesmo que estivesse marcado antes).
- **RN04 (Proteção do Legado):** Procedimentos antigos que já tinham esse campo preenchido para ações internas não devem ser impactados na visualização, a menos que o usuário edite o tipo de ação.

## 4. 🗺️ Guia Tático da Sessão (Passo a Passo - Caixa Preta)

**Passo 1: O Efeito Sanfona (Front-end)**
- Em um formulário novo, alterne o "Tipo de Ação" várias vezes entre "Ações para o Público Interno" e outros valores.
- **Validação:** Verifique se o campo "Houve Pessoa Resgatada?" some e aparece de forma fluida, sem quebrar o layout da tela.

**Passo 2: O Teste de Amnésia (Integração Front e Back)**
- Selecione um tipo de ação qualquer (Ex: Público Externo).
- Marque a opção "Houve Pessoa Resgatada?" como VERDADEIRA (Checkbox marcado).
- Agora, mude o tipo de ação para "Ações para o Público Interno" (o checkbox vai sumir).
- Abra a aba Network (F12) e clique em Salvar.
- **Validação:** Inspecione o JSON enviado no Payload. O campo deve ser enviado como `false`, `null` ou simplesmente ser omitido. Não pode ser enviado como `true`. O retorno deve ser Status 200.

**Passo 3: A Máquina do Tempo (Regressão de Legado)**
- Acesse um procedimento antigo (se houver na base de testes) do tipo "Público Interno" onde o campo tenha sido preenchido no passado.
- **Validação:** A tela deve carregar sem erros e não deve forçar a deleção dessa informação até que o usuário ativamente troque o tipo de ação.

## 5. 📸 Evidências Mínimas para o Qase
- Print do JSON (Payload) no momento de salvar (Passo 2), comprovando a sanitização do dado.
- GIF ou pequeno vídeo gravando a tela durante a alternância das opções (Passo 1).