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
-
-static bool
-insn_should_be_added_p (const insn_info *insn, unsigned int types)
-{
-  if (insn->is_real () && (types & REAL_SET))
-    return true;
-  if (insn->is_phi () && (types & PHI_SET))
-    return true;
-  if (insn->is_bb_head () && (types & BB_HEAD_SET))
-    return true;
-  if (insn->is_bb_end () && (types & BB_END_SET))
-    return true;
-  return false;
-}
-
-/* Recursively find all define instructions. The kind of instruction is
-   specified by the DEF_TYPE.  */
-static hash_set<set_info *>
-get_all_sets (phi_info *phi, unsigned int types)
-{
-  hash_set<set_info *> insns;
-  auto_vec<phi_info *> work_list;
-  hash_set<phi_info *> visited_list;
-  if (!phi)
-    return hash_set<set_info *> ();
-  work_list.safe_push (phi);
-
-  while (!work_list.is_empty ())
-    {
-      phi_info *phi = work_list.pop ();
-      visited_list.add (phi);
-      for (use_info *use : phi->inputs ())
-	{
-	  def_info *def = use->def ();
-	  set_info *set = safe_dyn_cast<set_info *> (def);
-	  if (!set)
-	    return hash_set<set_info *> ();
-
-	  gcc_assert (!set->insn ()->is_debug_insn ());
-
-	  if (insn_should_be_added_p (set->insn (), types))
-	    insns.add (set);
-	  if (set->insn ()->is_phi ())
-	    {
-	      phi_info *new_phi = as_a<phi_info *> (set);
-	      if (!visited_list.contains (new_phi))
-		work_list.safe_push (new_phi);
-	    }
-	}
-    }
-  return insns;
-}
-
-static hash_set<set_info *>
-get_all_sets (set_info *set, bool /* get_real_inst */ real_p,
-	      bool /*get_phi*/ phi_p, bool /* get_function_parameter*/ param_p)
-{
-  if (real_p && phi_p && param_p)
-    return get_all_sets (safe_dyn_cast<phi_info *> (set),
-			 REAL_SET | PHI_SET | BB_HEAD_SET | BB_END_SET);
-
-  else if (real_p && param_p)
-    return get_all_sets (safe_dyn_cast<phi_info *> (set),
-			 REAL_SET | BB_HEAD_SET | BB_END_SET);
-
-  else if (real_p)
-    return get_all_sets (safe_dyn_cast<phi_info *> (set), REAL_SET);
-  return hash_set<set_info *> ();
-}
-
 /* Helper function to get AVL operand.  */
 static rtx
 get_avl (rtx_insn *rinsn)
@@ -511,15 +371,6 @@ get_avl (rtx_insn *rinsn)
   return recog_data.operand[get_attr_vl_op_idx (rinsn)];
 }

-static set_info *
-get_same_bb_set (hash_set<set_info *> &sets, const basic_block cfg_bb)
-{
-  for (set_info *set : sets)
-    if (set->bb ()->cfg_bb () == cfg_bb)
-      return set;
-  return nullptr;
-}
-
 /* Helper function to get SEW operand. We always have SEW value for
    all RVV instructions that have VTYPE OP.  */
 static uint8_t
@@ -589,365 +440,186 @@ has_vector_insn (function *fn)
   return false;
 }

-/* Emit vsetvl instruction.  */
-static rtx
-gen_vsetvl_pat (enum vsetvl_type insn_type, const vl_vtype_info &info, rtx vl)
+static vlmul_type
+calculate_vlmul (unsigned int sew, unsigned int ratio)
 {
-  rtx avl = info.get_avl ();
-  /* if optimization == 0 and the instruction is vmv.x.s/vfmv.f.s,
-     set the value of avl to (const_int 0) so that VSETVL PASS will
-     insert vsetvl correctly.*/
-  if (info.has_avl_no_reg ())
-    avl = GEN_INT (0);
-  rtx sew = gen_int_mode (info.get_sew (), Pmode);
-  rtx vlmul = gen_int_mode (info.get_vlmul (), Pmode);
-  rtx ta = gen_int_mode (info.get_ta (), Pmode);
-  rtx ma = gen_int_mode (info.get_ma (), Pmode);
-
-  if (insn_type == VSETVL_NORMAL)
-    {
-      gcc_assert (vl != NULL_RTX);
-      return gen_vsetvl (Pmode, vl, avl, sew, vlmul, ta, ma);
-    }
-  else if (insn_type == VSETVL_VTYPE_CHANGE_ONLY)
-    return gen_vsetvl_vtype_change_only (sew, vlmul, ta, ma);
-  else
-    return gen_vsetvl_discard_result (Pmode, avl, sew, vlmul, ta, ma);
+  const vlmul_type ALL_LMUL[]
+    = {LMUL_1, LMUL_2, LMUL_4, LMUL_8, LMUL_F8, LMUL_F4, LMUL_F2};
+  for (const vlmul_type vlmul : ALL_LMUL)
+    if (calculate_ratio (sew, vlmul) == ratio)
+      return vlmul;
+  return LMUL_RESERVED;
 }

