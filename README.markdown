# get-addon

get-addon is a utility script that simplifies the process of installing
addons for an Omeka installation.

From an Omeka plugins or themes directory, you only need to specify the name of 
the addon you want to get, and get-addon will download and install it to the
correct location.

## Requirements

get-addon is a bash script, so obviously bash is required. Each of get-addon's
methods for fetching an addon also has requirements. You must fulfill the
requirements of at least one fetch method for get-addon to do anything useful.

### Fetch Methods

* Zip download from omeka.org (requires wget and unzip)
* Subversion checkout (requires Subversion)
* Git-SVN clone (requires git with Subversion support)

## Usage

get-addon must be run from within an Omeka plugins or themes directory.
If it is run from any other location, it will simply print an error and exit.

    get-addon [options] <addon name>

The `<addon name>` portion is required, regardless of what options are used.
Per Omeka's naming conventions, an plugin name should be written
UpperCamelCased, while a theme name should be written lowercase-and-hyphenated.

### Options

*   `-t <tag name>`
    *   Check out a specific Subversion tag.
*   `-b <branch name>`
    *   Check out a specific Subversion branch.
*   `-v <version number>`
    *   Download an official zipped release.
*   `-g`
    *   Use git-svn to clone the addon's repository.
*   `-p`
    *   Pretend.  Print the commands that would be run, but perform no actual
        operations.
*   `-h`
    *   Help. Displays basically this information about usage and options

get-addon detects what kind of addon you are trying to install by checking what
directory you run it from.  In the plugins directory, get-addon looks for
plugins, in the themes directory, get-addon looks for themes.

By default, with no options specified, get-addon will check out the Subversion trunk of the addon you specified.

## Example

Getting the ExhibitBuilder plugin (you must be in your Omeka plugins dir):

* Checkout SVN trunk: `get-addon ExhibitBuilder`
* Checkout version 1.3-2.1: `get-addon -t 1.3-2.1 ExhibitBuilder`
* Download zip of 1.3-2.1: `get-addon -v 1.3-2.1 ExhibitBuilder`
* Create local git-svn repo: `get-addon -g ExhibitBuilder`

## Caveats

get-addon only works for addons that are hosted at [omeka.org].
