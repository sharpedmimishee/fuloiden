# fuloiden
![Fuloiden_with_Icon](fuloiden.png)
**WELCOME TO THE PLACE WHICH IS NOT KNOWN BY ANYONE.**  
A editor for synthesis audio. you can perhaps make some characters pronounce what you want to make them say forcibly.
## Why did you start to make this?
This project was created before this repository was created because I just wanted it. That's all.  
Don't think everything is true.
## How to make a new fuloiden sound source
**Guide or some references will be made**  
You ought to check the [test fuloiden audio source](https://github.com/sharpedmimishee/utoshitesu).
```mermaid
---
title: Audio Source Detail
config:
  flowchart:
    curve: linear
---
flowchart LR
audiosource[("Audio Source")]
subgraph abouttoml["about.toml"]
name(Name)
version(Version):::dashedNode
desc(Description):::dashedNode
license(License):::dashedNode
end
licensefile("License File"):::dashedNode
subgraph audiodatafiles["Audio Data Files"]
fu("ふ")
whisru("whis#る")
lo("lo")
end
connectiontoml["audioconnection.toml"]:::dashedNode
subgraph audiodatatoml["audiodata.toml"]
direction LR
subgraph audiodataconf["Default Audio Data Configurations"]
direction LR
standardtone("Standard Tone")
range("Range"):::dashedNode
audioname~~~standardtone~~~range~~~alias
end
subgraph fuconf["ふ Configurations"]
  audioname("Audio Name"):::dashedNode
  standardtone("Standard Tone"):::dashedNode
  range("Range"):::dashedNode
  alias("Alias"):::dashedNode
end
whisruconf("whis#る Configurations")
loconf("lo Configurations")
end
audiosource---abouttoml & licensefile & audiodatafiles & connectiontoml & audiodatatoml
classDef dashedNode stroke-dasharray: 5 5
```
## Engine System
Fuloiden uses a engine for adjusting and connecting each notes and so on.  
Fuloiden can use some engines simultaneously and in that case, Fuloiden will use them each the engines on the basis of order of them.
```mermaid
---
title: Fuloiden
config:
  flowchart:
    curve: linear
---
flowchart LR
gui(GUI)
audiosource[("Audio Source")]
subgraph engines["Fuloiden Engines"]
  engine1("Engine 1")
  engine2("Engine 2")
  audiobuffer[("Audio Buffer")]
  engine1-->|Process the audio from given note configs|audiobuffer
  audiobuffer-->|Get the audio data|engine2-->|Process the audio in the same way|audiobuffer
end
renderedaudio[("Rendered Audio")]
renderedjoint{ }
audiosource-->|Get the audio data|engines
gui-->|Request to render the audio from configs of notes|engines-->|Get the configs of notes|gui
engines-->|Render the audio and return it|renderedaudio
renderedaudio & gui-->renderedjoint-->|Export the audio|exportedaudiofile[("Exported Audio File")]
renderedjoint-->|Play the audio|playaudio("Play the audio")
```
There is a list of engines by the creator:  
- dequidil (the name is from liquid) - The default engine for Fuloiden.  
- deopevarat (the name is from evaporate) - The creator's AI Engine for Fuloiden. It is not default engine because it is anticipated to be unstable and most outputs may be low quality.  
