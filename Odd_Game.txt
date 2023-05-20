LinkedList.java:
---------------
public class LinkedList {
    public Node head;
    public LinkedList myList = null;
    public int counter = 1;
   public LinkedList(int d){
       
       head = new Node (d);
       
   }
      public void show(){
       
       Node current = head;
      if(current == null){
         System.out.println("There is no list to display"); 
      }else{ 
          System.out.println("Here is your list");
       while (current.next != null){
           System.out.print(current.data + " --> ");
           current = current.next;
          
       }
       System.out.println(current.data);
      }
       
   }
   public int calcTotal(){
       int total = 0;
       Node current = head;
       if(current == null){
           total = 0;
       }else{
           while(current.next != null){
              total = total + current.data;
              current = current.next;
           }
         total = total + current.data;  
       }
       return total;
   }
   
    public boolean addHead(int d){
        
        Node begin = new Node(d);
        begin.next = head;
        head = begin;
        
        return true;
    }
     public boolean addTail(int newData){
        Node end = new Node(newData);
        Node current = head;
        if(current == null){
         head = end;   
        }else{
        while(current.next != null){
            current = current.next;
        }
        current.next = end;
        }
        return true;
    }  
    public boolean delHead(){
        
        Node temp = head;
        head =  temp.next;
        return true;
    }
    public boolean delEnd(){
        Node current = head;
        Node prev = head;
        if(current.next == null){
            head = null;
           
        }else{
        while(current.next !=null){
            prev = current;
            current = current.next;
        }
         prev.next = null;
        }
       
        return true;
    }
    public int oddGame(int n){
     int newTotal = 0;
         if(n%2 == 1  && counter == 1 ){
             if(n%5 == 0){
                myList = new LinkedList(n*2);
                counter++;
               
             }else{
             myList = new LinkedList(n);
             counter++;
         
             }
          }else if(n%2 == 1  && counter != 1){
             if(n%5 == 0){
                 myList.addHead(n*2);
            
             }else{
                myList.addTail(n);
                
             }
          }else if(n%2 == 0 && counter != 1){
              if(n%5 == 0){
                 myList.delHead(); 
              }else{
                  myList.delEnd();
              }
          }
          if(counter == 1){
             
          }else{
         
          newTotal = myList.calcTotal();
          if(newTotal >= 100){
            myList.show();  
            }
          }
        return newTotal;
    }
    
    
    
    
    
    
}

MyProgram.java:
--------------
import java.util.Scanner;

public class MyProgram
{
    public static int total = 0;
    public static void main(String[] args)
    {
        LinkedList myList = new LinkedList(0);
        Scanner kb = new Scanner (System.in);
      while(total <= 100){
          System.out.println("Enter a number");
          int in = kb.nextInt();
       total =  myList.oddGame(in);
         System.out.println("Score: " + total);
      }
      System.out.println("The game is over!\nYour final score is: " + total);
    }
}

Node.java:
---------
public class Node {
   
   int data;
   Node next = null;
   public Node(int d){
       
       data = d;
   }
}

