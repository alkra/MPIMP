# © Alban Kraus 2016
# École nationale des sciences géographiques
# 6-8 avenue Blaise Pascal - Champs-sur-Marne
# 77455 MARNE-LA-VALLÉE CEDEX 2
#
# TP de Ahmad Audi
#
# Ceci est le makefile du rapport


# Programmes
pdflatex=pdflatex
git=git
sed=sed
line=${sed} -n


# Fichiers sources
sources=rapport.tex \
	fragment/CC-BY.png \
	fragment/logo_ensg.png \
	fragment/titlepage.tex \
	fragment/copyright.tex \
	fragment/Albert-Einstein.jpg \
	fragment/rapport-convol.tex \
	mandelbrot/question-1.tex \
	mandelbrot/question-2.tex \
	mandelbrot/question-3.tex \
	mandelbrot/question-4.tex \
	mandelbrot/question-5.tex


data=data/mandel-seq-taille.csv data/mandel-seq-prof.csv \
	data/mandel-seq-taille-ext.csv \
	data/mandel-stat-taille-1-2.csv data/mandel-stat-prof-1-2.csv \
	data/mandel-stat-proc-1-1000.csv data/mandel-stat-proc-1-5000.csv \
	data/mandel-stat-taille-6-2.csv data/mandel-stat-prof-6-2.csv \
	data/mandel-stat-proc-6-1000.csv data/mandel-stat-proc-6-5000.csv \
	data/mandel-dyn-taille-1-2.csv data/mandel-dyn-prof-1-2.csv \
	data/mandel-dyn-proc-1-1000.csv data/mandel-dyn-proc-1-5000.csv \
	data/mandel-dyn-nblocks-1-1000.csv data/mandel-dyn-nblocks-1-5000.csv \
	data/convol-iter-1-0.csv data/convol-iter-1-2.csv data/convol-iter-1-4.csv \
	data/convol-iter-6-0.csv data/convol-iter-6-2.csv data/convol-iter-6-4.csv \
	data/convol-proc-1-0.csv data/convol-proc-1-4.csv \
	data/convol-proc-6-0.csv data/convol-proc-6-4.csv


# Cible primaire
rapport.pdf: ${sources} data
	${pdflatex} -interaction=nonstopmode "\input" rapport.tex
	${pdflatex} -interaction=nonstopmode "\input" rapport.tex


# Fichiers de donnée
mandel=../Resultats/mandel
convol=../Resultats/convol

../Resultats/%-stat.csv:
	git checkout mpi-static $@
	git reset -q HEAD $@

../Resultats/%-dyn.csv:
	git checkout mpi-dynamic $@
	git reset -q HEAD $@


# Génération des fichiers de donnée
data: ${data}
	${sed} -i 's/\([0-9]\),\([0.9]\)*/\1\.\2/g' ${data} # Conversion du point décimal

# SEQ
data/mandel-seq-taille.csv: ${mandel}-seq.csv
	${line}     '3p' ${mandel}-seq.csv  > $@
	${line}  '5,13p' ${mandel}-seq.csv >> $@
	${line} '13,18p' ${mandel}-seq.csv >> $@

data/mandel-seq-taille-ext.csv: ${mandel}-seq.csv
	${line} '13,21p' ${mandel}-seq.csv > $@

data/mandel-seq-prof.csv: ${mandel}-seq.csv
	${line} '40,58p' ${mandel}-seq.csv > $@


# STAT 1 machine
data/mandel-stat-taille-1-2.csv: ${mandel}-stat.csv
	${line}  '2,15p' ${mandel}-stat.csv > $@

data/mandel-stat-prof-1-2.csv: ${mandel}-stat.csv
	${line} '16,25p' ${mandel}-stat.csv > $@

data/mandel-stat-proc-1-1000.csv: ${mandel}-stat.csv
	${line} '2p;26p;28p;30p;32p;34p;36p;38p' ${mandel}-stat.csv > $@

data/mandel-stat-proc-1-5000.csv: ${mandel}-stat.csv
	${line} '15p;27p;29p;31p;33p;35p;37p;39p' ${mandel}-stat.csv > $@

# STAT 6 machines
data/mandel-stat-taille-6-2.csv: ${mandel}-stat.csv
	${line}  '46,59p' ${mandel}-stat.csv > $@

data/mandel-stat-prof-6-2.csv: ${mandel}-stat.csv
	${line} '60,69p' ${mandel}-stat.csv > $@

data/mandel-stat-proc-6-1000.csv: ${mandel}-stat.csv
	${line} '46p;70p;72p;74p;76p;78p;80p;82p' ${mandel}-stat.csv > $@

data/mandel-stat-proc-6-5000.csv: ${mandel}-stat.csv
	${line} '59p;71p;73p;75p;77p;79p;81p;83p' ${mandel}-stat.csv > $@

# DYN
data/mandel-dyn-taille-1-2.csv: ${mandel}-dyn.csv
	${line}  '40,53p' ${mandel}-dyn.csv > $@

data/mandel-dyn-prof-1-2.csv: ${mandel}-dyn.csv
	${line} '54,63p' ${mandel}-dyn.csv > $@

data/mandel-dyn-proc-1-1000.csv: ${mandel}-dyn.csv
	${line} '40p;64p;66p;68p;70p;72p;74p;76p' ${mandel}-dyn.csv > $@

data/mandel-dyn-proc-1-5000.csv: ${mandel}-dyn.csv
	${line} '53p;65p;67p;69p;71p;73p;75p;77p' ${mandel}-dyn.csv > $@

data/mandel-dyn-nblocks-1-1000.csv: ${mandel}-dyn.csv
	${line} '78p;80p;82p;84p' ${mandel}-dyn.csv > $@

data/mandel-dyn-nblocks-1-5000.csv: ${mandel}-dyn.csv
	${line} '79p;81p;83p;85p' ${mandel}-dyn.csv > $@


# Convol 1 machine

data/convol-iter-1-0.csv: ${convol}-stat.csv
	${line}  '2,11p' ${convol}-stat.csv > $@

data/convol-iter-1-2.csv:  ${convol}-stat.csv
	${line} '12,21p' ${convol}-stat.csv > $@

data/convol-iter-1-4.csv:  ${convol}-stat.csv
	${line} '22,31p' ${convol}-stat.csv > $@

data/convol-proc-1-0.csv: ${convol}-stat.csv
	${line} '32p;34p;36p;38p;40p;42p;44p;46p' ${convol}-stat.csv > $@

data/convol-proc-1-4.csv: ${convol}-stat.csv
	${line} '33p;35p;37p;39p;41p;43p;45p;47p' ${convol}-stat.csv > $@


# Convol 6 machines

data/convol-iter-6-0.csv: ${convol}-stat.csv
	${line} '48,57p' ${convol}-stat.csv > $@

data/convol-iter-6-2.csv:  ${convol}-stat.csv
	${line} '58,67p' ${convol}-stat.csv > $@

data/convol-iter-6-4.csv:  ${convol}-stat.csv
	${line} '68,77p' ${convol}-stat.csv > $@

data/convol-proc-6-0.csv: ${convol}-stat.csv
	${line} '78p;80p;82p;84p;86p;88p;90p;92p' ${convol}-stat.csv > $@

data/convol-proc-6-4.csv: ${convol}-stat.csv
	${line} '79p;81p;83p;85p;87p;89p;91p;93p' ${convol}-stat.csv > $@


clean:
	-rm -f ${data}
	-rm -f ${mandel}-stat* ${mandel}-dyn* \
	${convol}-stat* ${convol}-dyn*

# Autres cibles
.PHONY: pdf data clean mandel convol
