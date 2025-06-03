Este projeto foi desenvolvido como um desafio técnico para um processo seletivo de estágio na área de Análise de Dados. O objetivo principal era analisar uma base de dados do Tribunal Superior Eleitoral (TSE),
abrangendo os anos de 2020 e 2024, referente a candidatos(as) a vereador(a), vice-prefeito(a) e prefeito(a) nas capitais brasileiras.

Com base na análise dos dados do TSE para os anos de 2020 e 2024, utilizando Power BI e as métricas desenvolvidas em DAX, foram obtidas as seguintes respostas para as questões do desafio:

A diversidade nas candidaturas aumentou entre 2020 e 2024?

Observou-se uma queda geral no volume de candidaturas de todos os grupos entre 2020 e 2024. 
Pessoas pardas e pretas mantiveram sua presença nas candidaturas, mas não houve um crescimento proporcional em relação a outros grupos. 
A raça branca ainda representou a maior parcela no gráfico de candidaturas, indicando uma predominância neste aspecto. 
Grupos como indígenas, amarelos e aqueles sem informação de raça/cor seguiram com participação estatisticamente mínima nas candidaturas. 
Mulheres, pessoas negras e indígenas conseguiram se eleger mais em 2024?

Analisando os dados de eleitos em 2020 e 2024, não se constatou um aumento na representatividade de mulheres, pessoas negras ou indígenas entre os eleitos.
Pelo contrário, houve uma queda no número de mulheres negras eleitas: em 2020, foram 86 mulheres negras eleitas (considerando 28 pardas e 20 pretas – nota: a soma 28+20 é 48, verificar se o número 86 ou a discriminação parda/preta está correta ou se refere a categorias mais amplas); em 2024, este número caiu para apenas 8 (5 pardas e 3 pretas).
A eleição de homens negros também apresentou uma queda significativa, passando de 38 eleitos em 2020 para nenhum em 2024.
As candidaturas indígenas não obtiveram representação significativa entre os eleitos nos dois ciclos eleitorais analisados.
Houve diferenças significativas no financiamento (valor arrecadado) por gênero ou raça?

Sim, foram identificadas diferenças significativas no financiamento de campanha por gênero e raça entre 2020 e 2024:
Homens brancos: Arrecadação aumentou de aproximadamente R$ 14,6 bilhões em 2020 para mais de R$ 20 bilhões em 2024. 
Mulheres negras: Arrecadação permaneceu abaixo de R$ 2 bilhões em ambos os anos. 
Mulheres brancas: Arrecadaram R$ 5,4 bilhões em 2024, um valor quase quatro vezes menor que o arrecadado por homens brancos no mesmo ano. 
Indígenas: A arrecadação em 2024 foi inferior a R$ 100 milhões. 
Quais partidos e capitais elegeram o maior número de representantes diversos?

Apesar de avanços pontuais, a análise indicou que a diversidade entre os eleitos ainda está longe de ser equilibrada, com o poder permanecendo concentrado em perfis brancos.
Capitais com maior número de eleitos seguiram elegendo majoritariamente pessoas brancas. Por exemplo:
Recife (PSB): 10 eleitos brancos.
Belo Horizonte, Curitiba, Fortaleza, Natal: 6 eleitos brancos cada.
Campo Grande, Florianópolis, Porto Alegre (MDB): 5 eleitos brancos.
Partidos como PSB, PSD, DEM, MDB e PDT foram predominantes nestes cenários com menor diversidade entre os eleitos.
Em quais capitais houve maior avanço ou retrocesso na diversidade dos eleitos?

Capitais com Baixa Diversidade (predominantemente brancos entre os eleitos):
Rio de Janeiro: Apenas 3 eleitos, todos brancos.
Recife, Belo Horizonte, Curitiba, Florianópolis, Porto Alegre: Eleitos majoritariamente brancos, com partidos como PSB, PSD, DEM, MDB, PDT em destaque.
Capitais com Maior Diversidade (presença mais equilibrada ou boa proporção de grupos não-brancos):
Campo Grande: Apresentou uma presença mais equilibrada de pretos, pardos e brancos entre os eleitos.
João Pessoa, Maceió, Aracaju, Cuiabá, Boa Vista: Mostraram uma boa proporção de pardos e, em alguns casos, amarelos entre os eleitos.
Macapá e Palmas: Registraram uma representação expressiva de pardos entre os eleitos.

Metodologia e Ações Desenvolvidas:

Carregamento dos Dados: Os dados foram importados do Excel para o ambiente Power BI.

Tratamento de Dados: Utilização intensiva do Power Query para limpar, transformar e adequar os dados para análise (ex: padronização de categorias, tratamento de valores ausentes, criação de chaves, etc.).

Modelagem de Dados e Criação de Medidas: Desenvolvimento de um modelo de dados relacional no Power BI e criação de métricas e colunas calculadas em DAX para atender aos objetivos do desafio. As principais métricas incluíram "Soma de Contagem Candidato", "Soma de Valor de Receita". Para a análise específica da diversidade entre os eleitos, foi criada uma coluna calculada chave chamada "Diverso" com a seguinte lógica em DAX:

Snippet de código

Diverso =
IF(
    'Base_RenovaBR_Visualizacoes'[Eleito] = "Eleito" &&
    (
        'Base_RenovaBR_Visualizacoes'[Gênero_Simplificado] = "Feminino" ||
        'Base_RenovaBR_Visualizacoes'[Raça_Simplificada] = "Negra"
    ),
    1,
    0
)
Esta coluna atribui o valor 1 se o candidato foi eleito E se identifica como do gênero feminino OU como de raça negra (considerando sua categorização de "Raça_Simplificada"). Caso contrário, atribui 0. Foram criadas também medidas para calcular o "total de eleitos diversos por cidade em cada ano" e a "diferença na diversidade" entre os anos.

Desenvolvimento de Visualizações: Criação de dashboards com diversos gráficos para apresentar os resultados. A escolha por gráficos de barras, por exemplo, visou a simplicidade e clareza na interpretação dos dados, enquanto gráficos de linha foram usados para mostrar evoluções temporais.

Análise de Resultados: Foco na interpretação dos visuais e métricas para responder às perguntas do desafio.
