# Introduction
This project curates a list of physical quantities and their units of measure, in a structured data format that's easy to read and write.  In addition, these values are used to generate a lower-level intermediary representation of these quantities and units, suitable for use in various software projects.

# Concepts
TODO - Explain what a physical quantity is, and what a unit of measure is.  Explain the SI system and metric prefixes, and what the base quantities and derived quantities are.

TODO - Explain how I handled the conversion formula, and how the `new unit = f(metric unit)` thing works.

In the United States, the standards body for measurement is NIST, and they've published [NIST Special Publication 1038 "The International System of Units (SI) - Conversion factors for General Use"](http://www.nist.gov/pml/wmd/metric/upload/SP1038.pdf).  This guide contains the approved conversion factors between various units and the base SI units.  Where possible, we adhere strictly to the conversion factors laid out by this organization.

# High-Level Document Format Definition
- [Version 1](docs/high_level_doc_v1.md)

# Low-level Document Format Definition
- [Version 1](docs/low_level_doc_v1.md)

# Additional Documentation
[Building the Low-level Documents](docs/building.md)
[Contributing new Units and Unit Names](CONTRIBUTING.md)

# Projects Using These Definitions
If your project is regularly using these definitions and you don't see your project's name on the list, submit a pull request and we'll be happy to add it.
- [php-units-of-measure](https://github.com/PhpUnitsOfMeasure/php-units-of-measure)
