```
$ yarn prep
$ browserify src/js/index.ts -p [tsify] -o dist/js/bundle.js
[0] /Users/krobinson/Documents/github/google/emoji-scavenger-hunt/node_modules/node-sass/lib/binding.js:13
[0]       throw new Error(errors.unsupportedEnvironment());
[0]       ^
[0]
[0] Error: Node Sass does not yet support your current environment: OS X 64-bit with Unsupported runtime (64)
[0] For more information on which environments are supported please see:
[0] https://github.com/sass/node-sass/releases/tag/v4.7.2
[0]     at module.exports (/Users/krobinson/Documents/github/google/emoji-scavenger-hunt/node_modules/node-sass/lib/binding.js:13:13)
[0]     at Object.<anonymous> (/Users/krobinson/Documents/github/google/emoji-scavenger-hunt/node_modules/node-sass/lib/index.js:14:35)
[0]     at Module._compile (internal/modules/cjs/loader.js:688:30)
[0]     at Object.Module._extensions..js (internal/modules/cjs/loader.js:699:10)
[0]     at Module.load (internal/modules/cjs/loader.js:598:32)
[0]     at tryModuleLoad (internal/modules/cjs/loader.js:537:12)
[0]     at Function.Module._load (internal/modules/cjs/loader.js:529:3)
[0]     at Module.require (internal/modules/cjs/loader.js:636:17)
[0]     at require (internal/modules/cjs/helpers.js:20:18)
[0]     at Object.<anonymous> (/Users/krobinson/Documents/github/google/emoji-scavenger-hunt/node_modules/node-sass/bin/node-sass:10:10)
error Command failed with exit code 1.
```

```
$ npm rebuild node-sass
...
gyp verb node dev dir /Users/krobinson/.node-gyp/10.13.0
gyp verb `which` succeeded for `make` /usr/bin/make
gyp info spawn make
gyp info spawn args [ 'V=1', 'BUILDTYPE=Release', '-C', 'build' ]
sh: line 1: 32233 Abort trap: 6           /Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuild -sdk '' -find make 2> /dev/null
make: error: unable to find utility "make", not a developer tool or in PATH
gyp ERR! build error
gyp ERR! stack Error: `make` failed with exit code: 72
gyp ERR! stack     at ChildProcess.onExit (/Users/krobinson/Documents/github/google/emoji-scavenger-hunt/node_modules/node-gyp/lib/build.js:258:23)
gyp ERR! stack     at ChildProcess.emit (events.js:182:13)
gyp ERR! stack     at Process.ChildProcess._handle.onexit (internal/child_process.js:240:12)
gyp ERR! System Darwin 18.2.0
gyp ERR! command "/usr/local/bin/node" "/Users/krobinson/Documents/github/google/emoji-scavenger-hunt/node_modules/node-gyp/bin/node-gyp.js" "rebuild" "--verbose" "--libsass_ext=" "--libsass_cflags=" "--libsass_ldflags=" "--libsass_library="
gyp ERR! cwd /Users/krobinson/Documents/github/google/emoji-scavenger-hunt/node_modules/node-sass
gyp ERR! node -v v10.13.0
gyp ERR! node-gyp -v v3.6.2
gyp ERR! not ok
Build failed with error code: 1
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! node-sass@4.7.2 postinstall: `node scripts/build.js`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the node-sass@4.7.2 postinstall script.
```

hmm, seems like XCode doesn't work anymore since upgrading to Mojave.
So install it through the OSX App Store and wait...
(hour later, minimal progress, switch directions)

