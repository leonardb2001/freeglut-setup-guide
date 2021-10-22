# freeglut Setup Procedure for MSVC

This guide will show you how to set up a freeglut project in Microsoft Visual Studio.

Visual Studio is not available for Linux, so this procedure will only cover installation on Windows.

1. Download and install Visual Studio (Community is free)
    * https://visualstudio.microsoft.com/de/downloads/
    * make sure to check the `Desktop development with C++` workload when installing

2. Download freeglut (yes, only download it for now)
    * https://www.transmissionzero.co.uk/software/freeglut-devel/
3. Create a new VS project
    * select `C++` from the language dropdown, then select `Empty Project` and click `Next`
    * give your project a name and a location as you wish and click `Create`
4. Go to the folder which you downloaded freeglut and unzip it
    * it should look something like `freeglut-MSVC-3.0.0-2.mp.zip`
5. Set up `bin` correctly
    * go into `freeglut/bin` and create a new folder `Win32`
    * move the file `freeglut.dll` into that folder
    * your `bin` folder should now only contain the folders `Win32` and `x64`
6. Set up `lib` correctly
    * Repeat step 5 for `freeglut/lib` with the file `freeglut.lib`
7. Open your solution directory
    * you can easily open your solution directory by right-clicking on your solution in the solution explorer on the right and selecting `Open Folder in File Explorer`
8. Add a folder called `dependencies`
    * the actual name doesn't really matter
9. Copy the `freeglut` folder into the `dependencies` folder
    * this is referring to the actual folder called `freeglut`, not the folder looking like `freeglut-MSVC-3.0.0-2.mp.zip`
    * name it what you want, but it has to be a `*.cpp` or similar file
10. Create a new `C++` file in `Source files` 
11. Open the solution configuration
    * you can do this as well by right clicking your solution in the solution explorer and then selecting `properties`
12. Set the language standard of `C++`
    * make sure your configuration is set to `All Configurations` from the dropdown
    * can be found in `General`
    * set it to the standard of your choice, however the newest available standard is advised
    * always make sure to click `Apply` when you changed a configuration, like in the following steps
13. Set `Include Directories`
    * can be found in `VC++ Directories`
    * select `Edit` in the dropdown
    * create a new entry and paste in `$(SolutionDir)dependencies\freeglut\include`
    * click `OK`
14. Set `Library Directories`
    * can be found in `VC++ Directories`
    * select `Edit` in the dropdown
    * create a new entry and paste in `$(solutionDir)dependencies\freeglut\lib\$(Platform)`
    * click `OK`
15. Set `Additional Dependencies`
    * can be found in `Linker>Input`
    * select edit from the dropdown
    * write `freeglut.lib` and click `OK`, no need to create a new entry here
16. Set `Command Line` for post-build event
    * can be found in `Build Events>Post-Build Event`
    * select edit from the dropdown
    * paste in `copy "$(SolutionDir)dependencies\freeglut\bin\$(Platform)\freeglut.dll" "$(OutDir)"`
    * click `OK`
17. Put some freeglut code into your `C++` source file
    * you can find a bunch of example code online, if you want to test it straight away
    * if some red squiggly lines show up, repeat steps 13-15 (though you may not need all of them)
18. Rebuild the solution
    * click on `Build` in the top bar, then select `Rebuild Solution`
19. Rebuild project
    * click on `Build` in the top bar, then select `Rebuild <ProjectName>`
20. Run the project
    * click on the button with the green triangle

Your freeglut project is now setup and you can use it as you desire.

This guide was made using information from [this video](https://www.youtube.com/watch?v=A1LqGsyl3C4) by [TechLearners](https://www.youtube.com/channel/UCbuzi53dKhBa4BAe5KeIdYg).