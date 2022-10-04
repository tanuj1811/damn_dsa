# Infix Notation

Infix is the day to day notation that we use of format A + B type. The general form can be classified as (a op b) where a and b are operands(variables) and op is Operator.

Example : A + B

# Postfix Notation

Postfix is notation that compiler uses/converts to while reading left to right and is of format AB+ type. The general form can be classified as (ab op) where a and b are operands(variables) and op is Operator.

Example : AB+

# Prefix Notation
Prefix is notation that compiler uses/converts to while reading right to left (some compilers can also read prefix left to right) and is of format +AB type. The general form can be classified as (op ab) where a and b are operands(variables) and op is Operator.

Example : +AB

# Infix to Postfix
```
import java.util.Stack;

public class InfixtoPostfix {
	public static void main(String[] args) {
		String exp = "a+b*(c^d-e)^(f+g*h)-i";
		System.out.println(infixToPostfix(exp));
	}
	public static int Precidense(char ch) {
		switch (ch){
      case '+':
      case '-':
			  return 1;
	
      case '*':
      case '/':
        return 2;

      case '^':
        return 3;
		}
		return -1;
	}
	
	public static String infixToPostfix(String exp) {
		String result = "";
		Stack<Character> stack = new Stack<>();
		
		for (char c:exp.toCharArray()) {
			if (Character.isLetterOrDigit(c))
				result += c;
			else if (c == '(')
				stack.push(c);
			else if (c == ')') {
				while (!stack.isEmpty() && stack.peek() != '(')
					result += stack.pop();
					stack.pop();
			}
			else {// an operator is encountered
				while (!stack.isEmpty() && Precidense(c) <= Precidense(stack.peek()))
					result += stack.pop();	
				stack.push(c);
			}
	
		}
		while (!stack.isEmpty()){
			if(stack.peek() == '(')
				return "Invalid Expression";
			result += stack.pop();
		}
		return result;
	}
}
```

# Infix to Prefix
```
import java.util.Stack;
public class InfixToPreFix {
    static int precedence(char c){
        switch (c){
            case '+':
            case '-':
                return 1;
            case '*':
            case '/':
                return 2;
            case '^':
                return 3;
        }
        return -1;
    }

    static String infixToPreFix(String expression){

        StringBuilder result = new StringBuilder();
        StringBuilder input = new StringBuilder(expression);
        input.reverse();
        Stack<Character> stack = new Stack<Character>();

        char [] charsExp = new String(input).toCharArray();
        for (int i = 0; i < charsExp.length; i++) {

            if (charsExp[i] == '(') {
                charsExp[i] = ')';
                i++;
            }
            else if (charsExp[i] == ')') {
                charsExp[i] = '(';
                i++;
            }
        }
        for (int i = 0; i <charsExp.length ; i++) {
            char c = charsExp[i];

            //check if char is operator or operand
            if(precedence(c)>0){
                while(stack.isEmpty()==false && precedence(stack.peek())>=precedence(c)){
                    result.append(stack.pop());
                }
                stack.push(c);
            }else if(c==')'){
                char x = stack.pop();
                while(x!='('){
                    result.append(x);
                    x = stack.pop();
                }
            }else if(c=='('){
                stack.push(c);
            }else{
                //character is neither operator nor "("
                result.append(c);
            }
        }

        for (int i = 0; i <=stack.size() ; i++) {
            result.append(stack.pop());
        }
        return result.reverse().toString();
    }

    public static void main(String[] args) {
        String exp = "A+B*(C^D-E)";
        System.out.println("Infix Expression: " + exp);
        System.out.println("Prefix Expression: " + infixToPreFix(exp));
    }
}
```

# Evaluation of Postfix
```
import java.util.Stack;

public class Main {

    public static void main(String[] args) {
        String expression1 = "22*3+";
        //should print answer as 7
        evaluatePostfix(expression1);

        String expression2 = "32*2+";
        //should print answer as 8
        evaluatePostfix(expression2);

        String expression3 = "3*2+";
        //should print Not a valid expression
        evaluatePostfix(expression3);


    }
    public static int evaluate(int operand1, int operand2, char operator) {

        switch (operator) {
            case '+':
                System.out.println(operand1 + " + " + operand2);
                return operand1 + operand2;
            case '-':
                System.out.println(operand1 + " - " + operand2);
                return operand1 - operand2;
            case '/':
                System.out.println(operand1 + " / " + operand2);
                return operand1 / operand2;
            case '*':
                System.out.println(operand1 + " * " + operand2);
                return operand1 * operand2;
            default:
                return 0;
        }
    }

    static void evaluatePostfix(String expression) {

        System.out.println("Evaluating expression " + expression);
        Stack<Character> stack = new Stack<Character>();
        char[] array = expression.toCharArray();

        int i = 0;
        while (i < array.length) {
            //if its a digit put it in the stack
            if (Character.isDigit(array[i])) {
                stack.push(array[i]);
            } else {
                //always stack has to be of size of 2 , if not the expression is not valid
                if (stack.size() != 2) {
                    System.out.println("postfix expression is not valid");
                    return;
                }

                //get the operands by popping the stack
                int operand1 = Integer.parseInt(String.valueOf(stack.pop()));
                int operand2 = Integer.parseInt(String.valueOf(stack.pop()));

                //evaluate the operands using the operator
                int result = evaluate(operand1, operand2, array[i]);

                //push the result back to the stack
                stack.push(Character.forDigit(result, 10));
            }
            i++;
        }
        //print the result 
        System.out.println("result is " + stack.pop() + '\n');
    }
}
```
# Evaluation of Prefix
```
import java.util.Stack;

public class PrefixEvaluation {

    public static Double evaluate(double a, double b, char operator){
        switch (operator) {
            case '+':
                return a + b;
            case '-':
                return b - a;
            case '*':
                return a * b;
            case '/':
                if (a == 0)
                    throw new
                            UnsupportedOperationException("Cannot divide by zero");
                return b / a;
        }
        return 0.0;
    }
    public static Double convert(String expression) {

        StringBuilder input = new StringBuilder(expression);
        input.reverse();

        Stack<Double> stack = new Stack<>();
        for (int i = 0; i < input.length(); i++) {
            char c = input.charAt(i);

            //check if it is a space (separator)
            if(c==' ')
                continue;

            if (c == '*' || c == '/' || c == '^' || c == '+' || c == '-') {
                double s1 = stack.pop();
                double s2 = stack.pop();
                double temp = evaluate(s2, s1, c);
                stack.push(temp);
            } else {
                //if here means, its a digit

                //extract the characters and store it in num
                StringBuffer temp = new StringBuffer();
                while(Character.isDigit(c)) {
                    temp.append(c);
                    i++;
                    c = input.charAt(i);
                }
                i--;
                //push the number in stack
                double num = Double.parseDouble(temp.reverse().toString());
                stack.push(num);
            }
        }
        double result = stack.pop();
        return result;
    }

    public static void main(String[] args) {
        String exp = "- / * 20 * 50 + 3 6 300 2";
        System.out.println("Prefix Expression: " + exp);
        System.out.println("Evaluation: " + convert(exp));
    }
}
```