```
$ xcode-select --install
```
then
```
$ xcrun make
$ xcrun make
2019-01-26 13:15:16.068 xcodebuild[33407:1993995] [MT] DVTPlugInLoading: Failed to load code for plug-in com.apple.dt.IDE.DVTKitDFRSupport (/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin), error = Error Domain=NSCocoaErrorDomain Code=3588 "dlopen(/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, 265): Symbol not found: _OBJC_IVAR_$_NSTextViewIvars.sharedData
  Referenced from: /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit
  Expected in: /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit
 in /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit" UserInfo={NSLocalizedFailureReason=The bundle couldn’t be loaded., NSLocalizedRecoverySuggestion=Try reinstalling the bundle., NSFilePath=/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, NSDebugDescription=dlopen(/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, 265): Symbol not found: _OBJC_IVAR_$_NSTextViewIvars.sharedData
  Referenced from: /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit
  Expected in: /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit
 in /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit, NSBundlePath=/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin, NSLocalizedDescription=The bundle “DVTKitDFRSupport” couldn’t be loaded.}, dyldError = dlopen(/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, 0): Symbol not found: _OBJC_IVAR_$_NSTextViewIvars.sharedData
  Referenced from: /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit
  Expected in: /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit
 in /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit
2019-01-26 13:15:16.069 xcodebuild[33407:1993995] [MT] DVTPlugInExtensionFaulting: Failed to fire fault for extension Xcode.DVTKitDFRSupport.Initializer: Error Domain=DVTPlugInErrorDomain Code=2 "Loading a plug-in failed." UserInfo={DVTPlugInIdentifierErrorKey=com.apple.dt.IDE.DVTKitDFRSupport, DVTPlugInExecutablePathErrorKey=/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, NSLocalizedRecoverySuggestion=The plug-in or one of its prerequisite plug-ins may be missing or damaged and may need to be reinstalled., DVTPlugInDYLDErrorMessageErrorKey=dlopen(/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, 0): Symbol not found: _OBJC_IVAR_$_NSTextViewIvars.sharedData
  Referenced from: /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit
  Expected in: /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit
 in /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit, NSLocalizedDescription=Loading a plug-in failed., NSFilePath=/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin, NSLocalizedFailureReason=The plug-in “com.apple.dt.IDE.DVTKitDFRSupport” at path “/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin” could not be loaded.  The plug-in or one of its prerequisite plug-ins may be missing or damaged., NSUnderlyingError=0x7fb88c861500 {Error Domain=NSCocoaErrorDomain Code=3588 "dlopen(/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, 265): Symbol not found: _OBJC_IVAR_$_NSTextViewIvars.sharedData
  Referenced from: /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit
  Expected in: /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit
 in /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit" UserInfo={NSLocalizedFailureReason=The bundle couldn’t be loaded., NSLocalizedRecoverySuggestion=Try reinstalling the bundle., NSFilePath=/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, NSDebugDescription=dlopen(/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin/Contents/MacOS/DVTKitDFRSupport, 265): Symbol not found: _OBJC_IVAR_$_NSTextViewIvars.sharedData
  Referenced from: /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit
  Expected in: /System/Library/Frameworks/AppKit.framework/Versions/C/AppKit
 in /Applications/Xcode.app/Contents/Developer/usr/bin/../../../SharedFrameworks/DVTKit.framework/Versions/A/DVTKit, NSBundlePath=/Applications/Xcode.app/Contents/PlugIns/DVTKitDFRSupport.ideplugin, NSLocalizedDescription=The bundle “DVTKitDFRSupport” couldn’t be loaded.}}}
** INTERNAL ERROR: Uncaught exception **
Uncaught Exception: Error getting value for key 'initializationClass' of extension 'Xcode.DVTKitDFRSupport.Initializer' in plug-in 'com.apple.dt.IDE.DVTKitDFRSupport'
Stack:
  0   __exceptionPreprocess (in CoreFoundation)
  1   objc_exception_throw (in libobjc.A.dylib)
  2   -[DVTExtension valueForKey:error:] (in DVTFoundation)
  3   _IDEInitializeOnePlugInAndPrerequisites (in IDEFoundation)
  4   _IDEInitializePlugIns (in IDEFoundation)
  5   IDEInitialize (in IDEFoundation)
  6   -[Xcode3CommandLineBuildTool run] (in Xcode3Core)
  7  0x000000010a4d9202 (in xcodebuild)
  8   start (in libdyld.dylib)

sh: line 1: 33411 Abort trap: 6           /Applications/Xcode.app/Contents/Developer/usr/bin/xcodebuild -sdk macosx -find make 2> /dev/null
xcrun: error: unable to find utility "make", not a developer tool or in PATH
```

(https://superuser.com/questions/1374651/mac-os-10-14-1-error-getting-value-for-key-initializationclass-of-extension/1376717)

give up, just grab the compiled css from production and dump it in

...


```
$ yarn dev
yarn run v1.13.0
$ concurrently "yarn sass-watch" "yarn js-watch" "yarn dev:server"
$ echo node-sass -w src/sass/main.scss dist/css/main.min.css
$ watchify src/js/index.ts -p [tsify] -o dist/js/bundle.js -v --debug
$ dev_appserver.py --port=3000 app.yaml
[0] node-sass -w src/sass/main.scss dist/css/main.min.css
[2] /bin/sh: dev_appserver.py: command not found
[0] yarn sass-watch exited with code 0
error Command failed with exit code 127.
```

```
(assuming you have added `google-cloud-sdk/bin` to your path)
$ ~/google-cloud-sdk/bin/gcloud init
$ ~/google-cloud-sdk/bin/gcloud components install app-engine-python
```

```
$ yarn dev
$ concurrently "yarn sass-watch" "yarn js-watch" "yarn dev:server"
$ echo node-sass -w src/sass/main.scss dist/css/main.min.css
$ watchify src/js/index.ts -p [tsify] -o dist/js/bundle.js -v --debug
$ dev_appserver.py --port=3000 app.yaml
[0] node-sass -w src/sass/main.scss dist/css/main.min.css
[0] yarn sass-watch exited with code 0
[2] ERROR: Python 3 and later is not compatible with the Google Cloud SDK. Please use Python version 2.7.x.
[2]
[2] If you have a compatible Python interpreter installed, you can use it by setting
[2] the CLOUDSDK_PYTHON environment variable to point to it.
```


```
(i already used conda for python envs)
$ conda create -n emoji-scavenger-hunt python=2.7
$ conda activate -n emoji-scavenger-hunt python=2.7
```
