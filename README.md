
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

### 💨 Entrada com a Base: `nasa-xco2.rds`

``` r
nasa_xco2 <- read_rds("data/nasa-xco2.rds") |> 
  filter(state %in% my_states)
glimpse(nasa_xco2)
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

#### Classificando cada ponto em município

``` r
# resul <- vector()
# estado <- nasa_xco2$state
# for(i in 1:nrow(nasa_xco2)){
#   if(estado[i]!="Other"){
#     my_citys_obj <- municipality %>%
#       filter(abbrev_state == estado[i])
#     n_citys <- nrow(my_citys_obj)
#     my_citys_names <- my_citys_obj %>% pull(name_muni)
#     resul[i] <- "Other"
#     for(j in 1:n_citys){
#       pol_city <- my_citys_obj$geom  %>%
#         purrr::pluck(j) %>%
#         as.matrix()
#       if(def_pol(nasa_xco2$longitude[i],
#                  nasa_xco2$latitude[i],
#                  pol_city)){
#         resul[i] <- my_citys_names[j]
#       }
#     }
#   }
# }
# nasa_xco2$city_ref <- resul
# write_rds(nasa_xco2,"data/nasa-xco2.rds")
```

#### Gerar mapa

``` r
my_year = 2015
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    nasa_xco2 |> 
      group_by(year, city_ref) |> 
      filter(year == my_year) |> 
      summarise(
        xco2 = mean(xco2,na.rm=TRUE),
        .groups = "drop"
      ) |> 
      rename(  name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  ggplot()  +
  geom_sf(aes(fill=xco2), color="transparent",
          size=.05, show.legend = TRUE)  +
  geom_point(data = nasa_xco2 |> 
               filter(year==my_year), 
               aes(longitude, latitude, #size = emission,
                   color="red"))+
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = 'xco2',
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()
```

#### Criando o grid (malha de pontos) para valores não amostrados - nasa-xco2

``` r
# vetores para coordenadas x e y selecionadas da base do IBGE1
# Extrair coordenadas da base nasa_xco2 para definir extensão do grid
x<-nasa_xco2$longitude
y<-nasa_xco2$latitude
dis <- 0.5 # distância (do grid) para adensamento de pontos nos estados
grid_geral <- expand.grid( # Criar malha regular
  X=seq(min(x),max(x),dis), # Combinar cada x e y
  Y=seq(min(y),max(y),dis)) |>
  mutate( #teste ponto-no-polígono, TRUE se (X,Y) caem no polígono
    flag_ms = def_pol(X, Y, pol_ms),
    flag_mt = def_pol(X, Y, pol_mt),
    flag_go = def_pol(X, Y, pol_go),
    flag_df = def_pol(X, Y, pol_df)
  ) |>
  filter(flag_ms | flag_go | flag_mt | flag_df) |> # manter pontos correspondentes ao menos 1 dos limites
  select(-c(flag_ms,flag_mt,flag_go,flag_df)) # remover colunas criadas
plot(grid_geral)
sp::gridded(grid_geral) = ~ X + Y
```

#### Interpolação por Krigagem Ordinária

Estimar valores médios de concentração de CO2 entre 2015 e 2023

``` r
df_aux <- nasa_xco2 |> 
  filter(year == my_year) |> 
  group_by(longitude, latitude) |> 
  summarise(
    xco2 = mean(xco2,na.rm=TRUE), # média xco2
    .groups = "drop"
  ) |> sample_n(10000) 
sp::coordinates(df_aux) = ~ longitude + latitude # Converter data frame para objeto espacial - atribuir as colunas longitude/latitude como coordenadas. Várias funções de geoestatística do pacote gstat (como variogram() e krige()) não aceitam um data.frame, mas um objeto com coordenadas. Agora, a variável xco2 passa a ser o atributo associado a cada ponto espacial.

form <- xco2 ~ 1 # "~ 1" modelo de média constante, mas desconhecida (somente intercepto - assume média global, sem covariáveis).

vari_exp <- gstat::variogram(form, data = df_aux,
                      cressie = FALSE, #estimador clássico do semivar.
                      cutoff = 1, # distância máxima = 8
                      width = 0.075) # distancia entre pontos
vari_exp  |>
  ggplot(aes(x=dist, y=gamma)) +
  geom_point() +
  labs(x="lag (º)",
       y=expression(paste(gamma,"(h)")))
```

``` r
patamar=1.4
alcance=0.2
epepita=0.5
modelo_1 <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
modelo_2 <- fit.variogram(vari_exp,vgm(patamar,"Exp",alcance,epepita))
modelo_3 <- fit.variogram(vari_exp,vgm(patamar,"Gau",alcance,epepita))
plot_my_models(modelo_1,modelo_2,modelo_3)
modelo <- modelo_1 ## sempre modificar
```

``` r
ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                     block=c(0.1,0.1),
                     nsim=0,
                     na.action=na.pass,
                     debug.level=-1
)
```

``` r
ko_variavel |> 
  as_tibble() |> 
    ggplot(aes(x=X, y=Y)) +
  geom_tile(aes(fill = var1.pred)) +
  scale_fill_viridis_c(option = "mako") +
  coord_equal() +
  labs(x="Longitude",
       y="Latitude",
       fill="xco2",
       title = my_year) +
  theme_bw()
```

``` r
df_kgr <- ko_variavel |> 
      as_tibble() |> 
      select(-var1.var) |> 
      rename(longitude=X,latitude=Y,xco2=var1.pred)  |> 
      mutate(city_ref = "Other",
             state = ifelse(def_pol(longitude, latitude, pol_ms),"MS",
                            ifelse(def_pol(longitude, latitude, pol_mt),"MT",
                            ifelse(def_pol(longitude, latitude, pol_go),"GO",
                            "DF"))) 
             )
