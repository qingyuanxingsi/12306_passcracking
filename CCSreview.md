##Reasonable Comments, Easy to Improve
- The distortion function section is rather useless, as it is not tested with real users. There are several problems: a) no one would go through the additional effort of applying the distortion function firstly as it would take much longer, thus, significantly decrease usability. b) Memorability was not tested and could still suffer as the authors do not enter their chosen password but something else (lack of motor memory?).
<span style="color:red">Test the distortion on real users need us to do crowd-sourcing. However, a good point is the motor memory. I think adding a gap-typed passowrd would help maintain a motor memory. But to do this, still we need real user study to support our point. </span>

- The Distortion Function in section 5 needs a rigorous security analysis and it's not clear how much security the Distortion Function adds compared to not using such a function at all.
<span style="color:red">It could be the easiest one to prove. As the password security community nowadays mostly use NIST entropy, $\alpha$ guesswork and $\beta$ success rate to measure the security of dataset, we can also do this.</span>



##Reasonable Comments, Hard to Improve
- The authors hypotheses and thus, their algorithm are based on the 12306 password leak. Then, they test their algorithm using exactly this database. Thus, it is no surprise that their approach works well. This would have to be tested with another dataset. Again, I understand that the other datasets are missing the personal information. Still, this makes the results unusable.
<span style="color:red">I am not sure which algorithm the reviewer is referring. No matter which algorithm it is, it is hard to find another set to test. Besides, there is no algorithm that heavily relies on 12306 dataset. We simply learn the fact that some personal information is in passwords and try to leverage it to do more </span>

- Even if the password database were complete, the results couldn't be generalized in a way that the authors do as the users of this website are solely Chinese (other datasets consist of a much wider, worldwide dataset). Thus, cultural differences and other things specific to living in China are very likely to have a big influence on the passwords. I acknowledge that there are schemes presented by the authors that can be found in the international datasets as well (e.g. "qwerty") but they do not contain personal information.
<span style="color:red">Above 2 comments all criticize there is only 1 dataset. But expanding the dataset is difficult as we discussed. Not easy to improve in this way</span>

- Ethical concerns: Using leaked passwords and additional personal information to that extent raises serious ethical concerns. Since the leaked account information seem to be reliable in terms of correct email addresses and so on, the authors should have reached out to all affected users by email and ask them to consent to the authors' research. Without this consent I would argue the data should not be used. 
<span style="color:red">It is nearly impossible to get consent from all affected users. But I think we can talk about ethical consideration in the paper, highlighting that we are not using the data in an individual identifiable way. Besides, the data is safe kept in a isolated harddrive and is only used for research purpose. </span>

- The main premise of this paper is using personal information to guess passwords that is not a new technique.

- The proposed attack although being an improvement over PCFG attacks, doesn't contribute much to this class of attacks apart from being targeted towards an individual victim.

- The idea to use distortion function is not novel, it is just another way to obfuscate the password that can be done by using hash functions.
<span style="color:red">The above 3 comments are criticizing the value of the ideas. We cannot do any improvement unless we have better ideas. </span>

- A user study should have been conducted to see if the proposed security measures for password protection is easier to use than present methods of password protection like password managers etc. as it puts the burden of remembering the distortion function on the user. If the functions are as simple as Caeser's cipher, it won't take long for a motivated attacker to figure it out. Hash function are a better alternative in my opinion.
<span style="color:red">The reviewer suggests to do a user study to show distortion function is easier to use than present methods. It would be quite difficult because present methods are MANY. To do so we need to compare this to graphical password, password manager, multi-factor passwords, bio-metric passwords, etc. To me it is not worth to do such measurements. The reviewer finally point out using hash function. I cannot agree with this idea because users may have the hardest time to remember a hashed password. </span>

##Unreasonable (Or mistake) Comments -- I could be wrong
- I understand why the authors chose this dataset. It has personal information of real users and only this way can the authors test their assumption. However, this is not a real leaked database of passwords but, as the authors point out themselves, a brute-forced set. Thus, we have to assume, that the attack was only able to mainly retrieve the already easy passwords? I am 100% certain that the numbers would be significantly different if this were indeed the real data set. So unfortunately, we cannot learn much from the analysis.
<span style="color:red">This is a real leaked database, not a brute-forced set, but we can explain more clearly in the paper. Besides, all leaked database need to go through a cracking phase to recover the plaintext passwords. Therefore no leaked database can reflect 100% real password distribution. This is the limitation of any leaked passwords analysis, instead of specific to our study </span>

- The authors make several statements without giving any evidence or references that prove those statements (e.g. "However, its passwords are more sparse than previously studied datasets because users concern passwords security more when creating passwords for critical service systems." (2.1.2) and "Besides, as people tend to memorize a sequence of number by it into 3-digit groups, we believe that a match of at least length 3 is likely to be a real match." (2.2.2)).
<span style="color:red">This is a rather minor review. password sparsity (2.1.2) has been presented in our paper because we found few users use trivial passwords and the most popular passwords are not condensed as other dataset. The (2.2.2) claim does not have evidence support. But it should not matter, we just choose a reasonable parameter. </span>

- In 3.3, the authors claim that deploying their Coverage metric as part of a password strength-meter would force users to select more secure passwords. I highly doubt this claim and it would have to be proven with a user study. 
<span style="color:red">I do not understand why the reviewer would highly doubt a coverage-embeded password meter can force users to select more secure passwords. To me, embedding Coverage addresses the problem of intensive personal information usage without degrading any security feature of the original password meter. We do not know how much this can improve password security (Maybe not that much). But it does have the advantage of easy implementation and no extra drawback. Yes doing a user study would help but it could be a little losing our focus as we are only talking about possible usage of Coverage.  </span>

