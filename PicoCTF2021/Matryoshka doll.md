# Write-up of the challenge "Matryoshka doll"

This challenge is part of the "Forensics" category and earns 30 points.

# Goal of the challenge

Le message suivant nous est donné **"Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one?"** que l'on pourrait traduire par :   
Les poupées Matriochka sont un ensemble de poupées en bois de taille décroissante placées les unes dans les autres. Quelle est la dernière? 

De plus une image d'une poupée nous est fourni 

The following message is given to us **"Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one?"**

In addition an image of a doll is provided to us

![enter image description here](https://i.ibb.co/F3JP2ZD/dolls.png)
## Basic functions

In a forensic challenge with an image it is common to start with a panel of functions to detect a flag. First of all **Exiftool** which allows access to the metadata (the additional information of an image) but here we do not get anything very interesting. **Strings** which allows access to all the legible characters of the image but once again no flag. We can also use another tool to check the layers but the answer lies elsewhere.

## The solution

By using **binwalk** we access the signature of the file and we can read that the image is a compressed file under zip. So we can unzip the image and get another image of a smaller doll. You must have understood the reasoning you must unzip the image until you get a text file: the flag.

If you liked this writeup you can star our repository.
