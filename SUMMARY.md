# Table of contents

* [Introduction](README.md)
* [Edition notice](edition-notice.md)
* [About this book](about-this-book.md)
* [Project Giza overview](project-giza-overview/README.md)
  * [What is Project Giza](project-giza-overview/what-is-project-giza.md)
  * [Components overview](project-giza-overview/components-overview/README.md)
    * [zLUX overview](project-giza-overview/components-overview/zlux-overview.md)
    * [Atlas overview](project-giza-overview/components-overview/atlas-overview.md)
    * [Brightside CLI Overview](project-giza-overview/components-overview/brightside-cli-overview.md)
* [Installing Project Giza](installing-project-giza/README.md)
  * [Prerequisites](installing-project-giza/prerequisites/README.md)
    * [Prerequisites for z/OSMF configuration](installing-project-giza/prerequisites/prerequisites-for-z-osmf-configuration.md)
    * [Prerequisites for zLUX](installing-project-giza/prerequisites/prerequisites-for-zlux/README.md)
      * [Verifying that your system meets the software requirements](installing-project-giza/prerequisites/prerequisites-for-zlux/verifying-that-your-system-meets-the-software-requirements.md)
      * [Confirming that Node.js is installed on the z/OS host](installing-project-giza/prerequisites/prerequisites-for-zlux/confirming-that-node.js-is-installed-on-the-z-os-host.md)
      * [Verifying port number availability](installing-project-giza/prerequisites/prerequisites-for-zlux/verifying-port-number-availability.md)
    * [Prerequisites for Atlas](installing-project-giza/prerequisites/prerequisites-for-atlas.md)
    * [Prerequisites for Brightside CLI](installing-project-giza/prerequisites/prerequisites-for-brightside-cli.md)
  * [Installing components of Project Giza](installing-project-giza/installing-components-of-project-giza/README.md)
    * [Installing zLUX](installing-project-giza/installing-components-of-project-giza/installing-zlux/README.md)
      * [Setting up the Giza Node server and the ZSSAS on z/OS](installing-project-giza/installing-components-of-project-giza/installing-zlux/setting-up-the-giza-node-server-and-the-zssas-on-z-os.md)
      * [Starting the zLUX server](installing-project-giza/installing-components-of-project-giza/installing-zlux/starting-the-zlux-server.md)
      * [Stopping the zLUX server](installing-project-giza/installing-components-of-project-giza/installing-zlux/stopping-the-zlux-server.md)
    * [Installing Atlas](installing-project-giza/installing-components-of-project-giza/installing-atlas.md)
    * [Installing Brightside CLI](installing-project-giza/installing-components-of-project-giza/installing-brightside-cli.md)
  * [Verifying installation](installing-project-giza/verifying-installation/README.md)
    * [Verifying zLUX installation](installing-project-giza/verifying-installation/verifying-zlux-installation.md)
    * [Verifying Atlas installation](installing-project-giza/verifying-installation/verifying-atlas-installation.md)
    * [Validating Brightside CLI installation](installing-project-giza/verifying-installation/validating-brightside-cli-installation.md)
    * [Identify and correct problems detected by the validate profile command](installing-project-giza/verifying-installation/identify-and-correct-problems-detected-by-the-validate-profile-command.md)
  * [Uninstalling Project Giza](installing-project-giza/uninstalling-project-giza/README.md)
    * [Uninstalling zLUX](installing-project-giza/uninstalling-project-giza/uninstalling-zlux.md)
    * [Uninstalling Atlas](installing-project-giza/uninstalling-project-giza/uninstalling-atlas.md)
    * [Uninstalling Brightside CLI](installing-project-giza/uninstalling-project-giza/uninstalling-brightside-cli.md)
  * [Troubleshooting installation](installing-project-giza/troubleshooting-installation/README.md)
    * [Troubleshooting installing zLUX](installing-project-giza/troubleshooting-installation/troubleshooting-installing-zlux.md)
    * [Troubleshooting installing Atlas](installing-project-giza/troubleshooting-installation/troubleshooting-installing-atlas.md)
    * [Troubleshooting installing Brightside CLI](installing-project-giza/troubleshooting-installation/troubleshooting-installing-brightside-cli.md)
