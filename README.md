# json_model_mapper

[![pub version](https://img.shields.io/pub/v/json_model_mapper.svg)](https://pub.dev/packages/json_model_mapper)
[![GitHub stars](https://img.shields.io/github/stars/vishalkaklotar/json_model_mapper?style=social)](https://github.com/vishalkaklotar/json_model_mapper)

> A simple annotation package used to mark model classes for code generation.  
> Works with [`json_model_mapper_gen`](https://pub.dev/packages/json_model_mapper_gen) to generate
> clean, immutable Dart data classes automatically.

---

## ✨ Benefits

- ✅ **Annotate any Dart class with `@JsonModelMapper()`** — that's all you need to generate a fully
  usable model.
- ✅ **Say goodbye to `part` files** — no more juggling `.dart` and `.g.dart` for every model.
- ✅ **Cleaner codebase** — you can delete your annotated file once the model is generated.
- ✅ **Custom file naming support** — generated files follow smart patterns like:
    - `user.dart` → `user_model.dart`
    - `some_test.dart` → `some_model_test.dart`
- ✅ **Ready-to-use immutable model class** out-of-the-box.
- ✅ **Easily integrates** with other tools, no conflicts.

---

## 📦 Installation

Add the following to your `pubspec.yaml`:

```yaml
dependencies:
  json_model_mapper: ^0.0.1

dev_dependencies:
  build_runner: latest_version
  json_model_mapper_gen: latest_version
```

---

## 🧪 Example

Step 1: Create a file like `user.dart`

```dart
import 'package:json_model_mapper/json_model_mapper.dart';

@JsonModelMapper()
class User {
  int id;
  String name;
  String role;
  bool isActive;
  String? image;
}
```

Step 2: Run the build command

```
dart run build_runner build

```

> 💡 For more build_runner commands,
> visit [build_runner on pub.dev](https://pub.dev/packages/build_runner)

After the build completes, a new file `user_model.dart` is generated.

- **Generated Output: `user_model.dart`**

```dart
// GENERATED CODE - YOU CAN USE THIS CODE AS YOUR PROJECT CODE
// For issues, report to: product.vishalkaklotar@gmail.com

import 'dart:convert' show JsonEncoder;

class UserModel {
  final int id;
  final String name;
  final String role;
  final bool isActive;
  final String? image;

  const UserModel({
    required this.id,
    required this.name,
    required this.role,
    required this.isActive,
    this.image,
  });

  factory UserModel.fromJson(Map<String, dynamic> json) {
    int id = json['id'];
    String name = json['name'];
    String role = json['role'];
    bool isActive = json['isActive'];
    String? image = json['image'];

    return UserModel(
      id: id,
      name: name,
      role: role,
      isActive: isActive,
      image: image,
    );
  }

  Map<String, dynamic> toMap() {
    return {
      'id': id,
      'name': name,
      'role': role,
      'isActive': isActive,
      'image': image,
    };
  }

  @override
  String toString() => JsonEncoder.withIndent('	').convert(toMap());

  // Modify according requirement
  @override
  bool operator ==(Object other) {
    return identical(this, other) ||
        other is UserModel &&
            runtimeType == other.runtimeType &&
            id == other.id &&
            name == other.name &&
            role == other.role &&
            isActive == other.isActive &&
            image == other.image;
  }

  // Modify according requirement
  @override
  int get hashCode {
    return id.hashCode ^
    name.hashCode ^
    role.hashCode ^
    isActive.hashCode ^
    image.hashCode;
  }
}
```

---

## 🔥 Bonus

After generating the model file, you can even delete your original file ```user.dart```. The output
file is complete and ready to use on its own!
