PY=python
PANDOC=pandoc

INFILE=abrahamsen-proposal
OUTFILE=abrahamsen-dissertation-proposal
OUTPUTDIR=$(CURDIR)/output
STYLEDIR=../dissertation/style
BIBFILE=../citations/abrahamsen.bib
TITLEPG=abrahamsen-proposal-title-page.pdf

help:
	@echo ' 																			'
	@echo 'Makefile for the Markdown thesis       '
	@echo '                                       '
	@echo 'Usage:                                 '
	@echo '   make pdf		generate a .pdf file  	'
	@echo ' 																	  	'

pdf:
	pandoc "$(INFILE).md" \
	-o "$(OUTPUTDIR)/tmp.pdf" \
	--template="$(STYLEDIR)/template.tex" \
	--filter pandoc-include \
	--filter pandoc-fignos \
	--filter pandoc-tablenos \
	--filter pandoc-citeproc \
	--from=markdown+table_captions \
	--latex-engine=xelatex; \
	pdfjoin --outfile "$(OUTPUTDIR)/$(OUTFILE).pdf" "$(TITLEPG)" "$(OUTPUTDIR)/tmp.pdf"; \
	rm "$(OUTPUTDIR)/tmp.pdf"; \
	open "$(OUTPUTDIR)/$(OUTFILE).pdf";

# tex:
# 	pandoc "$(INPUTDIR)"/*.md \
# 	-o "$(OUTPUTDIR)/$(OUTFILE).tex" \
# 	--template="$(STYLEDIR)/template.tex" \
# 	--filter pandoc-include \
# 	--filter pandoc-fignos \
# 	--filter pandoc-tablenos \
# 	--filter pandoc-citeproc \
# 	--from=markdown+table_captions \
# 	--latex-engine=xelatex; \
# 	open "$(OUTPUTDIR)/$(OUTFILE).tex"

# docx:
# 	pandoc "$(INPUTDIR)"/*.md \
# 	-o "$(OUTPUTDIR)/$(OUTFILE).docx" \
# 	--reference-docx="$(STYLEDIR)/reference.docx" \
# 	--filter pandoc-include \
# 	--filter pandoc-fignos \
# 	--filter pandoc-tablenos \
# 	--filter pandoc-citeproc \
# 	--from=markdown+table_captions \
# 	--latex-engine=xelatex; \
# 	open "$(OUTPUTDIR)/$(OUTFILE).docx"
#
# odt:
# 	pandoc "$(INPUTDIR)"/*.md \
# 	-o "$(OUTPUTDIR)/$(OUTFILE).odt" \
# 	--reference-odt="$(STYLEDIR)/reference.odt" \
# 	--filter pandoc-include \
# 	--filter pandoc-fignos \
# 	--filter pandoc-tablenos \
# 	--filter pandoc-citeproc \
# 	--from=markdown+table_captions \
# 	--latex-engine=xelatex; \
# 	open "$(OUTPUTDIR)/$(OUTFILE).odt"

.PHONY: help pdf docx html tex
