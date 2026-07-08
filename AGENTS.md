# Manual do Agente IA — Desenvolvimento Mensuria / Baldan

Este guia orienta agentes autônomos sobre como atuar, expandir e dar manutenção no projeto **Baldan Innovation Control Tower**.

---

## 🏗️ Arquitetura do Projeto

O MVP atual é estruturado como uma **Single-Page Application (SPA)** encapsulada em um único arquivo HTML ([mvp-baldan.html](file:///home/victor/Documents/Mensuria/mvp-baldan.html)):
- **Visualização (View):** Elementos HTML `<section class="page">` gerenciados por classes CSS `.active` que definem visibilidade (`display: block` ou `display: none`).
- **Estado (State):** Um objeto global na variável `state` contendo configurações do motor 7×40, lista de projetos ativos, histórico de chat do copiloto e estados de UI.
- **Persistência:** Sincronização local síncrona com `localStorage` via chave única `baldan_innovation_control_tower_mvp_v1`.
- **Ritos de Renderização:** O fluxo é reativo unidirecional simulado:
  1. Alteração de dados pelo usuário chama um modificador de estado (ex.: `updateScore`).
  2. Modificador chama `saveState(false)` para persistir localmente.
  3. Modificador chama `renderAll()` (ou a função de renderização específica) para remontar o HTML dinâmico das páginas usando template strings.

---

## 🎨 Diretrizes de Design e Identidade Visual (Baldan)

Ao criar novos componentes, modais ou telas, **você deve seguir estritamente** o guia de identidade visual definido em [baldan-visual-identity.md](file:///home/victor/Documents/Mensuria/baldan-visual-identity.md) e [SKILL.md](file:///home/victor/Documents/Mensuria/skills/baldan-visual-identity/SKILL.md):

1.  **Cores Primárias:**
    *   Vermelho Principal: `#CB0A26` / `rgb(203, 10, 38)`
    *   Vermelho Hover/Escuro: `#AF0F2A` / `rgb(175, 15, 42)`
2.  **Cores de Fundo:**
    *   Bege Claro (premium): `#F5EDE3` / `rgb(245, 237, 227)`
    *   Bege Médio (cards): `#ECE3D6` / `rgb(236, 227, 214)`
3.  **Tipografia:**
    *   Sans-serif para corpo e controles: `effra`, `ui-sans-serif`, `system-ui`.
    *   Serif itálica estilizada para títulos: `freight-macro-pro` ou `Georgia` em itálico e negrito (ex.: `h1 i { font-family: Georgia, serif; font-style: italic; }`).
4.  **Assinatura de Layout (Chanfro Baldan):**
    *   Em vez de simples cantos arredondados, utilize a propriedade `clip-path` para criar o canto chanfrado oficial em containers proeminentes e cabeçalhos:
    ```css
    .baldan-angled-container {
      clip-path: polygon(24px 0, 100% 0, 100% calc(100% - 24px), calc(100% - 24px) 100%, 0 100%, 0 24px);
    }
    ```

---

## 🛠️ Boas Práticas para Desenvolvimento

Ao modificar o código-fonte, siga estas regras de engenharia de software:

*   **Não quebre o isolamento local:** O MVP deve permanecer funcional offline e carregável diretamente de um arquivo local. Não introduza dependências de rede externas (como CDNs não confiáveis ou APIs pagas) sem autorização expressa do usuário.
*   **Segurança de Escrita:** Sempre trate dados sensíveis utilizando a função de escape `esc(value)` antes de injetar variáveis em templates HTML dinâmicos para prevenir vulnerabilidades de XSS.
*   **Atualização do Pipeline:** Toda alteração de estado estrutural que impacte o painel geral deve invocar `renderAll()` para que todas as abas reflitam as métricas calculadas em tempo de execução (como SPI, CPI, Médias e Exceções).
*   **Preservação de Comentários:** Mantenha a estrutura modular e os comentários explicativos sobre os gates e TRLs aplicados à Baldan.

---