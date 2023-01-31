


Interesting way to add  Reading list / updates to webpage : https://www.philipithomas.com/posts/what-i-m-up-to-november-2022

Cal Newport's advice about [what to have on a personal website](https://www.youtube.com/watch?v=xluJvqtn8Ks&t=4255s)


[newcss](https://www.github.com/xz/new.css)  -  simple website in HTML and a single CSS file

[latex-css](https://github.com/vincentdoerig/latex-css)  - LaTeX.css is a minimal, almost class-less CSS library which makes any website look like a LaLaTeX.css is a minimal, almost class-less CSS library which makes any website look like a LaTeX documentTeX document

[plain-academic](https://github.com/mavroudisv/plain-academic) -  simple HTML only website for academics
		-an good example [www.hosspro.com](https://www.hosspro.com)

#### Markdown in HTML Pages
 - [zero-md](https://zerodevx.github.io/zero-md/)
 -  [Simple example](https://github.com/zhlicen/md.htm)

### Videos in HTML Webpages

#### GIF to HTML5 video conversion using ffmpeg

MP4 works in almost all devices/browsers
```
ffmpeg -i input.gif  -movflags +faststart -pix_fmt yuv420p -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" output.mp4
```
-   `-i`: Specifies the _input file_, in this case `file.gif`.
-   `-movflags`: For web video we can specify `+faststart` to allow the video to start playing before the download is complete.
-   `-pix_fmt`: The default `yuv444p` can't be played by some mobile browsers so we set it to `yuv420p` instead.
-   `-vf`: This flag is allows us to set `"scale=trunc(iw/2)*2:trunc(ih/2)*2"` to ensure the video width and height are divisible by 2 which would otherwise cause an error when using `yuv420p`.

Webm, although has lesser size, does not work reliably in Apple devices
```
ffmpeg -i input.gif  -c vp9 -b:v 0 -crf 40 output.webm

```
-   `-i`: Specifies the _input file_, in this case `file.gif`.
-   `-c`: Specifies the _codec_, `vp9` works in most browsers.
-   `-b:v`: Specifies the _video bitrate_, `0` allows us to specify the quality via the `-crf` option.
-   `-crf`: Specifies the _quality_, ranges between 0-63, lower means better quality.

#### Displaying videos in HTML webpage 
```
<div class="col-md-4">

<video class="img-responsive " autoplay loop muted playsinline disableRemotePlayback x-webkit-airplay="deny" disablePictureInPicture style="object-fit: fill" >

<source src="videos/my_video.mp4" type="video/mp4" />

</div>
```
-   `autoplay`: start playing the video ASAP, just like an animated GIF plays as it loads.
-   `loop`: restart the video when reaching the end. Optional in GIF but usually on.
-   `muted`: important even if your video has no audio! Browsers will often refuse to `autoplay` unless the video is `muted`.
-   `playsinline`: disable playing the video in “fullscreen”.
-   `disableRemotePlayback`: disable Google Cast or AirPlay buttons.
-   `x-webkit-airplay="deny"`: same as `disableRemotePlayback`, but respected by Safari.
-   `disablePictureInPicture`: disable any Picture-in-Picture prompts.

#### YouTube videos in HTML, that aligns to the shape and size of div

Add the following style to the `head` section of the HTML
```
<style>
	.youtube-video{
		aspect-ratio: 16 / 9;
		width: 100%;
		}
</style>
```

Add video as in the following example:
```
<div align="center">

	<iframe class="youtube-video" src="https://www.youtube.com/embed/hlw0aVvvHLQ" title="Video Title" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen>
</iframe>

</div>
```