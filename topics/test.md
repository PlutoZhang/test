<div id="page">

<div id="main" class="aui-page-panel">

<div class="aui-page-panel-nav">

<div class="aui-navgroup-inner">

<div id="tabs-nav" class="aui-tabs horizontal-tabs">

  - [**Contents**](#tabs-navigation)
  - [**Search**](#tabs-search)

<div id="tabs-navigation" class="tabs-pane active-pane" data-current-page-id="418944672">

</div>

<div id="tabs-search" class="tabs-pane">

</div>

</div>

</div>

</div>

<div class="section aui-page-panel-content">

<div id="main-header">

<div id="breadcrumb-section">

1.  <span> [CA Mainframe as a Service - Source](index.html) </span>
2.  <span> [Release Notes](Release-Notes_417008163.html)
</span>

</div>

# <span id="title-text"> Brightside CLI - Source : .Release Notes v1.0 </span>

</div>

<div id="content" class="view">

<div class="page-metadata">

</div>

<div id="main-content" class="wiki-content group">

Brightside Command Line Interface (Brightside CLI) lets
application developers interact with the mainframe in a format that is
natively familiar to them. Brightside CLI helps to increase overall
productivity, reduce the learning curve for developing mainframe
applications, and exploit the ease-of-use of off-platform tools.
Brightside CLI lets application developers use common tools such
as Integrated Development Environments (IDEs), shell commands, bash
scripts, and build tools for mainframe development. It provides a set of
utilities and services for application developers who need to quickly
become efficient in supporting and building z/OS applications.

Brightside CLI provides the following benefits:

  - Enables and encourages developers with limited z/OS expertise to
    build, modify, and debug z/OS applications.
  - Fosters the development of new and innovative tools from a personal
    computer that can interact with z/OS operating systems.
  - Ensure that business critical applications running on z/OS can be
    maintained and supported by existing and generally available
    software development resources.
  - Provides a more streamlined way to build software that integrates
    with z/OS
platforms. 

<span class="inline-comment-marker" data-ref="4cc7b69c-3ad9-4cf5-8f49-1b44addc0be3"><span class="inline-comment-marker" data-ref="61254f52-9c1f-4f8e-845e-d760af790d85">The
following sections explain the key features and details for Brightside
CLI:</span></span>

<div class="toc-macro rbtoc1519935065073">

  - [Solution Video](#id-.ReleaseNotesv1.0-SolutionVideo)
  - [Brightside
    CLI Capabilities](#id-.ReleaseNotesv1.0-bscliCapabilities)
  - [Supported Platforms](#id-.ReleaseNotesv1.0-SupportedPlatforms)
  - [Brightside CLI Early Access
    Preview](#id-.ReleaseNotesv1.0-BrightsideCLIEarlyAccessPreview)
  - [Participate in the Brightside
    CLI Community ](#id-.ReleaseNotesv1.0-ParticipateinthebscliCommunity)
  - [Known Issues](#id-.ReleaseNotesv1.0-KnownIssuesknownIssues)
  - [Third-Party Software
    Agreements](#id-.ReleaseNotesv1.0-Third-PartySoftwareAgreements)

</div>

<div class="confluence-information-macro confluence-information-macro-note">

<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>

<div class="confluence-information-macro-body">

**Note:** For installation, upgrade, and software requirements, see
[Installing.](.Installing-v1.0_429364971.html)

</div>

</div>

## Solution Video

Watch this short video about how Brightside
CLI works. 

## Brightside CLI <span class="inline-comment-marker" data-ref="56566f62-e8a4-4ddc-b046-c76fafe060ee">Capabilities</span>

With Brightside CLI, you can interact with z/OS remotely in the
following ways:

  - **Interact with mainframe files**  
    Create, edit, download, and upload mainframe files (data sets)
    directly from Brightside CLI. 

  - **Submit jobs**  
    Submit JCL from data sets or local storage, monitor the status, and
    view and download the output automatically.

  - **Issue TSO and z/OS console commands**  
    Issue TSO and console commands to the mainframe directly
    from Brightside CLI.

  - **Provision mainframe environments**  
    Exploit z/OSMF cloud provisioning features to provision environments
    on-demand.

  - **Integrates z/OS actions**  
    Build local scripts that accomplish both mainframe and local tasks. 

  - **Produce responses as JSON documents**  
    Return data in JSON format on request for consumption in other
    programming languages.

For more information about the available functionality in Brightside
CLI, see [Brightside CLI Command
Groups](.Brightside-CLI-Command-Groups-v1.0_444506328.html).

## Supported Platforms

**Workstations:** You can install Brightside CLI on any Windows, macOS,
and Linux operating system that supports Node.js version 6 or
later.

<div class="confluence-information-macro confluence-information-macro-note">

<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>

<div class="confluence-information-macro-body">

**Note:** CA Technologies does not maintain the prerequisite software
that Brightside CLI requires. You are responsible for updating Node.js
and other prerequisites on your personal computer or workstation. We
recommend that you update Node.js regularly to the latest Long Term
Support (LTS)
version.

</div>

</div>

<span class="anchor"><span class="inline-comment-marker" data-ref="33d97479-578e-428b-a03e-b528ad9d1191">**Mainframe
systems:** Brightside CLI was designed and tested to integrate with z/OS
Management Facility (z/OSMF) running on IBM version 2.2 z/OS mainframe
systems.</span></span>

## Brightside CLI <span class="inline-comment-marker" data-ref="2b1fbafc-36ba-430b-9020-42699f65ff91">Early Access Preview</span>

The Brightside CLI Early Access Preview lets early adopters preview
Brightside CLI. The Release
Note<span class="inline-comment-marker" data-ref="c2a2a52e-3d69-4a01-808d-a6ef19120a6c">s
describes</span> new features as they become available.

Brightside CLI is under
<span class="inline-comment-marker" data-ref="035f2ea0-8e6d-4e6c-8af3-39ae36d92643">continuous
development</span> and might have periodic updates. For information
about how to determine your current Brightside CLI version and apply
updates,
<span class="inline-comment-marker" data-ref="e2f26100-49d9-40da-b43c-7082d029a6d7">see</span> [Install
Brightside
CLI.](.Install-Brightside-CLI-v1.0_417272825.html)

### <span class="inline-comment-marker" data-ref="576cc313-dc64-47ca-83c5-2cd3c4f9f61a">Experimental Commands</span>

The Brightside CLI Early Access Preview contains features that are still
under development and have not been tested to GA quality. You can enable
or disable these commands. The experimental commands are disabled by
default.

<div class="confluence-information-macro confluence-information-macro-warning">

<span class="aui-icon aui-icon-small aui-iconfont-error confluence-information-macro-icon"></span>

<div class="confluence-information-macro-body">

**Important\!**  You
<span class="inline-comment-marker" data-ref="a8660728-8ded-4a9c-93d7-50d7a144285a">might</span>
encounter problems when using experimental commands. 

</div>

</div>

For more information, see [Enable and Disable Experimental
Commands](.Enable-and-Disable-Experimental-Commands-v1.0_427862248.html).

## <span class="anchor"><span class="inline-comment-marker" data-ref="8add129d-5faf-4b08-a452-ec62412980b8"><span class="inline-comment-marker" data-ref="0197014b-ad3e-44a3-904d-7f315211aef7">Participate in</span> the Brightside CLI Community</span> </span>

We want to know what you think about Brightside CLI. You can become a
part of the Brightside CLI community by participating in the [Brightside
CLI project on
validate.ca.com](https://validate.ca.com/project/version/item.html?cap=13283cc32fd9439c85aeb18bba4ac1f6&arttypeid=%7B4109d6e9-6c06-448b-8eb2-6601a5616391%7D&artid=%7B5ACC31C0-2176-437F-B06B-8C572D48C76C%7D).

Visit the Brightside CLI project on Validate.ca.com and navigate to the
relevant section where you can provide the following types of feedback:

  - **Suggestions:** Provide general feedback and make suggestions for
    product enhancements.

  - **Questions:** Ask questions about the product.

  - **Defect Reports:** Report defects that you encounter when using the
    product.

  - **User Forums:** Participate in forums with other Brightside
    CLI early
    adopters<span class="inline-comment-marker" data-ref="111dabcc-f529-4b78-8b7e-15c4039744f9">.</span>

<span class="inline-comment-marker" data-ref="111dabcc-f529-4b78-8b7e-15c4039744f9">Alternatively,
you can add comments at the bottom of this DocOps page to provide
feedback on your experience with the product and
documentation.</span>

## <span class="inline-comment-marker" data-ref="e9a2af4c-f5ca-4cd9-83f6-643d1962da2d"><span class="inline-comment-marker" data-ref="12a93861-6098-4de8-807b-42816b747f1d">K</span></span><span class="inline-comment-marker" data-ref="e4fa04ae-98e5-4344-a5e1-0a17dfe605f0"><span class="inline-comment-marker" data-ref="e9a2af4c-f5ca-4cd9-83f6-643d1962da2d"><span class="inline-comment-marker" data-ref="12a93861-6098-4de8-807b-42816b747f1d">nown Issues</span><span id="id-.ReleaseNotesv1.0-knownIssues" class="confluence-anchor-link"></span></span></span>

<span>The following issues are known to exist in this release
of Brightside CLI:</span>

  - **Additional syntax required to complete macOS and Linux
    installations.**  
    Depending on how you configured Node.js on Linux or Mac, you might
    need to add the prefix `sudo `before the `npm install -g` command or
    the `npm uninstall -g` command. This step gives Node.js write access
    to the installation directory.

  - **The  `npm install -g` command might fail several times due to
    an `EPERM` error (Windows).**
    
    This behavior is due to a problem with Node Package Manager (npm) on
    Windows. There is an open issue on the npm GitHub repository to fix
    the defect.
    
    If you encounter this problem, some users report that repeatedly
    attempting to install Brightside CLI yields success. Some users also
    report success using the following workarounds:
    
      - Issue the `npm cache clean` command.
      - Uninstall and reinstall Brightside CLI. For more information,
        see [Install BrightSide
        CLI](.Install-Brightside-CLI-v1.0_417272825.html).
      - Issue the `npm install -g brightside --no-optional` command.

  - **The `npm install -g` command might fail due to an `npm ERR! Cannot
    read property 'pause' of undefined` error.**
    
    This behavior is due to a problem with Node Package Manager (npm).
    If you encounter this problem, revert to a previous version of npm
    that does not contain this defect. To revert to a previous version
    of npm, issue the following command:
    
    `npm install npm@5.3.0 -g`

  - **Node.js commands do not respond as expected.**
    
    When you try to issue node commands and you do not receive the
    expected output, there might be a program that is named *node* on
    your path. The Node.js installer automatically adds a program that
    is named *node* to your path. When there are pre-existing programs
    that are named *node* on your computer, the program that appears
    first in the path is used. To correct this behavior, change the
    order of the programs in the path so that Node.js appears first.

<span>To report product defects, visit [Brightside CLI project on
validate.ca.com](https://validate.ca.com/project/version/item.html?cap=13283cc32fd9439c85aeb18bba4ac1f6&arttypeid=%7B4109d6e9-6c06-448b-8eb2-6601a5616391%7D&artid=%7B5ACC31C0-2176-437F-B06B-8C572D48C76C%7D) and
click **Defects** from the **Feedback** menu.</span>

<span>To report documentation issues or make suggestions, place your
comments in the Comments section at the bottom of the applicable
documentation
page.</span>

## <span class="inline-comment-marker" data-ref="ca80d48f-55b4-4bd7-ab13-81aa134b55d4">Third-Party Software Agreements</span>

<span class="inline-comment-marker" data-ref="ca80d48f-55b4-4bd7-ab13-81aa134b55d4"> </span>Brightside
CLI uses the following
<span class="inline-comment-marker" data-ref="d7019178-9c18-4412-88ff-8d9e59b26250">third-party
software:  
</span>

  - ag-grid
  - body-parser
  - chalk
  - cli-table2
  - csv
  - definitelytyped
  - express
  - filewatcher
  - getmdl-select
  - glob
  - i18n
  - jsonschema
  - js-yaml
  - levenshtein
  - lodash
  - log4js
  - material-design-lite
  - mustache
  - Nested-property
  - node.js
  - node-forge
  - node-progress
  - node-tmp
  - opn
  - prettyjson
  - prompt
  - reflect-metadata
  - rimraf
  - simple-ssh
  - stack-trace
  - string-argv
  - wrap-ansi
  - yamljs
  - yargs

<div class="confluence-information-macro confluence-information-macro-note">

<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>

<div class="confluence-information-macro-body">

**Note:** All trademarks, trade names, service marks, and logos
referenced herein belong to their respective companies.

</div>

</div>

To read each complete license, <span class="confluence-link">[download
the attached zip
file](attachments/418944672/433573343.zip)</span>[. ](https://docops.ca.com/)

<div class="confluence-information-macro confluence-information-macro-note">

<span class="aui-icon aui-icon-small aui-iconfont-warning confluence-information-macro-icon"></span>

<div class="confluence-information-macro-body">

**Note:** For all Early Access Preview releases of Brightside CLI,
download the TPSRs from the [Brightside CLI project on
validate.ca.com](https://validate.ca.com/project/version/item.html?cap=13283cc32fd9439c85aeb18bba4ac1f6&arttypeid=%7B4109d6e9-6c06-448b-8eb2-6601a5616391%7D&artid=%7B5ACC31C0-2176-437F-B06B-8C572D48C76C%7D).

</div>

</div>

</div>

</div>

</div>

</div>

  - <span id="n-417008154">[CA Mainframe as a Service -
    Source](index.html)</span>
      - <span id="n-417008163">[Release
        Notes](Release-Notes_417008163.html)</span>
          - <span id="n-418944672">[.Release Notes
            v1.0](.Release-Notes-v1.0_418944672.html)</span>
    <!-- end list -->
      - <span id="n-417008178">[Installing](Installing_417008178.html)</span>
          - <span id="n-432460844">[Wireframe - z/osmf Configuration
            Documentation Map](432460844.html)</span>
              - <span id="n-432460843">[.Overview of the z/OS Management
                Facility Configuration Process
                v1.0](432460843.html)</span>
            <!-- end list -->
              - <span id="n-432460813">[Wireframe - Configure
                z/osmf](432460813.html)</span>
                  - <span id="n-432460812">[.Configure z/OS Management
                    Facility v1.0](432460812.html)</span>
            <!-- end list -->
              - <span id="n-432460817">[Wireframe - Configure z/osmf
                Security](432460817.html)</span>
                  - <span id="n-432460816">[.Configure z/OS Management
                    Facility Security v1.0](432460816.html)</span>
            <!-- end list -->
              - <span id="n-432460826">[Wireframe - Configure z/somf
                Cloud Provisioning](432460826.html)</span>
                  - <span id="n-432460825">[.Configure z/OS Management
                    Facility Cloud Provisioning
                    v1.0](432460825.html)</span>
            <!-- end list -->
              - <span id="n-432460832">[Wireframe - Configure z/osmf
                Cloud Provisioning Security](432460832.html)</span>
                  - <span id="n-432460831">[.Configure z/OS Management
                    Facility Cloud Provisioning Security
                    v1.0](432460831.html)</span>
        <!-- end list -->
          - <span id="n-417272826">[Install BrightSide
            Framework](Install-BrightSide-Framework_417272826.html)</span>
              - <span id="n-417272825">[.Install Brightside CLI
                v1.0](.Install-Brightside-CLI-v1.0_417272825.html)</span>
        <!-- end list -->
          - <span id="n-428197043">[Verify
            Installation](Verify-Installation_428197043.html)</span>
              - <span id="n-428197042">[.Validate Installation
                v1.0](.Validate-Installation-v1.0_428197042.html)</span>
            <!-- end list -->
              - <span id="n-432462123">[Identify and Correct Problems
                Detected by the Validate Profile
                Command](Identify-and-Correct-Problems-Detected-by-the-Validate-Profile-Command_432462123.html)</span>
                  - <span id="n-432462122">[.Identify and Correct
                    Problems Detected by the Validate Profile Command
                    v1.0](.Identify-and-Correct-Problems-Detected-by-the-Validate-Profile-Command-v1.0_432462122.html)</span>
        <!-- end list -->
          - <span id="n-429364971">[.Installing
            v1.0](.Installing-v1.0_429364971.html)</span>
    <!-- end list -->
      - <span id="n-424897041">[Using](Using_424897041.html)</span>
          - <span id="n-424897040">[.Using
            v1.0](.Using-v1.0_424897040.html)</span>
        <!-- end list -->
          - <span id="n-427028455">[How to Get Help With Brightside
            CLI](How-to-Get-Help-With-Brightside-CLI_427028455.html)</span>
              - <span id="n-427028454">[.How to Display Brightside CLI
                Help
                v1.0](.How-to-Display-Brightside-CLI-Help-v1.0_427028454.html)</span>
        <!-- end list -->
          - <span id="n-444506329">[Brightside CLI
            Groups](Brightside-CLI-Groups_444506329.html)</span>
              - <span id="n-444506328">[.Brightside CLI Command Groups
                v1.0](.Brightside-CLI-Command-Groups-v1.0_444506328.html)</span>
        <!-- end list -->
          - <span id="n-427862249">[Enable and Disable Experimental
            Commands](Enable-and-Disable-Experimental-Commands_427862249.html)</span>
              - <span id="n-427862248">[.Enable and Disable Experimental
                Commands
                v1.0](.Enable-and-Disable-Experimental-Commands-v1.0_427862248.html)</span>
        <!-- end list -->
          - <span id="n-425380145">[BrightSide Framework
            Scenarios](BrightSide-Framework-Scenarios_425380145.html)</span>
              - <span id="n-425380144">[.Brightside CLI Scenarios
                v1.0](.Brightside-CLI-Scenarios-v1.0_425380144.html)</span>
            <!-- end list -->
              - <span id="n-425380190">[Scenario
                3](Scenario-3_425380190.html)</span>
                  - <span id="n-425380189">[.Submit a Job and Print Job
                    Output
                    v1.0](.Submit-a-Job-and-Print-Job-Output-v1.0_425380189.html)</span>
    <!-- end list -->
      - <span id="n-417008229">[.Brightside CLI
        v1.0](.Brightside-CLI-v1.0_417008229.html)</span>
    <!-- end list -->
      - <span id="n-38207496">[Legal
        Notices](Legal-Notices_38207496.html)</span>

<div id="footer">

<div class="section footer-body">

Copyright © 2018 CA. All rights reserved.

<div class="footer-logo">

</div>

Document generated on Mar 01, 2018 15:11.

</div>

</div>

</div>
