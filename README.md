# Google Whistle mapping configs

The repo contains the mapping configs for [Google Whistle](https://github.com/nwo-strap/healthcare-data-harmonization) (GW) mapping engine.


## Guide on developing mapping configs

The mapping configs is programmed with domain specific language, i.e. [Whistle Data Transformation Language](https://github.com/nwo-strap/healthcare-data-harmonization). This guide shows you how to develop new mapping configs.

### 1. Build GW mapping engine

Follow [this guide](https://github.com/nwo-strap/healthcare-data-harmonization#details) to install its dependencies and run building.

After building, the executable `GW_REPO_LOCAL_PATH/mapping_engine/main/main` should exist.

### 2. Clone this repo

```bash
git clone https://github.com/nwo-strap/mapping_configs.git
```
Let's call the path of this clone is `MAPPING_CONFIG_PATH`, e.g. `/home/mapping_configs`.

### 3. Update mapping configs

Update the mapping configs in e.g. `gamebus_fhir_r4` or develop new mapping configs based on your needs.

Some important materials about Whistle Data Transformation Language
-   [Mini guide on language basics](https://github.com/nwo-strap/healthcare-data-harmonization/blob/master/mapping_language/doc/codelab.md)
-   [Language reference](https://github.com/nwo-strap/healthcare-data-harmonization/blob/master/mapping_language/doc/reference.md)
-   [Builtin functions](https://github.com/nwo-strap/healthcare-data-harmonization/blob/master/mapping_language/doc/builtins.md)


### 4. Test mapping configs

Here we take `gamebus_fhir_r4` as an example.

#### 4.1 Update the `local_path` in `gamebus_fhir_r4/configurations/*.textproto` files

If the path of the cloned repo (`MAPPING_CONFIG_PATH`) is `/mapping_configs`, you don't need to anything;
Otherwise, you **MUST** update the `local_path` with absolute path.

#### 4.2 Run mapping

For example, try the following commands to convert GameBus player to [FHIR patient](https://www.hl7.org/fhir/patient.html):

    cd THIS_REPO_LOCAL_PATH
    GW_REPO_LOCAL_PATH/mapping_engine/main/main \
      -input_file_spec=MAPPING_CONFIG_PATH/gamebus_fhir_r4/example/gb_player.json
      -data_harmonization_config_file_spec=MAPPING_CONFIG_PATH/gamebus_fhir_r4/configurations/player.textproto \
      -output_dir=.

The output file is `./gb_player.output.json`.
You can find the reference output files in `gamebus_fhir_r4/example/output`.

### 5. Validate generated FHIR resources

To make sure the mapping output conforms to FHIR specification, the [fhir-validator-app](https://github.com/inferno-framework/fhir-validator-app) or its [service](https://inferno.healthit.gov/validator/) can help you on validation.
