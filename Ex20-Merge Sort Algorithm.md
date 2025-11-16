# EX 20 Single-Threaded CPU Task Scheduling

## AIM:
To write a Java program to determine the order in which a single-threaded CPU will process tasks based on their enqueue and processing times.

## Algorithm
1. Start  
2. Read the number of tasks `n` and their enqueue and processing times  
3. Store tasks along with their original indices  
4. Sort tasks by enqueue time  
5. Initialize a priority queue to select tasks with the shortest processing time, breaking ties by the smallest index  
6. Initialize `time = 0` and process tasks as follows:  
   - If the queue is empty and next task is not yet available, move `time` to the enqueue time of the next task  
   - Add all tasks whose enqueue time ≤ `time` to the priority queue  
   - Poll the task with the shortest processing time from the queue and increment `time` by its processing time  
7. Repeat until all tasks are processed  
8. Print the order of task indices processed by the CPU  
9. End

## Program:
```java
import java.util.*;

public class Solution {
    public int[] getOrder(int[][] tasks) {
        PriorityQueue<int[]> nextTask = new PriorityQueue<>(
            (a, b) -> (a[1] != b[1] ? (a[1] - b[1]) : (a[2] - b[2]))
        );

        int[][] sortedTasks = new int[tasks.length][3];
        for (int i = 0; i < tasks.length; i++) {
            sortedTasks[i][0] = tasks[i][0];
            sortedTasks[i][1] = tasks[i][1];
            sortedTasks[i][2] = i;
        }

        Arrays.sort(sortedTasks, Comparator.comparingInt(a -> a[0]));
        int time = 0, taskIndex = 0, orderIndex = 0;
        int[] order = new int[tasks.length];

        while (taskIndex < tasks.length || !nextTask.isEmpty()) {
            if (nextTask.isEmpty() && time < sortedTasks[taskIndex][0]) {
                time = sortedTasks[taskIndex][0];
            }

            while (taskIndex < tasks.length && sortedTasks[taskIndex][0] <= time) {
                nextTask.offer(sortedTasks[taskIndex]);
                taskIndex++;
            }

            int[] currentTask = nextTask.poll();
            time += currentTask[1];
            order[orderIndex++] = currentTask[2];
        }

        return order;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution sol = new Solution();
        int n = scanner.nextInt();
        int[][] tasks = new int[n][2];
        for (int i = 0; i < n; i++) {
            tasks[i][0] = scanner.nextInt();
            tasks[i][1] = scanner.nextInt();
        }
        System.out.println("Processing Order:");
        int[] order = sol.getOrder(tasks);
        for (int i : order) {
            System.out.print(i + " ");
        }
        System.out.println();
        scanner.close();
    }
}
```


## Output:

<img width="413" height="598" alt="Screen Shot 1947-08-25 at 20 29 38" src="https://github.com/user-attachments/assets/999875ed-5808-425d-89a6-1df7128f99b0" />


## Result:
Thus the Java program to determine the processing order of tasks on a single-threaded CPU is implemented successfully.

