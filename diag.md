## Time hierarchy (quick note)

If $f(n)\log f(n) = o(g(n))$, then $\mathsf{DTIME}(f(n)) \subsetneq \mathsf{DTIME}(g(n))$.

Uni TM simulates $f(n)$ steps (log overhead); just let $D$ output $1 - M$ and complete the proof, roughly.

## Nondeterministic time hierarchy (quick note)

If $f(n+1) = o(g(n))$, then $\mathsf{NTIME}(f(n)) \subsetneq \mathsf{NTIME}(g(n))$.

Note: don't use $1 - x$, as $\mathsf{NP}$ vs. $\mathsf{coNP}$ is sketchy.

Lazy diag: pick $h$ with $f(n+1) \ll h(n) \ll g(n)$; tower $f(i+1) = 2^{h(f(i)+1)}$.

Find $n$ between input $i$ and $i+1$, simulate $n^{f(n)} + 1$; copy for in-between and reject on the boundary:

- $D(n) = M(n+1)$ inside the gap,
- $D(\text{end}) \neq M(\text{start})$.

Fat func to brute force $M$ branches ($2^{h(f(i)+1)}$) on input $1^{f(i)+1}$.

## Ladner (quick note)

If $\mathsf{P} \neq \mathsf{NP}$, there exists an $\mathsf{NPI}$ problem.

Blow holes in SAT: $x \in L \iff x \in \mathrm{SAT}$ and $f(|x|)$ even.

$M_i$ poly deciders, $r_i$ poly reductions (clocked). Stage $= f(n)$: stage $2i$ attacks $M_i$, stage $2i+1$ attacks $r_i$; even means $L = \mathrm{SAT}$ on that length, odd means empty.

$f(n)$: go through strings in shortlex order, at $x$ check

- stage $2i$: $M_i(x) \neq L(x)$,
- stage $2i+1$: $\mathrm{SAT}(x) \neq L(r_i(x))$,

advance if different. $L(x)$ needs $\mathrm{SAT}(x)$ (brute force) and $f(|x|)$ (recursive, fine since $|x| < n$ and simulation step is bounded by n). Stop after $n$ steps, output the stage. So $f$ is poly, nondecreasing, and passes a stage iff a witness exists.

$L \in \mathsf{NP}$ since $f$ is poly.

Stuck at $2i$: $L = \mathrm{SAT}$ from some length on and $M_i$ decides it in poly, so $\mathrm{SAT} \in \mathsf{P}$.

Stuck at $2i+1$: $L$ is finite, so in $\mathsf{P}$, and $r_i$ reduces $\mathrm{SAT}$ to it, so $\mathrm{SAT} \in \mathsf{P}$.

So never stuck: every $M_i$ fails ($L \notin \mathsf{P}$), every $r_i$ fails ($L$ not $\mathsf{NP}$-complete).

## Diag tech (complexity ver.)

There exist TMs that simulate other TMs, and TMs can be encoded efficiently (simulate over machine details).

## BGS: anti-diag simulation tech

$A = \mathrm{EXPCOM}$ (outputs $1$ within $2^n$ steps): $\mathsf{P}^A = \mathsf{NP}^A = \mathsf{EXPTIME}$.

$B$: for each P machine, pick a fresh big $n$, run it on $1^n$; if it rejects, put a length-$n$ string it never asked into $B$ (it can't ask all $2^n$).

Add strings gradually; run oracle for $2^n/c$ time, make sure it didn't decide all of $B$. Nondet guess covers all $2^n$, but in p time can't cover $2^n/c$ possibilities.

Computation is local: a chain of local checks gives global correctness (cf. Cook–Levin). Oracle is a wicked device: one query answers a global question, which breaks locality. So relativizing arguments can't use locality; non-relativizing ones (arithmetization, $\mathsf{IP} = \mathsf{PSPACE}$) do.
