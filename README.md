# Project: Cone | Quick guide
I am glad to introduce this app to you.
This page is a temporary page that helps you use the early release app immediately and informs you of any errors you should be aware of when using the current version.

## The main technologies supported by the current version
- You can easily manage To-do.
- After building a Nakama server, you can chat and send and receive files with other people. (Godot-3.5.2-stable *.pck files can be viewed)
- You can chat with random people connected to the community server.
- You can share the prepared environment to others using a QR code.

## Confirmed errors and unprepared features that users should be aware of in this version
- Some media files cannot be opened depending on the media properties.
- Nakama chat channels are sometimes recognized as unavailable. If this happens even though you haven't left the channel, please restart the app after deleting the channel.
- Sometimes the 1:1 chat channel does not work properly.

## How to use the app
- You can download and use the to-do function without a separate login procedure.
- If you launched the app for the first time, enter your email address and nickname on the profile screen that is created.

Below are steps to use the chat function within the team.

- To use the chat function, you need to build a private Nakama server. Details can be found on [this page](https://heroiclabs.com/docs/nakama/getting-started/install/docker/).
- If setting up Nakama is difficult, install [Docker](https://www.docker.com/), [download this file](https://github.com/is2you2/pjcone_basic_guide/raw/main/nakama.zip), open a terminal in the folder where the docker-compose.yml file is located, and type **docker-compose up -d**.
- Go to the settings screen
- Enter the group server menu.
- Enter information such as the address of the Nakama server.
- After returning to the previous screen, move to the Add Group page.
- After entering group information, share the generated QR code with your team members.
- If you share the group server and group information with a QR code, you can interact with other team members.

## Godot engine configuration limitations
- You can play *.pck files compatible with the 3.5.2-stable version or equivalent version.
- The Viewer loads ContentViewer.tscn as a child object after loading the *.pck file. Therefore, *.pck files that you want to share must have ContentViewer.tscn.
- In general, set up the specific node you want to share by configuring it as follows.
```gdscript
# ContentViewer.gd
extends Node

func _ready():
	var inst = load('res://ShareTarget.tscn')
	add_child(inst.instance())
```
- Since the viewer function used in the app uses the default value of Godot Engine, the following functions may not work properly or the file may not be opened.
- All contents managed in the project.godot file are fixed as default values. As a result, representative features that cannot be used are as follows.
	- Newly registered keys in the keymap do not work.
	- Classes created by the user do not work.
	- Among other project settings, if the contents affecting the project.godot file are not configured as scripts, it will not work.
- Installed plugins do not work.
- Works only at the same level as HTML5 output.
	- It does not work if features not supported in HTML5 output, such as shapekey animation, are included.

translated by Google translator
