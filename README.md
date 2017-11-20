# Problem2
import java.util.*;

public class Coin{
  
  public static void main(String args[]){
       Scanner input= new Scanner(System.in);
       int Max= 301;
       int cases = input.nextInt();
       ArrayList<Integer> x,y;
       
       while(cases>0){
         int m,S;
         m= input.nextInt();
         S= input.nextInt();
         x= new ArrayList<Integer> ();
         y= new ArrayList<Integer> ();
         int [][] store = new int[301][301];
         
         for(int i=0; i<m;i++){
           int conventional = input.nextInt();
           int infotech = input.nextInt();
           x.add(conventional);
           y.add(infotech);
         }
         
         for(int i=0; i<=S; i++){
           
           for(int j=0;j<=S;j++){
             store[i][j]= Max;
           }
         }
         
         store[0][0] =0;
         
         for(int i=0; i<m; i++){
           for(int v1 = x.get(i); v1<=S;v1++){
             for(int v2= y.get(i); v2<=S;v2++){
               if(store[v1-x.get(i)][v2-y.get(i)] != Max){
                 store[v1][v2] = Math.min(store[v1][v2],
                                 store[v1-x.get(i)][v2-y.get(i)]+1);
               }
             }
           }
         }
           
         int ans = Max;
           
         int temp = S*S;
           
         for(int i=0;i<=S; i++){
           for(int j=0;j<=S;j++){
             if(i*i+j*j == temp && store[i][j] != Max){
               if(ans > store[i][j]){
                 ans = store[i][j];
               }
             }
           }
         }
           
         if(ans!= Max){
           System.out.println(ans+"");
         }
         else{
           System.out.println("not possible");
         }
           
         cases--;
         
       }
      
}
}
  
