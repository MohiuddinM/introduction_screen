# IntroductionScreen [![pub package](https://img.shields.io/pub/v/introduction_screen.svg)](https://pub.dartlang.org/packages/introduction_screen)

Introduction screen allow you to have a screen at launcher for example, where you can explain your app.
This Widget is customizable (more in the future) with a great design.

Introduction_screen use another package, [dots_indicator](https://github.com/Pyozer/dots_indicator), that I also created.

## Installation

You just need to add `introduction_screen` as a [dependency in your pubspec.yaml file](https://flutter.io/using-packages/).

```yaml
dependencies:
  introduction_screen: ^0.0.5
```

## Example

In these example, `listPagesViewModel` is the **list of pages**. A page is base on PageViewModel. See example of a PageViewModel below.

## PageViewModel

### Simple page

This example only define title, body and an image (you can define any widget)

```dart
new PageViewModel(
  "Title of first page",
  "Here you can write the description of the page, to explain someting...",
  Image.network("https://domaine.com/image.png", height: 175.0),
)
```

### Page with custom colors

This example show you how to define the color of the page (background but also the dot indicator color)

```dart
new PageViewModel(
  "Title of first page",
  "Here you can write the description of the page, to explain someting...",
  Image.asset("res/images/logo.png", height: 175.0),
  pageColor: Colors.blue,
  progressColor: Colors.red,
)
```

### Page with custom text style

This example show you how to define another TextStyle for the title and the body

```dart
new PageViewModel(
  "Title of first page",
  "Here you can write the description of the page, to explain someting...",
  const Icon(Icons.android),
  titleTextStyle: const TextStyle(color: Colors.orange),
  bodyTextStyle: const TextStyle(fontWeight: FontWeight.w700, fontSize: 20.0),
)
```

### Page with a footer, like a button

This example show you how to define a page with a footer, like a Button

```dart
new PageViewModel(
  "Title of first page",
  "Here you can write the description of the page, to explain someting...",
  const Icon(Icons.android),
  footer: RaisedButton(
    onPressed: () {
      // On button presed
    },
    child: const Text("Let's Go !"),
  ),
);
```

## IntroductionScreen

**Note :**

If you not provide `next` parameter, the Next button will be not displayed.
If you want to display a skip button, you must add `skip` parameter and `showSkipButton: true`
The `done` parameter is required.

### Simple intro screen

Simple intro screen

![Base intro](https://raw.githubusercontent.com/Pyozer/introduction_screen/master/demo/normal.gif)

```dart
new IntroductionScreen(
  pages: listPagesViewModel,
  done: const Text("Done", style: TextStyle(fontWeight: FontWeight.w600))
  onDone: () {
    // When done button is press
  },
); //Material App
```

### Intro screen with skip button

![With skip button](https://raw.githubusercontent.com/Pyozer/introduction_screen/master/demo/skip.gif)

```dart
new IntroductionScreen(
  pages: listPagesViewModel,
  onDone: () {
    // When done button is press
  },
  showSkipButton: true,
  skip: const Text("Skip"),
  done: const Text("Done", style: TextStyle(fontWeight: FontWeight.w600)),
);
```

### Intro screen with custom button text

![Custom button text](https://raw.githubusercontent.com/Pyozer/introduction_screen/master/demo/custom_buttons.gif)

```dart
new IntroductionScreen(
  pages: listPagesViewModel,
  onDone: () {
    // When done button is press
  },
  showSkipButton: true,
  skip: const Icon(Icons.skip_next),
  next: const Icon(Icons.next),
  done: const Text("Done", style: TextStyle(fontWeight: FontWeight.w600))
);
```

### Others parameters

There is other possibles parameters that you can add :

- Freeze the scroll, by adding `freeze: true` parameter.
- Duration of scrolling animation, by adding `animationDuration: 400` parameter.
- Initial page, by adding `initialPage: 1` parameter.