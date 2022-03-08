# Examples

Generate a PDF document with support for awesome boxes

```bash
cd complex
docker  run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--metadata-file=metadata.yml \
--listings --pdf-engine=xelatex \
--resource-path=images --filter pandoc-latex-environment \
--output=tvd-good-practice-template_en.pdf doc/?x??-*.md
```