# GSheet to ARB

Imports Application Resource Bundle (ARB) from Google Sheets 

https://github.com/googlei18n/app-resource-bundle/wiki/ApplicationResourceBundleSpecification

## Usage

### Import ARB files from the Google Sheet

1. To import ARB files from Google Sheet run the `gsheet_to_arb:import` program.

    ```
    pub run gsheet_to_arb:import --config gsheet_to_arb.yaml
    ```

2. If need - authenticate Google Sheet Access

3. Optionally generate Dart classes from the ARB files.

    ```
    pub run gsheet_to_arb:arb_to_dart --config gsheet_to_arb.yaml
    ```

## Setup

### Copy Google Sheet template

1. Open sample Google spreadsheet template available at:
    - https://docs.google.com/spreadsheets/d/1CwFRjtiCmCl8yvP55yBT70h-Yt00CcigD816hsGo7KU/edit?usp=sharing

2. Copy sample to your Drive account 
    - File -> Make a copy

3. Save `DOCUMENT_ID` of the Google spreadsheet
    - https://docs.google.com/spreadsheets/d/DOCUMENT_ID/edit#gid=0

### Authenticate

[Authenticate](docs/Authentication.md) API access either by using Client or Server authentication.

### Configure your Dart project

1. Add gsheet_to_arb dev dependency to the pubspec.yaml
    ```yaml
    dev_dependencies:
      gsheet_to_arb: ^0.0.4
    ```

2. Updated dependencies
    ```pub update```

3. Create plugin configuration
    ```yaml
    pub run gsheet_to_arb:import --create-config gsheet_to_arb.yaml
    ```

3. Update plugin configuration  ```gsheet_to_arb.yaml``` e.g.
    ```yaml
    gsheet_to_arb:
      arb_file_prefix: 'intl'
      output_directory: 'lib/src/i18n'
      gsheet:
        document_id: '<DOCUMENT_ID>'
        sheet_id: '0'
        auth:
          service_account_key_path: "~/.ssh/gsheet-to-arb-server-config.json"
    ```

## TODO

- Support ARB plurals