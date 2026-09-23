# ZCRE installation and connection assistance

These instructions apply when helping a user install or connect this package.

- Keep installation, OAuth completion, tool availability, and an authenticated
  model-list readback as separate checks. Do not report usable connection from
  installation output or a successful login command alone.
- After login, inspect the current turn's available tools and use the host's
  supported tool discovery when available. Earlier turns' inventories can be
  stale. Prefer the production `zcre-plugin` tools; `zcre-dev-qa` is a different
  connection and is not evidence that the production plugin works.
- If `query_zcre` is available, call it with `{"query":{"action":"models"}}`
  for connection verification. This is read-only. Do not upload, quote, or
  generate content to test a connection without the user's corresponding request.
- If tools remain unavailable, use a documented host refresh capability only
  when it is actually exposed and callable in the current environment. Do not
  invent a chat command or claim that a natural-language refresh request ran it.
- Follow the owner-approved onboarding guide: installation request, login request,
  browser consent plus a full app restart, then generation in the existing chat.
  The restart is based on the observed first-connection case, not a requirement
  before every use. Do not substitute an unverified MCP-list authentication
  button or promise restart-free activation. A generation example in a guide
  is not authorization to execute it while editing or testing the guide.
- Do not bypass denied app automation, read/extract OAuth credentials, alter
  another connection, or start a separate runtime and present its success as
  proof that the existing desktop conversation refreshed.

Documentation-only changes do not change the plugin's connection manifest.
Before publishing, review both READMEs together and run `git diff --check`.
