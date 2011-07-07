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
* Git clone (requires git)

## Usage

get-addon must be run from within an Omeka plugins or themes directory.
If it is run from any other location, it will simply print an error and exit.

    get-addon [options] <addon name>

The `<addon name>` portion is required, regardless of what options are used.
Per Omeka's naming conventions, an plugin name should be written
UpperCamelCased, while a theme name should be written lowercase-and-hyphenated.

### Options

*   `-w`
    *   Read/write clone. Clones the addon from a URL that will allow push as
        well as pull.
*   `-v <version number>`
    *   Download an official zipped release.
*   `-p`
    *   Pretend.  Print the commands that would be run, but perform no actual
        operations.
*   `-h`
    *   Help. Displays basically this information about usage and options.

get-addon detects what kind of addon you are trying to install by checking what
directory you run it from.  In the plugins directory, get-addon looks for
plugins, in the themes directory, get-addon looks for themes.

By default, with no options specified, get-addon will check out the addon you specified from a read-only Git URL.

## Example

Getting the ExhibitBuilder plugin (you must be in your Omeka plugins dir):

* Checkout from Git (read-only): `get-addon ExhibitBuilder`
* Checkout from Git (read-write): `get-addon -w ExhibitBuilder`
* Download zip of 1.3-2.1: `get-addon -v 1.3-2.1 ExhibitBuilder`

## Caveats

get-addon only works for addons that are hosted at [github.com/omeka], or are available for download from [omeka.org].
