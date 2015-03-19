# Introduction #

Telegraph Abstracts the Rails Integration from the FreeSWITCH socket libraries.  It is relatively easy to take the core freeswitch integration libraries and use them in your own Ruby framework/application.


# Details #

  * VoiceModels can easily be used with out Rails.  Look in the /lib/freeswitch/voice\_model directory.
  * For voice events you'll want to start with lib/freeswitch/voice\_events\_server.rb
  * For voice views (i.e. outbound socket) you'll need voice\_view\_server and voice\_view\_interface.

As always..please contribute back!

# Other VoIP Servers #

Telegraph is now architected so that it can be easily used with other VoIP servers.  Take a look or contact the dev if you are interested (we hope that someone will migrate the original telegraph asterisk servers to eventmachine and our new architecture...)