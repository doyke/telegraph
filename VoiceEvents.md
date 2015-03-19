### Setting Up ###

You need to set up voice event controllers.  Begin by doing the following:

```
  script/generate voice_events_controller controller_name
```

This will generate two files.  app/voice\_events/routes.rb is your event routing file.  Documentation on how to use it is in the file.  The first controller you set up will be the default.

The second file will be app/voice\_events/controller\_name\_voice\_events.rb.  Look inside this file for example events.  Calling params inside any of those functions will give you a hash of all the params sent by FreeSWITCH.  The function names must match the FreeSWITCH event names.  Voice events will then automatically subscribe to this event.

### Running ###
Run with
```
  script/voice_events
```

You can also daemonize just like VoiceView

```
  script/voice_events -a start -d
```

Inside of the events you have full access to your models and other rails functionalities.