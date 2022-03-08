# Author and Release Guide
<!-- markdownlint-configure-file { "MD013": { "tables": false } } -->
## Document Structure

### Folders

This repository contains a couple of default folders. The language specific
folders are only a suggestion and have to be adapted or deleted accordingly. If
you add or remove language folders you also have to adjust the Azure DevOps
pipeline. [Doc Build](.build/doc-pipeline.yml)

- [en](en) English documentation files.
- [images](images) Images and logo files.

The following Markdown files are generic files describing the repository,
authoring, contributing etc. They are not related to the good practice nor will
they be used to build the good practice documentation.

- [AUTHOR_GUIDE](AUTHOR_GUIDE.md) General author's guide to *Trivadis Markdown
  Doc Template*. This has to be adapted to the corresponding guideline.
- [CHANGELOG](CHANGELOG.md) Change log for the *Trivadis Markdown Doc Template*.
- [LICENSE](LICENSE) License for this template.
- [VERSION](VERSION) file to store the version number.

### Markdown Files

#### General Information

Each language of the *Trivadis Markdown Doc Template* includes a bunch of
*Markdown* files. These files do follow a naming pattern `NxMM-Title.md` where
`N` and `MM` stands for the following:

- **N** Digit for the main chapter number.
- **M** Two digit for sorting the files within a main chapter.
- **Title** Just a title to name the file. Should be related to the content.

*It is cructial* to keep the prefix, as this is used to sort the Markdown files
during the document build process. Files with no or an other prefix will be
ignored during documentation build.

| Prefix | Chapter                                                     |
|--------|-------------------------------------------------------------|
| `0x..` | Preface, Revision History and other general doc information |
| `1x..` | Introduction, management summary, scope, etc.               |
| `2x..` | Chapter 1 will be TOC number 3                              |
| `Nx..` | Good practice chapter N will be TOC number N+2              |
| `9x..` | Appendix files                                              |

You can add as much files as you want. The prefix itself is not relevant for
for the TOC itself. Pandoc will create the TOC based on the headings within the
Markdown files. e.g. `#` will create a top level heading.

#### Markdown Syntax

