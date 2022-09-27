# Examples

Generate a PDF document with support for awesome boxes

```bash
cd complex
docker  run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--metadata-file=metadata.yml \
--listings --pdf-engine=xelatex \
--resource-path=images --filter pandoc-latex-environment \
--output=tvd-complex-example.pdf doc/?x??-*.md
```

Complete documentation as DOCX using dedicated metadata.

```bash
pandoc --reference-doc=templates/trivadis.docx --listings \
--metadata-file=metadata.yml --resource-path=images \
-o tvd-complex-example.docx doc/?x??-*.md
```
