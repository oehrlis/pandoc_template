# Examples

Below you find a couple of examples to build different documentations

Simple PDF with embedded meta data

```bash
pandoc --template templates/trivadis.tex --listings --pdf-engine=xelatex \
-o examples/simple.pdf examples/simple.md
```

Simple DOCX with embedded meta data

```bash
pandoc --reference-doc templates/trivadis.docx --listings \
-o examples/simple.docx examples/simple.md
```

Complete documentation as PDF using dedicated metadata.

```bash
pandoc --template templates/trivadis.tex --listings --pdf-engine=xelatex \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md
```

Complete documentation as DOCX using dedicated metadata.

```bash
pandoc --reference-doc=templates/trivadis.docx --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.docx examples/en/?x??-*.md
```

Training / Workshop presentation (PPTX).

```bash
pandoc --reference-doc=templates/trivadis.pptx --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pptx examples/en/1x??-*.md
```
