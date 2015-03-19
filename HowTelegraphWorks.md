# Overview #

Telegraph tries to bring the MVC goodiness of Rails to the Voice environment.  There are three core components of Telegraph:

| Component | For the Web Developer | For the Voice Developer |
|:----------|:----------------------|:------------------------|
| VoiceModel | Allows you to perform CRUD operation on elements of your voice system.  Anywhere ActiveRecord is accessible, so are the voice models  For example, for a channel (call) you can create it (call someone), find (get info on a specific call), update (record/etc.) and delete (hangup). Same with Conferences and SIP Profiles | Provides a clean, Object Orientated abstraction wrapper around the FS XML-RPC interface (this is like a better version of AMI for Asterisk folks) |
| VoiceView | Allows you to control what happens to a live "call" like you would control what happens to a web page.  Bridge one channel to another, play sounds, put in queues, record, get dtmf input and so on | Provides abstraction layer around outbound event socket and allows you to separate business (controller) logic and view code |
| VoiceEvents | Allows you to respond to non-linear events thrown by voice server in the rails environment. Events like a user logging in, a call completing or hanging up and so on | Provides easy access to inbound socket.  You can "route" events to different code modules and easily access databases through the rails ORM magic. |