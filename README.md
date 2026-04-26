# Welcome to AIon

## Introduction

Learn more about [AIon](http://appinventor.mit.edu). 

AIon is a specialized platform built on the MIT App Inventor framework, designed to teach kids AI fundamentals through interactive blocks, machine learning inference, and ethical system design.

This code is designed to be run in Google's App Engine. MIT runs a public instance that all are welcome to use to build App Inventor Applications. You do not need to compile or use this code if you wish to build AIon applications.

We provide this code for reference and for experienced people who wish to operate their own AIon instance and/or contribute to the project.

This code is tested and known to work with Java 11.

## Contributors

The best way to go about integrating changes in AIon is to start a conversation in the [Open Source forum](https://community.appinventor.mit.edu/c/open-source-development/10) about whatever you intend to change or add.

We use ***very brief and informal*** design documents with descriptions of the proposed changes and screenshots of how the functionality would look like and behave, in order to gather as much feedback from the community, as early as possible. We generally use shared Google docs for this (with permissions to add comments), but any format that is accessible from a web browser (and allows comments) would do.

If you have skipped this step and have gone ahead and made your changes already, feel free to open a pull request, but don't be too surprised if we ask you to go back and document it in a design document. Remember that the main goal of doing this is ***to gather as much feedback, as early as possible***. We will also possibly ask you to put an instance with your changes on [appspot](http://appspot.com), and provide a modified Companion app (if that applies) so that reviewers can play with the changes before looking at the source.

Check out our open source [site](http://appinventor.mit.edu/appinventor-sources/) to find a lot more information about the project and how to contribute to it.

## Setup Instructions (Manual)

This is a quick guide to get started with the sources. More detailed instructions can be found [here](https://docs.google.com/document/pub?id=1Xc9yt02x3BRoq5m1PJHBr81OOv69rEBy8LVG_84j9jc), a slide show can be seen [here](http://josmas.github.io/contributingToAppInventor2/#/), and all the [documentation](http://appinventor.mit.edu/appinventor-sources/#documentation) for the project is available in our [site](http://appinventor.mit.edu/appinventor-sources/).

### Dependencies

You will need a full Java JDK (version 11, OpenJDK preferred; JRE is not enough) and [ant](http://ant.apache.org/) (version 1.10) to compile the sources.

You will also need a copy of the [Google Cloud SDK](https://cloud.google.com/appengine/docs/standard/java/download) to run the development servers. When setting up the gcloud cli you might be asked if you'd like to install Python 3.11, as the cli depends on it. In case of any issues with Python versions, check the value of the CLOUDSDK_PYTHON environment variable, which the cli can use to point to the right version.

If you want to make changes to the sources, you will have to run an automated test suite, and for that you will also need a recent version of NodeJS (node 20+ works) and the Firefox browser installed on your machine. Have a look at the testing section for more information.

Finally, if you want to make changes to the markdown docs you will need Ruby (versions 2.6 or 2.7).

### Forking or cloning

Consider ***forking*** the project if you want to make changes to the sources. If you simply want to run it locally, you can simply ***clone*** it.

#### Forking

If you decide to fork, follow the [instructions](https://help.github.com/articles/fork-a-repo) given by GitHub. After that you can clone your own copy of the sources with:

    $ git clone https://github.com/YOUR_USER_NAME/appinventor-sources.git

Make sure you change *YOUR_USER_NAME* to your user name.

Configuring a remote pointing to the original repository is also a good idea if you are forking:

    $ cd appinventor-sources
    $ git remote add upstream https://github.com/mit-cml/appinventor-sources.git

Finally, you will also have to make sure that you are ignoring files that need ignoring:

    $ cp sample-.gitignore .gitignore

### Checkout dependencies

AIon uses the [Picrin](https://picrin.readthedocs.io/en/latest/) Scheme implementation. It is unlikely that most contributors will need to make changes to this dependency, but it is necessary for local compilation, so you must initialize and track this library as a submodule. The first time after forking or cloning the repository, you can perform the following command:

    $ git submodule update --init

If you need to switch back to a branch that does not contain the dependency in the tree, you will need to run the command:

    $ git submodule deinit --all

to clear out the submodules ___before switching branches___. When switching back, you will need to repeat the initialization and update procedure above.

[Blockly](https://github.com/google/blockly) is also a dependency, currently being used as a slightly modified version 10 that can be found at [mit-cml/blockly](https://github.com/mit-cml/blockly/tree/rc/10.5.0).

### Troubleshooting common installation issues

Run this command to run a self-diagnosis of your environment. This command tries to figure out common installation issues and offers you a solution to fix them yourself. Make sure this passes all the checks before you proceed further.

#### Linux and macOS

```bash
./buildtools doctor
