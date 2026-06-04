# 📊 Análise de Sentimento em Avaliações de E-commerce (AWS)

[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)](https://pandas.pydata.org/)
[![Hugging Face](https://img.shields.io/badge/Hugging%20Face-FFD21E?style=for-the-badge&logo=huggingface&logoColor=black)](https://huggingface.co/)
[![AWS](https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)](https://aws.amazon.com/)

> **Projeto prático de NLP (Processamento de Linguagem Natural) focado em avaliar o grau de satisfação de clientes através de reviews, comparando modelos de Machine Learning e abordagens baseadas em Léxico.**

---

## 💡 Sobre o Projeto

Este projeto foi desenvolvido com o objetivo de realizar uma **Análise de Sentimento** profunda sobre um robusto banco de dados relacional de avaliações de um E-commerce brasileiro (operando em arquitetura AWS). Através da extração, limpeza e processamento de comentários e notas (1 a 5 estrelas), o projeto compara o desempenho, a precisão e a viabilidade computacional de três abordagens diferentes de IA para o idioma português:

1. **VADER** (Valence Aware Dictionary and sEntiment Reasoner)
2. **LeIA** (Léxico para Inferência Adaptada - fork otimizado para PT-BR)
3. **Transformers** (Modelo `nlptown/bert-base-multilingual-uncased-sentiment` utilizando arquitetura PyTorch via Hugging Face)

Através desta análise técnica, não apenas extraímos o sentimento do consumidor (Positivo, Neutro, Negativo), mas também avaliamos a capacidade de cada modelo em lidar com as nuances, sarcasmos e complexidades inerentes à língua portuguesa, gerando *insights* aplicáveis para tomada de decisão no ambiente de negócios.

---

## 👥 Equipe do Projeto

Projeto desenvolvido colaborativamente por:
* **[Kauã Marques Rodrigues](https://www.linkedin.com/in/kauamrodrigues/)**
* **[Sofia de Souza Carvalho](https://www.linkedin.com/in/sofiascarvalho/)**
* **[Rafael Cremasco Serrão da Silva](https://www.linkedin.com/in/rafael-cremasco074/)**
* **[Julia Miranda da Silva Santana](https://www.linkedin.com/in/julia-miranda-a9aa44401/)**

---

## 🎯 Objetivos

* **Engenharia de Dados (ETL):** Extração, consolidação e higienização de dados textuais estruturados e não estruturados (`review_comment_title` e `review_comment_message`), com remoção de ruídos e acentuação.
* **Análise Exploratória (EDA):** Entendimento da distribuição de avaliações e comportamento do consumidor a partir de quase 100 mil registros.
* **Modelagem NLP:** Aplicação escalável e comparação de modelos baseados em dicionário léxico contra modelos avançados de Redes Neurais baseados em atenção (Transformers).
* **Business Intelligence:** Traduzir a performance computacional e as discrepâncias das IAs em recomendações de negócio sólidas.

---

## 🛠️ Tecnologias e Ferramentas

* **Linguagem & Manipulação:** `Python 3`, `Pandas`, `NumPy`
* **Visualização de Dados:** `Matplotlib`, `Seaborn`
* **Processamento de Linguagem Natural (NLP):** * `vaderSentiment`
  * `leia-br`
  * `transformers` / `torch` (Hugging Face)
* **Ambiente & Infraestrutura:** Jupyter Notebook / Google Colab (com aceleração de GPU T4 para inferência otimizada em *batches*).

---

## ⚙️ Metodologia e Pipeline

1. **Coleta e Modelagem Relacional:** Leitura de múltiplas tabelas (Clientes, Pedidos, Itens, Avaliações, Pagamentos, Geolocalização, Vendedores).
2. **Feature Engineering:**
   Mapeamento matemático das notas de avaliação (1 a 5 estrelas) para uma pontuação contínua de -1.0 (Extremamente Negativo) a 1.0 (Extremamente Positivo), criando um *baseline* (gabarito) real para avaliar os modelos.
3. **Inferência NLP Otimizada:**
   Cálculo do *Polarity Score* utilizando processamento progressivo (`tqdm`). Para o modelo BERT (Transformer), foi implementado o processamento em lotes (*batches*) garantindo velocidade e alocação eficiente da memória VRAM da GPU.
4. **Avaliação e Benchmark (Discrepâncias):**
   Mapeamento analítico de contradições (ex: o cliente dá 1 estrela, mas a IA classifica o texto como positivo).

---

## 📈 Resultados e Insights Principais

Após processar milhares de avaliações reais, o projeto revelou *insights* estratégicos cruciais sobre o uso de IAs na análise de sentimento:

* **O Desafio do Idioma:** O português, rico em ironia, sarcasmo e duplo sentido, é uma barreira complexa. Modelos simples baseados puramente em contagem de palavras não compreendem contextos ambíguos.
* **Modelos Léxicos (VADER e LeIA):** O VADER apresentou o menor percentual de precisão para a base brasileira. O modelo **LeIA**, contudo, apresentou um excelente custo-benefício, entregando resultados intermediários sólidos com baixíssimo custo de processamento.
* **O Poder do Contexto (Transformers):** Apesar do altíssimo custo computacional (dependência de aceleração de hardware/GPU), o modelo Multilingual BERT apresentou a **maior taxa de acerto e sofisticação**. Suas falhas ocorrem apenas em cenários altamente complexos.
* **Veredito de Negócios:** * Para **Big Data em tempo real** onde a velocidade é mais crítica que a precisão absoluta, recomenda-se o uso do modelo **LeIA**.
  * Para **Análise de Churn, Auditoria e Experiência do Cliente (CX)** de alto impacto, o modelo **Transformers** justifica totalmente o seu peso computacional.

---

## 🚀 Como Reproduzir o Projeto

1. Clone o repositório para o seu ambiente local:
```bash

git clone [https://github.com/sofiascarvalho/Projeto_Integrador_AWS.git](https://github.com/sofiascarvalho/Projeto_Integrador_AWS.git)
