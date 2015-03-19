Getting Telegraph up and running is fairly easy.

  1. Install FreeSWITCH.  See http://wiki.freeswitch.org/wiki/Installation_Guide
  1. Make sure ruby eventmachine is installed `gem install eventmachine`
  1. cd into your rails project directory.
  1. Run ` script/plugins install http://svn.freeswitch.org/svn/freeswitch/trunk/scripts/contrib/jpalley/telegraph/trunk/ `
  1. If needed, modify RAILS\_ROOT/config/telegraph.yml (the default config will usually work).
  1. What do you want to do?  Check out VoiceModel, VoiceView or VoiceEvents for next steps.