* [Using Project Giza](using-project-giza/README.md)
  * [Using zLUX](using-project-giza/using-zlux/README.md)
    * [Navigating MVD](using-project-giza/using-zlux/navigating-mvd.md)
    * [Using Atlas Explorers within zLUX](using-project-giza/using-zlux/using-atlas-explorers-within-zlux.md)
    * [Creating an application plug-in](using-project-giza/using-zlux/creating-an-application-plug-in/README.md)
      * [Setting environment variables for plug-in development](using-project-giza/using-zlux/creating-an-application-plug-in/setting-environment-variables-for-plug-in-development.md)
      * [Experimenting with the zLUX sample application plug-in](using-project-giza/using-zlux/creating-an-application-plug-in/experimenting-with-the-zlux-sample-application-plug-in.md)
    * [zLUX logging](using-project-giza/using-zlux/zlux-logging.md)
  * [Using APIs](using-project-giza/using-apis/README.md)
    * [Using Atlas REST APIs](using-project-giza/using-apis/using-atlas-rest-apis/README.md)
      * [Dataset APIs](using-project-giza/using-apis/using-atlas-rest-apis/dataset-apis.md)
      * [Job APIs](using-project-giza/using-apis/using-atlas-rest-apis/job-apis.md)
      * [Persistent Data APIs](using-project-giza/using-apis/using-atlas-rest-apis/persistent-data-apis.md)
      * [System APIs](using-project-giza/using-apis/using-atlas-rest-apis/system-apis.md)
      * [USS File APIs](using-project-giza/using-apis/using-atlas-rest-apis/uss-file-apis.md)
      * [z/OS System APIs](using-project-giza/using-apis/using-atlas-rest-apis/z-os-system-apis.md)
      * [Programming Atlas REST APIs](using-project-giza/using-apis/using-atlas-rest-apis/programming-atlas-rest-apis/README.md)
        * [Sending a GET request in Java](using-project-giza/using-apis/using-atlas-rest-apis/programming-atlas-rest-apis/sending-a-get-request-in-java.md)
        * [Sending a GET request in JavaScript](using-project-giza/using-apis/using-atlas-rest-apis/programming-atlas-rest-apis/sending-a-get-request-in-javascript.md)
        * [Sending a POST request in JavaScript](using-project-giza/using-apis/using-atlas-rest-apis/programming-atlas-rest-apis/sending-a-post-request-in-javascript.md)
        * [Extended API sample in JavaScript](using-project-giza/using-apis/using-atlas-rest-apis/programming-atlas-rest-apis/extended-api-sample-in-javascript.md)
    * [Using Atlas WebSocket services](using-project-giza/using-apis/using-atlas-websocket-services/README.md)
      * [Programming Atlas WebSocket services](using-project-giza/using-apis/using-atlas-websocket-services/programming-atlas-websocket-services.md)
  * [Using Brightside CLI](using-project-giza/using-brightside-cli/README.md)
    * [How to display Brightside CLI help](using-project-giza/using-brightside-cli/how-to-display-brightside-cli-help.md)
    * [Brightside CLI Command groups](using-project-giza/using-brightside-cli/brightside-cli-command-groups.md)
    * [Enabling and disabling experimental commands](using-project-giza/using-brightside-cli/enabling-and-disabling-experimental-commands.md)
    * [Brightside CLI scenarios](using-project-giza/using-brightside-cli/brightside-cli-scenarios.md)
  * [Notices](using-project-giza/notices/README.md)
    * [IBM notices](using-project-giza/notices/ibm-notices.md)
    * [Rocket Software notices](using-project-giza/notices/rocket-software-notices.md)
    * [CA notices](using-project-giza/notices/ca-notices.md)

