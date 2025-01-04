# Leetcode--1448
Count Good Nodes in Binary Tree
// code in java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int x) { val = x; }
}

public class Solution {
    public int goodNodes(TreeNode root) {
        return dfs(root, Integer.MIN_VALUE);
    }

    private int dfs(TreeNode node, int maxVal) {
        if (node == null) {
            return 0;
        }
        int count = 0;
        if (node.val >= maxVal) {
            count = 1;
            maxVal = node.val;
        }
        count += dfs(node.left, maxVal);
        count += dfs(node.right, maxVal);
        return count;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        TreeNode root = new TreeNode(3);
        root.left = new TreeNode(1);
        root.right = new TreeNode(4);
        root.left.left = new TreeNode(3);
        root.right.left = new TreeNode(1);
        root.right.right = new TreeNode(5);
        System.out.println(solution.goodNodes(root)); // Output: 4
    }
}

