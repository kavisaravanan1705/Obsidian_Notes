public class prac {  
    static double maxArray(int a[] , int k){  
        int wsum =0;  
        int max = Integer.MIN_VALUE;  
        //int sum =0;  
        for(int i=0;i<k;i++){  
            wsum+=a[i];  
        }  
        for(int i =k;i<a.length;i++){  
            wsum = wsum - a[i-k] + a[i];  
            max = Math.max(wsum,max);  
        }  
        return (double) max/k;  
    }  
    public static void main(String[]args){  
        int a[] ={1,12,-5,-6,50,3};  
        int k=4;  
        double ans= maxArray(a,k);  
        System.out.println(ans);  
    }  
  
  
}