resul <- vector()
estado <- df_kgr$state
for(i in 1:nrow(df_kgr)){
  if(estado[i]!="Other"){
    my_citys_obj <- municipality %>%
      filter(abbrev_state == estado[i])
    n_citys <- nrow(my_citys_obj)
    my_citys_names <- my_citys_obj %>% pull(name_muni)
    resul[i] <- "Other"
    for(j in 1:n_citys){
      pol_city <- my_citys_obj$geom  %>%
        purrr::pluck(j) %>%
        as.matrix()
      if(def_pol(df_kgr$longitude[i],
                 df_kgr$latitude[i],
                 pol_city)){
        resul[i] <- my_citys_names[j]
      }
    }
  }
}
df_kgr$city_ref <- resul
```

``` r
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    nasa_xco2 |> 
      filter(year == my_year) |> 
      select(longitude,latitude,xco2,state,city_ref) |> 
      rbind(
        df_kgr
      ) |> 
      group_by(city_ref) |> 
      summarise(
        xco2 = mean(xco2,na.rm=TRUE),
        .groups = "drop"
      ) |> 
      rename(  name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  mutate(
    xco2 = ifelse(is.na(xco2),median(xco2,na.rm = TRUE),xco2)) |>
  ggplot()  +
  geom_sf(aes(fill=xco2), color="transparent",
          size=.05, show.legend = TRUE)  +
  # geom_point(data = df_kgr, 
  #            aes(longitude, latitude, #size = emission,
  #                color="red")) +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = 'xco2',
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()
```

#### Estimativa de XCO2 para o Brasil Central

``` r
nasa_xco2_kgr <- map_df(2015:2023,~{
  set.seed(1235)
  df_aux <- nasa_xco2 |>
    group_by(longitude, latitude) |>
    filter(year == .x) |>
    summarise(
      xco2 = mean(xco2,na.rm=TRUE),
      .groups = "drop"
    ) |> sample_n(8000)
  sp::coordinates(df_aux) = ~ longitude + latitude
  form <- xco2 ~ 1
  vari_exp <- gstat::variogram(form, data = df_aux,
                               cressie = FALSE,
                               cutoff = 1, # distância máxima 8
                               width = 0.075) # distancia entre pontos
  vari_exp  |>
    ggplot(aes(x=dist, y=gamma)) +
    geom_point() +
    labs(x="lag (º)",
         y=expression(paste(gamma,"(h)")))
  patamar=1.4
  alcance=0.2
  epepita=0.5
  modelo <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
  ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                       block=c(0.1,0.1),
                       nsim=0,
                       na.action=na.pass,
                       debug.level=-1
  )
  df_kgr <- ko_variavel |>
      as_tibble() |>
      select(-var1.var) |>
      rename(longitude=X,latitude=Y,xco2=var1.pred)  |>
      mutate(city_ref = "Other",
             state = ifelse(def_pol(longitude, latitude, pol_ms),"MS",
                            ifelse(def_pol(longitude, latitude, pol_mt),"MT",
                            ifelse(def_pol(longitude, latitude, pol_go),"GO",
                            "DF")))
             )
  resul <- vector()
  estado <- df_kgr$state
  for(i in 1:nrow(df_kgr)){
    if(estado[i]!="Other"){
      my_citys_obj <- municipality %>%
        filter(abbrev_state == estado[i])
      n_citys <- nrow(my_citys_obj)
      my_citys_names <- my_citys_obj %>% pull(name_muni)
      resul[i] <- "Other"
      for(j in 1:n_citys){
        pol_city <- my_citys_obj$geom  %>%
          purrr::pluck(j) %>%
          as.matrix()
        if(def_pol(df_kgr$longitude[i],
                   df_kgr$latitude[i],
                   pol_city)){
          resul[i] <- my_citys_names[j]
        }
      }
    }
  }
  df_kgr$city_ref <- resul

  df_final <- df_kgr |>
        mutate(year = .x)
  return(df_final)
})
# write_rds(nasa_xco2_kgr,"data-raw/nasa-xco2-kgr.rds")
```

``` r
nasa_xco2_kgr <- read_rds("data-raw/nasa-xco2-kgr.rds")
```

``` r
nasa_xco2_bind <- nasa_xco2 |> 
  select(longitude,latitude,xco2,city_ref,state,year) |> 
  rbind(nasa_xco2_kgr)

map(2015:2023,~{
  municipality |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      nasa_xco2_bind |> 
        filter(year == .x) |> 
        select(longitude,latitude,xco2,state,city_ref) |> 
        group_by(city_ref) |> 
        summarise(
          xco2 = mean(xco2,na.rm=TRUE),
          .groups = "drop"
        ) |> 
        rename(  name_muni = city_ref),
      by = c("name_muni")
    ) |> 
    mutate(
      xco2 = ifelse(is.na(xco2),median(xco2,na.rm = TRUE),xco2)) |>
    ggplot()  +
    geom_sf(aes(fill=xco2), color="transparent",
            size=.05, show.legend = TRUE)  +
    # geom_point(data = df_kgr, 
    #            aes(longitude, latitude, #size = emission,
    #                color="red")) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'xco2',
         x = 'Longitude',
         y = 'Latitude',
         title = .x) +
    scale_fill_viridis_c()})
```

### 💨 Entrada com a Base: `gosat-xch4.rds`

``` r
gosat_xch4 <- read_rds("data/gosat_xch4.rds") |> 
  filter(state %in% my_states) |> 
  select(-flag_nordeste, -flag_br)

glimpse(gosat_xch4)
```

``` r
gosat_xch4 |> 
  filter(year == 2021) |> 
  ggplot(aes(x=longitude,y=latitude)) +
  geom_point()
```

#### Classificando cada ponto em município

Já feito no arquivo da pasta docs

#### Gerar mapa

``` r
gosat_xch4 <- read_rds("data/gosat_xch4.rds") # os arquivos com underline foram tratados, classificados por município e deverão ser repassados para a pasta data futuramente

