# Change log

See [upgrade notes][upgrade-notes] for helpful information when upgrading from previous versions.

[upgrade-notes]: upgrade-notes.md

**Important notes**:

- YAML resources will require an `apiVersion` from PSRule v2. [#648](https://github.com/microsoft/PSRule/issues/648)

## Unreleased

## v1.2.0

What's changed since v1.1.0:

- Engine features:
  - Added support for extensibility with conventions. [#650](https://github.com/microsoft/PSRule/issues/650)
    - Conventions provide an extensibility point within PSRule to execute actions within the pipeline.
    - A convention can expose `Begin`, `Process`, and `End` blocks.
    - In additional to within rules `$PSRule.Data` can be accessed from `Begin` and `Process` blocks.
    - See [about_PSRule_Conventions] for details.
  - Added support for object expansion with conventions. [#661](https://github.com/microsoft/PSRule/issues/661)
    - Use the `$PSRule.Import` method to import child source objects into the pipeline.
    - See [about_PSRule_Variables] for details.
  - Added support for complex pre-conditions with selectors. [#649](https://github.com/microsoft/PSRule/issues/649)
    - See [about_PSRule_Selectors] for details.
- General improvements:
  - Added support for preferring automatic binding over custom binding configurations. [#670](https://github.com/microsoft/PSRule/issues/670)
    - Added the `Binding.PreferTargetInfo` option to prefer target info specified by the object.
    - See [about_PSRule_Options] for details.
  - Added strong apiVersion to resource types. [#647](https://github.com/microsoft/PSRule/issues/647)
    - Resource schemas now support an `apiVersion` field.
    - The `apiVersion` field is optional but recommended.
    - Resources without a `apiVersion` field will not be supported from PSRule v2.
    - Added warning to flag baseline without `apiVersion` set.
  - Added support for detecting files headers from additional file extensions using `FileHeader`. [#664](https://github.com/microsoft/PSRule/issues/664)
    - Added `.bicep`, `.csx`, `.jsx`, `.groovy`, `.java`, `.json`, `.jsonc`,
    `.scala`, `.rb`, `.bat`, `.cmd`.
    - Added support for `Jenkinsfile` and `Dockerfile` without an extension.
    - See [about_PSRule_Assert] for details.
  - Added support for automatic type binding with files that do not have a file extension. [#665](https://github.com/microsoft/PSRule/issues/665)
- Bug fixes:
  - Fixed dependent rule execution is skipped for consequent input objects. [#657](https://github.com/microsoft/PSRule/issues/657)

What's changed since pre-release v1.2.0-B2103043:

- No additional changes.

## v1.2.0-B2103043 (pre-release)

What's changed since pre-release v1.2.0-B2103031:

- Engine features:
  - Added support for complex pre-conditions with selectors. [#649](https://github.com/microsoft/PSRule/issues/649)
- General improvements:
  - Added support for preferring automatic binding over custom binding configurations. [#670](https://github.com/microsoft/PSRule/issues/670)
    - Added the `Binding.PreferTargetInfo` option to prefer target info specified by the object.
    - See [about_PSRule_Options] for details.
  - Added strong apiVersion to resource types. [#647](https://github.com/microsoft/PSRule/issues/647)
    - Resource schemas now support an `apiVersion` field.
    - The `apiVersion` field is optional but recommended.
    - Resources without a `apiVersion` field will not be supported from PSRule v2.
    - Added warning to flag baseline without `apiVersion` set.

## 1.2.0-B2103031 (pre-release)

What's changed since pre-release v1.2.0-B2103023:

- General improvements:
  - Added support for detecting files headers from additional file extensions. [#664](https://github.com/microsoft/PSRule/issues/664)
    - Added `.bicep`, `.csx`, `.jsx`, `.groovy`, `.java`, `.json`, `.jsonc`,
    `.scala`, `.rb`, `.bat`, `.cmd`.
    - Added support for `Jenkinsfile` and `Dockerfile` without an extension.
    - See [about_PSRule_Assert] for details.
  - Added support for automatic type binding with files that do not have a file extension. [#665](https://github.com/microsoft/PSRule/issues/665)

## v1.2.0-B2103023 (pre-release)

What's changed since pre-release v1.2.0-B2103016:

- Engine features:
  - Added support for object expansion with conventions. [#661](https://github.com/microsoft/PSRule/issues/661)
    - Use the `$PSRule.Import` method to import child source objects into the pipeline.
    - See [about_PSRule_Variables] for details.

## v1.2.0-B2103016 (pre-release)

What's changed since pre-release v1.2.0-B2103008:

- Bug fixes:
  - Fixed dependent rule execution is skipped for consequent input objects. [#657](https://github.com/microsoft/PSRule/issues/657)

## v1.2.0-B2103008 (pre-release)

What's changed since v1.1.0:

- Engine features:
  - Added support for extensibility with conventions. [#650](https://github.com/microsoft/PSRule/issues/650)
    - Conventions provide an extensibility point within PSRule to execute actions within the pipeline.
    - A convention can expose `Begin`, `Process`, and `End` blocks.
    - In additional to within rules `$PSRule.Data` can be accessed from `Begin` and `Process` blocks.
    - See [about_PSRule_Conventions] for details.

## v1.1.0

What's changed since v1.0.3:

- Engine features:
  - Added assertion helpers. [#640](https://github.com/microsoft/PSRule/issues/640)
    - Added `NotHasField` to check object does not have any of the specified fields.
    - Added `Null` to check field value is null.
    - Added `NotNull` to check field value is not null.
    - See [about_PSRule_Assert] for details.
  - Added type assertion helpers. [#635](https://github.com/microsoft/PSRule/issues/635)
    - Added `IsNumeric` to check field value is a numeric types.
    - Added `IsInteger` to check field value is an integer types.
    - Added `IsBoolean` to check field value is a boolean.
    - Added `IsArray` to check field value is an array.
    - Added `IsString` to check field value is a string.
    - Added `TypeOf` to check field value is a specified type.
    - See [about_PSRule_Assert] for details.
  - Added content helpers. [#637](https://github.com/microsoft/PSRule/issues/637)
    - Added `$PSRule.GetContentFirstOrDefault` to get content and return the first object.
    - Added `$PSRule.GetContentField` to get the field from content objects.
    - See [about_PSRule_Variables] for details.
- General improvements:
  - Updated `HasJsonSchema` assertion helper. [#636](https://github.com/microsoft/PSRule/issues/636)
    - The URI scheme can optionally be ignored for `http://` or `https://` URIs.
    - The fragment `#` is ignored.
    - See [about_PSRule_Assert] for details.
  - Added support for `-Outcome` and `-As` to produce filtered output from `Assert-PSRule`. [#643](https://github.com/microsoft/PSRule/issues/643)
    - Configure `Output.As` with `Summary` to produce summarized results per object.
    - Configure `Output.Outcome` to limit output to `Fail` or `Error`.
    - See [Assert-PSRule] for details.

What's changed since pre-release v1.1.0-B2102029:

- No additional changes.

## v1.1.0-B2102029 (pre-release)

What's changed since pre-release v1.1.0-B2102024:

- General improvements:
  - Added support for `-Outcome` and `-As` to produce filtered output from `Assert-PSRule`. [#643](https://github.com/microsoft/PSRule/issues/643)
    - Configure `Output.As` with `Summary` to produce summarized results per object.
    - Configure `Output.Outcome` to limit output to `Fail` or `Error`.
    - See [Assert-PSRule] for details.

## v1.1.0-B2102024 (pre-release)

What's changed since pre-release v1.1.0-B2102019:

- Engine features:
  - Added assertion helpers. [#640](https://github.com/microsoft/PSRule/issues/640)
    - Added `NotHasField` to check object does not have any of the specified fields.
    - Added `Null` to check field value is null.
    - Added `NotNull` to check field value is not null.
    - See [about_PSRule_Assert] for details.

## v1.1.0-B2102019 (pre-release)

What's changed since v1.0.3:

- Engine features:
  - Added type assertion helpers. [#635](https://github.com/microsoft/PSRule/issues/635)
    - Added `IsNumeric` to check field value is a numeric types.
    - Added `IsInteger` to check field value is an integer types.
    - Added `IsBoolean` to check field value is a boolean.
    - Added `IsArray` to check field value is an array.
    - Added `IsString` to check field value is a string.
    - Added `TypeOf` to check field value is a specified type.
    - See [about_PSRule_Assert] for details.
  - Added content helpers. [#637](https://github.com/microsoft/PSRule/issues/637)
    - Added `$PSRule.GetContentFirstOrDefault` to get content and return the first object.
    - Added `$PSRule.GetContentField` to get the field from content objects.
    - See [about_PSRule_Variables] for details.
- General improvements:
  - Updated `HasJsonSchema` assertion helper. [#636](https://github.com/microsoft/PSRule/issues/636)
    - The URI scheme can optionally be ignored for `http://` or `https://` URIs.
    - The fragment `#` is ignored.
    - See [about_PSRule_Assert] for details.

## v1.0.3

What's changed since v1.0.2:

- Bug fixes:
  - Fixed reason reported fields for `HasField` and `HasFields` assertion helpers. [#632](https://github.com/microsoft/PSRule/issues/632)

## v1.0.2

What's changed since v1.0.1:

- Engineering:
  - Bump Manatee.Json from 13.0.4 to 13.0.5. [#619](https://github.com/microsoft/PSRule/pull/619)
- Bug fixes:
  - Fixed `GetContent` processing of `InputFileInfo`. [#625](https://github.com/microsoft/PSRule/issues/625)
  - Fixed null reference of rule reason with wide output. [#626](https://github.com/microsoft/PSRule/issues/626)
  - Fixed markdown help handling of inline code blocks with `[`. [#627](https://github.com/microsoft/PSRule/issues/627)
  - Fixed markdown help inclusion of fenced code blocks in notes and description. [#628](https://github.com/microsoft/PSRule/issues/628)

## v1.0.1

What's changed since v1.0.0:

- Bug fixes:
  - Fixed module source key has already been added. [#608](https://github.com/microsoft/PSRule/issues/608)

## v1.0.0

What's changed since v0.22.0:

- General improvements:
  - Added rule help link in failed `Assert-PSRule` output. [#595](https://github.com/microsoft/PSRule/issues/595)
- Engineering:
  - **Breaking change**: Removed deprecated `$Rule` properties. [#495](https://github.com/microsoft/PSRule/pull/495)
  - Bump Manatee.Json from 13.0.3 to 13.0.4. [#591](https://github.com/microsoft/PSRule/pull/591)

What's changed since pre-release v1.0.0-B2011028:

- No additional changes.

## v1.0.0-B2011028 (pre-release)

What's changed since v0.22.0:

- General improvements:
  - Added rule help link in failed `Assert-PSRule` output. [#595](https://github.com/microsoft/PSRule/issues/595)
- Engineering:
  - **Breaking change**: Removed deprecated `$Rule` properties. [#495](https://github.com/microsoft/PSRule/pull/495)
  - Bump Manatee.Json from 13.0.3 to 13.0.4. [#591](https://github.com/microsoft/PSRule/pull/591)

[Assert-PSRule]: commands/PSRule/en-US/Assert-PSRule.md
[about_PSRule_Assert]: concepts/PSRule/en-US/about_PSRule_Assert.md
[about_PSRule_Options]: concepts/PSRule/en-US/about_PSRule_Options.md
[about_PSRule_Variables]: concepts/PSRule/en-US/about_PSRule_Variables.md
[about_PSRule_Conventions]: concepts/PSRule/en-US/about_PSRule_Conventions.md
[about_PSRule_Selectors]: concepts/PSRule/en-US/about_PSRule_Selectors.md