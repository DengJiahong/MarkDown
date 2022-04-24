Statement: if $C \sqsubseteq D$ holds, then $\exists r.C \sqsubseteq \exists r.D$ holds.

Prove:

If $C \sqsubseteq D$ holds, we can know that $C^{\mathcal{I}} \subseteq D^{\mathcal{I}}$ holds for all models of $C \sqsubseteq D$ because of soundness.

To prove $\exists r.C \sqsubseteq \exists r.D$, we only need to prove $(\exists r.C)^{\mathcal{I}} \subseteq (\exists r.D)^{\mathcal{I}}$ because of completeness.

$ \begin{aligned} (\exists r.C)^{\mathcal{I}} &= { x \in \Delta^{\mathcal{I}} | \text{ exists } y \in \Delta^{\mathcal{I}} \text{ such that } (x, y) \in r^{\mathcal{I}} \text{ and } y \in C^{\mathcal{I}} } \ &\subseteq { x \in \Delta^{\mathcal{I}} | \text{ exists } y \in \Delta^{\mathcal{I}} \text{ such that } (x, y) \in r^{\mathcal{I}} \text{ and } y \in C^{\mathcal{I}} } \ &\quad, \cup { x \in \Delta^{\mathcal{I}} | \text{ exists } y \in \Delta^{\mathcal{I}} \text{ such that } (x, y) \in r^{\mathcal{I}} \text{ and } y \in (D^{\mathcal{I}} \setminus C^{\mathcal{I}}) } \ &= { x \in \Delta^{\mathcal{I}} | \text{ exists } y \in \Delta^{\mathcal{I}} \text{ such that } (x, y) \in r^{\mathcal{I}} \text{ and } (y \in C^{\mathcal{I}} \text{ or } y \in (D^{\mathcal{I}} \setminus C^{\mathcal{I}})) } \ &= { x \in \Delta^{\mathcal{I}} | \text{ exists } y \in \Delta^{\mathcal{I}} \text{ such that } (x, y) \in r^{\mathcal{I}} \text{ and } y \in D^{\mathcal{I}} } \ &= (\exists r.D)^{\mathcal{I}} \end{aligned} $

So if $C \sqsubseteq D$ holds, then $\exists r.C \sqsubseteq \exists r.D$ holds.

Statement: $\exists r.C$ is equivalent to $\le 1r.\top$.

Disprove:

Let $\Delta^{\mathcal{I}} = { a, b }, C^{\mathcal{I}} = { a }, r^{\mathcal{I}} = { (a, b) }$

So $(\exists r.C)^{\mathcal{I}} = \empty$ and $\le 1r.\top = { a, b }$, we can know that $(\exists r.C)^{\mathcal{I}} \neq (\le 1r.\top)^{\mathcal{I}}$

By the counterexample, $\exists r.C$ is not equivalent to $\le 1r.\top$ because of completeness.

Statement: $\le 0r.\top$ is equivalent to $\forall r.\bot$.

Prove:

For any models,

$ \begin{aligned} (\le 0r.\top)^{\mathcal{I}} &= { x \in \Delta^{\mathcal{I}} | \left| { y \in \Delta^{\mathcal{I}} | (x, y) \in r^{\mathcal{I}} \text{ and } y \in \top^{\mathcal{I}} } \right| \le 0 } \ &= { x \in \Delta^{\mathcal{I}} | { y \in \Delta^{\mathcal{I}} | (x, y) \in r^{\mathcal{I}} \text{ and } y \in \Delta^{\mathcal{I}} } = \empty } \ &= { x \in \Delta^{\mathcal{I}} | { y \in \Delta^{\mathcal{I}} | (x, y) \in r^{\mathcal{I}} } = \empty } \ &= { x \in \Delta^{\mathcal{I}} | \text{ there is no } (x, y) \in r^{I} } \end{aligned} $

$ \begin{aligned} (\forall r.\bot)^{\mathcal{I}} &= { x \in \Delta^{\mathcal{I}} | \text{ for all } y \in \Delta^{\mathcal{I}} \text{ with } (x, y) \in r^{\mathcal{I}} \text{ we have } y \in \bot^{\mathcal{I}} } \ &= { x \in \Delta^{\mathcal{I}} | \text{ for all } y \in \Delta^{\mathcal{I}} \text{ with } (x, y) \in r^{\mathcal{I}} \text{ we have } y \in \empty } \ &= { x \in \Delta^{\mathcal{I}} | \text{ there is no } (x, y) \in r^{I} } \end{aligned} $

So $(\le 0r.\top)^{\mathcal{I}} = (\forall r.\bot)^{\mathcal{I}}$ for any models.

And we can know that $\le 0r.\top$ is equivalent to $\forall r.\bot$ because of completeness.

Statement: $\forall r(A \sqcup B)$ is equivalent to $(\forall r.A) \sqcup (\forall r.B)$.

