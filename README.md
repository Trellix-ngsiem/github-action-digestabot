# Trellix version of Chainguard digestabot github action
This is a cloned of https://github.trellix.com/Shared-GitHub-Actions/digestabot  until we can get a Trellix-github-action created in github.com


## Why not use the Chainguard version directly.
- It uses some 3rd party github actions
- The 3rd party github actions, retrieve binaries without verify the hash so opens us up to chain supply attack.


## End Result
- 3rd party actions have been replaced
- Binaries are pulled from artifactory, no hash checking (currently)..


## Workflows
see [Workflow.md](./Workflow.md)


## Commands
| Argument             | default | Description |
| :----------------  | :------: | :---- |
| working-dir        |   '.'   | Location to start searching for the files |
| token              |   ${{ github.token }}   | Github token to be used by the github cli |
| labels-for-pr      |   ''   | A comma or newline separated list of labels to be used in the pull request.<br> labels must exist, otherwise the PR will fail. |
| raise-pr-against      |   'main'   | Branch name for the PR to be raised against |
| raise-pr-against      |   'main'   | Branch name for the PR to be raised against |
| title-for-pr      |  'Update image digest(s)' | PR title will be prefixed with the date and time, followed by this title provided. |
| description-for-pr      |  'Update image digest(s)' | The description of the pull request |
| commit-message      |  'Automated: Digest Update' | The description for the git commit |
| github_host      |  'github.trellix.com' | Required for the github cli for **auth** command |
| github_protocol      |  'https' | Required for the github cli for **auth** command, this can be https or ssh |


## Pre-requisite
- **linux x64 runner** - due to the binaries being downloaded.
- **sed**   - must be installed and on the path prior to this action.
- **grep**  - must be installed and on the path prior to this action.
- **Docker login** -  for the docker registries should be done prior to this action.

- **git**   - Must be installed and on the path prior to this action.
    - **2.18 or higher** Due to **actions/checkout@v3** in order to create a local Git repository.
        - If not done then the none of the git commands will work :(
        - For Ubuntu do the following:
            ```
            sudo add-apt-repository ppa:git-core/ppa
            sudo apt-get update
            sudo apt-get install git
            ```

- **gh cli**    - Must be installed and on the path prior to the this action.
    - Required for the PR the runner to create an pull request when new digests found
        - For Ubuntu do the following:
        ```
        sudo snap install gh
        ```


## Todo
- Determine the location of the github actions
    - Either use https://github.trellix.com/trellix-utilities or request a new organization for trellix-actions.. TBD
- Determine the artifactory repo to be used and if it requires authentication or not.
- Determine if GH cli, should be placed in artifactory rather than making it a requirement.
- Adding hash for Crane to github action, to verify the binary hasn't been altered


---
---
## Original Chainguard Digestabot
Can be found on https://github.com/chainguard-dev/digestabot
Copy of the files and documentation can be found [here](./chainguard/)



