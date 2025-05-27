java code block
```java
public List<Integer> inOrderTraversalRecursion(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        inOrderTraverse(root, result);
        return result;
    }
    public void inOrderTraverse(TreeNode node, List<Integer> result) {
        if (node == null) return;

        inOrderTraverse(node.left, result);
        result.add(node.val);
        inOrderTraverse(node.right, result);
    }

    public List<Integer> inOrderTraversalIterative(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        Deque<TreeNode> stack = new ArrayDeque<>();
        TreeNode current = root;

        while (current != null || !stack.isEmpty()) {
            while (current != null) {
                stack.push(current);
                current = current.left;
            }
            current = stack.pop();
            result.add(current.val);

            current = current.right;
        }
        return result;
    }
    
```

Time Complexity: O(n) for both recursive and iterative methods, where n is the number of nodes in the tree.

Space Complexity: O(h) for the recursive method, where h is the height of the tree (due to recursion stack), and O(n) for the iterative method, where n is the number of nodes in the tree (in the worst case, all nodes could be in the stack).
