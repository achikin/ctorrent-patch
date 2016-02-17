# ctorrent negative integer patch
From [this issue](https://sourceforge.net/p/dtorrent/bugs/21/) on ctorrent SourceForge page:

I noticed with a bunch of random torrents that ctorrent would simply exit with "error, initial meta info failed". Since this got to be bothersome, I dug into it. If an integer with a negative value happens to occur before the "info" dictionary, then ctorrent aborts its parsing phase and exits immediately.
I wrote a patch to simply skip over the negative sign if present. the strtoll() already takes care of correctly parsing this, so there should be no need for ctorrent itself to worry about it.
