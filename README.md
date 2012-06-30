charlesztt-tools-libsvm-macosx-matlab-compiled
==============================================

Compiled Matlab Execution file of LibSVM for MacOSX

I know that most of you have some problems when compiling LibSVM with Mac. Especially in recent releases (XCode 4.3) Apple changed XCode into an app rather than a toolset, new MacOS and newly installed XCode won't give you an installed command line tools (such as gcc, git), things are kind of complicated.

Here I provide the compiled MATLAB execution files compiled under MATLAB R2012a (maci64), if you have problem with this build, you can follow the tutorial below. Also, even you don't have any problems, I still recommend you read the tutorial, because today we have LibSVM not able to be compiled in Mac, tommorrow I am afraid we may have LibLSH, LibClustering, LibDiablo or LibAoiSora which are proposed as cross-platform but always have problems with Macs and prevent Mac users from using them, by knowing this, I hope you can work out other similar problems.

Step I:
If you turn on Terminal on Mac, type "gcc" and it says "command not found", that means you did not install Command Line Tools. It often happens to users who bought Mac machines after the release of XCode 4.3. For those users, when they install XCode, Command Line Tools are not atomatically installed. Actually, XCode 4.3 (maybe the earlier release, XCode 4.2) also impacts the older users, because these releases include the change from pure GNU/GCC to LLVM+GCC, and some SDK directory path changes.

Open XCode, then click on "XCode" on left-top of the screen, choose "Preference", then select "Downloads", in components part, you can see the "great" Command Line Tools, just install them as prompted.

Then I think you can get an error (why always error) saying "no input files", that means, you succeeded.

Step II:
Open MATLAB, type:

mex -setup

Then it will prompt you to choose a compiler, in most cases, you have only one choice. This action will write or overwrite a file in you "~/.matlab/20XXx/mexopts.sh".