Disprove:

Let $\Delta^{\mathcal{I}} = { a, b, c }, A^{\mathcal{I}} = { a }, B^{\mathcal{I}} = { b }, r^{\mathcal{I}} = { (c, a), (c, b) }$

So $(\forall r.(A \sqcup B))^{\mathcal{I}} = { a, b, c }, ((\forall r.A) \sqcup (\forall r.B))^{\mathcal{I}} = { a, b }$, we can know that $(\forall r.(A \sqcup B))^{\mathcal{I}} \neq ((\forall r.A) \sqcup (\forall r.B))^{\mathcal{I}}$

By the counterexample, $\forall r(A \sqcup B)$ is not equivalent to $(\forall r.A) \sqcup (\forall r.B)$ because of completeness.

Statment: $\exists r.(A \sqcup B)$ is equivalent to $(\exists r.A) \sqcup (\exists r.B)$.

Prove:

To prove that $\exists r.(A \sqcup B)$ is equivalent to $(\exists r.A) \sqcup (\exists r.B)$, which is that $\empty \models \exists r.(A \sqcup B) \sqsubseteq (\exists r.A) \sqcup (\exists r.B)$ and $\empty \models (\exists r.A) \sqcup (\exists r.B) \sqsubseteq \exists r.(A \sqcup B)$, we can prove that $(\exists r.(A \sqcup B)) \sqcap \lnot ((\exists r.A) \sqcup (\exists r.B))$ is not satisfiable and $\lnot (\exists r.(A \sqcup B)) \sqcap ((\exists r.A) \sqcup (\exists r.B))$ is not satisfiable, too.

$\lnot ((\exists r.A) \sqcup (\exists r.B)) \equiv \lnot (\exists r.A) \sqcap \lnot (\exists r.B) \equiv (\forall r.\lnot A) \sqcap (\forall r.\lnot B)$

Prove $(\exists r.(A \sqcup B)) \sqcap (\forall r.\lnot A) \sqcap (\forall r.\lnot B)$ is not satisfiable:

$ \begin{aligned} & (1) & & & & x: (\exists r.(A \sqcup B)) \sqcap (\forall r.\lnot A) \sqcap (\forall r.\lnot B) \ & (2) & & \text{ from } (1) & & x: \exists r.(A \sqcup B) \ & (3) & & \text{ from } (1) & & x: \forall r.\lnot A \ & (4) & & \text{ from } (1) & & x: \forall r.\lnot B \ & (5) & & \text{ from } (2) & & (x, y): r \text{ and } y: A \sqcup B \text{ for fresh } y \ & (6) & & \text{ from } (3) \text{ & } (5) & & y: \lnot A \ & (7) & & \text{ from } (4) \text{ & } (5) & & y: \lnot B \ & (8.1) & & \text{ from } (5) \text{ & } (6) & & \text{contradiction: } y: A \text{ and } y: \lnot A \ & (8.2) & & \text{ from } (5) \text{ & } (7) & & \text{contradiction: } y: B \text{ and } y: \lnot B \ \end{aligned} $

$\lnot (\exists r.(A \sqcup B)) \equiv \forall r.\lnot (A \sqcup B) \equiv \forall r.(\lnot A \sqcap \lnot B)$

Prove $(\forall r.(\lnot A \sqcap \lnot B)) \sqcap ((\exists r.A) \sqcup (\exists r.B))$ is not satisfiable:

$ \begin{aligned} & (1) & & & & x: (\forall r.(\lnot A \sqcap \lnot B)) \sqcap ((\exists r.A) \sqcup (\exists r.B)) \ & (2) & & \text{ from } (1) & & x: \forall r.(\lnot A \sqcap \lnot B) \ & (3) & & \text{ from } (1) & & x: (\exists r.A) \sqcup (\exists r.B) \ & (4.1) & & \text{ from } (3) & & x: \exists r.A \ & (5.1) & & \text{ from } (4.1) & & (x, y): r \text{ and } y: A \text{ for fresh } y \ & (6.1) & & \text{ from } (2) \text{ & } (5.1) & & y: \lnot A \sqcap \lnot B \ & (7.1) & & \text{ from } (5.1) \text{ & } (6.1) & & \text{contradiction: } y: \lnot A \text{ and } y: A \ & (4.2) & & \text{ from } (3) & & x: \exists r.B \ & (5.2) & & \text{ from } (4.2) & & (x, y): r \text{ and } y: B \text{ for fresh } y \ & (6.2) & & \text{ from } (2) \text{ & } (5.2) & & y: \lnot A \sqcap \lnot B \ & (7.2) & & \text{ from } (5.2) \text{ & } (6.2) & & \text{contradiction: } y: \lnot B \text{ and } y: B \ \end{aligned} $

So $\exists r.(A \sqcup B)$ is equivalent to $(\exists r.A) \sqcup (\exists r.B)$.