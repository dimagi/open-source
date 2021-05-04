=============================
Common Category Contributions
=============================

Although many code conributions to projects are made as the result of changes requiring extensive planning and documentation, many instead come from much more limited scopes. A developer fixing a small bug or writing a new test case has less to communicate along with their PR.

To ensure that developers are able to make such contributions efficiently while retaining quality, common categories of changes have been outlined which can benefit from streamlined implementation and review. PR's that meet the criteria for a Common Category can be tagged to save time describing structure and intent, and are more efficient for review.

Our general Common Categories are described below, along with expectations that should be met by PR's tagged as such, and any expected criteria for review. In general it is a core expectation is that a Common Category contribution is as narrowly as possible, containing only the changes necessary and fulfilling the intent. A large PR which requires refactoring, bug fixing, and a functional change will be much more easily reviewed if separated into three contributions, two of which can be streamlined.

Modernization
~~~~~~~~~~~~~
Changes whose motivation is to change the codebase to ensure the ongoing compatibility with another system or component

Examples:

- Dependency updates
- Changes for external API compatibility
- Remove reliance on deprecated functionality

Bug Fix
~~~~~~~
Correct an error or out-of-spec behavior 

Expectations:

- The triggering condition for the error should be articulated through the PR, ideally through a replication test
- Any new behaviors should be described in full, ideally through a replication test, with explanations for the reasoning

Process
~~~~~~~
A PR which is used as part of a defined process defined by the project such as deployment. 

Reviewers are responsible for ensuring that the PR is compliant with the project process.

Expectations:

- PR references the specific process being followed


No-Ops
~~~~~~

The following "no-op" categories are for changes which improve the systems underlying structure without affecting its function.

Reviewers should verify that the changeset both does not impact the code, that the reasoning for the change matches the implementation, and that the outcome is aligned with the project standards and objectives

Common Expectations for no-op PR's

- The changeset will not meaningfully change system behavior
- Sufficient evidence is present to ensure that system behavior hasn't changed based on the scope of changes, ideally through reproducible tests

**Refactor**
    Restructure code to improve quality or comprehensibility without changing the function of the code
  
    - Expectation: The approach to code refactor is outlined and justified
 
**Performance**
    Improve the runtime speed or resource utilization of existing code without changing its function
  
    - Expectation: The magnitutde and real-world value of this improvement should be described in the Pull Request and the impact should be compatible with the scope of the change
 
**Documentation**
    Updates to docs about the code or about the system function in the codebase
