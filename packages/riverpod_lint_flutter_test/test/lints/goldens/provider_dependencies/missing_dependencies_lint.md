code: provider_dependencies
severity: Severity.warning
message: Unused dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:21:15

```dart

// expect_lint: provider_dependencies
@Dependencies(>>>[dep]<<<)
void depFn() {}

```

=======

code: provider_dependencies
severity: Severity.warning
message: Unused dependencies: depFamily
test/lints/provider_dependencies/missing_dependencies.dart:25:15

```dart

// expect_lint: provider_dependencies
@Dependencies(>>>[depFamily]<<<)
void depFamilyFn() {}

```

=======

code: provider_dependencies
severity: Severity.warning
message: Unused dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:41:15

```dart

// expect_lint: provider_dependencies
@Dependencies(>>>[dep]<<<)
class UnusedDepWidget extends ConsumerWidget {
  const UnusedDepWidget({super.key});
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:80:13

  ```dart
  @riverpod
  int plainAnnotation(Ref ref) {
    ref.watch(>>>depProvider<<<);
    return 0;
  }
  ```
message: Missing dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:78:1

```dart

// expect_lint: provider_dependencies
>>>@riverpod<<<
int plainAnnotation(Ref ref) {
  ref.watch(depProvider);
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:87:13

  ```dart
  @Riverpod(keepAlive: false)
  int customAnnotation(Ref ref) {
    ref.watch(>>>depProvider<<<);
    return 0;
  }
  ```
message: Missing dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:85:1

```dart

// expect_lint: provider_dependencies
>>>@Riverpod(keepAlive: false)<<<
int customAnnotation(Ref ref) {
  ref.watch(depProvider);
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:98:13

  ```dart
    Ref ref,
  ) {
    ref.watch(>>>depProvider<<<);
    return 0;
  }
  ```
message: Missing dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:92:1

```dart

// expect_lint: provider_dependencies
>>>@Riverpod(
  keepAlive: false,
)<<<
int customAnnotationWithTrailingComma(
  Ref ref,
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:108:13

  ```dart
  )
  int existingDep(Ref ref) {
    ref.watch(>>>depProvider<<<);
    return 0;
  }
  ```
message: Missing dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:105:17

```dart
  keepAlive: false,
  // expect_lint: provider_dependencies
  dependencies: >>>[]<<<,
)
int existingDep(Ref ref) {
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:118:13

  ```dart
  )
  int multipleDeps(Ref ref) {
    ref.watch(>>>depProvider<<<);
    ref.watch(dep2Provider);
    return 0;
  ```

  message: dep2
  test/lints/provider_dependencies/missing_dependencies.dart:119:13

  ```dart
  int multipleDeps(Ref ref) {
    ref.watch(depProvider);
    ref.watch(>>>dep2Provider<<<);
    return 0;
  }
  ```
message: Missing dependencies: dep, dep2
test/lints/provider_dependencies/missing_dependencies.dart:115:17

```dart
  keepAlive: false,
  // expect_lint: provider_dependencies
  dependencies: >>>[]<<<,
)
int multipleDeps(Ref ref) {
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:137:12

  ```dart
    @override
    Widget build(BuildContext context, WidgetRef ref) {
      return >>>DepWidget<<<(
        child: ProviderScope(
          overrides: [depProvider.overrideWithValue(42)],
  ```
message: Missing dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:134:1

```dart

// expect_lint: provider_dependencies
>>>class AboveScope extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    return DepWidget(
      child: ProviderScope(
        overrides: [depProvider.overrideWithValue(42)],
        child: Container(),
      ),
    );
  }
}<<<

// expect_lint: provider_dependencies
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:152:32

  ```dart
      return ProviderScope(
        overrides: [depProvider.overrideWithValue(42)],
        child: Text('${ref.watch(>>>depProvider<<<)}'),
      );
    }
  ```
message: Missing dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:147:1

```dart

// expect_lint: provider_dependencies
>>>class Scope2 extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    return ProviderScope(
      overrides: [depProvider.overrideWithValue(42)],
      child: Text('${ref.watch(depProvider)}'),
    );
  }
}<<<

// expect_lint: provider_dependencies
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:168:14

  ```dart
          if (condition) depProvider.overrideWithValue(42),
        ],
        child: >>>DepWidget<<<(),
      );
    }
  ```
message: Missing dependencies: dep
test/lints/provider_dependencies/missing_dependencies.dart:158:1

```dart

// expect_lint: provider_dependencies
>>>class ConditionalScope extends ConsumerWidget {
  ConditionalScope({super.key, required this.condition});
  final bool condition;

  @override
  Widget build(BuildContext context, WidgetRef ref) {
    return ProviderScope(
      overrides: [
        if (condition) depProvider.overrideWithValue(42),
      ],
      child: DepWidget(),
    );
  }
}<<<

class Scope4 extends ConsumerWidget {
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: depFamily
  test/lints/provider_dependencies/missing_dependencies.dart:228:14

  ```dart
      ProviderScope(
        overrides: [depProvider.overrideWith((ref) => 0)],
        child: >>>DepFamily<<<(),
      );
  
  ```

  message: dep
  test/lints/provider_dependencies/missing_dependencies.dart:233:14

  ```dart
      return ProviderScope(
        overrides: [depFamilyProvider.overrideWith((ref, arg) => 0)],
        child: >>>DepWidget<<<(),
      );
    }
  ```
message: Missing dependencies: depFamily, dep
test/lints/provider_dependencies/missing_dependencies.dart:223:1

```dart

// expect_lint: provider_dependencies
>>>class SupportsMultipleScopes2 extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    ProviderScope(
      overrides: [depProvider.overrideWith((ref) => 0)],
      child: DepFamily(),
    );

    return ProviderScope(
      overrides: [depFamilyProvider.overrideWith((ref, arg) => 0)],
      child: DepWidget(),
    );
  }
}<<<

class SupportsNestedScopes extends ConsumerWidget {
```

=======

code: provider_dependencies
severity: Severity.warning
contextMessages:
  message: depFamily
  test/lints/provider_dependencies/missing_dependencies.dart:259:14

  ```dart
      return ProviderScope(
        overrides: [depFamilyProvider(42).overrideWith((ref) => 0)],
        child: >>>DepFamily<<<(),
      );
    }
  ```
message: Missing dependencies: depFamily
test/lints/provider_dependencies/missing_dependencies.dart:254:1

```dart

// expect_lint: provider_dependencies
>>>class IncompleteFamilyOverride extends ConsumerWidget {
  @override
  Widget build(BuildContext context, WidgetRef ref) {
    return ProviderScope(
      overrides: [depFamilyProvider(42).overrideWith((ref) => 0)],
      child: DepFamily(),
    );
  }
}<<<

@Dependencies([dep])
```
