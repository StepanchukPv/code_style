

## <span style="background: #9ACD32; color:white">[WCA]</span> - Widget Constructor Arguments
1. ### Attributes in widgets <span style="color:red">[Required]</span>
    Attributes in widget classes should be placed ***AFTER*** constructor.

    It is common practice borrowed from Flutter docs

     #### BAD:
    ```dart
    class ExampleWidget extends StatelessWidget {
        final String title;
        final TextStyle style;
        final VoidCallback? onTap;

        const ExampleWidget({
            super.key,
            required this.title,
            required this.style,
            this.onTap,
        });

        @override
        Widget build(...)
    }
    ```

    #### GOOD:
    ```dart
    class ExampleWidget extends StatelessWidget {
        const ExampleWidget({
            super.key,
            required this.title,
            required this.style,
            this.onTap,
        });

        final String title;
        final TextStyle style;
        final VoidCallback? onTap;

        @override
        Widget build(...)
    }
    ```



2. ### Callbacks location <span style="color:blue">[Optional]</span> 
    Callbacks should be placed ***IN THE END*** of attributes annotation and be ***separated*** with blank space.


    #### BAD:
    ```dart
    class Example extends StatelessWidget {
        const Example({
            super.key,
            required this.title,
            required this.onTap,
            required this.decoration,
            required this.itemBuilder,
        });

        final String title;
        final VoidCallback onTap;
        final BoxDecoration decoration;
        final void Function(BuildContext, int) itemBuilder;

        @override
        Widget build(...)
    }
    ```

    #### GOOD:
    ```dart
    class Example extends StatelessWidget {
        const Example({
            super.key,
            required this.title,
            required this.decoration,
            required this.onTap,
            required this.itemBuilder,
        });

        final String title;
        final BoxDecoration decoration;

        final VoidCallback onTap;
        final void Function(BuildContext, int) itemBuilder;

        @override
        Widget build(...)
    }
    ```
3. ### Required attributes location <span style="color:blue">[Optional]</span> 
    Required attributes should be placed at the beginning of the constructor.

    #### BAD:
    ```dart
    class Example extends StatelessWidget {
        const Example({
            super.key,
            this.caption,
            required this.title,
            required this.someLongField,
        });

        final String title;
        final String? caption;
        final String someLongField;

        @override
        Widget build(...)
    }
    ```

    #### GOOD:
    ```dart
    class Example extends StatelessWidget {
        const Example({
            super.key,
            required this.title,
            required this.someLongField,
            this.caption,
        });

        final String title;
        final String? caption;
        final String someLongField;

        @override
        Widget build(...)
    }
    ```

