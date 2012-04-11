Modular/Master Control Program

This is a slightly different approach to create a set of application which will
reside on DCPU-16. MCP is meant to be compiled somewhere, and customized before
first run on your ship system.

MCP won't allow dynamic application loading. Instead, you can customize your
MCP to perform specific tasks. MCP gives you a set of APIs, which are pretty
consistent across themselves.

Some parts of the code (and inspirations or influences) are from AtlasOS
(https://github.com/Noxer/AtlasOS/), 0x42 (https://github.com/jdiez17/0x42c),
ProtoCS (http://0x10cforum.com/forum/m/4932880/viewthread/2759668-protocs),
and others.

================
Including modules:

Just copy and paste a module code to the end, and set modules variable in line
30. And there it is, a new module is installed.

I will be working on some automation for this, but now, to prepare fully
working snapshot of MCP, you can just use (on Windows):

copy mcp.dasm16 + module_console.dasm16 + module_clear.dasm16 mcp-dist.dasm16

This generates a mcp-dist.dasm16, where you need to edit "modules" variable,
around line 30.

:modules
dat module_console, module_clear, 0

And also you need to set up which module will be started when the computer is 
run, by defining entry procedure (about line 33):

:module_init dat module_console

Assemble, and run.
It will give you an access to text console, now only with "clear" command, to
clear the screen.

================

--
Marcin