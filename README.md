# DEVember Tutorial
Source:
https://www.youtube.com/@notjustdev
https://github.com/bqfan/DEVember

## Development environment
```
gcl git@github.com:bqfan/DEVember.git
cd DEVember
code .
git fetch upstream
gco day1-end
asdf local java openjdk-21
asdf local nodejs 20.15.0
npx expo install
npm install expo-dev-client 
npx expo-doctor
npm install expo@latest
npx expo install --fix
npx expo-doctor
npm install expo@51
npx expo-doctor
npx expo install --check
npx expo-doctor
npx expo prebuild
eas build --platform android --local
```
## Compile and run your app locally with Expo CLI
Start Android Studio with Virtual Device Manger and open a virtual Android device (e.g., Pixel 3a API 34) or use a real Android phone with USB connection.
```
npx expo run:android
```

## Trouble-shooting
1.
```The field cli.appVersionSource is not set, but it will be required in the future. Learn more```
```You don't have the required permissions to perform this operation.```

```This can sometimes happen if you are logged in as incorrect user.```
```Run eas whoami to check the username you are logged in as.```
```Run eas login to change the account.```

Remove
```
      "eas": {
        "projectId": "ee991416-c2d4-425a-affe-4ea58d9aa6c0"
      }
```
from app.json.

2.
```Execution failed for task ':expo-modules-core:buildCMakeRelWithDebInfo[arm64-v8a]'```

Upgrading NDK to 26.3.11579264 solves the issue
```
      ndkVersion = "26.3.11579264"
```

3.
```The field "cli.appVersionSource" is not set, but it will be required in the future.```
set { "cli": { "appVersionSource": "remote" } } in your eas.json.

4.
```[RUN_GRADLEW] SyntaxError: node_modules/expo-router/entry.js: [BABEL]: expo-router/babel is deprecated in favor of babel-preset-expo in SDK 50. To fix the issue, remove "expo-router/babel" from "plugins" in your babel.config.js file. (While processing: /tmp/bq/eas-build-local-nodejs/0476f03e-c37e-4974-ab03-2f8f38e170d4/build/node_modules/expo-router/babel.js)```

