# Lab 3
## Breaking the *(easy)* **shift cipher**
### *A paean to the great Roman Empire*

<div align="center">

![roman emblem](https://upload.wikimedia.org/wikipedia/commons/thumb/8/83/Vexilloid_of_the_Roman_Empire.svg/320px-Vexilloid_of_the_Roman_Empire.svg.png?1511946932553)

</div>

### Keywords
`shift cipher`, `substitution cipher`, `frequency analysis`, `dictionary attack`

> ### Before I start explaining what has to be done, I'd like to say that I found [this](https://www.youtube.com/watch?v=UkLGHUur8HM) video extremely useful. 

> I'm not going to explain a lot of theory here about this, because information about **shift ciphers** is easily available and accessing [this link](https://www.wikiwand.com/en/Caesar_cipher) will give enough background for it to be able to understand what I'm talking about.

### Objective
A shift cipher is an encryption technique used even by the great, glorious, heroic, remarkable, talented, and noble **Caesar** (the Julius one) in his private correspondence.

> It is a type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet. For example, with a left shift of 3, `D` would be replaced by `A`, `E` would become `B`, and so on. 

So the message `THE GREAT FAF OF THE ROMAN EMPIRE`, if encrypted with a **right shift of `3`** becomes: `WKH JUHDW IDI RI WKH URPDQ HPSLUH`.

Your task will be to crack the shift cipher, plain and simple.

There are two approaches you could use to "break the code" (so to speak):

#### Frequency Analysis
We live in a world of patterns, and a smart cracker (or hacker) knows that he has to look for them. Even if all letters are equal, *some letters are more equal than others*, thus some of them are used more often.
Language analysts have identified the so called **letter distribution tables** which establish the frequency for a letter to be found in a text. [Here](https://www.math.cornell.edu/~mec/2003-2004/cryptography/subs/frequencies.html) you can find a small experiment of letter distribution in the `English` language, and [here](https://www.wikiwand.com/en/Letter_frequency) you can read some more about letter frequency.

You can use this knowledge to try and guess the `shift rule`, by analyzing the frequency of letters in your encrypted text. 

Example:
> GUR EBZNA RZCVER JNF GUR CBFG-EBZNA ERCHOYVP CREVBQ BS GUR NAPVRAG EBZNA PVIVYVMNGVBA, PUNENPGREVMRQ OL TBIREAZRAG URNQRQ OL RZCREBEF NAQ YNETR GREEVGBEVNY UBYQVATF NEBHAQ GUR ZRQVGREENARNA FRN VA RHEBCR, NSEVPN NAQ NFVN.

Making a frequency analysis on the above text you can conclude that the most used character is `R`. Assuming that the text is in English and knowing that the most used letter in the English language is `E` you can make the (wild) guess (that is not that wild, really) that `E` has been substituted by `R`, thus concluding that **right shift of `13`** has been used. Applying this rule on the above text, the following result ensues:

> THE ROMAN EMPIRE WAS THE POST-ROMAN REPUBLIC PERIOD OF THE ANCIENT ROMAN CIVILIZATION, CHARACTERIZED BY GOVERNMENT HEADED BY EMPERORS AND LARGE  TERRITORIAL HOLDINGS AROUND THE MEDITERRANEAN SEA IN EUROPE, AFRICA AND ASIA.

Looks that we hit the spot: perfectly readable English about the glorious Roman Empire.

*A small suggestion I could make is for you to continue analyzing not only the first most common letter in the text, but take into consideration the next few as well, to make sure that the text is in the language you believe it is in.*

#### Dictionary Attack *(sort of)*
[True Dictionary Attack](https://www.wikiwand.com/en/Dictionary_attack)
The premise of this method is to have a dictionary of most common used words of the language, as you try every possible shift, you check if the words from the dictionary are found in the message you are trying to decrypt.

Some might say that this method is more **brute** than the other one. <br>
(I tried to make a pun using **Brut**us, a dude from the Roman Empire. I'm not sorry.)
<div align="center">

![brutus](https://www.biography.com/.image/ar_1:1%2Cc_fill%2Ccs_srgb%2Cg_face%2Cq_80%2Cw_300/MTE4MDAzNDEwNDY1NTU1OTgy/marcus-junius-brutus-9229883-1-402.jpg)

</div>

The advantage of this method is that you could have multiple dictionaries (for different languages) thus giving you the flexibility of not knowing the language the message you are trying to crack was written in.


### Deadline *(Dr. Bostan Style)*
AB ZNRL MAX WXTWEBGX YHK MABL ETUHKTMHKR BL MAX MPXGMBXMA HY WXVXFUXK B PHNEW EBDX MH PBLA RHN ZHHW ENVD PBMA BM TGW ATOX T GBVX EBYX


> #### *hint* 
> You have to decode this


### Messages
Decrypt these:

1. WKHSWEC: WI XKWO SC WKHSWEC NOMSWEC WOBSNSEC, MYWWKXNOB YP DRO KBWSOC YP DRO XYBDR, QOXOBKV YP DRO POVSH VOQSYXC, VYIKV COBFKXD DY DRO DBEO OWZOBYB, WKBMEC KEBOVSEC. PKDROB DY K WEBNOBON CYX, RECLKXN DY K WEBNOBON GSPO. KXN S GSVV RKFO WI FOXQOKXMO, SX DRSC VSPO YB DRO XOHD.

2. XOXKR IETG BL MH UX VHGLBWXKXW, XOXKR XQIXWBXGM MKBXW TGW XOXKR FXMAHW MTDXG UXYHKX FTMMXKL TKX UKHNZAM MH MABL ETLM XQMKXFBMR. ZHHW HYYBVXKL WXVEBGX ZXGXKTE XGZTZXFXGML PAXKX MAX HWWL TKX MHH ZKXTM, TGW IKXYXK MAX XFIEHRFXGM HY LMKTMTZXF TGW YBGXLLX MH WXLMKHR MAX XGXFR TL FNVA TL IHLLBUEX PBMAHNM XQIHLBGZ MAXBK HPG YHKVXL.

3. RD QTAJ KTW YMJ WTRFS JRUNWJ NX ZSIJSNFGQD LWJFYJW YMFS KTW RDXJQK. YMJ LWJFYJXY JRUNWJ JAJW YT MFAJ JCNXYJI. N UQJILJ RD JYJWSFQ XJWANYZIJ FSI N FR KTWJAJW GTZSI YT XJWAJ NY, NS QNKJ FSI NS IJFYM. YMJD MFAJ RJWJQD LNAJS ZX: WTFIX, HJSYWFQ MJFYNSL, HTSHWJYJ, YMJ HFQJSIFW, FSI KQZXMNSL YTNQJYX FSI XJBJWX.

### Grading policy
**9** - implement the `frequency analysis` type of breaking the code and decipher the messages from the **Messages** subsection <br>
> Example <br>
> the key used is: `right shift 11`, the message is: "blablabla" <br>

**10** - implement so that you could decipher messages from languages different than English *(Romanian for example)*<br>

*(possible)* **extra points** - for clean and beautiful code.