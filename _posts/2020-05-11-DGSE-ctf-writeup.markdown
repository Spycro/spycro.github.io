---
layout: post
title: "Alone Muks"
categories: ["ctf", "BrigitteFriang"]
tags: ["pwn", "privesc"]
---

This is quite a simple challenge from the Brigitte Firang ctf Challenge, a French Ctf organised by the DGSE.

They tell tou to connect to a connected truck, that you need to take control of (get root)
When you connect you get this screen : 
![connection screen](/assets/img/aloneMuks1.png)

With a simple ctrl+D you can get out quite easily out of this prompt, just to get to limited shell.

![reverse bash](/assets/img/alone2.png)

Putting a / is prohibited, we can't ls, we're quite limited.
An important point of interest is that we were in a python program, as we can see the error.
So we can try a simple thing, just to see if works: upgrading our shell via python;
`python -c 'import pty; pty.spawn("/bin/bash")'`
We doing that we get to teh same screen as the first, but we know what to do: ctrl+D.
This time, it seems we're in a more conventional bash : 

![bash](/assets/img/alone3.png)

ls is still not found, but we can try finding it directly under `/bin/ls`, and it works !

Then we can just check our env variable (`/usr/bin/env`).
We see `PATH=/home/user/bin`, so we can jus	t change that with :
`PATH=/bin:/usr/bin:$PATH`

Now we have access to a normal bash and we can easliy move around.
under /home we see two new user : globalSystem and navigationSystem.
We find a file named flag.txt in the home of navigationSystem, so we now have a clear goal: privesc to navigationSystem.

After some time and research you can issue a `sudo -l`, and we see :

![sudo -l](/assets/img/alone4.png)

So we just quickly privesc via vim :
`sudo -u globalSystem vim test.sg` and in vim `:!/bin/bash`

We are now globalSystem. We can try sudo -l again 

![sudo -l](/assets/img/alone5.png)

So we go check that binary : 

![update](/assets/img/alone6.png)

We have full write access, so we can just replace the binary by what we want, we can do that with vim, replacing the content with:
`cat /home/navigationSystem/flag.txt`
and then `sudo -u navigationSystem update`

![flag](/assets/img/alone7.png)
