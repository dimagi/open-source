
CommCare Mobile Standards and Best Practices
============================================


This document provides CommCare Mobile specific best practices that are to be followed while writing code for our mobile projects. Please read through [our general code standards first](https://github.com/dimagi/open-source/blob/master/docs/standards.rst) which apply to all our projects including CommCare Mobile.


### Code Style and Readability

- Code should be easy to read, understand, and maintain.
- Meaningful variable and method names should be used.
- Code should be formatted as per the [code style settings](https://github.com/dimagi/commcare-android/?tab=readme-ov-file#code-style-settings).
- Code should pass the coding standards set by the [checkstyle config](https://github.com/dimagi/commcare-android/blob/master/.github/linters/checkstyle.xml)

### Modularity and Resusability

- Code should be modular, with a clear separation of concerns, reusable components (e.g., utility classes, helper functions) should be identified and utilized.

### Performance

- Code should be optimized for performance where necessary (e.g., efficient data structures, and minimal resource usage).
- Code should not introduce performance bottlenecks or memory leaks.

###  Error Handling:

- Proper error-handling mechanisms should be implemented (e.g., try-catch blocks, exception handling).
- Errors should be logged appropriately for debugging purposes.

### Java-Specific Criteria:

- Synchronization mechanisms (e.g., synchronized blocks, locks) should be used where shared resources are accessed concurrently.
- Code should properly handle multithreading scenarios to avoid race conditions and deadlocks.
- Proper memory management practices should be followed (e.g., avoiding memory leaks, efficient use of data structures).
 
### Kotlin-Specific Criteria:

- Nullable types are handled appropriately with safe calls and nullability checks.
- Use of Kotlin's built-in null safety features where necessary.

### Testing Criteria:

- Code should be well-covered by unit tests to ensure individual components work as expected.
- Tests should cover edge cases, error scenarios, and critical functionalities.
- Any feature work should be accompained by [corresponding instrumentation tests]([url](https://developer.android.com/training/testing/instrumented-tests)) in cases where we are not able to verify complete functionality with the help of unit tests.
     
### Documentation and Comments:

- Code should be adequately documented using appropriate comments, especially for complex algorithms, business logic, or non-obvious functionalities.
- Code should follow JavaDoc or KDoc standards for documenting classes, methods, and parameters.
- Comments should be used sparingly and effectively, providing insights into code logic or reasoning where necessary.
- Redundant or outdated comments should be avoided as that can lead to confusion.


In addition to above code standards, any contributions are required to follow [the due process to write a pull request](https://github.com/dimagi/open-source/blob/master/docs/Writing_PRs.md)








