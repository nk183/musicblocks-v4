# Music Blocks 2

[![GitHub Super-Linter](https://github.com/sugarlabs/musicblocks-2/workflows/Super-Linter/badge.svg)](https://github.com/marketplace/actions/super-linter)

A complete overhaul of the original [Music Blocks](https://github.com/sugarlabs/musicblocks).

## Notes

Please visit the [discussions](https://github.com/sugarlabs/musicblocks-2/discussions) tab at the
top of the repository to follow the planning progress.

## Setup Development Environment

_This project is containerized using [**docker**](https://www.docker.com/). Therefore, it requires
**docker** to be installed on the development machine._

1. Setup _docker_.

    - For _Linux_, [install _Docker Engine_](https://docs.docker.com/engine/install/).
    - For _Windows_ or _Mac_ (_x86_64 / amd64_),
    [install _Docker Desktop_](https://www.docker.com/products/docker-desktop).

2. Open a teminal and navigate to working directory (where the source code will reside).

3. _Git Clone_ (additional [installation](https://git-scm.com/downloads) of Git required on
Windows) this repository using

    ```bash
    git clone https://github.com/sugarlabs/musicblocks-2.git
    ```

4. Build _docker image_ (built only first time) and launch _docker network_ using

    ```bash
    docker-compose up -d
    ```

5. In another terminal, run

    ```bash
    docker attach musicblocks
    ```

6. The _Linux Debian 10.7_ (_buster_) _shell_ in the _docker container_ named _musicblocks_ is
spawned and standard input/output is connected to the terminal.

    _**Node**_ (_Node.js Runtime_), _**npm**_ (_Node Package Manager_), _**tsc**_ (_TypeScript
    Compiler_), and _**Dart-SDK**_ (_Dart - Software Development Kit_) should be installed. Check
    using

    ```bash
    node --version && npm --version && tsc --version && dart --version
    ```

    Output should look like

    ```bash
    v14.15.1
    6.14.8
    Version 4.1.3
    Dart SDK version: 2.10.4 (stable) (Unknown timestamp) on "linux_x64"
    ```

7. To shut down the _docker network_, run (in the terminal where you ran `docker-compose up -d`)

    ```bash
    docker-compose down
    ```

8. To install all the dependencies (in `package.json`), run

    ```bash
    npm ci
    ```

9. To spawn a _HTTP Server_ (uses _Python 3_'s `http.server`), run

    ```bash
    npm run serve
    ```

    This is spawned on `0.0.0.0:80` inside the container, but mapped to `localhost:5001` on host.
    Visit `localhost:5001` in a browser to view the webpage served.

10. Run _React scripts_ using

    - For unoptimized development serving, run

        ```bash
        npm start
        ```

        This is spawned on `127.0.0.1:3000` inside the container, but mapped to `localhost:5000` on
        host. Visit `localhost:5000` in a browser to view the webpage served.

    - For testing, run

        ```bash
        npm run test
        ```

    - For generating production build, run

        ```bash
        npm run build
        ```

    _**Note:**_ If you're running using _Docker Desktop_ on _Windows_ or _Mac_, you might experience
    longer execution times for these scripts. This happens due to cross-file-system communication.
    Duration varies across machines; duration primarily depends on hard drive speed.

11. Miscellaneous commands

    - To launch the _Node runtime_, run

        ```bash
        node
        ```

    - To run a _JavaScript_ file, say `file.js`, run

        ```bash
        node file.js
        ```

    - To transpile a _TypeScipt_ file, say `file.ts`, to _JavaScript_ run

        ```bash
        tsc file.ts
        ```

        This compilation produces `file.js`.

    - To run a _Dart_ file, say `file.dart`, run

        ```bash
        dart file.dart
        ```

    - To compile a _Dart_ file, say `file.dart`, run

        ```bash
        dart compile js -o file.js file.dart
        ```

        This compilation produces `file.js`, `file.js.deps`, and `file.js.map`.

## Editor

_All code is just plain text, so it doesn't really matter what you use to edit them._ However, using
modern, feature-rich IDEs/text-editors like [_**Atom**_](https://atom.io/),
[_**Brackets**_](http://brackets.io/), [_**WebStorm**_](https://www.jetbrains.com/webstorm/),
[_**Sublime Text**_](https://www.sublimetext.com/),
[_**Visual Studio Code**_](https://code.visualstudio.com/), etc. makes life way easier. These come
with a directory-tree explorer, and an integrated terminal, at the very least, while having support
for plugins/extensions to expand their functionality.

Some (non-exhaustive) benefits of using these are _syntax highlighting_,
_warning/error annotations_, _formatting_, _auto-refactoring_, tons of customizable
_keyboard shortcuts_, etc.

**Visual Studio Code** (**VSCode**) is currently the most-popular code editor for reasons like being
_lightweight_, _cleaner_, large marketplace of _extensions_, integrated _Source Control_ features,
_debugger_, _remote explorer_ support, _Regular Expression_ (_regex_) based find/replace, etc.

In fact, a workspace configuration file for _vscode_`.vscode/settings.json` has already been added.
Recommended extensions for this project are `Babel JavaScript`, `Dart`, `Docker`, `ESLint`,
`Git Graph`, `GitLens`, `markdownlint`, `Prettier`, `SCSS IntelliSense`, and `SVG`.

All that, however, shouldn't necessarily stop you from using **Emacs**, **Nano**, or **Vim**, if
that's your poison :D. Happy coding!
