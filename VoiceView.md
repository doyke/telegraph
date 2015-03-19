### Calling Voice Views ###

Voice Views are standard actions in your controllers.  They use rails route and can be called by the voice application in one of two ways

  1. Using the socket application in the freeswitch dialplan (see freeswitch docs).

> 2.  From the VoiceChannelModel.create. For example:
```
        MyVoiceChannel.create(:destination=>'sofia/default/1000', :callback=>url_for(:action=>:show))
```

### Creating Voice Views ###

Telegraph tricks rails into thinking that a call from FreeSWITCH is really a web application call with a special mime type.  First, you need to make sure your action responds to the voice mime type:

In your controller:
```
  def show
    # Business Logic Here
    respond_to do |wants|
      wants.html
      wants.voice
    end
  end
```

Yes - you can share business logic between your voice and web application!

Next you need to create the view file.  In this case, you would make: show.voice.freeswitch.  This file works like an rjs file does.  It might look like:

```
voice.answer
voice.set "hangup_after_bridge=true"
voice.ring_ready
voice.set "ringback=%(2000, 4000, 440.0, 480.0)"

voice.bridge params[:call_me]
```

### Running ###

You have to run a separate rails server to listen for socket connections.  Simply do the following

```
 script/voice_view
```

Make sure voice\_view has permission to execute.

You can also daemonize with the following

```
  script/voice_view -a start -d
```
and
```
  script/voice_view -a stop
```

See -h for more options.

### Voice View Functions ###

Not all of the freeswitch socket functions have been implemented.  They are easy to add.  Please contribute..here are some that have been implemented:

  * spell
  * spell\_phonetic
  * say\_time
  * say\_timespec
  * answer
  * play\_sound
  * record
  * phrase
  * bridge
  * set
  * conference
  * hangup
  * hold
  * ring\_ready
  * socket
  * fifo\_in
  * fifo\_out
  * export

Please see voice\_view\_interface.rb for complete implementation.