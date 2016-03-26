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
	fragment/copyright.tex

data=


# Cible primaire
rapport.pdf: ${sources} data
	${pdflatex} -interaction=nonstopmode "\input" rapport.tex
	${pdflatex} -interaction=nonstopmode "\input" rapport.tex


# Fichiers de donnée
mandel=../Resultats/mandel
convol=../Resultats/convol


# Génération des fichiers de donnée
data: ${data}
	${sed} -i 's/\([0-9]\),\([0.9]\)*/\1\.\2/g' ${data} # Conversion du point décimal


clean:
	-rm -f ${data}

# Autres cibles
.PHONY: pdf data clean mandel convol