my_year = 2021
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    gosat_xch4 |> 
      group_by(year, city_ref) |> 
      summarise(
        xch4 = mean(xch4,na.rm=TRUE),
        .groups = "drop"
      ) |> 
      rename(name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  filter(year == my_year) |> 
  ggplot()  +
  geom_sf(aes(fill=xch4), color="transparent",
          size=.05, show.legend = TRUE)  +
  geom_point(data = gosat_xch4 |> 
               filter(year==my_year), 
               aes(longitude, latitude, #size = emission,
                   color="red"))+
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = 'xch4',
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()

# unidade partes por blihão (ppb)
```

#### Criando o grid (malha de pontos) para valores não amostrados - gosat-xch4

``` r
# vetores para coordenadas x e y selecionadas da base do IBGE1
# Extrair coordenadas da base gosat_xch4 para definir extensão do grid
x<-gosat_xch4$longitude
y<-gosat_xch4$latitude
dis <- 0.5 # distância (do grid) para adensamento de pontos nos estados
grid_geral <- expand.grid( # Criar malha regular
  X=seq(min(x),max(x),dis), # Combinar cada x e y
  Y=seq(min(y),max(y),dis)) |>
  mutate( #teste ponto-no-polígono, TRUE se (X,Y) caem no polígono
    flag_ms = def_pol(X, Y, pol_ms),
    flag_mt = def_pol(X, Y, pol_mt),
    flag_go = def_pol(X, Y, pol_go),
    flag_df = def_pol(X, Y, pol_df)
  ) |>
  filter(flag_ms | flag_go | flag_mt | flag_df) |> # manter pontos correspondentes ao menos 1 dos limites
  select(-c(flag_ms,flag_mt,flag_go,flag_df)) # remover colunas criadas
plot(grid_geral)
sp::gridded(grid_geral) = ~ X + Y
```

#### Interpolação por Krigagem Ordinária - gosat-xch4

Estimar valores médios de concentração de CH4 entre 2015 e 2021

``` r
df_aux <- gosat_xch4 |> 
  filter(year == my_year) |> 
  group_by(longitude, latitude) |> 
  summarise(
    xch4 = mean(xch4,na.rm=TRUE), # média xch4
    .groups = "drop"
  ) |> sample_n(2627) # tamanho máximo dos dados
sp::coordinates(df_aux) = ~ longitude + latitude # Converter data frame para objeto espacial - atribuir as colunas longitude/latitude como coordenadas. Várias funções de geoestatística do pacote gstat (como variogram() e krige()) não aceitam um data frame, mas sim um objeto com coordenadas. Agora, a variável xch4 passa a ser o atributo associado a cada ponto espacial.

form <- xch4 ~ 1 # "~ 1" modelo de média constante, mas desconhecida (somente intercepto - assume média global, sem covariáveis).

vari_exp <- gstat::variogram(form, data = df_aux,
                      cressie = FALSE, #estimador clássico do semivar.
                      cutoff = 0.01, # distância  
                      width = 0.0007) # distancia entre pontos
vari_exp  |>
  ggplot(aes(x=dist, y=gamma)) +
  geom_point() +
  labs(x="lag (º)",
       y=expression(paste(gamma,"(h)")))

# Melhor teste até o momento:
# vari_exp <- gstat::variogram(form, data = df_aux,
#                       cressie = FALSE, #estimador clássico do semivar.
#                       cutoff = 0.01, # distância  
#                       width = 0.0007) # distancia entre pontos
```

``` r
patamar=275
alcance=0.004
epepita=190
modelo_1 <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
modelo_2 <- fit.variogram(vari_exp,vgm(patamar,"Exp",alcance,epepita))
modelo_3 <- fit.variogram(vari_exp,vgm(patamar,"Gau",alcance,epepita))
plot_my_models(modelo_1,modelo_2,modelo_3)
modelo <- modelo_1 ## sempre modificar
```

``` r
ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                     block=c(0.1,0.1),
                     nsim=0,
                     na.action=na.pass,
                     debug.level=-1
)
```

``` r
ko_variavel |> 
  as_tibble() |> 
    ggplot(aes(x=X, y=Y)) +
  geom_tile(aes(fill = var1.pred)) +
  scale_fill_viridis_c(option = "mako") +
  coord_equal() +
  labs(x="Longitude",
       y="Latitude",
       fill="xch4",
       title = my_year) +
  theme_bw()
```

``` r
df_kgr <- ko_variavel |> 
      as_tibble() |> 
      select(-var1.var) |> 
      rename(longitude=X,latitude=Y,xch4=var1.pred)  |> 
      mutate(city_ref = "Other",
             state = ifelse(def_pol(longitude, latitude, pol_ms),"MS",
                            ifelse(def_pol(longitude, latitude, pol_mt),"MT",
                            ifelse(def_pol(longitude, latitude, pol_go),"GO",
                            "DF"))) 
             )
resul <- vector()
estado <- df_kgr$state
for(i in 1:nrow(df_kgr)){
  if(estado[i]!="Other"){
    my_citys_obj <- municipality %>%
      filter(abbrev_state == estado[i])
    n_citys <- nrow(my_citys_obj)
    my_citys_names <- my_citys_obj %>% pull(name_muni)
    resul[i] <- "Other"
    for(j in 1:n_citys){
      pol_city <- my_citys_obj$geom  %>%
        purrr::pluck(j) %>%
        as.matrix()
      if(def_pol(df_kgr$longitude[i],
                 df_kgr$latitude[i],
                 pol_city)){
        resul[i] <- my_citys_names[j]
      }
    }
  }
}
df_kgr$city_ref <- resul
```

``` r
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    gosat_xch4 |> 
      filter(year == my_year) |> 
      select(longitude,latitude,xch4,state,city_ref) |> 
      rbind(
        df_kgr
      ) |> 
      group_by(city_ref) |> 
      summarise(
        xch4 = mean(xch4,na.rm=TRUE),
        .groups = "drop"
      ) |> 
      rename(  name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  mutate(
    xch4 = ifelse(is.na(xch4),median(xch4,na.rm = TRUE),xch4)) |>
  ggplot()  +
  geom_sf(aes(fill=xch4), color="transparent",
          size=.05, show.legend = TRUE)  +
  # geom_point(data = df_kgr, 
  #            aes(longitude, latitude, #size = emission,
  #                color="red")) +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = 'xch4',
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()
```

#### Estimativa de XCH4 para o Brasil Central

``` r
# Warning haviam sido removidos, mas voltaram aparecer - revisar modelos 
gosat_xch4_kgr <- map_df(2015:2021,~{
  set.seed(1235)
  df_aux <- gosat_xch4 |>
    group_by(longitude, latitude) |>
    filter(year == .x) |>
    summarise(
      xch4 = mean(xch4,na.rm=TRUE),
      .groups = "drop"
    ) |> sample_n(1961)
  sp::coordinates(df_aux) = ~ longitude + latitude
  form <- xch4 ~ 1
  vari_exp <- gstat::variogram(form, data = df_aux,
                               cressie = FALSE,
                               cutoff = 0.01, # distância máxima 
                               width = 0.0007) # distancia entre pontos
  vari_exp  |>
    ggplot(aes(x=dist, y=gamma)) +
    geom_point() +
    labs(x="lag (º)",
         y=expression(paste(gamma,"(h)")))
  patamar=275
  alcance=0.004
  epepita=190
  modelo <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
  ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                       block=c(0.1,0.1),
                       nsim=0,
                       na.action=na.pass,
                       debug.level=-1
  )
  df_kgr <- ko_variavel |>
      as_tibble() |>
      select(-var1.var) |>
      rename(longitude=X,latitude=Y,xch4=var1.pred)  |>
      mutate(city_ref = "Other",
             state = ifelse(def_pol(longitude, latitude, pol_ms),"MS",
                            ifelse(def_pol(longitude, latitude, pol_mt),"MT",
                            ifelse(def_pol(longitude, latitude, pol_go),"GO",
                            "DF")))
             )
  resul <- vector()
  estado <- df_kgr$state
  for(i in 1:nrow(df_kgr)){
    if(estado[i]!="Other"){
      my_citys_obj <- municipality %>%
        filter(abbrev_state == estado[i])
      n_citys <- nrow(my_citys_obj)
      my_citys_names <- my_citys_obj %>% pull(name_muni)
      resul[i] <- "Other"
      for(j in 1:n_citys){
        pol_city <- my_citys_obj$geom  %>%
          purrr::pluck(j) %>%
          as.matrix()
        if(def_pol(df_kgr$longitude[i],
                   df_kgr$latitude[i],
                   pol_city)){
          resul[i] <- my_citys_names[j]
        }
      }
    }
  }
  df_kgr$city_ref <- resul

  df_final <- df_kgr |>
        mutate(year = .x)
  return(df_final)
})
# write_rds(gosat_xch4_kgr,"data-raw/gosat-xch4-kgr.rds")
```

``` r
xch4_kgr <- read_rds("data-raw/gosat-xch4-kgr.rds")
```

``` r
gosat_xch4_bind <- gosat_xch4 |> 
  select(longitude,latitude,xch4,city_ref,state,year) |> 
  rbind(gosat_xch4_kgr)

