# **Presentation**
The objective is to pretend to be a user who is accepted by the site to obtain the page with the flag.
# **Flaw to be exploited**
The flaw exploited is in the HTTP request, and more precisely in the headers thereof, which we send to the server that we can modify and which allows us to access the different pages.
# **Solution**
This solution is divided into several steps.
## Step 1
When we launch the challenge we arrive on this page.

![image](https://i.ibb.co/JrhhNwV/premiere-partie.png)

Note that only people coming from an official browser can access the real site.
We must therefore modify the header "User-Agent".
[Explanation of the effect of the header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent)
We therefore replace the value by :
`User-Agent: PicoBrowser`
## Step 2
After the first part we arrive on this page:

![image](https://i.ibb.co/p4rTk8s/2eme-partis.png)

He tells us that he doesn't believe users coming from other sites.
So we need to add the header :"Refer".
[Explanation of the effect of the header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referer)
Let's put this value :
`Referer: http://mercury.picoctf.net:36622/`
## Step 3
So we come to this page :

![image](https://i.ibb.co/q7KFWrv/3-partie.png)

We are told that the site only works in 2018.
So let's add the following header : "Date".
[Explanation of the effect of the header](https://developer.mozilla.org/fr/docs/Web/HTTP/Headers/Date)
Let's give it a date in 2018 like this :
`Date: Wed, 21 Oct 2018 07:28:00 GMT`
## Step 4
Once the request is sent this page appears :

![image](https://i.ibb.co/N6FJsrC/4-partie.png)

He tells us that he doesn't believe the users who are being stalked.
Let's add the following header : "DNT"
[Explanation of the effect of the header](https://developer.mozilla.org/fr/docs/Web/HTTP/Headers/DNT)
Insert this command in your request :
`DNT: 1`
## Step 5
This time the site brings us to this page :

![image](https://i.ibb.co/P6r0JSL/5-partie.png)

He tells us that he accepts people from Sweden.
We will therefore add the following header : "X-Forwarded-For"
[Explanation of the effect of the header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For)
You also need to find an IP address from Sweden.
I found one here : [Adresse ip from Sweden](https://awebanalysis.com/fr/ip-lookup/31.3.152.55/)
And we get a header like this :
`X-Forwarded-For: 31.3.152.55`
## Step 6
Finally we arrive on this page:

![image](https://i.ibb.co/THDTpCY/derniere-parti.png)

He wants us to speak Swedish to be able to access the last part.
We are therefore going to modify the following header : "Accept-Language"
[Explanation of the effect of the header](https://developer.mozilla.org/fr/docs/Web/HTTP/Headers/Accept-Language)
And let's put it the following value :
`Accept-Language: sv,en;q=0.9`
# Conclusion
The challenge is relatively simple once you know where you have to operate the site.
The rest is just research versus what the site tells us.
Hoping that this could help you ;)

If you liked this writeup you can check our github with this [link](https://github.com/PoCInnovation/ReblochonWriteups/tree/master/PicoCTF2021) and star our repository.
