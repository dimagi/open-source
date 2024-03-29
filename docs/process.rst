Code Release Process
^^^^^^^^^^^^^^^^^^^^

This document contains guidance on internal processes that are commonly part of code submission and review in our Open Source repositories.

PR Template
^^^^^^^^^^^

Depending on the repository, your PR may be populated with a structured template, or in some cases you may have a choice of templates to apply. 

We use templates for a mix of applying guiderails to the submission process, as well as ensuring that the structure of changes is clearly communicated including risks and how they are accounted for.

Labels
^^^^^^

Many of our repos require PRs to be labeled for the sake of internal process, with the labels themselves being specific to the contribution process for each repository. 

Label adherence is enforced by the `label-bot <https://github.com/dimagi/label-bot>`_, which will mark your PR as failing a check if it is unlabeled. 

If you do not have core committing access, a member with write access will label your PR based on the code changed, your PR overview, and any other factors that come up during review.

Code Review
^^^^^^^^^^^

All code goes through review, see `detailed docs <https://github.com/dimagi/open-source/blob/master/docs/code_review.md>`_.

QA
^^

Some changes, particularly those that are user-facing, may be subject to an internal QA review. If your change needs QA, this will be flagged during code review.
A repository owner will assist with getting your change through QA, but the general process is:

* QA is kicked off *after* code review is complete
* Developers work directly with QA to communicate the new/changed functionality
* QA team develops test plan for feature and may also run additional regression or exploratory testing
* QA team reports issues to developer
* Developer fixes or otherwise resolves issues and notifies QA as each issue is resolved
* QA re-tests to verify that issues are resolved
* When all issues are resolved, QA signs off on feature

QA is typically conducted on a staging server. A repository owner can assist with getting your code deployed to staging, both for initial QA and then as bugs are fixed.

User-Facing Changes
^^^^^^^^^^^^^^^^^^^

Any user-facing changes should be consistent with existing UIs and adhere to the `CommCare Style Guide <https://www.commcarehq.org/styleguide>`_.
Non-trivial user-facing changes are subject to internal product review.
