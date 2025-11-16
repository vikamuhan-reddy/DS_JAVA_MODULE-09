# EX 18 Implement a Queue Using Array

## AIM:
To write a Java program to implement a queue using an array with support for enqueue, dequeue, peek, and display operations.

## Algorithm
1. Start  
2. Read the capacity of the queue  
3. Initialize an array to store queue elements and variables for front, rear, and size  
4. For each operation:  
   - **Enqueue (1 x)**: Add x to the rear; print error if full  
   - **Dequeue (2)**: Remove front element; print error if empty  
   - **Peek (3)**: Print front element without removing; print error if empty  
   - **Display (4)**: Print all elements from front to rear; print error if empty  
5. Process commands until EOF  
6. End

## Program:
```java
import java.util.*;

public class ArrayQueue {
    private int[] queue;
    private int front, rear, size, capacity;

    public ArrayQueue(int capacity) {
        this.capacity = capacity;
        queue = new int[capacity];
        front = 0;
        rear = -1;
        size = 0;
    }

    public void enqueue(int data) {
        if (isFull()) {
            System.out.println("Queue is full! Cannot enqueue " + data);
            return;
        }
        rear = (rear + 1) % capacity;
        queue[rear] = data;
        size++;
        System.out.println(data + " enqueued");
    }

    public void dequeue() {
        if (isEmpty()) {
            System.out.println("Queue is empty! Cannot dequeue.");
            return;
        }
        System.out.println(queue[front] + " dequeued");
        front = (front + 1) % capacity;
        size--;
    }

    public void peek() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return;
        }
        System.out.println("Front element: " + queue[front]);
    }

    public void display() {
        if (isEmpty()) {
            System.out.println("Queue is empty!");
            return;
        }
        for(int i = 0; i < size; i++) {
            System.out.print(queue[(front + i) % capacity] + " ");
        }
        System.out.println();
    }

    public boolean isFull() {
        return size == capacity;
    }

    public boolean isEmpty() {
        return size == 0;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int cap = sc.nextInt();
        ArrayQueue q = new ArrayQueue(cap);

        while (sc.hasNext()) {
            int command = sc.nextInt();
            switch (command) {
                case 1:
                    int val = sc.nextInt();
                    q.enqueue(val);
                    break;
                case 2:
                    q.dequeue();
                    break;
                case 3:
                    q.peek();
                    break;
                case 4:
                    q.display();
                    break;
                default:
                    System.out.println("Invalid command: " + command);
            }
        }
        sc.close();
    }
}
```

 
## Output:
<img width="708" height="638" alt="Screen Shot 1947-08-25 at 20 25 09" src="https://github.com/user-attachments/assets/5b5d746c-8eec-4157-b2a8-63046e0bcc30" />


## Result:
Thus the Java program to implement a queue using an array with enqueue, dequeue, peek, and display operations is implemented successfully.

