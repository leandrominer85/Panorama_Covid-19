[![author](https://img.shields.io/badge/author-LeandroMinervino-red.svg)](https://www.linkedin.com/in/rafael-n-duarte/) [![](https://img.shields.io/badge/python-3.7.12+-blue.svg)](https://www.python.org/downloads/release/python-365/) [![GPLv3 license](https://img.shields.io/badge/License-GPLv3-blue.svg)](http://perso.crans.org/besson/LICENSE.html) [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/rafaelnduarte/portfolio/issues)

<p align="center">
  <img alt="Colaboratory logo" width="40%" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/94/Coronavirus._SARS-CoV-2.png/1024px-Coronavirus._SARS-CoV-2.png">
</p>


# Panorama da COVID-19

A pandemia provocada pelo surgimento do Coronavírus SARS-CoV-2 popularmente conhecida como COVID-19 marcou e continua marcando a história do mundo.

Tendo se iniciado na província chinesa de Wuhan no final de 2019 essa doença rapidamente se espalhou até ser declarada como pandemia oficialmente pela Organização Mundial de Saúde em Março de 2021.

Por se tratar de um vírus resíratório altamente transmissível a COVID-19 rapidamente se alastrou pelo mundo. O parco conhecimento da doença e a inexistência de tratamentos eficazes fez com que houvessem milhões de vítimas ao redor do mundo.





Enquanto um terço das pessoas se apresentam assintomáticas - o que dificulta o real dimensionamento da pandemia - 81% das pessoas com sintomas desenvolvem sintomas moderados e 14% sintomas severos. Já a taxa de mortalidade segue a seguinte distribuição etária:


Grupo Etário | Índice de fatalidade
----------   |  --------
0–34         |	0.004%
35–44        |	0.068%
45–54        |	0.23%
55–64        |	0.75%
65–74        |	2.5%
75–84        |	8.5%
85 +         |	28.3%

<div align="left" >
 <a href="https://en.wikipedia.org/wiki/COVID-19_pandemic#History">fonte: wikipedia</a> </div>


Enquanto a vacinação avança e a pandemia infecta mais pessoas surgem novas variantes. Essas variações do vírus original provocam modificações que podem torná-lo mais infeccioso ou aumentar o seu escape vacinal. Portanto, a maneira mais eficaz de prevenção é o distanciamento social e o uso de medidas profiláticas como uso de máscara.

Ao longo do desenrolar da pandemia podemos ver como está a evolução da doença ao longo do tempo de acordo com os dados. Nesse projeto utilizarei os dados do [Our World in Data](https://github.com/owid/covid-19-data/tree/master/public/data).

Primeiramente farei uma análise geral da base. Posteriormente dividirei o dataset em três grupos: Mundo, Continentes e Países (com foco no Brasil).

O objetivo é explorar a base retirando insights que demonstrem o panomara geral da doença em cada um dos blocos analisados, dando ênfase à análise gráfica. O ponto de partida será uma análise exploratória e a limpeza de dados para  posterior retirada de conclusões.

Todo o código, gráficos e conclusões estão disponíveis no [notebook](Panorama_do_COVID_19.ipynb).

## Dicionário de Variáveis

### Não utilizarei todas as variáveis disponíveis (para mais detalhes atentar para a parte de limpeza dos dados). O Dicionário a seguir é apenas das variáveis restantes:


| Variável                         | Descrição                                                           |
|:---------------------------------|:----------------------------------------------------------------------|
| `total_cases`                    | Total  de casos confirmados de  COVID-19                                     |
| `new_cases`                      | Novos casos confirmados de COVID-19                                       |
| `new_cases_smoothed`             | Novos casos confirmados de COVID-19 (média móvel de 7 dias)                      |
| `total_cases_per_million`        | Total de casos confirmados de COVID-19 por 1,000,000 de pessoas                |
| `new_cases_per_million`          | Novos casos confirmados de COVID-19 por 1,000,000 de pessoas                  |
| `new_cases_smoothed_per_million` | Média móvel de 7 dias de novos casos confirmados de COVID-19 por 1,000,000 de pessoas|
| `total_deaths`                    | Total de mortes atribuídas à COVID-19                                     |
| `new_deaths`                      | Novas de mortes atribuídas à COVID-19                                       |
| `new_deaths_smoothed`             | Novas mortes atribuídas à COVID-19 (média móvel de 7 dias)                      |
| `total_deaths_per_million`        | Total de mortes atribuídas à COVID-19 por 1,000,000 de pessoas                |
| `new_deaths_per_million`          | Novas mortes atribuídas à COVID-19 por 1,000,000 pessoas                  |
| `new_deaths_smoothed_per_million` | Novas mortes atribuídas à COVID-19 (média móvel de 7 dias) por 1,000,000 de pessoas |
| `total_vaccinations`                         | Número total de vacinas de COVID-19 aplicadas                                                                                                                                                                                                                                                                                           |
| `people_vaccinated`                          | Número total de pessoas com pelo menos uma dose de vacina                                                                                                                                                                                                                                                                                     |
| `people_fully_vaccinated`                    | Número total de pessoas com o esquema vacinal completo                                                                                                                                                                                                                                                              |
| `total_boosters`                             | Número total de vacinas de  COVID-19 aplicadas além do esquema vacinal mínimo                                                                                                                                                                                                     |
| `new_vaccinations`                           | Novas vacinas de COVID-19 administradas (calculadas apenas para dias consecutivos)                                                                                                                                                                                                                                                                |
| `new_vaccinations_smoothed`                  | Novas doses de vacinas de COVID-19 administradas (média móvel de 7 dias). Para países que não reportam os dados diariamente assumimos que a mudança se dá de forma equânime nos dias referentes aos dados. Isso produz uma série diária na qual a média diária de sete dias é  retirada |
| `total_vaccinations_per_hundred`             | Número total de vacinas de COVID-19 administradas por 100 pessoas no total da população                                                                                                                                                                                                                                                    |
| `people_vaccinated_per_hundred`              | Pessoas vacinadas por 100 pessoas no total da população                                                                                                                                                                                                                                              |
| `people_fully_vaccinated_per_hundred`        |Pessoas com o esquema vacinal completo por 100 pessoas no total da população                                                                                                                                                                                                                       |
| `total_boosters_per_hundred`                 | Número de vacinas de COVID-19 além do esquema vacinal mínimo aplicadas por 100 pessoas no total da população                                                                                                                                                                                                                                           |
| `new_vaccinations_smoothed_per_million`      | Novas doses de vacinas aplicadas (média móvel de 7 dias) por 1,000,000 pessoas no total da população                                                                                                                                                                                                                                         |
| `new_people_vaccinated_smoothed`             | Número de pessoas recebendo a primeira dose no dia (média móvel de 7 dias)                                                                                                                                                                                                                                                                        |
| `new_people_vaccinated_smoothed_per_hundred` |úmero de pessoas recebendo a primeira dose no dia (média móvel de 7 dias) por 100 pessoas no total da população                                                                                                                                                       
| `iso_code`                   | [ISO 3166-1 alpha-3](https://pt.wikipedia.org/wiki/ISO_3166-1_alfa-3) – código de três letras para os países                                                                                                                                                                                            |
| `continent`                  | Continente correspondente à localidade                                                                                                                                                                                                     |
| `location`                   | Localidade geográfica                                                                                                                                                                                                                      |
| `date`                       | Data da observação                                                                                                                                                                                                                        |
| `population`                 | População (últimos valores disponíveis). Veja: https://github.com/owid/covid-19-data/blob/master/scripts/input/un/population_latest.csv para os dados completos                                                                                |
| `population_density`         | Número de pessoas dividido pela área, medido em Kilometros quadrados, último ano disponível                                                                                                                                           |
| `median_age`                 | Mediana da idade da população, projeçao da ONU para 2020                                                                                                                                                                                       |
| `aged_65_older`              | Parcela da população com mais de 65 , último ano disponível                                                                                                                                                             |
| `aged_70_older`              | Parcela da população com mais de 75 , em 2015                                                                                                                                                                                 |
| `gdp_per_capita`             | Produto doméstico bruto de acordo com a [paridade de poder de compra](https://pt.wikipedia.org/wiki/Paridade_do_poder_de_compra#:~:text=Em%20economia%20a%20paridade%20do,de%20compra%20de%20dois%20pa%C3%ADses.&text=A%20PPC%2C%20ao%20rev%C3%A9s%2C%20leva,diferen%C3%A7as%20no%20custo%20de%20vida.)  (constante para 2011 em dólares americanos), ano mais recente disponível                                                                                                                        |
| `extreme_poverty`            | Percentagem da população vivendo em extrema pobreza, ano mais recente disponível a partir de 2010                                                                                                                                                   |
| `cardiovasc_death_rate`      | Taxa de morte por doenças cardiovasculares em 2017 número anual de mortes por 100,000 pessoas)                                                                                                                                                |
| `diabetes_prevalence`        | Prevalência de diabetes (% da população entre 20 to 79 anos) em 2017                                                                                                                                                                                |
| `female_smokers`             | Percentagem de mulheres fumantes, ano mais recente disponível                                                                                                                                                                                       |
| `male_smokers`               | Percentagem de homens fumantes, ano mais recente disponível                                                                                                                                                                                         |
| `handwashing_facilities`     | Percentagem da população com acesso a instalações para lavagem de mãos no local, ano mais recente disponível                                                                                                                                          |
| `hospital_beds_per_thousand` | Número de leitos disponíveis por 1,000 people, ano mais recente disponível a partir de  2010                                                                                                                                                                      |
| `life_expectancy`            | Expectativa de vida em 2019                                                                                                                                                                                                           |
| `human_development_index`    | [IDH](https://www.br.undp.org/content/brazil/pt/home/idh0.html) - Índice de desenvolvimento humano. Composto por três dimensões básicas do desenvolvimento humano: renda, educação e saúde Valores para 2019, importados de : http://hdr.undp.org/en/indicators/137506 |



## Alguns exemplos de visualizações

Exponho aqui algumas visualizações disponíveis:

Mortes por Covid no mundo:

![image](https://user-images.githubusercontent.com/48839817/145810992-8adc8f31-97fa-4f8b-a62f-ee08d8e15111.png)


Bar Chart Race de casos de Covid por continente:


https://user-images.githubusercontent.com/48839817/145811307-df02fc5e-84cc-4435-9d85-c87b11d9996f.mp4


Gráfico interativo de mortes no Brasil e e, u, país selecionado:

![image](https://user-images.githubusercontent.com/48839817/145812185-05f60e85-3208-4ae7-998f-7b9afe0abe57.png)


## Conclusão

A pandemia causada pela COVID-19 continua infectando e causando mortes pelo mundo. Vimos que os casos e mortes se somam ao longo do tempo mas isso não ocorre de maneira linear. Antes temos as chamdas ondas, com fluxos e refluxos mundiais causados por diversas razões - dentre elas o surgimento de variáveis e vacinas.

Ao fragmentar essa análise para o nível continental ficam claras as diferenças regionais. Vemos como cada onda da doença afetou de maneira diferente essas regiões. A primeira e segunda ondas se pronunciam na Europa com uma forte terceira nas américas e posteriormente as ondas asiáticas que afetaram sobretudo a Índia. Atualmente vemo o Novo Continente liderando em mortes por milhão, seguidos do Velho Continente e da Ásia - Oceania é um caso constante de controle da doença.

Descendo mais um nível de desagregação dos dados chegamos aos países. Mesmo nesse nível as disparidades internas impactam na pandemia. Mas é a partir desse nível que podemos ver mais claramente como as diferentes características afetam o desenvolvimento da pandemia.

O caso brasileiro se apresenta como um dos piores mundialmente. Tendo a primeira infecção detectada em 26 de Fevereiro de 2020 e a primeira morte 20 dias depois, a vacinação só iniciou em 17 de Janeiro de 2021. Após uma primeira onda entre Abril e Outubro de 2020 uma segunda onda mais forte veio próxima de Março de 2021. Essa nova onda alcança um pico em Abril e começa a arrefecer então - em parte pelo avanço da vacinação que nesse mesmo mês começa a acelerar.

Esse cenário coloca o Brasil como segundo país com mais mortes totais atrás de EUA e à frente de Índia e entre os 10 países com mais mortes por milhão de habitantes.

O que leva cada país a ter um cenário melhor ou pior na pandemia ainda é incerto. Mas  a correlação dos dados apontam como possíveis causas a idade da população, a pobreza e doenças cardiovasculares. Outras relações poderiam ser feitas, mas seriam necessários dados mais desagregados para afirmar com maior grau de certeza - como é o caso de mulheres fumantes .




## Software & Bibliotecas

O Projeto utilizou Python 3 e as seguintes bibliotecas:

-   [Pandas](http://pandas.pydata.org/)
-   [Seaborn](https://seaborn.pydata.org/index.html)
-   [Matplotlib](https://matplotlib.org/)
-   [ipywidgets](https://ipywidgets.readthedocs.io/en/latest/)
-   [bar_chart_race](https://pypi.org/project/bar-chart-race/)


**Meus Links:**
* [Artigo desse projeto no Medium](https://epp-minervino.medium.com/an%C3%A1lise-explorat%C3%B3ria-da-covid-19-fac91234ccee)
* [LinkedIn](https://www.linkedin.com/in/leandro-minervino-b469681b/)
* [Colab](https://colab.research.google.com/drive/1o4dzudIzvU1XIkGKI29nh7yPBMh9avuv?usp=sharing)





## Outros Projetos Meus:


* **[Scrap sites de notícia](https://github.com/leandrominer85/Scrap_sites_noticias)**

* **[Políticas Raciais no ensino superior](https://github.com/leandrominer85/Pol-tica-Racial-no-Ensino-Superior-2009-2019-)**
 
* **[Disaster-Response-Pipelines](https://github.com/leandrominer85/Disaster-Response-Pipelines)**

* **[Dados do Airbnb Lisboa](https://github.com/leandrominer85/Dados-do-Airbnb-Lisboa/blob/main/README.md)**
