This guide is meant hold all of the experience from Eficodeans working with Kubernetes, distilled into one an easily readable format.

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