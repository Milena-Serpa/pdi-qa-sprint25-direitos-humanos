# 🎯 Test Charter - Sessão Exploratória (HU 122)

**Projeto:** Sistema PDI - Incluir campo obrigatório "Público Alvo" (OTRS_06549189)
**Módulo:** PDI > Parte Diária > Procedimentos Diversos > Direitos Humanos e Cidadania
**Timebox:** 45 Minutos
**Ator / Persona:** Agente PRF

---

## 1. 🚀 Missão (Explore...)
**Explorar** a inclusão e o comportamento do novo campo "Público Alvo" no formulário,
**Com o objetivo de descobrir** falhas na validação de obrigatoriedade (bypasses), problemas de layout na renderização do Dropdown e falhas na atualização de procedimentos antigos (legado).

## 2. 📋 Pré-condições (Setup)
1. Estar autenticado no sistema com perfil de Agente PRF.
2. Acessar o módulo de criação de "Direitos Humanos e Cidadania".
3. Mapear, no banco de dados, pelo menos um procedimento antigo criado antes da implantação desta HU.

## 3. ⚠️ Regras de Negócios e Riscos (Critérios de Aceite)
- **RN01 (Layout e Opções):** O campo "Público Alvo" deve ser uma lista suspensa (dropdown) de seleção única contendo apenas "Ações para o Público Interno" e "Ações para o Público Externo" (nessa exata ordem).
- **RN02 (Obrigatoriedade - Criação):** O sistema DEVE bloquear o salvamento e exibir a mensagem de erro ("O campo 'Público Alvo' é obrigatório...") caso o usuário tente salvar um novo formulário sem selecionar uma opção.
- **RN03 (Obrigatoriedade - Edição):** Ao editar um documento antigo (que não tinha esse campo), o sistema deve exibi-lo em branco e OBRIGAR o preenchimento para permitir o salvamento das edições.
- **RN04 (Restrições de Input):** Não pode ser possível selecionar ambas as opções e não existe opção "Outros" ou "Não se aplica".

## 4. 🗺️ Guia Tático da Sessão (Passo a Passo - Caixa Preta)

**Passo 1: O Teste de Integridade Visual**
- Abra a tela de criação. Verifique a posição do campo (deve estar entre "Trecho" e o checkbox de ESCA).
- Clique no dropdown e valide a ordem e a exclusividade das duas opções. 

**Passo 2: O Bypass do Front-end (Teste Negativo)**
- Preencha todos os campos obrigatórios do formulário, **exceto** o campo "Público Alvo".
- Clique em Salvar. 
- *Validação:* Confirme o bloqueio na tela e a exibição da mensagem de erro amigável. Inspecione a aba Network (F12) para garantir que a requisição POST não foi enviada para o servidor.

**Passo 3: A Atualização do Passado (Teste de Edição)**
- Abra a edição do procedimento antigo (Legado).
- *Validação:* O campo deve aparecer em branco. Altere uma observação qualquer e tente salvar sem preencher o Público Alvo. O sistema deve bloquear. Escolha uma opção e salve com sucesso.

## 5. 📸 Evidências Mínimas para o Qase
- Print da tela exibindo a mensagem de erro de obrigatoriedade.
- Print do Dropdown expandido mostrando as opções na ordem correta.