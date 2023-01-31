
Writing introductions for research papers [Writing Research paper Intro](https://docs.google.com/presentation/d/1kJ2L1f3e7zHWhe1kgtk-Ycratp9QhuBh2Rsi99gQVxI/edit?usp=sharing) from [Kate Saenko](http://ai.bu.edu/ksaenko.html)

Ken Goldberg's [tips on writing papers](http://coeautomation.wpengine.com/advice-writing-papers)

Marc Raibert's [writing tips](http://www.cs.cmu.edu/~pausch/Randy/Randy/raibert.htm

[Three Sins of Authors in Computer Science and Math](https://www.cs.cmu.edu/~jrs/sins.html) [HN Discussion](https://news.ycombinator.com/item?id=29256868)



[[0004 Research Ideas]]

## SOP Writing Tips
https://krrish94.github.io/blog/gradschool-sop/
https://parentheticallyspeaking.org/articles/us-cs-phd-faq/
[Tips on presenting slides](https://twitter.com/jbhuang0604/status/1397058827405742085?s=20)

https://hemingwayapp.com/  -  to correct grammar and make text more readable.

[How I Motivate Myself to Write](https://blog.pragmaticengineer.com/writing-motivation/)


## Presentations:
 ### GIF from Videos using ffmpeg
```
ffmpeg -ss 00:00:00.000 -i input.mp4 -filter:v "setpts=PTS/10" -r 12 -s 640x480 -t 00:00:10.000 output.gif
```

The gif output will be 10x sped up and will have an output fps of 12fps at 640x480. It can also be used for slowing down. Also, when speeding up, note that this method will drop frames to achieve the desired speed. You can avoid dropped frames by specifying a higher output frame rate than the input. For example, to go from an input of 4 FPS to one that is sped up to 4x that (16 FPS)
 ss seeks to starting position
[More info - Link 1 ](https://trac.ffmpeg.org/wiki/How%20to%20speed%20up%20/%20slow%20down%20a%20video)
[More info  - Link 2](https://superuser.com/questions/1261678/how-do-i-speed-up-a-video-by-60x-in-ffmpeg)

### GIF from images

```
convert -delay 100 -loop 0 *.jpeg animatedGIF.gif
```

Use imagemagick. `delay` specifies time between frames, default unit is _hundredths of a second_  (in 1/100th of a second) to pause after drawing the images. SO the above example will pause 100/100 th  =  1 Second between frames.
and `loop` indicates how many loops to run. When you choose 0, it will run infinitely.

use [ImageMagick](http://www.imagemagick.org/)'s GIF optimizer to reduce the size:

```
convert -layers Optimize output.gif output_optimized.gif
```


or using ffmpeg  
```
ffmpeg -i %06d.png output.gif
```


#### Email Phrases - A guide for your daily "professional" interactions
https://howtoprofessionallysay.akashrajpurohit.com/


[How to write the Introduction for a Research Paper](https://docs.google.com/presentation/d/1kJ2L1f3e7zHWhe1kgtk-Ycratp9QhuBh2Rsi99gQVxI/edit?usp=sharing)

[Harvard CV- Resume- Cover Letter Tips and sample](https://hwpi.harvard.edu/files/ocs/files/hes-resume-cover-letter-guide.pdf)