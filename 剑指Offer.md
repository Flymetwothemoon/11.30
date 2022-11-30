# 2022.11.30

## 剑指 Offer 09. 用两个栈实现队列



简单

用两个栈实现一个队列。队列的声明如下，请实现它的两个函数 `appendTail` 和 `deleteHead` ，分别完成在队列尾部插入整数和在队列头部删除整数的功能。(若队列中没有元素，`deleteHead` 操作返回 -1 )

 

**示例 1：**

```
输入：
["CQueue","appendTail","deleteHead","deleteHead","deleteHead"]
[[],[3],[],[],[]]
输出：[null,null,3,-1,-1]
```

**示例 2：**

```
输入：
["CQueue","deleteHead","appendTail","appendTail","deleteHead","deleteHead"]
[[],[],[5],[2],[],[]]
输出：[null,-1,null,null,5,2]
```

```java
class CQueue {
  LinkedList<Integer> A, B;
    public CQueue() {
        A = new LinkedList<Integer>();
        B = new LinkedList<Integer>();
    }
    
    public void appendTail(int value) {
        A.push(value);

    }
    
    public int deleteHead() {
     if (B.isEmpty()) {
            while (!A.isEmpty()) {
                B.push(A.pop());
            }
        } 
        if (B.isEmpty()) {
            return -1;
        } else {
            int deleteItem = B.pop();
            return deleteItem;
        }
    }
}
```

java写算法确实挺好做的

**CQUeue()**是创建了2个**栈**,**appendTail()**是**队列尾部插入整数**,所以直接**A.push()**,

删除头部的话,有2种情况。

根据**栈**后进先出的思想,将**A**的东西传到**B**中,实现了反转功能.

然后**第一种情况:**如果**B**里面为空、

那么返回-1

**第二种情况:**如果**B**里面不为空

返回**B弹出的东西**



## 剑指 Offer 30. 包含min函数的栈

定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的 min 函数在该栈中，调用 min、push 及 pop 的时间复杂度都是 O(1)。

**示例:**

```
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.min();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.min();   --> 返回 -2.
```

```java
class MinStack {

​     LinkedList<Integer> A, B;

  /** initialize your data structure here. */

  public MinStack() {

​    A = new LinkedList<Integer>();

​    B = new LinkedList<Integer>();

  }

  public void push(int x) {

​    A.push(x);

​    if(B.isEmpty()){

​      B.push(x);

​    }

​    else{

​      if(B.peek()>=x){

​        B.push(x);

​      }

​    }

  }

  

  public void pop() {

​    if(A.pop().equals(B.peek())){

​      B.pop();

​    }

  }

  

  public int top() {

​    return A.peek();

  }

  

  public int min() {

​    return B.peek();

  }

}
```

唯一一个要注意的就是

**A.peek()**显示的是**A的栈顶元素**

https://github.com/Flymetwothemoon/11.30.git