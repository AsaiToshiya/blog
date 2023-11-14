---
title: "Electron Forge: `make` でエラーが発生した場合の回避策"
date: 2023-11-14 12:32:20
updated: 2023-11-14 12:32:20
tags: [Electron Forge, トラブルシューティング]
---

```bat
C:\path\to\app>pnpm run make

> app@1.0.0 make C:\path\to\app
> electron-forge make

✔ Checking your system
✔ Loading configuration
✔ Resolving make targets
  › Making for the following targets: squirrel
❯ Running package command
  ✔ Preparing to package application
  ✔ Running packaging hooks
    ✔ Running generateAssets hook
    ✔ Running prePackage hook
  ❯ Packaging application
    ❯ Packaging for x64 on win32
      ✖ Copying files
        › Failed to locate module "debug" from "C:\path\to\app\node_modules\electron-squirrel-startup"

                This normally means that either you have deleted this package already somehow (c…
      ◼ Preparing native dependencies
      ◼ Finalizing package
  ◼ Running postPackage hook
◼ Running preMake hook
◼ Making distributables
◼ Running postMake hook

An unhandled rejection has occurred inside Forge:
Error: Failed to locate module "debug" from "C:\path\to\app\node_modules\electron-squirrel-startup"

        This normally means that either you have deleted this package already somehow (check your ignore settings if using electron-packager).  Or your module installation failed.
at Walker.walkDependenciesForModuleInModule (C:\path\to\app\node_modules\.pnpm\flora-colossus@2.0.0\node_modules\flora-colossus\lib\Walker.js:57:19)
    at async Walker.walkDependenciesForModule (C:\path\to\app\node_modules\.pnpm\flora-colossus@2.0.0\node_modules\flora-colossus\lib\Walker.js:113:13)
    at async Walker.walkDependenciesForModuleInModule (C:\path\to\app\node_modules\.pnpm\flora-colossus@2.0.0\node_modules\flora-colossus\lib\Walker.js:63:13)
    at async Walker.walkDependenciesForModule (C:\path\to\app\node_modules\.pnpm\flora-colossus@2.0.0\node_modules\flora-colossus\lib\Walker.js:113:13)
    at async C:\path\to\app\node_modules\.pnpm\flora-colossus@2.0.0\node_modules\flora-colossus\lib\Walker.js:133:21
 ELIFECYCLE  Command failed with exit code 1.
```

<!-- more -->

## 環境

- Windows 10
- npm 8.12.0
- pnpm 8.8.0
- Electron Forge 6.4.2
- Electron Packager 17.1.2

## 回避策

Electron Packager を使用する。

```bat
C:\path\to\app>npm install --save-dev electron-packager
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.

up to date, audited 465 packages in 2s

75 packages are looking for funding
  run `npm fund` for details

1 high severity vulnerability

To address all issues, run:
  npm audit fix --force

Run `npm audit` for details.

C:\path\to\app>npx electron-packager ./
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.
Packaging app for platform win32 x64 using electron v26.2.2
Wrote new app to: C:\path\to\app\app-win32-x64
```

## 試したこと

### pnpm で実行

```bat
pnpm run make
```

冒頭のエラーが表示される。

Electron Forge は pnpm をサポートしていない。

参考: [Support pnpm · Issue #2633 · electron/forge](https://github.com/electron/forge/issues/2633)
参考: [feat: support pnpm by makeryi · Pull Request #3351 · electron/forge](https://github.com/electron/forge/pull/3351)

### npm で実行

```bat
npm run make
```

以下のエラーが表示される。

```bat
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.

> app@1.0.0 make
> electron-forge make

✔ Checking your system
✔ Loading configuration
✔ Resolving make targets
  › Making for the following targets: squirrel
❯ Running package command
  ✔ Preparing to package application
  ✔ Running packaging hooks
    ✔ Running generateAssets hook
    ✔ Running prePackage hook
  ❯ Packaging application
    ❯ Packaging for x64 on win32
      ✔ Copying files
      ✔ Preparing native dependencies [1s]
      ✖ Finalizing package
        › EPERM: operation not permitted, rmdir 'C:\Users\username\AppData\Local\Temp\electron-packager\win32-x64\app-win32-x64-98kJwf\resources\app\images'
  ◼ Running postPackage hook
◼ Running preMake hook
◼ Making distributables
◼ Running postMake hook

An unhandled rejection has occurred inside Forge:
Error: EPERM: operation not permitted, rmdir 'C:\Users\username\AppData\Local\Temp\electron-packager\win32-x64\app-win32-x64-98kJwf\resources\app\images'
```

### Issue の解決策 (その 1)

[resources/app folder has broken permissions · Issue #402 · electron/packager](https://github.com/electron/electron-packager/issues/402#issuecomment-227413182)

```bat
cd %TEMP%\electron-packager\win32-x64
attrib -R app-win32-x64-98kJwf
```

エラーは変わらない。

### Issue の解決策 (その 2)

[Removing temporary directory on Windows fails with no error · Issue #431 · electron/packager](https://github.com/electron/electron-packager/issues/431#issuecomment-918567179)

エラーは変わらない。

### Electron Packager の Asar を有効化

package.json:

```json
{
  ...
  "scripts": {
    ...
    "package-win": "electron-packager . --overwrite --asar --platform=win32 --arch=x64 --icon=icons/icon.ico --prune=true --out=out",
    ...
  },
  ...
}
```

```bat
C:\path\to\app>npm run package-win
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.

> app@1.0.0 package-win
> electron-packager . --overwrite --asar --platform=win32 --arch=x64 --icon=icons/icon.ico --prune=true --out=out

Packaging app for platform win32 x64 using electron v26.2.2
EPERM: operation not permitted, rmdir 'C:\Users\username\AppData\Local\Temp\electron-packager\win32-x64\app-win32-x64-98kJwf\resources\app\images'
```

Asar を有効にすると、Electron Packager でもエラーになる。

### Electron Forge の Asar を無効化

forge.config.js:

```javascript
module.exports = {
  packagerConfig: {
    asar: false,
  },
  ...
};
```

```bat
C:\path\to\app>npm run make
npm WARN config global `--global`, `--local` are deprecated. Use `--location=global` instead.

> app@1.0.0 make
> electron-forge make

✔ Checking your system
✖ Loading configuration
  › The AutoUnpackNatives plugin requires asar to be truthy or an object
◼ Resolving make targets
◼ Running package command
◼ Running preMake hook
◼ Making distributables
◼ Running postMake hook

An unhandled rejection has occurred inside Forge:
Error: The AutoUnpackNatives plugin requires asar to be truthy or an object
at AutoUnpackNativesPlugin.resolveForgeConfig (C:\path\to\app\node_modules\@electron-forge\plugin-auto-unpack-natives\dist\AutoUnpackNativesPlugin.js:14:23)
    at PluginInterface.triggerMutatingHook (C:\path\to\app\node_modules\@electron-forge\core\dist\util\plugin-interface.js:100:41)
    at runMutatingHook (C:\path\to\app\node_modules\@electron-forge\core\dist\util\hook.js:55:40)
    at exports.default (C:\path\to\app\node_modules\@electron-forge\core\dist\util\forge-config.js:161:60)
    at async Task.task (C:\path\to\app\node_modules\@electron-forge\core\dist\api\make.js:67:35)
    at async Task.run (C:\path\to\app\node_modules\listr2\dist\index.cjs:978:11)
    at async C:\path\to\app\node_modules\p-map\index.js:57:22
```

Electron Forge には Asar が必要。
