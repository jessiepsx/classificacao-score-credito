# Classificação de Score de Crédito com Machine Learning

Estudo de caso e desenvolvimento de um pipeline preditivo de ponta a ponta para a fintech fictícia **Data Girls Finance**, focado na otimização da análise de concessão de crédito e mitigação de risco de inadimplência.

---

## 🎯 Objetivo do Projeto
O objetivo principal deste projeto foi desenvolver um modelo supervisionado de Machine Learning capaz de classificar automaticamente o perfil de risco dos clientes em três categorias: **Poor** (Alto Risco), **Standard** (Médio Risco) e **Good** (Baixo Risco). 

A solução visa substituir análises manuais inconsistentes por uma esteira automatizada e escalável, protegendo o caixa da fintech contra calotes sem prejudicar a experiência e a conversão de bons pagadores.

---

## ⚙️ Etapas do Pipeline Desenvolvido

1. **Leitura e Tratamento de Dados:** Identificação e limpeza de ruídos estruturais (como caracteres especiais `_` em colunas numéricas), correção de outliers de idade/contas e inputação de valores nulos utilizando a estratégia da mediana.
2. **Análise Exploratória de Dados (EDA):** Investigação de padrões comportamentais, análise de distribuições financeiras e correlação de recursos através de visualizações gráficas.
3. **Preparação dos Dados (Pre-processing):** Transformação de variáveis categóricas/textuais em formatos numéricos utilizando `LabelEncoder` e divisão dos dados de forma estratificada em 80% para treino e 20% para teste.
4. **Modelagem Preditiva:** Treinamento e ajuste dos algoritmos de classificação baseline *Random Forest* e *XGBoost*.
5. **Avaliação e Métricas:** Análise comparativa focada em matrizes de confusão e relatórios de métricas de negócio (Acurácia, Precisão e Recall).

---

## 🤖 Modelos Testados e Resultados

Abaixo está o comparativo de desempenho dos dois algoritmos avaliados em uma base de testes com 20.000 clientes:

### 🌲 1. Random Forest (Modelo Escolhido)
* **Acurácia Geral:** 79%
* **Métricas por Classe:**
  * **Poor:** Precisão: 74% | Recall: 72%
  * **Standard:** Precisão: 78% | Recall: 80%
  * **Good:** Precisão: 81% | Recall: 80%

### 🚀 2. XGBoost
* **Acurácia Geral:** 75%
* **Métricas por Classe:**
  * **Poor:** Precisão: 66% | Recall: 69%
  * **Standard:** Precisão: 76% | Recall: 73%
  * **Good:** Precisão: 78% | Recall: 78%

### 🏆 Justificativa de Escolha
O modelo **Random Forest** foi selecionado para o ambiente de produção por superar o XGBoost em todas as frentes de teste. Para a saúde financeira da fintech, a classe de maior criticidade é a `Poor`. A Random Forest obteve maior Precisão (74% vs 66%) e maior Recall (72% vs 69%) nesta categoria, reduzindo drasticamente a incidência de falsos positivos perigosos (aprovar crédito para clientes com alto potencial de inadimplência).

---

## Principais Insights e Respostas de Negócio

* **Variáveis Decisivas:** O gráfico de importância de recursos revelou que o comportamento histórico do cliente, especificamente as variáveis `Delay_from_due_date` (Dias médios de atraso) e `Num_of_Delayed_Payment` (Número de pagamentos atrasados), impacta mais a decisão do modelo do que a renda declarada de forma isolada.
* **Perfil do Cliente 'Poor':** Clientes com média de atraso superior a 15 dias, múltiplos pagamentos pendentes e alta taxa de endividamento ativo (`Outstanding_Debt`) têm probabilidade acentuada de inadimplência.
* **Ganhos de Operação:** Automatizar a triagem com 79% de acurácia permite criar regras de aprovação instantânea para o perfil `Good` e direcionar propostas limítrofes (`Poor`) para mesas de auditoria humana especializada, otimizando o tempo da equipe.

---

## Tecnologias Utilizadas

* **Linguagem:** Python
* **Ambiente:** Google Colab / Jupyter Notebook
* **Bibliotecas de Manipulação e Visuais:** Pandas, NumPy, Matplotlib, Seaborn
* **Machine Learning:** Scikit-Learn, XGBoost

---

## Recomendações Práticas para a Fintech

1. **Implementação Imediata:** Integrar a Random Forest na esteira principal de análise de crédito como o primeiro filtro automatizado de propostas.
2. **Cobrança Preventiva:** Disparar réguas de notificação preventiva e dicas de finanças para clientes cujos indicadores comportamentais de dias de atraso começarem a subir na base, agindo de forma proativa antes que o score mude para `Poor`.
3. **Transparência e Governança:** Garantir o direito à explicabilidade do cliente. Recomenda-se o estudo futuro com ferramentas como SHAP ou LIME para detalhar visualmente os motivos de negativas de crédito, garantindo uma inteligência artificial ética e livre de vieses.

---

### Autora
* **Nome:** Jessica Pereira
* **Formação:** Análise e Desenvolvimento de Sistemas (ADS)