-static rtx
-gen_vsetvl_pat (rtx_insn *rinsn, const vector_insn_info &info,
-		rtx vl = NULL_RTX)
+/* Get the currently supported maximum sew used in the int rvv instructions. */
+static uint8_t
+get_max_int_sew ()
 {
-  rtx new_pat;
-  vl_vtype_info new_info = info;
-  if (info.get_insn () && info.get_insn ()->rtl ()
-      && fault_first_load_p (info.get_insn ()->rtl ()))
-    new_info.set_avl_info (
-      avl_info (get_avl (info.get_insn ()->rtl ()), nullptr));
-  if (vl)
-    new_pat = gen_vsetvl_pat (VSETVL_NORMAL, new_info, vl);
-  else
-    {
-      if (vsetvl_insn_p (rinsn))
-	new_pat = gen_vsetvl_pat (VSETVL_NORMAL, new_info, get_vl (rinsn));
-      else if (INSN_CODE (rinsn) == CODE_FOR_vsetvl_vtype_change_only)
-	new_pat = gen_vsetvl_pat (VSETVL_VTYPE_CHANGE_ONLY, new_info, NULL_RTX);
-      else
-	new_pat = gen_vsetvl_pat (VSETVL_DISCARD_RESULT, new_info, NULL_RTX);
-    }
-  return new_pat;
+  if (TARGET_VECTOR_ELEN_64)
+    return 64;
+  else if (TARGET_VECTOR_ELEN_32)
+    return 32;
+  gcc_unreachable ();
 }

