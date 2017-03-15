# AudioSocket Framework
This is a Basic python tornado app for handling websocket audio from the browser.

This is an ideal starting point for interfacing between the  web and an AI Vocie Bot platforms.

## Features


#Running
Now you can start the audiosocket service with:

```bash
./venv/bin/python server.py
```

If you want to see more verbose logging messsages add a `-v` flag to the startup to see all DEBUG level messages

#Extending
This framework is meant to be a starting point for integrating whatever voice processing solution you desire, within the `Processor` class there is a function named `process` modify this to do whatever you want to with the blocks of speech, for example posting them to a transcription API, the current code jsut saves them to wav files which is useful for debuggin but you do not have to write to the filesystem if you don't need to store the audio.
Configuration for the processor for example API keys for 3rd party services can be passed in when the `processor` object is created at line 219, you will see in the demo that a path object is passed in to tell the processor where to save files. Again this can be removed if not required.
You can also playback audio responses to the caller using the `playback` funciton of the `Processor` this uses the CLI of the caller as an identifier to ensure it is played to the correct connection therefore you need to track this in your requests and pass it in as a parameter along with wav or raw audio `content` in the response.