map(2015:2021,~{
  municipality |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      gosat_xch4_bind |> 
        filter(year == .x) |> 
        select(longitude,latitude,xch4,state,city_ref) |> 
        group_by(city_ref) |> 
        summarise(
          xch4 = mean(xch4,na.rm=TRUE),
          .groups = "drop"
        ) |> 
        rename(name_muni = city_ref),
      by = c("name_muni")
    ) |> 
    mutate(
      xch4 = ifelse(is.na(xch4),median(xch4,na.rm = TRUE),xch4)) |>
    ggplot()  +
    geom_sf(aes(fill=xch4), color="transparent",
            size=.05, show.legend = TRUE)  +
    # geom_point(data = df_kgr, 
    #            aes(longitude, latitude, #size = emission,
    #                color="red")) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'xch4',
         x = 'Longitude',
         y = 'Latitude',
         title = .x) +
    scale_fill_viridis_c()})
```

### 💨 Entrada com a Base: `oco2-sif.rds`

``` r
oco2_sif <- read_rds("data/oco2-sif.rds") |> 
  rename(SIF_757 = daily_sif757)

glimpse(oco2_sif)
```

``` r
oco2_sif |>
  filter(year == 2022,
         state %in% my_states) |>  # Brasil Central
  ggplot(aes(x=longitude,y=latitude)) +
  geom_point()
```

#### Gerar mapa

``` r
my_year = 2022
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    oco2_sif |> 
      group_by(year, city_ref) |> 
      summarise(
        SIF_757 = mean(SIF_757,na.rm=TRUE),
        .groups = "drop"
      ) |> 
      rename(name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  filter(year == my_year) |> 
  ggplot()  +
  geom_sf(aes(fill=SIF_757), color="transparent",
          size=.05, show.legend = TRUE)  +
  geom_point(data = oco2_sif |> 
               filter(year==my_year), 
               aes(longitude, latitude, #size = emission,
                   color="red"))+
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = 'SIF757',
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()
```

#### Criando o grid (malha de pontos) para valores não amostrados - oco2-sif

``` r
# vetores para coordenadas x e y selecionadas da base do IBGE1
# Extrair coordenadas da base oco2_sif para definir extensão do grid
x<-oco2_sif$longitude
y<-oco2_sif$latitude
dis <- 0.5 # distância (do grid) para adensamento de pontos nos estados
grid_geral <- expand.grid( # Criar malha regular
  X=seq(min(x),max(x),dis), # Combinar cada x e y
  Y=seq(min(y),max(y),dis)) |>
  mutate( #teste ponto-no-polígono, TRUE se (X,Y) caem no polígono
    flag_ms = def_pol(X, Y, pol_ms),
    flag_mt = def_pol(X, Y, pol_mt),
    flag_go = def_pol(X, Y, pol_go),
    flag_df = def_pol(X, Y, pol_df)
  ) |>
  filter(flag_ms | flag_go | flag_mt | flag_df) |> # manter pontos correspondentes ao menos 1 dos limites
  select(-c(flag_ms,flag_mt,flag_go,flag_df)) # remover colunas criadas
plot(grid_geral)
sp::gridded(grid_geral) = ~ X + Y
```

#### Interpolação por Krigagem Ordinária - oco2-sif

Os parâmetros do semivariograma (alcance, patamar e efeito pepita) da
sif foram estabelecidos com base na amostragem total dos pontos da base
de dados (sem a parte de “sample_n()”).

Estimar valores médios de concentração de SIF entre 2015 e 2023

``` r
df_aux <- oco2_sif |> 
  filter(year == my_year) |> 
  group_by(longitude, latitude) |> 
  summarise(
    SIF_757 = mean(SIF_757,na.rm=TRUE), # média sif
    .groups = "drop"
  ) |> sample_n(10000) # amostra
sp::coordinates(df_aux) = ~ longitude + latitude # Converter data frame para objeto espacial - atribuir as colunas longitude/latitude como coordenadas. Várias funções de geoestatística do pacote gstat (como variogram() e krige()) não aceitam um data frame, mas sim um objeto com coordenadas. Agora, a variável sif passa a ser o atributo associado a cada ponto espacial.

form <- SIF_757 ~ 1 # "~ 1" modelo de média constante, mas desconhecida (somente intercepto - assume média global, sem covariáveis).

vari_exp <- gstat::variogram(form, data = df_aux,
                      cressie = FALSE, # estimador clássico do semivar.
                      cutoff = 1.25, # distância semivar
                      width = 0.08) # distancia entre pontos

# vari_exp <- gstat::variogram(form, data = df_aux,
#                       cressie = FALSE, #estimador clássico do semivar.
#                       cutoff = 1, # distância semivar
#                       width = 0.08) # distancia entre pontos

vari_exp  |>
  ggplot(aes(x=dist, y=gamma)) +
  geom_point() +
  labs(x="lag (º)",
       y=expression(paste(gamma,"(h)")))
```

``` r
patamar=0.039
alcance=0.7
epepita=0.0352
modelo_1 <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
modelo_2 <- fit.variogram(vari_exp,vgm(patamar,"Exp",alcance,epepita))
modelo_3 <- fit.variogram(vari_exp,vgm(patamar,"Gau",alcance,epepita))
plot_my_models(modelo_1,modelo_2,modelo_3)
modelo <- modelo_2 ## sempre modificar
```

``` r
tictoc::tic()
ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                     block=c(0.1,0.1),
                     nsim=0,
                     na.action=na.pass,
                     debug.level=-1
)
tictoc::toc()
```

``` r
ko_variavel |> 
  as_tibble() |> 
    ggplot(aes(x=X, y=Y)) +
  geom_tile(aes(fill = var1.pred)) +
  scale_fill_viridis_c(option = "mako") +
  coord_equal() +
  labs(x="Longitude",
       y="Latitude",
       fill="SIF",
       title = my_year) +
  theme_bw()
```

``` r
df_kgr <- ko_variavel |> 
      as_tibble() |> 
      select(-var1.var) |> 
      rename(longitude=X,latitude=Y,SIF_757=var1.pred)  |> 
      mutate(city_ref = "Other",
             state = ifelse(def_pol(longitude, latitude, pol_ms),"MS",
                            ifelse(def_pol(longitude, latitude, pol_mt),"MT",
                            ifelse(def_pol(longitude, latitude, pol_go),"GO",
                            "DF"))) 
             )
