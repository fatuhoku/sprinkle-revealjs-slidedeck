Sprinkle presentation
=========================
Below are the main points.

### Title page

### Developers and Dev Ops
That funny grey area between sweet agile development
and system administration or IT operations.

Lots of IT infrastructure in software dev:
 - developer machine
 - QA environment
 - stage environment
 - production environment
 - client infrastructure...

5 machines floating about with possibly different configurations.

Given the scale not even emacs operators easily manage the configuration and
state of his 5 servers, or more, depending on scale. (octopus management)

Common questions
'is the right version of RVM installed?'
'is the right version of Ruby/Python activated (through RVM, PythonBrew)?'
'are all my project dependencies installed?'
'are my <tt>/etc/fstab</tt> settings correct?'
'have I updated /etc/fstab?'
'have I updated the port numbers Nginx runs on?'

Save yourself from writing bash scripts. They're not so naturally
idempotent.

Painful to iterate to develop such a script (previous side effects...)

I know what you're all thinking. Puppet!

### Puppet is not the answer.
 - 'puppet apply' builds
 - almost mandates virtualisation
 - Slow development time.
 - Designed for large infrastructures.
 - SSL Certificate management (add the puppet master)
 - Requires yet another host public puppet master host (which also requires its
   own provisioning)
 - Pull-based paradigm, wait 30 mins. Problematic.

We just have to ask, what is the developer's favourite tool.
SSH. Imagine if you could just SSH into everything and do just the
right thing on each of them.

It's about what you, the dev, wants to do to a machine.

### Sprinkle is your friend
 - Dependency based.
 - Push (active) server configuration
 - Idempotent given sensible verification commands
 - works over SSH
 - Ruby DSL
 - Might even work on Windows
 - Capistrano

#### Capistrano
Yet another Ruby DSL for running scripts on multiple servers over SSH.
Quite Ruby on  Rails oriented but thankfully Sprinkle hides this from you...
somehow... and allows you to install anything you wish, pretty much.

### Limitations
Testing is still a bitch.
You will need to iteratively
Development of such a script is much faster than making a Puppet script.
SSH access to every machine requires provisioning.
SSH key management
Often requires SSH root access (necessarily less secure)
