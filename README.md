# prm
A minimal project manager for the terminal.

## What?
This program basically lets you CRUD projects. Upon activation, each projects runs its associated start-script; on deactivation, it runs the project stop-script.

These bash-scripts can be used for things like changing directories, setting environment variables, cleanup, etc.

### Example
One of my project start-script might for instance look something like this:

```bash
# cd to project directory
cd $HOME/src/Python/hello-world

# activate conda env
source activate hello-world

# show current git status
git status
```

The same project's stop-script might look like this:

```bash
# deactivate conda env
source deactivate hello-world

# clean up
rm *.log *.tmp
```

When you activate a new project, prm automatically stops any active projects.
When a project is deactivated, prm changes the working directory back to the path you were originally on before starting your first project.

Adding and editing projects will open the associated start- and stop-scripts in your editor (as defined by the `$EDITOR` environment variable).

## Why?
I found myself missing project management features (like those seen in text editors and IDEs) on the terminal.

## Usage
In order to work properly, prm *must* be sourced, *nor* run in a subshell.
I.e. `. ./prm`.

The easiest way to do this is probably to add an alias to prm in your `~/.bashrc` (or wherever you keep your aliases), like so:

```bash
alias prm=". path/to/prm.sh"
```

From help option:

```bash
Usage: prm [options] ...
Options:
  add <project name>       Add project.
  edit <project name>      Edit project.
  list                     List all projects.
  remove <project name>    Remove project.
  start <project name>     Start project.
  stop                     Stop active project.
  -h --help                Display this information.
  -v --version             Display version info.
```

## License
This software is released under the terms of the 3-clause New BSD License. See the [license](LICENSE.txt) file for details.
