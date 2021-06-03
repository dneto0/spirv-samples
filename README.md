# SPIR-V samples for WGSL

These samples are extracted from the unit tests for the SPIR-V reader in Tint.
See https://dawn.googlesource.com/tint/+/refs/heads/main/src/reader/spirv/

The original sources are distributed under the Apache 2.0 LICENSE.

There are over 1000 .spvasm files which can be assembled into SPIR-V binary
modules that should be convertable into valid WGSL.

Example:

   tint -format wgsl spvasm/SpvUnaryLogicalTest_LogicalNot_Scalar.spvasm

The examples work except for a handful of issues:
- crbug.com/tint/860: missing support for transpose
- crbug.com/tint/862: missing support for textureSampleCompareLevel
- crbug.com/tint/863: broken support for bool vector & and |
