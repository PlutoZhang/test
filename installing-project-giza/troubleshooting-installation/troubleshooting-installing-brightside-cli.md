# Troubleshooting installing Brightside CLI

The following issues are known to exist when installing this release of Brightside CLI:

* **Additional syntax required to complete macOS and Linux installations.**

  Depending on how you configured Node.js on Linux or Mac, you might need to add the prefix sudo before the npm install -g command or the npm uninstall -g command. This step gives Node.js write access to the installation directory.

* **The npm** `install -g` **command might fail several times due to an EPERM error \(Windows\).**

  This behavior is due to a problem with Node Package Manager \(npm\) on Windows. There is an open issue on the npm GitHub repository to fix the defect.

  If you encounter this problem, some users report that repeatedly attempting to install Brightside CLI yields success. Some users also report success using the following workarounds:

  * Issue the `npm cache clean` command.
  * Uninstall and reinstall Brightside CLI.

    To uninstall Brightside CLI, issue the following command:

    ```text
    npm uninstall -g brightside
    ```

    Re-install Brightside CLI using the following command Install BrightSide CLI.

    ```text
    npm install -g brightside --no-optional
    ```

* **The** `npm install -g command` **might fail due to an** `npm ERR! Cannot read property 'pause' of undefined` **error.**

  This behavior is due to a problem with Node Package Manager \(npm\). If you encounter this problem, revert to a previous version of npm that does not contain this defect. To revert to a previous version of npm, issue the following command:

  ```text
  npm install npm@5.3.0 -g
  ```

* `node.js` **commands do not respond as expected.**

  When you try to issue node commands and you do not receive the expected output, there might be a program that is named node on your path. The Node.js installer automatically adds a program that is named node to your path. When there are pre-existing programs that are named node on your computer, the program that appears first in the path is used. To correct this behavior, change the order of the programs in the path so that Node.js appears first.

