# Inorder Successor in BST

Given a binary search tree and a node in it, find the in-order successor of that node in the BST.

**Note:** If the given node has no in-order successor in the tree, return `null`.

**Solution:**
```java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
  public TreeNode inorderSuccessor(TreeNode root, TreeNode p) {
    if (p.right != null) {
      return getMin(p.right);
    }

    TreeNode succ = null;

    while (root != null) {
      if (root.val <= p.val) {
        root = root.right;
      } else {
        succ = root;
        root = root.left;
      }
    }

    return succ;
  }

  TreeNode getMin(TreeNode p) {
    while (p.left != null) {
      p = p.left;
    }
    return p;
  }
}
```