# Mastering

## Making a GitHub release

It is useful to make zips for [GitHub Releases](https://docs.github.com/en/free-pro-team@latest/github/administering-a-repository/managing-releases-in-a-repository) if/when you make updates to the font.

First, commit any work you’ve done, as the current commit number will be used to tag to the released fonts.

To prepare a new release folder & zip, use:

```bash
mastering/make-github-release/make-release.sh
```

(This assumes you have already built with the correct version numbering in `fonts/Fraunces[SOFT,WONK,opsz,wght].ttf`. To check this, you can use [font-v](https://github.com/source-foundry/font-v/), or view `name ID 5` with `ttx -t name -o- fonts/Fraunces[SOFT,WONK,opsz,wght].ttf`.)

It will copy files to a folder like `UnderCaseType_Fraunces_1.001` and output a zip like `UnderCaseType_Fraunces_1.001.zip`.

You can then drag-and-drop this zip into your release notes.

NOTE: To edit the recommendations in the `README.md` included with releases, update `mastering/make-github-release/data/release-notes--all.md`, which is copied into release zips.


## Setting font file versions

Font versions are updated as part of `mastering/make-github-release/make-release.sh`, so if you just need to change version numbers in all fonts just make sure to have build the variable fonts with the correct versioning.

If for some reason you need to update versions without building new fonts, you can quickly do so with `helpers/set-version-fonts-in-dir.sh`.

```
<path>/set-version-fonts-in-dir.sh <directory> <version>
```

For example:

```
mastering/make-github-release/helpers/set-version-fonts-in-dir.sh fonts 1.000
```

NOTE: You should remake woff2 files with `sources/build-scripts/make-woff2s.sh` after you update version numbers, as font-v doesn’t currently change woff2 versions.


## Making PRs to google/fonts for updates

You can use `mastering/googlefonts/gftools-packager-fraunces.sh` to make PRs to [google/fonts](https://github.com/google/fonts). However, this tool may evolve.

NOTE: You need push access to google/fonts for this to work.