TEX=platex
DVIPDF=dvipdfmx
#DVIPDFFLAGS=-pa4
DVIPS=dvips
PDF2PS=pdf2ps
PAPERSIZE=b5
PAPERSIZE_PRINT=b4

PREFIX=LuaLua
SRC_PREFIX=main
TEXF=${SRC_PREFIX}.tex
DVI=${SRC_PREFIX}.dvi
PS=${SRC_PREFIX}.ps
PDF=../${PREFIX}.pdf
BOOK=../${PREFIX}-print.pdf
TEXFILES=main.tex imple.tex totp.tex nginx-lua.tex intro.tex colophon.tex cover.tex 

.suffix: .tex .dvi

#all: ${DVI}
all: book

pdf: ${PDF}

ps: ${PS}

book: ${BOOK}


${DVI}: ${TEXFILES} ${PSFILES}
	${TEX} main.tex
	${TEX} main.tex

${PDF}: ${DVI} 
	${DVIPDF} -f ipa.map -p ${PAPERSIZE} -o ${PDF} ${DVI}

${PS}: ${PDF} 
	${PDF2PS} ${PDF} ${PS}

${BOOK}: ${PS}
	psbook ${PS} | psnup -2 -P ${PAPERSIZE}| ps2ps -sPAPERSIZE=${PAPERSIZE_PRINT} - - | ps2pdf - ${BOOK}


clean:
	rm -f ${DVI} ${PDF} ${PS} ${BOOK} *.log *.aux

