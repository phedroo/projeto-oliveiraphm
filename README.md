
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
library(ggridges)
library(ggpubr)
library(geobr)
library(gstat)
library(vegan)
library(sf)
library(dplyr)
library(lwgeom) # para st_make_valid
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

\##W Carregando as bases

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

data_set_kgr |> 
  group_by(year,state) |> 
  count()
#> # A tibble: 36 × 3
#> # Groups:   year, state [36]
#>     year state     n
#>    <int> <chr> <int>
#>  1  2015 DF       21
#>  2  2015 GO     1147
#>  3  2015 MS     1240
#>  4  2015 MT     3026
#>  5  2016 DF       21
#>  6  2016 GO     1147
#>  7  2016 MS     1240
#>  8  2016 MT     3026
#>  9  2017 DF       21
#> 10  2017 GO     1147
#> # ℹ 26 more rows
```

## Criar os mapas por variáveis por ano… como a base do geobr

## para verifcar os municípios não plotados

vamos ver onde estão os NA
