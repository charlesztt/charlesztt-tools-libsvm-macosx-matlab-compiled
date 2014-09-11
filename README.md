charlesztt-tools-libsvm-macosx-matlab-compiled
==============================================

Actually, there is no need to use the manual here, because current version of MATLAB(2014a) and LibSVM has already made everything simple as a line of

	make

Compiled Matlab Execution file of LibSVM for MacOSX

I know that most of you have some problems when compiling LibSVM with Mac. Especially in recent releases (XCode 4.3) Apple changed XCode into an app rather than a toolset, new MacOS and newly installed XCode won't give you an installed command line tools (such as gcc, git), things are kind of complicated.

Here I provide the compiled MATLAB execution files compiled under MATLAB R2012a (maci64), if you have problem with this build, you can follow the tutorial below. Also, even you don't have any problems, I still recommend you read the tutorial, because today we have LibSVM not able to be compiled in Mac, tommorrow I am afraid we may have LibLSH, LibClustering, LibDiablo or LibAoiSora which are claimed as cross-platform but always have problems with Macs and prevent Mac users from using them. Hopefully, by knowing this, you can work out other similar problems.

Step I:
If you turn on Terminal on Mac, type "gcc" and it says "command not found", that means you did not install Command Line Tools. It often happens to users who bought Mac machines after the release of XCode 4.3. For those users, when they install XCode, Command Line Tools are not atomatically installed. Actually, XCode 4.3 (maybe the earlier release, XCode 4.2) also impacts the older users, because these releases include the change from pure GNU/GCC to LLVM+GCC, and some SDK directory path changes.

Open XCode, then click on "XCode" on left-top of the screen, choose "Preference", then select "Downloads", in components part, you can see the "great" Command Line Tools, just install them as prompted.

Then I think you can get an error (why always error) saying "no input files", that means, you succeeded.

Step II:
Open MATLAB, type:

	mex -setup

Then it will prompt you to choose a compiler, in most cases, you have only one choice. This action will write or overwrite a file in you "~/.matlab/20XXx/mexopts.sh".

Now in Terminal, type:(suppose you have MATLAB 2012a)

	cd ~/.matlab/2012a/
	chmod a+w mexopts.sh
	open mexopts.sh

Then you scroll down to the button, you can see the session for "maci64" architecture. You can notice that in the CC and CXX variables, there is a "-4.2" tail. Just delete them, leaving them "gcc" and "g++".

Wait, did you notice the SDKROOT='/Developer/SDKs/MacOSX10.6.sdk'? Yes, that's another problem, Apple is really a bad boy, they hide the SDKs in the Xcode Application, very very deep inside. So you have to explore something, on my machine it is like this SDKROOT='/Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX10.8.sdk', you can use Terminal to follow the path and confirm whether it really contains a "usr" folder, and in this usr folder you will see "gcc" in the bin and some header files in the "include".

Please note that you should choose SDK according to the version of OS X or (Mac OS X) or at least, the SDK contained in your SDK folder (on 10.7 we can see SDK of 10.6 and 10.7, on 10.8 we can see SDK of 10.7 and 10.8).
Then save it, revoke the writing priority.

	chmod a-w mexopts.sh

Step III:
Option 1:
Now I think you are close to success. Open Matlab, go to LibSVM matlab folder, then, type

	make

Works?

Option 2:
Another option is to compile them using the Makefile, then you can compile them in Terminal.

You should change the MATLABDIR variable at the beginning of the file. For Mac, it often installs your MATLAB20XXx in /Applications/MATLAB_R20XXx.app, if you are not sure, you can explore it in Terminal or finder, make sure that you can reach bin folder wihich contains matlab's main program.

Then in Terminal, type

	make

or in MATLAB command line, type

	!make

Works?

Had you any questions, please send an email to tz2163(rat)caa(punkt)columbia(punkt)edu.
