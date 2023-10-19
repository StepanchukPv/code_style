

## <span style="background: #9ACD32; color:white">[IS]</span> - Imports Styles
1. ### Sort Imports <span style="color:red">[Required]</span>
    It's a GOOD: practice to sort imports for several reasons: ***Readability and Consistency, Avoiding Conflicts, Easier Maintenance, Helpful for Version Control***

    **Usage** - Sort import after each PR using:

        dart run import_sorter:main 
    
    #### BAD:
    ```dart
    import 'package:flutter/material.dart';
    import 'package:some_package/some_module.dart';
    import 'package:another_package/another_module.dart';
    import 'package:flutter/scheduler.dart';
    import 'package:flutter/services.dart';
    import 'dart:convert';
    ```

    #### GOOD:
    ```dart
    import 'dart:convert';

    import 'package:flutter/material.dart';
    import 'package:flutter/services.dart';
    import 'package:flutter/scheduler.dart';

    import 'package:another_package/another_module.dart';
    import 'package:some_package/some_module.dart';
    ```


2. ### Creating indexes <span style="color:red">[Required]</span>
    Creating indexes for imports enhance code organization, improve maintainability, reduce redundancy

    **Usage** - Create the *index.dart* file where the necessary files will be exported. Use this file to reduce imports amount

    Example of index.dart
    ```dart
    export 'opacity_card.dart';
    export 'custom_section.dart';
    export 'slidable_action.dart';
    ```

     #### BAD:
    ```dart
    import 'package:flutter/material.dart';

    import 'widgets/opacity_card.dart';
    import 'widgets/custom_section.dart';
    import 'widgets/slidable_action.dart';

    //Some other imports

    ```

    #### GOOD:
    ```dart
    import 'package:flutter/material.dart';

    import 'widgets/index.dart';
    // Some other imports
    
    ```



3. ### Use full import path <span style="color:blue">[Optional]</span> 
   Including the full import path makes it clear and explicit where the imported module or component is coming from. It leaves no ambiguity about the source of the imported functionality.

   In a larger project, there might be modules or components with similar names in different packages. Using the full import path helps avoid potential naming conflicts or ambiguities by specifying the exact source of the import.

    #### BAD:
    ```dart
    import '../../../extensions.dart';
    ```

    #### GOOD:
    ```dart
    import 'package:project/widgets/helpers/extensions.dart';
    ```
