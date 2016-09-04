PY=python
PANDOC=pandoc

BASEDIR=$(CURDIR)
INPUTDIR=$(BASEDIR)/source
OUTPUTDIR=$(BASEDIR)/output
STYLEDIR=$(BASEDIR)/style
SCRIPTSDIR=/Volumes/Data/Dropbox/Scripts
OUTFILE=dissertation

BIBFILE=../citations/abrahamsen.bib

help:
	@echo ''
	@echo 'Makefile for the Markdown thesis'
	@echo ''
	@echo 'Usage:'
	@echo '   make docx		generate a .docx file'
	@echo '   make html		generate a .html file'
	@echo '   make odt		generate a .odt file'
	@echo '   make pdf		generate a .pdf file'
	@echo '   make tex		generate a .tex file'
	@echo ''

pdf:
	time pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).pdf" \
	--template="$(STYLEDIR)/template.tex" \
	--filter "$(SCRIPTSDIR)/pandoc-linespacing.py" \
	--filter "$(SCRIPTSDIR)/pandoc-diss-filter.py" \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).pdf"

tex:
	time pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).tex" \
	--template="$(STYLEDIR)/template.tex" \
	--filter "$(SCRIPTSDIR)/pandoc-linespacing.py" \
	--filter "$(SCRIPTSDIR)/pandoc-accidentals.py" \
	--filter "$(SCRIPTSDIR)/pandoc-timesig.py" \
	--filter "$(SCRIPTSDIR)/pandoc-rhythms.py" \
	--filter "$(SCRIPTSDIR)/pandoc-dynamics.py" \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--wrap=none \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).tex"

docx:
	time pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).docx" \
	--reference-docx="$(STYLEDIR)/reference.docx" \
	--filter "$(SCRIPTSDIR)/pandoc-linespacing.py" \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).docx"

odt:
	time pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).odt" \
	--reference-odt="$(STYLEDIR)/reference.odt" \
	--filter "$(SCRIPTSDIR)/pandoc-linespacing.py" \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).odt"

html:
	time pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).html" \
	--template="$(STYLEDIR)/template.html" \
	--include-in-header="$(STYLEDIR)/style.css" \
	--standalone \
	--toc \
	--number-sections
	rm -rf "$(OUTPUTDIR)/source"
	mkdir "$(OUTPUTDIR)/source"
	cp -r "$(INPUTDIR)/figures" "$(OUTPUTDIR)/source/figures"

.PHONY: help pdf docx html tex
