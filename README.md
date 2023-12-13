# simple-active-learning
Just for Instance Segmentation Models.

Tooling for some really simple, heuristic based active learning strategies. Easy to understand, and fast to calculate over a lot of data.


1) Single model, internal differences, e.g. the same object, multiple predictions for different classes. 

2) Literally just the number of objects.

3) 2 models, and their disagreement. 

4) There should be a simple way to just do a calculation over the masks, like a per-pixel entropy.

We're going to use a crude temporary measure. Which is the sum of all of the scores, apart from the max score (assume that this score is correct)

```python
entropies = []
for each pixel:
   # keep all but the highest
   # if sorted defaults to ascending then
   scores = sorted(scores)[:-1]
   entropy = sum(scores != max score)
   entropies.append(entropy) 

total_entropy = sum(entropies)
```
