---
geometry: "margin=1in"
---

# Naive Bayes Homework


| Size (L,S) | Color (R,G,B) | Output (P,N) |
| :--------: | :-----------: | :----------: |
|     L      |       R       |      P       |
|     S      |       B       |      P       |
|     S      |       B       |      N       |
|     L      |       R       |      N       |
|     L      |       B       |      P       |
|     L      |       G       |      N       |
|     S      |       B       |      P       |

|  Probability Name | Probability |
| :---------------: | :---------: |
|        P(P)       |     4/7     |
|        P(N)       |     3/7     |
|   P(Size=L\|P)    |     2/4     |
|   P(Size=S\|P)    |     2/4     |
|   P(Size=L\|N)    |     2/3     |
|   P(Size=S\|N)    |     1/3     |
|   P(Color=R\|P)   |     1/4     |
|   P(Color=G\|P)   |     0/4     |
|   P(Color=B\|P)   |     3/4     |
|   P(Color=R\|N)   |     1/3     |
|   P(Color=G\|N)   |     1/3     |
|   P(Color=B\|N)   |     1/3     |

- Relative Probabilities:
    - $P(P|S,B) = P(P) * P(Size=S|P) * P(Color=B|P) = 4/7 * 2/4 * 3/4 = 24/112 = 0.2143$
    - $P(N|S,B) = P(N) * P(Size=S|N) * P(Color=B|N) = 3/7 * 1/3 * 1/3 = 3/63 = 0.0476$
    - The predicted class will be Positive ($P$) based on `argmax`
- Real Probabilities:
    - $P(P|S,B) = 0.2143 / (0.2143 + 0.0476) = 0.82$
    - $P(N|S,B) = 0.0476 / (0.2143 + 0.0476) = 0.18$
