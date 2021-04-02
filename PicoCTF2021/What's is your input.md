# Write-up of the challenge "What's is your input"

This challenge is part of the "Binary exploitation" category and earns 50 points.

# Goal of the challenge

The objective of the challenge is to enter the correct answers to 2 questions that a python program asks us. We have available the source code that we can use.

## Program structure

![enter image description here](https://i.ibb.co/Y7p6fwq/english-input.png)
## Problème

By reading the source code we understand that to obtain the flag we must answer the second question correctly. However, unlike the first question where the answer is identical each time the program is launched, the preferred city chosen is the result of a random choice of several cities unknown to the user.

## Security breach

The security flaw lies in 2 points: the version of python used **"Python2"** and the function used to retrieve the inputs of the user **"Input"**. Indeed by entering certain functions in input it is possible to inject code and therefore display what you want

## Solution

Several solutions exist, each more or less optimized. The best is to inject the following command `__import __ ('os'). System ('sh')` which consists in directly importing a shell to the user. The latter can thus cat the flag and even the names of the cities. You can directly cat the `__import __ ('os'). System ('cat flag')` flag or even try to brute force the program by choosing a city and repeat the program until it is chosen.

If you liked this writeup you can check our github with this [link](https://github.com/PoCInnovation/ReblochonWriteups/tree/master/PicoCTF2021) and star our repository.
