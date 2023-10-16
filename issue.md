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
 gcc/config/riscv/riscv-vsetvl.def             |  634 +-
 gcc/config/riscv/riscv-vsetvl.h               |  459 --
 .../gcc.target/riscv/rvv/base/scalar_move-1.c |    2 +-
 .../riscv/rvv/vsetvl/avl_single-104.c         |   35 +
 .../riscv/rvv/vsetvl/avl_single-105.c         |   23 +
 .../riscv/rvv/vsetvl/avl_single-21.c          |    5 +-
 .../riscv/rvv/vsetvl/avl_single-23.c          |    6 +-
 .../riscv/rvv/vsetvl/avl_single-46.c          |    3 +-
 .../riscv/rvv/vsetvl/avl_single-67.c          |    8 +-
 .../riscv/rvv/vsetvl/avl_single-68.c          |    9 +-
 .../riscv/rvv/vsetvl/avl_single-71.c          |   11 +-
 .../riscv/rvv/vsetvl/avl_single-89.c          |    8 +-
 .../riscv/rvv/vsetvl/avl_single-93.c          |    2 +-
 .../riscv/rvv/vsetvl/avl_single-95.c          |    2 +-
 .../riscv/rvv/vsetvl/avl_single-96.c          |    2 +-
 .../riscv/rvv/vsetvl/imm_bb_prop-1.c          |    7 +-
 .../gcc.target/riscv/rvv/vsetvl/pr109743-2.c  |    2 +-
 .../gcc.target/riscv/rvv/vsetvl/pr109773-1.c  |    2 +-
 .../riscv/rvv/{base => vsetvl}/pr111037-1.c   |    0
 .../riscv/rvv/{base => vsetvl}/pr111037-2.c   |    0
 .../gcc.target/riscv/rvv/vsetvl/pr111037-3.c  |   16 +
 .../gcc.target/riscv/rvv/vsetvl/pr111037-4.c  |   16 +
 .../riscv/rvv/vsetvl/vlmax_back_prop-25.c     |   10 +-
 .../riscv/rvv/vsetvl/vlmax_back_prop-26.c     |   10 +-
 .../riscv/rvv/vsetvl/vlmax_conflict-12.c      |    1 -
 .../riscv/rvv/vsetvl/vlmax_conflict-3.c       |    2 +-
 .../gcc.target/riscv/rvv/vsetvl/vsetvl-1-1.c  |   18 +
 .../gcc.target/riscv/rvv/vsetvl/vsetvl-1.c    |    2 +-
 .../gcc.target/riscv/rvv/vsetvl/vsetvl-13.c   |    4 +-
 .../gcc.target/riscv/rvv/vsetvl/vsetvl-18.c   |    4 +-
 .../gcc.target/riscv/rvv/vsetvl/vsetvl-23.c   |    2 +-
 32 files changed, 3247 insertions(+), 4679 deletions(-)
 create mode 100644 gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-104.c
 create mode 100644 gcc/testsuite/gcc.target/riscv/rvv/vsetvl/avl_single-105.c
 rename gcc/testsuite/gcc.target/riscv/rvv/{base => vsetvl}/pr111037-1.c (100%)
 rename gcc/testsuite/gcc.target/riscv/rvv/{base => vsetvl}/pr111037-2.c (100%)
 create mode 100644 gcc/testsuite/gcc.target/riscv/rvv/vsetvl/pr111037-3.c
 create mode 100644 gcc/testsuite/gcc.target/riscv/rvv/vsetvl/pr111037-4.c
 create mode 100644 gcc/testsuite/gcc.target/riscv/rvv/vsetvl/vsetvl-1-1.c

--
2.36.3

diff --git a/gcc/config/riscv/riscv-vsetvl.cc b/gcc/config/riscv/riscv-vsetvl.cc
index 4b06d93e7f9..f636b8e68e3 100644
--- a/gcc/config/riscv/riscv-vsetvl.cc
+++ b/gcc/config/riscv/riscv-vsetvl.cc
@@ -18,60 +18,47 @@ You should have received a copy of the GNU General Public License
 along with GCC; see the file COPYING3.  If not see
 <http://www.gnu.org/licenses/>.  */

