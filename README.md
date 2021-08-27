# CoRL_rebuttal_paper_235

Dear reviewer,

here we present the results on our additional experiments evaluating the effectiveness of robust GAILFO for perturbations different than the ones induced by a friction or mass change in MuJoCo.

**The environment**

We consider a continuous gridworld, we denote the horizontal coordinate as \\( x \\) and vertical one as \\( y \\). We enforce spatial constarints, i.e. \\( x \in [0,1], y \in [0,1] \\).

The agent starts in coordinates \\([0, 1]\\) (the upper left corner) and the episode ends when the agent reaches the lower right region defined by the indicator function $\mathbf{1}\bc{x\in [0.95, 1], y \in [-1, -0.95]} $.

The reward function is given by:
\begin{equation}
R(x,y) = -(x-1)^2 -(y+1)^2 -80 e^{-8(x^2 + y^2)} + 10 \cdot \mathbf{1}\bc{x\in [0.95, 1], y \in [-1, -0.95]} 
\end{equation}

In addition, the actions space for the agent is given by $\mathcal{A} = [-0.5, 0.5]^2$ and the transition dynamics are given by:

\begin{equation}
    s_{t+1} = \begin{cases}
& s_t + \frac{a_t}{10} \quad \text{w.p.} \quad 1 - \epsilon \\
& s_t - \frac{s_t}{10\norm{s_t}_2} \quad \text{w.p.} \quad \epsilon 
\end{cases}
\end{equation}

The parameter $\epsilon$ can be varied to create a dynamic mismatch.

**The experiments**

We use three experts trained with $\epsilon = 0.0, \epsilon=0.05 \text{ and } \epsilon = 0.1$.

The learners act in a different environment with the following values for $\epsilon$: $0.0, 0.05, 0.1, 0.15 0.2$.

The following plots report the ablation study for different values of alpha for each of the 3 experts.

![Expert \epsilon = 0.0](https://github.com/lviano/CoRL_rebuttal_paper_235/blob/main/envGaussianGridworld-v0type2noiseE0.0/gaifoGaussianGridworld-v0bestTrue_0_1_2_normalized_reward.pdf) 

![Expert \epsilon = 0.0](envGaussianGridworld-v0type2noiseE0.0/gaifoGaussianGridworld-v0bestTrue_0_1_2_normalized_reward.pdf) 
