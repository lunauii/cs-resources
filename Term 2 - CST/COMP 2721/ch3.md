---
author:
label: "Chapter 3: Basic Error-Correcting Code Theory"
icon: code
---

# Chapter 3: Error-Correcting Code

## Terminology

**Data word** - the raw data word we want to protect and store, error-free

**Codeword** - the data word with extra bits added for integrity

**Code** - a set of valid words (ex: a dictionary)

**Parity** - whether a number is odd or even (or 1 or 0)

**Hamming Distance** - the minimum amount of different bits between any two codewords of a code

# Error-Correcting Codes
Error-correcting code consists of:
- Detecting errors in code (easy)
- Correcting errors in code (hard)

Okay, well, detecting a few errors is easy. But sometimes, errors are undetectable because there’s so many errors it ends up at a different, but valid, message.
- For example, say you try to text someone “wanna go to the club”, but you type “wanna go to the pub” instead. 
- There’s been an error, a typo, but it’s undetectable, because “pub” is a valid word, despite it being a typo of “club”.

This is an unsolvable problem; you cannot correct all errors. Instead, the goal’s to make it very unlikely for a message with errors to be interpreted as valid. The more differences between valid messages, the better.
- We differentiate valid messages by adding **redundant bits** to the data word. Adding lots of redundancy is ideal, but also becomes more inefficient the more bits you add.

Error correction is a trade-off between **clarity** and **efficiency**. To get clearer data words, we need longer codewords with lots of differences between them. More dissimilar valid words make it easier to correct errors.

## Worst-Case Scenarios
Error correction goes by probabilities. We look for the nearest valid data word for a given code word, and assume that that’s the data word the code word was transferring. If there hasn’t been that many errors while transferring the code, this works pretty well!

However, there are **three unlikely, worst-case scenarios** in code transferring:
- A received code is halfway between two valid solutions (detectable, but impossible to fix)
- A received code has been messed up enough to seem like less errors occurred than how much actually happened (detectable, but will be fixed incorrectly)
- A received code has completely messed up and stumbled into becoming another valid solution (undetectable, won’t be fixed at all)

### Example: Code A
Imagine a code word comprised of 8 bits, two possible values for each bit, and only two valid values:
- 0000 0000
- 1111 1111

In this case, the worst scenarios would be:
- 0000 0000 → 0000 1111
  - There’s definitely an error, but the code won’t know how to decipher it. Is it 0000 0000? Or is it 1111 1111? There’s no way to tell.
- 0000 0000 → 0011 1111
  - There’s definitely an error, but the code interprets less errors than there actually are. This codeword gets wrongly corrected to 1111 1111, instead of 0000 0000.
- 0000 0000 → 1111 1111
  - The code doesn’t see an error with this, even though there is. The codeword got corrupted so much, it wrapped back around into seeming like a different, but valid, codeword.

### Example: Code B
Now, imagine a code comprised of 8 bits, two possible values for each bit, and only two INvalid values:
- 0000 0000
- 1111 1111

Every other combination of bits is valid in this code.

This code is very bad because it’s nearly impossible to figure out if there’s an error. It has zero correctability. If you looked at any valid codeword, say, 0101 1101, you wouldn’t be able to tell if an error occurred or not. The sender might have wanted to send 0001 1101 instead, but the recipient wouldn’t know!

Code A **wasn’t space efficient**, but offered **clarity**.
Code B was **very space efficient**, but **did not offer** clarity.

### Hamming Distance
The Hamming Distance of a code is the minimum distance between any 2 valid words in that code.\
In Code A, the Hamming Distance is 8 bits, as there are 8 bits of difference between the two codewords.

Ex: Look at this 6-bit code with three valid words.
- 000 000
- 000 011
- 111 111
The distance between the latter two code words is 2 bits. Therefore, this code has a Hamming Distance of 2.

A code with Hamming Distance of h bits can:
- Detect all errors consisting of up to $h - 1$ bits
  - At $h$-bit errors, the codeword may seem valid (see: worst-case scenario #3)
- Correct all errors consisting of up to $h/2 - 1$ bits
  - At $h/2$ bits, it may be unclear as to which valid solution the codeword was supposed to be (see: worst-case scenario #2)

Big Hamming Distance = large gap between valid codewords = good.

# Hamming Code
Hamming code takes in a data word, and inserts **parity bits** on every power of two to transform it into a codeword.
- Parity bits set the parity of their respective group of bits, by setting themselves to 0 or 1.
- Generally, when you create Hamming code, you want the parity of each parity bit to be even.
- If you want odd parity, just flip the parity bits.

## Parity Bit "Groups"
Parity bits each check the parity of a certain "group" of bits in a codeword.

The parity at bit 1 checks the following bits in a given codeword sequence:
- 1 0 1 0 1 0 1 0 1 0 1 0 1 0 1 0 …

The parity at bit 2 checks:
- 0 1 1 0 0 1 1 0 0 1 1 0 0 1 1 0 …

The parity at bit 4 checks:
- 0 0 0 1 1 1 1 0 0 0 0 1 1 1 1 0 …

The parity at bit 8 checks:
- 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 0 …

Say we have a data word of 0110 1100, and we want to encode it with Hamming code, with an EVEN parity.
> `1010 1100`

The first step to transform this into Hamming code is to insert spots for parity bits on bits 1, 2, 4, 8, etc. Every power of two.
> Inserting at bit 1: `_101 0110 0`\
> Inserting at bit 2: `__10 1011 00`\
> Inserting at bit 4: `__1_ 0101 100`\
> Inserting at bit 8: `__1_ 010_ 1100`

Next, examine the groups for each parity bit and set the parity for each group to be EVEN.
> Examining bit 1: `__1_ 010_ 1100`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; `↑-↑- ↑-↑- ↑-↑-`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; `--1- 0-0- 1-0-`\
> Parity is already even --> bit 1 is 0
>
> Inserting at bit 2: `0_1_ 010_ 1100`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp; `-↑↑- -↑↑- -↑↑-`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp; `--1- -10- -10-`\
> Parity is odd --> bit 2 becomes 1 to make it even
>
> Inserting at bit 4: `011_ 010_ 1100`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp; `---↑ ↑↑↑- ---↑`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp; `---- 010- ---0`\
> Parity is odd --> bit 4 becomes 1 to make it even
>
> Inserting at bit 8: `0111 010_ 1100`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp; `---- ---↑ ↑↑↑↑`\
> &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&nbsp; `---- ---- 1100`\
> Parity is even --> bit 8 is 0

And there you have your codeword!
> Final codeword: `0111 0100 1100`

If the parity of a parity bit doesn’t align with the parity of its group, that means either:
- There’s an error with several parity bits
- There’s an error in that parity bit’s group

The most likely statement is that there’s an error in that parity bit’s group. It’s not impossible that the parity bits are wrong, but it’s less likely.

> TO DO: Make an example of this\
> I don't feel like it rn though

Hamming code detects errors by having the parity of each data word bit covered by at least two parity bits. That way, errors can be narrowed down based on which parity bits don’t match their groups.

Hamming code is not that good of a code. It can only detect and correct a **single bit error**. Hamming code can’t correct multi-bit errors, and sometimes, it can’t even detect them either.

To recover the original data word from Hamming code:
- Remove all the parity bits
- Flip the intersection of all groups whose parity bits aren’t correct