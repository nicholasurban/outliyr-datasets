# Light Therapy Devices Dataset

Device index for red/NIR panels, wearables, brain PBM, full-spectrum lamps, and SAD lamps. It contains a corrected product index and a separate observation file. A value is not an independently verified measurement merely because it appears in this repository; use the observation metadata and eligibility fields described below.

## Current release files

The current release has two canonical CSVs, generated from the same validated comparison source:

- [`light-therapy-products.csv`](light-therapy-products.csv) is one row per product. Its columns are `product_id`, `slug`, `title`, `subtype`, `trust_tier`, `price_usd`, `comparison_member`, `comparison_eligible_at_12in`, `comparable_irradiance_mw_cm2`, `comparison_context_key`, and `observation_count`.
- [`light-therapy-measurements.csv`](light-therapy-measurements.csv) is one row per observation. Its columns are `product_id`, `slug`, `observation_index`, `metric`, `value`, `unit`, `origin`, `distance_in`, `geometry`, `device_mode`, `spectrum_coverage`, `comparison_cohort`, `method_id`, `method_version`, `test_run_id`, `tested_at`, `instrument`, `source_url`, `source_captured_at`, `status`, `legacy_source_field`, `comparison_eligible_at_12in`, `dose_reference_eligible`, and `ineligibility_reason`.

`light-therapy-devices.csv` is a compatibility alias that is byte-identical to `light-therapy-products.csv`. It intentionally replaces the prior 28-column CSV with the corrected product-index schema. Consumers of the old field layout must migrate to the two canonical files.

The row counts are release-specific. Read the committed files or release notes for the count in a given version rather than assuming a fixed catalog size.

## Sources and observation status

- `verified` is a legacy product-level tier indicating that Outliyr tested the device hands-on. It does **not** establish the source, distance, geometry, device mode, or test-run details of every value on that product's record.
- An individual Outliyr observation is comparison-eligible only when its record documents compatible test context under the published [testing methodology](https://outliyr.com/light-therapy-testing-methodology): origin, distance, geometry, device mode, unit, and source or test-run details.
- `spec-sheet` identifies a manufacturer claim. A manufacturer claim is retained at its native stated conditions and is not an Outliyr measurement.
- `community` identifies a user-submitted record. It is not an Outliyr measurement unless separately documented as one.

Source URLs and capture dates help readers assess claims, but missing source context means the claim cannot support a comparable conclusion. A value may remain in the observation file as historical source data without being eligible for a recommendation, sortable comparison, dose calculation, summary statement, or structured-data measurement property.

## Reading irradiance values

Manufacturer irradiance claims and independently observed irradiance values answer different questions. Do not compare them as interchangeable values.

The current release does not normalize manufacturer claims into observed irradiance. In particular:

- A value without documented measurement distance, geometry, and device mode has **unknown measurement context** and is comparison-ineligible.
- A manufacturer claim made at a native distance, including contact, is not an observation at another distance. No inferred or inverse-square conversion is supplied for comparison use.
- A historical claim field labeled for a fixed distance must not be read as a direct manufacturer claim or Outliyr measurement at that distance unless the supporting source explicitly establishes it.

The dataset's maintained comparison outputs should use only observations with documented, compatible conditions. `comparison_eligible_at_12in` and `dose_reference_eligible` are generated decisions from the shared validation source; do not derive them from raw values or manufacturer claims.

## Other fields

The previous 28-column CSV included wavelengths, flicker, EMF, noise, ratings, and other non-irradiance fields. Those values are preserved in the immutable [`v2026.07.0`](https://github.com/nicholasurban/outliyr-datasets/tree/v2026.07.0) release and Git history, where their older source and geometry limitations remain visible. They are intentionally omitted from the current canonical files until each field has a validated source and export contract. Their omission does not establish that a device lacks the property.

## Historical release boundary

The `v2026.07.0` snapshot and its [Zenodo DOI](https://doi.org/10.5281/zenodo.21251601) are historical, immutable artifacts. They are not corrected by this release. In particular, their fixed-distance irradiance and derived claim fields must not be used as current comparison evidence. Cite a current repository release for the corrected schema; cite the historical tag only when reproducing or auditing the prior snapshot.

Live sortable version: https://outliyr.com/app/light-therapy-comparison

License: CC BY 4.0 (attribution required). Suggested citation: "Outliyr Light Therapy Devices Dataset, [version or access date], outliyr.com/app/light-therapy-comparison". When citing a finding, include the product record and its source or observation metadata.
