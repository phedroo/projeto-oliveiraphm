
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
longo dos anos de 2015 a 2023. **Serão adquiridos dados das
concentrações atmosféricas de CO<sub>2</sub> (X<sub>CO2</sub>) e
CH<sub>4</sub> (X<sub>CH4</sub>) a partir dos sensores orbitais GOSAT e
OCO-2. Em adição, dados das variáveis climáticas serão obtidos na
plataforma da Agência Espacial Americana (NASA). Para todos os setores
emissores de GEE, os dados serão obtidos a partir dos relatórios da
plataforma Climate TRACE, coalizão sem fins lucrativos capaz de rastrear
e fornecer informações sobre as emissões de GEE globalmente**. A
aquisição dos dados será sistematizada para redução das diferenças entre
as resoluções espaciais dos dados de sensoriamento remoto, com posterior
remoção da tendência mundial de X<sub>CO2</sub> e X<sub>CH4</sub>.
**Para exploração dos dados adquiridos, serão utilizadas técnicas
exploratórias multivariadas e análise geoestatística, implementadas em
linguagem R**. A interrelação entre as variáveis analisadas será
descrita por de reconhecimento de padrão, que incluíram análises de
agrupamento hierárquico e não-hierárquico, análise de componentes
principais associadas aos padrões de variabilidade espacial. Espera-se
que essa abordagem contribua para melhorar a compreensão da dinâmica dos
gases de efeito estufa na atmosfera e suas interações com variáveis
climáticas e de uso da terra no Brasil Central, auxiliando na formulação
de políticas públicas voltadas para a mitigação das emissões de GEE e,
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

#### 🛠️ Pré-processameto [script](https://arpanosso.github.io//projeto-oliveiraphm//02_preprocessamento.html)

#### ⛓️ Incorporação das bases

[script](adicionar%20link)

### 🛠 Preparação dos dados para análise.

``` r
library(tidyverse)
library(dplyr)
library(purrr) # criar funções
library(tibble)
library(corrplot)
library(vegan)
library(stringi)
library(patchwork) # facilitar visualização das figuras
source("R/my-function.R")
```

#### Definindo estados

``` r
my_states <- c("MS","MT","GO","DF")
```

## 💨 Entrada com todas as bases atualizadas com os setores `base_completa_setores.rds`

``` r
base_completa_setores <- read_rds('data/base_completa_setores.rds')
```

### Tratando outliers dos setores

