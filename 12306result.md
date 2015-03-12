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
Considered that the average length of the password is 8.43. The rate does not seem much. However, the structure of passwords are usually combined with letters, symbols, and digits. The rate is underested.

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


#### 4.Coverage

Coverage will be an important factor for measuring the correlation of the passwords and personal informaiton. Coverage is defined as the ratio of the password that can be recovered from the personal information. In short, $cvg = {len(LCS) \over len(password)}$. Firstly we segmentize the passwords into "Letter", "Digits", and "Special Symbols". Then we try to map "Letter" and "Digits" with personal information (Map Letter with name, email, and account, map digits with birthday, email, cellphone, id number, and account). We map these segments by the following rules:
1. We find the longest common sequence (LCS) between each segment of password and each type of personal information that is used to mapping.
2. We select the longest common sequence as the candidate for each segment of password.
3. As a result we found a (and only one which is the longest) subset for each segment of the password, and we calculate how much the subsets can cover the entire password. 

Longest common sequence may not accurately indicate that the 2 sequences have certain relation. There might be coicidence that 2 irrelavent strings have some common sequence, say "12345678" and "19920303" have LCS "123", we introduce a threshold $\sigma$ to reduce the probability of such coincidences. That is to say, when the $len(Seg) \times \sigma >= len(LCS)$, the coverages counts, otherwise the coverage will be reset to 0 for this segment. The example above will then result in 0 coverage when $\sigma$ is chosen as 0.5 (len(LCS) needs to be at least 0)

We then calculate the coverage for different threshold.

|threshold| Coverage|threshold|Coverage|
|-------:|:--------:|:------:|:-------|
|0| 0.717 |0.6| 0.556 |
|0.1| 0.717 |0.7| 0.475 |
|0.2| 0.715 |0.8| 0.419 |
|0.3| 0.708 |0.9| 0.374 |
|0.4| 0.691 |1| 0.374 |
|0.5| 0.662 |




Note that ID number contains exactly the birthday in our dataset, and it contains too many digits which may have negative impact on our measurement, so we remove it and the result is:

|threshold| Coverage|threshold|Coverage|
|-------:|:--------:|:------:|:-------|
|0| 0.667 |0.6| 0.467 |
|0.1| 0.667 |0.7| 0.402 |
|0.2| 0.665 |0.8| 0.372 |
|0.3| 0.651 |0.9| 0.350 |
|0.4| 0.621 |1|0.350|
|0.5| 0.572 |


We can have the following observation:
1. Personal information has large correlation with password
2. Threshold $\sigma$ does reduce the probability of coincidence
3. Even with $\sigma = 1$, which means each segment in the password can be fully recovered from personal information, A significant number of password can be recovered. 

#### 5.New representation of password
Although coverage may be a good indicator of how passwords are correlated to personal information, we still do not know how the passwords are constructed from personal information and which type of information are mostly used. 

Therefore we create a new representation of password, which is useful in measurement and password cracking. This new representation is evolved from the original PCFG. We call it personal representation. Like original PCFG, personal representation consists of different "TYPES" of segments. An example is $[name_4][bd_8]$ or $[name-initial_2][cellphone_{11}]$

==TODO:Key stroke strings can be added==


####6. Personal Information Matching
We use a greedy algorithm to match the password with personal information. It involves multiple steps:
1. Find all the substrings of the password.
2. Sort the substrings by its length in descending order
3. From the longest length, try to match the personal information to the substrings. 
4. If a match is found, recursively found the segments left. 

For example, a string Chris19880808abc will be matched in the following order:

1. Find all the substring of Chris19880808abc
2. Try from Chris19880808abc, Chris19880808ab, and hris19880808ab to 19880808
3. A birthday is matched, substitute 19880808 with [BD], the password becomes Chris[BD]abc
4. Match Chris and abc separately with personal information again
5. A name is matched, the password becomes [NAME][BD]abc
6. abc is not matched to anything, it will then be represented using a PCFG convention
7. The password will finally be [NAME][BD]L3

####7. Matching rules 
By matching we mean the password substring is very related to a kind of personal information. Different kind of personal information is handled differently. 


|FORM|FREQUENCY|percentage|
|------:|:------:|:------|
|D7|7182|5.46%|
|[ACCT]|6915|5.26%|
|[BD]|5965|4.53%|
|D6|4930|3.75%|
|[NAME][BD]|4343|3.30%|
|D8|4272|3.25%|
|L1D7|3310|2.51%|
|[EMAIL]|3070|2.33%|
|[NAME]D7|2213|1.68%|
|L2D7|1966|1.49%|
|[NAME]|1859|1.41%|
|D9|1841|1.40%|
|[NAME]D3|1769|1.34%|
|[NAME]D6|1684|1.28%|
|L1D8|1655|1.25%|
|L6D3|1513|1.15%|
|L2D6|1482|1.12%|
|D7L1|1440|1.09%|
|L3D6|1356|1.03%|
|L1D6|1342|1.02%|



This may be the outline of the data analysis result
* Data Overview 
  * Data Structure Overview
  * Most commly usd passwords
* Coverage
* New representation of password ([name][birthday][special symbol])
* Which is the most relevant personal information, an analysis
* Gender Diff
  * Personal info struct
* Age Diff
  * Same as Gender diff



