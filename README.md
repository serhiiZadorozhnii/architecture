# architecture

## Media extentions priority:
1. SVG
2. WEBR

## Folders:

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


## Screen example

```
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
