PY=python
PANDOC=pandoc

BASEDIR=$(CURDIR)
INPUTDIR=$(BASEDIR)/source
OUTPUTDIR=$(BASEDIR)/output
STYLEDIR=$(BASEDIR)/style
OUTFILE=dissertation

BIBFILE=../citations/abrahamsen.bib

help:
	@echo ' 																			'
	@echo 'Makefile for the Markdown thesis       '
	@echo '                                       '
	@echo 'Usage:                                 '
	@echo '   make html			generate a web version'
	@echo '   make pdf      generate a PDF file  	'
	@echo '   make docx	    generate a Docx file 	'
	@echo '   make tex	    generate a Latex file '
	@echo ' 																	  	'
	@echo 'get local templates with: pandoc -D latex/html/etc'
	@echo 'or generic ones from: https://github.com/jgm/pandoc-templates'

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
	--from=markdown+table_captions \
	--latex-engine=xelatex

docx:
	pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).docx" \
	--reference-docx="$(STYLEDIR)/reference.docx" \
	--filter pandoc-include \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex
	--toc

odt:
	pandoc "$(INPUTDIR)"/*.md \
	-o "$(OUTPUTDIR)/$(OUTFILE).odt" \
	--reference-docx="$(STYLEDIR)/reference.odt" \
	--filter pandoc-include \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex
	--toc

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
