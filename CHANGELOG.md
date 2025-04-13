## 0.0.1

- 🎉 Initial release of `json_model_mapper`.
- Add `@JsonModelMapper()` annotation to mark Dart classes for model generation.
- Generate full model files like `user_model.dart` without `.g.dart` and `part` usage.
- Support smart naming convention:
    - `user.dart` ➝ `user_model.dart`
- Add support for nullable types and primitive types.
- Add support for basic custom class recognition (if also annotated).
- Include utility methods in generated model:
    - `fromJson`
    - `toMap`
    - `toString`, `==`, `hashCode`
- Add header to all generated files:
  ```dart
  // GENERATED CODE - YOU CAN USE THIS CODE AS YOUR PROJECT CODE
  // For issues, report to: example@gmail.com
