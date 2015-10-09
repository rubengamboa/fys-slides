---

title:        COSC 1101 The Beauty & Joy of Computing
subtitle:     Blown to Bits. Ghosts in the Machine
author:       Ruben Gamboa
date:         October 5, 2015
#logo:         uw-logo-large.png
#biglogo:      uw-logo-large.png
job:          Professor
highlighter:  highlight.js
hitheme:      tomorrow             # default
mode:         selfcontained        # {standalone, draft}
framework:    io2012               # {io2012, html5slides, shower, dzslides, revealjs, ...}
widgets:      [mathjax, bootstrap] # {mathjax, quiz, bootstrap}

---

<style>
slide.title-slide {
     background-color: #EDE0CF; /* CBE7A5; #EDE0CF; ; #CA9F9D*/
     background-image: url(assets/img/uw-logo-large.png);
     background-repeat: no-repeat;
     background-position: center top;
   }
slide:not(.title-slide) {
    background-image: url(assets/img/uw-logo-small.png);
    background-repeat: no-repeat;
    background-position: right bottom;
    background-size: 24px;
}
</style>

# File Formats

---

## Text Files

* Simplest files there are

* Easiest to share between systems (e.g., Mac/Windows/Linux/Supercomputers)
  * Even then, there are problems (e.g., CR vs. CRLF)

* Key question is how to represent each character

---

## Text Files: Character Encoding

Character   | EBCDIC    | ASCII
------------|-----------|----------------
A           | 11000001  | 01000001
B           | 11000010  | 01000010
I           | 11001001  | 01001001
J           | 11010001  | 01001010
a           | 10000001  | 01100001
b           | 10000010  | 01100010
0           | 11110000  | 00110000
1           | 11110001  | 00110001
,           | 01101011  | 00101100

EBCDIC: , a b A B 0 1

ASCII: , 0 1 A B a b

---

## Text Files: Other Languages

* Whoops!  We forgot other languages

* We need to address the characters, like &#223;, &#233;, &#228;, &#230;, and &#231;

* There are also complications with orderings
  * Different dialects of the same language can have different orderings!

---

## Music Files

* Important question: What do you want to do with music?

* Some possible answers are
  * I want help composing
  * I want the computer to play something I've written
  * I want the computer to play a recording of my playing the piano (maybe to scare innocent children)

---

## Music Files: Sheet Music

* We can encode sheet music in a number of ways

1. A **header** stores the time signature and key
2. The header is followed by one or more measures
3. Each measure has one or more voices
4. Each voice has a sequence of notes and durations (which must add up to the time signature)

* Notice that each note is encoded just like a character in text
* Also notice that there are bound to be complications:
  * Dynamical markings
  * Key changes
  * Time signature changes (thank you, Mr. Bart&#243;k)

* Examples: MusicXML for composing, and MIDI for playback

---

## Music Files: Recordings

* Or we can store recorded music

* Here we need to think about how music is played in the real (not virtual) world
  * The speaker moves back and forth to push air, making sound waves
  * How often the speaker moves determines the frequency or note
  * How far the speaker moves determines the amplitude or volume

* So we can simply encode music in one of these two ways:
  * For each time unit, store the displacement of the speaker (takes into account amplitude and frequency)
  * For each period, store the frequency, amplitude, and duration of the period

* The second option requires less space (e.g., C# at volume 11 for 1 second, as opposed to 11,025 entries detailing the amplitudes, sampled at 11,025 Hz)

---

## Music Files: Compression

* Earliest music formats were uncompressed, e.g., WAV format (which uses approach #1, so it takes up a lot of space)
* Newer formats are compressed, e.g., MP3

* There are many approaches to compression, and we'll talk more about this later

---

## Image Files

* To store images, we have to consider light intensities over a 2D grid (of pixels)

* Easiest way to think of it is as a gray scale, say from 0 to 255
  * Exactly what 0 or 255 or (especially) 128 means is a hard topic
  * Humans perceive color (and sound) logarithmically, not linearly
  * That means that doubling the intensity simply moves it up a notch, not twice as much
  * Similar example: doubling the frequency raises the pitch by one scale

* This can be generalized to arbitrary colors by having separate intensities for Red, Green, and Blue
  * Sort of mimics the way the eye perceives color, but not quite
* But it means that each pixel is represented by three colors, each from 0 to 255

---

## Image Files: Size

* The simplest approach is to store all colors for all pixels
* The display I'm using has 2560 rows of 1440 pixels each, for a total of 3.6864 &times; 10<sup>6</sup> pixels
  * That corresponds to a 3.6 megapixel camera -- my phone camera has better resolution!
* At three bytes each, that means each picture needs 1.10592 &times; 10<sup>7</sup> bytes, or around 11Mbytes.
* My 32Gbyte thumb drive could only store 3106 images!
* For a sense of scale, my computer has roughly 16,000 family photos

---

## Image Files: Compression

* One way to compress images is to take advantage of *spatial coherence*
* That just means that if one pixel is green, the pixels next to it are probably green, too
* So we do not need to use three bytes to encode each pixel
* We only need to encode the (much smaller) differences between pixels

* E.g., instead of 100, 101, 101, 101, 102, 101, ... we can store 100, +1, +0, +0, +1, -1, ...

* We can also use "general" compression techniques, which follow a similar idea, but may look at the entire file first

* Key distinction:
  * **Lossless** compression completely replicates the original image
  * **Lossy** compression replicates a very similar image (e.g., it may return 101 for a color instead of 102 -- could you tell the difference, anyway?)

* Examples: RAW and TIFF are uncompressed, GIF and PNG have lossless compression, and JPEG has lossy compression

---

## Video Files

* Two main challenges
  * A video consists of lots of still images, roughly 30 images per second of video
  * A video also has an audio track

* For the first challenge, consider a YouTube video uploaded at (the recommended) 1920x1080 resolution
* That's 2.0736 &times; 10<sup>6</sup> pixels, which at 3 bytes each turns into 6.2208 &times; 10<sup>6</sup> bytes per image
* Which means 1.86624 &times; 10<sup>8</sup> bytes per second -- yeah, that's 186 Mbytes per second!

* 30-minute TV episode: 3.359232 &times; 10<sup>11</sup> bytes
* 2-hour movie: 1.3436928 &times; 10<sup>12</sup> bytes
* Lord of the Rings Trilogy: 6.2369741 &times; 10<sup>12</sup> bytes

* Note: $10^{12}$ bytes is a **terabyte**

---

## Video Files: Compression

* The same discussion about image file compression applies

* Video supports one more trick: **temporal coherence**

* The idea is that if a particular pixel is blue in frame #1394, then it's probably also blue in the next frame!

* So we can take differences not just between pixels in one frame, but between corresponding pixels in adjacent frames

---

## Video Files: Compression Sanity Check

* By the way, a DVD stores about 5Gbytes, compared with 3Tbytes for a 2-hour movie

* We would need to compress the movie by a ratio of 600:1 to make it fit into a DVD
  * That's not happening!
  
<br />

* The problem is that we're using "high-definition" video

* DVDs can handle video up to 720x480 pixels, which corresponds to old TV resolution

* Blue Ray disks, on the other hand, store up to 50Gbytes (and with some tricks, 128Gbytes)

* That means we need compressions on the order of 60:1, which is still very high

* A quick experiment yields a compression ratio of 64:1 for Apple QuickTime -- so we're good, barely!
