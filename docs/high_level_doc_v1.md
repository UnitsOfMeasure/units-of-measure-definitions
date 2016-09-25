# High-Level Language Documentation - Version 1
TODO - explain that it's a yaml file, and that the usual YAML spec applies.

## File Naming Conventions
TODO - explain that it's `physical_quantites.en-US.yml`, with the right language/country codes.

## Top Level Structure
The document has 4 top-level items:
- `schema_version` - required - The version of this specification to which the file adheres.
- `language` - required - The `ISO 639-1` language code followed by a `-` followed by the `ISO 3166-1` country code.
- `base_quantities` - required - Containing a list of base physical quantity definitions (see below)
- `derived_quantities` - required - Containing a list of derived physical quantity definitions (see below)

### Definition of a `base_quantities` Element
- `name` - required - Must be a string, no spaces, CamelCased, and unique in `base_quantities` and `derived_quantities`.
- `si_unit` - required - Defines the SI base unit for the quantity.  Can be either:
  - a list of equivalent unit names, with optional metric substitution tokens, where the first element is the default unit name:
    - examples:
      - `[${p}K, °K, ${P}kelvin]`
      - `[m, meter, meters]`

  - OR, it can be an object with these fields:
    - `names` - required - same as the unit name list above, but disallowing metric substitution tokens
    - `metric_prefixes` - optional - an object with fields:
      - `patterns` - required - a list of unit names with metric substitution tokens, representing the base metric unit (like [gram, grams], not [kilogram, kilograms])
      - `base_metric_unit_scaling_factor` - optional - The conversion between the SI unit and the base metric unit (like 1e-3 for the SI 'kilograms' and the metric base unit 'grams').  Assumed 1 if omitted.
    - examples:
      - `{names: [m, meter, meters]}`
      - `{names: [m, meter, meters], metric_prefixes: {patterns: [%{p}m, %{P}meter, %{P}meters]}}`
      - `{names: [kg, kilogram, kilograms], metric_prefixes: {patterns: [%{p}g, %{P}gram, %{P}grams], base_metric_unit_scaling_factor: 1e-3} }`

- `additional_units` - optional - list of alternate units of measure for the physical quantity.  Each item is either:
- a string of the form "{conversion expression} = {unit's names}", where the string follows these rules:
  - If the conversion expression has no variable "x", it is implied to be present like "x * {conversion expression}"
  - Once the variable "x" is identified (either explicit, or implied as above), a conversion equation can be formed as `{conversion expression with x as the SI unit} = {new unit}`. This equation can then be solved for either unit.
  - the additional unit's names are a comma separated set of equivalent unit aliases, with optional metric substitution tokens, where the first element is the default unit name:
  - examples:
    - `"x - 273.15 = °C, {p}C, {P}celsius"`
    - `"1e3 = ${p}t, ${P}tonne, ${P}tonnes"`

- OR, it can be an object with these fields:
  - `names` - required - like the SI unit object's `names` list above
  - `expression` - required - equivalent to the string component above
  - `metric_prefixes` - optional - like the SI unit object's `metric_prefixes` above
  - examples:
    - `{names: [ft, foot, feet], expression: 0.3048}`
    - `{names: [°C], expression: "x - 273.15", metric_prefixes: {patterns: [{p}C, {P}celsius"]}}`

## Metric Prefix Substitutions
TODO - explain how this works and where it's allowed (note this repeats some of the above)

## Allowed Constants
- `pi` -
