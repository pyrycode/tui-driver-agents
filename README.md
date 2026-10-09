## Opt-in corpus tools

`tools/tui-driver` holds `corpus-label`, `corpus-sampler`, `corpus-replay` and
`repro-permission-flake` with their fixtures and tests.
They are a separate Go module and never part of the product's ordinary gate or e2e build.
The module uses the sibling `../tui-driver` library checkout.
Set `TUIDRIVER_REPO_PATH` for another installation, or invoke the launcher from
the product checkout. A temporary Go workspace binds tools to that library.

From a product checkout, run `../tui-driver-agents/bin/tui-tool TOOL [ARGS...]`.
`make corpus-replay` and `make repro-permission-flake` remain compatibility commands.
Run `bin/tui-tool test` explicitly for the offline tool tests.
The labeling and permission diagnostic commands can invoke real Claude.
Their tests use fake children and spend no model tokens.
Deploy this agents change before using the matching product's maintenance launchers.

`bin/pyry-test --slow` includes full-duration dispatcher timeout and wait-credit proofs.
