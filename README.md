# Gift Grab UI

A Flutter package with the shared theme, form inputs and widgets for the Gift Grab game's menus and social screens. It keeps the look of the game client consistent: a blue and orange Material theme, Formz-validated inputs, Lottie-animated menu buttons and empty states, and a scaffold with the game's background art.

## What's included

Everything is exported from `package:gift_grab_ui/ui.dart`.

- **Theme** (`lib/config/gift_grab_theme.dart`): `GiftGrabTheme.lightTheme` and `GiftGrabTheme.darkTheme`, with a blue 900 primary, orange 700 secondary, the Montserrat font family and a full text theme.
- **Formz inputs** (`lib/formz_inputs/`), each a `FormzInput` model plus a matching widget:

  | Input | Model | Widget | Rules |
  | --- | --- | --- | --- |
  | Short text | `ShortText` | `ShortTextInput` | required, 6 to 20 characters |
  | Long text | `LongText` | `LongTextInput` | required, 10 to 100 characters, 2 to 3 lines |
  | Range | `Range` | `RangeInput` (slider) | integer from 2 to 10 |
  | Toggle | `Toggle` | `ToggleInput` (switch tile) | none |

- **Widgets** (`lib/widgets/`):
  - `GGScaffoldWidget`: an app bar with a title, optional actions and back control, over the background image.
  - `MenuButtonWidget` with the `MenuButton` enum: Chat Rooms, Friends, Edit Profile, Groups, Leaderboard, Notifications, Play, Profile, Users and Tournaments, each with its own Lottie animation.
  - `NoResultsWidget` with the `NoResultsEnum` empty states (no chat rooms, friends, invites, requests, groups, tournaments, notifications, leaderboard entries or users).
  - `FlexGridviewWidget`: a grid that picks its column count from the screen width.
- **Lottie URLs** (`lib/constants/lotties.dart`): the hosted animations the buttons and empty states use.

## Usage

Add it as a git or path dependency (it isn't published to pub.dev):

```yaml
dependencies:
  gift_grab_ui:
    git:
      url: https://github.com/trey-a-hope/gift_grab_ui
```

```dart
import 'package:gift_grab_ui/ui.dart';

MaterialApp(
  theme: GiftGrabTheme.lightTheme,
  darkTheme: GiftGrabTheme.darkTheme,
  home: GGScaffoldWidget(
    title: 'Menu',
    child: FlexGridviewWidget(
      children: [
        MenuButtonWidget(menuButton: MenuButton.play, onTap: () {}),
        MenuButtonWidget(menuButton: MenuButton.leaderboard, onTap: () {}),
      ],
    ),
  ),
);
```

## Notes

- `GGScaffoldWidget` loads `assets/images/background-sprite.jpg` without a package prefix, and the package's `pubspec.yaml` doesn't declare that asset or bundle the Montserrat font, so the app using this package needs to provide both.
- The animations load from lottie.host at runtime, so they need a network connection.
- Requires Dart SDK `^3.8.1`. Dependencies: `formz`, `gap`, `lottie`.
- `test/gift_grab_ui_test.dart` is still the commented-out template test.

## Related

- [gift_grab_game](https://github.com/trey-a-hope/gift_grab_game) and [gift_grab_client](https://github.com/trey-a-hope/gift_grab_client)
