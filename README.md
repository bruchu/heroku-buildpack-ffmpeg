Heroku buildpack: FFMpeg
=======================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for using [ffmpeg](http://www.ffmpeg.org/) in your project. 

ffmpeg build is a custom vulcan build downloaded from (http://bruchu.github.io/heroku-binaries/ffmpeg.tar.gz) and also contains [ffmpegthumbnailer](https://code.google.com/p/ffmpegthumbnailer/)

It doesn't do anything else, so to actually compile your app you should use [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to combine it with a real buildpack.

Usage
-----
To use this buildpack, you should prepare .buildpacks file that contains this buildpack url and your real buildpack url.  

    $ ls
    .buildpacks
    ...
    
    $ cat .buildpacks
    https://github.com/bruchu/heroku-buildpack-ffmpeg
    https://github.com/heroku/heroku-buildpack-play

    $ heroku create --buildpack https://github.com/ddollar/heroku-buildpack-multi

    $ git push heroku master
    ...

You can verify installing ffmpeg by following command.

    $ heroku run "ffmpeg -version"

ffmpeg verification

    $ heroku run 'ffmpegthumbnailer -v'