-/*  This pass is to Set VL/VTYPE global status for RVV instructions
-    that depend on VL and VTYPE registers by Lazy code motion (LCM).
-
-    Strategy:
-
-    -  Backward demanded info fusion within block.
-
-    -  Lazy code motion (LCM) based demanded info backward propagation.
-
-    -  RTL_SSA framework for def-use, PHI analysis.
-
-    -  Lazy code motion (LCM) for global VL/VTYPE optimization.
-
-    Assumption:
-
-    -  Each avl operand is either an immediate (must be in range 0 ~ 31) or reg.
-
-    This pass consists of 5 phases:
-
-    -  Phase 1 - compute VL/VTYPE demanded information within each block
-       by backward data-flow analysis.
-
-    -  Phase 2 - Emit vsetvl instructions within each basic block according to
-       demand, compute and save ANTLOC && AVLOC of each block.
-
-    -  Phase 3 - LCM Earliest-edge baseed VSETVL demand fusion.
-
-    -  Phase 4 - Lazy code motion including: compute local properties,
-       pre_edge_lcm and vsetvl insertion && delete edges for LCM results.
-
-    -  Phase 5 - Cleanup AVL operand of RVV instruction since it will not be
-       used any more and VL operand of VSETVL instruction if it is not used by
-       any non-debug instructions.
-
-    -  Phase 6 - DF based post VSETVL optimizations.
-
-    Implementation:
-
-    -  The subroutine of optimize == 0 is simple_vsetvl.
-       This function simplily vsetvl insertion for each RVV
-       instruction. No optimization.
-
-    -  The subroutine of optimize > 0 is lazy_vsetvl.
-       This function optimize vsetvl insertion process by
-       lazy code motion (LCM) layering on RTL_SSA.
-
-    -  get_avl (), get_insn (), get_avl_source ():
-
-	1. get_insn () is the current instruction, find_access (get_insn
-   ())->def is the same as get_avl_source () if get_insn () demand VL.
-	2. If get_avl () is non-VLMAX REG, get_avl () == get_avl_source
-   ()->regno ().
-	3. get_avl_source ()->regno () is the REGNO that we backward propagate.
- */
+/* The values of the vl and vtype registers will affect the behavior of RVV
+   insns. That is, when we need to execute an RVV instruction, we need to set
+   the correct vl and vtype values by executing the vsetvl instruction before.
+   Executing the fewest number of vsetvl instructions while keeping the behavior
+   the same is the problem this pass is trying to solve. This vsetvl pass is
+   divided into 5 phases:
+
+     - Phase 1 (fuse local vsetvl infos): traverses each Basic Block, parses
+       each instruction in it that affects vl and vtype state and generates an
+       array of vsetvl_info objects. Then traverse the vsetvl_info array from
+       front to back and perform fusion according to the fusion rules. The fused
+       vsetvl infos are stored in the vsetvl_block_info object's `infos` field.
+
+     - Phase 2 (earliest fuse global vsetvl infos): The header_info and
+       footer_info of vsetvl_block_info are used as expressions, and the
+       earliest of each expression is computed. Based on the earliest
+       information, try to lift up the corresponding vsetvl info to the src
+       basic block of the edge (mainly to reduce the total number of vsetvl
+       instructions, this uplift will cause some execution paths to execute
+       vsetvl instructions that shouldn't be there).
+
+     - Phase 3 (pre global vsetvl info): The header_info and footer_info of
+       vsetvl_block_info are used as expressions, and the LCM algorithm is used
+       to compute the header_info that needs to be deleted and the one that
+       needs to be inserted in some edges.
+
+     - Phase 4 (emit vsetvl insns) : Based on the fusion result of Phase 1 and
+       the deletion and insertion information of Phase 3, the mandatory vsetvl
+       instruction insertion, modification and deletion are performed.
+
+     - Phase 5 (cleanup): Clean up the avl operand in the RVV operator
+       instruction and cleanup the unused dest operand of the vsetvl insn.
+
+     After the Phase 1 a virtual CFG of vsetvl_info is generated. The virtual
+     basic block is represented by vsetvl_block_info, and the virtual vsetvl
+     statements inside are represented by vsetvl_info. The later phases 2 and 3
+     are constantly modifying and adjusting this virtual CFG. Phase 4 performs
+     insertion, modification and deletion of vsetvl instructions based on the
+     optimized virtual CFG. The Phase 1, 2 and 3 do not involve modifications to
+     the RTL.
+*/

 #define IN_TARGET_CODE 1
 #define INCLUDE_ALGORITHM
