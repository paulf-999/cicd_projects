# Azure Pipelines Predefined Variables

## Build-Related Variables

| Variable                    | Description                                                 |
|-----------------------------|-------------------------------------------------------------|
| `Build.BuildId`             | The ID of the current build.                                |
| `Build.BuildNumber`         | The human-readable build number, often set using a pattern. |
| `Build.DefinitionName`      | The name of the current build definition.                  |
| `Build.Repository.Name`     | The name of the repository being built.                    |
| `Build.SourceBranch`        | The branch being built.                                     |
| `Build.SourceVersion`       | The commit/changeset ID being built.                        |
| `Build.SourceVersionMessage`| The commit message of the current build.                   |
| `Build.SourcesDirectory`    | The local path on the agent where the source code is downloaded.|

## Agent-Related Variables

| Variable              | Description                          |
|-----------------------|--------------------------------------|
| `Agent.Id`            | The ID of the agent running the pipeline.|
| `Agent.Name`          | The name of the agent running the pipeline.|
| `Agent.WorkFolder`    | The working directory of the agent.   |

## Environment Variables

| Variable                        | Description                                      |
|---------------------------------|--------------------------------------------------|
| `System.DefaultWorkingDirectory`| The default working directory of the build agent.|
| `System.TeamProject`            | The name of the Azure DevOps project.            |
| `System.JobId`                  | The ID of the current job.                       |
| `System.StageDisplayName`       | The name of the current stage.                   |
| `System.JobDisplayName`         | The name of the current job.                     |
| `System.CollectionId`           | The ID of the collection containing the pipeline.|

## Pull Request Variables

| Variable                           | Description                                                                |
|------------------------------------|----------------------------------------------------------------------------|
| `System.PullRequest.SourceBranch`   | The source branch of the pull request.                                |
| `System.PullRequest.SourceCommitId` | The commit ID of the latest change in the source branch of the pull request.|
| `System.PullRequest.TargetBranch`   | The target branch of the pull request (the branch being merged into).       |
| `System.PullRequest.PullRequestId`  | The ID of the pull request.                                               |
| `System.PullRequest.PullRequestNumber` | The number of the pull request.                                           |
| `System.PullRequest.IsFork`         | Indicates whether the pull request is from a forked repository.            |

## Release-Related Variables

| Variable                    | Description                                        |
|-----------------------------|----------------------------------------------------|
| `Release.ReleaseId`         | The ID of the current release (for release pipelines).|
| `Release.ReleaseName`       | The name of the current release (for release pipelines).|
| `Release.Artifacts.{Alias}.Alias` | The alias of the artifact used in the release pipeline.|

## User-Defined Variables

You can define your own custom variables in your pipeline configuration and access them during the build or release process.
