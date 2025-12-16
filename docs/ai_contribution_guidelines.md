## AI Facilitated Contribution Guidelines
Dimagi’s development teams welcome code contributions which are supported by AI backed tools like Cursor, Claude Code, and Copilot.

We expect developers to adhere to some guidelines when using these tools, to ensure that these contributions can be appropriately assessed and reviewed. Contributors who don’t meet these expectations may have their PR’s closed or unreviewed without further guidance. 

### Expect a standard review
Contributions to codebases supported by AI agents will be expected to meet the same standards for approach and execution as traditional contributions, and developers should familiarize themself with any repository specific CONTRIBUTING guidelines before submitting a change proposal. 

* Developers are expected to have a line-by-line understanding of their contribution before it is submitted
* Developers are expected to execute all proposed code changes either manually or through automated tests before it is submitted
* Developers are expected to address checks on the PR (automated testing, linting, etc) before people will engage on it
* Developers will be expected to be able to engage with feedback and independently ensure that feedback is addressed 
* Complex contributions are expected to structurally facilitate effective review (commit-by-commit structure, etc)
* We still expect accessible technical descriptions, design documentation, and full safety story articulating how contributions were structured and tested to ensure their correctness and safety to apply

### Adhere to codebase specific expectations
Most Dimagi codebases should support supporting materials and documentation to support AI backed development (like `agents.md` guidance files), these materials guide coding agents to adhere to style and approach expectations for a codebase. 

We expect developers to ensure these guidelines are processed and followed by any tools supporting their coding. Contributions which don’t follow those expectations may be rejected without significant review to protect the consistency of the code.

If you are using a common agent which doesn’t automatically consume the guidance file, you should create a symlink to where your agent expects to consume it, and add that location to gitignore if it has not already. 

### Keep it concise
Agents have a documented tendency to be extremely verbose when generating code or other artifacts like comments, git commit messages, or documentation. Generally speaking, contributions with a normal LLM level of verbosity would not meet Dimagi’s standards.

Individual repositories should provide as much guidance on this as possible, but as per Dimagi’s [general, global guidance](https://github.com/dimagi/open-source/blob/master/docs/standards.rst#code-styles) for contribution the overriding rule is that code (and other contributions) should look like code around it. Contributors should review similar artifacts to the ones they are planning on submitting to ensure that they are familiar with what is expected. 

### Isolate agent generated portions in history
When contributions contain significant volumes of AI generated code (new files, large complex functions, etc), contributors are encouraged to allow agents to commit initial functional code (or to manually commit agent generated code) before making significant refactors or changes, other than those needed to get code functional or to remove (without major refactor) significant amounts of unnecessary code. 

This allows stakeholders to understand the history of the contribution more clearly, and more accurately trace the origin of code to an initial AI generation. It is less important for iterative commits to be associated with the AI agent, since iterative changes are expected to be more clearly guided by developers. 
