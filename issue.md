---
title: Apply Patch Status 25734-RISCV_Refactor_and_cleanup_vsetvl_pass-1
---

## Apply Status
|Target|Status|
|---|---|
|Baseline hash: https://github.com/gcc-mirror/gcc/commit/77faa3e198a6b6f9a55a8010bef1c394d2e3cf8e|Failed|
|Tip of tree hash: https://github.com/gcc-mirror/gcc/commit/77faa3e198a6b6f9a55a8010bef1c394d2e3cf8e|Failed|

## Command
```
> git am ../patches/*.patch --whitespace=fix -q --3way
```
## Output
```
error: patch failed: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-21.c:20
error: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-21.c: patch does not apply
error: patch failed: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-23.c:7
error: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-23.c: patch does not apply
error: patch failed: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-71.c:6
error: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-71.c: patch does not apply
error: patch failed: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-89.c:11
error: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-89.c: patch does not apply
error: patch failed: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/imm_bb_prop-1.c:16
error: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/imm_bb_prop-1.c: patch does not apply
error: patch failed: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/vsetvl-13.c:4
error: gcc/testsuite/gcc.target/riscv/rvv/vsetvl/vsetvl-13.c: patch does not apply
error: Did you hand edit your patch?
It does not apply to blobs recorded in its index.
hint: Use 'git am --show-current-patch=diff' to see the failed patch
Patch failed at 0001 RISC-V: Refactor and cleanup vsetvl pass
When you have resolved this problem, run "git am --continue".
If you prefer to skip this patch, run "git am --skip" instead.
To restore the original branch and stop patching, run "git am --abort".
---
 gcc/config/riscv/riscv-vsetvl.cc              | 6621 ++++++++---------
