# NumberPad

[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)

## Features
- [x] Return button
- [x] Optional buttons (plus, dot)
- [x] Long press support for delete key
- [x] [Custom styles](#use-custom-style)
- [x] Improve InputControlller (ask delegate aboult shouldChangeCharactersInRange)
- [ ] System slyles (light, dark) + vibrancy
- [ ] iOS 11 PhonePad keyboard style
- [ ] Appearance from `UIInputTraits.keyboardAppearance`

## Usage

### Standard `InputController`

```swift
let textField = UITextField(frame: .zero)

...
textField.inputView = NumberPad(optionalKey: .dot)
    .with(styleFrom: textField)
    .withStandardInputController()
```

### Custom `InputController`
You can provide Your own keyboard behaviour by implementing `InputConroller` protocol

```swift
// custom conroller for keyboard events
class MyInputController: InputController {
   ...
}

let pad = NumberPad()
    .with(inputController: MyInputController())
```

Or use closures directly:

```swift
let pad = NumberPad(optionalKey: .plus)
    .onTextInput { (symbol) in
        // proccess symbol input
    }.onReturn {
        // proccess action button
    }.onBackspace {
        // proccess backspace button
    }
```

### Use custom style
Default implementation of  `KeyboardStyle` represents default style.

```swift
// define your own custom style
struct MyCustomStyle: KeyboardStyle {
...
}

let pad = NumberPad(optionalKey: .dot)
    .with(style: MyCustomStyle())
```

## Requirements

- Swift 3.2+
- xCode 9+
- iOS 8.0+

## Installation

### Carthage

[Carthage](https://github.com/Carthage/Carthage) is a decentralized dependency manager that builds your dependencies and provides you with binary frameworks.

You can install Carthage with [Homebrew](http://brew.sh/) using the following command:

```bash
$ brew update
$ brew install carthage
```
To integrate NumberPad into your Xcode project using Carthage, specify it in your `Cartfile`:

```ogdl
github "OlegKetrar/NumberPad"
```
Run `carthage update` to build the framework and drag the built `NumberPad.framework` into your Xcode project.

## License

NumberPad is released under the MIT license. [See LICENSE](LICENSE.md) for details.
