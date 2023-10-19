

## <span style="background: #9ACD32; color:white">[DCA]</span> - Data Constructor Arguments
1. ### Attributes in data-classes <span style="color:red">[Required]</span>
    Attributes in data or BLoC classes should be placed ***BEFORE*** constructor.

    By placing attributes ***at the top*** of the data-class definition, you can easily see and manage the data members of the class. This can help you keep track of the state of the object and maintain code organization.

   
    
    #### BAD:
    ```dart
    class Model {
        Model({
            required this.id,
            required this.title,
            required this.description,
        });

        final int id;
        final String title;
        final String description;
    }
    ```

    #### GOOD:
    ```dart
    class Model {
        final int id;
        final String title;
        final String description;

        Model({
            required this.id,
            required this.title,
            required this.description,
        });
    }
    ```

2. ### Creating models with Freezed <span style="color:red">[Required]</span>
    - Instead of key word 'required' user '@Default(defaultValue)'. 
    - Use '@Default(defaultValue)' for optional parameters, in case logic for default value behave the same as null-value.

    This is useful for creating default values, payloads and omitting to use redundant null-safety  

    
    #### BAD:
    ```dart
    @freezed
    class ExampleModel with _$ExampleModel {
        const factory ExampleModel({
            required int id,
            required String name,
            bool? isCompleted,
            int? assignedTo,
        }) = _ExampleModel;

        factory ExampleModel.fromJson(Map<String, dynamic> json) =>
            _$ExampleModelFromJson(json);
    }
    ```

    #### GOOD:
    ```dart
    @freezed
    class ExampleModel with _$ExampleModel {
        const factory ExampleModel({
            @Default(0) int id,
            @Default('') String name,
            @Default(false) bool isCompleted,
            int? assignedTo,
        }) = _ExampleModel;

        factory ExampleModel.fromJson(Map<String, dynamic> json) =>
            _$ExampleModelFromJson(json);
    }
    ```

