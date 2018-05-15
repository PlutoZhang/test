# Uninstalling Atlas

To uninstall Atlas, take the following steps:

1.  Stop your Atlas Liberty server by running the following operator command:

    ```
    P FEKATLS
    ```

2.  Delete the FEKATLS member from your system PROCLIB data set.
3.  Remove RACF® \(or equivalent\) definitions with the following command:

    ```
    RDELETE STARTED (FEKATLS.*)
    SETR RACLIST(STARTED) REFRESH
    REMOVE (userid) GROUP(IZUUSER)
    ```

4.  Delete the z/OS® UNIX™ System Services Atlas directory and files from the Atlas installation directory by using the following command:

    ```sh
    rm -R /var/atlas #*Atlas Installation Directory*
    ```

    **Notes:**

    -   You might need super user authority to run this command.
    -   You must identify the Atlas installation directory correctly. Running a recursive remove command with the wrong directory name might delete critical files.

**Parent topic:** [Installing Atlas](../topics/uninstall.md)
