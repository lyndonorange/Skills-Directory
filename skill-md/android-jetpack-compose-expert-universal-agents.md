---
name: android-jetpack-compose-expert
display_name: android-jetpack-compose-expert
platform: Universal Agents
category: Software engineering and app building
---

# android-jetpack-compose-expert - Universal Agents Skill Package

## What This Is

This is a friend-safe Markdown copy of `android-jetpack-compose-expert` for Universal Agents. It removes local filesystem paths, Finder-only links, and machine-specific source locations.

## When To Use This Skill

Use this skill when your task matches this description:

Build, review, migrate, and optimize production Android apps using Jetpack Compose, Kotlin, Material 3, ViewModel state holders, StateFlow, lifecycle-aware collection, type-safe Navigation Compose, side effects, recompos

## How To Use It In Universal Agents

In tools that read ~/.agents/skills, type: Use the android-jetpack-compose-expert skill to...

## Skill Metadata

| Field | Value |
| --- | --- |
| Display name | `android-jetpack-compose-expert` |
| Canonical name | `android-jetpack-compose-expert` |
| Platform | `Universal Agents` |
| Category | Software engineering and app building |

## Description

Build, review, migrate, and optimize production Android apps using Jetpack Compose, Kotlin, Material 3, ViewModel state holders, StateFlow, lifecycle-aware collection, type-safe Navigation Compose, side effects, recompos


## Original SKILL.md

---
name: android-jetpack-compose-expert
description: Build, review, migrate, and optimize production Android apps using Jetpack Compose, Kotlin, Material 3, ViewModel state holders, StateFlow, lifecycle-aware collection, type-safe Navigation Compose, side effects, recomposition performance, stability annotations, previews, testing, and XML-to-Compose migration. Use when starting Compose projects, adding Compose features, migrating legacy Android XML layouts, designing complex UI state management, debugging recomposition or side effects, setting up type-safe navigation, or reviewing Compose architecture and performance.
---

# Android Jetpack Compose Expert

## Core Rules

Use current project versions and official Android docs before changing Gradle dependencies or version-sensitive APIs. Prefer the Compose BOM for Compose library alignment, and avoid hardcoding stale versions into new projects unless the repository already pins them.

Build Compose screens as a thin screen layer over explicit UI state and events. Do not pass `ViewModel` instances down into leaf composables. Pass immutable state and lambda callbacks.

Use Material 3 components and theme tokens by default. Do not introduce third-party UI frameworks without asking.

## Workflow

1. Identify project shape: Gradle version catalog, Kotlin version, Compose compiler setup, Android Gradle Plugin, min/target SDK, DI framework, and navigation approach.
2. Read the relevant reference files:
   - Setup and Gradle: `references/setup.md`.
   - State, ViewModels, side effects: `references/state-architecture.md`.
   - Navigation Compose: `references/navigation.md`.
   - Performance and stability: `references/performance.md`.
   - XML migration and interoperability: `references/migration.md`.
   - Testing and previews: `references/testing.md`.
3. Implement or review one layer at a time: state model, ViewModel/events, screen composable, stateless content composables, navigation, tests/previews.
4. Verify with the repository's Android checks before claiming success.

## Screen Pattern

Expose screen state from a `ViewModel` and consume it once at the screen boundary.

```kotlin
data class UserUiState(
    val isLoading: Boolean = false,
    val user: User? = null,
    val error: String? = null
)

class UserViewModel(
    private val userRepository: UserRepository
) : ViewModel() {
    private val _uiState = MutableStateFlow(UserUiState())
    val uiState: StateFlow<UserUiState> = _uiState.asStateFlow()

    fun loadUser() {
        viewModelScope.launch {
            _uiState.update { it.copy(isLoading = true, error = null) }
            runCatching { userRepository.getUser() }
                .onSuccess { user ->
                    _uiState.update { it.copy(user = user, isLoading = false) }
                }
                .onFailure { error ->
                    _uiState.update {
                        it.copy(error = error.message, isLoading = false)
                    }
                }
        }
    }
}
```

```kotlin
@Composable
fun UserScreen(
    viewModel: UserViewModel = hiltViewModel()
) {
    val uiState by viewModel.uiState.collectAsStateWithLifecycle()

    UserContent(
        uiState = uiState,
        onRetry = viewModel::loadUser
    )
}

@Composable
fun UserContent(
    uiState: UserUiState,
    onRetry: () -> Unit,
    modifier: Modifier = Modifier
) {
    Scaffold(modifier = modifier) { padding ->
        Box(modifier = Modifier.padding(padding)) {
            when {
                uiState.isLoading -> CircularProgressIndicator()
                uiState.error != null -> ErrorView(uiState.error, onRetry)
                uiState.user != null -> UserProfile(uiState.user)
            }
        }
    }
}
```

## Review Checklist

- Compose dependencies use BOM or an explicit project-approved version strategy.
- `ViewModel` exposes immutable `StateFlow` or equivalent immutable state.
- `collectAsStateWithLifecycle()` is used for Android Flow collection in composables.
- Leaf composables are stateless where practical.
- State is hoisted to the lowest common owner.
- Side effects use `LaunchedEffect`, `DisposableEffect`, `SideEffect`, or ViewModel scope intentionally.
- Type-safe Navigation Compose is preferred for new navigation when dependency versions support it.
- Long lists use lazy containers with stable keys.
- Expensive work is not performed directly in composable bodies without `remember`, `derivedStateOf`, or precomputed state.
- UI state models are stable or immutable enough for efficient recomposition.
- Previews cover meaningful states.
- Accessibility semantics, content descriptions, focus order, font scale, and touch targets are checked.

## Troubleshooting

For infinite recomposition, look for state writes during composition, new object instances that should be remembered, unstable parameters, or effects keyed with changing values.

For state loss after rotation or process recreation, use `rememberSaveable`, `SavedStateHandle`, or persisted state at the correct ownership level.

For navigation crashes, validate route definitions, argument serialization, deep links, and back stack assumptions.

For sluggish lists, check stable item keys, expensive row work, image loading, and unnecessary state reads inside each item.

## Verification

Use the project commands. Common options include:

- `./gradlew test`
- `./gradlew connectedAndroidTest`
- `./gradlew lint`
- `./gradlew assembleDebug`
- `./gradlew :app:compileDebugKotlin`

Run fresh verification before saying builds or tests pass.
