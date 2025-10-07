### Welcome to the Noomxffplayer github repo.

No more omxplayer but ffplay works :)

* Make sure your ffmpeg has been built with drm.
* Install ffmpeg and egl and mesa drivers for your hardware, then test connection to a camera or stream.
* Then you can start up automatically in a kiosk either using systemd or a shell script. Systemd is easier because it will manage the restarts if needed
and you can run it as a specific user easy as well,  I think you just need to make sure they are a member of the video group, maybe audio,input too.

GL and enjoy!
*I might upload an example systemd unit soon.*
ffplay Documentation - FFmpeg
1 day ago1 Synopsis ffplay [options] [input_url] 2 Description FFplay is a very simple and portable media player using the FFmpeg libraries and the SDL library. It is mostly used as a testbed for the various FFmpeg APIs. 3 Options All the numerical options, if not specified otherwise, accept a string representing a number as input, which may be followed by one of the SI unit prefixes, for example: 'K ...
This is so easy to do, I won't be building a dedicated build for it, all the debian and other distros have this tech available, and it's not deprecated :)





Use Control + Shift + m to toggle the tab key moving focus. Alternatively, use esc then tab to move to the next interactive element on the page.
Attach files by dragging & dropping, selecting or pasting them.


This is mostly here for information and tips on how to move away from omxplayer using ffmpeg's: ffplay.

Using FFmpeg/ffplay one can achieve full freedom away from omxplayer(if you haven't long ago already) and ensure updates will be coming.

### How does it work? 
From my understanding, ffmpeg leverages it using drm/mesa dri and probably sdl2.

* What is great about it, is that it will work on all most hardware using the same method.

* What else is cool about using ffplay instead of omxplayer? 
  *You still have control over your console, you can actually quit the application even if its running under systemd.*

### How can you make this work on your distro or build?

* Make sure your ffmpeg has been built with drm.
* For the rpi's make sure your using:

   dtoverlay=vc4-kms-v3d 

* For generic x86_64, it should just work once you have installed everything.
* Install ffmpeg and egl and mesa drivers for your hardware, then test connection to a camera or stream.
* Then you can start up automatically in a kiosk either using systemd or a shell script. Systemd is easier because it will manage the restarts if needed
and you can run it as a specific user easy as well,  I think you just need to make sure they are a member of the video group, maybe audio,input too.

GL and enjoy!
*I might upload an example systemd unit soon.*
ffplay Documentation - FFmpeg
1 day ago1 Synopsis ffplay [options] [input_url] 2 Description FFplay is a very simple and portable media player using the FFmpeg libraries and the SDL library. It is mostly used as a testbed for the various FFmpeg APIs. 3 Options All the numerical options, if not specified otherwise, accept a string representing a number as input, which may be followed by one of the SI unit prefixes, for example: 'K ...
This is so easy to do, I won't be building a dedicated build for it, all the debian and other distros have this tech available, and it's not deprecated :)