-static void
-emit_vsetvl_insn (enum vsetvl_type insn_type, enum emit_type emit_type,
-		  const vl_vtype_info &info, rtx vl, rtx_insn *rinsn)
-{
-  rtx pat = gen_vsetvl_pat (insn_type, info, vl);
-  if (dump_file)
-    {
-      fprintf (dump_file, "\nInsert vsetvl insn PATTERN:\n");
-      print_rtl_single (dump_file, pat);
-      fprintf (dump_file, "\nfor insn:\n");
-      print_rtl_single (dump_file, rinsn);
-    }
-
-  if (emit_type == EMIT_DIRECT)
-    emit_insn (pat);
-  else if (emit_type == EMIT_BEFORE)
-    emit_insn_before (pat, rinsn);
-  else
-    emit_insn_after (pat, rinsn);
+/* Get the currently supported maximum sew used in the float rvv instructions.
+ */
+static uint8_t
+get_max_float_sew ()
+{
+  if (TARGET_VECTOR_ELEN_FP_64)
+    return 64;
+  else if (TARGET_VECTOR_ELEN_FP_32)
+    return 32;
+  else if (TARGET_VECTOR_ELEN_FP_16)
+    return 16;
+  gcc_unreachable ();
 }

-static void
-eliminate_insn (rtx_insn *rinsn)
+/* Helper function to get VL operand.  */
+static rtx
+get_vl2 (rtx_insn *rinsn)
 {
-  if (dump_file)
+  if (has_vl_op (rinsn))
     {
-      fprintf (dump_file, "\nEliminate insn %d:\n", INSN_UID (rinsn));
-      print_rtl_single (dump_file, rinsn);
+      extract_insn_cached (rinsn);
+      return recog_data.operand[get_attr_vl_op_idx (rinsn)];
     }
-  if (in_sequence_p ())
-    remove_insn (rinsn);
-  else
-    delete_insn (rinsn);
+  return SET_DEST (XVECEXP (PATTERN (rinsn), 0, 0));
 }

-static vsetvl_type
-insert_vsetvl (enum emit_type emit_type, rtx_insn *rinsn,
-	       const vector_insn_info &info, const vector_insn_info &prev_info)
+/* Count the number of REGNO in RINSN.  */
+static int
+count_regno_occurrences (rtx_insn *rinsn, unsigned int regno)
 {
-  /* Use X0, X0 form if the AVL is the same and the SEW+LMUL gives the same
-     VLMAX.  */
-  if (prev_info.valid_or_dirty_p () && !prev_info.unknown_p ()
-      && info.compatible_avl_p (prev_info) && info.same_vlmax_p (prev_info))
-    {
-      emit_vsetvl_insn (VSETVL_VTYPE_CHANGE_ONLY, emit_type, info, NULL_RTX,
-			rinsn);
-      return VSETVL_VTYPE_CHANGE_ONLY;
-    }
-
-  if (info.has_avl_imm ())
-    {
-      emit_vsetvl_insn (VSETVL_DISCARD_RESULT, emit_type, info, NULL_RTX,
-			rinsn);
-      return VSETVL_DISCARD_RESULT;
-    }
-
-  if (info.has_avl_no_reg ())
-    {
-      /* We can only use x0, x0 if there's no chance of the vtype change causing
-	 the previous vl to become invalid.  */
-      if (prev_info.valid_or_dirty_p () && !prev_info.unknown_p ()
-	  && info.same_vlmax_p (prev_info))
-	{
-	  emit_vsetvl_insn (VSETVL_VTYPE_CHANGE_ONLY, emit_type, info, NULL_RTX,
-			    rinsn);
-	  return VSETVL_VTYPE_CHANGE_ONLY;
-	}
-      /* Otherwise use an AVL of 0 to avoid depending on previous vl.  */
-      vl_vtype_info new_info = info;
-      new_info.set_avl_info (avl_info (const0_rtx, nullptr));
-      emit_vsetvl_insn (VSETVL_DISCARD_RESULT, emit_type, new_info, NULL_RTX,
-			rinsn);
-      return VSETVL_DISCARD_RESULT;
-    }
-
-  /* Use X0 as the DestReg unless AVLReg is X0. We also need to change the
-     opcode if the AVLReg is X0 as they have different register classes for
-     the AVL operand.  */
-  if (vlmax_avl_p (info.get_avl ()))
-    {
-      gcc_assert (has_vtype_op (rinsn) || vsetvl_insn_p (rinsn));
-      /* For user vsetvli a5, zero, we should use get_vl to get the VL
-	 operand "a5".  */
-      rtx vl_op = info.get_avl_or_vl_reg ();
-      gcc_assert (!vlmax_avl_p (vl_op));
-      emit_vsetvl_insn (VSETVL_NORMAL, emit_type, info, vl_op, rinsn);
-      return VSETVL_NORMAL;
-    }
-
-  emit_vsetvl_insn (VSETVL_DISCARD_RESULT, emit_type, info, NULL_RTX, rinsn);
-
-  if (dump_file)
-    {
-      fprintf (dump_file, "Update VL/VTYPE info, previous info=");
-      prev_info.dump (dump_file);
-    }
-  return VSETVL_DISCARD_RESULT;
+  int count = 0;
+  extract_insn (rinsn);
+  for (int i = 0; i < recog_data.n_operands; i++)
+    if (refers_to_regno_p (regno, recog_data.operand[i]))
+      count++;
+  return count;
 }

-/* Get VL/VTYPE information for INSN.  */
-static vl_vtype_info
-get_vl_vtype_info (const insn_info *insn)
+enum def_type
 {
-  set_info *set = nullptr;
-  rtx avl = ::get_avl (insn->rtl ());
-  if (avl && REG_P (avl))
-    {
-      if (vlmax_avl_p (avl) && has_vl_op (insn->rtl ()))
-	set
-	  = find_access (insn->uses (), REGNO (get_vl (insn->rtl ())))->def ();
-      else if (!vlmax_avl_p (avl))
-	set = find_access (insn->uses (), REGNO (avl))->def ();
-      else
-	set = nullptr;
-    }
-
-  uint8_t sew = get_sew (insn->rtl ());
-  enum vlmul_type vlmul = get_vlmul (insn->rtl ());
-  uint8_t ratio = get_attr_ratio (insn->rtl ());
-  /* when get_attr_ratio is invalid, this kind of instructions
-     doesn't care about ratio. However, we still need this value
-     in demand info backward analysis.  */
-  if (ratio == INVALID_ATTRIBUTE)
-    ratio = calculate_ratio (sew, vlmul);
-  bool ta = tail_agnostic_p (insn->rtl ());
-  bool ma = mask_agnostic_p (insn->rtl ());
-
-  /* If merge operand is undef value, we prefer agnostic.  */
-  int merge_op_idx = get_attr_merge_op_idx (insn->rtl ());
-  if (merge_op_idx != INVALID_ATTRIBUTE
-      && satisfies_constraint_vu (recog_data.operand[merge_op_idx]))
-    {
-      ta = true;
-      ma = true;
-    }
-
-  vl_vtype_info info (avl_info (avl, set), sew, vlmul, ratio, ta, ma);
-  return info;
-}
+  REAL_SET = 1 << 0,
+  PHI_SET = 1 << 1,
+  BB_HEAD_SET = 1 << 2,
+  BB_END_SET = 1 << 3,
+  /* ??? TODO: In RTL_SSA framework, we have REAL_SET,
+     PHI_SET, BB_HEAD_SET, BB_END_SET and
+     CLOBBER_DEF def_info types. Currently,
+     we conservatively do not optimize clobber
+     def since we don't see the case that we
+     need to optimize it.  */
+  CLOBBER_DEF = 1 << 4
+};

-/* Change insn and Assert the change always happens.  */
-static void
-validate_change_or_fail (rtx object, rtx *loc, rtx new_rtx, bool in_group)
+static bool
+insn_should_be_added_p (const insn_info *insn, unsigned int types)
 {
-  bool change_p = validate_change (object, loc, new_rtx, in_group);
-  gcc_assert (change_p);
+  if (insn->is_real () && (types & REAL_SET))
+    return true;
+  if (insn->is_phi () && (types & PHI_SET))
+    return true;
+  if (insn->is_bb_head () && (types & BB_HEAD_SET))
+    return true;
+  if (insn->is_bb_end () && (types & BB_END_SET))
+    return true;
+  return false;
 }

