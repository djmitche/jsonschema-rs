# Changelog

## [Unreleased]

## [0.12.1] - 2021-07-29

### Fixed

- Allow using empty arrays or arrays with non-unique elements for the `enum` keyword in schemas. [#258](https://github.com/Stranger6667/jsonschema-rs/issues/258)
- Inaccurate schema path in validation error messages. [#257](https://github.com/Stranger6667/jsonschema-rs/issues/257)
- Panic on incomplete escape sequences in regex patterns. [#253](https://github.com/Stranger6667/jsonschema-rs/issues/253)

## [0.12.0] - 2021-07-24

### Changed

- Pre-compute `JSONSchema` representation.

## [0.11.1] - 2021-07-06

### Added

- Additional attributes to `ValidationError`. They are `message`, `schema_path` and `instance_path`. [#197](https://github.com/Stranger6667/jsonschema-rs/issues/197)

### Changed

- Update `pyo3` to `0.14.1`.

## [0.11.0] - 2021-06-19

### Added

- Report schema paths in validation errors. At the moment, it only displayed in the `ValidationError` message. [#199](https://github.com/Stranger6667/jsonschema-rs/issues/199)

## [0.10.0] - 2021-06-17

### Added

- Meta-schema validation for input schemas. [#198](https://github.com/Stranger6667/jsonschema-rs/issues/198)

## [0.9.1] - 2021-06-17

### Fixed

- The `format` validator incorrectly rejecting supported regex patterns. [#230](https://github.com/Stranger6667/jsonschema-rs/issues/230)

## [0.9.0] - 2021-05-07

### Added

- Support for look-around patterns. [#183](https://github.com/Stranger6667/jsonschema-rs/issues/183)

### Fixed

- Extend the `email` format validation. Relevant test case from the JSONSchema test suite - `email.json`.

## [0.8.0] - 2021-05-05

### Changed

- Error messages show paths to the erroneous part of the input instance. [#144](https://github.com/Stranger6667/jsonschema-rs/issues/144)

### Fixed

- Skipped validation on an unsupported regular expression in `patternProperties`. [#213](https://github.com/Stranger6667/jsonschema-rs/issues/213)
- Missing `array` type in error messages for `type` validators containing multiple values. [#216](https://github.com/Stranger6667/jsonschema-rs/issues/216)

## [0.6.2] - 2021-05-03

## Changed

- Update `PyO3` to `0.13.x`.
- Improved error message for the `additionalProperties` validator. After - `Additional properties are not allowed ('faz' was unexpected)`, before - `False schema does not allow '"faz"'`.
- The `additionalProperties` validator emits a single error for all unexpected properties instead of separate errors for each unexpected property.

### Fixed

- Floating point overflow in the `multipleOf` validator. Relevant test case from the JSONSchema test suite - `float_overflow.json`

### Performance

- Various performance improvements from the underlying Rust crate.

## [0.6.1] - 2021-03-26

### Fixed

- Incorrect handling of `\w` and `\W` character groups in `pattern` keywords. [#180](https://github.com/Stranger6667/jsonschema-rs/issues/180)
- Incorrect handling of strings that contain escaped character groups (like `\\w`) in `pattern` keywords.

## [0.6.0] - 2021-02-03

### Added

- `with_meta_schemas` argument for `is_valid` and update docstrings.
- `validate` function.

### Performance

- General performance improvements for subsets of `items` and `additionalProperties` validators.
- Defer schema & instance loading until they are used. It improves performance for cases when the user passes an nvalid draft version.

## [0.5.1] - 2021-01-29

### Changed

- Exclude unnecessary files from source code distribution.

## [0.5.0] - 2021-01-29

### Added

- Cache for documents loaded via the `$ref` keyword. [#75](https://github.com/Stranger6667/jsonschema-rs/issues/75)
- Meta schemas for JSON Schema drafts 4, 6, and 7. [#28](https://github.com/Stranger6667/jsonschema-rs/issues/28)

### Fixed

- Not necessary network requests for schemas with `$id` values with trailing `#` symbol. [#163](https://github.com/Stranger6667/jsonschema-rs/issues/163)
- Source code distribution. It was missing the source code for the underlying Rust crate and were leading to
  a build error during `pip install css-inline` on platforms that we don't have wheels for.
  [#159](https://github.com/Stranger6667/jsonschema-rs/issues/159)

### Performance

- Enum validation for input values that have a type that is not present among the enum variants. [#80](https://github.com/Stranger6667/jsonschema-rs/issues/80)

## [0.4.3] - 2020-12-15

### Changed

- Exclude the `cli` dependency from the `jsonschema` crate & update dependencies in `Cargo.lock`.

## [0.4.2] - 2020-12-11

### Fixed

- Number comparison for `enum` and `const` keywords. [#149](https://github.com/Stranger6667/jsonschema-rs/issues/149)
- Do not accept `date` strings with single-digit month and day values. [#151](https://github.com/Stranger6667/jsonschema-rs/issues/151)

## [0.4.1] - 2020-12-09

### Fixed

- Integers not recognized as numbers when the `type` keyword is a list of multiple values. [#147](https://github.com/Stranger6667/jsonschema-rs/issues/147)

## [0.4.0] - 2020-11-09

### Added

- Python 3.9 support.

### Changed

- Remove not needed `__init__.py` file. It improves performance for compiled schemas. [#121](https://github.com/Stranger6667/jsonschema-rs/issues/121)
- Update `PyO3` to `0.12`. [#125](https://github.com/Stranger6667/jsonschema-rs/issues/125)
- Use stable Rust.
- Set module documentation only once.

### Fixed

- ECMAScript regex support
- Formats should be associated to Draft versions (ie. `idn-hostname` is not defined on draft 4 and draft 6)
- Handle errors during conversion to `Value` instead of using `unwrap` in `JSONSchema::is_valid` and `JSONSchema::validate`. [#127](https://github.com/Stranger6667/jsonschema-rs/issues/127)

### Removed

- Python 3.5 support.

## [0.3.3] - 2020-06-22

### Fixed

- `items` allows the presence of boolean schemas. [#115](https://github.com/Stranger6667/jsonschema-rs/pull/115)

## [0.3.2] - 2020-06-13

### Fixed

- Packaging issue.

## [0.3.1] - 2020-06-12

### Added

- Added `jsonschema_rs.__build__` which contains useful build information. [#111](https://github.com/Stranger6667/jsonschema-rs/pulls/111)
- Wheels for Mac OS and Windows. [#110](https://github.com/Stranger6667/jsonschema-rs/issues/110)

### Changed

- Linux wheels are `manylinux2014` compatible. Previously they were `manylinux2010` compatible. [#111](https://github.com/Stranger6667/jsonschema-rs/pulls/111)

## [0.3.0] - 2020-06-11

### Fixed

- Copying not needed compiled files to the wheel distribution files. [#109](https://github.com/Stranger6667/jsonschema-rs/issues/109)

## [0.2.0] - 2020-06-11

### Added

- `JSONSchema.validate` method that raises `ValidationError` for invalid input. [#105](https://github.com/Stranger6667/jsonschema-rs/issues/105)

### Changed

- Public functions docstrings to support PyCharm skeletons generation. Functions signatures now have proper signatures (but untyped) in PyCharm. [#107](https://github.com/Stranger6667/jsonschema-rs/issues/107)
- Enable Link-Time Optimizations and set `codegen-units` to 1. [#104](https://github.com/Stranger6667/jsonschema-rs/issues/104)

## 0.1.0 - 2020-06-09
- Initial public release

[Unreleased]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.12.1...HEAD
[0.12.1]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.12.0...python-v0.12.1
[0.12.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.11.1...python-v0.12.0
[0.11.1]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.11.0...python-v0.11.1
[0.11.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.10.0...python-v0.11.0
[0.10.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.9.1...python-v0.10.0
[0.9.1]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.9.0...python-v0.9.1
[0.9.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.8.0...python-v0.9.0
[0.8.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.6.2...python-v0.8.0
[0.6.2]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.6.1...python-v0.6.2
[0.6.1]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.6.0...python-v0.6.1
[0.6.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.5.1...python-v0.6.0
[0.5.1]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.5.0...python-v0.5.1
[0.5.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.4.3...python-v0.5.0
[0.4.3]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.4.2...python-v0.4.3
[0.4.2]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.4.1...python-v0.4.2
[0.4.1]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.4.0...python-v0.4.1
[0.4.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.3.3...python-v0.4.0
[0.3.3]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.3.2...python-v0.3.3
[0.3.2]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.3.1...python-v0.3.2
[0.3.1]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.3.0...python-v0.3.1
[0.3.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.2.0...python-v0.3.0
[0.2.0]: https://github.com/Stranger6667/jsonschema-rs/compare/python-v0.1.0...python-v0.2.0
