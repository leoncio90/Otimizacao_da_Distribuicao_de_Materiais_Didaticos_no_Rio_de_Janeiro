# Otimização da Distribuição de Materiais Didáticos no Rio de Janeiro


Este projeto foi desenvolvido para uma consultoria de dados, com o objetivo de otimizar a logística de distribuição de materiais didáticos para as escolas da cidade do Rio de Janeiro. A tarefa principal envolveu o tratamento e a padronização de dados provenientes de diversas fontes, seguida pela definição de uma rota otimizada para a entrega dos materiais.

1. Coleta e Entendimento Inicial dos Dados:

O projeto iniciou-se com o recebimento de três conjuntos de dados essenciais:

escolas.csv: Continha informações cadastrais das escolas, como ID, nome, endereço e coordenadas geográficas.
subprefeituras.csv: Apresentava a relação entre os bairros da cidade e suas respectivas subprefeituras.
material_didatico.csv: Detalhava a quantidade de material didático destinada a cada escola.
2. Tratamento e Padronização dos Dados:

Esta foi uma etapa crucial para garantir a qualidade e consistência das informações, seguindo as normas definidas pelo cliente:

Unificação dos Dados: Os três arquivos CSV foram carregados e, em seguida, as informações foram consolidadas. O dataset de escolas foi mesclado com o de material didático, utilizando o ID da escola como chave. Posteriormente, este conjunto de dados foi enriquecido com as informações das subprefeituras, baseando-se no bairro de cada escola.
Padronização de Nomes de Colunas: Todas as colunas foram renomeadas para o formato snake_case (ex: "Nome da Escola" para "nome_da_escola").
Formatação de Strings:
Todas as strings foram convertidas para letras maiúsculas.
Acentos e caracteres especiais foram removidos para garantir a uniformidade.
Padronização de Logradouros: Abreviações comuns em nomes de logradouros foram substituídas por suas formas extensas (ex: "R." para "RUA", "AV." para "AVENIDA").
Separação de Endereço: A coluna de endereço original foi dividida para criar colunas distintas para "logradouro" e "número", facilitando a análise e a utilização em sistemas de roteirização.
Formatação de IDs: Os IDs das escolas foram padronizados como strings contendo sempre três caracteres, com zeros à esquerda quando necessário (ex: "24" para "024").
Precisão Geográfica: As colunas de latitude e longitude foram ajustadas para conter, no máximo, cinco casas decimais, otimizando o armazenamento e a precisão necessária para a roteirização.
Identificação do Tipo de Escola: Uma nova coluna "tipo_da_escola" foi criada, extraindo a sigla do tipo de instituição (EM, CIEP ou COLÉGIO) a partir do nome da escola.
Limpeza de Dados Ausentes: Foi realizada a verificação e o tratamento de valores ausentes, garantindo a integridade do dataset final. Por exemplo, escolas sem bairro ou subprefeitura associada após as mesclagens foram identificadas.
3. Cálculo de Materiais por Subprefeitura:

Para auxiliar na contabilização de custos e na logística regional, foi gerado um segundo arquivo CSV. Este arquivo totalizou a quantidade de material didático a ser entregue em cada subprefeitura, agrupando os dados processados e somando as quantidades correspondentes.

4. Otimização de Rota:

Com os dados devidamente tratados e enriquecidos, o foco direcionou-se para a otimização da rota de entrega. Embora o foco principal do projeto tenha sido o tratamento dos dados, foi implementada uma heurística para ordenar as escolas. Para este projeto, foi selecionada uma escola como ponto de partida (depósito) e, a partir dela, as demais escolas foram ordenadas utilizando um algoritmo de "vizinho mais próximo" de forma simplificada. Este método calcula iterativamente a próxima escola a ser visitada como aquela mais próxima da última escola visitada, até que todas as escolas tenham sido incluídas na rota.

5. Geração dos Produtos Finais:

Ao final do processo, foram entregues os seguintes artefatos:

Arquivo CSV com Rota Otimizada (escolas_ordenadas.csv): Este arquivo contém os dados das escolas já ordenados de acordo com a rota de entrega sugerida. As colunas incluídas foram: id_escola, nome_escola, tipo_escola, logradouro_entrega, numero, bairro, subprefeitura, latitude, longitude e quantidade_material_didatico. Todos os dados seguiram rigorosamente os padrões de formatação especificados.
Arquivo CSV com Total de Material por Subprefeitura: Um arquivo consolidando a quantidade total de material escolar por subprefeitura.
(Desafio) Visualização da Rota: Como parte do desafio, foi gerado um gráfico (plot) representando visualmente a melhor rota encontrada. Este plot exibe as escolas como pontos em um mapa, conectados na sequência de entrega otimizada, partindo de um ponto de depósito inicial. Foram ajustados os limites dos eixos para melhor visualização da área do Rio de Janeiro.
Conclusão:

O projeto culminou na entrega de dados limpos, padronizados e organizados de forma a facilitar a operação logística de distribuição de materiais didáticos. A rota otimizada, juntamente com a sumarização de materiais por subprefeitura, fornece informações valiosas para a tomada de decisão, visando a eficiência e a redução de custos no processo de entrega. O tratamento meticuloso dos dados assegurou a confiabilidade das informações utilizadas na etapa de otimização e nos relatórios gerados.