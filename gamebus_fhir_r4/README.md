# GameBus-FHIR Mapping Configurations

This is the [Google Whistle](https://github.com/GoogleCloudPlatform/healthcare-data-harmonization) mapping configurations for the data transformation from [GameBus](https://blog.gamebus.eu/) to [FHIR version R4](https://www.hl7.org/fhir/index.html).


## Overview

- `configurations`: The settings for running Google Whistle engine
- `projector_library`: All transformation functions
- `code_harmonization`: Transformation configurations of code systems
- `example`: Example files of input and output

## Usage

Make sure the path of this folder is `/mapping_configs/gamebus_fhir_r4`
```
Google_Whistle_mapping_engine_PATH \
  -input_file_spec=/mapping_configs/gamebus_fhir_r4/example/gb_player.json  \
  -data_harmonization_config_file_spec=/mapping_configs/gamebus_fhir_r4/configurations/player.textproto \
  -output_dir=.
```
`Google_Whistle_mapping_engine_PATH` is e.g. `healthcare-data-harmonization/mapping_engine/main/main`.