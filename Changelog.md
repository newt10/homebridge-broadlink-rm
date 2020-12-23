# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## Release 3.6.23 - 2020-12-23
### Fixed
1. Bug in heater-cooler accessory due to const variable assignment when changing modes.

### Changed
1. Platform helper is integrated into the project for better maintainability.

## Release 3.6.22 - 2020-12-08
### Added
1. Support for recording default power on oscillation state for fan accessory.

### Fixed
1. Reset to default setting for fan updates Home app UI based on default state defined in config.json.
2. HAP Warning for Characteristic.On in fan accessory.

### Changed
1. Improved changelog formatting based on keep your changelog.
2. Documentation enhancements for fan accessory in a single document.

## Release 3.6.21 - 2020-11-03
### Added
1. New accessory type - heater-cooler for better representation of standalone ACs and heaters

## Release 3.6.20 - 2020-10-19
### Fixed
1. Documentation updates for better readability
### Added
1. Changelog to provide better visibility into changes and progress.

## Release 3.6.19 - 2020-10-18
### Added
1. Updated fan accessory specifications with support for speed step size property
2. Support for combined hex codes for fan speed and swing mode

### Changed
3. Renamed plugin, platform and npm packages to support installation along side original plugin or other forks
