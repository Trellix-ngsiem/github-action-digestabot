
# Github actions

## Example steps using the action
Example of using workflow for using the action.

```mermaid
graph
    subgraph Steps
        Step1["actions/checkout@v3"]
        Step2["wayne-gibson/githubactions@main"]
    end
    Step1 --> Step2
```

## Manual steps
To remediate pulling 3rd party binaries from the internet, the user will need to download the GO Crane binaries manually for now from https://github.com/google/go-containerregistry/releases and creating a new release within artifactory https://artifactory.trellix.com/ui/repos/tree/General/perinola-local/github-actions/crane  (To be change in the future)


```mermaid
graph
    User -- Download Crane release --> github.com
    User -- Scan --> Binaries
    User -- Upload release --> artifactory.trellix.com
```


## Steps for this action
```mermaid
graph

    subgraph Steps
        Step1[Obtain GO Crane]
        Step2[Detect New Images]
        Step3[Create Pull Request]
    end
    Step1 -- Download Crane --> artifactory.trellix.com
    Step2 -- Docker search for new Digests --> Registries[Docker Registries]

    Step1 --> Step2 --> Step3
```
