1. Create a virtual machine with docker-machine using the virtualbox driver, and
named Char.
2. Get the IP address of the Char virtual machine.
3. Define the variables needed by your virtual machine Char in the general env of your
terminal, so that you can run the docker ps command without errors. You have
to fix all four environment variables with one command, and you are not allowed
to use your shell’s builtin to set these variables by hand.
4. Get the hello-world container from the Docker Hub, where it’s available.
5. Launch the hello-world container, and make sure that it prints its welcome message, then leaves it.
6. Launch an nginx container, available on Docker Hub, as a background task. It
should be named overlord, be able to restart on its own, and have its 80 port
attached to the 5000 port of Char. You can check that your container functions
properly by visiting
http://<ip-de-char>:5000 on your web browser.
7. Get the internal IP address of the overlord container without starting its shell and
in one command.
8. Launch a shell from an alpine container, and make sure that you can interact
directly with the container via your terminal, and that the container deletes itself
once the shell’s execution is done.
9. From the shell of a debian container, install via the container’s package manager
everything you need to compile C source code and push it onto a git repo (of
course, make sure before that the package manager and the packages already in the
container are updated). For this exercise, you should only specify the commands
to be run directly in the container.
10. Create a volume named hatchery.
11. List all the Docker volumes created on the machine. Remember. VOLUMES.