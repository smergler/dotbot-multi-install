# Dotbot Multi Install

This is a [dotbot](https://github.com/anishathalye/dotbot) plugin that allows for multiple *nix-based installers.

While recently using dotbot, I found that there were a lot of plugins for installers, but most only had a few pieces of really good functionality.  I decided to build my own with lessons learned from these other repos.

## Currently supported installers:
- Apt
- Homebrew (including taps and casks)

## Standard Options
- `sudo` - Should we use sudo to install your packages? (default: false)

## Adding your own Installers

I also made adding your own installer very easy.  All you need to do is a python file to the root of the folder named after the installer. The following will allow you to use a `samplerd` directive to use the `samplerinstall` installer program

```
import os
# import the install base
cwd = os.path.dirname(os.path.abspath(__file__))
exec(open('{0}/install_base.py'.format(cwd)).read())

# create your class, override any internal functions needed.
class Sampler(InstallBase):
    _directive = 'samplerd'
    _cli_call = 'samplerinstall'
```
