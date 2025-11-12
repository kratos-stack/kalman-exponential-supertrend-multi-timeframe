# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### Added
* [Your next feature]

### Changed
* [A change you are working on]

### Fixed
* [A bug you are fixing]

---

## [1.1.0] - 2025-11-12

### Added
* **Multi-Timeframe (MTF) Support:** Added `useMtf` toggle and `mtf_timeframe` input to allow the Kalman Exponential SuperTrend to run on a higher timeframe.
* Encapsulated all logic into `f_calculateIndicator()` to support a non-repainting MTF implementation.

### Fixed
* Corrected the `Lower` band calculation in the Exponential SuperTrend logic, which was incorrectly referencing `UpperBand`.

---

## [1.0.0] - 2025-11-10

### Added
* **Initial Release:** Kalman Exponential SuperTrend (KEST)
* Kalman Filter for price smoothing (`f_kalman`).
* Exponentially smoothed SuperTrend bands.
* Customizable style and color settings.
