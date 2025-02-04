# Installing BlueJ
URL : https://canvas.vt.edu/courses/204710/pages/install-bluej
| OS              | Source/Version                                                     |
|-----------------|--------------------------------------------------------------------|
| BlueJ Version   | 5.4.0-vt1.7                                                        |
| Windows         | https://courses.cs.vt.edu/~cs1114/files/BlueJ-windows-540-vt17.zip |
| Mac Os          | https://courses.cs.vt.edu/~cs1114/files/BlueJ-mac-540-vt17.zip     |
| All other       | https://courses.cs.vt.edu/~cs1114/files/BlueJ-generic-540-vt17.jar |
| --------------- | ----------------                                                   |

You must use the links above to download BlueJ--the downloads from bluej.org do not include the support libraries used in our assignments and will give compiler errors you are unable to fix.

To install BlueJ, download the zip file for your operating system from the links above and unzip it. The Windows and Mac versions of the application include a Java environment built-in and no separate Java installation is required.

- **Windows users** can move the application (or application folder) to their preferred location, and optionally add it to their start menu.
- **Mac OS users** can move the application (or application folder) to their Applications folder, if desired.
- **Generic (non-OS-specific) version**: You must have JDK 11+ installed. Follow the BlueJ generic instructions to complete the install for your operating system.

## Reinstalling a New Version of BlueJ

Follow the same instructions to download and unzip the zip file. Just drag/drop or copy the new version on top of the old version to replace it.

### Windows Users: Windows protected your PC

Some Windows users may see a security warning the first time they run BlueJ. If you see this, click **"More Info"** and then **"Run Anyway"** to start BlueJ.

### Mac OS Users: Cannot Check for Malicious Software?

Some Mac OS users may see the following message when trying to open BlueJ for the first time:

> *“BlueJ” can’t be opened because Apple cannot check it for malicious software.*

If you receive this message:

1. Close the dialog.
2. Instead of double-clicking the application to open it, **ctrl-click** on the application to open the pop-up menu and choose **"Open"** (right-clicking may also work). This should whitelist the application.
3. If this doesn't work, go to **System Preferences > Security & Privacy > General** and ensure **"App Store and identified developers"** is selected.
4. If you still receive the same message, go to **System Preferences > Security & Privacy** and look for a message about BlueJ at the bottom. Click to **"Open Anyway"** (you may need to unlock security preferences first).
5. See it in action in this video: [https://youtu.be/0V5Phac8pao](https://youtu.be/0V5Phac8pao)
6. If you still can't open it, try this solution: [https://youtu.be/6fqzb4qpgcs](https://youtu.be/6fqzb4qpgcs)

## After Installing or Updating, BlueJ Will Not Compile My Code

If, after installing BlueJ or upgrading, BlueJ no longer recognizes the library classes, check the following:

- Ensure you **extracted** the contents of the zip file. Delete the zip file after extraction to avoid confusion.
- **Windows users**: Do not move `bluej.exe` out of its folder. You can move the entire folder, but do not separate the BlueJ command from its resources.
- Ensure you are executing the **extracted copy** of BlueJ, not the original inside the zip file.
- **Windows users**: Do not launch BlueJ from inside the zip file—extract it first.
- Once installed correctly, create a **shortcut** or pin it to your taskbar for easier access.

## Opting In to Anonymous Data Collection

When you first start BlueJ, it will prompt you for participation in anonymous research:

![anon-data.png](anon-data.png)

We request that you consider agreeing if you are over 18. No user-identifying information (including names in source files) is ever sent. The collected data helps improve software tools and studies how students learn to program. More details are available from the BlueJ team.

## Source Code

- **BlueJ** is an open-source application with source available [online](https://bluej.org).
- **Greenfoot** is an open-source application with source available [online](https://greenfoot.org).


