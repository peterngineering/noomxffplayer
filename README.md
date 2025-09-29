**I've delayed the public release a bit more, I'm testing a couple different options before I'm ready to release**
# ohmxplayer
the last of omxplayer

**Ohmxplayer**

omxplayer is deprecated, not many (if any) are developing around it since newer technology exists with open source and newer clean supported APIs.

Then why bother with using a bitrotten and/or deprecated stack?

Simple:
*Omxplayer still accels at doing one thing great:* 
**Displaying mpeg4 streams live with no gui, in hardware (with very little cpu needed).**This on the rpi0(s) is very low power as well,1-2Watts roughly.
   (I have not tried it, but supposibly you can still buy the license/codecs for the rpi0/1/2/3 32bit gpu(s) to do mpeg2 decode in hw as well.)
    

A lot of debating has gone around that other technologies can do the same thing that are actively developed.
	Most often its suggested for one to use one of the following alternatives configured for console use.
  To which I would generally agree with, for most uses.
  
  1. vlc      
  2. mplayer/mpv 
  3. ffplay with SDL

*I actually want to move towards building one of those after this, for a direct comparision and truly replace this method with a newer vc4/drm/gbm/mesa3d/ffmpeg based stack.
Something very lean and to the point as omxplayer is(was). I have other projects using drm/vc4 that work great without using the older proprietary stack at all, but they use QT which is quite heavy in itself. Some advanced embedded developers such as those in Kodi/OSMC etc already do this type of work lower than QT already, but I'm not at that level of development skill, yet. 
Omxplayer is the only project I have left using the old stack and this is it, the last of it.
The eventual transition should be a fun learning experience.

**Stern Warning!** *A lot of developers don't appreciate anyone making it easy for people to use technologies they want dead, no longer develop, that are deemed deprecated,most of this I think comes from a  fact that a 'main stream developers work' is constant ongoing/trying to keep up with the latest and greatest *everything*.
So they invest in new code which is most often superior than old, easy enough to understand in theory. Next time you get barked at for using older software keep in mind the role(s) they play is/are not likely to be same as yours and asking a main stream devel questions around old software often appeals NOT to them, to say the least.
So don't go asking for help anywhere for openmax stack info, you been warned! Your own ur own if you try this and even more if you use it. This setup will be transitioned to something better, eventually. 

Keep in mind, I'm doing this for learning and fun mostly. I'm more of a generic systems person generally speaking; and specifically I'm more of a packager/sysbuilder than developer, but I enjoy it all.
