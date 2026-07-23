# Detecção de E-mails de Phishing

Este repositório contém o projeto prático de classificação binária focado em identificar e-mails maliciosos (phishing) para evitar o comprometimento de credenciais e sistemas. Utilizamos o dataset [Phishing Email](https://www.kaggle.com/datasets/subhajournal/phishingemails/) do Kaggle para treinar e validar os modelos.
**Tipo da Tarefa:** Classificação.

## 👥 Integrantes
* Sidnei Silva Golçalves Junior
* Danilo Campos Deichmann
* José Marcos Bittencourt Oliveira Prado

## 🗂️ Fonte dos Dados e Organização dos Arquivos
* **Fonte dos dados:** Dataset [Phishing Email](https://www.kaggle.com/datasets/subhajournal/phishingemails/) do Kaggle. Os dados são carregados via URL pública diretamente no notebook.
* **Organização dos arquivos:**
  * `deteccao_phishing.ipynb`: Código-fonte contendo a análise exploratória, pré-processamento, modelagem e avaliação.
  * `README.md`: Documentação central do projeto.

## 🚀 Como executar
Todo o código foi estruturado para rodar de forma simples e direta no Google Colab, sem necessidade de instalações locais.

1. Faça o download do arquivo `.ipynb` deste repositório.
2. Acesse o [Google Colab](https://colab.research.google.com/).
3. Vá em **Arquivo > Fazer upload de notebook** e selecione o arquivo baixado.
4. Execute as células sequencialmente. A base de dados será carregada automaticamente a partir da nuvem.

## 🛠️ Modelos Utilizados e Principais Resultados
* **Baseline:** Classificador base (DummyClassifier) utilizado para estabelecer a precisão mínima aceitável.
* **RandomForestClassifier:** Modelo ensemble baseado em árvores de decisão.
* **SGDClassifier:** Modelo linear com regularização L2 (alpha=0.0001), ideal para dados esparsos provenientes de vetorização de texto.

**Comparação de Resultados:**
O desenvolvimento comparou o desempenho da modelagem em duas etapas estruturais:

1. **Sem Pipeline (Teste Inicial):** 
   * O modelo `RandomForestClassifier` obteve um F1-Score de 0.9528, registrando 76 falsos positivos.
   * O modelo `SGDClassifier` obteve um F1-Score de 0.9726, registrando 38 falsos positivos.
2. **Com Pipeline (Modelo Final em Produção):**
   * O encapsulamento do `TfidfVectorizer` e do `SGDClassifier` (otimizado via GridSearchCV com `loss='hinge'`, `penalty='l2'` e `alpha=0.0001`) atingiu um desempenho superior com F1-Score de 0.9759 para a classe de phishing.
   * A matriz de confusão revelou 2168 verdadeiros negativos e apenas 28 falsos positivos, resultando em uma taxa de erro de aproximadamente 1.2% ao classificar e-mails legítimos.

**Conclusão:** O `SGDClassifier` superou o `RandomForestClassifier` na adaptação à esparsidade da matriz TF-IDF. A abordagem final utilizando o `Pipeline` foi mantida como oficial, pois garante a ausência de vazamento de dados (*data leakage*) e demonstrou a melhor capacidade de generalização segura.

## 👥 Divisão de Tarefas
* **Sidnei Silva Golçalves Junior:** [Itens 5.1 a 5.3] Responsável pelo tratamento inicial da estrutura da base (remoção de índices nulos) e plotagem visual da análise exploratória.
* **Danilo Campos Deichmann:** [Itens 5.4 a 5.6] Responsável pelo núcleo lógico e modelagem, executando a transformação dos dados, particionamento estratificado, construção do Pipeline (prevenção de vazamento) e busca de hiperparâmetros (GridSearchCV).
* **José Marcos Bittencourt Oliveira Prado:** [Itens 5.7] Responsável pela inferência e diagnóstico final, interpretação da matriz de confusão e formulação técnica das limitações do modelo em produção.

## 🤖 Declaração de Uso de Inteligência Artificial
* **Ferramenta utilizada:** Modelos de Linguagem (LLMs).
* **Finalidade:** Resolução de impasses técnicos e formatação estrutural da documentação.
* **Parte do trabalho em que foi utilizada:** Decisão arquitetural para a aplicação do conceito de `Pipeline` no Scikit-Learn e estruturação de blocos de texto em Markdown.
* **Forma de verificação do conteúdo:** A inteligência artificial foi utilizada de forma estritamente assistida. Nenhum código gerado foi incluído sem revisão prévia; os blocos foram testados individualmente, e a lógica analítica por trás das escolhas permaneceu sob controle, validação e auditoria manual da equipe.
