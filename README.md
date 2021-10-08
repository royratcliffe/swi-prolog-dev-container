# SWI Prolog Dev Container

Sets up SWI Prolog in a VS Code [development
container](https://code.visualstudio.com/docs/remote/containers). You need
[Docker](https://www.docker.com/products/docker-desktop) and [VS
Code](https://code.visualstudio.com/) with [Microsoft's Remote
Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
extension. You can run SWI Prolog from a docker container within Visual Studio
Code.

## X11 and Emacs

The container sets up `DISPLAY` for X11 connectivity.

```json
"runArgs": [
    "-e", "DISPLAY=host.docker.internal:0"
],
```

You can then run the `emacs` predicate, e.g.

```bash
$ swipl -g emacs
```

or, of course, you can launch it and other graphical Prolog tools from the
ubiquitous _Do What I Mean_ prompt.

```text
Welcome to SWI-Prolog (threaded, 64 bits, version 8.5.0)
SWI-Prolog comes with ABSOLUTELY NO WARRANTY. This is free software.
Please run ?- license. for legal details.

For online help and background, visit https://www.swi-prolog.org
For built-in help, use ?- help(Topic). or ?- apropos(Word).
```
```prolog
?- emacs.
true.

?- prolog_ide(thread_monitor), prolog_ide(xref).
```

This assumes that you have an X server at `host.docker.internal` which
corresponds to the host interface.

On Windows, you can install an X11 server using [VcXsrv Windows X
Server](https://community.chocolatey.org/packages/vcxsrv) using Chocolatey. Do
not forget to disable access control. The enclosed `config.xlaunch` X launcher
configuration includes the necessary `DisableAC="True"` setting. Double-click it
to launch the X server on Windows.

# MIT License

Copyright (c) 2021 Roy Ratcliffe, United Kingdom

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
