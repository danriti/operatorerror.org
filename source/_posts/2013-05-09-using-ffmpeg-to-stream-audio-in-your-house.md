---
title: Using FFmpeg to stream audio in your home
author: Dan Riti
layout: post
permalink: /2013/05/using-ffmpeg-to-stream-audio-in-your-house/
comments: true
categories:
  - Article
tags:
  - audio
  - ffmpeg
  - home
  - network
  - notcode
  - stream
---
I like to listen to records. I also like to listen to my records when I code. So recently, I said to myself,

{% blockquote %}
&#8220;How can I easily pipe audio between rooms in my house using my network and open source software?&#8221;
{% endblockquote %}

The answer: <a href="http://www.ffmpeg.org/" title="FFmpeg" target="_blank">FFmpeg</a>!

For the unfamiliar, FFmpeg is a complete, cross-platform solution to record, convert and stream audio and video. If you have a task that falls into any of those categories, FFmpeg can do it like no other!

So without derailing this post and rambling on about my audio setup at home, all you have to know is I have a line level audio source plugged into the sound card&#8217;s *Line In* on one computer and I want to pipe that audio to any other computer in my house. So conceptually:

<pre>[Line Level Audio Source]---->[Computer A]====(Home Network)====>[Computer B]</pre>

Still with me? Ok good! The first thing I want to do is figure out what audio inputs FFmpeg can see:

**Computer A**:

```
ffmpeg.exe -list_devices true -f dshow -i dummy
```

**Output**:

```
D:\apps>ffmpeg.exe -list_devices true -f dshow -i dummy
ffmpeg version N-44818-g13f0cd6 Copyright (c) 2000-2012 the FFmpeg developers
  built on Sep 27 2012 19:30:20 with gcc 4.7.1 (GCC)
  configuration: --enable-gpl --enable-version3 --disable-pthreads --enable-runtime-cpudetect --enable-avisynth --enable-bzlib --enable-frei0r --enable-libass --enable-libcelt --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libfreetype --enable-libgsm --enable-libmp3lame --enable-libnut --enable-libopenjpeg --enable-librtmp --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libutvideo --enable-libvo-aacenc --enable-libvo-amrwbenc --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxavs --enable-libxvid --enable-zlib
  libavutil      51. 73.101 / 51. 73.101
  libavcodec     54. 59.100 / 54. 59.100
  libavformat    54. 29.104 / 54. 29.104
  libavdevice    54.  2.101 / 54.  2.101
  libavfilter     3. 17.100 /  3. 17.100
  libswscale      2.  1.101 /  2.  1.101
  libswresample   0. 15.100 /  0. 15.100
  libpostproc    52.  0.100 / 52.  0.100
[dshow @ 01ffc400] DirectShow video devices
[dshow @ 01ffc400]  "Rocketfish HD Webcam"
[dshow @ 01ffc400] DirectShow audio devices
[dshow @ 01ffc400]  "Microphone (Rocketfish HD Webca"
[dshow @ 01ffc400]  "Digital Audio (S/PDIF) (High De"
[dshow @ 01ffc400]  "Line In (High Definition Audio "
dummy: Immediate exit requested
```

And bingo! The second to last line is just what we want, so keep note of this!

```
[dshow @ 01ffc400]  "Line In (High Definition Audio "
```

For this example, let&#8217;s assume Computer B&#8217;s IP address is **192.168.1.17**, which is our streaming destination. So hit play on your audio source and fire off the following to begin streaming:

**Computer A**:

```
ffmpeg -f dshow -i audio="Line In (High Definition Audio " -acodec libmp3lame -ab 320000 -f rtp rtp://192.168.1.17:1234
```

Now, just set Computer B listening for audio:

**Computer B**:

```
ffplay 192.168.1.17:1234
```

BOOM! Point to point audio streaming using the power of FFmpeg in your own home!

References:

*   <a href="http://www.ffmpeg.org/documentation.html" title="FFmpeg Documentation" target="_blank">FFmpeg Documentation</a>
*   <a href="http://sonnati.wordpress.com/2011/07/11/ffmpeg-the-swiss-army-knife-of-internet-streaming-part-i/" title="FFmpeg - The swiss army knife of Internet streaming" target="_blank">FFmpeg &#8211; The swiss army knife of Internet Streaming</a>
*   <a href="http://ffmpeg.org/trac/ffmpeg/wiki/StreamingGuide" title="FFmpeg Streaming Guide" target="_blank">FFmpeg Streaming Guide</a>
