# callback_modules
This is a collection of callback modules for ansible.

### Yaml2 ###
Currently working on making the standard yaml module it a more robust callback module.

Changes:
Incorporates the stdout of the minimalist callback module that is default for ansible ad-hoc with the yaml module so that the stdout is still shown when using ad-hoc commands.

### Default2 ###
Make the default plugin more readable

Changes:
When the dump results is called, added an indent of 4. This seems to make the output multi line instead of a single line, and making it easier to read, along with indenting the output. This was borrowed from the minimalist callback plugin. 