-static void
-change_insn (rtx_insn *rinsn, rtx new_pat)
+static const hash_set<use_info *>
+get_all_real_uses (insn_info *insn, unsigned regno)
 {
-  /* We don't apply change on RTL_SSA here since it's possible a
-     new INSN we add in the PASS before which doesn't have RTL_SSA
-     info yet.*/
-  if (dump_file)
-    {
-      fprintf (dump_file, "\nChange PATTERN of insn %d from:\n",
-	       INSN_UID (rinsn));
-      print_rtl_single (dump_file, PATTERN (rinsn));
-    }
+  gcc_assert (insn->is_real ());

-  validate_change_or_fail (rinsn, &PATTERN (rinsn), new_pat, false);
+  hash_set<use_info *> uses;
+  auto_vec<phi_info *> work_list;
+  hash_set<phi_info *> visited_list;

-  if (dump_file)
+  for (def_info *def : insn->defs ())
     {
-      fprintf (dump_file, "\nto:\n");
-      print_rtl_single (dump_file, PATTERN (rinsn));
+      if (!def->is_reg () || def->regno () != regno)
+	continue;
+      set_info *set = safe_dyn_cast<set_info *> (def);
+      if (!set)
+	continue;
+      for (use_info *use : set->nondebug_insn_uses ())
+	if (use->insn ()->is_real ())
+	  uses.add (use);
+      for (use_info *use : set->phi_uses ())
+	work_list.safe_push (use->phi ());
     }
-}

-static const insn_info *
-get_forward_read_vl_insn (const insn_info *insn)
-{
-  const bb_info *bb = insn->bb ();
-  for (const insn_info *i = insn->next_nondebug_insn ();
-       real_insn_and_same_bb_p (i, bb); i = i->next_nondebug_insn ())
+  while (!work_list.is_empty ())
     {
-      if (find_access (i->defs (), VL_REGNUM))
-	return nullptr;
-      if (read_vl_insn_p (i->rtl ()))
-	return i;
-    }
-  return nullptr;
-}
+      phi_info *phi = work_list.pop ();
+      visited_list.add (phi);

-static const insn_info *
-get_backward_fault_first_load_insn (const insn_info *insn)
-{
-  const bb_info *bb = insn->bb ();
-  for (const insn_info *i = insn->prev_nondebug_insn ();
-       real_insn_and_same_bb_p (i, bb); i = i->prev_nondebug_insn ())
-    {
-      if (fault_first_load_p (i->rtl ()))
-	return i;
-      if (find_access (i->defs (), VL_REGNUM))
-	return nullptr;
+      for (use_info *use : phi->nondebug_insn_uses ())
+	if (use->insn ()->is_real ())
+	  uses.add (use);
+      for (use_info *use : phi->phi_uses ())
+	if (!visited_list.contains (use->phi ()))
+	  work_list.safe_push (use->phi ());
     }
-  return nullptr;
+  return uses;
 }

-static bool
-change_insn (function_info *ssa, insn_change change, insn_info *insn,
-	     rtx new_pat)
+/* Recursively find all define instructions. The kind of instruction is
+   specified by the DEF_TYPE.  */
+static hash_set<set_info *>
+get_all_sets (phi_info *phi, unsigned int types)
 {
-  rtx_insn *rinsn = insn->rtl ();
-  auto attempt = ssa->new_change_attempt ();
-  if (!restrict_movement (change))
-    return false;
+  hash_set<set_info *> insns;
+  auto_vec<phi_info *> work_list;
+  hash_set<phi_info *> visited_list;
+  if (!phi)
+    return hash_set<set_info *> ();
+  work_list.safe_push (phi);

-  if (dump_file)
+  while (!work_list.is_empty ())
     {
-      fprintf (dump_file, "\nChange PATTERN of insn %d from:\n",
-	       INSN_UID (rinsn));
-      print_rtl_single (dump_file, PATTERN (rinsn));
-    }
-
-  insn_change_watermark watermark;
-  validate_change_or_fail (rinsn, &PATTERN (rinsn), new_pat, true);
-
-  /* These routines report failures themselves.  */
-  if (!recog (attempt, change) || !change_is_worthwhile (change, false))
-    return false;
+      phi_info *phi = work_list.pop ();
+      visited_list.add (phi);
+      for (use_info *use : phi->inputs ())
+	{
+	  def_info *def = use->def ();
+	  set_info *set = safe_dyn_cast<set_info *> (def);
+	  if (!set)
+	    return hash_set<set_info *> ();

-  /* Fix bug:
-      (insn 12 34 13 2 (set (reg:RVVM4DI 120 v24 [orig:134 _1 ] [134])
-	(if_then_else:RVVM4DI (unspec:RVVMF8BI [
-		    (const_vector:RVVMF8BI repeat [
-			    (const_int 1 [0x1])
-			])
-		    (const_int 0 [0])
-		    (const_int 2 [0x2]) repeated x2
-		    (const_int 0 [0])
-		    (reg:SI 66 vl)
-		    (reg:SI 67 vtype)
-		] UNSPEC_VPREDICATE)
-	    (plus:RVVM4DI (reg/v:RVVM4DI 104 v8 [orig:137 op1 ] [137])
-		(sign_extend:RVVM4DI (vec_duplicate:RVVM4SI (reg:SI 15 a5
-    [140])))) (unspec:RVVM4DI [ (const_int 0 [0]) ] UNSPEC_VUNDEF)))
-    "rvv.c":8:12 2784 {pred_single_widen_addsvnx8di_scalar} (expr_list:REG_EQUIV
-    (mem/c:RVVM4DI (reg:DI 10 a0 [142]) [1 <retval>+0 S[64, 64] A128])
-	(expr_list:REG_EQUAL (if_then_else:RVVM4DI (unspec:RVVMF8BI [
-			(const_vector:RVVMF8BI repeat [
-				(const_int 1 [0x1])
-			    ])
-			(reg/v:DI 13 a3 [orig:139 vl ] [139])
-			(const_int 2 [0x2]) repeated x2
-			(const_int 0 [0])
-			(reg:SI 66 vl)
-			(reg:SI 67 vtype)
-		    ] UNSPEC_VPREDICATE)
-		(plus:RVVM4DI (reg/v:RVVM4DI 104 v8 [orig:137 op1 ] [137])
-		    (const_vector:RVVM4DI repeat [
-			    (const_int 2730 [0xaaa])
-			]))
-		(unspec:RVVM4DI [
-			(const_int 0 [0])
-		    ] UNSPEC_VUNDEF))
-	    (nil))))
-    Here we want to remove use "a3". However, the REG_EQUAL/REG_EQUIV note use
-    "a3" which made us fail in change_insn.  We reference to the
-    'aarch64-cc-fusion.cc' and add this method.  */
-  remove_reg_equal_equiv_notes (rinsn);
-  confirm_change_group ();
-  ssa->change_insn (change);
+	  gcc_assert (!set->insn ()->is_debug_insn ());

-  if (dump_file)
-    {
-      fprintf (dump_file, "\nto:\n");
-      print_rtl_single (dump_file, PATTERN (rinsn));
+	  if (insn_should_be_added_p (set->insn (), types))
+	    insns.add (set);
+	  if (set->insn ()->is_phi ())
+	    {
+	      phi_info *new_phi = as_a<phi_info *> (set);
+	      if (!visited_list.contains (new_phi))
+		work_list.safe_push (new_phi);
+	    }
+	}
     }
-  return true;
+  return insns;
 }

