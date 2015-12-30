.phony: build clean deep-clean

LECTURES :=
LECTURES += 01_introduction

PDF_LECTURES := $(patsubst %,ann2015_l%.pdf, $(LECTURES))
TEX_LECTURES := $(patsubst %.pdf,%.tex, $(PDF_LECTURES))

NOISE := *.nav *.log *.out *.snm *.toc *.aux *~ *.blg *.bbl *.vrb _minted*

build: $(PDF_LECTURES)
	rm -rf $(NOISE)

$(PDF_LECTURES): ann2015_%.pdf: ann2015_%.tex
	pdflatex -shell-escape $+
	bibtex $(subst .pdf,,$@)
	pdflatex -shell-escape $+
	pdflatex -shell-escape $+

clean:
	rm -rf $(NOISE)

deep-clean: clean
	rm -f $(PDF_LECTURES)
