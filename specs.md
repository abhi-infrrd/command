Let's design a command line applications library or framework.

# What is a Command Line Application ?

A command line application (which I will call shortly command) is a program with no graphic interface. We run it from a console, giving it some arguments and it does **something**. This **something** can be *showing some text in the console*, *downloading a file from the internet*, ... Let's call these the **Effects** of the command. These effects depends on the state of the environment (*command line arguments*, *standard input*, *filesystem*, *internet connection*, ...) on which the command is being executed.

> A **command** is a function that takes an **environment** and applies some **effects** on it.

A commands framework should have the following features:

1. Define commands: define the syntax and the logic.
2. Test commands: run the command on mock env and check the effects.
3. Compose commands: 
    - call command from other commands.
    - make command which run mutiple commands in sequence.
    - make command which run mutiple commands in parallel.
4. Predefined Commands:
    - Help: shows the help message for a command.
    - Version: shows the version of a command.
    - ...
5. Easy way to read/write from/to different parts of the environment:
    - Console: command line args, stdin, stdout, stderr
    - Filesystem
    - ...
6. ...


## Functional Approach

```php
$command = function(Env $env) : Effects {
    // ...
}

function apply(Effects $effects, Env $env) {
    // ...
}

function execute(Closure $command, Env $env) {
    apply($command($env), $env);
}
```

