
<!-- README.md is generated from README.Rmd. Please edit that file -->

# MODELAGEM COMPUTACIONAL DA CONCENTRAÇÃO ATMOSFÉRICA DE CO<sub>2</sub> e CH<sub>4</sub> NO BRASIL CENTRAL

**Resumo**: As mudanças climáticas globais são uma preocupação mundial
constante, sendo a principal causa o aumento da concentração de gases de
efeito estufa (GEE) na atmosfera, especialmente o dióxido de carbono
(CO<sub>2</sub>) e o metano (CH<sub>4</sub>). Para implementar medidas
eficientes de mitigação das emissões de GEE, é fundamental compreender a
dinâmica desses gases na atmosfera e estabelecer relações com outras
variáveis associadas ao sistema solo-planta-atmosfera. Nesse contexto,
diversos esforços têm sido realizados para aprimorar as técnicas de
monitoramento de GEE em escala global e regional. Esta proposta tem como
objetivo descrever a variabilidade espaçotemporal das concentrações
atmosféricas de CO<sub>2</sub> e CH<sub>4</sub> em áreas do Brasil
Central, identificando fontes e possíveis sumidouros desses gases ao
longo dos anos de 2015 a 2023. Serão adquiridos dados das concentrações
atmosféricas de CO<sub>2</sub> (X<sub>CO2</sub>) e CH<sub>4</sub>
(X<sub>CH4</sub>) a partir dos sensores orbitais GOSAT e OCO-2. Em
adição, dados das variáveis climáticas serão obtidos na plataforma da
Agência Espacial Americana (NASA). Para todos os setores emissores de
GEE, os dados serão obtidos a partir dos relatórios da plataforma
Climate TRACE, coalizão sem fins lucrativos capaz de rastrear e fornecer
informações sobre as emissões de GEE globalmente. A aquisição dos dados
será sistematizada para redução das diferenças entre as resoluções
espaciais dos dados de sensoriamento remoto, com posterior remoção da
tendência mundial de X<sub>CO2</sub> e X<sub>CH4</sub>. Para exploração
dos dados adquiridos, serão utilizadas técnicas exploratórias
multivariadas e análise geoestatística, implementadas em linguagem R. A
interrelação entre as variáveis analisadas será descrita por de
reconhecimento de padrão, que incluíram análises de agrupamento
hierárquico e não-hierárquico, análise de componentes principais
associadas aos padrões de variabilidade espacial. Espera-se que essa
abordagem contribua para melhorar a compreensão da dinâmica dos gases de
efeito estufa na atmosfera e suas interações com variáveis climáticas e
de uso da terra no Brasil Central, auxiliando na formulação de políticas
públicas voltadas para a mitigação das emissões de GEE e,
principalmente, a adaptação às mudanças climáticas.

**Objetivo**: Analisar a variabilidade espaçotemporal das concentrações
atmosféricas de CO<sub>2</sub> e CH<sub>4</sub> em áreas do Brasil
Central, identificando fontes e possíveis sumidouros desses gases ao
longo dos anos de 2015 a 2023, bem como suas relações com índices
vegetativos e climáticos, por meio de dados de GOSAT, OCO-2 e Climate
TRACE.

## 👨‍🔬 Autores

- **Pedro Henrique Marucio de Oliveira**  
  Graduando em Agronomia - FCAV/Unesp  
  Email: [pedro.marucio@unesp.br](mailto:pedro.marucio@unesp.b)

- **Prof. Dr. Alan Rodrigo Panosso**  
  Coorientador — Departamento de Ciências Exatas - FCAV/Unesp  
  Email: <alan.panosso@unesp.br>

## 📁 Etapas do Projeto

Os scripts abaixo foram desenvolvidos em RMarkdown e estão disponíveis
em formato HTML:

