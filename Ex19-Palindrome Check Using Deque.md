# EX 19 Generate Bitonic Sequence of Length N from a Given Range

## AIM:
To write a Java program to generate a Bitonic Sequence of length N from integers in a given range [L, R], such that the first element is the maximum. If not possible, print "-1".

## Algorithm
1. Start  
2. Read integers N, L, R  
3. Check if it is possible to generate the sequence: if `R - L + 1 < N`, print "Not possible" and return  
4. Initialize a list to store the Bitonic sequence  
5. Calculate `incLen = (N + 1)/2` and `decLen = N - incLen`  
6. Add `incLen` increasing elements starting from L  
7. Add `decLen` decreasing elements starting from R  
8. Print the Bitonic sequence  
9. End

## Program:
```java
import java.util.*;

public class BitonicSequence {

    public static void bitonicSequence(int n, int L, int R) {
        if (R - L + 1 < n) {
            System.out.println("Not possible");
            return;
        }

        List<Integer> bitonic = new ArrayList<>();
        int incLen = (n + 1) / 2;
        int decLen = n - incLen;
        int peak = R;

        for (int i = 0; i < incLen; i++) {
            bitonic.add(L + i);
        }
        for (int i = 0; i < decLen; i++) {
            bitonic.add(peak - i);
        }

        for (int num : bitonic) {
            System.out.print(num + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int L = sc.nextInt();
        int R = sc.nextInt();
        bitonicSequence(n, L, R);
        sc.close();
    }
}
```



## Output:
<img width="422" height="212" alt="Screen Shot 1947-08-25 at 20 27 24" src="https://github.com/user-attachments/assets/3d3c9d44-6064-4bfd-bc38-efff88d97f8f" />


## Result:
Thus the Java program to generate a Bitonic Sequence of length N from a given range [L, R] is implemented successfully.

