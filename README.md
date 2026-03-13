# Deletion-AVL-tree-
Practice program 
class Node:
    def __init__(self, key):
        self.key = key
        self.left = None
        self.right = None
        self.height = 1
def height(node):
    if node is None:
        return 0
    return node.height
def rightRotate(y):
    x = y.left
    y.left = x.right
    x.right = y
    return x
def leftRotate(x):
    y = x.right
    x.right = y.left
    y.left = x
    return y
def minValue(node):
    current = node
    while current.left is not None:
        current = current.left
return current
def delete(root, key):
    if root is None:
        return root
    if key < root.key:
        root.left = delete(root.left, key)
    elif key > root.key:
        root.right = delete(root.right, key)
    else:
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left
        temp = minValue(root.right)
        root.key = temp.key
        root.right = delete(root.right, temp.key)
    return root
def inorder(root):
    if root:
        inorder(root.left)
        print root.key,
        inorder(root.right)
root = Node(30)
root.left = Node(20)
root.right = Node(40)
root.left.left = Node(10)
print "AVL Tree:"
inorder(root)
print "\nDelete 20"
root = delete(root, 20)
print "Tree after deletion:"
inorder(root)
OUTPUT:

AVL Tree:
10 20 30 40

Delete 20
Tree after deletion:
10 30 40
