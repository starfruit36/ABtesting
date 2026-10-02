## Space classes, conf graph

$\mathsf{DTIME}(s(n)) \subseteq \mathsf{DSPACE}(s(n)) \subseteq \mathsf{NSPACE}(s(n)) \subseteq \mathsf{DTIME}(2^{O(s(n))})$.

Conf graph $G_{M,x}$: conf, dire graph. tl;dr, just a graph where nodes are configs at a time.

Has at most $2^{O(s(n))}$ nodes, a vertex can be described using $O(s(n))$. CNF $\varphi_{M,x}$ (don't care, didn't ask). Proof, encoding scheme.

## Space hierarchy (quick note)

If $f(n) = o(g(n))$, then $\mathsf{DSPACE}(f(n)) \subsetneq \mathsf{DSPACE}(g(n))$.

Same proof as time hierarchy (flip at space $g(n)$).

## TQBF PSPACE-complete

Sketch from memory, just brute force 1 try, after getting result erase and eval again. If $\exists$ then quick exit (get it, exist exit), $\forall$ analogous.

Completeness: transform to CNF (2 of config graph, but I cba).

## Savitch

$\mathsf{NSPACE}(s(n)) \subseteq \mathsf{DSPACE}(s(n)^2)$.

Split reachability in half, $2^{i-1}$, chain line of $\log n$ (reachability $\mathsf{NL}$) ($\sum_{i=1}^{n}$).

## NL: logspace reductions

Logspace red: normal log space (can tell $f(x)$ at index $i$, and whether $i \le |f(x)|$), or write-once tape.

- write-once $\to$ normal: keep counter on symbols written, output the same for desired index,
- normal $\to$ write-once: run for all indexes, ask for $f(x)$ at index $i$ each round, till $i > |f(x)|$ and halt.

## PATH NL-complete

Config graph (same proof as Savitch but), adj mat for graph. Just scan entry and uh, check trans func of at most 2 trans ($\delta_0, \delta_1$).

## Read-once cert

Read-once cert is a stream of guesses: bit 0/1 picks $\delta_0$ or $\delta_1$ in the conf graph (at most 2 choices). Old bits are gone unless stored on the work tape, same as an $\mathsf{NL}$ machine forgetting its guesses.

If can reread and stuff, $\mathsf{NP}$: cert works as free memory (store info), copy TQBF.

## NL = coNL (I-S theorem)

- cert of $v \in C_i$: easy (just check vertex lol),
- cert of $|C_i|$: (induction) (count neighbour of $C_{i-1}$),
- cert of $v \notin C_i$: no certificate for $v$, other cert valid up to $|C_i|$ (increasing vertex order, so read once is enough),
- cert of $v \notin C_i$, but induction: $v$ neighbour instead of $v$ membership in no cert check.

Pad up so $\mathsf{NSPACE}(s(n)) = \mathsf{coNSPACE}(s(n))$.