-static void
-change_vsetvl_insn (const insn_info *insn, const vector_insn_info &info,
-		    rtx vl = NULL_RTX)
+static hash_set<set_info *>
+get_all_sets (set_info *set, bool /* get_real_inst */ real_p,
+	      bool /*get_phi*/ phi_p, bool /* get_function_parameter*/ param_p)
 {
-  rtx_insn *rinsn;
-  if (vector_config_insn_p (insn->rtl ()))
-    {
-      rinsn = insn->rtl ();
-      gcc_assert (vsetvl_insn_p (rinsn) && "Can't handle X0, rs1 vsetvli yet");
-    }
-  else
-    {
-      gcc_assert (has_vtype_op (insn->rtl ()));
-      rinsn = PREV_INSN (insn->rtl ());
-      gcc_assert (vector_config_insn_p (rinsn));
-    }
-  rtx new_pat = gen_vsetvl_pat (rinsn, info, vl);
-  change_insn (rinsn, new_pat);
-}
+  if (real_p && phi_p && param_p)
+    return get_all_sets (safe_dyn_cast<phi_info *> (set),
+			 REAL_SET | PHI_SET | BB_HEAD_SET | BB_END_SET);

-static bool
-avl_source_has_vsetvl_p (set_info *avl_source)
-{
-  if (!avl_source)
-    return false;
-  if (!avl_source->insn ())
-    return false;
-  if (avl_source->insn ()->is_real ())
-    return vsetvl_insn_p (avl_source->insn ()->rtl ());
-  hash_set<set_info *> sets = get_all_sets (avl_source, true, false, true);
-  for (const auto set : sets)
-    {
-      if (set->insn ()->is_real () && vsetvl_insn_p (set->insn ()->rtl ()))
-	return true;
-    }
-  return false;
+  else if (real_p && param_p)
+    return get_all_sets (safe_dyn_cast<phi_info *> (set),
+			 REAL_SET | BB_HEAD_SET | BB_END_SET);
+
+  else if (real_p)
+    return get_all_sets (safe_dyn_cast<phi_info *> (set), REAL_SET);
+  return hash_set<set_info *> ();
 }

 static bool
@@ -959,93 +631,14 @@ source_equal_p (insn_info *insn1, insn_info *insn2)
   rtx_insn *rinsn2 = insn2->rtl ();
   if (!rinsn1 || !rinsn2)
     return false;
+
   rtx note1 = find_reg_equal_equiv_note (rinsn1);
   rtx note2 = find_reg_equal_equiv_note (rinsn2);
-  rtx single_set1 = single_set (rinsn1);
-  rtx single_set2 = single_set (rinsn2);
-  if (read_vl_insn_p (rinsn1) && read_vl_insn_p (rinsn2))
-    {
-      const insn_info *load1 = get_backward_fault_first_load_insn (insn1);
-      const insn_info *load2 = get_backward_fault_first_load_insn (insn2);
-      return load1 && load2 && load1 == load2;
-    }
-
   if (note1 && note2 && rtx_equal_p (note1, note2))
     return true;
