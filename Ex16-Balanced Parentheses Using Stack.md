# EX 16 Sort the Elements of a Stack in Ascending Order

## AIM:
To write a Java program to sort the elements of a given stack in ascending order.

## Algorithm
1. Start  
2. Read the elements of the stack from the user  
3. Push all elements into a stack  
4. Sort the internal array of the stack using `Arrays.sort()`  
5. Display the sorted stack elements  
6. End

## Program:
```java
import java.util.*;

public class Stack {
  private int[] arr;
  private int top;

  public Stack(int size) {
    arr = new int[size];
    top = -1;
  }

  public void push(int num) {
    if (top == arr.length - 1) {
      System.out.println("Stack is full");
    } else {
      arr[++top] = num;
    }
  }

  public int pop() {
    if (top == -1) {
      System.out.println("Stack Underflow");
      return -1;
    } else {
      return arr[top--];
    }
  }

  public int peek() {
    if (top == -1) {
      System.out.println("Stack is empty");
      return -1;
    } else {
      return arr[top];
    }
  }

  public boolean isEmpty() {
    return top == -1;
  }

  public void sort() {
    Arrays.sort(arr);
  }
  
  public void display(){
      for(int ch : arr){
          System.out.print(ch + " ");
      }
  }

  public static void main(String[] args) {
    Scanner scanner = new Scanner(System.in);

    String[] input = scanner.nextLine().trim().split("\\s+");
    int size = input.length;

    Stack stack = new Stack(size);

    for (String s : input) {
      stack.push(Integer.parseInt(s));
    }

    stack.sort();
    stack.display();

    scanner.close();
  }
}
```


## Output:
<img width="372" height="157" alt="Screen Shot 1947-08-25 at 20 20 50" src="https://github.com/user-attachments/assets/0a74947b-3f08-4def-9913-0f952807be3f" />


## Result:
Thus the Java program to sort the elements of a stack in ascending order is implemented successfully.

