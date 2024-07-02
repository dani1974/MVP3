# MVP Healthcare Analysis

## Objetivo
O objetivo deste trabalho é analisar como diferentes fatores influenciam as avaliações gerais dos hospitais. Pretende-se responder às seguintes perguntas de negócio:
1. Quais são os hospitais com as melhores avaliações gerais?
2. Como as avaliações dos hospitais variam entre diferentes estados e tipos de propriedade dos hospitais?
3. Como a gestão individual e a qualidade do atendimento influenciam as avaliações gerais dos hospitais?

## Busca pelos Dados
Os dados utilizados neste MVP foram obtidos do Kaggle.
- **Fonte dos Dados**: [Kaggle](https://www.kaggle.com/datasets/amritpal24/top-1000-companies-details)
- **Licença de Uso**: [Licença Kaggle](https://www.kaggle.com/datasets/amritpal24/top-1000-companies-details/license)

## Coleta
Os dados foram baixados do Kaggle e armazenados localmente. Posteriormente, foram carregados para o Databricks File System (DBFS) para facilitar o processamento e a análise na nuvem.
- **Fonte dos Dados**: [Kaggle](https://www.kaggle.com/datasets/amritpal24/top-1000-companies-details)
- **Local de Armazenamento**: `dbfs:/FileStore/shared_uploads/danilameirao@gmail.com/Hospital_General_Information-5.csv`
- **Licença de Uso**: [Licença Kaggle](https://www.kaggle.com/datasets/amritpal24/top-1000-companies-details/license)

## Modelagem
Foi construído um modelo de dados em Esquema Estrela para facilitar a análise. O modelo inclui as seguintes tabelas de fatos e dimensões:

### Tabela de Fatos: HealthExpenditures
- **Expense_ID**: Identificação única da despesa.
- **Amount**: Valor da despesa.
- **Category**: Categoria da despesa.
- **Region**: Região onde a despesa foi realizada.
- **Date**: Data da despesa.

### Tabela de Dimensões: Categories
- **Category**: Nome da categoria.
- **Description**: Descrição da categoria.

### Tabela de Dimensões: Regions
- **Region**: Nome da região.
- **State**: Estado associado à região.

### Tabela de Dimensões: Dates
- **Date**: Data da despesa.
- **Year**: Ano da despesa.
- **Month**: Mês da despesa.
- **Quarter**: Trimestre da despesa.

### Catálogo de Dados
O cat
