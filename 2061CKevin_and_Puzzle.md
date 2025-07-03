## [Kevin and Puzzle](https://codeforces.com/problemset/problem/2061/C)

Every game configuration can be represented by a string $s$ of $\lbrace h,l \rbrace$ e.g. $s[i] = h$ iff the $i$ th classmate is honest.

Let $S_{i,h}$ (similarly $S_{i,l}$) be the set of all distinct possible game configurations considering only the first $i$ students and
given that classmate $i$ is honest (similarly lier). Notice any configuration in $S_{i,h}, i > 1$ has the form $sh$ where $s \in S_{i-1,h} \cup S_{i-1,l}$.
Therefore, $|S_{i,h}|$ is exactly how many different configuration can $s$ take (think of it as a varaible) so that $sh$ remains in $S_{i,h}$.
If $a_{i-1} = a_i$ then $s$ can be $any$ configuration in $S_{i-1,h}$ (1). On the other hand, if $s$ can be $some$ configuration in $S_{i-1,h}$, then  $a_{i-1} = a_i$ (2).
Similarly,
if $a_{i-2} + 1 = a_i$ then $s$ can be any configuration in $S_{i-1,l}$ (3). 
On the other hand, if $s$ can be $some$ configuration in $S_{i-1,l}$, then  $a_{i-2} + 1 = a_i$ (4).

To compute $|S_{i,h}|$, we have the following case :

- only $a_{i-1} = a_i$ holds, then $|S_{i,h}| = |S_{i-1,h}|$ (by 1, 4)

- only $a_{i-2} + 1 = a_i$ holds, then $|S_{i,h}| = |S_{i-1,l}|$ (by 2, 3)

- both $a_{i-1} = a_i$ and $a_{i-2} + 1 = a_i$ hold, as $S_{i-1,h}$ and $S_{i-1,l}$ are disjoint, we have $|S_{i,h}| = |S_{i-1,h}| + |S_{i,l}|$ (by 1,3)

- none holds, then $S_{i,h} = 0$ (by 2,4)

Similarly notice any configuration in $S_{i,l}, i > 1$ has the form $sl$ where $s \in S_{i-1,h}$. However, for any $s \in S_{i-1,h}$
$sl$ will be $S_{i,l}$. It follows $|S_{i,l}| = |S_{i-1,h}|$.

To conclude, given $|S_{i-1,h}|$ and $|S_{i-1,l}|$ one can compute $|S_{i,h}|$ and $|S_{i,l}|$ in $O(1)$ time. The base case can also be easily handled :
If $a_1 = 0$ then $|S_{1,h}| = 1$ else $|S_{1,h}| = 0$. $|S_{1,l}| = 1$. Therefore, the desired answer $|S_{n,h}| + |S_{n,l}|$ can be found in $O(n)$ time.
