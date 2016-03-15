# Login System Example

This is a login system example, basically modified from the original auction
example. It is intended to model a simple login system. A trusted
third party will do something like zero knowledge proof to illustrate
whether the user's password is equal to the root's password.

The example utilizes feature of the persistent store in Fabric, where
if the user / root get shutdown by accident, it will be easy to recover
without losing information.

This directory contains the following sub-directories:

  - src: source code for the login example
  - bin: a collection of scripts for running the example
  - etc: configuration files for the example's Fabric nodes

## Usage

This example uses three stores ("userStore", "rootStore", "ttpStore").

  0. Cloning the repo from Github.
     Start in the login example directory and build the initialization
     code for setting up the principal hierarchy:

        $ git clone https://github.com/yzgysjr/try_fabric.git $FABRIC/examples/login/
        $ cd $FABRIC/examples/login/
        $ ant

  1. Start up instances of the trusted third party, root stores,
     and user stores. The 'start-all' script will start each store
     in a separate xterm window:

        $ bin/start-all

     You can also use an xterm replacement (e.g., gnome-terminal or
     konsole):

        $ XTERM=gnome-terminal bin/start-all

     Or, if you prefer, you can start each store individually in your
     favourite terminal emulator:

        $ bin/start-store userStore
        $ bin/start-store rootStore
        $ bin/start-store userStore

  2. If you are starting from fresh stores, you will need to initialize
     the application state. Otherwise, skip to step 3 below.

     Run the 'initialize' script to initialize the stores' state. This
     will initialize the principal hierarchy, publish the example's code
     to the stores, and initialize the application's state.

        $ bin/initialize

  3. The 'login' script will run the example.

        $ bin/login

  4. Exit the stores with the "exit" command in each console (you can
     also use CTRL-D).

     You can clean up the stores' persistent state by removing 'var'
     from the login example directory:

        $ rm -rf var
