
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
  - [nasapower](https://power.larc.nasa.gov/): Variáveis climáticas
    (Temperatura; precipitação; radiação solar; umidade relativa;
    velocidade do vento e pressão) de 2015 a 2024  
  - [DETER](https://terrabrasilis.dpi.inpe.br/downloads/): Dados de
    focos de fogo (cicatriz de queimadas)  
  - [Desmatamento - INPE - PRODES - Plataforma
    Terrabrasilis](https://terrabrasilis.dpi.inpe.br/geonetwork/srv/eng/catalog.search#/metadata/fe02f2bf-2cc0-49d5-ab72-a3954f997408):
    Dados sobre desmatamento de 31/07/2000 a 30/07/2023  
- **Dados adicionais adquiridos (não utilizados no trabalho)**
  - [NASA](https://climate.nasa.gov/): Dados climáticos  
  - [NASA-FIRMS](https://firms.modaps.eosdis.nasa.gov): Dados de focos
    de incêndio de 2015 a 2025  
  - [BDQUEIMADAS](https://terrabrasilis.dpi.inpe.br/queimadas/bdqueimadas/#exportar-dados):
    Dados de focos de incêndio de 2015 a 2025  
  - [Programa Queimadas - INPE - Plataforma
    Terrabrasilis](https://terrabrasilis.dpi.inpe.br/queimadas/portal/):
    Dados de focos de queimadas x Supressão da vegetação nativa de
    08/2018 a 01/2025 & Dados de focos de fogo ativo de 1998 a
    21/01/2025  

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
emissions_sources <- read_rds("data/emissions_sources.rds")|> 
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

<!--
### ⛓️ Carregando as novas bases
&#10;
``` r
# Empilhando lista de caminho de arquivos
file_kgr_bind <- list.files("data/",
                      full.names = TRUE,pattern = "bind")
&#10;# Vetor para padronizar nomes para lat e lon
new_names_b = c(lat = "latitude", lon = "longitude")
&#10;# Função para leitura e padronização dos nomes das colunas/variáveis dos arquivos kgr
read_kgr <- function(path){
  df <- readr::read_rds(path) |> 
    janitor::clean_names() |> # padronizar colunas
    dplyr::rename(dplyr::any_of(new_names_b))
  &#10;  nome <- df[3] |> names()    
  new_name_b <- c(value = nome)
  df <- df |> 
    mutate(
      variable = nome
    ) |> 
    dplyr::rename(dplyr::any_of(new_name_b))
  return(df)  
};read_kgr(file_kgr_bind[1])
&#10;# Aplicando função para leitura e construindo novo DataFrame
data_set_kgr_bind <- map_df(file_kgr_bind,read_kgr)
&#10;# Reorganizando DataFrame criado
data_set_kgr_bind2 <- data_set_kgr_bind |> 
  filter(year %in% 2015:2023, # período de análise
         state %in% my_states) |> 
  group_by(year, state, city_ref, variable) |> 
  summarise(
    value_mean = mean(value, na.rm=TRUE),
    .groups = "drop") |>
  pivot_wider(names_from = variable, values_from = value_mean) # reduz linhas
```
&#10;### Criar os mapas por variáveis por ano para verifcar os municípios não plotados 
&#10;Vamos verificar onde estão os NA
&#10;
``` r
# my_year <- 2015 # definindo ano
# variavel <- "xch4" # definindo a variável
# anos <- if (variavel == "xch4") 2015:2021 else 2015:2023 #definindo anos, caso a variável seja xch4, anos até 2021, que é até onde contém os dados da variável
# 
# # Plotando mapas variável/ano
# mapas <- map(anos, function(my_year) { #map -> Aplicando função para cada elemento de vetor
#   municipality |> 
#     filter(abbrev_state %in% my_states) |> 
#     left_join( 
#       data_set_kgr_bind2 |>
#         filter(variavel == all_of(variavel),
#                state %in% my_states) |> 
#         group_by(year, city_ref) |> 
#         rename(name_muni = city_ref),
#       by = c("name_muni")
#     ) |> 
#     filter(year == my_year) |> 
#     ungroup() |> 
#     ggplot()  +
#     geom_sf(aes(fill = variavel), color="transparent",
#             size=.05, show.legend = TRUE) +
#     labs(title = paste("Ano:", my_year, "-", variavel))
#   
# })
# 
# mapas[[1]]
&#10;# municipality |>
#   filter(abbrev_state %in% my_states) |> 
#   ggplot() +
#   geom_sf() +
#   geom_point(data = data_set_kgr,
#              aes(x = lon, y = lat, color = "red"))
```
&#10;Foram verificados: 
1. Classificação por estado e municípios das bases
2. Adição da base
3. Krigagem
&#10;Desde a varificação 1, observa-se somente cerca de 90 observações para os municípios do estado de GO, estando ausentes mais de 150 municípios. Não foram verificados problemas em nenhuma destas verificações.
&#10;O problema esta que, a krigagem é feita, mas não adicionam os valores observados, apenas é possível visualizá-los no plot, ou seja, o arquivo kgr.rds gerado não contém tais dados, ficando como "NA".
&#10;Para resolver, deve-se agregar a krigagem à geometria municipal para que todos os municípios sejam preenchidos.   
  Isto ja havia sido feito em "nasa_xco2_bind", no entanto, não foi este o arquivo kgr salvo na pasta data-raw, logo gerando os NAs mesmo após a krigagem.
    Sendo assim, basta salvar fazer o bind e salvar os arquivos de cada variável
&#10;### Função para atribuir a mediana em um município, a partir da observação média da mediana de municípios vizinhos 
&#10;
``` r
# Função para imputar NAs pela mediana dos até n vizinhos mais próximos
impute_NAs_vizinhos <- function( 
    # Determinando parâmetros e valores da função
  df,
  coords = NULL,  # data.frame com colunas city_col, lat_col, lon_col
  vars = NULL,    # vetores de colunas a imputar; se NULL, usa todas exceto agrupadoras
  n_neighbors = 3, # n° de vizinhos para calcular mediana
  year_col = "year", # nome da coluna com o ano
  state_col = "state", # nome da coluna com o estado
  city_col = "city_ref", # nome da coluna com o município
  lat_col = "lat", # nome da coluna com a latitude
  lon_col = "lon", # nome da coluna coma longitude
  same_state = TRUE, # só considera vizinhos do mesmo estado
  verbose = TRUE # mostrar mensagens de aviso no console
){
  # Checagens iniciais:
  &#10;    # Verificar se o data.frame tem as colunas city_col...
  if (!is.null(coords) && !all(c(city_col, lat_col, lon_col) %in% names(coords)))
    &#10;    # Verificar se o pacote geosphere (usado para calcular distâncias entre coordenadas geográficas) está instalado.
  if (!is.null(coords) && !requireNamespace("geosphere", quietly = TRUE)) {
    stop("Instale o pacote 'geosphere' para usar coordenadas: install.packages('geosphere')")
  }
&#10;  # Garantir que df esteja no formato data.frame
  df <- as.data.frame(df)
  &#10;  # Encontrar a diferença entre dois conjuntos pelo "setdiff", retornando elementos do primeiro conjunto "(names (df))", ou seja, retornam as colunas do df que não sejam as de identificação "year_col, state_col, city_col".
  if (is.null(vars)) {
    vars <- setdiff(names(df), c(year_col, state_col, city_col))
  }
&#10;  # Normalizar coords 
  if (!is.null(coords)) {
    coords <- as.data.frame(coords)
    coords_map <- coords[!duplicated(coords[[city_col]]), c(city_col, lat_col, lon_col)] # remover duplicatas
  }
&#10;  # Objetos de saída
  out_df <- df # cópia do ddf, onde os valores imputados serão salvos
  imputed_list <- list() # guardará um registro com tudo o que foi imputado
&#10;  # Loop pelos anos
  years <- unique(df[[year_col]]) # extrai anos únicos
  for (y in years) { # y contém o valor do ano atual na iteração
    sub <- df[df[[year_col]] == y, , drop = FALSE] # cria subconjunto com os dados apenas do ano determinado e garante que seja um data.frame (drop = FALSE)
    # 'sub' é o subconjunto do data.frame contendo apenas os dados de um único ano
&#10;    # Loop pelas variáveis
    for (var in vars) {
      nas_idx <- which(is.na(sub[[var]])) # encontrar quais linhas tem NA
      if (length(nas_idx) == 0) next # Se não encontra NA passa
&#10;      # Loop por cada NA
      for (i in nas_idx) {
        city <- sub[[city_col]][i] # guarda cidade
        city_state <- sub[[state_col]][i] # guarda estado
&#10;        # Vetor vazio para depois armazenar os vizinhos usados para imputar o valor
        neighs_used <- character(0)
        &#10;        # Busca dos vizinhos mais próximos
        if (!is.null(coords)) {
          &#10;          # Busca coords da cidade atual
          tgt_row <- coords_map[coords_map[[city_col]] == city, , drop = FALSE]
          # Se não cncontrar mostra mensagem e pula
          if (nrow(tgt_row) == 0) {
            if (verbose) message("Sem coords para ", city, " (ano ", y, "). Pulando.")
            next
          }
          tgt_lon <- as.numeric(tgt_row[[lon_col]][1])
          tgt_lat <- as.numeric(tgt_row[[lat_col]][1])
&#10;          # Seleção dos 'candidatos' a vizinhos
            # Candidatos com mesmos ano, (opcionalmente) mesmo estado (se same_state = TRUE), valor não-NA, != self
          candidates <- sub[!is.na(sub[[var]]), , drop = FALSE] # valor não-NA
          # 'candidates' passa a ser um subconjunto do ano atual contendo apenas as cidades que têm valores válidos (não NA) para aquela variável
          &#10;          # Filtro adicional opcional controlado pelo parâmetro 'same_state'
          # Se same_state = TRUE, então:
            # Filtra o data.frame de candidatos para manter apenas os municípios do mesmo estado (state_col) da cidade-alvo (city_state)
          # Se same_state = FALSE, então:
            # A linha é ignorada (nenhum filtro é aplicado)
          if (same_state) candidates <- candidates[candidates[[state_col]] == city_state, , drop = FALSE]
          &#10;          # Remover própria cidade da lista de candidatos
          candidates <- candidates[candidates[[city_col]] != city, , drop = FALSE]
          &#10;          # Verificar se sobrou algum candidato
          if (nrow(candidates) == 0) { # contagem de cidades que restaram
            if (verbose) message("Nenhum candidato não-NA para ", city, " / ", var, " em ", y) 
            next
          }
&#10;          # Obter coords dos candidatos e verificar quais não são NA em lat/lon
          cand_idx <- match(candidates[[city_col]], coords_map[[city_col]])
          valid_cand <- !is.na(cand_idx) & !is.na(coords_map[[lon_col]][cand_idx]) & !is.na(coords_map[[lat_col]][cand_idx])
          if (!any(valid_cand)) next
&#10;          # Calcular distâncias e ordenar
            # Este trecho:
              # Cria uma matriz com as coordenadas dos candidatos válidos;
              # Usa geosphere::distHaversine() para calcular a distância geográfica (em metros) entre a cidade-alvo e os candidatos;
              # Ordena os municípios pela menor distância (ord);
              # Seleciona apenas os n vizinhos mais próximos, definidos em n_neighbors (por padrão, 3).
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
&#10;        # Imputação do valor
          # Se conseguimos vizinhos, imputar mediana
            # Este trecho:
             # Pega os valores da variável (var) nos vizinhos escolhidos.
             # Calcula a mediana desses valores.
             # Essa mediana será o novo valor imputado.
        if (length(neighs_used) == 0) next
        neighbor_vals <- sub[[var]][match(neighs_used, sub[[city_col]])]
        new_value <- median(neighbor_vals, na.rm = TRUE)
&#10;        # Atribuir ao data.frame de saída
          # Este trecho:
            # Encontra a linha correspondente no out_df (mesmo ano e cidade) e substitui o NA pelo valor imputado (new_value)
        idx_out <- which(out_df[[year_col]] == y & out_df[[city_col]] == city)
        if (length(idx_out) >= 1) {
          out_df[idx_out, var] <- new_value
        }
&#10;        # Registrar no log os detalhes da imputação
          # Este trecho:  
            # Cria um registro com detalhes da imputação:
            # ano, cidade, estado, variável imputada, número de vizinhos usados, quais foram, e o valor imputado.
            # Cada registro é guardado como um tibble dentro de imputed_list.
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
&#10;  # Finalização
    # Este trecho:
      # Junta todos os registros (imputed_list) em um único data frame chamado imputation_log.
      # Retorna uma lista com dois elementos:
      # data → o banco com NAs preenchidos (out_df)
      # log → o histórico de imputações realizadas (imputation_log)
  imputation_log <- if (length(imputed_list) > 0) dplyr::bind_rows(imputed_list) else tibble::tibble()
  return(list(data = out_df, log = imputation_log))
}
```
&#10;
### Aplicando a função `impute_NAs_vizinhos`
&#10;
``` r
# data_set_kgr_bind2  (Com: year, state, city_ref, e variáveis a imputar)
# muni_coords         (Colunas: city_ref, latitude, longitude)
&#10;# Criando uma tabela auxiliar contendo lat/lon de cada município
muni_coords <- data_set_kgr_bind |>
  filter(
    state %in% my_states
  ) |>
  select(city_ref, lat, lon) |>
  distinct()
&#10;# Lista de variáveis a imputar/completar 
vars_to_impute <- c("precipitacao","temperatura","radiacao","vento","umidade","xco2","xch4","sif_757","pressao")
&#10;# Resultado (chamada da função de imputação)
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
&#10;# Banco de dados com NAs preenchidos
df_kgr_preenchido <- result$data       
df_kgr_preenchido
&#10;# Analisar quais municípios/variáveis foram imputados
# imputation_log <- result$log 
&#10;# Contagem de NAs
# sum(is.na(filled_df)) # reduziram drasticamente
&#10;# Observação:
# Nenhum candidato não-NA para xch4 a partir de 2022 pois só contém até o ano de 2021
&#10;# Carregar base atual para posterior incorporação com as restantes
# write_rds(df_kgr_preenchido, "data/parcial_base.rds")
```
&#10;### Verificação dos valores NA preenchidos (grande maioria para municiípios de GO)
&#10;``` r
# data_set_kgr_bind2 |> 
#   filter(
#     state == 'GO'
#   )
# 
# data_set_kgr_bind2 |> 
#   filter(state == 'MS')
# 
# df_kgr_preenchido |> 
#   filter(state == 'GO')
# 
# df_kgr_preenchido |> 
#   filter(state == 'MS')
```
-->

## 💨 Entrada com a base parcial `parcial_base.rds`

**É a mesma que a “df_kgr_preenchido”**

Essa base apresenta os dados do nasapower, oco2 e gosat. Portanto,
faltam incorporar as bases do modis, deter, prodes e a climate trace.

``` r
base_parcial <- read_rds("data/parcial_base.rds")
```

### 🔋 Carregando e tratando as bases faltantes

``` r
# Carregando bases
deter <- read_rds("data/deter_queimadas.rds")
prodes <- read_rds("data/prodes_deforestation.rds")
modis <- read_rds("data/appeears_modis.rds")
climate_trace <- read_rds("data/emissions_sources.rds")

# DETER --------------------------------------------
# Tratando base deter
deter_trat <- deter |> 
  rename(state = UF,
         year = ANO,
         city_ref = MUNICIPALI,
         area_queimada = AREAMUNKM) |> 
  select(state, city_ref, year, area_queimada) |> 
  filter(state %in% my_states,
         year == 2015:2023) |> 
  group_by(state, city_ref, year, area_queimada)

# PRODES --------------------------------------------
# Tratando base prodes
prodes_trat <- prodes |> 
  filter(categorie %in% 15:22) |> 
  rename(year = categorie,
         city_ref = muni) |> 
  mutate(
    year = 2000 + as.numeric(year)
    ) |>
  group_by(state, city_ref, year) |> 
  count() |> 
  group_by(year) |> 
  mutate(
    percent = n/sum(n)*100
  ) |> 
  rename(desmatamento = percent) # destamento proporcional ao número de ocorrências em relação ao total de registros daquele ano.

# MODIS --------------------------------------------
# Tratando base modis
modis_trat <- modis |>
  filter(media_fpar < 250, media_lai < 250)

# Climate TRACE ------------------------------------
# Tratando base Climate TRACE
climate_trace_trat <- climate_trace |>
  filter(year %in% 2015:2023,
         sigla_uf %in% my_states,
         gas == "co2e_100yr",
         sector_name == "agriculture") |> 
  select(city_ref, sigla_uf, emissions_quantity, year) |>
  rename(state = sigla_uf)
```

### ⛓️ Incorporando as bases faltantes

``` r
base_completa <- base_parcial |> 
  left_join(deter_trat,
  by = c("year", "state", "city_ref"),
  relationship = "many-to-many") |> 
  left_join(prodes_trat |> 
    select(state, city_ref, year, desmatamento),
  by = c("year", "state", "city_ref"),
  relationship = "many-to-many") |> 
  left_join(modis_trat |> select(
    year, state, city_ref, media_fpar, media_lai, media_ndvi, media_et),
  by = c("year", "state", "city_ref"),
  relationship = "many-to-many") |>
  left_join(climate_trace_trat,
  by = c("year", "state", "city_ref"),
  relationship = "many-to-many")

glimpse(base_completa)

# write_rds(base_completa, "data/base_completa.rds")
```

### Plotar mapa
