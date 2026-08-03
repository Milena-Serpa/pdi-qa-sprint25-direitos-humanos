# 🚀 Estratégia de Qualidade de Software (QA) - Sprint 25 (Direitos Humanos)

> **Projeto:** Sistema PDI  
> **Módulo:** Direitos Humanos e Cidadania (HUs 120 a 124)  
> **Abordagem:** Testes Exploratórios Baseados em Charters (SBTM) & Gestão via Qase.io  
> **Responsável / QA Lead:** Milena Serpa  
> **Status:** 🟡 Em Execução de Testes de Interface e Negócio  

---

## 📌 1. Visão Geral
Este repositório consolida a documentação técnica de QA referente à **Sprint 25 - Módulo de Direitos Humanos e Cidadania** do sistema PDI.

Diante da estratégia atual de validação de interface e regras de negócio, a atuação está estruturada em dois pilares:
1. **GitHub (Git):** Documentação do plano de testes, mapeamento de riscos de tela e cartas de testes exploratórios (Charters)
2. **Qase.io:** Execução detalhada dos casos de teste passo a passo, controle da equipe de estagiários e armazenamento centralizado de evidências visuais (prints).

---

## 🛠️ 2. Mapeamento de Histórias e Charters

| ID HU | Descrição da História | Charter de Teste Exploratório | Execução e Evidências (Qase.io) |
| :--- | :--- | :--- | :--- |
| **HU_120** | Manutenção de Legado (Versionamento) | 📄 [Acessar Charter HU_120](./docs/charters/CHARTER_HU120.md) | 🔗 [Ver Suíte no Qase.io](https://app.qase.io/project/S25?suite=1) |
| **HU_121** | Remoção de Itens Obsoletos no Campo "Temas" | 📄 [Acessar Charter HU_121](./docs/charters/CHARTER_HU121.md) | 🔗 [Ver Suíte no Qase.io](https://app.qase.io/project/S25?suite=2) |
| **HU_122** | Inclusão do Campo Obrigatório "Público Alvo" | 📄 [Acessar Charter HU_122](./docs/charters/CHARTER_HU122.md) | 🔗 [Ver Suíte no Qase.io](https://app.qase.io/project/S25?suite=3) |
| **HU_123** | Omissão Condicional do Campo "Resgatada?" | 📄 [Acessar Charter HU_123](./docs/charters/CHARTER_HU123.md) | 🔗 [Ver Suíte no Qase.io](https://app.qase.io/project/S25?suite=4) |
| **HU_124** | Inclusão dos 8 Novos Temas | 📄 [Acessar Charter HU_124](./docs/charters/CHARTER_HU124.md) | 🔗 [Ver Suíte no Qase.io](https://app.qase.io/project/S25?suite=5) |

---

## 🎯 3. Fluxo de Trabalho Integrado

```text
┌───────────────────────────────────────────────────────────┐
│                     GITHUB (Git)                          │
│  - Leitura do Charter da HU pelo Analista/Estagiário      │
│  - Orientação sobre o que explorar, Timebox e Riscos      │
└─────────────────────────────┬─────────────────────────────┘
│
▼
┌───────────────────────────────────────────────────────────┐
│                       QASE.IO                             │
│  - Execução dos Casos de Teste Passo a Passo              │
│  - Anexo de Prints e Evidências Visuais (PASS / FAIL)     │
│  - Registro de Defeitos e Inconsistências de Requisito    │
└───────────────────────────────────────────────────────────┘
---

## 👥 4. Instruções para a Equipe de Testes (Estagiários)

1. **Consulte o Charter:** Abra o arquivo correspondente em `docs/charters/` para entender o objetivo e os pontos de atenção da HU.
2. **Respeite o Timebox:** Cada sessão exploratória tem duração padrão de **45 minutos**.
3. **Execute no Qase.io:** Acesse a suíte do projeto no Qase.io, inicie o *Test Run* e marque o resultado (*Passed* ou *Failed*).
4. **Anexe a Evidência:** Todo caso executado **DEVE** ter ao menos 1 print anexado no Qase.io comprovando a validação visual da tela.

---

## 📂 5. Estrutura de Arquivos
```text
├── docs/
│   └── charters/
│       ├── CHARTER_HU120.md
│       ├── CHARTER_HU121.md
│       ├── CHARTER_HU122.md
│       ├── CHARTER_HU123.md
│       └── CHARTER_HU124.md
└── README.md