
CommCare Mobile Standards and Best Practices
============================================


This document provides CommCare Mobile specific best practices that are to be followed while writing code for our mobile projects. Please read through [our general code standards first](https://github.com/dimagi/open-source/blob/master/docs/standards.rst) which apply to all our projects including CommCare Mobile.


### Code Style and Readability

- Code should be easy to read, understand, and maintain.
- Meaningful variable and method names should be used. Variables should generally follow camel case except for static constants which should follow the `STATIC_CONSTANT` pattern
- Code should be formatted as per the [code style settings](https://github.com/dimagi/commcare-android/?tab=readme-ov-file#code-style-settings).
- Code should pass the coding standards set by the [checkstyle config](https://github.com/dimagi/commcare-android/blob/master/.github/linters/checkstyle.xml)
- All subcontexts should be braced, even one-liners  (if {})
- keyword expressions with arguments should be separated by a space (if (), not if())
- Braced expressions should begin a newline after opening brace, and before and after the close brace
- Typecasts should be adjacent to the value being cast: (int)value
- To improve code readability, newly added code should limit size of Classes under 500 lines and size of methods under 50 lines

### Modularity and Resusability

- Code should be modular, with a clear separation of concerns, reusable components (e.g., utility classes, helper functions) should be identified and utilized.

### Performance

- Code should be optimized for performance where necessary (e.g., efficient data structures, and minimal resource usage).
- Code should not introduce performance bottlenecks or memory leaks.

###  Error Handling:

- Proper error-handling mechanisms should be implemented (e.g., try-catch blocks, exception handling).
- Errors should be logged appropriately for debugging purposes.
- Don't include exceptions that extend `RuntimeException` in method signatures (as in "throws StorageFullException"). The compiler provides no static guarantees on runtime exceptions. Recoverable runtime exceptions should be documented in the javadoc (as in "@throws StorageFullException reason/how to recover").

### Logging

- `System.out` should be avoided.
- `Logger.log` statements logs are submitted back to HQ. These should be for top level events that help us get a feel for what's going on on the phone, as well as any unexpected states that the app gets into. For Ex. Beginning unsent data submission: N forms to be submitted" or "Unexpected cache miss for recently serialized records".
- `Logger.log` messages are persisted so it is important to be judicious when deciding to use logger.log. Log events should occur with a frequency that is bounded by user events (login, sync, form entry start, etc), not looping or machine driven. For instance "Migrated 512 cases", not "Migrating case 23 of 512"
- Always include as much context as possible. "Error - Invalid date for parsing" is much less helpful than "Error - Invalid date for parsing: 'January 2015'"

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
