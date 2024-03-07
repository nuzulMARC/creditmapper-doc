## Module: FatalErrorException.php
### Module Name
The module is identified as `FatalErrorException.php`.

### Primary Objectives
Its primary purpose is to define a custom exception type for handling fatal errors within the Psy Shell environment, enhancing error reporting and handling capabilities.

### Critical Functions
- **__construct**: This is the constructor method for creating a new instance of `FatalErrorException`. It initializes the exception with a message, error code, severity level, filename, line number, and an optional previous exception for chaining.
- **getRawMessage**: Returns the raw, unformatted version of the error message.

### Key Variables
- **$rawMessage**: Holds the original, unformatted error message passed to the exception.

### Interdependencies
This class extends `ErrorException`, indicating it relies on PHP's standard error exception handling mechanisms. It also interacts with PHP's `\Throwable` interface for exception chaining, allowing it to work seamlessly within PHP's exception handling system.

### Core vs. Auxiliary Operations
- **Core Operations**: The core functionality revolves around the creation and handling of fatal error exceptions, primarily through its constructor and the retrieval of raw error messages.
- **Auxiliary Operations**: Formatting the error message for better readability and integration with Psy Shell's overall error handling framework.

### Operational Sequence
1. An instance of `FatalErrorException` is created when a fatal error is encountered.
2. The constructor formats the error message, incorporating the file name and line number, and initializes the exception.
3. The raw error message can be retrieved using `getRawMessage`, potentially for logging or display purposes without the formatted additions.

### Performance Aspects
Performance considerations include the efficient handling of fatal errors without significantly impacting the runtime performance. The class should be lightweight, focusing on essential error information processing and propagation.

### Reusability
The design of `FatalErrorException` allows it to be reused in any PHP project that requires refined fatal error handling, particularly those using the Psy Shell or similar interactive debugging environments.

### Usage
It is used within the Psy Shell to represent and handle fatal errors, providing a structured and informative way to report such errors to the user. It enhances the shell's robustness by allowing developers to catch and respond to fatal errors gracefully.

### Assumptions
- The module assumes that fatal errors will be caught and handled explicitly, which requires PHP's error handling to be set up in a way that allows exceptions to be thrown for errors.
- It assumes the presence of a running Psy Shell environment or a similar context where detailed error reporting and handling are necessary.
- The use of `-1` for line numbers is treated as `null`, indicating an assumption that certain errors may not be associated with a specific line in a script or are evaluated code.
## Flow Diagram [via mermaid]
```mermaid
flowchart TB
    start([Start]) -->|Create FatalErrorException| constructFatalErrorException[FatalErrorException Constructor]
    constructFatalErrorException -->|Set rawMessage| setRawMessage[Set rawMessage]
    constructFatalErrorException -->|Format message| formatMessage[Format Error Message]
    formatMessage -->|Call parent::__construct| callParentConstructor[Call Parent Constructor]
    setRawMessage --> callParentConstructor
    callParentConstructor --> end([End])

    style start fill:#f9f,stroke:#333,stroke-width:2px
    style end fill:#f9f,stroke:#333,stroke-width:2px
```