resul <- vector()
estado <- df_kgr$state
for(i in 1:nrow(df_kgr)){
  if(estado[i]!="Other"){
    my_citys_obj <- municipality %>%
      filter(abbrev_state == estado[i])
    n_citys <- nrow(my_citys_obj)
    my_citys_names <- my_citys_obj %>% pull(name_muni)
    resul[i] <- "Other"
    for(j in 1:n_citys){
      pol_city <- my_citys_obj$geom  %>%
        purrr::pluck(j) %>%
        as.matrix()
      if(def_pol(df_kgr$longitude[i],
                 df_kgr$latitude[i],
                 pol_city)){
        resul[i] <- my_citys_names[j]
      }
    }
  }
}
df_kgr$city_ref <- resul
```

``` r
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    oco2_sif |> 
      filter(year == my_year) |> 
      select(longitude,latitude,SIF_757,state,city_ref) |> 
      rbind(
        df_kgr
      ) |> 
      group_by(city_ref) |> 
      summarise(
        SIF_757 = mean(SIF_757,na.rm=TRUE),
        .groups = "drop"
      ) |> 
      rename(name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  mutate(
    SIF_757 = ifelse(is.na(SIF_757),median(SIF_757,na.rm = TRUE),SIF_757)) |>
  ggplot()  +
  geom_sf(aes(fill=SIF_757), color="transparent",
          size=.05, show.legend = TRUE)  +
  # geom_point(data = df_kgr, 
  #            aes(longitude, latitude, #size = emission,
  #                color="red")) +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = 'SIF_757',
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()
```

#### Estimativa de SIF para o Brasil Central

``` r
oco2_sif_kgr <- map_df(2015:2023,~{
  set.seed(1235)
  df_aux <- oco2_sif |>
    group_by(longitude, latitude) |>
    filter(year == .x) |>
    summarise(
      SIF_757 = mean(SIF_757,na.rm=TRUE),
      .groups = "drop"
    ) |> sample_n(10000)
  sp::coordinates(df_aux) = ~ longitude + latitude
  form <- SIF_757 ~ 1
  vari_exp <- gstat::variogram(form, data = df_aux,
                               cressie = FALSE,
                               cutoff = 1.25, # distância máxima
                               width = 0.08) # distancia entre pontos
  vari_exp  |>
    ggplot(aes(x=dist, y=gamma)) +
    geom_point() +
    labs(x="lag (º)",
         y=expression(paste(gamma,"(h)")))
  patamar=0.039
  alcance=0.7
  epepita=0.0352
  modelo <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
  ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                       block=c(0.1,0.1),
                       nsim=0,
                       na.action=na.pass,
                       debug.level=-1
  )
  df_kgr <- ko_variavel |>
      as_tibble() |>
      select(-var1.var) |>
      rename(longitude=X,latitude=Y,SIF_757=var1.pred)  |>
      mutate(city_ref = "Other",
             state = ifelse(def_pol(longitude, latitude, pol_ms),"MS",
                            ifelse(def_pol(longitude, latitude, pol_mt),"MT",
                            ifelse(def_pol(longitude, latitude, pol_go),"GO",
                            "DF")))
             )
  resul <- vector()
  estado <- df_kgr$state
  for(i in 1:nrow(df_kgr)){
    if(estado[i]!="Other"){
      my_citys_obj <- municipality %>%
        filter(abbrev_state == estado[i])
      n_citys <- nrow(my_citys_obj)
      my_citys_names <- my_citys_obj %>% pull(name_muni)
      resul[i] <- "Other"
      for(j in 1:n_citys){
        pol_city <- my_citys_obj$geom  %>%
          purrr::pluck(j) %>%
          as.matrix()
        if(def_pol(df_kgr$longitude[i],
                   df_kgr$latitude[i],
                   pol_city)){
          resul[i] <- my_citys_names[j]
        }
      }
    }
  }
  df_kgr$city_ref <- resul

  df_final <- df_kgr |>
        mutate(year = .x)
  return(df_final)
})
write_rds(oco2_sif_kgr,"data-raw/oco2-sif-kgr.rds")
```

``` r
sif_kgr <- read_rds("data-raw/oco2-sif-kgr.rds")
```

``` r
oco2_sif_bind <- oco2_sif |> 
  select(longitude,latitude,SIF_757,city_ref,state,year) |> 
  rbind(oco2_sif_kgr)

map(2015:2023,~{
  municipality |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      oco2_sif_bind |> 
        filter(year == .x) |> 
        select(longitude,latitude,SIF_757,state,city_ref) |> 
        group_by(city_ref) |> 
        summarise(
          SIF_757 = mean(SIF_757,na.rm=TRUE),
          .groups = "drop"
        ) |> 
        rename(name_muni = city_ref),
      by = c("name_muni")
    ) |> 
    mutate(
      SIF_757 = ifelse(is.na(SIF_757),median(SIF_757,na.rm = TRUE),SIF_757)) |>
    ggplot()  +
    geom_sf(aes(fill=SIF_757), color="transparent",
            size=.05, show.legend = TRUE)  +
    # geom_point(data = df_kgr, 
    #            aes(longitude, latitude, #size = emission,
    #                color="red")) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'SIF_757',
         x = 'Longitude',
         y = 'Latitude',
         title = .x) +
    scale_fill_viridis_c()})
```

### 💨 Entrada com a Base: `appeears-modis.rds` - krigagem não feita ainda

``` r
# original archive "appeears-modis.rds" = 8,7mb
# appeears data requisited by API (project fapesp)

appeears_modis <- read_rds("data/appeears_modis.rds") 
  # don't have "state" column - previously filtred
glimpse(appeears_modis)

# variables: FPAR, LAI, ET, EVI, NDVI
```

``` r
appeears_modis |> 
  filter(year == 2020) |>
  ggplot(aes(x=lon,y=lat)) +
  geom_point()
```

#### Gerar mapa - appeears

``` r
my_year = 2022

# Variáveis
# media_ndvi
# media_evi
# media_et
# media_lai
# media_fpar

variavel <- "media_ndvi" # <-- mudar

municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    appeears_modis |> 
      group_by(year, city_ref) |> 
      summarise(
        !!variavel := .data[[variavel]],na.rm=TRUE, # VERIFICAR - municipios em cinza ao cacular a media
        .groups = "drop"
      ) |> 
      rename(name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  filter(year == my_year) |> 
  ggplot()  +
  geom_sf(aes(fill=.data[[variavel]]), color="transparent",
          size=.05, show.legend = TRUE)  +
  # geom_point(data = appeears_modis |> 
  #              filter(year==my_year), 
  #              aes(lon, lat, #size = emission,
  #                  color="red"))+
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = variavel,
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c(limit = c(-1, 1)) # Resolver --> se remover limit fica errado
```

#### Criando o grid (malha de pontos) para valores não amostrados - appeears

``` r
# vetores para coordenadas x e y selecionadas da base do IBGE1
# Extrair coordenadas da base appeears_modis para definir extensão do grid
x<-appeears_modis$lon
y<-appeears_modis$lat
dis <- 0.5 # distância (do grid) para adensamento de pontos nos estados
grid_geral <- expand.grid( # Criar malha regular
  X=seq(min(x),max(x),dis), # Combinar cada x e y
  Y=seq(min(y),max(y),dis)) |>
  mutate( #teste ponto-no-polígono, TRUE se (X,Y) caem no polígono
    flag_ms = def_pol(X, Y, pol_ms),
    flag_mt = def_pol(X, Y, pol_mt),
    flag_go = def_pol(X, Y, pol_go),
    flag_df = def_pol(X, Y, pol_df)
  ) |>
  filter(flag_ms | flag_go | flag_mt | flag_df) |> # manter pontos correspondentes ao menos 1 dos limites
  select(-c(flag_ms,flag_mt,flag_go,flag_df)) # remover colunas criadas
plot(grid_geral)
sp::gridded(grid_geral) = ~ X + Y
```

#### Interpolação por Krigagem Ordinária - appeears

``` r
df_aux <- appeears_modis |> 
  filter(year == my_year) |> 
  group_by(lon, lat) |> 
  reframe(
    media_ndvi = media_ndvi, # ALTERAR - média dos parâmetros
    .groups = "drop"
  ) # |> sample_n(10000) 
sp::coordinates(df_aux) = ~ lon + lat # Converter data frame para objeto espacial - atribuir as colunas longitude/latitude como coordenadas. Várias funções de geoestatística do pacote gstat (como variogram() e krige()) não aceitam um data frame, mas sim um objeto com coordenadas. Agora, as variáveis vegetativas passam a ser o atributo associado a cada ponto espacial.

form <- media_ndvi ~ 1 # "~ 1" modelo de média constante, mas desconhecida (somente intercepto - assume média global, sem covariáveis).

vari_exp <- gstat::variogram(form, data = df_aux,
                      cressie = FALSE, #estimador clássico do semivar.
                      cutoff = 15, # distância  
                      width = .05) # distancia entre pontos
vari_exp  |>
  ggplot(aes(x=dist, y=gamma)) +
  geom_point() +
  labs(x="lag (º)",
       y=expression(paste(gamma,"(h)")))
```

``` r
patamar=800
alcance=0.25
epepita=780
modelo_1 <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
modelo_2 <- fit.variogram(vari_exp,vgm(patamar,"Exp",alcance,epepita))
modelo_3 <- fit.variogram(vari_exp,vgm(patamar,"Gau",alcance,epepita))
plot_my_models(modelo_1,modelo_2,modelo_3)
modelo <- modelo_1 ## sempre modificar
```

#### 💨 Entrada com a Base: `nasa-power.rds`

``` r
# original archive "nasa-power.rds" = 174,6mb

nasa_power <- read_rds("data/nasa_power.rds") |> 
  rename(
    Radiacao = allsky_sfc_sw_dwn,
    Temperatura = t2m,
    Precipitacao = prectotcorr,
    Umidade = rh2m,
    Vento = ws2m,
    Pressao = ps
  )
  # don't have "state" column - previously filtred
glimpse(nasa_power)

# Temperatura (t2m), precipitação (prectotcorr), radiação solar (allsky) e umidade relativa a 2 m (rh2m), velocidade do vento a 2 metros (ws2m) e pressão na superfície (ps).
```

``` r
nasa_power |> 
  filter(year == 2023) |> 
  ggplot(aes(x=lon,y=lat)) +
  geom_point()
```

#### Classificando cada ponto em município

Já feito no script de faxina “nasa-power.Rmd”

#### Gerar mapa

``` r
# Atribuir ao objeto "variavel" a variável climática da base do nasa power que iremos trabalhar
# Radiacao 
# Temperatura
# Precipitacao
# Umidade 
# Vento
# Pressao

variavel <- "Pressao" #mudar

my_year = 2022
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    nasa_power |> 
      group_by(year, city_ref) |>
      summarise(
        !!variavel := mean(.data[[variavel]],na.rm=TRUE), #Criar coluna com mesmo nome da variavel
        .groups = "drop"
      ) |> 
      rename(name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  filter(year == my_year) |> 
  ggplot()  +
  geom_sf(aes(fill=.data[[variavel]]), color="transparent",
          size=.05, show.legend = TRUE)  +
  geom_point(data = nasa_power |> 
               filter(year==my_year), 
               aes(lon, lat, #size = emission,
                   color="red"))+
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = variavel,
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()
```

#### Criando o grid (malha de pontos) para valores não amostrados - nasa-power

``` r
# vetores para coordenadas x e y selecionadas da base do IBGE1
# Extrair coordenadas da base nasa_power para definir extensão do grid
x<-nasa_power$lon
y<-nasa_power$lat
dis <- 0.5 # distância (do grid) para adensamento de pontos nos estados
grid_geral <- expand.grid( # Criar malha regular
  X=seq(min(x),max(x),dis), # Combinar cada x e y
  Y=seq(min(y),max(y),dis)) |>
  mutate( #teste ponto-no-polígono, TRUE se (X,Y) caem no polígono
    flag_ms = def_pol(X, Y, pol_ms),
    flag_mt = def_pol(X, Y, pol_mt),
    flag_go = def_pol(X, Y, pol_go),
    flag_df = def_pol(X, Y, pol_df)
  ) |>
  filter(flag_ms | flag_go | flag_mt | flag_df) |> # manter pontos correspondentes ao menos 1 dos limites
  select(-c(flag_ms,flag_mt,flag_go,flag_df)) # remover colunas criadas
plot(grid_geral)
sp::gridded(grid_geral) = ~ X + Y
```

#### Interpolação por Krigagem Ordinária - nasa-power

Parâmetros testados para contruir o semivariograma, com base na
variável:

*Temperatura* cutoff = 5,  
width = 0.09 patamar=2.2 alcance=4.5 epepita=0.2

*Radiacao* **Não consegui estabelecer o semivariograma adequado** cutoff
= – width = – patamar = alcance = epepita =

*Precipitacao* cutoff = 6,  
width = 0.5 patamar= 1.35 alcance= 15 epepita= 0.01

*Umidade* **Muitos avisos de warning** ***Warning in
fit.variogram(vari_exp, vgm(patamar, “Sph”, alcance, epepita)) :No
convergence after 200 iterations: try different initial values?***
cutoff = 12,  
width = 0.5 patamar= 60 alcance= 11 epepita= 0.1

*Vento* **3 warning** cutoff = 5,  
width = 0.08 patamar=.2 alcance=1.5 epepita=0

*Pressao* cutoff = 7, width = 0.35 patamar=4.2 alcance=5 epepita=.4

``` r
df_aux <- nasa_power |> 
  filter(year %in% my_year) |> 
  group_by(lon, lat) |> 
  summarise(
    !!variavel := mean(.data[[variavel]],na.rm=TRUE), # média temperatura
    .groups = "drop"
  ) # |> sample_n(546) # tamanho máximo dos dados
sp::coordinates(df_aux) = ~ lon + lat # Converter data frame para objeto espacial - atribuir as colunas longitude/latitude como coordenadas. Várias funções de geoestatística do pacote gstat (como variogram() e krige()) não aceitam um data frame, mas sim um objeto com coordenadas. Agora, a variável passa a ser o atributo associado a cada ponto espacial.

# Converter string em fórmula para atribuir a variavel preestabelecida
form <- as.formula(paste(variavel, "~ 1")) 

vari_exp <- gstat::variogram(form, data = df_aux,
                      cressie = FALSE, #estimador clássico do semivar.
                      cutoff = 7, # distância  
                      width = 0.35) # distancia entre pontos
vari_exp  |>
  ggplot(aes(x=dist, y=gamma)) +
  geom_point() +
  labs(x="lag (º)",
       y=expression(paste(gamma,"(h)")))
```

``` r
patamar=4.2
alcance=5
epepita=.4
modelo_1 <- fit.variogram(vari_exp,vgm(patamar,"Sph",alcance,epepita))
modelo_2 <- fit.variogram(vari_exp,vgm(patamar,"Exp",alcance,epepita))
modelo_3 <- fit.variogram(vari_exp,vgm(patamar,"Gau",alcance,epepita))
plot_my_models(modelo_1,modelo_2,modelo_3)
modelo <- modelo_1 ## sempre modificar
```

``` r
ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                     block=c(0.1,0.1),
                     nsim=0,
                     na.action=na.pass,
                     debug.level=-1
)
```

``` r
ko_variavel |> 
  as_tibble() |> 
    ggplot(aes(x=X, y=Y)) +
  geom_tile(aes(fill = var1.pred)) +
  scale_fill_viridis_c(option = "mako") +
  coord_equal() +
  labs(x="Longitude",
       y="Latitude",
       fill=variavel,
       title = my_year) +
  theme_bw()
```

``` r
df_kgr <- ko_variavel |> 
      as_tibble() |> 
      select(-var1.var) |> 
      rename(lon=X,lat=Y,!!variavel :=var1.pred)  |> 
      mutate(city_ref = "Other",
             state = ifelse(def_pol(lon, lat, pol_ms),"MS",
                            ifelse(def_pol(lon, lat, pol_mt),"MT",
                            ifelse(def_pol(lon, lat, pol_go),"GO",
                            "DF"))) 
             )
resul <- vector()
estado <- df_kgr$state
for(i in 1:nrow(df_kgr)){
  if(estado[i]!="Other"){
    my_citys_obj <- municipality %>%
      filter(abbrev_state == estado[i])
    n_citys <- nrow(my_citys_obj)
    my_citys_names <- my_citys_obj %>% pull(name_muni)
    resul[i] <- "Other"
    for(j in 1:n_citys){
      pol_city <- my_citys_obj$geom  %>%
        purrr::pluck(j) %>%
        as.matrix()
      if(def_pol(df_kgr$lon[i],
                 df_kgr$lat[i],
                 pol_city)){
        resul[i] <- my_citys_names[j]
      }
    }
  }
}
df_kgr$city_ref <- resul
```

``` r
municipality |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    nasa_power |> 
      filter(year == my_year) |> 
      select(lon,lat,variavel,state,city_ref) |> 
      rbind(
        df_kgr
      ) |> 
      group_by(city_ref) |> 
      summarise(
        !!variavel := mean(.data[[variavel]],na.rm=TRUE),
        .groups = "drop"
      ) |> 
      rename(  name_muni = city_ref),
    by = c("name_muni")
  ) |> 
  mutate(
    !!variavel := ifelse(is.na(.data[[variavel]]),median(.data[[variavel]],na.rm = TRUE),.data[[variavel]])) |>
  ggplot()  +
  geom_sf(aes(fill=.data[[variavel]]), color="transparent",
          size=.05, show.legend = TRUE)  +
  # geom_point(data = df_kgr, 
  #            aes(lon, lat, #size = emission,
  #                color="red")) +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = variavel,
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c()
```

#### Estimativa da variável para o Brasil Central - nasa-power

``` r
nome_variavel <- paste0("nasa_power_",variavel,"_kgr")

