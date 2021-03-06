# Architecture

This is a guideline on architecture for web applications, with the goal of minimizing technical debt and otherwise saving time.

### Dependencies

1. See any dependency as a cost. The marginal benefit (so, minus opportunity cost of using no dependency) must be positive, ideally large.
2. The Python ecosystem does dependencies well. Node.js has gone overboard.
3. Avoid dependencies that themselves depend on other optional dependencies where possible. ie) django-celery-tags depends on django AND celery which increases the risk of support blackout periods for new versions of Django and Celery.
4. If you must use a dependency, in general you should use the one that does the least additional things you're not going to use.
5. As an extension of the above, prefer micro-libraries which provide a small number of tools to accomplish a lot in your application's domain.

As a heuristic, the value of a dependency is:

TOTAL_MARGINAL_BENEFIT / ( SQRT(LIBRARY_API_SIZE) + NUMBER_OF_SUB_DEPENDENCIES)

### Data Model

Spend a lot of time getting the right data model (data structures and DB schema) as all your other application layers tend to have deeper dependencies on this.

### Interfaces and Indirection

Interfaces occur when we create a new abstraction which messages others, rather than a single abstraction. Strategy and tactics:

1. Generally, function boundary interfaces are the most efficient to use.
2. They should be used whenever it eliminates code duplication unless this would substantially reduce the overall clarity.
3. Functions should include as few arguments as possible (loose coupling)

TODO: this section needs a lot of work.
