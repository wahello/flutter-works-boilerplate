# Flutter Works

[![KodingWorks][logo]][kodingworks_link]

Developed with 💙 by [KodingWorks][kodingworks_link] 🦄

[![Language][dart_language_badge]](http://dart.dev)
[![Flutter Works][github_action_badge]][github_action_workflow_link]
[![Codecov][codecov_badge]][codecov_link]
[![style: very good analysis][very_good_analysis_badge]][very_good_analysis_link]
[![License: MIT][license_badge]][license_link]
[![PRs Welcome][pr_welcome_badge]][repo_link]
[![Stars][stars_badge]][repo_link]
[![Stars][issues_badge]][repo_link]
[![Stars][pull_request_badge]][repo_link]

A FlutterWorks Flutter Starter Project created by the [KodingWorks Team][kodingworks_link].

---

## Getting Started 🚀

This project contains 3 flavors:

- development
- staging
- production

To run the desired flavor either use the launch configuration in VSCode/Android Studio or use the following commands:

```sh
# Development
$ flutter run --flavor development --target lib/main_development.dart

# Staging
$ flutter run --flavor staging --target lib/main_staging.dart

# Production
$ flutter run --flavor production --target lib/main_production.dart
```

_\*Flutter Works works on iOS, Android, and Web._

---

## Running Tests 🧪

To run all unit and widget tests use the following command:

```sh
$ flutter test --coverage --test-randomize-ordering-seed random
```

To view the generated coverage report you can use [lcov](https://github.com/linux-test-project/lcov).

```sh
# Generate Coverage Report
$ genhtml coverage/lcov.info -o coverage/

# Open Coverage Report
$ open coverage/index.html
```

---

## Working with Translations 🌐

This project relies on [flutter_localizations][flutter_localizations_link] and follows the [official internationalization guide for Flutter][internationalization_link].

### Adding Strings

1. To add a new localizable string, open the `app_en.arb` file at `lib/l10n/arb/app_en.arb`.

```arb
{
    "@@locale": "en",
    "counterAppBarTitle": "Counter",
    "@counterAppBarTitle": {
        "description": "Text shown in the AppBar of the Counter Page"
    }
}
```

2. Then add a new key/value and description

```arb
{
    "@@locale": "en",
    "counterAppBarTitle": "Counter",
    "@counterAppBarTitle": {
        "description": "Text shown in the AppBar of the Counter Page"
    },
    "helloWorld": "Hello World",
    "@helloWorld": {
        "description": "Hello World Text"
    }
}
```

3. Use the new string

```dart
import 'package:flutter_works/l10n/l10n.dart';

@override
Widget build(BuildContext context) {
  final l10n = context.l10n;
  return Text(l10n.helloWorld);
}
```

### Adding Supported Locales

Update the `CFBundleLocalizations` array in the `Info.plist` at `ios/Runner/Info.plist` to include the new locale.

```xml
    ...

    <key>CFBundleLocalizations</key>
	<array>
		<string>en</string>
		<string>es</string>
	</array>

    ...
```

### Adding Translations

1. For each supported locale, add a new ARB file in `lib/l10n/arb`.

```
├── l10n
│   ├── arb
│   │   ├── app_en.arb
│   │   └── app_es.arb
```

2. Add the translated strings to each `.arb` file:

`app_en.arb`

```arb
{
    "@@locale": "en",
    "counterAppBarTitle": "Counter",
    "@counterAppBarTitle": {
        "description": "Text shown in the AppBar of the Counter Page"
    }
}
```

`app_es.arb`

```arb
{
    "@@locale": "es",
    "counterAppBarTitle": "Contador",
    "@counterAppBarTitle": {
        "description": "Texto mostrado en la AppBar de la página del contador"
    }
}
```


## Working with Route Navigation 🧭

### Now run the generator

```bash
flutter packages pub run build_runner watch
```

We use the watch flag to watch for file changes which will rebuild the generated files when necessary. If you would like to only generate files once and exit after use:

```bash
flutter packages pub run build_runner build
```

When generating route encountered this error:

```
[SEVERE] Conflicting outputs were detected and the build is unable to prompt for permission to remove them. These outputs must be removed manually or the build can be run with `--delete-conflicting-outputs`. The outputs are: lib/app/routes.gr.dart
```

You must add `--delete-conflicting-outputs` when generating, Ex:

```bash
flutter packages pub run build_runner build --delete-conflicting-outputs
```

> More info: https://autoroute.vercel.app/

[flutter_localizations_link]: https://api.flutter.dev/flutter/flutter_localizations/flutter_localizations-library.html
[internationalization_link]: https://flutter.dev/docs/development/accessibility-and-localization/internationalization
[license_badge]: https://img.shields.io/badge/license-MIT-blue.svg
[license_link]: https://opensource.org/licenses/MIT
[logo]: https://avatars.githubusercontent.com/u/57176505?s=200&v=4
[very_good_analysis_badge]: https://img.shields.io/badge/style-very_good_analysis-B22C89.svg
[very_good_analysis_link]: https://pub.dev/packages/very_good_analysis
[very_good_cli_link]: https://github.com/VeryGoodOpenSource/very_good_cli
[kodingworks_link]: https://kodingworks.io
[codecov_badge]: https://codecov.io/gh/kodingworks/flutter-works-boilerplate/branch/main/graph/badge.svg
[codecov_link]: https://codecov.io/gh/kodingworks/flutter-works-boilerplate
[repo_link]: https://github.com/kodingworks/flutter-works-boilerplate
[github_action_badge]: https://github.com/kodingworks/flutter-works-boilerplate/actions/workflows/main.yaml/badge.svg
[github_action_workflow_link]: https://github.com/kodingworks/flutter-works-boilerplate/actions/workflows/main.yaml
[stars_badge]: https://img.shields.io/github/stars/kodingworks/flutter-works-boilerplate.svg?style=flat&logo=github&colorB=deeppink&label=Stars
[issues_badge]: https://img.shields.io/github/issues/kodingworks/flutter-works-boilerplate.svg?style=flat&logo=github&colorB=orange&label=Issues
[pull_request_badge]: https://img.shields.io/github/issues-pr/kodingworks/flutter-works-boilerplate.svg?style=flat&logo=github&colorB=brightgreen&label=Pull+Request
[dart_language_badge]: https://img.shields.io/badge/Language-Dart-blue
[pr_welcome_badge]: https://img.shields.io/badge/PRs-welcome-brightgreen.svg