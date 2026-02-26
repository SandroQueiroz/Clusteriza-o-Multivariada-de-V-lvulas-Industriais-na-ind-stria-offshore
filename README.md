#Clusterização Multivariada de Válvulas Industriais: Uma Análise Comparativa entre K-Means e DBSCAN em Plataformas Offshore

#### Aluno: [Sandro Queiroz Borges](https://github.com/SandroQueiroz)
#### Orientadora: [Manoela Kohler](https://github.com/manoelakohler).

---

Trabalho apresentado ao curso [BI MASTER](https://ica.puc-rio.ai/bi-master) como pré-requisito para conclusão de curso e obtenção de crédito na disciplina "Projetos de Sistemas Inteligentes de Apoio à Decisão".

---

### Resumo

Projetos de engenharia integram diversos elementos e softwares para simulação e seleção técnica. Embora cada projeto seja único, muitos padrões entre variáveis se repetem: quando certas grandezas sobem, outras acompanham — o que indica relações passíveis de serem mapeadas e aproveitadas para automação. Contudo, essas relações nem sempre estão explícitas e a integração de ferramentas é incompleta, gerando custo elevado e riscos de preenchimentos manuais. Com o uso de inteligência artificial e bases históricas (ex.: relatório do Valve Wizard com atributos de linha e de válvula), podemos aprender esses padrões e recomendar preenchimentos ou validar coerência de dados, reduzindo esforço de engenharia.

### 1. Objetivo

Iniciar um ambiente de aprendizado aplicado ao catálogo de válvulas, normalizando dados e executando clusterização (K-Means/DBSCAN) para identificar regimes de processo e outliers: dados numéricos (pressão/temperatura/NPS) combinados com categóricos (ex.: presença de sólidos, aromáticos, TYPE, FLUID), compondo um espaço n-dimensional de onde emergem "nuvenzinhas" (clusters).

### 2. Modelagem

(1) Pré-tratamento: padronização de unidades (NPS em polegadas, pressão em bar, temperatura em °C), limpeza de nulos e duplicidades, coerência min ≤ oper ≤ max, vocabulários (TYPE/VALVE_APPLICATION/FLUID). 
(2) Clusterização: K-Means com seleção de k por silhouette e DBSCAN com varredura de eps/min_samples. 
(3) Detecção de outliers (DBSCAN = −1), produzindo lista de revisão de qualidade dos dados.
(4) Geração de fontes auxiliares csv para refinamento das análises

### 3. Resultados e interpretação

A visualização em PCA (Principal Component Analysis) 2D evidencia regimes distintos, rotulados por famílias de válvulas (TYPE_NORM), aplicação (VALVE_APP_NORM)  e fluidos/serviços (FLUID_CODE_NORM) dominantes, enquanto os heatmaps revelam correlações internas (ex.: pressão associada a NPS específicos). Os outliers se destacam como candidatos a dados espúrios ou erros de preenchimento, corroborando a proposta do diálogo. Essa leitura orienta: (i) regras de seleção por regime; (ii) sanidade do cadastro; (iii) priorização de correções onde há maior impacto.
Os dados foram projetados em duas componentes principais extraídas de todas as variáveis relevantes, permitindo uma inspeção visual da separação de grupos. Nos mapas PC1×PC2, observou-se que os clusters identificados por K-Means e por DBSCAN apresentam regiões de alta densidade parcialmente coincidentes, embora o DBSCAN evidencie pontos classificados como ruído (outliers) quando existentes. A inspeção das distribuições de TYPE_NORM, VALVE_APP_NORM e FLUID_CODE_NORM no espaço reduzido indica que certas categorias tendem a se concentrar em sub-regiões específicas, sugerindo correlação entre características técnicas e os agrupamentos.

### 4. Conclusões

Ao reduzir a dependência de preenchimentos manuais e recomendar valores com base em padrões aprendidos, há potencial de economia significativa de HH e mitigação de falhas — em linha com o modelo do resumo anexado. Como continuidade, pode-se incorporar modelos supervisionados (ex.: Gradient Boosting) para inferir atributos e medir importância de variáveis, permitindo explicar “quais features levam à decisão”, com validação pelas disciplinas.

---

Matrícula: 231.101.030

Pontifícia Universidade Católica do Rio de Janeiro

Curso de Pós Graduação *Business Intelligence Master*

