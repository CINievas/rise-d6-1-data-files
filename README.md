# RISE D6.1 Data Files

This repository contains the input files used for the proof of concept developed as part of
Task 6.1 of the [RISE project](http://rise-eu.org/home/), as well as the main outputs. This task
has focused on demonstrating the integration of RISE innovations in the fields of operational
earthquake loss forecasting (OELF), rapid loss assessment (RLA) and structural health
monitoring. The complete report can be found
[here](http://static.seismo.ethz.ch/rise/deliverables/Deliverable_6.1.pdf).

These input files are intended to be run with the
[Real-Time Loss Tools](https://git.gfz-potsdam.de/real-time-loss-tools/real-time-loss-tools).

## Contents of this README

[Structure of this repository](#structure-of-this-repository)

[Running the analyses](#running-the-analyses)

[Attribution of individual input data files](#attribution-of-individual-input-data-files)

[Acknowledgements](#acknowledgements)

[Citation](#citation)

[License](#license)

## Structure of this repository

Input and output files for the three case-studies presented in detail in the
[Deliverable 6.1](http://static.seismo.ethz.ch/rise/deliverables/Deliverable_6.1.pdf) of the
[RISE project](http://rise-eu.org/home/) are contained herein, split into two directories:
[input](./input) and [output](./output).

The [input](./input) directory contains three ZIP files with the input files for each of the
case-studies, while the [output](./output) directory contains three sub-directories, each of
them with the following files:

- `all_damage_states_after_OELF_cumulative.csv`: Expected probabilities or number of buildings
per `building_id` in each damage state after each OELF calculation. Values are cumulative with
respect to already-run RLAs.
- `all_damage_states_after_RLA_cumulative.csv`: Expected probabilities or number of buildings
per `building_id` in each damage state after each RLA. Values are cumulative (i.e. considering
all RLAs run up to each point in time).
- `all_damage_states_after_RLA_incremental.csv`: Expected changes in probabilities or number of
buildings per `building_id` for each damage state due to each RLA. 
- `all_losses_economic_OELF_cumulative_absolute.csv`: Expected economic losses per `building_id`
after each OELF calculation (mean of all stochastic event sets of seismicity). Values are
cumulative with respect to already-run RLAs.
- `all_losses_economic_OELF_cumulative_ratio.csv`: Expected economic loss ratios per
`building_id` (as percentages) after each OELF calculation (mean of all stochastic event sets of
seismicity). Values are cumulative with respect to already-run RLAs.
- `all_losses_economic_RLA_cumulative_absolute.csv`: Expected economic losses per `building_id`
after each RLA calculation. Values are cumulative (i.e. considering all RLAs run up to each
point in time).
- `all_losses_economic_RLA_cumulative_ratio.csv`: Expected economic loss ratios per
`building_id` (as percentages) after each RLA calculation. Values are cumulative (i.e.
considering all RLAs run up to each point in time).
- `all_losses_economic_RLA_incremental_absolute.csv`: Expected incremental economic losses per
`building_id` due to each RLA calculation (i.e. current economic loss minus economic loss up to
the previous earthquake).
- `all_losses_economic_RLA_incremental_ratio.csv`: Expected incremental economic loss ratios per
`building_id` (as percentages) due to each RLA calculation (i.e. current economic loss ratio
minus economic loss ratio up to the previous earthquake).
- `all_losses_human_severity_X_OELF_incremental_absolute.csv`: Expected human casualties of
severity X (see definition of X below) due to each OELF calculation (mean of all stochastic
event sets of seismicity) per `building_id`.
- `all_losses_human_severity_X_OELF_incremental_ratio.csv`: Expected ratio of human casualties of
severity X (see definition of X below) due to each OELF calculation (mean of all stochastic
event sets of seismicity) per `building_id`. The ratio is calculated with respect to the total
number of census occupants associated with each `building_id` and expressed as a percentage.
- `all_losses_human_severity_X_RLA_cumulative_absolute.csv`: Expected human casualties of
severity X (see definition of X below) after each RLA calculation per `building_id`. Values are
cumulative (i.e. considering all RLAs run up to each point in time).
- `all_losses_human_severity_X_RLA_cumulative_ratio.csv`: Expected human casualties of severity
X (see definition of X below) after each RLA calculation per `building_id`. Ratios are
cumulative (i.e. considering all RLAs run up to each point in time) and calculated with respect
to the total number of census occupants associated with each `building_id` (expressed as
percentages).
- `all_losses_human_severity_X_RLA_incremental_absolute.csv`: Expected human casualties of
severity X (see definition of X below) due to each RLA calculation per `building_id`.
- `all_losses_human_severity_X_RLA_incremental_ratio.csv`: Expected ratio of human casualties of
severity X (see definition of X below) due to each RLA calculation per `building_id`. The ratio
is calculated with respect to the total number of census occupants associated with each
`building_id` and expressed as a percentage.
- `all_portfolio_losses_economic_RLA_cumulative_absolute.csv`: Expected economic losses for the
whole building portfolio after each RLA calculation. Values are cumulative (i.e. considering all
RLAs run up to each point in time). Equivalent of
`all_losses_economic_RLA_cumulative_absolute.csv` but for the whole portfolio.
- `all_portfolio_losses_economic_RLA_cumulative_ratio.csv`: Expected economic loss ratios for
the whole building portfolio (as percentages) after each RLA calculation. Values are cumulative
(i.e. considering all RLAs run up to each point in time). Equivalent of
`all_losses_economic_RLA_cumulative_ratio.csv` but for the whole portfolio.
- `all_portfolio_losses_economic_RLA_incremental_absolute.csv`: Expected incremental economic
losses for the whole building portfolio due to each RLA calculation (i.e. current economic loss
minus economic loss up to the previous earthquake). Equivalent of
`all_losses_economic_RLA_incremental_absolute.csv` but for the whole portfolio.
- `all_portfolio_losses_economic_RLA_incremental_ratio.csv`: Expected incremental economic loss
ratios for the whole building portfolio (as percentages) due to each RLA calculation (i.e. current
economic loss ratio minus economic loss ratio up to the previous earthquake). Equivalent of
`all_losses_economic_RLA_incremental_ratio.csv` but for the whole portfolio.
- `all_portfolio_losses_human_severity_X_RLA_cumulative_absolute.csv`: Equivalent of
`all_losses_human_severity_X_RLA_cumulative_absolute.csv` but for the whole building portfolio.
- `all_portfolio_losses_human_severity_X_RLA_cumulative_ratio.csv`: Equivalent of
`all_losses_human_severity_X_RLA_cumulative_ratio.csv` but for the whole building portfolio.
- `all_portfolio_losses_human_severity_X_RLA_incremental_absolute.csv`: Equivalent of
`all_losses_human_severity_X_RLA_incremental_absolute.csv` but for the whole building portfolio.
- `all_portfolio_losses_human_severity_X_RLA_incremental_ratio.csv`: Equivalent of
`all_losses_human_severity_X_RLA_incremental_ratio.csv` but for the whole building portfolio.

In all results associated with human casualties, `severity_X` refers to the severity of the
sustained injuries as per the injury classification scale reported in the HAZUS-MH Technical
Manual (Federal Emergency Management Agency, 2003):

- Injury severity level 4: instantaneously killed or mortally injured;
- Injury severity level 3: injuries that pose an immediate life-threatening condition;
- Injury severity level 2: injuries that require use of medical technology (e.g. x-rays,
surgery) but are not expected to be life-threatening.
- Injury severity level 1: injuries that require basic medical aid (in the field, no
hospitalisation).

## Running the analyses

The steps to be able to run any of the case-studies with the
[Real-Time Loss Tools](https://git.gfz-potsdam.de/real-time-loss-tools/real-time-loss-tools) are
the following:

1. Clone this repository or download the individual input ZIP file of interest (e.g.,
`Central_Italy_Seq_12.zip`).
2. Unzip the ZIP file. The result will be one directory (e.g., `Central_Italy_Seq_12`) with the
internal structure as described in the Real-Time Loss Tools.
3. Place the main directory (e.g. `Central_Italy_Seq_12`) under a location of your choice (e.g.,
`/username/folder/sub_folder`).
4. Indicate the final path to the main directory
(`/username/folder/sub_folder/Central_Italy_Seq_12`) as `main_path` in the configuration file
(`config.yml`). The path currently indicated is `main_path: TODO`.
5. If not done yet, install the `Real-Time Loss Tools` as indicated
[here](https://git.gfz-potsdam.de/real-time-loss-tools/real-time-loss-tools#installation).
6. Run the `Real-Time Loss Tools` as indicated
[here](https://git.gfz-potsdam.de/real-time-loss-tools/real-time-loss-tools#running).

## Attribution of individual input data files

Individual input files in this repository stem from different sources, as enumerated below.
Files not mentioned in this enumeration are attributed directly to the main
[citation](#citation). If you make use of the whole set of files, please attribute to the main
[citation](#citation). If you make use of individual files, please attribute as described below.

- `catalogues`:

  - `Central_Italy_EQ_XX.csv` (`XX` from `01` through `09`), `LAquila_EQ_YY.csv` (`YY` from `01`
  through `08`): all earthquake properties from [ITACA](https://itaca.mi.ingv.it):

    - Russo E, Felicetta C, D Amico M, Sgobba S, Lanzano G, Mascandola C, Pacor F, Luzi L (2022)
    Italian Accelerometric Archive v3.2 - Istituto Nazionale di Geofisica e Vulcanologia,
    Dipartimento della Protezione Civile Nazionale. doi:10.13127/itaca.3.2

  - `forecast_YYYY_MM_DDTHH_MM_SSday.txt`: 24-hour seismicity forecasts generated right after
  the date and time indicated in the file name, generated with the
  [ETAS.inlabru](https://github.com/edinburgh-seismicity-hub/spatio_temporal_ETAS_for_OEF)
  method developed by:

    - Naylor M, Serafini F, Lindgren F, Main I (2023) Bayesian modelling of the temporal
    evolution of seismicity using the ETAS.inlabru R-package. Frontiers in Applied Mathematics
    and Statistics, special issue Physical and Statistical Approaches.
    [DOI: 10.3389/fams.2023.1126759](https://www.frontiersin.org/articles/10.3389/fams.2023.1126759)

    - Serafini F, Lindgren F, Naylor M (2023) Approximation of Bayesian Hawkes process with
	inlabru. Envirometrics, 29 p.
	[https://doi.org/10.1002/env.2798](https://doi.org/10.1002/env.2798)

- `ruptures`: 

  - `source_model_for_stochastic_OELF.xml`: Italian source model used to stochastically sample
  rupture properties for OELF developed by:

    - Visini F, Meletti C, Rovida A, D'Amico V, Pace B, Pondrelli S (2022) An updated
	area-source seismogenic model (MA4) for seismic hazard of Italy. Natural Hazards and Earth
	System Sciences 22:2807-2827.
	[https://doi.org/10.5194/nhess-22-2807-2022](https://doi.org/10.5194/nhess-22-2807-2022)

  - `rla/source_parameters.csv`: all earthquake properties from [ITACA](https://itaca.mi.ingv.it):

    - Russo E, Felicetta C, D Amico M, Sgobba S, Lanzano G, Mascandola C, Pacor F, Luzi L (2022)
    Italian Accelerometric Archive v3.2 - Istituto Nazionale di Geofisica e Vulcanologia,
    Dipartimento della Protezione Civile Nazionale. doi:10.13127/itaca.3.2

- `shm/damage_results_shm.csv`: Probabilities of each damage grade for the three monitored
buildings resulting from the preliminary Structural Health Monitoring (SHM)-based fragility
models created for use in RISE Deliverable 6.1 based on the damage-sensitive features presented
in:

  - Reuland Y, Martakis P, Chatzi E (2023) A Comparative Study of Damage-Sensitive Features for
  Rapid Data-Driven Seismic Structural Health Monitoring. Applied Sciences 13(4):2708.
  [https://doi.org/10.3390/app13042708](https://doi.org/10.3390/app13042708).

- `static`:

  - `fragility_model.xml`: state-dependent fragility models for Italian building classes
  developed by:

    - Orlacchio M (2022) The effects of seismic sequences on seismic hazard and structural
    vulnerability. PhD Thesis. University of Naples Federico II, Naples, Italy.

  - `site_model.csv`: average shear-wave velocities in the top 30 metres (Vs30) interpolated
  using inverse distance weighting from:
  
    - Weatherill G, Crowley H, Roullé A, Tourlière B, Lemoine A, Gracianne C, Kotha SR, Cotton F
    (2022) Modelling site response at regional scale for the 2020 European Seismic Risk Model
    (ESRM20). Bulletin of Earthquake Engineering 21:665-714.
    [https://doi.org/10.1007/s10518-022-01526-5](https://doi.org/10.1007/s10518-022-01526-5)

  - `consequences_economic.csv`: damage ratios from:
  
    - Crowley H, Dabbeek J, Despotaki V, Rodrigues D, Martins L, Silva V, Romão, X, Pereira N,
    Weatherill G, Danciu L (2021a) European Seismic Risk Model (ESRM20), EFEHR Technical Report
    002, V1.0.1, 84 pp.
    [https://doi.org/10.7414/EUC-EFEHR-TR002-ESRM20](https://doi.org/10.7414/EUC-EFEHR-TR002-ESRM20)

## Acknowledgements

These data files have been developed within the [RISE project](http://rise-eu.org/home/), which
has received funding from the European Union's Horizon 2020 research and innovation programme
under grant agreement No. 821115.

## Citation

Please read [here](#attribution-of-individual-input-data-files) for details on the attribution
of individual files.

Please cite the two references below:

Nievas CI, Crowley H, Reuland Y, Weatherill G, Baltzopoulos G, Bayliss K, Chatzi E, Chioccarelli
E, Guéguen P, Iervolino I, Marzocchi W, Naylor M, Orlacchio M, Pejovic J, Popovic N, Serafini F,
Serdar N (2023) Integration of RISE innovations in the fields of OELF, RLA and SHM.
RISE Project Deliverable 6.1. Available at
[http://static.seismo.ethz.ch/rise/deliverables/Deliverable_6.1.pdf](http://static.seismo.ethz.ch/rise/deliverables/Deliverable_6.1.pdf).

Nievas CI, Crowley H, Reuland Y, Weatherill G, Baltzopoulos G, Bayliss K, Chatzi E, Chioccarelli
E, Guéguen P, Iervolino I, Marzocchi W, Naylor M, Orlacchio M, Pejovic J, Popovic N, Serafini F,
Serdar N (2023) Integration of RISE innovations in the fields of OELF, RLA and SHM: input and
output datasets (Version 1.0) [Data set]. Zenodo. (ZENODO DOI TO BE ADDED HERE)

## License

These files are distributed under the Creative Commons Attribution-ShareAlike 4.0 International
(CC BY-SA 4.0) License. To view a copy of this license, visit
[https://creativecommons.org/licenses/by-sa/4.0/](https://creativecommons.org/licenses/by-sa/4.0/)
or send a letter to Creative Commons, PO Box 1866, Mountain View, CA 94042, USA.
