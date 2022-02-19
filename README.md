//642115001 Kornkanok Kanchana

import java.util.*;

import java.io.*;

public class ProgrammingAssignment3{

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





public class Stack{

    char a[]=new char[100];  
    
    int top=-1;  
    
    public void push(char c) {
        try { 
        a[++top]= c;
    } catch(StringIndexOutOfBoundsException e) {
        System.out.println("Stack full, no room to push, size=100");
        System.exit(0);
    }
}  
    
    public char pop() {
        return a[top--];  
}

    public boolean isEmpty()  
{  
return (top==-1)?true:false;  
}

public char peek()  
{  
return a[top];  
}
}  




import java.io.File;

import java.util.Vector;

public class Node { 

    private File data;
    
    private Node next;
    
    private Vector<String> list;

    public Node(){
        this.data = null;
        this.next = null;
        list = new Vector<>();
    }
    public Node(File data, Node next, String x){
        this.data = data;
        this.next = next;
        list.add(x);
    }

    public File getData(){
        return data;
    }

    public void setData(File data){
        this.data = data;
    }

    public Node getNext(){
        return next;
    }

    public void setNext(Node next){
        this.next = next;
    }

    public String toString(){
        if(data == null){
    
            return "Node: null";
    
        }
    
        else{
    
            return "Node:" + data;
    
        }
    }
}
  
  
  
  
  
  public class LinkedList {
  
    private Node size;

    public LinkedList(){
        this.size = null;
    }

    public LinkedList(Node size){
        this.size = size;
    }

    public void setSize(Node size){
        this.size = size;
    }

    public Node getSize(){
        return size;
    }

    public boolean isEmpty(){
        if (size == null) {
            return true;
        }
        else{
            return false;
        }
    }

    public void add(Node node){
        if (getSize() == null){
            Node temp = new Node(null, null, null);
            temp.setNext(getSize());
            setSize(temp);
        }

        else{
            add(getSize());
        }
    }

    public  Node insert(Node node, int data) {
        Node temp;
        if (node == null) {
          node = new Node(null, null, null);
          return node;
        } else {
          temp = node;
          while (temp.getNext() != null) {
            temp = temp.getNext();
          }
          temp.setNext(new Node(null, null, null));
          return node;
        }
      }

    public void Delete(int position){
        if (size == null){
            return;
        }

        Node temp = size;

        if(position == 0){
            size = temp.getNext();
            return;
        }
        
        for (int i = 0; temp != null && i < position - 1; i++){
            temp = temp.getNext();
        }
        
        if (temp == null || temp.getNext() == null){
            return;
        }
        
        Node next = temp.getNext().getNext();
        
        temp.setNext(next);
    }

    public void DeleteAll(){
        Node temp = new Node(null, null, null);
        while(size != null) {
          temp = size;
          size = size.getNext();
          temp = null;
        }
        System.out.println("Delete All");
    }

    public void traversal(){
        traversal(getSize());
    }

    public void traversal(Node size){
    
        if(size != null){ 
        
            System.out.println(size);
            
            traversal(size.getNext());
        }
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
