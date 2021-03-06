## What is a mono repo?
One Repo, many related JS/TS packages, co-located in a git repo.

## Why sould i care ?
- Encapsulation tools that JS ecosystem is missing
- One commit can modify many packages, single history of a collection
- Test a family of packages together and before a release
- Dramatically reduced maintanance overhead compared to N Libraries

### Problems
- More challenging to manage than a single "monolith" repo
- Sveral new tools we'll need to learn
- new risks you'll need to mitigate
- ...but sometimes it's worth it

## Topics
- Yarn workspaces
- TypeScript composite projects
- Build scripts for monorepos
- Lerna
- Api Extractor
- "Pacakge private" and "Project private" interfaces
- Hassle-free "publish to npm" testing
- Versioning strategies
- App and Library Use Cases
- "Wrapper" packages
- Private "dev utility" packages


`"C:\Program Files\nodejs\node_modules\typescript\bin\tsc" -b .`
``rm -rf */*.tsbuildinfo */dist`
in root
`yarn add -WD rimraf`
`yarn add -WD eslint @typescript-eslint/eslint-plugin @typescript-eslint/parser`
`yarn add -DW lerna`
`yarn add -DW scripty`
`chmod +x scripts/greet` - `chmod -R +x scripts-win/greet` - `chmod -R +x scripts-win` make file executable
`ls -all scripts`
`yarn add -WD @commitlint/cli @commitlint/config-conventional @commitlint/config-lerna-scopes commitlint husky lerna-changelog`
`echo "build(api): change something in api's build" | yarn commitlint` fail because api not is a scope (package) right now
`echo "build(types): change something in api's build" | yarn commitlint`
`volta install commitlint`
`echo "build(api): change something in api's build" | commitlint` fail because api not is a scope (package) right now
`rm -r -f .git/hooks/`
`cat .git/hooks/commit-msg`
`echo "ft(types): more reasonable default types for generics" | commitlint`
`echo "feat(types): more reasonable default types for generics" | commitlint`

`lerna version`
`lerna version --conventional-commits` (to upgrade version)

`volta install verdaccio`
`rm -rf ~/.local/share/verdaccio`
`lerna publish --conventional-commits`
`lerna exec 'yarn publish'`


`lerna add @shlack/utils --scope '@shlack/{ui,data}'`
`lerna add @shlack/types --scope '@shlack/{ui,data}'`
`lerna add @shlack/data --scope @shlack/ui`
`lerna link`
`lerna run dev --scope @shlack/ui`
`lerna run dev --scope @shlack/ui --stream`
`node packages/ui/server/server.js `

`yarn add -WD @microsoft/api-extractor`
`yarn api-extractor init`

`lerna exec 'mkdir etc'`
`yarn build`
`lerna api-report`

`yarn add -WD  @microsoft/api-documenter`
`yarn api-docs`

`lerna link`
`lerna run clean`
`lerna run build --concurrency 2`
`lerna run test --concurrency 2 --stream`

in utils
`yarn add react date-fns`
`yarn add -D @types/react @types/date-fns`

in utils and types
`yarn add -D @types/jest jest`
`yarn add -D @babel/preset-env @babel/preset-typescript`

## Install volta
Volata manages global and package specific dependencies.

`volta install typescript@3`

`yarn tsc --version` still working `tsc --version`

`ls -all node_modules/.bin`

`volta pin node yarn`

# JS/TS Monorepos

[![Node.js CI (solution)](https://github.com/mike-north/js-ts-monorepos/workflows/Node.js%20CI%20(solution)/badge.svg)](https://github.com/mike-north/js-ts-monorepos/actions?query=workflow%3A%22Node.js+CI+%28solution%29%22)
[![TypeScript@Next tests (solution)](https://github.com/mike-north/js-ts-monorepos/workflows/TypeScript@Next%20tests%20(solution)/badge.svg)](https://github.com/mike-north/js-ts-monorepos/actions?query=workflow%3A%22TypeScript%40Next+tests+%28solution%29%22)

## Project setup

First, you should ensure you have [your ssh keys working with GitHub](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent). You can verify this by running

```sh
ssh git@github.com
```

and getting a response like

```sh
Hi jaramillo-carlos! You've successfully authenticated, but GitHub does not provide shell access.
Connection to github.com closed.
```

### Tools

Next, make sure you have installed [volta](http://volta.sh/) which ensures you have the right version of node and yarn for this project

We also strongly recommend the use of [Visual Studio Code](https://code.visualstudio.com/) as an authoring tool. If you use something else, you're on your own.

### Clone

Next, checkout a working copy of this project

```sh
git clone git@github.com:jaramillo-carlos/js-ts-monorepos
```

enter the directory you just created

```sh
cd js-ts-monorepos
```

### Install dependencies

[`yarn`](https://yarnpkg.com/) is the recommended package manager to use with this project. Please use it instead of npm.

Install dependencies with yarn by running

```sh
yarn
```

### Starting the project

Start up the project in development mode by running

```sh
yarn dev
```

Changing any files in the `src` folder will result in an incremental rebuild, and a refresh of the screen.

By default, the app is served on https://localhost:1234.

# Legal

&copy; 2020 LinkedIn, All Rights Reserved

## Licensing

The code in this project is licensed as [BSD-2-Clause](https://opensource.org/licenses/BSD-2-Clause) license, and the written content in the ./notes folder is licensed under [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)
