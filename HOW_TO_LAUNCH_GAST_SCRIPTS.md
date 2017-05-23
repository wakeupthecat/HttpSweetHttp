# How to launch the gast samples 

## Gastona binary (jar)

Gastona is a java application, it is an open source which code
can be found at github.com/wakeupthecat/gastona

You can run gastona scripts (extension gast) using the binary gastona.jar 
that you can found in the subdirectory BUILD if you clone or fork the github
project (just donwloading the jar seems not to work !) or get an updated
copy from https://sourceforge.net/projects/gastona/

Of course java version > 1.5 needs to be installed as well.

## Launching gast scripts

There are several ways of runing a gastona script named for example SCRIPT.gast
   
### Using the command line
   
         java -jar gastona.jar SCRIPT.gast
      
so for example to run the example scripts you can do
      
         java -jar gastona.jar tellMeIP.gast
         java -jar gastona.jar firstServer.gast
         
         java -jar gastona.jar sweetHttp_Screenshot.gast
         java -jar gastona.jar sweetHttp_FileServer.gast
         java -jar gastona.jar sweetHttp_Boletin.gast

   
### Windows extension asssociation 

By associating the extension gast with the command (e.g. having gastona.jar in c:\gastona)
   
       java -jar "C:\gastona\gastona.jar" "%1"
      
to do so you can try opening a command prompt in administrator mode and type
      
         assoc .gast=gastApp
         ftype gastApp=java -jar "C:\gastona\gastona.jar" "%1"
      
unfortunatelly this seems not to work (at least for me) in some Windows versions like Windows 10

I've written a small tool in C++ to help me having associations in windows in a much more easier and flexible way.
If you use to struggle with this issue as well, take a look at it in https://github.com/wakeupthecat/lanzaras
for me it has been "THE SOLUTION".

     
### Using autoStart.gast
   
Having gastona.jar in the directory make a file called autoStart.gast with either the
contents of the script you want to run or with following script
      
         #listix#
            <main> GAST, SCRIPT.gast
         #**FIN#

given that SCRIPT.gast is your script you want to run.

Then on running gastona.jar directly, either by double click on it or with
         
         java -jar gastona.jar
         
 the script will be launched.
         
### Packing all in a jar 

This method is a way to pack you script in a jar, so just one file will have all.
   
Make a copy of gastona.jar, for example over myscript.jar, then add the your script 
and the autoStart.gast script of the previous method into myscript.jar. This can be done 
with some zip tool like for example 7z.exe opening myscript.jar with 7z.exe, then 
drag and drop both SCRIPT.gast and autoStart.gast and any other additional file needed 
by your script in the root directory of the file.
      
From now on all is contained in myscript.jar and it can be launched directly (e.g. double click etc)

This works because the logic for gastona to launch a script is as follows

   - if given as parameter then it launches the script
   - launched without parameter is searches for autoStart.gast (case matters!) first in
     the current directory and second in the own jar
   - if no autoStart.gast is found then it launches the internal script 
     META-GASTONA\WelcomeGastona\WelcomeGastona.gast which is the gastona language reference
   

### Make a simple gast launcher in autoStart.gast 

Save following script in autoStart.gast and by double clicking gastona.jar a
simple launcher for all gast scripts found in the directory will appear
   
            #javaj#

               <frames> iLanza

            #listix#

               <main0>
                  VAR=, iLanza, path
                  LOOP, FILES, ., gast
                      ,, VAR+, iLanza, @<fullSubPath>

               <-- iLanza>
                  GAST, @<iLanza selected.path>
