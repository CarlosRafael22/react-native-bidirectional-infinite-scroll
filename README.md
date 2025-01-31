# 📜 React Native Bi-directional Infinite Scroll

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/GetStream/react-native-bidirectional-infinite-scroll/blob/main/LICENSE)
[![Npm Package](https://img.shields.io/badge/npm--package-v0.1.0-blue)](https://www.npmjs.com/package/react-native-bidirectional-infinite-scroll)
[![Compatibility](https://img.shields.io/badge/react--native%20--%20android%20%7C%20iOS-compatible-brightgreen)](https://reactnative.dev/)

**[** Built with ♥ at [Stream](https://getstream.io/) **]**

[FlatList](https://reactnative.dev/docs/flatlist) by react-native only allows infinite scroll in one direction (using `onEndReached`). This package adds capability on top of FlatList to allow infinite scroll from both directions, and also maintains **smooth scroll** UX.

**Features**

- Accepts prop `onStartReached` & `onEndReached`, which you can use to load more results. 
- Calls to onEndReached and onStartReached have been optimized.
- Inline loading Indicators, which can be customized as well.
- Uses [flat-list-mvcp](https://github.com/GetStream/flat-list-mvcp#maintainvisiblecontentposition-prop-support-for-android-react-native) to maintain scroll position or smooth scroll UX.


<table>
  <tr>
    <td align='center' width="33%"><img src='https://user-images.githubusercontent.com/11586388/108675127-a5545680-74e6-11eb-89f9-b617b5ce6cc6.gif'/></td>
    <td align='center' width="33%"><img src='https://user-images.githubusercontent.com/11586388/108675105-9ff70c00-74e6-11eb-8abf-7c07b79338e2.gif'/></td>
  </tr>
  <tr></tr>
  <tr>
    <td align='center'>
        <strong>iOS</strong>
    </td>
    <td align='center'>
        <strong>Android</strong>
    </td>
  </tr>
</table>

## 🛠 Installation

```sh
yarn add react-native-bidirectional-infinite-scroll @stream-io/flat-list-mvcp
```

## 🔮 Usage

Please check the [example app](https://github.com/GetStream/react-native-bidirectional-infinite-scroll/tree/main/example) for working demo.

```jsx
import { FlatList } from "react-native-bidirectional-infinite-scroll";

<FlatList
    data={numbers}
    renderItem={ListItem}
    keyExtractor={(item) => item.toString()}
    onStartReached={onStartReached} // required, should return a promise
    onEndReached={onEndReached} // required, should return a promise
    showDefaultLoadingIndicators={true} // optional
    onStartReachedThreshold={10} // optional
    onEndReachedThreshold={10} // optional
    activityIndicatorColor={'black'} // optional
    HeaderLoadingIndicator={() => { /** Your loading indicator */ }} // optional
    FooterLoadingIndicator={() => { /** Your loading indicator */ }} // optional
    // You can use any other prop on react-native's FlatList
/>

```

**Note**:
- `onEndReached` and `onStartReached` only get called once, per content length.
- `onEndReached` and `onStartReached` must return a promise.
- `maintainVisibleContentPosition` is fixed, and can't be modified through props.
- doesn't accept `ListFooterComponent` via prop, since it is occupied by `FooterLoadingIndicator`


## ✍ Contributing

See the [contributing guide](CONTRIBUTING.md) to learn how to contribute to the repository and the development workflow.

## 🎗 License

MIT
