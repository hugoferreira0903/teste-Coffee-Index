# teste-Coffee-Index

Configuração dos Recursos no Azure
Antes de começar a indexar e buscar informações, precisamos criar e configurar três principais recursos no Azure:
Azure AI Search : Responsável por criar e consultar índices de busca.



Upload dos Documentos no Azure Storage
Os documentos contendo as avaliações dos clientes são armazenados no Azure Blob Storage.
Criamos um Container chamado coffee-reviews.
Subimos os arquivos baixados de um link externo para esse container.
Ativamos o acesso anônimo para facilitar a leitura dos arquivos pelo Azure AI Search.

Importação dos Dados
No portal do Azure, escolhemos a opção "Import data" e conectamos ao Blob Storage.
Definimos um nome para a fonte de dados: coffee-customer-data.
Configuramos a extração de conteúdo e metadados.

Consultando o Índice (Search Explorer)

{
    "search": "*",
    "count": true
}

Retorna todos os documentos do índice, incluindo a contagem total.

{
 "search": "locations:'Chicago'",
 "count": true
}

Filtra os documentos para exibir apenas as avaliações que mencionam "Chicago".

{
 "search": "sentiment:'negative'",
 "count": true
}


Filtra os documentos para exibir somente as avaliações com sentimentos negativos.

Como Funcionam os Filtros e a Relevância dos Resultados?
Filtragem (search)

O sistema busca documentos que contenham os termos específicos no campo indicado (locations, sentiment, etc.).
Se o campo não for marcado como filterable, não pode ser usado para filtragem.
Ordenação pela Relevância (@search.score)

O Azure AI Search ranqueia os documentos conforme a relevância para a consulta.
O @search.score indica quão bem um documento corresponde ao que foi buscado.
Segmentação por Análises de IA

A análise de sentimento permite detectar emoções nas avaliações.
A extração de frases-chave ajuda a identificar os principais tópicos abordados.
A identificação de locais permite buscar avaliações por cidade ou região.

resumo:
Este fluxo permite criar uma solução poderosa para analisar feedbacks de clientes,
entender sentimentos, identificar padrões de reclamações e obter insights valiosos 
de forma automatizada usando o Azure AI Search.
