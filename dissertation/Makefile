PY=python
PANDOC=pandoc

BASEDIR=$(CURDIR)
INPUTDIR=$(BASEDIR)/source
OUTPUTDIR=$(BASEDIR)/output
STYLEDIR=$(BASEDIR)/style
SCRIPTSDIR=/Volumes/Data/Box Sync/Scripts
OUTFILE=dissertation

BIBFILE=../citations/abrahamsen.bib

	# --filter "$(SCRIPTSDIR)/pandoc-linespacing.py" \

help:
	@echo ' 																			'
	@echo 'Makefile for the Markdown thesis       '
	@echo '                                       '
	@echo 'Usage:                                 '
	@echo '   make html		generate a .html file		'
	@echo '   make pdf		generate a .pdf file  	'
	@echo '   make docx		generate a .docx file 	'
	@echo '   make odt		generate a .odt file 		'
	@echo '   make tex		generate a .tex file 		'
	@echo ' 																	  	'

pdf:
	pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).pdf" \
	--template="$(STYLEDIR)/template.tex" \
	--filter pandoc-include \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).pdf"

tex:
	pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).tex" \
	--template="$(STYLEDIR)/template.tex" \
	--filter pandoc-include \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--wrap=none \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).tex"

docx:
	pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).docx" \
	--reference-docx="$(STYLEDIR)/reference.docx" \
	--filter pandoc-include \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).docx"

odt:
	pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).odt" \
	--reference-odt="$(STYLEDIR)/reference.odt" \
	--filter pandoc-include \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	open "$(OUTPUTDIR)/$(OUTFILE).odt"

html:
	pandoc "$(INPUTDIR)"/*.md \
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
