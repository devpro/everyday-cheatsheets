# fly

The fly CLI tool is the command line client of [Concourse](./concourse.md).

→ [concourse-ci.org/fly](https://concourse-ci.org/fly.html)

## Installation

Download from a running Concourse instance or from the [GitHub release page](https://github.com/concourse/concourse/releases).

## Commands

Command | Action
------- | ------
`fly login` | Authenticates with a given endpoint and saves it under a convenient name
`fly targets` | Displays the targets that are currently known to fly
`fly status` | Checks the current authentication status with a given target
`fly userinfo` | Checks what user is logged in, with team & role information
`fly logout` | Clears out the token for a given target (or for all targets)
`fly edit-target` | Modifies a target's name, team, or URL
`fly delete-target` | Deletes all targets (or all)
`fly sync` | Adds additional features to fly or make changes to the communication between it and Concourse's API server
`fly completion` | Outputs autocomplete configuration for some shells

## Examples

```bash
fly --target example login --team-name my-team --concourse-url https://ci.example.com

fly -t example status

fly logout -a
```
