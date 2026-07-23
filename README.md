# Detecção de E-mails de Phishing

Este repositório contém o projeto prático de classificação binária focado em identificar e-mails maliciosos (phishing) para evitar o comprometimento de credenciais e sistemas. Utilizamos o dataset "Phishing Email" do Kaggle para treinar e validar os modelos.

## 🚀 Como executar
Todo o código foi estruturado para rodar de forma simples e direta no Google Colab, sem necessidade de instalações locais.

1. Faça o download do arquivo `.ipynb` deste repositório.
2. Acesse o [Google Colab](https://colab.research.google.com/).
3. Vá em **Arquivo > Fazer upload de notebook** e selecione o arquivo baixado.
4. Execute as células sequencialmente. A base de dados será carregada automaticamente a partir da nuvem.

## 🛠️ Tecnologias e Arquitetura
* **Linguagem:** Python
* **Bibliotecas Principais:** Pandas, Scikit-Learn, Matplotlib, Seaborn
* **Modelagem:** Implementamos uma arquitetura de `Pipeline` integrando o `TfidfVectorizer` e o `SGDClassifier`. Essa escolha foi essencial para isolar o processo de vetorização de palavras exclusivamente no conjunto de treino, prevenindo qualquer vazamento de dados (*data leakage*) para o conjunto de teste.

## 👥 Divisão de Tarefas
* **Sidnei Silva Golçalves Junior:** Responsável pelo tratamento inicial da estrutura da base (remoção de índices nulos) e plotagem visual da análise exploratória.
* **Danilo Campos Deichmann:** Responsável pelo núcleo lógico e modelagem, executando a transformação dos dados, particionamento estratificado, construção do Pipeline (prevenção de vazamento) e busca de hiperparâmetros.
* **José Marcos Bittencourt Oliveira Prado:** Responsável pela inferência e diagnóstico final, interpretação da matriz de confusão e formulação técnica das limitações do modelo em produção.

## 🤖 Declaração de Uso de Inteligência Artificial
A inteligência artificial foi utilizada de forma assistida e validada pelo grupo para acelerar etapas pontuais do desenvolvimento:
* **Decisão Arquitetural:** Compreensão e aplicação do conceito de `Pipeline` no Scikit-Learn para integrar a vetorização TF-IDF ao classificador de forma segura.
* **Formatação:** Apoio na estruturação visual dos blocos de texto (Markdown) para atender fielmente aos tópicos exigidos no edital.
Nenhum código gerado foi incluído sem revisão prévia, e a lógica analítica por trás das escolhas permaneceu sob responsabilidade da equipe.
