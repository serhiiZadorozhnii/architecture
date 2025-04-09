# architecture

## Media extentions priority:
1. SVG
2. WEBR

## Folders:
```
project
  lib
    core
      extentions
      theme
      utils
    data
      datastore
      repositories
    domain
      datastore
      repositories
    router
    generated
    presantation
      components
      features
        feature_1
          cubit
          feature_screen
```


#### Feature Structure

Basic feature structure

```
foo/
│
├── bloc/
│   ├── foo_cubit.dart
│   ├── foo_state.dart
│   └── foo_event.dart
│
├── widgets/
│   ├── foo_list_tile.dart
│   └── foo_button.dart
│
└── foo_screen.dart
```

If the feature is complex and contains multiple screens, consider creating a separate folder for each screen.

```
foo/
│
├── list/
│   ├── bloc/
│   │   ├── foo_list_cubit.dart
│   │   ├── foo_list_state.dart
│   │   └── foo_list_event.dart
│   │
│   └── foo_list_screen.dart
│
└── details/
    ├── bloc/
    │   ├── foo_details_cubit.dart
    │   ├── foo_details_state.dart
    │   └── foo_details_event.dart
    │
    └── foo_details_screen.dart

```

#### Feature Screen

- **File name** `<feature_name>_screen.dart`
- **Class name**: `<FeatureName>Screen`
- **Navigation**: 
  - Annotate widget with `@RoutePage`
  - Add new route to `AppRouter`
- **Screen Example**:

## Screen example

```dart
@RoutePage()
class FaqScreen extends StatelessWidget implements AutoRouteWrapper {
  const FaqScreen({super.key});

  static const String path = '/faq';

  @override
  Widget wrappedRoute(BuildContext context) {
    return BlocProvider<FaqCubit>(
      create: (_) => GetIt.I(),
      child: this,
    );
  }

  @override
  Widget build(BuildContext context) {
    final l10n = context.l10n;
    final typography = context.typography;
    final colors = context.colors;
    return Scaffold();
  }
}
```


### Commit Message Rules

We follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) specification for commit messages.


#### Commit types

- **fix**: A bug fix.
- **feat**: A new feature.
- **docs**: Documentation only changes
- **style**: Changes that do not affect the meaning of the code (white-space, formatting, missing semi
- **refactor**: A code change that neither fixes a bug nor adds a feature
- **perf**: A code change that improves performance
- **test**: Adding missing or correcting existing tests
- **build**: Changes that affect the build system or external dependencies
- **ci**: Changes to CI configuration files and scripts (example scopes: GitLabCI)

### Pull Request Rules

- **PR Title**
  ```
  [<type(by conventional commits>)][<issue key>] <Short description>
  ```
  ```
  [feat][TSK-65943] Add two-factor authentication
  ```
- **Description**: Should include a summary of the changes, the reason for the changes, and any relevant information
- **Reviewers**: Assign at least one reviewer
- **Assignees**: Assign yourself to the PR
- **Dependencies**: If the PR depends on another PR, mention it in the description
- **Merge**: Wait for at least one approval before merging