@@ -98,61 +85,180 @@ along with GCC; see the file COPYING3.  If not see
 #include "predict.h"
 #include "profile-count.h"
 #include "gcse.h"
-#include "riscv-vsetvl.h"

 using namespace rtl_ssa;
 using namespace riscv_vector;

-static CONSTEXPR const unsigned ALL_SEW[] = {8, 16, 32, 64};
-static CONSTEXPR const vlmul_type ALL_LMUL[]
-  = {LMUL_1, LMUL_2, LMUL_4, LMUL_8, LMUL_F8, LMUL_F4, LMUL_F2};
+/* Set the bitmap DST to the union of SRC of predecessors of
+   basic block B.
+   It's a bit different from bitmap_union_of_preds in cfganal.cc. This function
+   takes into account the case where pred is ENTRY basic block. The main reason
+   for this difference is to make it easier to insert some special value into
+   the ENTRY base block. For example, vsetvl_info with a status of UNKNOW.  */
+static void
+bitmap_union_of_preds_with_entry (sbitmap dst, sbitmap *src, basic_block b)
+{
+  unsigned int set_size = dst->size;
+  edge e;
+  unsigned ix;
+
+  for (ix = 0; ix < EDGE_COUNT (b->preds); ix++)
+    {
+      e = EDGE_PRED (b, ix);
+      bitmap_copy (dst, src[e->src->index]);
+      break;
+    }

-DEBUG_FUNCTION void
-debug (const vector_insn_info *info)
+  if (ix == EDGE_COUNT (b->preds))
+    bitmap_clear (dst);
+  else
+    for (ix++; ix < EDGE_COUNT (b->preds); ix++)
+      {
+	unsigned int i;
+	SBITMAP_ELT_TYPE *p, *r;
+
+	e = EDGE_PRED (b, ix);
+	p = src[e->src->index]->elms;
+	r = dst->elms;
+	for (i = 0; i < set_size; i++)
+	  *r++ |= *p++;
+      }
+}
+
+/* Compute the reaching defintion in and out based on the gen and KILL
+   informations in each Base Blocks.
+   This function references the compute_avaiable implementation in lcm.cc  */
+static void
+compute_reaching_defintion (sbitmap *gen, sbitmap *kill, sbitmap *in,
+			    sbitmap *out)
 {
-  info->dump (stderr);
+  edge e;
+  basic_block *worklist, *qin, *qout, *qend, bb;
+  unsigned int qlen;
+  edge_iterator ei;
+
+  /* Allocate a worklist array/queue.  Entries are only added to the
+     list if they were not already on the list.  So the size is
+     bounded by the number of basic blocks.  */
+  qin = qout = worklist
+    = XNEWVEC (basic_block, n_basic_blocks_for_fn (cfun) - NUM_FIXED_BLOCKS);
+
+  /* Put every block on the worklist; this is necessary because of the
+     optimistic initialization of AVOUT above.  Use reverse postorder
+     to make the forward dataflow problem require less iterations.  */
+  int *rpo = XNEWVEC (int, n_basic_blocks_for_fn (cfun) - NUM_FIXED_BLOCKS);
+  int n = pre_and_rev_post_order_compute_fn (cfun, NULL, rpo, false);
+  for (int i = 0; i < n; ++i)
+    {
+      bb = BASIC_BLOCK_FOR_FN (cfun, rpo[i]);
+      *qin++ = bb;
+      bb->aux = bb;
+    }
+  free (rpo);
+
+  qin = worklist;
+  qend = &worklist[n_basic_blocks_for_fn (cfun) - NUM_FIXED_BLOCKS];
+  qlen = n_basic_blocks_for_fn (cfun) - NUM_FIXED_BLOCKS;
+
+  /* Mark blocks which are successors of the entry block so that we
+     can easily identify them below.  */
+  FOR_EACH_EDGE (e, ei, ENTRY_BLOCK_PTR_FOR_FN (cfun)->succs)
+    e->dest->aux = ENTRY_BLOCK_PTR_FOR_FN (cfun);
+
+  /* Iterate until the worklist is empty.  */
+  while (qlen)
+    {
+      /* Take the first entry off the worklist.  */
+      bb = *qout++;
+      qlen--;
+
+      if (qout >= qend)
+	qout = worklist;
+
+      /* Do not clear the aux field for blocks which are successors of the
+	 ENTRY block.  That way we never add then to the worklist again.  */
+      if (bb->aux != ENTRY_BLOCK_PTR_FOR_FN (cfun))
+	bb->aux = NULL;
+
+      bitmap_union_of_preds_with_entry (in[bb->index], out, bb);
+
+      if (bitmap_ior_and_compl (out[bb->index], gen[bb->index], in[bb->index],
+				kill[bb->index]))
+	/* If the out state of this block changed, then we need
+	   to add the successors of this block to the worklist
+	   if they are not already on the worklist.  */
+	FOR_EACH_EDGE (e, ei, bb->succs)
+	  if (!e->dest->aux && e->dest != EXIT_BLOCK_PTR_FOR_FN (cfun))
+	    {
+	      *qin++ = e->dest;
+	      e->dest->aux = e;
+	      qlen++;
+
+	      if (qin >= qend)
+		qin = worklist;
+	    }
+    }
+
+  clear_aux_for_edges ();
+  clear_aux_for_blocks ();
+  free (worklist);
 }