-
-  /* Since vsetvl instruction is not single SET.
-     We handle this case specially here.  */
-  if (vsetvl_insn_p (insn1->rtl ()) && vsetvl_insn_p (insn2->rtl ()))
-    {
-      /* For example:
-	   vsetvl1 a6,a5,e32m1
-	   RVV 1 (use a6 as AVL)
-	   vsetvl2 a5,a5,e8mf4
-	   RVV 2 (use a5 as AVL)
-	 We consider AVL of RVV 1 and RVV 2 are same so that we can
-	 gain more optimization opportunities.
-
-	 Note: insn1_info.compatible_avl_p (insn2_info)
-	 will make sure there is no instruction between vsetvl1 and vsetvl2
-	 modify a5 since their def will be different if there is instruction
-	 modify a5 and compatible_avl_p will return false.  */
-      vector_insn_info insn1_info, insn2_info;
-      insn1_info.parse_insn (insn1);
-      insn2_info.parse_insn (insn2);
-
-      /* To avoid dead loop, we don't optimize a vsetvli def has vsetvli
-	 instructions which will complicate the situation.  */
-      if (avl_source_has_vsetvl_p (insn1_info.get_avl_source ())
-	  || avl_source_has_vsetvl_p (insn2_info.get_avl_source ()))
-	return false;
-
-      if (insn1_info.same_vlmax_p (insn2_info)
-	  && insn1_info.compatible_avl_p (insn2_info))
-	return true;
-    }
-
-  /* We only handle AVL is set by instructions with no side effects.  */
-  if (!single_set1 || !single_set2)
-    return false;
-  if (!rtx_equal_p (SET_SRC (single_set1), SET_SRC (single_set2)))
-    return false;
-  /* RTL_SSA uses include REG_NOTE. Consider this following case:
-
-     insn1 RTL:
-	(insn 41 39 42 4 (set (reg:DI 26 s10 [orig:159 loop_len_46 ] [159])
-	  (umin:DI (reg:DI 15 a5 [orig:201 _149 ] [201])
-	    (reg:DI 14 a4 [276]))) 408 {*umindi3}
-	(expr_list:REG_EQUAL (umin:DI (reg:DI 15 a5 [orig:201 _149 ] [201])
-	    (const_int 2 [0x2]))
-	(nil)))
-     The RTL_SSA uses of this instruction has 2 uses:
-	1. (reg:DI 15 a5 [orig:201 _149 ] [201]) - twice.
-	2. (reg:DI 14 a4 [276]) - once.
-
-     insn2 RTL:
-	(insn 38 353 351 4 (set (reg:DI 27 s11 [orig:160 loop_len_47 ] [160])
-	  (umin:DI (reg:DI 15 a5 [orig:199 _146 ] [199])
-	    (reg:DI 14 a4 [276]))) 408 {*umindi3}
-	(expr_list:REG_EQUAL (umin:DI (reg:DI 28 t3 [orig:200 ivtmp_147 ] [200])
-	    (const_int 2 [0x2]))
-	(nil)))
-      The RTL_SSA uses of this instruction has 3 uses:
-	1. (reg:DI 15 a5 [orig:199 _146 ] [199]) - once
-	2. (reg:DI 14 a4 [276]) - once
-	3. (reg:DI 28 t3 [orig:200 ivtmp_147 ] [200]) - once
-
-      Return false when insn1->uses ().size () != insn2->uses ().size ()
-  */
-  if (insn1->uses ().size () != insn2->uses ().size ())
-    return false;
-  for (size_t i = 0; i < insn1->uses ().size (); i++)
-    if (insn1->uses ()[i] != insn2->uses ()[i])
-      return false;
-  return true;
+  return false;
 }

-/* Helper function to get single same real RTL source.
-   return NULL if it is not a single real RTL source.  */
 static insn_info *
 extract_single_source (set_info *set)
 {
@@ -1066,7 +659,7 @@ extract_single_source (set_info *set)
 	 NULL so that VSETVL PASS will insert vsetvl directly.  */
       if (set->insn ()->is_artificial ())
 	return nullptr;
-      if (!source_equal_p (set->insn (), first_insn))
+      if (set != *sets.begin () && !source_equal_p (set->insn (), first_insn))
 	return nullptr;
     }

@@ -1074,3115 +667,2825 @@ extract_single_source (set_info *set)
 }

 static unsigned
-calculate_sew (vlmul_type vlmul, unsigned int ratio)
+get_expr_id (unsigned bb_index, unsigned regno, unsigned num_bbs)
 {
-  for (const unsigned sew : ALL_SEW)
-    if (calculate_ratio (sew, vlmul) == ratio)
-      return sew;
-  return 0;
+  return regno * num_bbs + bb_index;
 }
-
-static vlmul_type
-calculate_vlmul (unsigned int sew, unsigned int ratio)
+static unsigned
+get_regno (unsigned expr_id, unsigned num_bb)
 {
-  for (const vlmul_type vlmul : ALL_LMUL)
-    if (calculate_ratio (sew, vlmul) == ratio)
-      return vlmul;
-  return LMUL_RESERVED;
+  return expr_id / num_bb;
 }
