# Glossário — Torre de Controle de Inovação Baldan

Este glossário define os conceitos de negócio, técnicos e métricas de gestão utilizados no sistema **Baldan Innovation Control Tower (MVP)**.

---

## 📊 Conceitos de Gestão e Métricas

### 1. Lentes e Critérios (Lenses & Criteria)
Modelo estratégico de tomada de decisão que divide a avaliação de projetos em blocos temáticos denominados **Lentes**, contendo cada um um conjunto de **Critérios** específicos.
- **Lentes:** Categorias de alto nível (ex.: Estratégia, Mercado, Financeiro, Tecnologia, Execução, Risco, ESG) que agrupam critérios relacionados. Cada lente possui um peso que atua no cálculo final.
- **Critérios:** Parâmetros de avaliação individuais pontuados de 1 a 5 (ex.: Aderência Estratégica, Dor do Produtor, Payback, Complexidade Técnica). 

### 2. Motor 7×40
O algoritmo matemático responsável por processar as avaliações dos projetos. Ele consolida **7 Lentes estratégicas** e **40 Critérios padrão** em uma única nota normalizada de 0 a 100 (**Score**), considerando os pesos individuais das lentes e dos critérios.
$$\text{Score} = \text{round}\left( \frac{\sum (\text{Nota} \times \text{Peso do Critério} \times \text{Peso da Lente})}{\sum (5 \times \text{Peso do Critério} \times \text{Peso da Lente})} \times 100 \right)$$

### 3. TRL (Technology Readiness Level / Nível de Maturidade Tecnológica)
Escala de 1 a 9 usada para avaliar a maturidade de uma tecnologia no contexto agrícola da Baldan:
- **TRL 1 a 3 (Pesquisa/Conceito):** Princípio observado, conceito formulado e prova de conceito.
- **TRL 4 a 6 (Desenvolvimento):** Validação em laboratório, em ambiente relevante e protótipo funcional.
- **TRL 7 a 8 (Validação/Lançamento):** Piloto operacional e sistema qualificado.
- **TRL 9 (Escala):** Produto introduzido com sucesso no mercado.

### 4. SPI (Schedule Performance Index / Índice de Desempenho de Prazo)
Métrica de valor agregado que mede a aderência ao cronograma do projeto.
$$\text{SPI} = \frac{\text{Avanço Real (\%)}}{\text{Avanço Planejado (\%)}}$$
- **SPI ≥ 1.0:** Projeto em dia ou adiantado.
- **0.9 ≤ SPI < 1.0:** Pequeno desvio (Atenção).
- **SPI < 0.9:** Atraso crítico (Crítico).

### 5. CPI (Cost Performance Index / Índice de Desempenho de Custo)
Métrica de valor agregado que avalia a eficiência financeira.
$$\text{CPI} = \frac{\text{Valor Agregado (Budget Planejado} \times \text{Avanço Real)}}{\text{Custo Real (Budget Realizado)}}$$
- **CPI ≥ 1.0:** Projeto executando dentro ou abaixo do orçamento proporcional.
- **CPI < 0.9:** Custo excessivo em relação ao progresso físico entregue.

### 6. Curva S (S-Curve)
Representação gráfica que cruza o progresso planejado acumulado versus o progresso real obtido ao longo do tempo. Serve para diagnosticar visualmente se o projeto está divergindo do plano original.

### 7. Processo Stage-Gate (Fases e Gates)
Fluxo de governança de projetos estruturado em 5 fases sequenciais (Descoberta, Conceituação, Desenvolvimento, Validação, Lançamento), separadas por **Gates**. O avanço entre as fases requer evidências documentadas e aprovação formal do sponsor.

---

## 🛠️ Catálogo de Funções de Código (`mvp-baldan.html`)

O arquivo [mvp-baldan.html](file:///home/victor/Documents/Mensuria/mvp-baldan.html) contém a lógica de estado, cálculos e visualizações do MVP:

### Persistência e Configuração
*   [loadState()](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L309): Lê os dados do `localStorage` ou retorna o estado vazio padrão.
*   [saveState(show)](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L321): Grava o estado no `localStorage` e exibe feedback se `show` for verdadeiro.
*   [defaultConfig()](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L227): Estrutura os pesos iniciais, as 7 lentes com os 40 critérios e as fases/gates padrão.

### Métricas e Cálculos
*   [scoreProject(p)](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L347): Calcula o score 7×40 ponderado de um projeto (0 a 100).
*   [lensScore(p, lens)](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L357): Calcula o score isolado de um projeto dentro de uma lente específica.
*   [spi(p)](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L366) e [cpi(p)](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L371): Calculam os índices SPI e CPI do projeto.
*   [getExceptions()](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L555): Filtra projetos que violam regras de risco (≥ 4), SPI ou CPI (< 0.9), ou que possuem gates atrasados.

### Renderizadores de UI
*   [renderDashboard()](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L470): Exibe os KPIs gerais, o gráfico prioridade x TRL, o funil e a lista de exceções.
*   [scatterPlot(projects)](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L538): Desenha um gráfico SVG dinâmico cruzando Score (Eixo X) e TRL (Eixo Y).
*   [renderPriorizacao()](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L583): Interface de edição de pontuações de critérios por slider e inclusão de novas ideias.
*   [renderTRL()](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L640): Painel explicativo da escala TRL adaptada à Baldan com o calculador rápido de maturidade.
*   [renderReports()](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L777): Gera relatórios textuais formatados em Markdown para exportação rápida.
*   [answerCopilot(q)](file:///home/victor/Documents/Mensuria/mvp-baldan.html#L816): Responde a prompts e perguntas do usuário baseado na análise lógica dos dados locais do portfólio.

---

## 🔍 Falhas Funcionais e Limitações Identificadas (Mapeamento de Pontos Cegos)

Durante a exploração do código, foram identificados os seguintes comportamentos sem ação real ou inconsistências lógicas no MVP:

1.  **Histórico de Updates Oculto (`p.updates`)**
    *   *Falha:* Ações como mover o card no roadmap/funil, editar um campo ou aprovar um gate inserem logs no array `p.updates`. No entanto, este histórico **nunca é renderizado** na UI do MVP, permanecendo oculto nos dados brutos.
2.  **Módulo de Tarefas Estático**
    *   *Falha:* O painel de projetos exibe uma lista de tarefas e pendências, mas não possui controles na UI para adicionar novas tarefas, marcar tarefas existentes como concluídas ou alterar seus responsáveis.
3.  **Calculador de TRL Isolado**
    *   *Falha:* O botão "Sugerir TRL" no avaliador de maturidade calcula o TRL com base em evidências e documentação e o imprime em tela, mas **não fornece opção de atualizar** automaticamente o projeto selecionado com este novo TRL.
4.  **Seletor Inútil de Projeto no Reporte de Portfólio**
    *   *Falha:* Na página de Status Reports, o menu select para escolher um projeto individual continua visível e ativo mesmo quando o modo de relatório selecionado é "Portfólio" (onde o menu não tem nenhuma função prática).
5.  **Gráfico de Dispersão (Scatter Plot) sem Interação**
    *   *Falha:* O mapa SVG Prioridade × TRL exibe belos pontos flutuantes com o nome abreviado de cada projeto, mas não é possível clicar nas bolhas para selecionar ou abrir o respectivo projeto.
6.  **Decisões Semanais Estáticas**
    *   *Falha:* O card "Decisões sugeridas da semana" no painel principal elenca ações corretivas para os projetos problemáticos detectados, mas atua puramente como mostruário de texto, sem links diretos para as áreas de mitigação ou ritos de decisão correspondentes.
