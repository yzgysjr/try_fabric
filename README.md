# Login System Example

This is an example of [Fabric](https://github.com/apl-cornell/fabric),
basically modified from the original auction example.
It is intended to model a simple login system. A trusted
third party will do something like zero knowledge proof to illustrate
whether the user's password is equal to the root's password.

The example utilizes feature of the persistent store in Fabric, where
if the user / root is shutdown by accident, it will be easy to recover
without losing persistent data.

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

        $ bin/start-store ttpStore
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

## References
[1] Owen Arden, Michael D. George, Jed Liu, K. Vikram, Aslan Askarov,
    and Andrew C. Myers. Sharing mobile code securely with information
    flow control. In Proc. IEEE 2012 Symposium on Security and Privacy,
    pages 191–205, San Francisco, CA, USA, May 2012. Software release
    at <http://www.cs.cornell.edu/projects/fabric/>.

[2] Jed Liu, Michael D. George, K. Vikram, Xin Qi, Lucas Waye, and
    Andrew C. Myers. Fabric: A platform for secure distributed
    computation and storage. In Proc. 22nd ACM Symposium on Operating
    Systems Principles (SOSP), pages 321–334, Big Sky, MT, USA, October
    2009. Software release at
          <http://www.cs.cornell.edu/projects/fabric/>.

[3] Stephen Chong, K. Vikram, and Andrew C. Myers. SIF: Enforcing
    confidentiality and integrity in web applications. In Proc. 16th
    USENIX Security Symposium, pages 1–16, Boston, MA, USA, August
    2007. See <http://www.cs.cornell.edu/jif/sif/>.

[4] Michael J. Carey, David J. DeWitt, and Jeffrey F. Naughton. The OO7
    Benchmark. In Proc. ACM SIGMOD 1993 International Conference on
    Management of Data, pages 12-21, Washington, DC, USA, May 1993.
