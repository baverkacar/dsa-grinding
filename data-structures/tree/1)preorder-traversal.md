create java code block
```java
class BinaryTreePreOrderTraversal {
    public List<Integer> preOrderTraversalRecursion(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        preOrderTraverse(root, result);
        return result;
    }

    public void preOrderTraverse(TreeNode node, List<Integer> result) {
        if (node == null) return;

        result.add(node.val);
        preOrderTraverse(node.left, result);
        preOrderTraverse(node.right, result);
    }

    public List<Integer> preOrderTraversalIterative(TreeNode root) {
        Deque<TreeNode> stack = new ArrayDeque<>();
        List<Integer> result = new ArrayList<>();
        if (root == null) return result;

        stack.push(root);
        while (!stack.isEmpty()) {
            TreeNode current = stack.pop();
            result.add(current.val); 

            if (current.right != null) {
                stack.push(current.right);
            }

            if (current.left != null) {
                stack.push(current.left);
            }
        }
        return result;
    }
 }
```

Time Complexity: O(n) for both recursive and iterative methods, where n is the number of nodes in the tree.
Space Complexity: O(h) for the recursive method, where h is the height of the tree (due to recursion stack), and O(n) for the iterative method, where n is the number of nodes in the tree (in the worst case, all nodes could be in the stack).