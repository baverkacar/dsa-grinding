create java code block
```java
public List<Integer> postOrderTraversalRecursion(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        postOrderTraverse(root, result);
        return result;
    }
    public void postOrderTraverse(TreeNode node, List<Integer> result) {
        if (node == null) return;

        postOrderTraverse(node.left, result);
        postOrderTraverse(node.right, result);
        result.add(node.val); // 3. Root
    }

    public List<Integer> postOrderTraversalIterative(TreeNode root) {
        List<Integer> result = new ArrayList<>();
        if (root == null) return result;

        Deque<TreeNode> stack1 = new ArrayDeque<>();
        Deque<TreeNode> stack2 = new ArrayDeque<>();

        stack1.push(root);

        while (!stack1.isEmpty()) {
            TreeNode current = stack1.pop();
            stack2.push(current);

            if (current.left != null) {
                stack1.push(current.left);
            }

            if (current.right != null) {
                stack1.push(current.right);
            }
        }

        while (!stack2.isEmpty()) {
            result.add(stack2.pop().val);
        }

        return result;
    }
```

Time Complexity: O(n) for both the recursive and iterative approaches, where n is the number of nodes in the tree. Each node is visited exactly once.
Space Complexity: O(n) for the recursive approach due to the call stack, and O(n) for the iterative approach due to the use of two stacks.