- **Aquisição e download dos dados brutos**
  - [GOSAT](https://data.ceda.ac.uk/neodc/gosat/data/ch4/nceov1.0/CH4_GOS_OCPR/):
    Dados de concentração de CH<sub>4</sub> 2009 a 2021  
  - [OCO-2](https://disc.gsfc.nasa.gov): Dados de concentração de
    XCO<sub>2</sub>
    (<https://disc.gsfc.nasa.gov/datasets/OCO2_L2_Lite_FP_11.2r/summary?keywords=OCO2>)
    e SIF (<a
    href="https://disc.gsfc.nasa.gov/datasets/OCO2_L2_Lite_SIF_11r/summary?keywords=OCO2\"
    class="uri">https://disc.gsfc.nasa.gov/datasets/OCO2_L2_Lite_SIF_11r/summary?keywords=OCO2\</a>
  - [Climate TRACE](https://climatetrace.org/): Dados de emissões de GEE
    de 2015 a 2022  
  - [AppEEARS](https://appeears.earthdatacloud.nasa.gov/task/point):
    Variáveis climáticas e vegetativas  
  - [NASA](https://climate.nasa.gov/): Dados climáticos  
  - [NASA-FIRMS](https://firms.modaps.eosdis.nasa.gov): Dados de focos
    de incêndio de 2015 a 2025  
  - [BDQUEIMADAS](https://terrabrasilis.dpi.inpe.br/queimadas/bdqueimadas/#exportar-dados):
    Dados de focos de incêndio de 2015 a 2025  
  - [DETER](https://terrabrasilis.dpi.inpe.br/downloads/): Dados de
    focos de fogo (cicatriz de queimadas)  
  - [Programa Queimadas - INPE - Plataforma
    Terrabrasilis](https://terrabrasilis.dpi.inpe.br/queimadas/portal/):
    Dados de focos de queimadas x Supressão da vegetação nativa de
    08/2018 a 01/2025 & Dados de focos de fogo ativo de 1998 a
    21/01/2025  
  - [Desmatamento - INPE - PRODES - Plataforma
    Terrabrasilis](https://terrabrasilis.dpi.inpe.br/geonetwork/srv/eng/catalog.search#/metadata/fe02f2bf-2cc0-49d5-ab72-a3954f997408):
    Dados sobre desmatamento de 31/07/2000 a 30/07/2023  
  - [nasapower](https://power.larc.nasa.gov/): Variáveis climáticas
    (Temperatura; precipitação; radiação solar; umidade relativa;
    velocidade do vento e pressão) de 2015 a 2024  

## 🧹 Faxina e Tratamento [script_geral](https://arpanosso.github.io//projeto-oliveiraphm//01_faxina_tratamento_dados.html)

Nessa etapa foi realizada a faxina, filtragem e organização inicial dos
dados. Os dados de concentração atmosférica de dióxido de carbono (XCO2)
e metano (XCH4) foram devidamente processados e filtrados para o
território brasileiro, incluindo:

Filtro geográfico (apenas medições dentro do Brasil);  
Controle de qualidade (baseado nos flags de qualidade dos dados
originais);  
Organização por regiões (Norte, Nordeste, Sudeste, Sul e Centro-Oeste);

### 🔗 Scripts de tratamentos e Links para Download dos dados processados:

| Script de Tratamento | Dados Processados Para Download |
|:--:|:--:|
| [nasa-xco2](https://arpanosso.github.io//projeto-oliveiraphm//nasa-xco2.html) | ⬇️ [nasa-xco2.rds](https://drive.google.com/file/d/1sVsLvBLxUB1YbqWyDUg177Eua2oREvgH/view?usp=sharing) |
| [gosat-xch4](https://arpanosso.github.io//projeto-oliveiraphm//gosat-xch4.html) | ⬇️ [gosat-xch4.rds](https://drive.google.com/file/d/1Rj-jcHOblEEb1ARMyJ1Jyfo4wCJnGliB/view?usp=drive_link) |
| [oco2-sif](https://arpanosso.github.io//projeto-oliveiraphm//oco2-sif.html) | ⬇️ [oco2-sif.rds](https://drive.google.com/file/d/1c4WlEmgnwu7R_ENjzMTTg2a4mP1IaiG_/view?usp=sharing) |
| [appeears-modis](https://arpanosso.github.io//projeto-oliveiraphm//appeears-modis.html) | ⬇️ [appeears-modis.rds](https://drive.google.com/file/d/15bpg2r2_XSWveyWrFu6oumt79UUlxzJr/view?usp=sharing) |
| [emissions-sources](https://arpanosso.github.io//projeto-oliveiraphm//emissions-sources.html) | ⬇️ [emissions-sources.rds](https://drive.google.com/file/d/17erldRlIlTiB5sVtLWjsv4E--zZ3gmH-/view?usp=sharing) |
| [nasa-power](https://arpanosso.github.io//projeto-oliveiraphm//nasa-xco2.html) | ⬇️ [nasa-power.rds](https://drive.google.com/file/d/13_PR3bQ9-ga_Wiv7jEv-GhYpAJwhmyTN/view?usp=sharing) |
| [prodes-deforestation](https://arpanosso.github.io//projeto-oliveiraphm//prodes-deforestation.html) | ⬇️ [prodes-deforestation.rds](https://drive.google.com/file/d/1X4KJ_XK3GRcrwNCwWVEihJQBMGb72Z3S/view?usp=sharing) |
| [deter-queimadas](https://arpanosso.github.io//projeto-oliveiraphm//deter-queimadas.html) | ⬇️ [deter-queimadas.rds](https://drive.google.com/file/d/1cmikkge6MtLJXuPBYeV-ZuMYoaNKP967/view?usp=sharing) |
| [nasa-firms](https://arpanosso.github.io//projeto-oliveiraphm//nasa-firms.html) | ⬇️ [nasa-firms.rds](https://drive.google.com/file/d/1aMsbg35-QRBs-xiS8jl6lQ6feUySxM3e/view?usp=sharing) |

Formato dos arquivos:

> .rds (formato nativo do R para rápido carregamento)

> salve os arquivos na pasta `data` do seu projeto

### 🛠️ Pré-processameto [script](https://arpanosso.github.io//projeto-oliveiraphm//02_preprocessamento.html)

### 🛠 Preparação dos dados para análise.

``` r
library(tidyverse)
library(geobr)
library(gstat)
library(sf)
library(dplyr)
source("R/my-function.R")
#> List of polygons loaded [list_pol]
```

#### Definindo estados

``` r
my_states <- c("MS","MT","GO","DF")
```

### 💨 Entrada com a Base: `emissions-sources.rds`

``` r
emissions_sources <- read_rds("data/emissions-sources.rds")|> 
  filter(sigla_uf %in% my_states)
glimpse(emissions_sources)
```

#### Filtrando os polígonos do municípios

``` r
munici_state <- municipality |> 
  filter(abbrev_state %in% my_states)
pol_ms <- states |> filter(abbrev_state == "MS") |> 
  pull(geom) |> pluck(1) |> as.matrix()
pol_mt <- states |> filter(abbrev_state == "MT") |> 
  pull(geom) |> pluck(1) |> as.matrix()
pol_go <- states |> filter(abbrev_state == "GO") |> 
  pull(geom) |> pluck(1) |> as.matrix()
pol_df <- states |> filter(abbrev_state == "DF") |> 
  pull(geom) |> pluck(1) |> as.matrix()
```

### Carregando as bases

``` r
file_kgr <- list.files("data-raw/",
                      full.names = TRUE,pattern = "kgr") 
new_names = c(lat = "latitude", lon = "longitude")

read_kgr <- function(path){
  df <- readr::read_rds(path) |> 
    janitor::clean_names() |> 
    dplyr::rename(dplyr::any_of(new_names))
  
  nome <- df[3] |> names()    
  new_name <- c(value = nome)
  df <- df |> 
    mutate(
      variable = nome
    ) |> 
    dplyr::rename(dplyr::any_of(new_name))
  return(df)  
};read_kgr(file_kgr[1])
#> # A tibble: 3,815 × 7
#>      lon   lat value city_ref      state  year variable
#>    <dbl> <dbl> <dbl> <chr>         <chr> <int> <chr>   
#>  1 -55.4 -23.6 1812. Paranhos      MS     2015 xch4    
#>  2 -54.9 -23.6 1812. Tacuru        MS     2015 xch4    
#>  3 -54.4 -23.6 1812. Iguatemi      MS     2015 xch4    
#>  4 -55.4 -23.1 1812. Amambai       MS     2015 xch4    
#>  5 -54.9 -23.1 1812. Amambai       MS     2015 xch4    
#>  6 -54.4 -23.1 1812. Naviraí       MS     2015 xch4    
#>  7 -53.9 -23.1 1812. Naviraí       MS     2015 xch4    
#>  8 -55.4 -22.6 1812. Laguna Carapã MS     2015 xch4    
#>  9 -54.9 -22.6 1812. Caarapó       MS     2015 xch4    
#> 10 -54.4 -22.6 1812. Jateí         MS     2015 xch4    
#> # ℹ 3,805 more rows

data_set_kgr <- map_df(file_kgr,read_kgr)
data_set_kgr |> 
  group_by(year, state, city_ref, variable) |> 
  summarise(
    value_mean = mean(value, na.rm=TRUE),
    .groups = "drop") |>
  pivot_wider(names_from = variable, values_from = value_mean)
#> # A tibble: 3,281 × 13
#>     year state city_ref  precipitacao pressao radiacao sif_757   t2m temperatura
#>    <int> <chr> <chr>            <dbl>   <dbl>    <dbl>   <dbl> <dbl>       <dbl>
#>  1  2015 DF    Brasília          2.62    90.7     20.5   0.234  23.2        23.2
#>  2  2015 GO    Abadiânia        NA       NA       NA    NA      NA          NA  
#>  3  2015 GO    Acreúna           3.33    94.4     19.8   0.241  24.7        24.7
#>  4  2015 GO    Alexânia         NA       NA       NA    NA      NA          NA  
#>  5  2015 GO    Alto Par…        NA       NA       NA    NA      NA          NA  
#>  6  2015 GO    Alvorada…        NA       NA       NA     0.153  NA          NA  
#>  7  2015 GO    Amaralina         2.71    97.1     20.4  NA      27.9        27.9
#>  8  2015 GO    Amorinóp…        NA       NA       NA     0.229  NA          NA  
#>  9  2015 GO    Anicuns           3.25    93.5     20.1  NA      24.6        24.6
#> 10  2015 GO    Anápolis          3.30    90.7     20.2  NA      22.9        22.9
#> # ℹ 3,271 more rows
#> # ℹ 4 more variables: umidade <dbl>, vento <dbl>, xch4 <dbl>, xco2 <dbl>

# data_set_kgr |> 
#   group_by(year,state) |> 
#   count()

data_set_kgr |>
  select(variable, city_ref) |>
  pull(city_ref) |> unique() |> sort()
#>   [1] "Abadiânia"                        "Acorizal"                        
#>   [3] "Acreúna"                          "Água Boa"                        
#>   [5] "Água Clara"                       "Água Fria De Goiás"              
#>   [7] "Água Limpa"                       "Alcinópolis"                     
#>   [9] "Alexânia"                         "Alta Floresta"                   
#>  [11] "Alto Araguaia"                    "Alto Boa Vista"                  
#>  [13] "Alto Garças"                      "Alto Paraguai"                   
#>  [15] "Alto Paraíso De Goiás"            "Alto Taquari"                    
#>  [17] "Alvorada Do Norte"                "Amambai"                         
#>  [19] "Amaralina"                        "Amorinópolis"                    
#>  [21] "Anápolis"                         "Anastácio"                       
#>  [23] "Anaurilândia"                     "Angélica"                        
#>  [25] "Anicuns"                          "Aparecida Do Taboado"            
#>  [27] "Apiacás"                          "Aporé"                           
#>  [29] "Aquidauana"                       "Araguaiana"                      
#>  [31] "Araguapaz"                        "Aral Moreira"                    
#>  [33] "Araputanga"                       "Arenápolis"                      
#>  [35] "Arenópolis"                       "Aripuanã"                        
#>  [37] "Aruanã"                           "Baliza"                          
#>  [39] "Bandeirantes"                     "Barão De Melgaço"                
#>  [41] "Barra Do Bugres"                  "Barra Do Garças"                 
#>  [43] "Barro Alto"                       "Bataguassu"                      
#>  [45] "Batayporã"                        "Bela Vista"                      
#>  [47] "Bela Vista De Goiás"              "Bodoquena"                       
#>  [49] "Bom Jardim De Goiás"              "Bom Jesus De Goiás"              
#>  [51] "Bom Jesus Do Araguaia"            "Bonito"                          
#>  [53] "Bonópolis"                        "Brasilândia"                     
#>  [55] "Brasília"                         "Brasnorte"                       
#>  [57] "Brazabrantes"                     "Britânia"                        
#>  [59] "Buriti Alegre"                    "Caarapó"                         
#>  [61] "Cabeceiras"                       "Cáceres"                         
#>  [63] "Cachoeira Alta"                   "Cachoeira Dourada"               
#>  [65] "Caçu"                             "Caiapônia"                       
#>  [67] "Caldas Novas"                     "Camapuã"                         
#>  [69] "Campinaçu"                        "Campinápolis"                    
#>  [71] "Campinorte"                       "Campo Alegre De Goiás"           
#>  [73] "Campo Grande"                     "Campo Novo Do Parecis"           
#>  [75] "Campo Verde"                      "Campos Belos"                    
#>  [77] "Campos De Júlio"                  "Canabrava Do Norte"              
#>  [79] "Canarana"                         "Caracol"                         
#>  [81] "Carlinda"                         "Cassilândia"                     
#>  [83] "Castanheira"                      "Catalão"                         
#>  [85] "Cavalcante"                       "Chapada Dos Guimarães"           
#>  [87] "Chapadão Do Céu"                  "Chapadão Do Sul"                 
#>  [89] "Cidade Ocidental"                 "Cláudia"                         
#>  [91] "Cocalinho"                        "Cocalzinho De Goiás"             
#>  [93] "Colíder"                          "Colinas Do Sul"                  
#>  [95] "Colniza"                          "Comodoro"                        
#>  [97] "Confresa"                         "Conquista D'oeste"               
#>  [99] "Corguinho"                        "Coronel Sapucaia"                
#> [101] "Córrego Do Ouro"                  "Corumbá"                         
#> [103] "Corumbá De Goiás"                 "Corumbaíba"                      
#> [105] "Costa Rica"                       "Cotriguaçu"                      
#> [107] "Coxim"                            "Cristalina"                      
#> [109] "Crixás"                           "Cuiabá"                          
#> [111] "Curvelândia"                      "Damianópolis"                    
#> [113] "Denise"                           "Deodápolis"                      
#> [115] "Diamantino"                       "Dois Irmãos Do Buriti"           
#> [117] "Dom Aquino"                       "Douradina"                       
#> [119] "Dourados"                         "Doverlândia"                     
#> [121] "Edealina"                         "Edéia"                           
#> [123] "Faina"                            "Fátima Do Sul"                   
#> [125] "Fazenda Nova"                     "Feliz Natal"                     
#> [127] "Figueirão"                        "Figueirópolis D'oeste"           
#> [129] "Flores De Goiás"                  "Formosa"                         
#> [131] "Formoso"                          "Gameleira De Goiás"              
#> [133] "Gaúcha Do Norte"                  "General Carneiro"                
#> [135] "Glória D'oeste"                   "Glória De Dourados"              
#> [137] "Goianápolis"                      "Goiandira"                       
#> [139] "Goianésia"                        "Goiânia"                         
#> [141] "Goianira"                         "Goiás"                           
#> [143] "Goiatuba"                         "Gouvelândia"                     
#> [145] "Guapó"                            "Guarani De Goiás"                
#> [147] "Guarantã Do Norte"                "Guia Lopes Da Laguna"            
#> [149] "Guiratinga"                       "Hidrolândia"                     
#> [151] "Hidrolina"                        "Iaciara"                         
#> [153] "Iguatemi"                         "Inaciolândia"                    
#> [155] "Indiara"                          "Inocência"                       
#> [157] "Ipameri"                          "Ipiranga De Goiás"               
#> [159] "Ipiranga Do Norte"                "Iporá"                           
#> [161] "Israelândia"                      "Itaberaí"                        
#> [163] "Itajá"                            "Itanhangá"                       
#> [165] "Itapaci"                          "Itapirapuã"                      
#> [167] "Itaporã"                          "Itapuranga"                      
#> [169] "Itaquiraí"                        "Itarumã"                         
#> [171] "Itaúba"                           "Itiquira"                        
#> [173] "Itumbiara"                        "Ivinhema"                        
#> [175] "Ivolândia"                        "Jaciara"                         
#> [177] "Jandaia"                          "Jaraguá"                         
#> [179] "Jaraguari"                        "Jardim"                          
#> [181] "Jataí"                            "Jateí"                           
#> [183] "Jauru"                            "Juara"                           
#> [185] "Juína"                            "Juruena"                         
#> [187] "Juscimeira"                       "Jussara"                         
#> [189] "Ladário"                          "Laguna Carapã"                   
#> [191] "Lambari D'oeste"                  "Leopoldo De Bulhões"             
#> [193] "Lucas Do Rio Verde"               "Luciara"                         
#> [195] "Luziânia"                         "Mairipotaba"                     
#> [197] "Mambaí"                           "Mara Rosa"                       
#> [199] "Maracaju"                         "Marcelândia"                     
#> [201] "Matrinchã"                        "Matupá"                          
#> [203] "Maurilândia"                      "Mimoso De Goiás"                 
#> [205] "Minaçu"                           "Mineiros"                        
#> [207] "Miranda"                          "Moiporá"                         
#> [209] "Monte Alegre De Goiás"            "Montes Claros De Goiás"          
#> [211] "Montividiu"                       "Montividiu Do Norte"             
#> [213] "Morrinhos"                        "Mossâmedes"                      
#> [215] "Mozarlândia"                      "Mundo Novo"                      
#> [217] "Naviraí"                          "Nazário"                         
#> [219] "Nioaque"                          "Niquelândia"                     
#> [221] "Nobres"                           "Nossa Senhora Do Livramento"     
#> [223] "Nova Alvorada Do Sul"             "Nova América"                    
#> [225] "Nova Andradina"                   "Nova Bandeirantes"               
#> [227] "Nova Brasilândia"                 "Nova Canaã Do Norte"             
#> [229] "Nova Crixás"                      "Nova Guarita"                    
#> [231] "Nova Iguaçu De Goiás"             "Nova Lacerda"                    
#> [233] "Nova Marilândia"                  "Nova Maringá"                    
#> [235] "Nova Monte Verde"                 "Nova Mutum"                      
#> [237] "Nova Nazaré"                      "Nova Olímpia"                    
#> [239] "Nova Roma"                        "Nova Santa Helena"               
#> [241] "Nova Ubiratã"                     "Nova Xavantina"                  
#> [243] "Novo Brasil"                      "Novo Horizonte Do Norte"         
#> [245] "Novo Horizonte Do Sul"            "Novo Mundo"                      
#> [247] "Novo Planalto"                    "Novo Santo Antônio"              
#> [249] "Novo São Joaquim"                 "Orizona"                         
#> [251] "Other"                            "Padre Bernardo"                  
#> [253] "Palestina De Goiás"               "Palmeiras De Goiás"              
#> [255] "Palmelo"                          "Paranaíba"                       
#> [257] "Paranaíta"                        "Paranatinga"                     
#> [259] "Paranhos"                         "Paraúna"                         
#> [261] "Pedra Preta"                      "Pedro Gomes"                     
#> [263] "Peixoto De Azevedo"               "Perolândia"                      
#> [265] "Petrolina De Goiás"               "Piracanjuba"                     
#> [267] "Piranhas"                         "Pirenópolis"                     
#> [269] "Planaltina"                       "Planalto Da Serra"               
#> [271] "Poconé"                           "Ponta Porã"                      
#> [273] "Pontal Do Araguaia"               "Pontalina"                       
#> [275] "Ponte Branca"                     "Pontes E Lacerda"                
#> [277] "Porangatu"                        "Porto Alegre Do Norte"           
#> [279] "Porto Dos Gaúchos"                "Porto Esperidião"                
#> [281] "Porto Estrela"                    "Porto Murtinho"                  
#> [283] "Posse"                            "Poxoréo"                         
#> [285] "Primavera Do Leste"               "Querência"                       
#> [287] "Quirinópolis"                     "Reserva Do Cabaçal"              
#> [289] "Ribas Do Rio Pardo"               "Ribeirão Cascalheira"            
#> [291] "Ribeirãozinho"                    "Rio Brilhante"                   
#> [293] "Rio Negro"                        "Rio Verde"                       
#> [295] "Rio Verde De Mato Grosso"         "Rochedo"                         
#> [297] "Rondolândia"                      "Rondonópolis"                    
#> [299] "Rosário Oeste"                    "Rubiataba"                       
#> [301] "Salto Do Céu"                     "Santa Bárbara De Goiás"          
#> [303] "Santa Carmem"                     "Santa Cruz Do Xingu"             
#> [305] "Santa Fé De Goiás"                "Santa Isabel"                    
#> [307] "Santa Rita Do Novo Destino"       "Santa Rita Do Pardo"             
#> [309] "Santa Rita Do Trivelato"          "Santa Tereza De Goiás"           
#> [311] "Santa Terezinha"                  "Santa Terezinha De Goiás"        
#> [313] "Santo Afonso"                     "Santo Antônio Da Barra"          
#> [315] "Santo Antônio Do Descoberto"      "Santo Antônio Do Leste"          
#> [317] "Santo Antônio Do Leverger"        "São Domingos"                    
#> [319] "São Félix Do Araguaia"            "São Gabriel Do Oeste"            
#> [321] "São João D'aliança"               "São João Da Paraúna"             
#> [323] "São José Do Rio Claro"            "São José Do Xingu"               
#> [325] "São José Dos Quatro Marcos"       "São Luís De Montes Belos"        
#> [327] "São Miguel Do Araguaia"           "São Miguel Do Passa Quatro"      
#> [329] "São Simão"                        "Sapezal"                         
#> [331] "Selvíria"                         "Serra Nova Dourada"              
#> [333] "Serranópolis"                     "Sidrolândia"                     
#> [335] "Silvânia"                         "Sinop"                           
#> [337] "Sítio D'abadia"                   "Sonora"                          
#> [339] "Sorriso"                          "Tabaporã"                        
#> [341] "Tacuru"                           "Tangará Da Serra"                
#> [343] "Tapurah"                          "Taquaral De Goiás"               
#> [345] "Taquarussu"                       "Terenos"                         
#> [347] "Terezópolis De Goiás"             "Terra Nova Do Norte"             
#> [349] "Tesouro"                          "Torixoréu"                       
#> [351] "Três Lagoas"                      "Três Ranchos"                    
#> [353] "Trombas"                          "Turvânia"                        
#> [355] "Turvelândia"                      "Uirapuru"                        
#> [357] "União Do Sul"                     "Uruaçu"                          
#> [359] "Uruana"                           "Urutaí"                          
#> [361] "Vale De São Domingos"             "Varjão"                          
#> [363] "Várzea Grande"                    "Vera"                            
#> [365] "Vianópolis"                       "Vicentinópolis"                  
#> [367] "Vila Bela Da Santíssima Trindade" "Vila Boa"                        
#> [369] "Vila Propício"                    "Vila Rica"
```

## Criar os mapas por variáveis por ano… como a base do geobr

## para verifcar os municípios não plotados

vamos ver onde estão os NA

``` r
# my_year <- 2016
variavel <- "temperatura"
anos <- if (variavel == "xch4") 2015:2021 else 2015:2023

mapas <- map(anos, function(my_year) {
  municipality |> 
    filter(abbrev_state %in% my_states) |> 
    left_join( 
      data_set_kgr |>
        filter(variable == all_of(variavel)) |> 
        group_by(year, city_ref) |> 
        rename(name_muni = city_ref),
      by = c("name_muni")
    ) |> 
    filter(year == my_year) |> 
    ungroup() |> 
    ggplot()  +
    geom_sf(aes(fill = variavel), color="transparent",
            size=.05, show.legend = TRUE) +
    labs(title = paste("Ano:", my_year, "-", variavel))
  
})

mapas[[1]]

# municipality |>
#   filter(abbrev_state %in% my_states) |> 
#   ggplot() +
#   geom_sf() +
#   geom_point(data = data_set_kgr,
#              aes(x = lon, y = lat, color = "red"))
```
