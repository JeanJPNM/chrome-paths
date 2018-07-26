# chrome-paths

[![npm version](https://img.shields.io/npm/v/chrome-paths.svg)](https://www.npmjs.com/package/chrome-paths)
[![Build Status](https://travis-ci.com/shinnn/chrome-paths.svg?branch=master)](https://travis-ci.com/shinnn/chrome-paths)
[![Build status](https://ci.appveyor.com/api/projects/status/fudm5n2n84c1fd4i/branch/master?svg=true)](https://ci.appveyor.com/project/ShinnosukeWatanabe/chrome-paths/branch/master)

Possible paths or binary names of [Chrome](https://www.google.com/chrome/), [Chrome Canary](https://www.google.com/chrome/canary/) and [Chromium](https://www.chromium.org/Home) in the current platform

```javascript
const chromePaths = require('chrome-paths');

// On macOS

chromePaths.chrome; //=> '/Applications/Google Chrome.app/Contents/MacOS/Google Chrome'
chromePaths.chromeCanary; //=> '/Applications/Google Chrome Canary.app/Contents/MacOS/Google Chrome Canary'
chromePaths.chromium; //=> '/Applications/Chromium.app/Contents/MacOS/Chromium'

// On Linux

chromePaths.chrome; //=> 'google-chrome'
chromePaths.chromeCanary; //=> null
chromePaths.chromium; //=> 'chromium-browser'

// On Windows

chromePaths.chrome; //=> 'C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe'
chromePaths.chromeCanary; //=> 'C:\\Program Files (x86)\\Google\\Chrome SxS\\Application\\chrome.exe'
chromePaths.chromium //=> 'C:\\Program Files (x86)\\Chromium\\Application\\chrome.exe'

// On Solaris

chromePaths.chrome; //=> null
chromePaths.chromeCanary; //=> null
chromePaths.chromium; //=> null
```

## Installation

[Use](https://docs.npmjs.com/cli/install) [npm](https://docs.npmjs.com/getting-started/what-is-npm).

```
npm install chrome-paths
```

## API

```javascript
const chromePaths = require('chrome-paths');
```

### chromePaths.chrome, chromePaths.chromeCanary, chromePaths.chromium

Type: `string` or `null`

```javascript
const {execFile} = require('child_process');
const {promisify} = require('util');
const {chrome, chromeCanary} = require('chrome-paths');

(async () => {
  (await promisify(execFile)(chrome, ['--version'])).stdout; //=> 'Google Chrome 68.0.3440.75 \n'
  (await promisify(execFile)(chromeCanary, ['--version'])).stdout; //=> 'Google Chrome 70.0.3502.0 canary\n'
})();
```

Whether each property is a full path, just a binary name or `null` depends on the current [platform](https://nodejs.org/api/process.html#process_process_platform).

## License

[ISC License](./LICENSE) © 2018 Shinnosuke Watanabe