


import java.util.*;  
class Main{  
  
    public static int[] ShortestPath(int src , ArrayList<ArrayList<Integer>>adjList,int V){  
        int dist[] = new int[V];  
        Arrays.fill(dist,Integer.MAX_VALUE);  
        dist[src]= 0;  
        Queue<Integer>q=new LinkedList<>();  
        q.offer(src);  
        while(!q.isEmpty()){  
            int current = q.poll();  
            for(int neighbour : adjList.get(current)){  
                if(dist[neighbour] == Integer.MAX_VALUE){  
                    dist[neighbour] = dist[current] + 1;  
                    q.offer(neighbour);  
                }  
            }  
        }  
        return dist;  
    }  
  
  
  
    public static void main(String[] args){  
        Scanner sc = new Scanner(System.in);  
        System.out.println("Enter the no.of vertices");  
        int V = sc.nextInt();  
        ArrayList<ArrayList<Integer>> adjList = new ArrayList<>();  
        for(int i=0;i<V;i++){  
            adjList.add(new ArrayList<>());  
        }  
        System.out.println("Enter the no.of edges");  
        int E = sc.nextInt();  
        System.out.println("Enter the edges");  
        for(int i=0;i<E;i++){  
            int u = sc.nextInt();  
            int v = sc.nextInt();  
            adjList.get(u).add(v);  
            adjList.get(v).add(u);  
        }  
        System.out.println("Enter the source:");  
        int source = sc.nextInt();  
        int dist[] = ShortestPath(source,adjList,V);  
  
        System.out.println("Shortest Path:");  
        for(int i=0;i<V;i++){  
            System.out.println(i+" "+dist[i]);  
        }  
  
    }  
}