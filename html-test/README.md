# Caesar

{% video https://www.youtube.com/watch?v=Rg8P1wHDc0s %}

{% next %}

## Et tu?

Supposedly, Caesar (yes, that Caesar) used to "encrypt" (i.e., conceal in a reversible way) confidential messages by shifting each letter therein by some number of places. For instance, he might write A as B, B as C, C as D, ..., and, wrapping around alphabetically, Z as A. And so, to say HELLO to someone, Caesar might write IFMMP. Upon receiving such messages from Caesar, recipients would have to "decrypt" them by shifting letters in the opposite direction by the same number of places.

The secrecy of this "cryptosystem" relied on only Caesar and the recipients knowing a secret, the number of places by which Caesar had shifted his letters (e.g., 1). Not particularly secure by modern standards, but, hey, if you're perhaps the first in the world to do it, pretty secure!

Unencrypted text is generally called _plaintext_. Encrypted text is generally called _ciphertext_. And the secret used is called a _key_.

To be clear, then, here's how encrypting `HELLO` with a key of 1 yields `IFMMP`:

| plaintext    | H | E | L | L | O |
|--------------|---|---|---|---|---|
| + key        | 1 | 1 | 1 | 1 | 1 |
| = ciphertext | I | F | M | M | P |

More formally, Caesar's algorithm (i.e., cipher) encrypts messages by "rotating" each letter by _k_ positions. More formally, if _p_ is some plaintext (i.e., an unencrypted message), _p<sub>i</sub>_ is the _i<sup>th</sup>_ character in _p_, and _k_ is a secret key (i.e., a non-negative integer), then each letter, _c<sub>i</sub>_, in the ciphertext, _c_, is computed as

c<sub>i</sub> = (p<sub>i</sub> + k) % 26

wherein `% 26` here means "remainder when dividing by 26." This formula perhaps makes the cipher seem more complicated than it is, but it's really just a concise way of expressing the algorithm precisely. Indeed, for the sake of discussion, think of A (or a) as 0, B (or b) as 1, ..., H (or h) as 7, I (or i) as 8, ..., and Z (or z) as 25. Suppose that Caesar just wants to say Hi to someone confidentially using, this time, a key, _k_, of 3. And so his plaintext, _p_, is Hi, in which case his plaintext's first character, _p<sub>0</sub>_, is H (aka 7), and his plaintext's second character, _p<sub>1</sub>_, is i (aka 8). His ciphertext's first character, _c<sub>0</sub>_, is thus K, and his ciphertext's second character, _c<sub>1</sub>_, is thus L. Can you see why?

{% spoiler "Hints" %}

* Recall that `argc` and `argv` give you information about what was provided at the command line.
* Recall that `argv` is an array of strings.
* Recall that with `printf` we can print a string using `%s` as the placeholder.
* Recall that computer scientists like counting starting from 0.
* Recall that we can access individual elements of an array, such as `argv` using square brackets, for example: `argv[0]`.

{% endspoiler %}

{% next %}

## Your Turn

Now it's time to tie everything together! Instead of shifting the characters by 1, modify `caesar.c` to instead shift them by the actual key value. And be sure to preserve case! Uppercase letters should stay uppercase, lowercase letters should stay lowercase, and characters that aren't alphabetical should remain unchanged.

{% spoiler "Hints" %}

* Best to use the modulo (i.e., remainder) operator, `%`, to handle wraparound from Z to A! But how?
* Things get weird if we try to wrap `Z` or `z` by 1 using the technique in the previous section.
* Things get weird also if we try to wrap punctuation marks using that technique.
* Recall that ASCII maps all printable characters to numbers.
* Recall that the ASCII value of `A` is 65. The ASCII value of `a`, meanwhile, is 97.
* If you're not seeing any output at all when you call `printf`, odds are it's because you're printing characters outside of the valid ASCII range from 0 to 127. Try printing characters as numbers (using `%i` instead of `%c`) at first to see what values you're printing, and make sure you're only ever trying to print valid characters!

{% endspoiler %}

{% next %}

## How to Submit

Execute the below, logging in with your GitHub username and password when prompted. For security, you'll see asterisks (`*`) instead of the actual characters in your password.

```
submit50 cs50/2018/fall/caesar
```
