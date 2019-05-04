# hell-world
My first repository
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html" charset="UTF-8">
    </head>
    <title>二叉树</title>

    <script>
        function Node(data, left, right)
        {
            this.data = data;
            this.left = left;
            this.right = right;
            this.show = show;
        }

        function show()
        {
            return this.data;
        }

        function BST()
        {
            this.root = null;//设根节点为空
            this.insert = insert;//Bst方法的insert属性指向insert方法
        }

        function insert(data)//添加新节点方法,参数data为待插入节点
        {
            var n = new Node(data, null, null);
            if(this.root == null)//如果根节点为空
            {
                this.root = n;//传入data做根节点
            }
            else//如果根节点不为空
            {
                var current = this.root;//声明新变量current存储根节点
                var parent;//声明空的新变量parent
                while(true)//无限循环，只有遇到break语句才会跳出循环
                {
                    parent = current;//变量parent存储当前节点
                    if(data < current.data)//如果待插入节点小于当前节点
                    {
                        current = current.left;//待插入节点移动到根节点的左子树上
                        if(current == null)//如果左子树为空
                        {
                            parent.left = n;//待插入节点做左子树节点
                            break;//跳出当前循环并执行之后的代码
                        }
                    }
                    else//如果待插入节点大于当前节点
                    {
                        current = current.right;//待插入节点移动到右子树上
                        if(current == null)//如果右子树为空
                        {
                            parent.right = n;//待插入节点做右子树节点
                            break;//跳出当前循环并执行之后的代码
                        }
                    }
                }
            }
        }

        function inOrder(node)
        {
            if(!(node == null))//如果当前节点不为空
            {
                inOrder(node.left);//采用递归调用方法自身判断左子树是否存在
                console.log(node.show() + " ");//如果左子树存在，则向控制台输出左子树节点
                inOrder(node.right);//接着采用递归调用方法自身判断右子树是否存在
            }
        }

        var nums = new BST();//声明nums变量存储一个新的BST类
        nums.insert(23);//添加节点中...
        nums.insert(45);
        nums.insert(16);
        nums.insert(37);
        nums.insert(3);
        nums.insert(99);
        nums.insert(22);
        inOrder(nums.root);//调用中序遍历方法，从根节点开始遍历二叉树
        console.log("中序遍历后：");//输出遍历后的结果
    </script>
</html>
