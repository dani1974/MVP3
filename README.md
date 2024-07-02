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
O catálogo de dados contém uma descrição detalhada de cada tabela e seus respectivos campos, incluindo os valores mínimos e máximos esperados para dados numéricos e possíveis categorias para dados categóricos.

#### Linhagem dos Dados
- **Fonte dos Dados**: Kaggle
- **Técnica de Coleta**: Download manual seguido de upload para o DBFS
- **Transformações**: Conversões de tipos de dados e normalização

## Carga
Os dados foram carregados para o Data Warehouse utilizando o Databricks. As etapas de ETL (Extração, Transformação e Carga) foram realizadas conforme descrito abaixo:
1. **Extração (Extract)**: Os dados foram extraídos do DBFS.
2. **Transformação (Transform)**: Conversão dos tipos de dados e normalização das avaliações.
3. **Carga (Load)**: Os dados transformados foram carregados para as tabelas no Databricks.

### Documentação das Transformações
- **Conversão de Tipos**: Campos `employees` e `estimated_revenues` convertidos para `int`.
- **Normalização**: Avaliações normalizadas para facilitar a comparação.

**Scripts Utilizados**:
```python
df1 = spark.read.format("csv").option("header", "true").load("dbfs:/FileStore/shared_uploads/danilameirao@gmail.com/Hospital_General_Information-5.csv")
df1.write.format("delta").mode("overwrite").saveAsTable("Hospital_General_Information")


