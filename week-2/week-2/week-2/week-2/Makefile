SHELL               := /bin/bash
LATEX_COMPILER			?= latexmk
HTML_CONVERTER 			?= pdf2htmlEX
WEEKS          			?= $(shell ls -d week-*)

help:
	@$(LATEX_COMPILER) --help

.PHONY: help Makefile

clean:
	git clean -x -f
	rm -rf _minted*

html: $(WEEKS)
	for BUILDDIR in $(WEEKS);\
		do \
			echo "Building ----> $${BUILDDIR}"; \
			$(LATEX_COMPILER) -pdf -jobname="$${BUILDDIR}/$${BUILDDIR}" -shell-escape $${BUILDDIR}/$${BUILDDIR}; \
			$(HTML_CONVERTER) --zoom 1.5 "$${BUILDDIR}/$${BUILDDIR}.pdf"&& mv $${BUILDDIR}.html $${BUILDDIR};\
		done
