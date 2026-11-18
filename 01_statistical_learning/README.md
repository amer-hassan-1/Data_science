# Statistical learning (ISL ch.2)

**Week:** 1
**Resource:** ISL ch.2
**Status:** read, notes written

## Method
Statistical learning is the process of applying mathematical functions to help
predict future observations — more precisely, estimating an unknown function f
that links predictors X to a response Y, using observed data.

Two reasons to do it, and they pull in opposite directions:
- **Prediction** — you only want an accurate Ŷ, so f can be a black box.
- **Inference** — you want to know how each predictor affects Y, so f has to be
  interpretable.

The goal decides the model, not the other way round.

## Assumptions
- **Training and test data come from the same distribution.** Everything else
  rests on this, and it is the first thing to break in production.
- There is a real f to estimate: Y = f(X) + ε, with ε independent of X and mean
  zero.
- ε is irreducible. Var(ε) is a floor on test error that no model can beat. The
  classification equivalent is the Bayes error rate.
- Observations are independent — which is why random cross-validation splits
  leak on time-ordered data.

## When it fails
- **Training error is not evidence.** It falls monotonically as flexibility
  rises, while test error is U-shaped. Near-zero training error usually means
  overfit, not good.
- Flexibility trades bias for variance: bias falls, variance rises, and expected
  test error = bias² + variance + Var(ε). The right model sits at the bottom of
  the U, not at maximum flexibility.
- Small samples and noisy data push that optimum toward *less* flexible models.
- Non-parametric methods like KNN degrade badly in high dimensions — the curse
  of dimensionality, where "nearby" stops meaning anything.
- If train and test distributions differ, test error is optimistic and the whole
  framework misleads rather than merely underperforming.

## Notes
Two things that didn't click on the first read.

**The Bayes classifier.** Assigns each observation to the class with the highest
P(Y = j | X = x). It is provably optimal, and that is its entire job — a
benchmark, not a method. You cannot run it on real data because it requires the
true conditional distribution, which is exactly what you are trying to learn.
ISL can draw its decision boundary only because the data is simulated. KNN,
logistic regression and LDA/QDA are all attempts to estimate the same quantity
by different routes. Not to be confused with Naive Bayes, which is a real
algorithm with a strong independence assumption.

**Where the 0.5 comes from.** The rule is an argmax over classes, not a
threshold. With two classes the probabilities sum to 1, so "pick the larger" and
"is P > 0.5" are the same question. With three classes there is no threshold at
all. And 0.5 minimises