import java.util.*;
import java.io.*;

public class ProgrammingAssignment3{ //642115001 Kornkanok Kanchana
    public static Stack operators = new Stack();         
    public static void main(String[] args) throws IOException{
        String location = "input.txt";
        File file = new File(location);
        Scanner sc = new Scanner(file);


        List<String> list = new ArrayList<>();
        while (sc.hasNextLine()) {

        list.add(sc.nextLine());

    for (String line : list) {
        System.out.println("Infix expression: " + line + " " + "\nPostfix expression: " + toPostfix(line));
        System.out.println();
    }
    }
    sc.close();
    }

    private static String toPostfix(String infix) {
        char symbol;
        String postfix = "";
        for(int i=0;i<infix.length();++i){  
            symbol = infix.charAt(i);
            if (Character.isLetter(symbol)) {
                postfix = postfix + symbol;  
            }
            else if 
                (symbol=='(') {
                    operators.push(symbol);
            }
            else if (symbol==')') {
                while (operators.peek() != '(') {
                postfix = postfix + operators.pop();
            }
            operators.pop();
            }
            else {
                while (!operators.isEmpty() && !(operators.peek()=='(') && prec(symbol) <= prec(operators.peek()))
                postfix = postfix + operators.pop();
                operators.push(symbol);
            }
        }

        while (!operators.isEmpty()){
            postfix = postfix + operators.pop();
        }
            return postfix;      
}

public static int prec(char x) {
    if (x == '+' || x == '-'){
        return 1;  
    }
    if (x == '*' || x == '/' || x == '%') {
        return 2;  
    }
    return 0;  
}  
}  





Output:
Infix expression: a-b/(c+d-e)*(f^g*h+i) 
Postfix expression: abcd+e-/fgh*i+^*-

Infix expression: a-b/(c+d-e)*(f^g*h+i) 
Postfix expression: abcd+e-/fgh*i+^*-

Infix expression: 1+2+3^4 
Postfix expression: +1+23^4
[image](https://drive.google.com/file/d/1ePRPsIpSuOX8YT6loS0v83URM09Y1APV/view?usp=sharing)
