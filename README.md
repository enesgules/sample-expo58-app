# Expo 58 sample

An Expo SDK 58 app generated from `expo-template-default@58.0.22`, using npm,
Expo Router, and React Native 0.88. The native projects are generated during
builds and are not committed.

Both platforms use the app identifier `com.limrun.sampleexpo58`.

## Development

```sh
npm ci
npx expo start --dev-client
```

The app includes `expo-dev-client`. Install a development build before connecting
to Metro. The Home and Explore tabs exercise navigation, native UI, images,
and animations from the Expo starter app.

## Build with Limrun

Install the [Limrun CLI](https://docs.limrun.com) and sign in with `lim login`.
Run these commands from this repository.

### iOS

```sh
lim xcode build . --configuration Release --upload sample-expo58-app/ios-release.zip
lim ios create --attach
```

The Release build includes the JavaScript bundle and runs without Metro. For a
development build, use `--configuration Debug` and follow the
[Expo development workflow](https://docs.limrun.com/docs/ios/build-with-xcode).

### Android

```sh
lim gradle build . --upload sample-expo58-app/android-debug.apk
lim android create --install-asset sample-expo58-app/android-debug.apk --no-connect
```

The default Debug build connects to Metro. After the emulator is ready, use its
instance ID to tunnel Metro through Limrun:

```sh
lim android tunnel --id <android-instance-id> --selector localhost:8081 --no-inspect --detach
EXPO_PACKAGER_PROXY_URL=http://127.0.0.1:8081 npx expo start --dev-client --port 8081
```

In another terminal, open the development client:

```sh
lim android open-url 'sampleexpo58app://expo-development-client/?url=http%3A%2F%2F127.0.0.1%3A8081' --id <android-instance-id>
```

On the first launch, tap Continue and close the developer menu. When finished,
stop Metro and delete the emulator with `lim android delete <android-instance-id>`.

## Checks

```sh
npx expo install --check
npx tsc --noEmit
```
