# Kirei Attacks the Estate

For each node $i$ compute its largest alternating sum $L[i] = \max(danger[i] - S[p_i], danger[i])$ and its smallest alternating sum $S[i] = \min(danger[i] - L[p_i], danger[i])$. 

This's correct because the alternating sum along the vertical path starting from node $i$ to $j$ where $j\neq i$ is $danger[i] -$ 
the alternating sum along the vertical path starting from node $p_i$ to $j$. This quantity is maximized (minimized) when the quantity after the minus sign is minimized (maximized).

Doing this in BFS/DFS style takes $O(n)$ time.
