WhiteRobotLibrary
=================

Exploratory TestStack.White C# remote library for Robot Framework, built upon the possibility to use the NRobotRemote remoteserver for hosting test libraries written in C.

This is a basic Visual Studio Project. Open the project using the WhiteRobotLibrarySolution.sln file.

For developing and building the test library dll, you will need to install the Visual Studio Express 2013 and the latest Windows SDK (both can be installed free of charge). Open the WhiteRobotLibrarySolution.sln project in Visual studio and build the Release binaries. If the TestStack.White reference is missing, just add it from the NuGet repository by right-clicking the Project item or the References item in the Solution Manager window and selecting "Manage NuGet Packages...". Install or refresh (if notified) the TestStack.White package (use the search functionality if necessary).

### NRobotRemote v1.xx instructions:

Once the WhiteRobotLibrary.dll has been built, the remote server is started using the command:

NRobotRemoteConsole.exe -p 8271 -k WhiteRobotLibrary.dll:WhiteRobotLibrary.WhiteKeywords

(Note that the WhiteRobotLibrary.dll must be placed to the same directory where NRobotRemote has been copied)

### NRobotRemote v2.xx instructions: 

Once the WhiteRobotLibrary.dll has been built, you need to add the WhiteRobotLibrary dll to the NRbotoRemote config.

Copy the .config file for NRobotRemote from the "\WhiteRobotLibrary\packages\NRobotRemote.2.0.2\lib\net46\" directory into the directory your dll was built.

Modify the .config file to look for the WhiteRobotLibrary.dll by replacing the default assemblies with this one: 

```
	<assemblies>
		<add name="WhiteRobotLibrary" type="WhiteRobotLibrary.WhiteKeywords" docfile="WhiteRobotLibrary.xml"/>
	</assemblies>
```
		
Then run the NRobotRemoteTray.exe from the same directory, you should see the NRobotRemoteTray in your system tray. 

To make sure that it worked, right-click the NRobotRemote tray and select "Keywords".
That should open a webpage with a list of the White keywords. 

### Using the keywords in RobotFramework: 

To take the library into use in test scripts use:

Library    Remote    http://127.0.0.1:8271/WhiteRobotLibrary/WhiteKeywords    WITH NAME    White


Currently the most essential keywords for clicking objects, writing text and reading text have been implemented. As a speciality, the formalism of xpaths has been adopted to give flexibility to object selection.

Please also take a look at the WhiteRobotLibrary.html for keyword documentation.

Happy testing!

PS. In some cases it is recommended to use the UIAComWrapper branch of TestStack.White. The UIAComWrapper exposes more objects to be visible for White. The UIAutomationVerify also uses the UIAComWrapper, so it can be used as a reference to see what elements are locatable by White.

