#	$Id: Makefile,v 1.14 2012/01/31 21:52:47 pooka Exp $
#

PAPER=	rumpkernel

SUBS=	introduction.tex
SUBS+=	concept.tex
SUBS+=	implementation.tex
SUBS+=	evaluation.tex
SUBS+=	related.tex
SUBS+=	conclusions.tex

all: ${PAPER}.ps
	
${PAPER}.ps: ${PAPER}.tex man.tex thebibs.bib
	rm -f inputs.tex ${PAPER}.pdf

	for s in ${SUBS}; do \
		echo \\input{$${s}} >> inputs.tex ; \
	done

	pdflatex ${PAPER}.tex
	bibtex ${PAPER}
	makeindex ${PAPER}.nlo -s nomencl.ist -o ${PAPER}.nls
	pdflatex ${PAPER}.tex

man.tex: manpages/makemanappendix.sh
	(cd manpages ; sh makemanappendix.sh) > man.tex

clean:
	rm -f dummy *aux *bbl *blg *dvi *log *.ps *lof *lot *.toc *.ilg *.nls *.nlo ${PAPER}.pdf *.mof inputs.tex man.tex ${PAPER}.out

cleandir: clean
