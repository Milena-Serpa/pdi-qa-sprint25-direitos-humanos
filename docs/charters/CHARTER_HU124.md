# 🎯 Test Charter - Sessão Exploratória (HU 124)

**Projeto:** Sistema PDI - Inclusão de Novos Temas (OTRS_06549189)
**Módulo:** PDI > Parte Diária > Procedimentos Diversos > Direitos Humanos e Cidadania
**Timebox:** 45 Minutos
**Ator / Persona:** Agente PRF

---

## 1. 🚀 Missão (Explore...)
**Explorar** o campo de lista suspensa "Temas",
**Com o objetivo de descobrir** falhas de grafia nos novos itens, substituição indevida de itens antigos, falhas na indexação de busca do componente e erros de persistência (salvamento).

## 2. 📋 Pré-condições (Setup)
1. Estar autenticado no sistema com perfil de Agente PRF.
2. Acessar o módulo "Direitos Humanos e Cidadania".

## 3. ⚠️ Regras de Negócios e Riscos (Critérios de Aceite)
- **RN01 (Adição sem Exclusão):** Os novos temas devem ser inseridos sem a exclusão ou modificação dos temas pré-existentes.
- **RN02 (Fidelidade Semântica):** Os temas devem respeitar rigorosamente a grafia, capitalização e pontuação da solicitação.
- **RN03 (Busca Interna):** O comportamento de "busca" dentro do dropdown deve indexar corretamente também os novos temas.
- **RN04 (Persistência):** O sistema deve salvar o chamado com sucesso utilizando os novos temas, e exibi-los corretamente na tela de detalhes após o salvamento.

## 4. 🗺️ Guia Tático da Sessão (Passo a Passo - Caixa Preta)

**Passo 1: A Auditoria de Grafia e Legado**
- Abra um novo formulário e expanda o dropdown "Temas".
- *Validação:* Verifique se os itens antigos continuam lá. 
- *Validação:* Confira letra por letra os 8 novos itens: "Pessoas com Transtorno do Espectro Autista"; "Povos Originários ou tradicionais"; "Pessoas com Deficiência"; "Pessoas LGBTQIAPN+"; "Idosos"; "Diversidade e Inclusão"; "Combate ao Racismo"; "Violência contra Mulher".

**Passo 2: O Teste de Indexação (Filtro do Dropdown)**
- Com o dropdown aberto, digite trechos específicos dos novos temas (ex: "LGBT", "Autista", "Racismo").
- *Validação:* O dropdown deve filtrar e encontrar as opções rapidamente.

**Passo 3: A Persistência e Recuperação (Caminho Feliz)**
- Selecione um dos novos temas, preencha os demais campos obrigatórios e clique em salvar.
- *Validação:* O sistema deve retornar sucesso. Abra o documento salvo em modo de visualização ou edição e garanta que o tema correto foi recuperado do banco de dados (não pode aparecer em branco ou com ID quebrado).

## 5. 📸 Evidências Mínimas para o Qase
- Print do Dropdown expandido evidenciando a convivência dos itens antigos com os novos.
- Print da tela de detalhe do chamado salvo com um tema novo selecionado.