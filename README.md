
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
library(purrr) # criar funções
library(tibble)
source("R/my-function.R") 
#> List of polygons loaded [list_pol]
```

#### Definindo estados

``` r
my_states <- c("MS","MT","GO","DF")
```

### 💨 Entrada com a Base: `emissions-sources.rds`

``` r
emissions_sources <- read_rds("../data/emissions-sources.rds")|> 
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
data_set_kgr2 <- data_set_kgr |> 
  group_by(year, state, city_ref, variable) |> 
  summarise(
    value_mean = mean(value, na.rm=TRUE),
    .groups = "drop") |>
  pivot_wider(names_from = variable, values_from = value_mean)

# data_set_kgr |>
#   group_by(year,state) |>
#   count()
```

### Criar os mapas por variáveis por ano para verifcar os municípios não plotados

Vamos verificar onde estão os NA

``` r
my_year <- 2015 # definindo ano
variavel <- "xch4" # definindo a variável
anos <- if (variavel == "xch4") 2015:2021 else 2015:2023 #definindo anos, caso a variável seja xch4, anos até 2021, que é até onde contém os dados da variável

# Plotando mapas variável/ano
mapas <- map(anos, function(my_year) { #map -> Aplicando função para cada elemento de vetor
  municipality |> 
    filter(abbrev_state %in% my_states) |> 
    left_join( 
      data_set_kgr_bind2 |>
        filter(variavel == all_of(variavel),
               state %in% my_states) |> 
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

Foram verificados: 1. Classificação por estado e municípios das bases 2.
Adição da base 3. Krigagem

Desde a varificação 1, observa-se somente cerca de 90 observações para
os municípios do estado de GO, estando ausentes mais de 150 municípios.
Não foram verificados problemas em nenhuma destas verificações.

O problema esta que, a krigagem é feita, mas não adicionam os valores
observados, apenas é possível visualizá-los no plot, ou seja, o arquivo
kgr.rds gerado não contém tais dados, ficando como “NA”.

Para resolver, deve-se agregar a krigagem à geometria municipal para que
todos os municípios sejam preenchidos.  
Isto ja havia sido feito em “nasa_xco2_bind”, no entanto, não foi este o
arquivo kgr salvo na pasta data-raw, logo gerando os NAs mesmo após a
krigagem. Sendo assim, basta salvar fazer o bind e salvar os arquivos de
cada variável

### ⛓️ Carregando as novas bases

``` r
# Empilhando lista de caminho de arquivos
file_kgr_bind <- list.files("data/",
                      full.names = TRUE,pattern = "bind")

# Vetor para padronizar nomes para lat e lon
new_names_b = c(lat = "latitude", lon = "longitude")

# Função para leitura e padronização dos nomes das colunas/variáveis dos arquivos kgr
read_kgr <- function(path){
  df <- readr::read_rds(path) |> 
    janitor::clean_names() |> # padronizar colunas
    dplyr::rename(dplyr::any_of(new_names_b))
  
  nome <- df[3] |> names()    
  new_name_b <- c(value = nome)
  df <- df |> 
    mutate(
      variable = nome
    ) |> 
    dplyr::rename(dplyr::any_of(new_name_b))
  return(df)  
};read_kgr(file_kgr_bind[1])

# Aplicando função para leitura e construindo novo DataFrame
data_set_kgr_bind <- map_df(file_kgr_bind,read_kgr)

# Reorganizando DataFrame criado
data_set_kgr_bind2 <- data_set_kgr_bind |> 
  filter(year %in% 2015:2023, # período de análise
         state %in% my_states) |> 
  group_by(year, state, city_ref, variable) |> 
  summarise(
    value_mean = mean(value, na.rm=TRUE),
    .groups = "drop") |>
  pivot_wider(names_from = variable, values_from = value_mean) # reduz linhas
```

### Função para atribuir a mediana em um município, a partir da observação média da mediana de municípios vizinhos

``` r
# Função para imputar NAs pela mediana dos até n vizinhos mais próximos
impute_NAs_vizinhos <- function( # determinando parâmetros da função
  df,
  coords = NULL,                # data.frame com colunas city_col, lat_col, lon_col
  vars = NULL,                  # vetores de colunas a imputar; se NULL, usa todas exceto agrupadoras
  n_neighbors = 3,
  year_col = "year",
  state_col = "state",
  city_col = "city_ref",
  lat_col = "lat",
  lon_col = "lon",
  same_state = TRUE,
  verbose = TRUE
){
  # checagens iniciais
  if (!is.null(coords) && !all(c(city_col, lat_col, lon_col) %in% names(coords))) {
    stop("Se usar 'coords', ela deve conter colunas: ", paste(c(city_col, lat_col, lon_col), collapse = ", "))
  }
  if (!is.null(coords) && !requireNamespace("geosphere", quietly = TRUE)) {
    stop("Instale o pacote 'geosphere' para usar coordenadas: install.packages('geosphere')")
  }

  df <- as.data.frame(df)
  if (is.null(vars)) {
    vars <- setdiff(names(df), c(year_col, state_col, city_col))
  }

  # normaliza coords (se houver)
  if (!is.null(coords)) {
    coords <- as.data.frame(coords)
    coords_map <- coords[!duplicated(coords[[city_col]]), c(city_col, lat_col, lon_col)]
  }

  out_df <- df
  imputed_list <- list()

  years <- unique(df[[year_col]])
  for (y in years) {
    sub <- df[df[[year_col]] == y, , drop = FALSE]

    for (var in vars) {
      nas_idx <- which(is.na(sub[[var]]))
      if (length(nas_idx) == 0) next

      for (i in nas_idx) {
        city <- sub[[city_col]][i]
        city_state <- sub[[state_col]][i]

        # --- obter lista de candidatos vizinhos disponíveis (não-NA) ---
        neighs_used <- character(0)
        
        if (!is.null(coords)) {
          # usar coords + distância geodésica
          # busca coords do alvo
          tgt_row <- coords_map[coords_map[[city_col]] == city, , drop = FALSE]
          if (nrow(tgt_row) == 0) {
            if (verbose) message("Sem coords para ", city, " (ano ", y, "). Pulando.")
            next
          }
          tgt_lon <- as.numeric(tgt_row[[lon_col]][1])
          tgt_lat <- as.numeric(tgt_row[[lat_col]][1])

          # candidatos: mesmos ano, (opcionalmente) mesmo estado, valor não-NA, != self
          candidates <- sub[!is.na(sub[[var]]), , drop = FALSE]
          if (same_state) candidates <- candidates[candidates[[state_col]] == city_state, , drop = FALSE]
          candidates <- candidates[candidates[[city_col]] != city, , drop = FALSE]
          if (nrow(candidates) == 0) {
            if (verbose) message("Nenhum candidato não-NA para ", city, " / ", var, " em ", y)
            next
          }

          # obter coords dos candidatos
          cand_idx <- match(candidates[[city_col]], coords_map[[city_col]])
          valid_cand <- !is.na(cand_idx) & !is.na(coords_map[[lon_col]][cand_idx]) & !is.na(coords_map[[lat_col]][cand_idx])
          if (!any(valid_cand)) next

          cand_cities <- candidates[[city_col]][valid_cand]
          cand_coords_mat <- cbind(
            as.numeric(coords_map[[lon_col]][cand_idx[valid_cand]]),
            as.numeric(coords_map[[lat_col]][cand_idx[valid_cand]])
          )

          # distâncias e ordenação
          dists <- geosphere::distHaversine(matrix(c(tgt_lon, tgt_lat), nrow = 1),
                                            cand_coords_mat)
          ord <- order(dists, na.last = NA)
          neighs_used <- cand_cities[ord][1:min(length(ord), n_neighbors)]
        }

        # se conseguimos vizinhos, imputar mediana
        if (length(neighs_used) == 0) next
        neighbor_vals <- sub[[var]][match(neighs_used, sub[[city_col]])]
        new_value <- median(neighbor_vals, na.rm = TRUE)

        # atribuir ao data.frame de saída
        idx_out <- which(out_df[[year_col]] == y & out_df[[city_col]] == city)
        if (length(idx_out) >= 1) {
          out_df[idx_out, var] <- new_value
        }

        # registrar
        imputed_list[[length(imputed_list) + 1]] <-
          tibble::tibble(
            year = y,
            city_ref = city,
            state = city_state,
            variable = var,
            n_neighbors = length(neighs_used),
            neighbors = paste0(neighs_used, collapse = "|"),
            imputed_value = new_value
          )
      } # end each NA row
    } # end each var
  } # end each year

  imputation_log <- if (length(imputed_list) > 0) dplyr::bind_rows(imputed_list) else tibble::tibble()
  return(list(data = out_df, log = imputation_log))
}
```

``` r
# data_set_kgr_bind2  (Com: year, state, city_ref, e variáveis a imputar)
# muni_coords         (Colunas: city_ref, latitude, longitude)

# Pegando os municípios e suas coordenadas
muni_coords <- data_set_kgr_bind |>
  filter(
    state %in% my_states
  ) |>
  select(city_ref, lat, lon) |>
  distinct()

# Variáveis a imputar/completar 
vars_to_impute <- c("precipitacao","temperatura","radiacao","vento","umidade","xco2","xch4","sif_757","pressao")

# Resultado 
result <- impute_NAs_vizinhos(
  df = data_set_kgr_bind2,
  coords = muni_coords,
  vars = vars_to_impute,
  n_neighbors = 3, # n° de municípios vizinhos
  year_col = "year",
  state_col = "state",
  city_col = "city_ref",
  lat_col = "lat",
  lon_col = "lon",
  same_state = TRUE
)

# Banco de dados com NAs preenchidos (quando possível)
df_kgr_preenchido <- result$data       
df_kgr_preenchido

# Analisar quais municípios/variáveis foram imputados
# imputation_log <- result$log 

# Contagem de NAs
# sum(is.na(filled_df)) # reduziram drasticamente

# Nenhum candidato não-NA para xch4 a partir de 2022 pois só contém até o ano de 2021
```
