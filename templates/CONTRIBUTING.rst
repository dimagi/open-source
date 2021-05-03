==========================
Contributing to the Project
==========================

This project is primarily developed by `Dimagi`_, but we welcome contributions.

Please keep in mind that we hold the standard of quality in contributions to a very high level regardless of source. Contributions which careful adhere to the processes and standards outlined here are much more likely to be reviewed for inclusion.

Issues
~~~~~~

This project uses Github's Issue Manager for public ticketing of bugs or improvements. 

For non-trivial changes requirements and design decisions can be captured in one of these tickets and referenced by any Pull Requests which implement the proposed changes.


Code Contributions
~~~~~~~~~~~~~~~~~~

Code contributions should be submitted as Github Pull Requests following templates and checklists in detail. Pull requests will be reviewed by the project maintainers according to this `Code Review Process`_.

To ensure the safety and consistentcy of this project any contributions will be expected to follow guidelines, meet quality standards, and follow any processes requested. You should ensure that your PR meets these expecations before it will be considered for review or re-review.

Before submitting a PR, review our `Guide to Authoring Pull Requests`_.  


Structure
---------

Pull requests must contain sufficient documentation to provide clarity on the purpose and structure of the changes being proposed and the requirements for their implementation, generally through a link to the ticketed issue which the PR is addressing.

Any architectural decisions which were made while choosing an approach should be explicitly documented along with the reasoning for eventual decisions. 

To streamline development, Pull Requests which fall into a `Common Category`_ should be tagged as such specifically.


Quality
-------

Pull requests will be subjected to automated testing through a Continuous Integration (CI) process. PR's with failing tests cannot be pulled, and are unlikely to be reviewed until test failures are addressed.

Reviewers are resonsible for ensuring that changes do not introduce defects with basic coding standards, performance issues, security concerns, maintainability, and dependency/configuration management of the codebase. If the scope of a changeset poses risks in these areas, those risks will need to be mitigated in the PR through additional testing, documentation, QA, analysis, etc. 

.. _Dimagi: https://www.dimagi.com/
.. _Code Review Process: https://github.com/dimagi/code-review/blob/master/README.md
.. _Common Category: https://github.com/dimagi/code-review/blob/master/common_category.md
.. _Guide to Authoring Pull Requests: https://github.com/dimagi/code-review/blob/master/Writing_PRs.md
