This guide is meant hold all of the experience from Eficodeans working with Kubernetes, distilled into one easily readable guide.

This means, that we welcome all contributions to 'what is the right tech stack'.

There are fundamentally 2 ways to contribute to this guide: recommend a tool, and adjust wording or tool areas of the guide.

## Recommend a tool

If you want to recommend a tool, the place to start is to write an Architecture Decision Record (ADR). All tools recommended in the guide is reflected in an ADR. 

To add an ADR do the following:

`hugo new --kind adr <DesiredFolder>/ADRs/<NameOfADRFile>.md --source .pages`

Fill out the sections in the generated ADR

Create a PR with the ADR and let the discussion begin. If the PR is approved, the status should be updated to 'accepted', and the ADR previously in place should be updated to superseded by ADR-0123.

## Suggest more general edits to tool categories or text

Create a PR with your suggestions, it will automatically be assigned to the maintainers of the repo.

## Questions

If in doubt you can always reach out to the maintainers of this guide, maintainers can be found in the codeowners file in the .github folder.

## Setting Up Your Development Environment

You can use either Devbox or Dev Containers to set up a consistent development environment for working on this guide.

### Using Devbox

1. Install [Devbox](https://www.jetpack.io/devbox/docs/installing_devbox/)
2. Clone this repository
3. Navigate to the repository root directory
4. Run `devbox shell` to enter a shell with all the required dependencies
5. You're now ready to make your changes!

### Using Dev Containers

1. Install [Visual Studio Code](https://code.visualstudio.com/) and the [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension
2. Clone this repository
3. Open the repository in VS Code
4. When prompted to "Reopen in Container", click "Yes". Alternatively, press F1 and select "Remote-Containers: Reopen in Container"
5. Wait for the container to build and start
6. You now have a fully configured development environment!

## Local Website Preview

To preview the website locally while making changes:

1. Run the Hugo development server:
   ```
   hugo server --source .pages
   ```
2. Open your browser and navigate to `http://localhost:1313/On-prem_Kubernetes_Guide/ `
3. The website will automatically refresh when you make changes to the source files
