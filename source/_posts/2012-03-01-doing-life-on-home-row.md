---
title: Doing Life on Home Row
author: Dan Riti
layout: post
permalink: /2012/03/doing-life-on-home-row/
categories:
  - Article
tags:
  - beginners
  - efficiency
  - learning
  - programming
  - text editor
  - tools
  - vim
---
I&#8217;ve always had a fascination with <a href="http://www.vim.org/" title="VIM" target="_blank">Vim</a>. For the unfamiliar, Vim is a text editor that disowns the mouse and challenges the user to put those 8th grade typing classes to good use. That&#8217;s right folks, you are now doing life on home row!

![Home Row][1]

My fascination with Vim started back in college during my *experimentation* days. You know what I&#8217;m talking about. The long, carefree nights, trying anything put on the table, and always looking for the next, better distribution.

Wait. Distribution? I&#8217;m talking about experimenting *with* Linux! What did you think I was talking about?

Oops. Now that we&#8217;ve cleared that up, lets move on&#8230;

At this time, it was impossible for me to avoid command line editing, so it was necessary to learn the absolute, minimum basics of Vim to get by. This meant learning how to insert a change, save the file, and quit. However, I always did things the **wrong** way, like using the arrows keys for navigation. I know many of you just **shuddered** at the thought of inefficient cursor movement, but you have to understand where I (and most likely you) come from.

<a href="http://www.youtube.com/watch?v=_NSn5RfxoXs" title="there was Jack" target="_blank">In the beginning</a>, Vim felt completely foreign to me and understandably so. All my life, I&#8217;ve used a computer with a mouse. From accidentally deleting Notepad on Windows 3.1 (Oops!) to playing Quake 3 on Windows ME, a mouse has always been firmly in my grip. Thus, when I began my foray into the world of ones and zeros, I naturally gravitated towards text editors designed to be used with a keyboard and a mouse. Forgive me father, for I have sinned.

![Notepad on Windows 3.1][2]

Even through all this, I never felt the desire to use Vim as my full time text editor. The challenge and associated fears of relearning a skill (editing text) that you&#8217;ve done one way for years can be a bit daunting. Moving from <a href="http://notepad-plus-plus.org/" title="Notepad++" target="_blank">Notepad++</a> to <a href="http://macromates.com/" title="TextMate" target="_blank">TextMate</a> isn&#8217;t a big deal, because your proficiency can translate easily between &#8220;modeless&#8221; text editors. However, this all gets thrown out the window once you step in the Vim world. Don&#8217;t be afraid children, it&#8217;s well worth it.

I felt that if I really wanted to learn Vim, I would have to go all in. This meant only using Vim both at home and at work. However, the latter would be a challenge for several reasons. 

I work in a development environment that is difficult to change. To paint a picture, the majority of my development at work happens on a Windows box that is on an <a href="http://en.wikipedia.org/wiki/Air_gap_(networking)" title="Air Gapped" target="_blank">air gapped</a> network. To top it off, I do not have administrative rights and it is against the rules for me to put or install any *unauthorized* software on my machine. So this means that I am basically stuck with whatever software is installed on my machine when it was given to me. Furthermore, the default and recommended text editor for my software team was <a href="http://www.editplus.com/" title="Edit Plus" target="_blank">Edit Plus</a>. While these security restrictions are unavoidable when working for a <a href="http://en.wikipedia.org/wiki/United_States_Department_of_Defense" title="Department of Defense" target="_blank">DoD</a> contractor, it can be extremely frustrating. 

All hope was not lost. A few weeks ago, I finally decided it was time to jump into the deep end with Vim after being blown away by the *devastating* power of Vim demonstrated at <a href="https://www.destroyallsoftware.com/screencasts" title="Destroy All Software" target="_blank">Destroy All Software</a>. With a little charm, patience, and just plain old asking nicely, I was able to get my system administrator to install Vim &#038; gVim on my machine. Guess it pays being on the good side of your IT folks?

Now that the stage was finally set, it was time for me to actually get my hands dirty and **learn** Vim!

In my quest to understand the Vim way, I searched far and wide on the vast plains of the internet. Below are some of the most useful resources that I utilized:

*   <a href="http://www.derekwyatt.org/vim/vim-tutorial-videos/" title="Vim Tutorial Videos by Derek Wyatt" target="_blank">Vim Tutorial Videos</a> &#8211; From novice to advanced, Derek Wyatt has produced a fantastic set of videos to learn Vim. This is my **recommended** starting point. Watching all the novice videos really helped me dive into Vim and get a strong, fundamental understand of the basics. 
*   <a href="http://vim.wikia.com/wiki/Tutorial" title="Vimtutor" target="_blank">Vimtutor</a> &#8211; Vim ships with its own tutorial called Vimtutor. Vimtutor is essentially just a text file that opens in Vim and instructs you on Vim basics. However, it is useful because it forces you to use Vim to complete the tutorial and enables you to apply the knowledge from Derek&#8217;s videos. It is a solid and easy way to start getting hands on experience, which is key to learning Vim. I **recommend** this as a second step and takes roughly an hour to complete. 

For further learning of Vim and it&#8217;s advanced features, I use the following resources on a daily basis:

*   <a href="http://vim.wikia.com/wiki/Vim_Tips_Wiki" title="Vim Wiki" target="_blank">Vim Wiki</a> &#8211; The name is pretty self explanatory, so stop wasting time and start reading! 
*   <a href="http://stackoverflow.com/" title="Stack Overflow" target="_blank">Stack Overflow</a> &#8211; If you don&#8217;t know what Stack Overflow is, then you&#8217;ve been living under a rock. Its crowd sourced, question and answering done right. A ton of Vim questions have already been answered, so make sure you search first! 
*   <a href="https://github.com/notfunk/configs" title="My Vim Config" target="_blank">My Vim Config</a> &#8211; I used <a href="https://github.com/derekwyatt/vim-config" title="Derek Wyatt's Vim Config" target="_blank">Derek Wyatt&#8217;s Vim Config</a> as a starting baseline and customized it to my likings. Not going to lie, its pretty sexy. 

Recommended:

*   <a href="http://stackoverflow.com/questions/1497958/how-to-use-vim-registers" title="How to use registers in Vim" target="_blank">How to use registers in Vim</a> 
*   <a href="http://stackoverflow.com/questions/235839/how-do-i-indent-multiple-lines-quickly-in-vi" title="How to indent quickly in Vim" target="_blank">How to Indent Quickly in Vim</a>

 [1]: http://i.imgur.com/VPYF1.jpg
 [2]: http://i.imgur.com/0xqgF.png
