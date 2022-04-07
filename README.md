# Archive for Staadecker et al. "The Value of Long-Duration Energy Storage and its Interaction with a Zero-Emissions Electricity Grid"

This repository stores the configuration files used in the paper "The Value of Long-Duration Energy Storage and its Interaction with a Zero-Emissions Electricity Grid".

The baseline scenario input and output files are also given as examples. The model code used to generate all the scenarios input and output
files is available in the REAM-lab/switch repo [here](https://github.com/REAM-lab/switch/releases/tag/v2.0.0) (v2.0.0).

## Respository structure

### `zonal_capacity_factors.csv`

This file contains the wind and solar variable capacity factors aggregated by load zone used for all scenarios.
For load zones not present in the file, unaggregated variable capacity factors were used (from our database).
See the section "Wind and Solar Candidate Plant Aggregation" under "EXPERIMENTAL PROCEDURES" to learn more.
This file is included seperately as it is not stored in our database and cannot be created by `get_inputs.py`.

### `Storage Scenario Parameters.xlsx`

This file contains a bunch of storage scenarios and their associate storage parameters. 
For example, costs_scenario #13 on the "costs" tab stores the cost parameters used in the baseline.

When running the model, these values were directly retrieved by `switch_model/wecc/get_inputs/post_process_steps/add_storage.py`
based on the specified ID files in `config.yaml`.

### `/1342` 

This folder contains the inputs and outputs of the baseline scenario in the SWITCH format (as well as some logs and diagnostic graphs).

Note that large files (`variable_capacity_factors.csv`, `dispatch.csv`, and `DispatchGen.csv`) have been split into multiple files to not exceed Github's file size limit. 
(using the command `split -n l/2 --suffix=1 --additional-suffix=.csv variable_capacity_factors.csv variable_capacity_factors_`).

### `Scenario Tracker.xlsx`

This spreadsheet keeps track of all the scenarios we ran and importantly which scenario corresponds to which configuration file.

### `/scenario-configurations`

This folder contains the input `config.yaml` files for each scenario. These files specify how the input data is generated.