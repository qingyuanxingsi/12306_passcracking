##12306 Paper
###Preliminary Results:
#### 1. Structure of the passowrds:
The following table shows the most frequent 20 password structures, in which "D" represents digits, "L" represents letters, and "S" represent special characters. The number following the letters indicate the length of the segment. For example, password132 -> L7D3

|Structure | frequency| percentage|
|------:|:------:|:----|
|D7|10906|8.283%|
|D8|9458|7.184%|
|D6|9102|6.913%|
|L2D7|5073|3.853%|
|L3D6|4832|3.670%|
|L1D7|4778|3.629%|
|L2D6|4275|3.247%|
|L3D7|3885|2.950%|
|D9|3594|2.729%|
|L2D8|3371|2.560%|
|L4D4|3105|2.358%|
|L1D8|3103|2.356%|
|L6D3|2798|2.125%|
|L6D4|2476|1.880%|
|L7D3|2192|1.664%|
|L5D3|2158|1.639%|
|L5D4|2125|1.614%|
|L8|2079|1.579%|
|D7L1|1973|1.498%|
|L3D4|1879|1.427%|

The result is a little different from previous workds due to:
* No complicated password constraint is set.
* The nature of this website is different from others.


####2. Most frequently used passwords

NOTE:this is very different from previous research. The congregation is regarded much higher than this in Chinese Password set.

|PASSWORD|PERCENTAGE|
|-------:|:-------|
|123456|0.297%|
|a123456|0.213%|
|123456a|0.125%|
|5201314|0.122%|
|111111|0.119%|
|woaini1314|0.103%|
|123123|0.074%|
|qq123456|0.074%|
|000000|0.073%|
|1qaz2wsx|0.070%|
|1q2w3e4r|0.063%|
|qwe123|0.060%|
|7758521|0.057%|
|123qwe|0.051%|
|a123123|0.047%|
|woaini520|0.042%|
|123456aa|0.041%|
|1314520|0.039%|
|100200|0.039%|
|woaini|0.038%|

####3. Longest Common Sequence
Here we compute the coverage of longest common sequence, which is computed as $len(LCS) \over len(password)$

The results are shown below:

|Info | longest common sequence|longest common consecutive sequence|
|-------:|:-------:|:--------|
|Birthday |0.33 | 0.23|
|Name|0.17| 0.13|
|Email|0.32| 0.21|
|Tel|0.31| 0.16|
|Account|0.32| 0.24|
|ID Number|0.44| 0.27|
Considered that the average length of the password is 7. The rate does not seem much. However, the structure of passwords are usually combined with letters, symbols, and digits. The rate is underested.

Let's see the same rate for D7, D8, and D6, which are most commonly used structures (account for over 20% of all passwords)

for __D7__

|Info | longest common sequence|longest common consecutive sequence|
|-------:|:-------:|:--------|
| Birthday |0.376|0.226|
|Name|0.0|0.0|
|Email|0.326|0.207|
|Tel|0.425|0.215|
|Account|0.294|0.250|
|ID Number|0.572|0.277|

for __D8__

|Info | longest common sequence|longest common consecutive sequence|
|-------:|:-------:|:--------|
| Birthday |0.543|0.430|
|Name|0.0|0.0|
|Email|0.312|0.205|
|Tel|0.432|0.195|
|Account|0.238|0.194|
|ID Number|0.669|0.461|

for __D6__

|Info | longest common sequence|longest common consecutive sequence|
|-------:|:-------:|:--------|
| Birthday |0.532|0.390|
|Name|0.0|0.0|
|Email|0.319|0.220|
|Tel|0.462|0.236|
|Account|0.245|0.210|
|ID Number|0.695|0.445|

Now let's set a threshold of coverage to be 0.7 (most of the digits in password are covered) and compare the password to birthday.

|Dataset| longest common sequence|longest common consecutive sequence|
|-------:|:-------:|:--------|
| D7 |0.076|0.048|
| D8 |0.214|0.192|
| D6 |0.303|0.289|