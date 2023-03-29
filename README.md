# Cargo-Dropping-Ships
There is a cargo ship that contains an unlimited amount of cargo in it. The ship is ready to sail and you have a list of N non-negative integers which denotes the water level in the sea at the ith points. A wave is defined as the continuously decreasing water level or continuously increasing water level.

Let A= [1,2,6,4,2,3,1,8,9,7], it has 6 waves in it [1,2,6],[6,4,2],[2,3],[3,1],[1,8,9],[9,7]

The amount of cargo that falls into the sea is equal to the product of the smallest height of the wave and length of the wave.
You have to find the total amount of cargo which falls into the sea.

NOTE: No two adjacent value will be equal in the list.

Input:
First-line contains T-number of TestCases. Then for every test case,
• 1st line contains a non-negative integer N.
• The next line contains a list of N space-separated integer denoting the water level at the ith point.

Output:
The total amount of cargo that falls into the sea.

Constraints:
1 <= T <= 1e3
2 <= N <= 1e5
1 <= A[i] <= 1e5

Note: The sum of N in a test would not exceed 1e10

Sample test cases:

1
10
1 2 6 4 2 3 1 8 9 7

Sample output:
32
import java.util.*;
public class Main
{
	public static void main(String[] args) {
		Scanner in=new Scanner(System.in);
		int t=in.nextInt();
		while(t-->0){
		    int n=in.nextInt();
		    int a[]=new int[n];
		    for(int i=0;i<n;i++){
		        a[i]=in.nextInt();
		    }
		    int i=0,c=0,min=Integer.MAX_VALUE,j=0,s=0;
		    while(i<n){
		        c=1;
		        min=a[i];
		        j=i+1;
		        if(j==n){
		            break;
		        }
		        if(a[j]>a[i]){
		            while(j<n && a[j]>a[j-1]){
		                min=Math.min(a[j],min);
    		            c++;
    		            j++;
    		        }
		        }   
		        else{
		             while(j<n && a[j]<a[j-1]){
		                min=Math.min(a[j],min);
    		            c++;
    		            j++;
    		            
    		        }
		        }
		        s+=c*min;
		        i=j-1;
		    }
		    System.out.println(s);
		}
	}
}