+static unsigned
+get_bb_index (unsigned expr_id, unsigned num_bb)
+{
+  return expr_id % num_bb;
+}
+
+/* This flags indicates the minimum demand of the vl and vtype values by the
+   RVV instruction. For example, DEMAND_RATIO_P indicates that this RVV
+   instruction only needs the SEW/LMUL ratio to remain the same, and does not
+   require SEW and LMUL to be fixed.
+   Therefore, if the former RVV instruction needs DEMAND_RATIO_P and the latter
+   instruction needs DEMAND_SEW_LMUL_P and its SEW/LMUL is the same as that of
+   the former instruction, then we can make the minimu demand of the former
+   instruction strict to DEMAND_SEW_LMUL_P, and its required SEW and LMUL are
+   the SEW and LMUL of the latter instruction, and the vsetvl instruction
+   generated according to the new demand can also be used for the latter
+   instruction, so there is no need to insert a separate vsetvl instruction for
+   the latter instruction.  */
+enum demand_flags : unsigned
+{
+  DEMAND_EMPTY_P = 0,
+  DEMAND_SEW_P = 1 << 0,
+  DEMAND_LMUL_P = 1 << 1,
+  DEMAND_RATIO_P = 1 << 2,
+  DEMAND_GE_SEW_P = 1 << 3,
+  DEMAND_TAIL_POLICY_P = 1 << 4,
+  DEMAND_MASK_POLICY_P = 1 << 5,
+  DEMAND_AVL_P = 1 << 6,
+  DEMAND_NON_ZERO_AVL_P = 1 << 7,
+};

-static bool
-incompatible_avl_p (const vector_insn_info &info1,
-		    const vector_insn_info &info2)
-{
-  return !info1.compatible_avl_p (info2) && !info2.compatible_avl_p (info1);
-}
+/* We split the demand information into three parts. They are sew and lmul
+   related (sew_lmul_demand_type), tail and mask policy related
+   (policy_demand_type) and avl related (avl_demand_type). Then we define three
+   interfaces avaiable_with, compatible_with and merge_with. avaiable_with is
+   used to determine whether the two vsetvl infos prev_info and next_info are
+   available or not. If prev_info is available for next_info, it means that the
+   RVV insn corresponding to next_info on the path from prev_info to next_info
+   can be used without inserting a separate vsetvl instruction. compatible_with
+   is used to determine whether prev_info is compatible with next_info, and if
+   so, merge_with can be used to merge the stricter demand information from
+   next_info into prev_info so that prev_info becomes available to next_info.
+ */

-static bool
-different_sew_p (const vector_insn_info &info1, const vector_insn_info &info2)
+enum class sew_lmul_demand_type : unsigned
 {
-  return info1.get_sew () != info2.get_sew ();
-}
+  sew_lmul = demand_flags::DEMAND_SEW_P | demand_flags::DEMAND_LMUL_P,
+  ratio_only = demand_flags::DEMAND_RATIO_P,
+  sew_only = demand_flags::DEMAND_SEW_P,
+  ge_sew = demand_flags::DEMAND_GE_SEW_P,
+  ratio_and_ge_sew
+  = demand_flags::DEMAND_RATIO_P | demand_flags::DEMAND_GE_SEW_P,
+};

-static bool
-different_lmul_p (const vector_insn_info &info1, const vector_insn_info &info2)
+enum class policy_demand_type : unsigned
 {
-  return info1.get_vlmul () != info2.get_vlmul ();
-}
+  tail_mask_policy
+  = demand_flags::DEMAND_TAIL_POLICY_P | demand_flags::DEMAND_MASK_POLICY_P,
+  tail_policy_only = demand_flags::DEMAND_TAIL_POLICY_P,
+  mask_policy_only = demand_flags::DEMAND_MASK_POLICY_P,
+  ignore_policy = demand_flags::DEMAND_EMPTY_P,
+};

-static bool
-different_ratio_p (const vector_insn_info &info1, const vector_insn_info &info2)
+enum class avl_demand_type : unsigned
 {
-  return info1.get_ratio () != info2.get_ratio ();
-}
+  avl = demand_flags::DEMAND_AVL_P,
+  non_zero_avl = demand_flags::DEMAND_NON_ZERO_AVL_P,
+  ignore_avl = demand_flags::DEMAND_EMPTY_P,
+};

-static bool
-different_tail_policy_p (const vector_insn_info &info1,
-			 const vector_insn_info &info2)
-{
-  return info1.get_ta () != info2.get_ta ();
-}

-static bool
-different_mask_policy_p (const vector_insn_info &info1,
-			 const vector_insn_info &info2)
+class vsetvl_info
 {
-  return info1.get_ma () != info2.get_ma ();
-}
+private:
+  insn_info *m_insn;
+  bb_info *m_bb;
+  rtx m_avl;
+  rtx m_vl;
+  set_info *m_avl_def;
+  uint8_t m_sew;
+  uint8_t m_max_sew;
+  vlmul_type m_vlmul;
+  uint8_t m_ratio;
+  bool m_ta;
+  bool m_ma;
+
+  sew_lmul_demand_type m_sew_lmul_demand;
+  policy_demand_type m_policy_demand;
+  avl_demand_type m_avl_demand;
+
+  enum class state_type
+  {
+    UNINITIALIZED,
+    VALID,
+    UNKNOWN,
+    EMPTY,
+  };
+  state_type m_state;
+
+  bool m_ignore;
+  bool change_vtype_only;
+  insn_info *m_read_vl_insn;
+  bool use_by_non_rvv_insn;

