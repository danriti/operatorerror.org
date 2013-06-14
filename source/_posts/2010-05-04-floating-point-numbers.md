---
title: Floating Point Numbers
author: Dan
layout: post
permalink: /2010/05/floating-point-numbers/
categories:
  - Article
tags:
  - floating point
  - programming
---
I just recently finished up a project at work that required float-point number comparison and initially stumbled into the **float-point comparison pitfall** displayed below:

<div class="wp_syntax">
  <table>
    <tr>
      <td class="code">
        <pre class="ada" style="font-family:monospace;"><span style="color: #00007f;">if</span> <span style="color: #66cc66;">&#40;</span>float_a == float_b<span style="color: #66cc66;">&#41;</span>
    // compare evaluates true.
<span style="color: #00007f;">else</span>
    // compare evaluates false.</pre>
      </td>
    </tr>
  </table>
</div>

Of course, my team lead quickly pointed out my mistake while reviewing my code and I promptly smacked myself in the head for making such a rookie error!

After fixing the code in question following his recommendation, I just so happened to stumble upon an interesting [article][1] on [Slashdot][2] called [What Every Computer Scientist Should Know About Floating-Point Arithmetic][3] and figured it was right up my alley! Below is a piece of the abstract that I think sums of the paper nicely:

> This paper presents a tutorial on those aspects of floating-point that have a direct impact on designers of computer systems. It begins with background on floating-point representation and rounding error, continues with a discussion of the IEEE floating-point standard, and concludes with numerous examples of how computer builders can better support floating-point.

If you&#8217;re rusty on the ins and outs of floating-point (it happens to the best of us) and short on time, then you should check out the digested version over at [The Floating-Point Guide][4]. This is a great high-level summary of the original article and covers topics such as number formats, IEEE 754 standard, and comparison errors just to name a few.

**BONUS LINK: **[Comparing float point numbers][5]

 [1]: http://developers.slashdot.org/story/10/05/02/1427214/What-Every-Programmer-Should-Know-About-Floating-Point-Arithmetic
 [2]: http://slashdot.org
 [3]: http://docs.sun.com/source/806-3568/ncg_goldberg.html
 [4]: http://floating-point-gui.de/
 [5]: http://www.cygnus-software.com/papers/comparingfloats/comparingfloats.htm