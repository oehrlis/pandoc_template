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

Create DOCX

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc --listings \
-o examples/simple.docx examples/simple.md
```

Create PDF

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
-o examples/simple.pdf examples/simple.md
```
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc:2.5 \
--pdf-engine=xelatex --listings \
-o examples/simple.tex examples/simple.md
LuaLaTeX
Create PDF

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
-o examples/simple.pdf examples/simple.md
```

Create PDF

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
--template templates/trivadis.tex \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc:2.5 \
--listings \
--template templates/trivadis.tex \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md
```

LuaLaTeX

docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
--resource-path=.,./examples/images \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
--resource-path=. \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z ccdd70ba4c41 \
--pdf-engine=pdflatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z ccdd70ba4c41 \
--pdf-engine=lualatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md


docker run --rm -v "$PWD":/workdir:z ccdd70ba4c41 \
--pdf-engine=pdflatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z ccdd70ba4c41 \
--pdf-engine=xelatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md

weasyprint, prince, pdflatex, lualatex, xelatex, latexmk, tectonic, pdfroff, context
```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
--template templates/eisvogel.tex \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md
```

--trace

Create PDF

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md
```

Create PDF

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md
```

Create DOCX

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--listings --metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.docx examples/en/?x??-*.md
```

Create PPTX

```bash
docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--listings --metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pptx examples/en/1x??-*.md
```




docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc:dev2 /usr/local/bin/pandoc \
--pdf-engine=xelatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md



docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc:dev2 /usr/local/bin/pandoc \
--listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide.pdf examples/en/?x??-*.md



docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide_default.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide_xelatex.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
--metadata-file=examples/en/metadata.yml \
-o examples/simple_xelatex.pdf examples/simple.md

oehrlis/pandoc:oel

docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc \
--pdf-engine=xelatex --listings \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide_xelatex_no.pdf examples/en/?x??-*.md

docker run --rm -v "$PWD":/workdir:z oehrlis/pandoc:oel \
--pdf-engine=xelatex --listings \
-o examples/O-DB-DOCKER_Lab_and_Exercise_Guide_xelatex_no.pdf examples/en/?x??-*.md