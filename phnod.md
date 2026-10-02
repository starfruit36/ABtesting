## PH def

Some def (doesn't matter, just alternating quantifiers).

## Collapse theorem

If $\Sigma_i^p = \Pi_i^p$, then $\mathsf{PH} = \Sigma_i^p$.

If $\mathsf{P} = \mathsf{NP}$, then $\mathsf{PH} = \mathsf{P}$.

- $\mathsf{P} = \mathsf{NP}$: induction, $\exists$ = ok, $\Sigma_i^p = \exists(\Pi_{i-1}^p = \text{ind})$ = ok,
- $\exists(\forall\exists\forall\cdots) = \forall(\exists\forall\exists\cdots)$: prlly just induction up like prev.

## PH-complete

If $L$ is $\mathsf{PH}$-complete, there exists a collapse level ($L$ is in a level, so that is that).

## Alternating TMs

AB TMs have 2 transition functions only, $\delta_0$ and $\delta_1$, which is neat.

Config graph mark ($1$ for $\exists$, $2$ for $\forall$); if start marked, accept, then cool.

Level $i$ allows $i-1$ alternating marks.

## AP, APSPACE, AL

$\mathsf{AP} = \mathsf{PSPACE}$ (yes), proof = $\mathsf{TQBF}$ proof, aka just guess bro.

$\mathsf{APSPACE} = \mathsf{EXP}$, $\mathsf{AL} = \mathsf{P}$ (config graph size + exponent identity, I suppose).

## Time-space tradeoff for SAT

$\mathsf{SAT} \notin \mathsf{TISP}(n^c, n^d)$ for $(c+d)c < 2$ (and more cutting edge).

The proof below is for $\mathsf{NTIME}(n) \not\subseteq \mathsf{TISP}(n^{1.2}, n^{0.2})$.

- $\mathsf{TISP}(n^{12}, n^2)$: split at $n^6$, add space $n^2$ for $n^8$ cert check,
- if $\mathsf{NTIME}(n) \subseteq \mathsf{DTIME}(n^{1.2})$, then $\Sigma_2\mathsf{TIME}(n^8) \subseteq \mathsf{NTIME}(n^{9.6})$ ($8 \times 1.2$ ig),
- chain to get $\mathsf{NTIME}(n^{10}) \subseteq \mathsf{NTIME}(n^{9.6})$ (contradicts hierarchy).

## Oracle def

Same def.
