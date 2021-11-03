# Changelog
All notable changes to this project will be documented in this file.
This project adheres to [Semantic Versioning](https://semver.org/).

## Unreleased
### Added
More algorithms
Customize Presets
Colors to information being displayed
Start Power Limit tuning from the lowest value
Custom pool/wallet to use with the --keepMining parameter
### Changed
### Removed
### Fixed

## [1.4.1](https://github.com/CryptoTuner/CryptoTuner/releases/tag/1.4.1) 2021-11-03
### Fixed
Problem with the initialization of the program.

## [1.4.0](https://github.com/CryptoTuner/CryptoTuner/releases/tag/1.4.0) 2021-11-02 [YANKED]
### Added
Check if gpu already finished Tuning
Watt Steps argument

## [1.3.1](https://github.com/CryptoTuner/CryptoTuner/releases/tag/1.3.1) 2021-11-02
### Fixed
Loading of process.json for non-existing gpus

## [1.3.0](https://github.com/CryptoTuner/CryptoTuner/releases/tag/1.3.0) 2021-11-02
### Added
"--resume" flag for continuing the OC process from where it was left at (in case of BSOD or manually quitting)
Only count datapoints once there is Hashrate
"--keepMining" flag for continuing with mining once Tuning is complete
Memory tweak detection: will lower Mem OC to -1000 for stability

## [1.2.0](https://github.com/CryptoTuner/CryptoTuner/releases/tag/1.2.0) 2021-11-01
### Added
Catch Ctrl+C and exit gracefully
Verbosity setting (up to 3 levels)
### Changed
Changed parameters names and short-names compared to v1.1.0. Not changing major version as there are no known users
Improve verbose
Miner now is on the root folder
### Removed
Debug information form CLI

## [1.1.0](https://github.com/CryptoTuner/CryptoTuner/releases/tag/1.1.0) 2021-10-30
### Added
"MemTweak" parameter/argument for compatible cards
This CHANGELOG as a way to document changes on the code.


## [1.0.0](https://github.com/CryptoTuner/CryptoTuner/releases/tag/1.0.0) 2021-10-29
### Added
Initial Release