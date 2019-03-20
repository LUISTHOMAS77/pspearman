# Calculate the p-value significance of Spearman's rank correlation coefficient (Spearman's rho)
Spearman's rho is a measure of the monotonic correlation between two variables.
A useful property of Spearman's rho is that a p value can be
calculated determine the significance of the correlation.  The 
python numpy package has a calculation for the p value that uses
the Student's T distribution and is only valid for large numbers
of samples (n), e.g. > 500.  This pure python package calculates the
p value exactly for n <= 22 and uses a more accurate approximation
for n > 22. The approximation is described in Appl. Statist. (1975) Vol.24, No. 3, P377, 
<http://lib.stat.cmu.edu/apstat/89>.
 The code was translated from the R package 
pspearman, <https://cran.r-project.org/web/packages/pspearman/index.html> 

To use the code, let's assume that there are two parallel arrays, `rank1`
and `rank2` that contain matched ranked samples.  Then:

```python
from pspearman import *
import numpy as np
rank1 = [1, 2, 3]
rank2 = [1, 3, 2]
s = np.sum(np.square(np.array(rank1)-np.array(rank2)))
n = int(np.max([rank1, rank2]))
p = pspearman(s, n)
```

Lewis Geer
