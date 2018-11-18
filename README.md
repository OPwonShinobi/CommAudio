An networked audio-streaming/playing application, written using Qt C++ framework.

How to Run
----------
Please see the user manual PDF for the different modes of operation.

Modules outline
---------------
Below are the program's modules & support classes. 

#### MediaPlayerModule :
The only non-networked module. It uses high-level QMediaPlayer functions to play both wav & mp3 files
that are already saved on the host computer.

#### StreamingModule :
Handles all stream-related features. Audio from this module is not saved.
This includes 2-way microphone, peer2peer file streaming, and TCP 
multicasting. It uses a map of QTcpServer and QTcpSockets to handle multiple simultaneous connections.	
The server chooses the file to stream in this mode.

#### TransferingModule :
Handles all non-streamed file transfering.
Audio from this module is saved. 
It uses a single QTcpServer and QTcpSocket to be as simple but
efficient as possible. It can handle subsequent clients but not simultaneous ones. 							
The client chooses the file to download in this mode.

Support classes, these dont have enough functionality to be full modules but provide support to the modules above
-----------------
> MainWindow :
	Controls main GUI, it controls the modules through signals, and in turned is updated
	when modules signal

> SettingsWindow :
	Stores all user settings, and is where the modules get their user input from.

> IOSocketPair : 
	Storage class used by StreamingModule to map client connections.
	Also contains members for speaker & microphone device interfaces.				 

Minimum System requirements
---------------------------
To run the executable, make sure your Windows Machine is running Windows 7 or 10 (8 may work but untested).
Mic and speakers are needed to use some of the features, but the program will run without them.

Building & running the executable
	A precompiled executable is provided (zipped, rather big and many Qt dlls). 

	If you need to build a new executable, this assumes you meet the min system requirements above, and have at least Qt 5.10.1 and Qt Creator installed. 
	1. Go into the "source code" directory, and click on the .pro file. This should load the project in Qt Creator.
	2. When prompted, click "Configure Project" with the default settings. This should now open the project.
	3. Hit f5 to build & run the application.
	4. The program will run, and a new folder in the root directory(same folder that contains source & executable folders), named like: build-CommAudio-Desktop_Qt_5_10_1_MSVC2017_64bit-Release will now contain your new executable.