-static bool
-possible_zero_avl_p (const vector_insn_info &info1,
-		     const vector_insn_info &info2)
-{
-  return !info1.has_non_zero_avl () || !info2.has_non_zero_avl ();
-}
-
-static bool
-second_ratio_invalid_for_first_sew_p (const vector_insn_info &info1,
-				      const vector_insn_info &info2)
-{
-  return calculate_vlmul (info1.get_sew (), info2.get_ratio ())
-	 == LMUL_RESERVED;
-}
-
-static bool
-second_ratio_invalid_for_first_lmul_p (const vector_insn_info &info1,
-				       const vector_insn_info &info2)
-{
-  return calculate_sew (info1.get_vlmul (), info2.get_ratio ()) == 0;
-}
-
-static bool
-float_insn_valid_sew_p (const vector_insn_info &info, unsigned int sew)
-{
-  if (info.get_insn () && info.get_insn ()->is_real ()
-      && get_attr_type (info.get_insn ()->rtl ()) == TYPE_VFMOVFV)
-    {
-      if (sew == 16)
-	return TARGET_VECTOR_ELEN_FP_16;
-      else if (sew == 32)
-	return TARGET_VECTOR_ELEN_FP_32;
-      else if (sew == 64)
-	return TARGET_VECTOR_ELEN_FP_64;
-    }
-  return true;
-}
-
-static bool
-second_sew_less_than_first_sew_p (const vector_insn_info &info1,
-				  const vector_insn_info &info2)
-{
-  return info2.get_sew () < info1.get_sew ()
-	 || !float_insn_valid_sew_p (info1, info2.get_sew ());
-}
-
-static bool
-first_sew_less_than_second_sew_p (const vector_insn_info &info1,
-				  const vector_insn_info &info2)
-{
-  return info1.get_sew () < info2.get_sew ()
-	 || !float_insn_valid_sew_p (info2, info1.get_sew ());
-}
-
-/* return 0 if LMUL1 == LMUL2.
-   return -1 if LMUL1 < LMUL2.
-   return 1 if LMUL1 > LMUL2.  */
-static int
-compare_lmul (vlmul_type vlmul1, vlmul_type vlmul2)
-{
-  if (vlmul1 == vlmul2)
-    return 0;
-
-  switch (vlmul1)
-    {
-    case LMUL_1:
-      if (vlmul2 == LMUL_2 || vlmul2 == LMUL_4 || vlmul2 == LMUL_8)
-	return 1;
-      else
-	return -1;
-    case LMUL_2:
-      if (vlmul2 == LMUL_4 || vlmul2 == LMUL_8)
-	return 1;
-      else
-	return -1;
-    case LMUL_4:
-      if (vlmul2 == LMUL_8)
-	return 1;
-      else
-	return -1;
-    case LMUL_8:
-      return -1;
-    case LMUL_F2:
-      if (vlmul2 == LMUL_1 || vlmul2 == LMUL_2 || vlmul2 == LMUL_4
-	  || vlmul2 == LMUL_8)
-	return 1;
-      else
-	return -1;
-    case LMUL_F4:
-      if (vlmul2 == LMUL_F2 || vlmul2 == LMUL_1 || vlmul2 == LMUL_2
-	  || vlmul2 == LMUL_4 || vlmul2 == LMUL_8)
-	return 1;
-      else
-	return -1;
-    case LMUL_F8:
-      return 0;
-    default:
-      gcc_unreachable ();
-    }
-}
-
-static bool
-second_lmul_less_than_first_lmul_p (const vector_insn_info &info1,
-				    const vector_insn_info &info2)
-{
-  return compare_lmul (info2.get_vlmul (), info1.get_vlmul ()) == -1;
-}
-
-static bool
-second_ratio_less_than_first_ratio_p (const vector_insn_info &info1,
-				      const vector_insn_info &info2)
-{
-  return info2.get_ratio () < info1.get_ratio ();
-}
-
-static CONSTEXPR const demands_cond incompatible_conds[] = {
-#define DEF_INCOMPATIBLE_COND(AVL1, SEW1, LMUL1, RATIO1, NONZERO_AVL1,         \
-			      GE_SEW1, TAIL_POLICTY1, MASK_POLICY1, AVL2,      \
-			      SEW2, LMUL2, RATIO2, NONZERO_AVL2, GE_SEW2,      \
-			      TAIL_POLICTY2, MASK_POLICY2, COND)               \
-  {{{AVL1, SEW1, LMUL1, RATIO1, NONZERO_AVL1, GE_SEW1, TAIL_POLICTY1,          \
-     MASK_POLICY1},                                                            \