Foram considerados outliers, pois foram observados valores absurdos
(acima de até 1300 Mton no ano) e não foram encontradas bases já
consolidadas (como o
[SEEG](https://energiaeambiente.org.br/oito-dos-dez-municipios-que-mais-emitem-gases-de-efeito-estufa-estao-na-amazonia-20220617))
com valores próximos a estes

*Realizar a média das emissões dos outliers com base nas observações da
nova base*

Foram observados padrões de emissões de acordo com os anos pares e
ímpares, sendo assim, essa média será passada para os anos pares e
ímpares, separadamente, de 2015 a 2020, com o objetivo de manter este
padrão

``` r
# Fazendo média 
base_completa_set_novas_medias <- base_completa_setores |>
  filter(year %in% 2021:2024,
         city_ref %in% c("sao jose do xingu", "sorriso", "taquaral de goias", "terenos", "pocone")) |> 
  # devemos caracterizar ano par e ímpar, para pareá-los:
  mutate(paridade = if_else(year %% 2 == 0, "par", "impar")) |>
  # agrupar por paridade para que as médias sejam feitas separadamente, por ano par e ímpar
  group_by(state, city_ref, paridade) |> 
  summarise(across(florestas_e_uso_da_terra:edificacoes, ~ mean(., na.rm = TRUE)), .groups = "drop")

# Atribuindo novos valores dos outliers de 2015 a 2020
base_completa_set <- base_completa_setores |>
  mutate(paridade = if_else(year %% 2 == 0, "par", "impar")) |>
  left_join(base_completa_set_novas_medias, by = c("state", "city_ref", "paridade"), suffix = c("", "_media")) |>
  mutate(across(
    florestas_e_uso_da_terra:edificacoes,
    ~ ifelse(year < 2021 & city_ref %in% c("sao jose do xingu", "sorriso", "taquaral de goias", "terenos", "pocone"), 
             get(paste0(cur_column(), "_media")),
             .)
  )) |>
  select(-ends_with("_media"), -paridade)

# Verificar outliers
# base_completa_setores |>
#   pivot_longer(
#     cols = florestas_e_uso_da_terra:edificacoes,
#     names_to = "setor",
#     values_to = "emission"
#   ) |>
#   group_by(year, state, city_ref) |>
#   summarise(
#     emission = sum(emission/1e6, na.rm = TRUE)
#   ) |>
#   arrange(desc(emission)) |>
#   head(11)


# Verificar se a média foi corretamente passada
# base_completa_set_corrigida |>
#   select(year:city_ref, agricultura:edificacoes) |>
#   filter(year %in% 2015:2024,
#          city_ref %in% c("sao jose do xingu", "sorriso", "taquaral de goias", "terenos", "pocone"))
```

## 💨 Entrada com todas as bases atualizadas com os subsetores `base_completa_subsetores.rds`

``` r
base_completa_subsetores <- read_rds('data/base_completa_subsetores.rds')
```

### Tratando outliers dos subsetores… (ainda não refeito para anos pares e ímpares)

Mesma lógica que à utilizada para os setores

``` r
# Fazendo média 
base_completa_subset_novas_medias <- base_completa_subsetores |>
  filter(year %in% 2021:2024,
         city_ref %in% c("sao jose do xingu", "sorriso", "taquaral de goias", "terenos", "pocone")) |>
  # devemos caracterizar ano par e ímpar, para pareá-los:
  mutate(paridade = if_else(year %% 2 == 0, "par", "impar")) |>
  # agrupar por paridade para que as médias sejam feitas separadamente, por ano par e ímpar
  group_by(state, city_ref, paridade) |>
  summarise(across(degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais, ~ mean(., na.rm = TRUE)), .groups = "drop")

# Atribuindo novos valores dos outliers de 2015 a 2020
  base_completa_subset <- base_completa_subsetores |>
    # devemos caracterizar ano par e ímpar, para pareá-los:
  mutate(paridade = if_else(year %% 2 == 0, "par", "impar")) |>
  # agrupar por paridade para que as médias sejam feitas separadamente, por ano par e ímpar
    left_join(base_completa_subset_novas_medias, by = c("state", "city_ref", "paridade"), suffix = c("", "_media")) |>
    mutate(across(
      degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais,
      ~ ifelse(year < 2021 & city_ref %in% c("sao jose do xingu", "sorriso", "taquaral de goias", "terenos", "pocone"), 
               get(paste0(cur_column(), "_media")), # "cur_column()", "_media" Pega o valor da coluna de média correspondente
               .)
  )) |>
  select(-ends_with("_media"))

  
  # Verificar outliers
# base_completa_subsetores |>
#   select(year:city_ref,degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais) |>
#   filter(city_ref %in% c("sao jose do xingu", "sorriso", "taquaral de goias", "terenos", "pocone")) |>
#   pivot_longer(
#     cols = degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais,
#     names_to = "subsetor",
#     values_to = "emission"
#   ) |>
#   group_by(year, state, city_ref) |>
#   summarise(
#     emission = sum(emission/1e6, na.rm = TRUE)
#   ) |>
#   arrange(desc(emission)) |>
#   head(11)
```

# 🔎 Análises

<!--
### 🧮 Estatística descritiva
&#10;
``` r
variavel <- "xch4" # opcional (mudar variavel)
&#10;# Criar vetor com as variáveis
variaveis <- base_completa_set |>
  select(-year, -state, -city_ref) |>
  names()
&#10;# names(base_completa_setores) # ver colunas
&#10;# Função de loop sobre as variáveis para facilitar processo
# for (variavel in variaveis) {
#   cat("Processando:", variavel, "\n")  # feedback
&#10;df <- base_completa_set |>
  filter(state != 'DF') |>
  group_by(year,state) |>
  summarise(
    N = sum(!is.na(.data[[variavel]]), na.rm = TRUE), # observações
    MIN = min(.data[[variavel]], na.rm = TRUE), # valor mínimo
    MEAN = mean(.data[[variavel]], na.rm = TRUE), # média
    MEDIAN = median(.data[[variavel]], na.rm = TRUE), # mediana
    MAX = max(.data[[variavel]], na.rm = TRUE), # valor máximo
    VARIANCIA  = var(.data[[variavel]], na.rm = TRUE),
    STD_DV = sd(.data[[variavel]], na.rm = TRUE), # desvio padrão
    CV = 100*STD_DV/MEAN, # coeficiete de variação
    SKW = agricolae::skewness(.data[[variavel]]), #
    KRT = agricolae::kurtosis(.data[[variavel]]), #
  )
&#10;# Salvar
writexl::write_xlsx(df, paste0("output/estat-descritiva-",variavel,"_.xlsx"))
&#10;}
&#10;```
&#10;### 📊 Histogramas
&#10;
``` r
variavel <- "xco2" # mudar
&#10;# base resumida
base_completa_setores |>
  ggplot(aes(x=.data[[variavel]])) +
  geom_histogram(color="black",fill="gray",
                 bins = 30) +
  facet_wrap(~year, scales = "free") +
  theme_bw()
```
&#10;
``` r
base_completa |>
  mutate(
  fct_year = fct_rev(as.factor(year)),
  ) |>
  ggplot(aes(y=fct_year)) +
  ggridges::geom_density_ridges(rel_min_height = 0.03,
                      aes(x=.data[[variavel]], fill=state),
                      alpha = .6, color = "black"
  ) +
  scale_fill_viridis_d() +
  ggridges::theme_ridges() +
  theme(
    legend.position = "top"
  ) +
  labs(fill="")
```
-->

## Análise de tendência dos dados de XCO2 e XCH4

Caraterizando a tendência para resolução temporal em anos.

``` r
# XCO2
base_completa_set |> 
  mutate(
    state = ifelse(state=="DF","GO",state),0) |> 
  # sample_n(10000) |> 
  ggplot(aes(x=year, y=xco2)) +
  geom_point() +
  geom_point(shape=21,color="black",fill="gray") +
  geom_smooth(method = "lm") +
  ggpubr::stat_regline_equation(ggplot2::aes(
  label =  paste(..eq.label.., ..rr.label.., sep = "*plain(\",\")~~"))) +
  theme_bw()

# XCH4
base_completa_set |> 
  mutate(
    state = ifelse(state=="DF","GO",state),0) |> 
  # sample_n(10000) |> 
  ggplot(aes(x=year, y=xch4)) +
  geom_point() +
  geom_point(shape=21,color="black",fill="gray") +
  geom_smooth(method = "lm") +
  ggpubr::stat_regline_equation(ggplot2::aes(
  label =  paste(..eq.label.., ..rr.label.., sep = "*plain(\",\")~~"))) +
  theme_bw()
```

Análise de regressão linear para posterior retirada de tendência.

``` r
# Criar year_adj (1, 2, 3...)
base_completa_set_tend <- base_completa_set |>
  mutate(year_adj = year - min(year, na.rm = TRUE))

# Modelo XCO2
mod_trend_xco2 <- lm(
  xco2 ~ year_adj + city_ref,
  data = base_completa_set_tend |> drop_na(xco2, city_ref)
)
mod_trend_xco2

# Modelo XCH4
mod_trend_xch4 <- lm(
  xch4 ~ year_adj + city_ref,
  data = base_completa_set_tend |> drop_na(xch4, city_ref)
)
mod_trend_xch4

# 2) Previsão da tendência usando os modelos

base_completa_set_tend <- base_completa_set |>
  mutate(
    delta_co2 = predict(mod_trend_xco2, newdata = base_completa_set_tend),
    delta_ch4 = predict(mod_trend_xch4, newdata = base_completa_set_tend)
  )
```

#### Retirando a tendência

``` r
# Código PIBIC 

# base_completa_set |>
#   group_by(variable) |>
#   mutate(
#     value_est = ifelse(variable=="xco2",
#                        a_co2+b_co2*(year-min(year)),
#                        ifelse(variable=="xch4",
#                               a_ch4+b_ch4*(year-min(year)),
#                               value)),
#     delta = ifelse(variable=="sif",value,value_est-value),
#     value_detrend = ifelse(variable =="xco2", (a_co2-delta)-(mean(value)-a_co2),
#                        ifelse(variable =="xch4",
#                               (a_ch4-delta)-(mean(value)-a_ch4),value)),
#     value = value_detrend
#   ) |> ungroup() |>
#   select(-value_est,-delta,-value_detrend)
# 
# kgr_maps_detrend |> 
#   filter(variable == "xch4")


# Código PIBIC adaptado à nova base
  # xco2 e xch4 em colunas separadas

# 3) Remoção da tendência mantendo média por cidade

base_completa_set_tend <- base_completa_set_tend |>
  group_by(city_ref) |>
  mutate(
    xco2_detrend = (xco2 - delta_co2) + mean(xco2, na.rm = TRUE),
    xch4_detrend = (xch4 - delta_ch4) + mean(xch4, na.rm = TRUE)
  ) |>
  ungroup()

base_completa_set_tend <- base_completa_set_tend |> 
  mutate(
    xco2 = xco2_detrend,
    xch4 = xch4_detrend
  ) |> 
  select(-(delta_co2:xch4_detrend))
```

### 🔄 Atualização da Base - Cáculo da Anomalia

``` r
base_completa_set <- base_completa_set_tend |> 
  group_by(year) |> 
  mutate(anomalia_xco2 = xco2 - median(xco2,na.rm=TRUE),
         anomalia_xch4 = xch4 - median(xch4, na.rm=TRUE)) |> 
  dplyr::ungroup() |> 
  relocate(year:city_ref, xco2, anomalia_xco2, xch4, anomalia_xch4, sif_757, temperatura, umidade, precipitacao, pressao, radiacao, vento,media_fpar:media_ndvi, desmatamento,area_queimada) |> 
    select(-media_et) |> 
  rename(queimada = area_queimada,
         fpar = media_fpar,
         lai = media_lai,
         evi = media_evi,
         ndvi = media_ndvi)
```

A base de dados do GOSAT disponibiliza informações de XCH₄ até o ano de
2021. Para possibilitar a análise de regressão, realizou-se a predição
dos valores para 2022 e 2023 por meio do método de regressão linear
simples, utilizando os dados observados no período de 2015 a 2021 como
base de treinamento.

``` r
city_ref <- base_completa_set$city_ref |> unique()

for(i in seq_along(city_ref)){
  da <- base_completa_set |>
    filter(city_ref == city_ref[i]) |>
    filter(year >= 2014 & year <= 2021)
  if(nrow(da) >= 2){
  mod <- lm(xch4 ~ year,data=da)
  a <- mod$coefficients[[1]]
  b <- mod$coefficients[[2]]

  base_completa_set <- base_completa_set |>
    mutate(
      xch4 = ifelse(city_ref == city_ref[i],
                    ifelse(is.na(xch4),
                           a+year*b,xch4),xch4)
    )}
}
base_completa_set <- base_completa_set |> 
  group_by(year, state) |> 
  mutate(
    xch4 = ifelse(is.na(xch4),median(xch4,na.rm = TRUE),xch4)
  ) |> 
  group_by(year) |> 
  mutate(anomalia_xch4 = xch4 - median(xch4, na.rm=TRUE)) |> 
  ungroup()

base_completa_set$xch4 |> is.na() |>  sum()
```

### 🔎 Mapas de XCO2 e XCH4 + respectivas anomalias

``` r
for( i in 2015:2023){
  df_aux <- municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      base_completa_set |> 
        filter(year == i) |> 
        rename(name_muni = city_ref, abbrev_state = state),
      by = c("abbrev_state","name_muni")
    ) 

  plot_xco2 <- df_aux |> 
    ggplot() +
    geom_sf(aes(fill=xco2), color="transparent", size=.05, show.legend = TRUE) +
    geom_sf(data = municipality |> filter(abbrev_state %in% my_states),
            fill="transparent", size=.3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = "XCO2 (ppm)",
         x = "Longitude",
         y = "Latitude") +
    scale_fill_viridis_c()

  plot_anom_xco2 <- df_aux |> 
    ggplot() +
    geom_sf(aes(fill=anomalia_xco2), color="transparent", size=.05, show.legend = TRUE) +
    geom_sf(data = municipality |> filter(abbrev_state %in% my_states),
            fill="transparent", size=.3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = "Anomalia-XCO2",
         x = "Longitude",
         y = "Latitude") +
    scale_fill_viridis_c(option = "A")

  plot_xch4 <- df_aux |> 
    ggplot() +
    geom_sf(aes(fill=xch4), color="transparent", size=.05, show.legend = TRUE) +
    geom_sf(data = municipality |> filter(abbrev_state %in% my_states),
            fill="transparent", size=.3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = "XCH4 (ppb)",
         x = "Longitude",
         y = "Latitude") +
    scale_fill_viridis_c(option = "E")

  plot_anom_xch4 <- df_aux |> 
    ggplot() +
    geom_sf(aes(fill=anomalia_xch4), color="transparent", size=.05, show.legend = TRUE) +
    geom_sf(data = municipality |> filter(abbrev_state %in% my_states),
            fill="transparent", size=.3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = "Anomalia-XCH4",
         x = "Longitude",
         y = "Latitude") +
    scale_fill_viridis_c(option = "B")
  
  print((plot_xco2 | plot_anom_xco2)/ #patchwork
    (plot_xch4 | plot_anom_xch4) + plot_annotation(title = i))

   # PARA SALVAR ----------------------------------------------
  # painel_gee_anom <- (plot_xco2 | plot_anom_xco2) /
  #           (plot_xch4 | plot_anom_xch4) +
  #           plot_annotation(title = .x)

  # if (!dir.exists("results")) dir.create("results")

  # ggsave(
  #   filename = paste0("results/mapas_", .x, ".png"),
  #   plot = painel_gee_anom,
  #   width = 16,
  #   height = 12,
  #   dpi = 300
  # )

  # painel_gee_anom
}


# (plot_xco2 | plot_anom_xco2)/ #patchwork
#   (plot_xch4 | plot_anom_xch4) + plot_annotation(title = i)
```

### 🔎 Análise de correlação - entre setores

``` r
# mc_set <- cor(base_completa_set |>
#             select(florestas_e_uso_da_terra:edificacoes, -operacoes_de_combustiveis_fosseis), use = "pairwise.complete.obs")
# corrplot(mc_set,method = "color",
#          outline = TRUE,
#          type = "upper",
#          addgrid.col = "darkgray",cl.pos = "r", tl.col = "black",
#          tl.cex = .7, cl.cex = 1,  bg="azure2",
#          # diag = FALSE,
#          # addCoef.col = "black",
#          cl.ratio = 0.2,
#          cl.length = 5,
#          number.cex = 0.8
# ) 
```

### 🔎 Análise de correlação - total

``` r
mc <- cor(base_completa_set |>
                select(anomalia_xco2:queimada, -xch4, -evi,-ndvi), use = "pairwise.complete.obs") # "complete.obs" descarta totalemnte linha com qualquer NA
corrplot(mc,method = "color",
         outline = TRUE,
         type = "upper",
         addgrid.col = "darkgray",cl.pos = "r", tl.col = "black",
         tl.cex = .8, cl.cex = 1,  bg="azure2",
         # diag = FALSE,
         # addCoef.col = "black",
         cl.ratio = 0.2,
         cl.length = 5,
         number.cex = 0.8
) 
```

### 🔎 Análise de correlação - ANO

``` r
ngrp <- rep(3,9) # c(3,3,3,4,4,5,3,4, -) 
for( i in 2015:2023){
  # Análise de correlação
  base_aux <- base_completa_set |>
    filter(year == i) |> 
    select(xco2:desmatamento, -evi, -ndvi,-xco2,-xch4, -temperatura,-sif_757) 
  
  municipios <-base_completa_set |>
    filter(year == i) |> 
    pull(city_ref)
  
  mc <- cor(base_aux,use = "pairwise.complete.obs")
  fc <- !is.na(mc[1,])
  fl <- !is.na(mc[,1])
  mc <- mc[fc,fl]
  mc <- mc[1:5,-(1:5)]
  corrplot(mc,method = "color",
           outline = TRUE,
           addgrid.col = "darkgray",cl.pos = "r", tl.col = "black",
           tl.cex = 1, cl.cex = 1,  bg="azure2",
           # diag = FALSE,
           addCoef.col = "black",
           cl.ratio = 0.2,
           cl.length = 5,
           number.cex = 0.8) 
  
  # Análise de agrupamento
  da_pad <- decostand(base_aux[,fc] |> 
                        mutate(across(everything(), ~replace_na(., 0))),  # invés de passar NA = 0, não podemos passar a mediana do estado?
                      method = "standardize",
                      na.rm=TRUE)
  da_pad_euc <- vegdist(da_pad,"euclidean") 
  da_pad_euc_ward<-hclust(da_pad_euc, method="ward.D")
  da_pad_euc_ward$labels <- municipios
  grupo<-cutree(da_pad_euc_ward,ngrp[i-2014]) #### numero de agrupamentos
  d <- da_pad_euc_ward$height
  d_corte <- d[which(d |> diff() == max(diff(d)))]
  plot(da_pad_euc_ward, 
       ylab="Distância Euclidiana",
       xlab="Acessos", hang=-1,
       col="blue", las=1,
       cex=.6,lwd=1.5);box();abline(h=d_corte*1.15)
  
  # Mapaeamento dos Grupos
  plot_map_group <- municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
        name_muni = names(grupo),
        grupo = as_factor(grupo)
      ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>      
    ggplot() +
    geom_sf(aes(fill=grupo), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'Agrupamento',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_d()
  print(plot_map_group)
  
  pca <-  prcomp(da_pad,scale.=TRUE)
  # Autovalores
  eig<-pca$sdev^2
  print("==== Autovalores ====")
  print(round(eig,3))
  print("==== % da variância explicada ====")
  ve<-eig/sum(eig)
  print(round(ve,4))
  print("==== % da variância explicada acumulada ====")
  print(round(cumsum(ve),4)*100)
  print("==== Poder Discriminante ====")
  mcor<-cor(da_pad,pca$x)
  corrplot(mcor)
  
  pc1V<-cor(da_pad,pca$x)[,1]/sd(cor(da_pad,pca$x)[,1])
  pc2V<-cor(da_pad,pca$x)[,2]/sd(cor(da_pad,pca$x)[,2])
  pc3V<-cor(da_pad,pca$x)[,3]/sd(cor(da_pad,pca$x)[,3])
  pc1c<-pca$x[,1]/sd(pca$x[,1])
  pc2c<-pca$x[,2]/sd(pca$x[,2])
  pc3c<-pca$x[,3]/sd(pca$x[,3])
  nv<-ncol(mcor) # número de variáveis utilizadas na análise
      
  # gráfico biplot
  bip<-data.frame(pc1c,pc2c,pc3c,grupo)
  texto <- data.frame(
    x = pc1V,
    y = pc2V,
    z = pc3V,
    label = rownames(mcor)
  )
  for(k in 1:ngrp[i-2014]){
    cat(paste0("[Grupo ",k,"]:\n"), paste(municipios[grupo==k],collapse = "; "))
    cat("\n\n")
  }
  
  bi_plot <- bip |> 
    ggplot(aes(x=pc1c,y=pc2c,colour = as_factor(grupo))) +
    geom_point(size = 3) +
    theme_minimal() +
    # scale_shape_manual(values=16:18)+
    # scale_color_manual(values=c("#009E73", "#D55E00")) + #"#999999",
    # annotate(geom="text", x=pc1c, y=pc2c, label=cultivar,
    #             color="black",size=.25)+
    geom_vline(aes(xintercept=0),
               color="black", size=1)+
    geom_hline(aes(yintercept=0),
               color="black", size=1)+
    annotate(geom="segment",
             x=rep(0,nv),
             xend=texto$x,
             y=rep(0,nv),
             yend=texto$y,color="black",lwd=.5)+
    geom_label(data=texto,aes(x=x,y=y,label=label),
               color="black",angle=0,fontface="bold",size=3,fill="white")+
    labs(x=paste("CP1 (",round(100*ve[1],2),"%)",sep=""),
         y=paste("CP2 (",round(100*ve[2],2),"%)",sep=""),
         color="",shape="")+
    theme(legend.position = "top")+
    scale_color_viridis_d() #+
    # xlim(min(pc1c)*1.5,max(pc1c)*1.5) 
  print(bi_plot)
  
  print("==== Tabela da correlação dos atributos com cada PC ====")
      ck<-sum(pca$sdev^2>=0.98)
      tabelapca<-vector()
      for( l in 1:ck) tabelapca<-cbind(tabelapca,mcor[,l])
      colnames(tabelapca)<-paste(rep(c("PC"),ck),1:ck,sep="")
      pcat<-round(tabelapca,3)
      tabelapca<-tabelapca[order(abs(tabelapca[,1])),]
      print(tabelapca)
      
corr_maps <- plot_map_group + bi_plot + plot_layout(ncol = 2) +
  plot_annotation(title = i)

# Salvar mapas das correlações e biplot por ano
# ggsave(
#   filename = paste0("results/map_biplot_", i, ".png"),
#   plot = corr_maps,
#   width = 14, height = 6, dpi = 300
# )


# Salvar Tabela da correlação dos atributos com cada Componente Principal (PC)
# write.csv(
#   tabelapca,
#   file = paste0("results/tabelapca", i, ".csv"),
#   row.names = TRUE
# )

}
```

<!--
## 🗺️ Mapa de EMISSÃO TOTAL - setores
&#10;
``` r
# Remover outliers (trecho comentado pois os outliers agora foram tratados)
# Criando vetor com os municipios que são outliers, nos anos em que são outliers
  # observação: é possível fazer um replace dos valores para estes outliers com a média dos anos seguintes (2021 a 2025)
&#10;# remov_out <- base_completa_set |> filter(
#   state %in% my_states) |>
#   # select(-florestas_e_uso_da_terra) |> 
#   pivot_longer(
#     cols = florestas_e_uso_da_terra:edificacoes,
#     names_to = "setor",
#     values_to = "emission"
#   ) |> 
#   group_by(year, state, city_ref) |> 
#   summarise(
#     emission = sum(emission/1e6, na.rm = TRUE)
#   ) |> 
#   arrange(desc(emission)) |> 
#   head(11) |> 
#   pull(city_ref, year)
&#10;# Criando vetor para extrair os municipios de todos os tipos de emissões, possibilitando a padronização dos nomes para evitar outliers aparecendo
municipios <- base_completa_set |>
  mutate(
    city_ref = stri_trans_general(tolower(city_ref), "Latin-ASCII"),
    city_ref = trimws(city_ref)) |>
  pull(city_ref) |> unique()
&#10;padrao_municipios <- paste0(municipios, collapse = "|") 
&#10;# Gerando mapa
map(2015:2023,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
      base_completa_set |> 
        #remover edificacoes por estar presente só na nova base
        select(-edificacoes) |>
        mutate(florestas_e_uso_da_terra = ifelse(florestas_e_uso_da_terra>=0, florestas_e_uso_da_terra,0)) |> 
        filter(year == .x) |> 
        pivot_longer(
          cols = florestas_e_uso_da_terra:extracao_mineral, # não considera edificacoes porque só tem na base 2021 a 2025, e devido remoções, o de florestas 
          names_to = "setor",
          values_to = "emission"
        ) |> 
        group_by(year, state, city_ref) |> 
        summarise(
          emission = sum(emission, na.rm = TRUE)
        ) |> 
        select(state:emission) |> 
        rename(name_muni = city_ref)
       ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>
    ggplot() +
    geom_sf(aes(fill=emission/1e6), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'Agrupamento',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_c()})
```
&#10;-->

#### 🗺️ Mapa de EMISSÃO TOTAL - setores - Criando classe de emissão

``` r
map(2015:2023,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
        base_completa_set |> 
          #remover edificacoes por estar presente só na nova base
          select(-edificacoes) |>
          mutate(florestas_e_uso_da_terra = ifelse(florestas_e_uso_da_terra>0, florestas_e_uso_da_terra,0)) |> 
          filter(year == .x)|> 
          pivot_longer(
            cols = florestas_e_uso_da_terra:extracao_mineral, #remove edificacoes porque só tem na base 2021 a 2023 
            names_to = "setor",
            values_to = "emission"
          ) |> 
          group_by(year, state, city_ref) |> 
          summarise(
            emission = sum(emission, na.rm = TRUE)
          ) |> 
          select(state:emission) |> 
          rename(name_muni = city_ref)
      ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>  
    mutate(
      classe_emissao = case_when(
        emission <1e6 ~ ' <  1 Mton',
        emission <2e6 ~ ' <  2 Mton',
        emission >=2e6 ~ '>= 2 Mton'
      )
    ) |> 
    ggplot() +
    geom_sf(aes(fill=classe_emissao), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    labs(fill = 'Classe de emissão',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_d()})
```

<!--
#### 🗺️ Mapa de EMISSÃO TOTAL - escolher setor
&#10;
``` r
setor = "agricultura" #mudar
# setor = c("agricultura", "florestas_e_uso_da_terra") #escolher mais de 1 setor...
&#10;# Gerando mapa
map(2015:2023,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
      base_completa_set |> 
        filter(year == .x) |> 
        pivot_longer(
          cols = setor, 
          names_to = "setor",
          values_to = "emission"
        ) |> 
        group_by(year, state, city_ref) |> 
        summarise(
          emission = sum(emission, na.rm = TRUE)
        ) |> 
        select(state:emission) |> 
        rename(name_muni = city_ref)
       ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>  
    mutate(
       classe_emissao = case_when(
       emission <1e6 ~ ' <  1 Mton',
       emission <2e6 ~ ' <  2 Mton',
       emission >=2e6 ~ '>= 2 Mton'
     )
    ) |> 
    ggplot() +
    geom_sf(aes(fill=classe_emissao), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    labs(fill = 'Agrupamento',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_d()})
```
&#10;
&#10;## 🗺️ Mapa de EMISSÃO TOTAL - subsetores
&#10;Aparentemente, muitos subsetores (não consegui ver todos que são) estão com suas metodologias alteradas, e isso esta gerando grande divergência entre os mapas
&#10;
``` r
map(2015:2023,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
      base_completa_subset |> 
        mutate(
          # Valores não positivos para essas colunas de remoção recebem 0
            # Isso pois alguns subsetores contém remoções e emissões juntas
    uso_liquido_de_terras_florestais = ifelse(uso_liquido_de_terras_florestais > 0, uso_liquido_de_terras_florestais, 0),
    uso_liquido_de_areas_arbustivas_e_gramineas = ifelse(uso_liquido_de_areas_arbustivas_e_gramineas > 0, uso_liquido_de_areas_arbustivas_e_gramineas, 0),
    uso_liquido_de_areas_umidas = ifelse(uso_liquido_de_areas_umidas > 0, uso_liquido_de_areas_umidas, 0)
  ) |>
    # Removendo subsetores que contém remoções
        # select(-remocoes_de_carbono_sequestro,
        #        -uso_liquido_de_terras_florestais, -uso_liquido_de_areas_arbustivas_e_gramineas, -uso_liquido_de_areas_umidas) |>
        filter(year == .x) |> 
        pivot_longer(
          cols = degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais,
          names_to = "subsetor",
          values_to = "emission"
        ) |> 
        group_by(year, state, city_ref) |> 
        summarise(
          emission = sum(emission, na.rm = TRUE)
        ) |> 
        select(state:emission) |> 
        rename(name_muni = city_ref)
       ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>      
    ggplot() +
    geom_sf(aes(fill=emission/1e6), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'Agrupamento',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_c()})
```
&#10;-->

#### 🗺️ Mapa de EMISSÃO TOTAL - subsetores - Criando classe de emissão

*Leves diferenças do mapa de classes da emissão total dos setores*

``` r
map(2015:2023,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
      base_completa_subset |> 
        mutate(
          # Valores não positivos para essas colunas de remoção recebem 0
            # Isso pois alguns subsetores contém remoções e emissões juntas
    uso_liquido_de_terras_florestais = ifelse(uso_liquido_de_terras_florestais > 0, uso_liquido_de_terras_florestais, 0),
    uso_liquido_de_areas_arbustivas_e_gramineas = ifelse(uso_liquido_de_areas_arbustivas_e_gramineas > 0, uso_liquido_de_areas_arbustivas_e_gramineas, 0),
    uso_liquido_de_areas_umidas = ifelse(uso_liquido_de_areas_umidas > 0, uso_liquido_de_areas_umidas, 0)
  ) |>
    # Removendo subsetores que contém remoções
        # select(-remocoes_de_carbono_sequestro,
        #        -uso_liquido_de_terras_florestais, -uso_liquido_de_areas_arbustivas_e_gramineas, -uso_liquido_de_areas_umidas) |>
        filter(year == .x) |> 
        pivot_longer(
          cols = degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais,
          names_to = "setor",
          values_to = "emission"
        ) |> 
        group_by(year, state, city_ref) |> 
        summarise(
          emission = sum(emission, na.rm = TRUE)
        ) |> 
        select(state:emission) |> 
        rename(name_muni = city_ref)
       ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>  
    mutate(
       classe_emissao = case_when(
       emission <1e6 ~ ' <  1 Mton',
       emission <2e6 ~ ' <  2 Mton',
       emission >=2e6 ~ '>= 2 Mton'
     )
    ) |> 
    ggplot() +
    geom_sf(aes(fill=classe_emissao), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    labs(fill = 'Classe de emissão',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_d()})
```

<!--
&#10;#### 🗺️ Mapa de EMISSÃO TOTAL - escolher subsetor
&#10;
``` r
subsetor = "queimadas_em_areas_agricolas" #mudar
#detalhe: alguns subsetores como "degradacao_em_terras_florestais" só estão em uma das bases (nesse caso, na antiga)
&#10;# Escolher mais de 1 subsetor...
# subsetor = c("degradacao_em_terras_florestais", "queimadas_em_areas_agricolas", "fermentacao_enterica_gado_a_pasto", "desmatamento_em_terras_florestais", "queimadas_em_terras_florestais", "esterco_deixado_no_pasto_gado", "queimadas_em_areas_arbustivas", "queimadas_em_areas_umidas")
#detalhe: não passará na legenda do mapa
&#10;
# Gerando mapa
map(2015:2023,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
      base_completa_subset |> 
        filter(year == .x) |> 
        pivot_longer(
          cols = subsetor, 
          names_to = "subsetor",
          values_to = "emission"
        ) |> 
        group_by(year, state, city_ref) |> 
        summarise(
          emission = sum(emission, na.rm = TRUE)
        ) |> 
        select(state:emission) |> 
        rename(name_muni = city_ref)
       ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>
    mutate(
      classes_de_emissao = case_when(
        emission < 0.1e6 ~ "<0.1",
        emission < 0.4e6 ~ "<0.4",
        emission < 0.7e6 ~ "<0.7", 
        emission < 1e6 ~ "<1.0",
        emission >= 1e6 ~ ">=1.0"
      )
    ) |> 
    ggplot() +
    geom_sf(aes(fill=ifelse(emission > 2e6, emission/1e6, classes_de_emissao)), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    labs(fill = paste(subsetor, "(Mton)"),
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_d()})
```
&#10;
## 🗺️ SETOR/SUBSETOR DE MAIOR EMISSÃO DA CIDADE
&#10;
``` r
# Unindo as bases climate TRACE
  # Feito caso queira visualizar os setores e subsetores de maior emissão em um mesmo mapa
# base_completa_ct <- base_completa_set |> 
#   select(year:city_ref, florestas_e_uso_da_terra:edificacoes) |> 
#   full_join(base_completa_subset |> 
#               select(year:city_ref, degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais),
#             by = c("year", "city_ref", "state"))
```
-->

## 🗺️ SETOR DE MAIOR EMISSÃO

``` r
# Padronizar cores, criando vetor
padr_cor <- base_completa_set |> 
  select(florestas_e_uso_da_terra:edificacoes) |> 
  names()

# Paleta fixa 
cores_fixas <- viridis::viridis(length(padr_cor), option = "D")

map(2015:2024,~{municipality |> 
  mutate(
    name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
    name_muni = trimws(name_muni)
  )  |> 
  filter(abbrev_state %in% my_states) |> 
  left_join(
    base_completa_set |> 
      select(year:city_ref, florestas_e_uso_da_terra:edificacoes) |> 
      mutate(florestas_e_uso_da_terra = ifelse(florestas_e_uso_da_terra>0,florestas_e_uso_da_terra,0)) |> 
      filter(year == .x) |> 
      pivot_longer(
        cols = florestas_e_uso_da_terra:edificacoes,
        names_to = "setores",
        values_to = "emission"
      ) |> 
      group_by(year, city_ref) |> 
      mutate(
        max_emission = max(emission,na.rm = TRUE),
        s_max_emission = ifelse(emission == max_emission,setores,NA)
      ) |> 
      filter(!is.na(s_max_emission)) |> 
      rename(name_muni = city_ref),
    by = "name_muni") |> 
  drop_na() |> 
  ggplot() +
    geom_sf(aes(fill=s_max_emission), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw()+
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'Setor de Maior Emissão',
         x = 'Longitude',
         y = 'Latitude') +
      scale_fill_manual(
        values = setNames(cores_fixas, padr_cor),
      )
  
  })
```

## 🗺️ SUBSETOR DE MAIOR EMISSÃO

``` r
# Padronizar cores, criando vetor
padr_cor <- base_completa_subset |> 
  select(degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais) |> 
  names()

# Paleta fixa 
cores_fixas <- viridis::viridis(length(padr_cor), option = "D")

map(2015:2024,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      base_completa_subset |> 
        select(year:city_ref, degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais, -remocoes_de_carbono_sequestro) |>
        mutate(
          uso_liquido_de_terras_florestais = ifelse(uso_liquido_de_terras_florestais > 0, uso_liquido_de_terras_florestais, 0),
          uso_liquido_de_areas_arbustivas_e_gramineas = ifelse(uso_liquido_de_areas_arbustivas_e_gramineas > 0, uso_liquido_de_areas_arbustivas_e_gramineas, 0),
          uso_liquido_de_areas_umidas = ifelse(uso_liquido_de_areas_umidas > 0, uso_liquido_de_areas_umidas, 0)
        ) |> 
        filter(year == .x) |> 
        pivot_longer(
          cols = degradacao_em_terras_florestais:tratamento_e_descarte_de_efluentes_industriais,
          names_to = "subsetores",
          values_to = "emission"
        ) |> 
        group_by(year, city_ref) |> 
        mutate(
          max_emission = max(emission,na.rm = TRUE),
          s_max_emission = ifelse(emission == max_emission,subsetores,NA)
        ) |> 
        filter(!is.na(s_max_emission)) |> 
        rename(name_muni = city_ref),
      by = "name_muni") |> 
    drop_na() |> 
    ggplot() +
    geom_sf(aes(fill=s_max_emission), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw()+
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'Subsetor de Maior Emissão',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_manual(
      values = setNames(cores_fixas, padr_cor),
    )
  
})
```

## 🗺 Mapa de REMOÇÃO

Vale ressaltar que a nova metodologia do climate TRACE subdivide o
subsetor de *remocoes_de_carbono_sequestro* (as remoções) em 3 novos
subsetores:

*uso_liquido_de_terras_florestais*
*uso_liquido_de_areas_arbustivas_e_gramineas*
*uso_liquido_de_areas_umidas*

``` r
# Primeiramente, é necessário passar os valores da coluna "remocoes_de_carbono_sequestro" da nova base do climate TRACE para negativos, para tornar a análise visual entre os mapas iguais:
    # Tornando todos os valores absolutos positivos
      # base_completa_subset |>
      #   mutate(remocoes_de_carbono_sequestro = -abs(remocoes_de_carbono_sequestro)) |>  select(year,city_ref,remocoes_de_carbono_sequestro,uso_liquido_de_terras_florestais,uso_liquido_de_areas_arbustivas_e_gramineas,uso_liquido_de_areas_umidas)

map(2015:2024,~{municipality |> 
    mutate(
      name_muni = stri_trans_general(tolower(name_muni), "Latin-ASCII"),
      name_muni = trimws(name_muni)
    )  |> 
    filter(abbrev_state %in% my_states) |> 
    left_join(
      data.frame(
        base_completa_subset |> 
          mutate(remocoes_de_carbono_sequestro = -abs(remocoes_de_carbono_sequestro)) |> #valores absolutos negativos
          filter(year == .x,
                 remocoes_de_carbono_sequestro <=0,
                 uso_liquido_de_terras_florestais<=0,
                 uso_liquido_de_areas_arbustivas_e_gramineas<=0,
                 uso_liquido_de_areas_umidas<=0) |> 
          pivot_longer(
            cols = c(remocoes_de_carbono_sequestro,uso_liquido_de_terras_florestais,uso_liquido_de_areas_arbustivas_e_gramineas,uso_liquido_de_areas_umidas),
            names_to = "subsector",
            values_to = "emission"
          ) |> 
          group_by(year, state, city_ref) |> 
          summarise(
            emission = sum(emission, na.rm = TRUE)
          ) |> 
          select(state:emission) |> 
          rename(name_muni = city_ref)
      ),by = "name_muni", relationship = "many-to-many"
    ) |> drop_na() |>      
    ggplot() +
    geom_sf(aes(fill=emission/1e6), color="transparent",
            size=.05, show.legend = TRUE)  +
    geom_sf(data=municipality |> filter(abbrev_state %in% my_states), fill="transparent", size=3, show.legend = FALSE) +
    theme_bw() +
    theme(
      axis.text.x = element_text(size = rel(.9), color = "black"),
      axis.title.x = element_text(size = rel(1.1), color = "black"),
      axis.text.y = element_text(size = rel(.9), color = "black"),
      axis.title.y = element_text(size = rel(1.1), color = "black"),
      legend.text = element_text(size = rel(1), color = "black"),
      legend.title = element_text(face = 'bold', size = rel(1.2))
    ) +
    labs(fill = 'Agrupamento',
         x = 'Longitude',
         y = 'Latitude') +
    scale_fill_viridis_c()})
```

## 📊 VISUALIZANDO MAIORES EMISSORES PARA TODOS OS SETORES e SUBSETORES

Visualização em acumulado de CO2 equivalente no período de 2021 a 2024
(somente considerada a base climate TRACE nova, devido sua metodologia
consolidada, de modo que se evite os outliers entre outros problemas da
base antiga)

``` r
#### SETORES
top_set <- base_completa_setores |>
  pivot_longer(
    cols = florestas_e_uso_da_terra:edificacoes,
    names_to = "setor",
    values_to = "emissao"
  ) |> 
  mutate(emissao = ifelse(emissao>=0, emissao,0),
         setor = stri_trans_general(setor, "title"), # passar para maiuscula
         setor = str_replace_all(setor, "_", " ")) |> 
  filter(
    year%in%2021:2024,                   #%in% 2015:2023
  ) |>
  select(year:city_ref, setor, emissao) |> 
  group_by(city_ref, state, setor) |>
  summarise(
    emission = sum(emissao, na.rm = T)
  ) |>
  group_by(city_ref,state) |>
  mutate(
    emissao_total = sum(emission, na.rm = T)
  ) |>
  ungroup() |>
  group_by(state) |>
  mutate(
    state = ifelse(state == "DF", "GO", state)) |>
  mutate(
    city_ref = city_ref |> fct_reorder(emissao_total) |>
      fct_lump(n = 3, w = emissao_total)) |>
  filter(city_ref != "Other") |> 
  filter(city_ref != 'other') |>  
  mutate(
      setor = case_when(
        setor == "Operacoes De Combustiveis Fosseis" ~ "CF",
        setor == "Extracao Mineral" ~ "EM.",
        setor == 'Florestas E Uso Da Terra' ~ 'FUT',
        setor == 'Edificacoes' ~ 'Edificações',
        setor == 'Residuos' ~ 'Resíduos',
        TRUE ~ setor # qualquer outro valor, manter valor original (setor)
      )) |>
  ggplot(aes(emission/1e6, #passar de ton para Mton
             city_ref,
             fill = setor)) +
  geom_col(col="black", lwd = 0.1) +
  xlab(bquote(Emissão~CO[2]~e~(Mton))) +
  labs(#x = 'Emission (Mton)',
    y = 'Cidade',
    fill = 'Setor') +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(1)),
    # axis.title.x = element_text(size = rel(2)),
    axis.text.y = element_text(size = rel(1.3)),
    # axis.title.y = element_text(size = rel(2)),
    legend.text = element_text(size = rel(.9)),
    #legend.title = element_text(size = rel(1.7)),
    title = element_text(face = 'bold'),
    legend.position = 'top',
    legend.background = element_rect(fill = "transparent", color = "black")) +
  scale_fill_viridis_d(option ='plasma') +
  facet_wrap(~state,scales = "free",ncol = 1) +
  annotate("text",
           x=2,
           y=1,
           label = ".",
           size=0.1)

# -------------------------------------------------------------
#### SUBSETORES
top_subset <- base_completa_subsetores |>
  pivot_longer(
    cols = degradacao_em_terras_florestais:craqueamento_a_vapor_petroquimico,
    names_to = "subsetor",
    values_to = "emissao"
  ) |> 
  filter(
    emissao > 0,
    year%in%2021:2024,                   #%in% 2015:2022
  ) |>
  select(year:city_ref, subsetor, emissao) |> 
  group_by(city_ref, state, subsetor) |>
  summarise(
    emission = sum(emissao, na.rm = T)
  ) |>
  group_by(city_ref,state) |>
  ungroup() |>
  group_by(state) |>
  mutate(
    state = ifelse(state == "DF", "GO", state),
    city_ref = city_ref |> fct_reorder(emission) |> 
      fct_lump(n = 3, w = emission)) |>
  mutate(
  subsetor = fct_lump_n(subsetor, n = 5, w = emission) # despoluir legenda, selecionando principais subsetores
) |> 
  filter(subsetor != "Other") |> 
  filter(city_ref != "Other") |>
  group_by(state, city_ref) |>
  mutate(total_city = sum(emission, na.rm = TRUE)) |>  # soma total por cidade DENTRO do estado
  ungroup() |>
  mutate(city_ref = fct_reorder(city_ref, total_city, .desc = FALSE)) |> 
  mutate(
    subsetor = case_when(
      subsetor == 'degradacao_em_terras_florestais'~'DgTF',
      subsetor == 'fermentacao_enterica_gado_confinado'~'FEGC',
      subsetor == 'fermentacao_enterica_gado_a_pasto'~'FEGP',
      subsetor == 'esterco_deixado_no_pasto_gado'~'EP',
      subsetor == 'manejo_de_esterco_gado_confinado'~'MEGC',
      subsetor == 'desmatamento_em_terras_florestais'~'DmTF',
      subsetor == 'queimadas_em_terras_florestais'~'QTF',
      subsetor == 'queimadas_em_areas_agricolas'~'QG',
      subsetor == 'queimadas_em_areas_arbustivas'~'QA',
      subsetor == 'queimadas_em_areas_umidas'~'QU',
      subsetor == 'cultivo_de_arroz'~'CA',
      subsetor == 'residuos_de_culturas_agricolas'~'RCA',
      subsetor == 'esterco_aplicado_ao_solo'~'EAS',
      subsetor == 'uso_liquido_de_terras_florestais'~'ULTF', 
      subsetor == 'uso_liquido_de_areas_arbustivas_e_gramineas'~'ULARG',
      subsetor == 'uso_liquido_de_areas_umidas'~'UAU', 
      subsetor == 'aplicacao_de_fertilizantes_sinteticos'~'AFS',
      subsetor == 'transporte_rodoviario'~'TR',
      subsetor == 'remocoes_de_carbono_sequestro'~'RCS',
      TRUE ~ subsetor))|>
  ggplot(aes(emission/1e6, #passar de ton para Mton
             city_ref,
             fill = subsetor)) +
  geom_col(col="black", lwd = 0.1) +
  xlab(bquote(Emissão~CO[2]~e~(Mton))) +
  labs(#x = 'Emission (Mton)',
    y = 'Cidade',
    fill = 'Setor') +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(1)),
    # axis.title.x = element_text(size = rel(2)),
    axis.text.y = element_text(size = rel(1.3)),
    # axis.title.y = element_text(size = rel(2)),
    legend.text = element_text(size = rel(1)),
    #legend.title = element_text(size = rel(1.7)),
    title = element_text(face = 'bold'),
    legend.position = 'top',
    legend.background = element_rect(fill = "transparent", color = "black")) +
  scale_fill_viridis_d(option ='plasma') +
  facet_wrap(~state,scales = "free",ncol = 1) +
  annotate("text",
           x=2,
           y=1,
           label = ".",
           size=0.1)

top_set 
top_subset
```

## 📊 VISUALIZANDO MAIORES EMISSORES PARA OS SUBSETORES DE AGRICULTURA

Base NOVA - Pegando a base antes da incorporação, apenas para
representar um ano de emissões

*É possível escolher outro setor, alterando o setor do seguinte trecho
de código:*
`s_agricultura = ifelse(setor == "Agricultura", subsetor, NA)`

Visualização em acumulado de CO2 equivalente no período de 2021 a 2024
(somente considerada a base climate TRACE nova, devido sua metodologia
consolidada, de modo que se evite os outliers entre outros problemas da
base antiga)

``` r
# Base nova antes da incorporação
emissions_sources_21_24 <- readxl::read_excel("data-raw/climate-trace-br.xlsx")

top_agc <- emissions_sources_21_24 |>
  mutate(emissao_co2e = ifelse(emissao_co2e>=0, emissao_co2e,0)) |> 
  rename(city_ref = fonte,
         emissao = emissao_co2e,
         state = estado,
         year = ano) |>
  filter(
    year %in% 2021:2024,                   #%in% 2021:2024
    state %in% my_states # <-----
  ) |>
  mutate(
    city_ref = stri_trans_general(tolower(city_ref), "Latin-ASCII"),
    city_ref = trimws(city_ref),
    city_ref = str_extract(city_ref, padrao_municipios)) |> 
  mutate(
    s_agricultura = ifelse(setor == "Agricultura", subsetor, NA)) |> 
  drop_na() |>
  select(year, state, city_ref, setor, s_agricultura, emissao) |>
  group_by(state, city_ref,s_agricultura) |>
  summarise(
    emissao_tot = sum(emissao, na.rm = T)
  ) |>
  ungroup() |>
  group_by(state) |>
  mutate(
    state = ifelse(state == "DF", "GO", state),
    city_ref = city_ref |> fct_reorder(emissao_tot) |>
      fct_lump(n = 3, w = emissao_tot)) |>
  filter(city_ref != "Other") |> 
  filter(city_ref != 'other') |> 
    group_by(state, city_ref) |>
    mutate(total_city = sum(emissao_tot, na.rm = TRUE)) |>  # soma total por cidade DENTRO do estado
    ungroup() |>
    mutate(city_ref = fct_reorder(city_ref, total_city, .desc = FALSE)) |> 
  mutate(
    s_agricultura = case_when(
      s_agricultura == "esterco aplicado ao solo" ~ "EAS",
      s_agricultura == "Fermentação entérica – gado confinado" ~ "FEGC",
      s_agricultura == "Fermentação entérica – gado a pasto" ~ "FEGP",
      s_agricultura == "Queimadas em áreas agrícolas" ~ "QAG",
      s_agricultura == "Resíduos de culturas agrícolas" ~ "RCA",
      s_agricultura == "Uso líquido de áreas arbustivas e gramíneas" ~"ULAG", 
      s_agricultura == "Uso líquido de áreas úmidas" ~"ULAU",
      s_agricultura == "Uso líquido de terras florestais" ~"ULTF",
      s_agricultura == "Esterco deixado no pasto (gado)"  ~ "EP",
      s_agricultura == "Manejo de esterco – gado confinado" ~ "MEGC",
      s_agricultura == 'Cultivo de arroz' ~ 'CA',
      s_agricultura == "Aplicação de fertilizantes sintéticos" ~ 'AFS'
    )) |> 
  drop_na() |> 
  ggplot(aes(emissao_tot/1e6, #passar de ton para Mton
             city_ref,
             fill = s_agricultura)) +
  geom_col(col="black", lwd = 0.1) +
  xlab(bquote(Emissão~CO[2]~e~(Mton))) +
  labs(#x = 'Emission (Mton)',
    y = 'Cidade',
    fill = 'Subsetor') +
  theme_bw() +
  theme(
    axis.text.x = element_text(size = rel(1)),
    # axis.title.x = element_text(size = rel(2)),
    axis.text.y = element_text(size = rel(1.3)),
    # axis.title.y = element_text(size = rel(2)),
    legend.text = element_text(size = rel(1)),
    #legend.title = element_text(size = rel(1.7)),
    title = element_text(face = 'bold'),
    legend.position = 'top',
    legend.background = element_rect(fill = "transparent", color = "black")) +
  scale_fill_viridis_d(option ='plasma') +
  facet_wrap(~state,scales = "free",ncol = 1) +
  annotate("text",
           x=2,
           y=1,
           label = ".",
           size=0.1)

top_agc
```
