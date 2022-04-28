# react-native-keyboard-controller

Platform agnostic keyboard manager

## Demonstration

<div>
  <img align="right" width="30%" style="margin-left: 20px" src="./gifs/ios.gif?raw=true">
  <img align="right" width="30%" style="margin-left: 20px" src="./gifs/android.gif?raw=true">
</div>

- mapping keyboard appearance to animated values 😎
- missing `keyboardWillShow`/`keyboardWillHide` events are available on Android 😍
- module for changing soft input mode on Android 🤔
- reanimated support 🚀
- interactive keyboard dismissing (planned) 👆📱
- and more is coming... Stay tuned! 😊
## Installation

The module is not available on `npm`, but you can install it from github.

```sh
yarn add https://github.com/kirillzyusko/react-native-keyboard-controller
```

## Usage

For more comprehensive usage you can have a look on [example](https://github.com/kirillzyusko/react-native-keyboard-controller/tree/main/example).

Below you can see a short overview of library API:

```js
import {
  KeyboardProvider,
  useKeyboardAnimation,
} from 'react-native-keyboard-controller';

// 1. wrap your app in Provider
<KeyboardProvider>
  <AppContainer />
</KeyboardProvider>

// 2. get animation values where you need them
const { height, progress } = useKeyboardAnimation();

// 3. Animate any elements as you wish :)
<Animated.View
  style={{
    width: 50,
    height: 50,
    backgroundColor: 'red',
    borderRadius: 25,
    // the element will move up with the keyboard
    transform: [{ translateY: height }],
  }}
/>
<Animated.View
  style={{
    width: 50,
    height: 50,
    backgroundColor: 'green',
    borderRadius: 25,
    transform: [
      {
        // or use custom interpolation using `progress`
        translateX: progress.interpolate({
          inputRange: [0, 1],
          outputRange: [0, 100],
        }),
      },
    ],
  }}
/>
```

## Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## License

MIT
