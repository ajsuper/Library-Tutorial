Be sure to read this README.md in RAW mode. You can do this by clicking on it in the list of all the files of this program and then clicking on RAW which should be just above the top right of the text. it doesnt like alot of my formatting
Hello!! This is a simple tutorial on how to compile and link a custom library in c++. 
It doesn't quite cover everything, but if you look at the contents of the files you can figure out more info.

How did I do it!???
Idk I'm pretty talented.
This tutorial is for linux; however Windows and macOS are similarp; however idk how to do it so you might need another tutorial.

#1:
well, first I created the files. This is the structrue of all my important ones:

Before compile/link:

/LearningLibraries/
    testlib/
        mylibrary.cpp
        mylibrary.h
    main.cpp
    HowTo.txt(that's me!!)

After compile/link:

/LearningLibraries/
    testlib/
        libmylibrary.a
        mylibrary.cpp
        mylibrary.h
        mylibrary.o
    main.cpp
    HowTo.txt(that's me!!)
    myprogram

#2:
Now make sure all of your file names are correct and be sure that the code from here is copied correctly, or create your own if you feel brave. 
Feel free to clone this repo and then delete the files that are in the "After compile/link", but not in the "Before compile/link". Use a file manager, you should end up removing
myprogram, mylibrary.o, libmylibrary.a, 

Compile!!!!
How do we compile?? Well, hey chatG- I mean google!

#1: 
cd into the LearningLibraries folder but NO FURTHER!!!

#2:
Okay I lied, cd into our testlib file, then typing dir into the terminal should output:
mylibrary.cpp mylibrary.h

#3:
create our mylibrary.o file. This is done with the following terminal command:
$ g++ -c mylibrary.cpp -o mylibrary.o
This compiles our .cpp file into binary that the computer can read and stores it in mylibrary.o

#4:
create our libmylibrary.a file. This is done with the following terminal command
$ ar rcs libmylibrary.a mylibrary.o
This basically links our mylibrary.o file and some extra data to libmylibrary.a 
and creates libmylibrary.a if it does not exist and replaces it if it does

#5:
Now cd back out of there:
$ cd ..
We should now be back in LearningLibraries

#6:
compile our main.cpp and link it to our library and create a linux executable folder.
$ g++ -I./testlib main.cpp -L./testlib -lmylibrary -o myprogram
Let's break this one down line by line:
    g++           Run the g++ compiler
    -I./testlib   Sets an include path to ./testlib
    main.cpp      Tells g++ to compile our main.cpp file
    -L./testlib   Sets the path to the directory that contains our file to link from (the libmylibrary.a we created earlier)
    -lmylibrary   Links the libmylibrary.a file. They were lazy and made it to where the prefix lib is implied with an l and the .a is implied with the - and the L
                  So basically it is linking our libmylibrary.a file to our main.cpp file when we run the command
    -o myprogram  creates myprogram which is an executable that will run the finished code!!!

#7:
Run it!!!
this can be done by typing this into the terminal:
$ ./myprogram

if it works correctly the output should be
HelloWorld!
The result is: 12

Good Job!! I hope it worked!!! Now look around at the files, their contents, and mess around with changing stuff and seeing what happens! 
Just make sure to remove the files that were created in the compile stage and then recompile all of it!
