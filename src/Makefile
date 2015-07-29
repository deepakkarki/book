
PAPER=	rumpkernel
DATE:=	$(shell git show -s --format="%ci" HEAD | sed 's/-//g;s/ .*//')
TARGET=	${PAPER}-PRELIMINARY-${DATE}

SUBS=	introduction.tex
SUBS+=	concept.tex
SUBS+=	implementation.tex
SUBS+=	evaluation.tex
SUBS+=	related.tex
SUBS+=	history.tex
SUBS+=	conclusions.tex

all: ${PAPER}.tex thebibs.bib
	rm -f inputs.tex ${PAPER}.pdf

	for s in ${SUBS}; do \
		echo \\input{$${s}} >> inputs.tex ; \
	done

	pdflatex ${PAPER}.tex
	bibtex ${PAPER}
	makeindex ${PAPER}.nlo -s nomencl.ist -o ${PAPER}.nls
	pdflatex ${PAPER}.tex
	mv ${PAPER}.pdf ${TARGET}.pdf

clean:
	rm -f dummy *aux *bbl *blg *dvi *log *.ps *lof *lot *.toc *.ilg *.nls *.nlo ${PAPER}.pdf ${TARGET}.pdf *.mof inputs.tex ${PAPER}.out

cleandir: clean
