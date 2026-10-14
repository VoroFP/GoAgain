# GoAgain

My Android learning lab: recreating real-app features as reusable feature modules, following current Android architecture guidance.

> 🚧 **Work in progress.** The project is being set up; the module structure below is the target, not the current state.

## Goals

- **Learn by rebuilding**: pick features from well-known apps and recreate them from scratch.
- **Portable features**: each feature is a self-contained module that can be dropped into another project with minimal wiring.
- **Many entry points**: features are reachable through in-app navigation, deep links and, later, shortcuts, widgets and notifications.

## Tech stack

- **Kotlin**, **Jetpack Compose** with **Material 3**
- **MVVM** with `StateFlow` and lifecycle-aware collection
- **Clean Architecture** (`domain`, `data`, `presentation`) inside each feature
- **Hilt** for dependency injection
- **Navigation 3** with type-safe keys, plus deep links
- **Coroutines** and **Flow**
- **Gradle Kotlin DSL**, version catalog and convention plugins
- **GitHub Actions** for CI

## Architecture (planned)

```
:app                   composition root: wires every feature together
:feature:<name>:api    navigation keys and public contracts only
:feature:<name>:impl   domain, data and presentation for the feature
:core:designsystem     theme and reusable UI components
:core:navigation       shared navigation contracts
:core:testing          shared test helpers
build-logic            convention plugins (shared build config)
```

Dependency rules:

- `impl` modules never depend on other `impl` modules; features talk only through `api` modules.
- `core` modules never depend on features.
- Only `:app` knows about every feature.

## Getting started

Requirements: Android Studio (latest stable) and JDK 25. Android Studio's bundled JDK works.

```
git clone https://github.com/VoroFP/GoAgain.git
cd GoAgain
./gradlew assembleDebug
```

## License

Copyright 2026 Voro Ferrer Peris

Licensed under the [Apache License, Version 2.0](LICENSE).
