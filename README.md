# Arbitrage-Free Neural SDEs for European Option Books

A mathematical and pedagogical study of neural stochastic differential equations
for modelling the joint dynamics of an underlying asset and a European call-option
price surface.

The report revisits **Arbitrage-free neural-SDE market models** by Samuel N. Cohen,
Christoph Reisinger and Sheng Wang, with expanded derivations, explanatory figures
and a critical discussion of the latent-factor representation.

**Main question:** how can a flexible, data-driven model capture option-price
dynamics while respecting financial no-arbitrage constraints?

**Author:** Laurent Martini-Bonnet.

**[Read the full report](Neural_SDE_European_Calls.pdf)**

## Approach

The framework represents a high-dimensional option-price surface using a small
number of latent factors. Neural networks parameterize the drift and diffusion
of an SDE governing these factors jointly with the underlying asset.

The central challenge is to reconcile three objectives:

- **Statistical accuracy:** reconstruct observed option prices with a compact
  factor representation.
- **Static no-arbitrage:** enforce consistency between options with different
  strikes and maturities.
- **Dynamic consistency:** analyse the conditions under which discounted traded
  prices admit a common martingale measure.

## Main steps

1. **Formulate the market model.** Normalize call prices and represent the surface
   in time-to-maturity and log-moneyness coordinates.
2. **Derive the constraints.** Study static price inequalities and dynamic
   no-arbitrage conditions, and express the static restrictions as a polytope in
   latent-factor space.
3. **Construct the factors.** Explain the PCA-based procedure that balances price
   reconstruction with static and dynamic arbitrage objectives.
4. **Learn constrained dynamics.** Describe neural drift and diffusion models,
   boundary conditions and training through an Euler-Maruyama approximation of
   transition densities.
5. **Examine validation.** Discuss the Heston stochastic-local-volatility benchmark,
   local drift/diffusion comparisons and distributional checks for simulated paths.
6. **Assess the representation.** Investigate nonlinear dependence between the
   decoded factors and motivate an alternative nonlinear decoder.

## Contributions of this report

- **Detailed mathematical exposition:** expand the reasoning behind the market
  model, arbitrage constraints, factor construction and constrained SDE formulation.
- **Pedagogical illustrations:** explain how boundary-aware drift and diffusion
  affect trajectories, distinguishing a hand-crafted illustrative simulation from
  a trained neural SDE.
- **Interpretation of validation:** clarify the distinction between reconstructing
  observed prices, recovering local dynamics and generating new trajectories with
  comparable statistical properties.
- **Critical analysis of the decoder:** examine whether additional linear factors
  partly compensate for the curvature of the option-price surface. Discuss a
  nonlinear autoencoder as a possible alternative to PCA-based decoding.

The autoencoder is a proposed research direction. Its performance and ability to
preserve no-arbitrage constraints are not established in this repository.

## Reading guide

| Report sections | Topic |
| --- | --- |
| 1-3 | Motivation, market model and latent-factor representation |
| 4 | Static and dynamic arbitrage constraints |
| 5 | Factor construction and reconstruction objectives |
| 6 | Neural SDE formulation and constrained dynamics |
| 7 | Synthetic-data and training procedure described in the study |
| 8 | Validation framework, interpretation and critique |

## Repository scope

This repository contains the PDF report. It does not currently include a standalone
training implementation, datasets or scripts reproducing all figures.

The neural-SDE framework and its original benchmark belong to Cohen, Reisinger and
Wang. The report explains and critically examines that work; numerical results
discussed from the reference paper should not be interpreted as a newly reproduced
benchmark. Continuous-time constraint arguments also need to be distinguished
from the behaviour of a numerical discretization.

## Reference

Samuel N. Cohen, Christoph Reisinger and Sheng Wang.
**Arbitrage-free neural-SDE market models.**
Applied Mathematical Finance, 30(1), 1-46, 2023.
[Paper and preprint](https://arxiv.org/abs/2105.11053).