-DEBUG_FUNCTION void
-debug (const vector_infos_manager *info)
+/* Classification of vsetvl instruction.  */
+enum vsetvl_type
 {
-  info->dump (stderr);
-}
+  VSETVL_NORMAL,
+  VSETVL_VTYPE_CHANGE_ONLY,
+  VSETVL_DISCARD_RESULT,
+  NUM_VSETVL_TYPE
+};

-static bool
-vlmax_avl_p (rtx x)
+enum emit_type
 {
-  return x && rtx_equal_p (x, RVV_VLMAX);
+  /* emit_insn directly.  */
+  EMIT_DIRECT,
+  EMIT_BEFORE,
+  EMIT_AFTER,
+};
+
+/* dump helper functions */
+static const char *
+vlmul_to_str (vlmul_type vlmul)
+{
+  switch (vlmul)
+    {
+    case LMUL_1:
+      return "m1";
+    case LMUL_2:
+      return "m2";
+    case LMUL_4:
+      return "m4";
+    case LMUL_8:
+      return "m8";
+    case LMUL_RESERVED:
+      return "INVALID LMUL";
+    case LMUL_F8:
+      return "mf8";
+    case LMUL_F4:
+      return "mf4";
+    case LMUL_F2:
+      return "mf2";
+
+    default:
+      gcc_unreachable ();
+    }
 }

-static bool
-vlmax_avl_insn_p (rtx_insn *rinsn)
+static const char *
+policy_to_str (bool agnostic_p)
 {
-  return (INSN_CODE (rinsn) == CODE_FOR_vlmax_avlsi
-	  || INSN_CODE (rinsn) == CODE_FOR_vlmax_avldi);
+  return agnostic_p ? "agnostic" : "undisturbed";
 }

-/* Return true if the block is a loop itself:
-	  local_dem
-	     __________
-	 ____|____     |
-	|        |     |
-	|________|     |
-	     |_________|
-	  reaching_out
-*/
 static bool
