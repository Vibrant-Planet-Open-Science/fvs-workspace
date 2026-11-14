# Contributing

We welcome example workflows that help people get started with FVS: a walkthrough in the FVS GUI, an R notebook using `rFVS`, a Python notebook using `fvs2py`, or a comparison across them.

## Start with an issue

Before you write anything, [open an issue](https://github.com/Vibrant-Planet-Open-Science/fvs-workspace/issues/new) describing what you'd like to share, so we can agree on scope and fit before you put in the work. Tell us:

- what the workflow teaches, and who it's for
- whether it uses the GUI, R, Python, or more than one
- which FVS variant(s) it runs
- what input data it needs, where that data comes from, and how large it is

Issues are also the place to report a problem with the workspace or ask for a package to be added to it.

## Preparing an example

Once we've agreed on an example in its issue, open a pull request that adds it in its own folder under `examples/`, with a short `README.md` that says what it shows and how to run it.

An example should:

- **Run as-is in fvs-workspace,** on Binder or in Docker, top to bottom, with no extra installs or downloads. If it needs a package the workspace doesn't have, raise that in the issue.
- **Bring its own data.** Include the keyword files and input databases it uses, and keep them small (a few MB). FVS writes its output files into the current working directory, so have notebooks change into a scratch folder first rather than writing beside the inputs.
- **Use data you can share publicly.** Only include data you have the right to publish under this repository's license, and nothing confidential or personal, such as landowner or private-property details.
- **Keep notebook outputs small.** GitHub shows saved outputs, which helps readers, but clear large tables or plots that bloat the file.

Contributions are released under this repository's [MIT License](LICENSE).

## Pull request titles

Pull requests are squash-merged, and the title becomes the commit message that [release-please](https://github.com/googleapis/release-please) uses for versioning and release notes. Use a [Conventional Commit](https://www.conventionalcommits.org/) title, such as `feat: add an rFVS thinning example`. If you're unsure, a maintainer will adjust it before merging.
