# About this book

This book describes how to install, configure, and use Project Giza Closed Beta.

## Who should read this book

This book is intended for system programmers who are responsible for installing Project Giza, developers who want to use Project Giza to improve z/OS user experience, and anyone who wants to know about Project Giza.

To use this book, you must be familiar with the mainframe and z/OSMF configuration.

## Terminology used in this book

Before getting started with Project Giza, please acquaint yourself with the following terms:

| Term | Abbreviation | Definition |
| --- | --- | --- |
| Mainframe Virtual Desktop | MVD | A virtual desktop, accessed through a web browser. |
| Atlas | N/A | A z/OS RESTful web service and deployment architecture for z/OS microservices. |
| Brightside Command Line Interface | Brightside CLI | Lets application developers interact with the mainframe in a format that is natively familiar to them.  It lets application developers use common tools such as Integrated Development Environments \(IDEs\), shell commands, bash scripts, and build tools for mainframe development. |
| Command Groups | N/A | Command groups focus on specific business processes that application developers and systems programmers perform during their day-to-day activities. |
| Experimental Commands | N/A | Commands that are currently in development and are not ready for general availability. Users can enable or disable these commands. Experimental commands are disabled by default. |
| z/OS Lightweight User Experience | zLUX | zLUX consists of the framework, MVD, plugin applications, TN3270 emulator, and Discovery. |
| zLUX Secure Services address space | ZSS | The server that provides secure REST services to support the Giza Node Server. |
| Giza Node Server | N/A | Node.js server plus Express.js as webservices framework, and the proxy applications that communicate with the z/OS services and components. |
| TN3270 | N/A | A limited license Giza plugin that provides a 3270 connection to the mainframe on which the Giza Node Server is running. |
| Application | N/A | A plug-in that is an application. |
| Discovery | N/A | z/OS subsystems plug-in. |

## How to use this book

This book contains an introduction and information for installing and using Project Giza.

* [Project Giza overview](project-giza-overview/) explains what is Project Giza and what it can do.
* [Installing Project Giza](installing-project-giza/) explains how to install and maintain Project Giza so that it can work. It also provides information about troubleshooting installation related problems.
* [Using Project Giza](using-project-giza/) explains how to use the features that Project Giza provides.

## How to send your feedback

Your feedback is important in helping us to provide accurate and high-quality information. If you have comments about this documentation, raise an issue and send us a pull request.

Be sure to include the version of the product, and, if applicable, the specific location \(for example, the page number or section heading\) of the text that you are commenting on.