-loop_basic_block_p (const basic_block cfg_bb)
+vlmax_avl_p (rtx x)
 {
-  if (JUMP_P (BB_END (cfg_bb)) && any_condjump_p (BB_END (cfg_bb)))
-    {
-      edge e;
-      edge_iterator ei;
-      FOR_EACH_EDGE (e, ei, cfg_bb->succs)
-	if (e->dest->index == cfg_bb->index)
-	  return true;
-    }
-  return false;
+  return x && rtx_equal_p (x, RVV_VLMAX);
 }

 /* Return true if it is an RVV instruction depends on VTYPE global
@@ -171,13 +277,6 @@ has_vl_op (rtx_insn *rinsn)
   return recog_memoized (rinsn) >= 0 && get_attr_has_vl_op (rinsn);
 }

-/* Is this a SEW value that can be encoded into the VTYPE format.  */
-static bool
-valid_sew_p (size_t sew)
-{
-  return exact_log2 (sew) && sew >= 8 && sew <= 64;
-}
-
 /* Return true if the instruction ignores VLMUL field of VTYPE.  */
 static bool
 ignore_vlmul_insn_p (rtx_insn *rinsn)
@@ -223,7 +322,7 @@ vector_config_insn_p (rtx_insn *rinsn)
 static bool
 vsetvl_insn_p (rtx_insn *rinsn)
 {
-  if (!vector_config_insn_p (rinsn))
+  if (!rinsn || !vector_config_insn_p (rinsn))
     return false;
   return (INSN_CODE (rinsn) == CODE_FOR_vsetvldi
 	  || INSN_CODE (rinsn) == CODE_FOR_vsetvlsi);
@@ -239,34 +338,13 @@ vsetvl_discard_result_insn_p (rtx_insn *rinsn)
 	  || INSN_CODE (rinsn) == CODE_FOR_vsetvl_discard_resultsi);
 }

-/* Return true if it is vsetvl zero, zero.  */
-static bool
-vsetvl_vtype_change_only_p (rtx_insn *rinsn)
-{
-  if (!vector_config_insn_p (rinsn))
-    return false;
-  return (INSN_CODE (rinsn) == CODE_FOR_vsetvl_vtype_change_only);
-}
-
-static bool
-after_or_same_p (const insn_info *insn1, const insn_info *insn2)
-{
-  return insn1->compare_with (insn2) >= 0;
-}
-
 static bool
 real_insn_and_same_bb_p (const insn_info *insn, const bb_info *bb)
 {
   return insn != nullptr && insn->is_real () && insn->bb () == bb;
 }

-static bool
-before_p (const insn_info *insn1, const insn_info *insn2)
-{
-  return insn1->compare_with (insn2) < 0;
-}
-
-/* Helper function to get VL operand.  */
+/* Helper function to get VL operand for VLMAX insn.  */
 static rtx
 get_vl (rtx_insn *rinsn)
 {
@@ -278,224 +356,6 @@ get_vl (rtx_insn *rinsn)
   return SET_DEST (XVECEXP (PATTERN (rinsn), 0, 0));
 }

