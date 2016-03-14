# pitools
tools for playing streams and embedded videos live on the raspberry pi.

While the scripts here are oriented towards the raspberry pi, they should
theoretically work on any media platform. Their main focus is to capture media
for the purposes of streaming it live on a remote computer.

These scripts are written for Linux.

# requirements
On the computer sending the commands, pitools requires rtmpsnoop, youtube-dl,
and jshon.

On the computer recieving the commands, pitools requires curl, rtmpdump, and
omxplayer (configuration for a different video player is possible).

If you wish for maximum speed, you must configure an ssh server on your remote
computer and set up an rsa key on your main computer. You must also set the 
PI\_SSH\_ID environment variable to the id used in ~/.ssh/config. Please see
below.

# ssh
catchstream and catchvid merely capture the url of streams and embedded
videos. It is possible to do most of the extra computation on your main
computer. To send them remotely to your raspberry pi, you must configure an ssh
server. It is required that you use an rsa key so that you can execute commands
remotely without a password.

Please see your distro's documentation for information on setting up rsa keys
and ~/.ssh/config.

#configuration
pitools is configured with environmental variables contained in ~/.pirc. An
example configuration is provided by examplepirc.

#catchstream
catchstream captures a live stream and plays it with omxplayer over ssh.

catchstream takes one argument, which is a stream URL.

A "killstream" command is provided, which also kills omxplayer.

#catchvid
catchvid captures videos from any of the many sites supported by youtube-dl and
plays them on the pi. It feeds a url directly to omxplayer, preventing the need
to download videos beforehand.

It supports playlist and English captions (native or auto captions). The
caption language will soon be configurable.

For speed reasons, it parses json from youtube-dl manually. If this fails to
work on any website, please inform the author by posting the bug on github.
