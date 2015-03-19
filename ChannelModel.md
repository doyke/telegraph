## Add to Project ##

You can have different channel models to wrap your own additional functionality and business logic.

To add a channel:

```
  script/generate voice_model channel MyChannelName
```

This will generate app/models/my\_channel\_name.rb

# Available Functions #

## Class Methods ##

### create ###

Create can take various.
  * :destination (required) - The destination of the channel you would like to create.  Examples include: "sofia/default/1000" or "sofia/gateways/my\_gateway/18001231234"
  * :callback - A URL to call a voice\_view at when the destination is answered.  For example: :callback => url\_for(:action=>:connect).  If callback is specified then :params is ignored.
  * :vars - variables to set on the channel.  Example: :vars=>{:hold\_music=>'something'}
  * :cid\_number - caller id number
  * :cid\_name - caller id name
  * :params - used if callback is not set.  Everything after the destination in the normal freeswitch originate syntax.

Examples:
```
  MyChannel.create(:destination=>'sofia/default/1000', :callback=>url_for(:action=>:connect))
```

### find ###

Find all the channels or one specific channel.  Either takes :all as option or the uuid of the channel.  Examples:

```
  MyChannel.find(:all) #Returns an array of my_channel objects for each channel found
```
```
  MyChannel.find(uuid) #Returns my channel object for uuid or nil if not found
```

### humanize\_error\_code ###

Humanizes FreeSWITCH error codes.  Examples:

```
  MyChannel.humanize_error_code 'USER_BUSY'
```

## Instance Methods ##

### destroy ###
Hangups up channel.  Example:

```
  MyChannel.find(:all).first.destroy #Hangs up first channel
```

### park/hold ###
Park or hold a channel.  Example:

```
  channel = MyChannel.find(:all).first #Get first channel
  channel.park #Park Channel
  channel.hold #Hold channel
```

### recordings ###
Start/Stop Recording on Channel

```
  channel = MyChannel.find(:all).first #Get first channel
  channel.start_recording('/tmp/filename.wav')
  channel.stop_recording('/tmp/filename.wav')
```

### variables ###
Any channel variables can be accessed simply by:

```
  channel = MyChannel.find(:all).first #Get first channel
  puts channel.some_channel_variable #puts some_channel_variable
```

### inline transfer ###
Transfer channel to another app

```
  channel = MyChannel.find(:all).first #Get first channel
  channel.inline_transfer "bridge:sofia/default/1001"
```

Add your content here.  Format your content with:
  * Text in **bold** or _italic_
  * Headings, paragraphs, and lists
  * Automatic links to other wiki pages