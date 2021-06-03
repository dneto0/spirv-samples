# SPIR-V samples for WGSL

These samples are extracted from the unit tests for the SPIR-V reader in [Tint](https://dawn.googlesource.com/tint).
See [the SPIR-V reader source code](https://dawn.googlesource.com/tint/+/refs/heads/main/src/reader/spirv/).

The original sources are distributed under the Apache 2.0 LICENSE.

I don't plan to take contributions.  Instead, contribute tests to upstream
projects such as Tint.  You can file a Tint bug at [https://crbug.com/tint](https://crbug.com/tint).

There are over 1000 .spvasm files which can be assembled into SPIR-V binary
modules that should be convertable into valid WGSL.

Example:

    tint --format wgsl spvasm/SpvUnaryLogicalTest_LogicalNot_Scalar.spvasm

produces the following output:

```
[[stage(vertex)]]
fn main() {
  let x_1 : bool = !(true);
  return;
}
```

The examples work in Tint except for a handful of known issues:
- [tint:860](https://crbug.com/tint/860): missing support for transpose
- [tint:862](https://crbug.com/tint/862): missing support for textureSampleCompareLevel
- [tint:863](https://crbug.com/tint/863): broken support for bool vector & and |

The SPIR-V is valid for SPIR-V 1.0, but some examples use:
- `SPV_KHR_storage_buffer_storage_class`
- StorageBuffer storage class (without extension)
- `SPV_KHR_non_semantic_info`
- `SPV_KHR_vulkan_memory_model`
