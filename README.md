# LAB-AI-900-SEARCH-DOC
Neste LAB, aplicamos técnicas de organização de documentos e realizamos pesquisas através da ingestão de dados, seguindo três passos essenciais: 
- Ingestão de conhecimento de IA;
- Criação do índice correspondente; e 
- Exploração dessas funcionalidades.

# Desenvolvimento do LAB
A solução relacionada ao Fourth Coffee requer os seguintes **recursos de assinatura do Azure:**
- Um recurso do Azure AI Search, que gerenciará a indexação e a consulta.
- Um recurso de serviços de IA do Azure, que fornece serviços de IA para habilidades que a solução de pesquisa pode usar para enriquecer os dados com insights gerados por IA.
- Uma conta de armazenamento com contêineres de blobs, que armazenará documentos brutos e outras coleções de tabelas, objetos ou arquivos.

#### Carregar documentos para o armazenamento do Azure:
- Em Containers, adicionar um novo Conteiner;
- Nome: coffeereviews
- Nível de acesso público: Container (acesso de leitura anônimo para containers e blobs)
- Baixar as **avaliações de café compactadas** em [https://aka.ms/mslearn-coffee-reviews](https://aka.ms/mslearn-coffee-reviews);
- Carregar no Conteiner as avaliações.

#### Indexar os documentos:
Depois de armazenar os documentos, vamos utilizar o Azure AI Search para extrair insights dos documentos.
- **Importar dados** na página de **Visão geral**, no Portal do Azure (recurso Azure AI Search);
- Conectar aos dados, selecionando a fonte de dados criada em **Azure Blob Storage**;
- Fonte de dados: Armazenamento de Blobs do Azure
- Nome da fonte de dados: coffee-customer-data
- Dados a extrair: Conteúdo e metadados
- Modo de análise: Padrão
- Criar um indexador de nome **coffeeindexer**
- Selecionar **Enviar** para criar a fonte de dados, o conjunto de habilidades, o índice e o indexador.

#### Consultar o índice:
- Alterar a visualização para **JSON view**;
- No campo do **editor de sonsultas JSON**, realizar uma consulta de todos os documentos, a partir do código:
```
{
    "search": "*",
    "count": true
}
```
- Agora vamos filtrar por localização. No campo do **editor de consultas JSON**, inserir o código:
```
{
 "search": "locations:'Chicago'",
 "count": true
}
```
- Agora vamos filtrar por sentimento. No campo do **editor de consultas JSON**, inserir o código:
```
{
 "search": "sentiment:'negative'",
 "count": true
}
```
# Resultados
Ao executar o _Import data wizard_, criamos um armazenamento de conhecimento. Dentro do armazenamento de conhecimento, pudemos encontrar os dados enriquecidos extraídos pelas habilidades de IA que persistem na forma de projeções e tabelas. 
Além disso, é possível observar as palavras-chave que o armazenamento de conhecimento conseguiu capturar do conteúdo das avaliações. Essas palavras-chave podem ser vinculadas a tabelas como um banco de dados relacional.
