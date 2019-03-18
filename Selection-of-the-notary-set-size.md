# Selection of the notary set size

As mention in our consensus algorithm, we follow the hypergeometry distribution to decide the size of notary set.

Given a node set of size N, the ratio of Byzantine nodes is R, and the notary set size n, then, the probability of more than 1/3 of notary set be Byzantine nodes is

<p align="center">
  <img src="https://imgur.com/wszheq8.png" width="250">
</p>

We set the probability to be 10^-8; that is, there is one fault in more than 10000 years in expectation.
Assume R=1/5 and applying this equation, we can derive the size of notary set which is shown in the following figure.

![Alt text](https://docs.google.com/spreadsheets/d/e/2PACX-1vREyLJEd7CpHNUG3O-uDWQFbiNidL7j5QtoQtvAKw4cNA3KC9Vs7Za0DfkKcU9L_kafIYBWkO7adouO/pubchart?oid=1623853170&format=image)


We give two curves to approximate the data point.
The first one is y = 70.5 ln(x) - 264, which is the purple dash line and the second one is y = 74 ln(x) - 264, which is the green dash line.
Then, the following table is the resilience ratio to the Byzantine by giving the number of the size of notary set and probability 10^-8.



| node set size | notary set size | resilience | notary set size | resilience |
| -------- | -------- | -------- | --- | --- |
| 200 | 110 | 0.199 | 123 | 0.220 |
| 400 | 159 | 0.197 | 174 | 0.207 |
| 600 | 187 | 0.194 | 203 | 0.202 |
| 800 | 208 | 0.197 | 224 | 0.202 |
| 1000 | 223 | 0.197 | 252 | 0.202 |
| 1500 | 252 | 0.199 | 270 | 0.204 |
| 2000 | 272 | 0.199 | 291 | 0.207 |
| 4000 | 321 | 0.207 | 342 | 0.209 |


DEXON mainnet will use y = 70.5 ln(x) - 264 to decide the notary set size from the node set size.