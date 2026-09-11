# Light Therapy Devices Dataset

Device index for red/NIR panels, wearables, brain PBM, full-spectrum lamps, and SAD lamps. It contains a mix of independently observed measurements where their provenance is documented and manufacturer-supplied specifications. It is not a universal lab-test database, and a value should not be interpreted as an independently verified measurement unless its observation metadata supports that conclusion.

## Sources and observation status

- `verified` is a legacy product-level tier indicating that Outliyr tested the device hands-on. It does **not** establish the source, distance, geometry, device mode, or test-run details of every value on that product's record.
- An individual Outliyr observation is comparison-eligible only when its record documents compatible test context under the published [testing methodology](https://outliyr.com/light-therapy-testing-methodology): origin, distance, geometry, device mode, unit, and source or test-run details.
- `spec-sheet` identifies a manufacturer claim. A manufacturer claim is retained at its native stated conditions and is not an Outliyr measurement.
- `community` identifies a user-submitted record. It is not an Outliyr measurement unless separately documented as one.

Source URLs and capture dates help readers assess claims, but missing source context means the claim cannot support a comparable conclusion. A value may remain in the index as historical source data without being eligible for a recommendation, sortable comparison, dose calculation, summary statement, or structured-data measurement property.

## Reading irradiance values

Manufacturer irradiance claims and independently observed irradiance values answer different questions. Do not compare them as interchangeable values.

The current CSV retains historical fixed-distance irradiance slots. Those slots are raw historical values, not a validated conversion or normalization system. In particular:

- A value without documented measurement distance, geometry, and device mode has **unknown measurement context** and is comparison-ineligible.
- A manufacturer claim made at a native distance, including contact, is not an observation at another distance. No inferred or inverse-square conversion is supplied for comparison use.
- A legacy claim field labeled for a fixed distance must not be read as a direct manufacturer claim or Outliyr measurement at that distance unless the supporting source explicitly establishes it.

The dataset's maintained comparison outputs should use only observations with documented, compatible conditions. The dataset will be regenerated from the same validated source used by the live comparison; until that release is published, do not infer new columns, distances, counts, or eligibility from this README.

## Other fields

The device index can include wavelength, flicker, EMF, power, noise, price, and related information. Each field must be read with its record-level source and observation status. Absence of a value or source is not evidence that a device lacks the property.

Live sortable version: https://outliyr.com/app/light-therapy-comparison

License: CC BY 4.0 (attribution required). Suggested citation: "Outliyr Light Therapy Devices Dataset, [version or access date], outliyr.com/app/light-therapy-comparison". When citing a finding, include the product record and its source or observation metadata.
