---
title: 'Disable &#8216;Run A Command&#8217; in Ubuntu 11.04'
author: Dan Riti
layout: post
permalink: /2011/06/disable-run-a-command-in-ubuntu-11-04/
categories:
  - Article
tags:
  - natty narwhal
  - notcode
  - ubuntu
  - unity
---
<p>I recently upgraded one of my laptops to Ubuntu 11.04 &#8220;Natty Narwhal&#8221; and I have had the <del><em>pleasure</em></del> opportunity to explore the new Unity user interface for GNOME. Immediately I was annoyed when I noticed that my keyboard shortcuts for switching workspaces (ALT+F1, ALT+F2, etc) were defaulted to several dedicated commands in the Unity shell. This was frustrating because the standard GNOME Keyboard Shortcuts were overlapping with these Unity based commands. So after a bit of digging on on the intertubes, here is how you can disable the &#8216;Run A Command (ALT+F2)&#8217; in the Unity shell:</p>
<p><em>On a command line:</em></p>

```bash
$ sudo apt-get install compizconfig-settings-manager
$ ccsm &
```

<ul>
<li>Select &#8216;Category &gt; Desktop &gt; Ubuntu Unity Plugin&#8217;</li>
<li>On the &#8216;Behavior&#8217; tab, click the button to the right of the &#8220;Key to execute a command&#8221; text.</li>
<li>Uncheck the &#8216;Enabled&#8217; checkbox and click the &#8216;Ok&#8217; button.</li>
</ul>
<p><a title="Hosted by imgur.com" href="http://i.imgur.com/eghXV.png"><img title="Hosted by imgur.com" src="http://i.imgur.com/eghXV.png" alt="" /></a></p>
