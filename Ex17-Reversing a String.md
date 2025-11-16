# EX 17 Convert Infix Expression to Postfix

## AIM:
To write a Java program to convert an infix expression to its equivalent postfix expression using a stack.

## Algorithm
1. Start  
2. Read the infix expression  
3. Initialize an empty stack for operators  
4. Traverse the expression character by character:  
   - If the character is an operand, append it to the result  
   - If '(', push it to the stack  
   - If ')', pop from the stack until '(' is encountered  
   - If an operator, pop all operators from the stack with higher or equal precedence and push the current operator  
5. After traversal, pop any remaining operators from the stack and append to the result  
6. Print the postfix expression  
7. End

## Program:
```java
import java.util.Scanner;
import java.util.Stack;

public class InfixToPostfix {
    
    static int prec(char c) {
        if (c == '^') return 3;
        else if (c == '/' || c == '*') return 2;
        else if (c == '+' || c == '-') return 1;
        else return -1;
    }

    static String infixToPostfix(String s) {
        String val = "";
        Stack<Character> st = new Stack<>();
        
        for(char ch : s.toCharArray()){
            if(Character.isLetterOrDigit(ch)){
                val += ch;
            }
            else if(ch == '('){
                st.push(ch);
            }
            else if(ch == ')'){
                while(!st.isEmpty() && st.peek() != '('){
                    val += st.pop();
                }
                st.pop();
            }
            else{
                while(!st.isEmpty() && prec(st.peek()) >= prec(ch)){
                    val += st.pop();
                }
                st.push(ch);
            }
        }
        while(!st.isEmpty()){
            val += st.pop();
        }
        return val;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String exp = scanner.nextLine().replaceAll("\\s+", "");
        String postfix = infixToPostfix(exp);
        System.out.println("Postfix expression: " + postfix);
        scanner.close();
    }
}
```


## Output:
<img width="754" height="150" alt="Screen Shot 1947-08-25 at 20 23 20" src="https://github.com/user-attachments/assets/e73edd98-8819-4175-92a5-bbfffd77c503" />


## Result:
Thus the Java program to convert an infix expression to postfix form using a stack is implemented successfully.

