# EX 3B Hamiltonian Circuit Problem
## DATE:
## AIM:
To write a python program to check whether Hamiltonian path exits in the given graph.

## Algorithm
1. Start from each vertex and mark it as visited.
2. Try visiting all other vertices one by one using edges.
3. Use dynamic programming to remember visited sets and paths.
4. If you can visit all vertices exactly once, a Hamiltonian path exists.
5. If no such path is found after checking all options, return "NO".

## Program:
```
/*
Program to implement to check whether Hamiltonian path exits in the given graph.
Developed by: Vignesh M
Register Number: 212223240176
*/
```
```
def Hamiltonian_path(adj, N):
    dp = [[False for i in range(1 << N)] for j in range(N)]
    for i in range(N):
        dp[i][1 << i] = True
    for i in range(1 << N):
        for j in range(N):
            if ((i & (1 << j)) != 0):
 
                for k in range(N):
                    if ((i & (1 << k)) != 0 and
                             adj[k][j] == 1 and
                                     j != k and
                          dp[k][i ^ (1 << j)]):
                        dp[j][i] = True
                        break
    for i in range(N):
        if (dp[i][(1 << N) - 1]):
            return True
    return False
    #End here
    
adj = [ [ 0, 1, 1, 1, 0 ] ,
        [ 1, 0, 1, 0, 1 ],
        [ 1, 1, 0, 1, 1 ],
        [ 1, 0, 1, 0, 0 ] ]
 
N = len(adj)
 
if (Hamiltonian_path(adj, N)):
    print("YES")
else:
    print("NO")
```

## Output:
![image](https://github.com/user-attachments/assets/8cd7c45e-8115-40d0-abb5-a7a43332675c)




## Result:
The Hamiltonian path program executed successfully, and it determined whether a Hamiltonian path exists in the given graph.