nome_variavel <- map_df(2015:2023,~{
  set.seed(1235)
  df_aux <- nasa_power |>
    group_by(lon, lat) |>
    filter(year == .x) |>
    summarise(
      !!variavel := mean(.data[[variavel]],na.rm=TRUE),
      .groups = "drop"
    ) 
  sp::coordinates(df_aux) = ~ lon + lat
  form <- as.formula(paste(variavel, "~ 1")) 
  vari_exp <- gstat::variogram(form, data = df_aux,
                               cressie = FALSE,
                               cutoff = 7, # !! mudar
                               width = 0.35) # !! mudar
  vari_exp  |>
    ggplot(aes(x=dist, y=gamma)) +
    geom_point() +
    labs(x="lag (º)",
         y=expression(paste(gamma,"(h)")))
  patamar=2.2
  alcance=4.5
  epepita=0.2
  modelo <- fit.variogram(vari_exp,vgm(patamar,"Exp",alcance,epepita))
  ko_variavel <- krige(formula=form, df_aux, grid_geral, model=modelo,
                       block=c(0.1,0.1),
                       nsim=0,
                       na.action=na.pass,
                       debug.level=-1
  )
  df_kgr <- ko_variavel |>
      as_tibble() |>
      select(-var1.var) |>
      rename(lon=X,lat=Y,!!variavel :=var1.pred)  |>
      mutate(city_ref = "Other",
             state = ifelse(def_pol(lon, lat, pol_ms),"MS",
                            ifelse(def_pol(lon, lat, pol_mt),"MT",
                            ifelse(def_pol(lon, lat, pol_go),"GO",
                            "DF")))
             )
  resul <- vector()
  estado <- df_kgr$state
  for(i in 1:nrow(df_kgr)){
    if(estado[i]!="Other"){
      my_citys_obj <- municipality %>%
        filter(abbrev_state == estado[i])
      n_citys <- nrow(my_citys_obj)
      my_citys_names <- my_citys_obj %>% pull(name_muni)
      resul[i] <- "Other"
      for(j in 1:n_citys){
        pol_city <- my_citys_obj$geom  %>%
          purrr::pluck(j) %>%
          as.matrix()
        if(def_pol(df_kgr$lon[i],
                   df_kgr$lat[i],
                   pol_city)){
          resul[i] <- my_citys_names[j]
        }
      }
    }
  }
  df_kgr$city_ref <- resul

  df_final <- df_kgr |>
        mutate(year = .x)
  return(df_final)
})
write_rds(nome_variavel,paste0("data-raw/nasa-power-",variavel,"-kgr.rds"))
```

``` r
# Rodar somente quando necessário!!!!
nasa_power_kgr <- read_rds(paste0("data-raw/nasa-power-",variavel,"-kgr.rds"))
```

``` r
nasa_power_bind <- nasa_power |> 
  select(lon,lat,.data[[variavel]],city_ref,state,year) |> 
  rbind(nasa_power_kgr)