-/* An "anticipatable occurrence" is one that is the first occurrence in the
-   basic block, the operands are not modified in the basic block prior
-   to the occurrence and the output is not used between the start of
-   the block and the occurrence.
-
-   For VSETVL instruction, we have these following formats:
-     1. vsetvl zero, rs1.
-     2. vsetvl zero, imm.
-     3. vsetvl rd, rs1.
-
-   So base on these circumstances, a DEM is considered as a local anticipatable
-   occurrence should satisfy these following conditions:
-
-     1). rs1 (avl) are not modified in the basic block prior to the VSETVL.
-     2). rd (vl) are not modified in the basic block prior to the VSETVL.
-     3). rd (vl) is not used between the start of the block and the occurrence.
-
-   Note: We don't need to check VL/VTYPE here since DEM is UNKNOWN if VL/VTYPE
-	 is modified prior to the occurrence. This case is already considered as
-	 a non-local anticipatable occurrence.
-*/
-static bool
-anticipatable_occurrence_p (const bb_info *bb, const vector_insn_info dem)
-{
-  insn_info *insn = dem.get_insn ();
-  /* The only possible operand we care of VSETVL is AVL.  */
-  if (dem.has_avl_reg ())
-    {
-      /* rs1 (avl) are not modified in the basic block prior to the VSETVL.  */
-      rtx avl = dem.get_avl_or_vl_reg ();
-      if (dem.dirty_p ())
-	{
-	  gcc_assert (!vsetvl_insn_p (insn->rtl ()));
-
-	  /* Earliest VSETVL will be inserted at the end of the block.  */
-	  for (const insn_info *i : bb->real_nondebug_insns ())
-	    {
-	      /* rs1 (avl) are not modified in the basic block prior to the
-		 VSETVL.  */
-	      if (find_access (i->defs (), REGNO (avl)))
-		return false;
-	      if (vlmax_avl_p (dem.get_avl ()))
-		{
-		  /* rd (avl) is not used between the start of the block and
-		     the occurrence. Note: Only for Dirty and VLMAX-avl.  */
-		  if (find_access (i->uses (), REGNO (avl)))
-		    return false;
-		}
-	    }
-
-	  return true;
-	}
-      else if (!vlmax_avl_p (avl))
-	{
-	  set_info *set = dem.get_avl_source ();
-	  /* If it's undefined, it's not anticipatable conservatively.  */
-	  if (!set)
-	    return false;
-	  if (real_insn_and_same_bb_p (set->insn (), bb)
-	      && before_p (set->insn (), insn))
-	    return false;
-	  for (insn_info *i = insn->prev_nondebug_insn ();
-	       real_insn_and_same_bb_p (i, bb); i = i->prev_nondebug_insn ())
-	    {
-	      /* rs1 (avl) are not modified in the basic block prior to the
-		 VSETVL.  */
-	      if (find_access (i->defs (), REGNO (avl)))
-		return false;
-	    }
-	}
-    }
-
-  /* rd (vl) is not used between the start of the block and the occurrence.  */
-  if (vsetvl_insn_p (insn->rtl ()))
-    {
-      rtx dest = get_vl (insn->rtl ());
-      for (insn_info *i = insn->prev_nondebug_insn ();
-	   real_insn_and_same_bb_p (i, bb); i = i->prev_nondebug_insn ())
-	{
-	  /* rd (vl) is not used between the start of the block and the
-	   * occurrence.  */
-	  if (find_access (i->uses (), REGNO (dest)))
-	    return false;
-	  /* rd (vl) are not modified in the basic block prior to the VSETVL. */
-	  if (find_access (i->defs (), REGNO (dest)))
-	    return false;
-	}
-    }
-
-  return true;
-}
-
-/* An "available occurrence" is one that is the last occurrence in the
-   basic block and the operands are not modified by following statements in
-   the basic block [including this insn].
-
-   For VSETVL instruction, we have these following formats:
-     1. vsetvl zero, rs1.
-     2. vsetvl zero, imm.
-     3. vsetvl rd, rs1.
-
-   So base on these circumstances, a DEM is considered as a local available
-   occurrence should satisfy these following conditions:
-
-     1). rs1 (avl) are not modified by following statements in
-	 the basic block.
-     2). rd (vl) are not modified by following statements in
-	 the basic block.
-
-   Note: We don't need to check VL/VTYPE here since DEM is UNKNOWN if VL/VTYPE
-	 is modified prior to the occurrence. This case is already considered as
-	 a non-local available occurrence.
-*/
-static bool
-available_occurrence_p (const bb_info *bb, const vector_insn_info dem)
-{
-  insn_info *insn = dem.get_insn ();
-  /* The only possible operand we care of VSETVL is AVL.  */
-  if (dem.has_avl_reg ())
-    {
-      if (!vlmax_avl_p (dem.get_avl ()))
-	{
-	  rtx dest = NULL_RTX;
-	  insn_info *i = insn;
-	  if (vsetvl_insn_p (insn->rtl ()))
-	    {
-	      dest = get_vl (insn->rtl ());
-	      /* For user vsetvl a2, a2 instruction, we consider it as
-		 available even though it modifies "a2".  */
-	      i = i->next_nondebug_insn ();
-	    }
-	  for (; real_insn_and_same_bb_p (i, bb); i = i->next_nondebug_insn ())
-	    {
-	      if (read_vl_insn_p (i->rtl ()))
-		continue;
-	      /* rs1 (avl) are not modified by following statements in
-		 the basic block.  */
-	      if (find_access (i->defs (), REGNO (dem.get_avl ())))
-		return false;
-	      /* rd (vl) are not modified by following statements in
-		 the basic block.  */
-	      if (dest && find_access (i->defs (), REGNO (dest)))
-		return false;
-	    }
-	}
-    }
-  return true;
-}
