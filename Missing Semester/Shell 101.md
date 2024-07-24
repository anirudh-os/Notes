# The Shell

* Flags do not take value but options do
* Flags and options are arguments to the commands (which are essentially programs)
* `>` and `<` are used for linking
    * `>` tells the shell that the output of the preceeding program needs to be forwarded / rewired to the succeeding file
    ```bash
    $ echo hello > hello.txt
    ```
    This means the output of hello is to be printed in hello.txt
    * `<` tells the shell to give thecontent of the succeding file to the preceeding program
    ```bash
    $ cat > hello.txt
    ```
    Here the  contents of hello.txt are taken as input for the cat program
* `>>` is used to append
    ```bash
    $ cat < hello.txt > hello2.txt
    $ cat hello2.txt
    hello
    $ cat < hello.txt >> hello2.txt
    $ cat hello2.txt
    hello
    hello
    ```
* `|` is called pipe and it allows to pass ythe output of one program to another
    ```bash
    $ ls -l / | tail -n1
    ```
    Here the output of ls is piped to tail[^1]
* `sudo` means 'do as super user' 
    * It is used to run programs with the permissions of the root user or admin
    * commands starting with the pound symbol (#) instead of the dollar symbol ($) mean that the commands are being run as the root user
    ```bash
    # echo 1 > /sys/net/ipv4_forward
    ```
* `tee` command takes the input and writes it to a file "and" to the standard output
    ```bash
    $ echo 500 | sudo tee brightness
    ```
    Since the `tee` is run as the root, it can access and modify the file contents of the `brightness` file. It takes 500 as inpput and writes it to the file and also to the terminal
* `xdg-open` command helps us to open the file in an appropriate application
    * This only works on linux or macos.
    ```bash
    $ xdg-open sample.html
    ```


[^1]: `tail` is a program to print the last part of a file given as its input (for more details run `man tail` on bash)

## Useful Commands (or Shorthands)

* `cd ~` (cd tilde) refers to the home directory
    * It can be used as a reference in relative paths like `cd ~bin/`
* `cd -` switches to the previous directory u were in   
* `ls -l` lists the contents with additional info like their type and permissions