# Shared Actions and Workflows

This repository contains shared files used across all repositories.

## Reusable Actions

The [actions/](actions) folder contains reusable actions that can be called from any repository with:

```bash
- name: Run Action
  uses: MOEAFramework/.github/actions/<action_name>@main
  with:
    foo: ${{ inputs.bar }}
```

When authoring an action, a few key observations:

1. Unlike a workflow file, inputs are not typed and are treated as strings.  For booleans, we must use string comparison to check the value,
   such as `${{ inputs.foo == 'true' }}`.
2. Repository or organization secrets can not be accessed from the action and instead must be passed in as inputs.  GitHub does redact any
   secret values from the logs.