You will find plenty of Markdown references and cheat sheets online e.g.
[/Markdown-Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

Just be aware, that the Markdown syntax is checked by a Pipeline based on
markdownlint-cli (see
[markdownlint](https://github.com/DavidAnson/markdownlint),
[markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli)
or [DavidAnson/markdownlint](https://hub.docker.com/r/06kellyjac/markdownlint-cli)).
Any violation of the
[rules](https://github.com/DavidAnson/markdownlint/blob/main/doc/Rules.md)
will result in an error. You either have to fix the error or add an exception
to the rule. The exception has to be added to each file or alternatively in the
global configuration [.markdownlint.json](.markdownlint.json).

A few examples for embedded exceptions:

- Ignore rule MD013 / line length for tables

```html
<!-- markdownlint-configure-file { "MD013": { "tables": false } } -->
```

- Ignore rule MD013 / line length completely in this file

```html
<!-- markdownlint-disable MD013 -->
```

- Ignore rule MD024 / Multiple headings with the same content

```html
<!-- markdownlint-configure-file { "MD024": { "allow_different_nesting": true } } -->
```

An example for a global exception:

```JSON
{
  "default": true,
  "MD003": { "style": "atx_closed" },
  "MD007": { "indent": 4 },
  "no-hard-tabs": false,
  "whitespace": false
}
```

It is recommended to add a Markdown Lint to you favorite editor like
*Visual Studio Code* and the Markdownlint by David Anson.

The latest release does support boxes in PDF generation. See
[1x10-General_Information](en/1x10-General_Information.md) for an example.

```markdown
::: note
**Note** Lorem ipsum dolor ...
:::
```

### Document Metadata

Pandoc document conversion can be configured / customized using metadata either
as a metadata block in the Markdown file itself or in a dedicated
[YAML](https://yaml.org/spec/1.2/spec.html) file. See also the
[pandoc documentation](https://pandoc.org/MANUAL.html). The workflow in this
repository is configured to use a dedicated metafile for each language. The file
is named `metadata.yml` and located in the corresponding directory (e.g.
[en/metadata.yml](en/metadata.yml))

It is strongly recommended to adjust the metadata according to the requirement
of the respective *documentation*.

## Additional Language

This template does have one folders per languages english [en](en). If
necessary, this directory can be copied to add another language. The language
abbreviation is used as the directory name. e.g. fr, de, en etc. In order for
the documents to be created for an additional language, the Azure DevOps
pipeline *Doc Build* must be adapted. For the new language, corresponding steps
must be available or corresponding job must be removed. The Azure DevOps
pipeline *Doc Build* is available in [doc-pipeline.yml](.build/doc-pipeline.yml).

As an example, the step the German PDF documentation:

```YAML
  # Build PDF documentation using oehrlis/pandoc container
  - script: |
      DOC_LANG="de"
      DOC_NAME="${BUILD_REPOSITORY_NAME}_${DOC_LANG}"
      docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
      --metadata-file=${DOC_LANG}/metadata.yml \
      --listings --pdf-engine=xelatex \
      --resource-path=images --filter pandoc-latex-environment \
      --output=${DOC_NAME}.pdf ${DOC_LANG}/?x??-*.md
    displayName: 'Build PDF documentation'
```

As you can see you only have to adapt the language variable `DOC_LANG=de`.

## Releases and Versions

### Release and Version Numbering

You find all official releases and release information on the Azure DevOps
project release page. As well documented in the [CHANGELOG](CHANGELOG.md).

The versioning and release tags follow the
[semantic versioning](https://semver.org/). A version number is specified by
*MAJOR.MINOR.PATCH*, increase the:

- *MAJOR* version when you make incompatible API changes,
- *MINOR* version when you add functionality in a backwards compatible manner,
  AND
- *PATCH* version when you make backwards compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions
to the MAJOR.MINOR.PATCH format.

### Create a Release

New releases currently have to be build via GitHub release. Each release require
a short release note. Procedure:

- Update / Commit changes
- Update the [CHANGELOG](CHANGELOG.md) add the latest change information
- Create an new release
- Add release information based on changes e.g.
  `git log --pretty=format:%s v0.1.0...HEAD`

## Creating a new *Markdown* documentation

This GIT repository is defined as a template and can be used in a new
repository. Just copy the corresponding files / folders in you GIT repository.

- Add the files to your GIT repository
- Add or remove language folders
- Update the README files and links
- Add the Azure DevOps pipeline using the file
  [.build/doc-pipeline.yml](.build/doc-pipeline.yml)

## Build Documentation

### Automatic Build Workflow

The Azure DevOps GIT repository does have a pipeline with several jobs defined.

| File                                                       | Workflow Name | Purpose                                              |
|------------------------------------------------------------|---------------|------------------------------------------------------|
| [doc-pipeline.yml](./.build/doc-pipeline.yml) | Doc Build     | Workflow with different jobs to build and publish the documents. |

The workflow do trigger on any *push* and *pull-request* on the main branch. If
necessary it can also be triggered manually via Azure DevOps.

### Manual Build

#### Docker Container

Creating the documents with the help of pandoc container
[oehrlis/pandoc](https://github.com/oehrlis/pandoc_template) is the most
convenient method. Apart from having Docker installed, there are no other
dependencies. The container xxx contains all the necessary components like
pandoc, TeX, fonts, templates, etc.

- Generate a PDF document with support for awesome boxes

```bash
docker  run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--metadata-file=en/metadata.yml \
--listings --pdf-engine=xelatex \
--resource-path=images --filter pandoc-latex-environment \
--output=tvd-good-practice-template_en.pdf en/?x??-*.md
```

- Generate a PDF document without support boxes

```bash
docker  run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--metadata-file=en/metadata.yml \
--listings --pdf-engine=xelatex \
--resource-path=images \
--output=tvd-good-practice-template_en.pdf en/?x??-*.md
```

- Generate a DOCX document

```bash
docker  run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--metadata-file=en/metadata.yml \
--listings --resource-path=images \
--output=tvd-good-practice-template_en.docx en/?x??-*.md
```

- Generate a PPTX document from Chapter 2-8. This will omit preface,
  introduction and appendix.

```bash
docker  run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--metadata-file=en/metadata.yml \
--listings --resource-path=images \
--output=tvd-good-practice-template_en.pptx en/[1-8]x??-*.md
```

#### Local pandoc Installation

If you do have a local *pandoc* installation including LaTeX, you may also
generate the corresponding documents directly using `pandoc` via command line.
But be aware of the necessary requirements. e.g. fonts, LaTeX, templates from
[oehrlis/pandoc_template](https://github.com/oehrlis/pandoc_template) etc.

- Generate a PDF document

```bash
pandoc --metadata-file=en/metadata.yml \
--template=$(pwd)/templates/trivadis.tex \
--listings --pdf-engine=xelatex \
--resource-path=images \
--output=tvd-good-practice-template_en.pdf en/?x??-*.md
```

- Generate a PDF document with support for awesome boxes.

```bash
pandoc --metadata-file=en/metadata.yml \
--template=$(pwd)/templates/trivadis.tex \
--listings --pdf-engine=xelatex \
--resource-path=images --filter pandoc-latex-environment \
--output=tvd-good-practice-template_en.pdf en/?x??-*.md
```

- Generate a DOCX document

```bash
pandoc --metadata-file=en/metadata.yml \
--listings --reference-doc templates/trivadis.docx \
--resource-path=images \
--output=tvd-good-practice-template_en.docx en/?x??-*.md
```

- Generate a standalone HTML document

```bash
pandoc --metadata-file=en/metadata.yml \
-s --toc --template=$(pwd)/templates/GitHub.html5 \
--resource-path=images \
--output=tvd-good-practice-template_en.html en/?x??-*.md
```

- Generate a EPUB document

```bash
pandoc --metadata-file=en/metadata.yml \
--reference-doc templates/trivadis.epub \
--resource-path=images \
--output=tvd-good-practice-template_en.epub en/?x??-*.md
```

## Further Topics

There a couple of additional topics which are not yet implemented or documented.
This includes among other the following points.

- Automatic Release Workflow
- Generate additional formates like Word (.docx), eBooks (.epub), Power Point
  (.pptx), man pages, etc.
- Generate HTML version / Webpage