map(2015:2023,~{
  municipality |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      nasa_power_bind |> 
        filter(year == .x) |> 
        select(lon,lat,.data[[variavel]],state,city_ref) |> 
        group_by(city_ref) |> 
        summarise(
          !!variavel := mean(.data[[variavel]],na.rm=TRUE),
          .groups = "drop"
        ) |> 
        rename(name_muni = city_ref),
      by = c("name_muni")
    ) |> 
    mutate(
      !!variavel := ifelse(is.na(.data[[variavel]]),median(.data[[variavel]],na.rm = TRUE),.data[[variavel]])) |>
    ggplot()  +
    geom_sf(aes(fill=.data[[variavel]]), color="transparent",
            size=.05, show.legend = TRUE)  +
    # geom_point(data = df_kgr, 
    #            aes(longitude, latitude, #size = emission,
    #                color="red")) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = variavel,
         x = 'Longitude',
         y = 'Latitude',
         title = .x) +
    scale_fill_viridis_c()})
```

–\>

### 💨 Entrada com a Base: `prodes-deforestation.rds`

``` r
# original archive "prodes-deforestation.rds" = 2.2gb

prodes_deforestation <- read_rds("data/prodes-deforestation.rds")
  # sample_n(1000000)
  # "state" column previously filtred 

glimpse(prodes_deforestation)
```

``` r
prodes_deforestation |> 
  sample_n(100000) |> 
  filter(categorie == 15) |> 
  ggplot(aes(x=x,y=y)) +
  geom_point()
```

#### Gerar mapa

``` r
# Alocando intensidade com base nas observações de desmatamento no ano
df_prodes <- prodes_deforestation |> 
  group_by(categorie, state, muni) |> 
  count() |> 
  group_by(categorie) |> 
  mutate(
    percent = n/sum(n)*100
  )
```

``` r
# Gerando o mapa de intensidade de desmatamento
 municipality |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      df_prodes |> 
        filter(categorie == 22) |>  # mudar anos
        rename(name_muni = muni),
      by = c("name_muni")
    ) |> 
  ggplot() +
   geom_sf(aes(fill=percent), color="transparent",
            size=.05, show.legend = TRUE)  +
    # geom_point(data = df_kgr, 
    #            aes(longitude, latitude, #size = emission,
    #                color="red")) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'Intensidade',
         x = 'Longitude',
         y = 'Latitude',
         title = 'Desmatamento') +
    scale_fill_viridis_c()

# Município em destaque no mapa é Corumbá (para anos como 2022)
 # municipality |> 
 #    filter(abbrev_state %in% my_states) |> 
 #   filter(
 #     name_muni == "Corumbá"
 #   ) |> 
 #    left_join(
 #      df_prodes |> 
 #        filter(categorie == 16) |> 
 #        rename(name_muni = muni),
 #      by = c("name_muni")
 #    ) 
```

–\>

### 💨 Entrada com a Base: `deter_queimadas.rds`

É importante ressaltar que, embora diversos estados estejam contemplados
nas observações, estes não apresentam informações referentes a
queimadas, somente desmatamento ou outras.

Apenas o estado do Mato Grosso apresenta observações de queimadas

Disponibilidade de dados de cicatriz de queimada para biomas como
Amazônia e Pantanal (<https://terrabrasilis.dpi.inpe.br/downloads>)

``` r
# original archive "deter-queimadas.rds" = 122,1mb

deter_queimadas <- read_rds("data/deter_queimadas.rds")

# glimpse(deter_queimadas)

# deter_queimadas |> 
#   filter(UF == "MT",
#          ANO == 2024,
#          CLASSNAME == "CICATRIZ_DE_QUEIMADA") |> 
#   glimpse()
```

``` r
deter_queimadas |> 
  # pull(ANO) |> unique()
  filter(ANO == 2020) |> 
  ggplot(aes(x=longitude,y=latitude)) +
  geom_point()
```

### Padronizando nomes dos municípios da base DETER com os do pacote geobr

Este chunk tem como objetivo padronizar para posterior incorporação,
necessária para evitar perda de informação durante a geração dos mapas

``` r
library(stringi)  # para normalização de strings

# Alocando área de queimadas
df_deter <- deter_queimadas |> 
  filter(UF %in% my_states) |> 
  rename(name_muni = MUNICIPALI) |> 
  select(name_muni, ANO, AREAMUNKM,) |> 
  arrange(name_muni) |> 
  group_by(ANO, name_muni) |> 
  summarise(
    area_queimada_muni_km = sum(AREAMUNKM, na.rm = TRUE),
    .groups = "drop"
  ) |> 
  mutate(
    name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
    name_muni = trimws(name_muni)
  )

# glimpse(df_deter)

# Pacote geobr 
munic_geobr <- municipality |> 
  filter(abbrev_state %in% my_states) |> 
  select(name_muni, abbrev_state) |> 
  arrange(name_muni) |>  
  mutate(
    name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
    #stri_trans_general(..., "Latin-ASCII") → remove acentos e normaliza para comparação;
    #tolower() → padroniza para minúsculas;
    #trimws() → remove espaços extras.
    name_muni = trimws(name_muni)
  )

glimpse(munic_geobr)
```

#### Gerar mapa - deter

``` r
my_year = 2022 # mudar anos (detalhe: alguns anos, como 2016, só tem para 1 estado)

# Fazer filtro por ano antes do join para passar NA = 0 nos municípios faltantes
df_deter_ano <- df_deter |> 
  filter(ANO == my_year)

munic_geobr |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    df_deter_ano |> 
      group_by(ANO, name_muni) |> 
      summarise(area_queimada_muni_km = sum(area_queimada_muni_km, na.rm = TRUE)),
    by = "name_muni"
  ) |> 
  mutate(area_queimada_muni_km = replace_na(area_queimada_muni_km, 0)) |>
  ggplot() +
  geom_sf(aes(fill=area_queimada_muni_km), color="transparent",
          size=.05, show.legend = TRUE) +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(.9), color = "black"),
    axis.title.x = element_text(size = rel(1.1), color = "black"),
    axis.text.y = element_text(size = rel(.9), color = "black"),
    axis.title.y = element_text(size = rel(1.1), color = "black"),
    legend.text = element_text(size = rel(1), color = "black"),
    legend.title = element_text(face = 'bold', size = rel(1.2))
  ) +
  labs(fill = 'Queimadas (área km)',
       x = 'Longitude',
       y = 'Latitude') +
  scale_fill_viridis_c(
    option = "inferno"
  )
```
