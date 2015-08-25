# Copyright (c) 2008-2009 solvethis
# Copyright (c) 2010-2011 Casper Ti. Vector
# Public domain.

# ����������ļ����ļ�������������չ����
JOBNAME = pkuthss
# ���������ֵ����Ϊ latex��pdflatex �� xelatex��
LATEX = latex
BIBTEX = bibtex
GBK2UNI = gbk2uni
DVIPDF = dvipdfmx

# ����� LaTeX ���룬��ʹ�� dvipdfmx �� dvi ת�� pdf��
ifeq ($(LATEX), latex)
	DODVIPDF = $(DVIPDF) $(JOBNAME)
endif

# ʹ�� GBK ����� pdflatex ���뷽ʽʱ��������Ҫʹ�� gbk2uni ת�� .out
# �ļ����룬�Է���ǩ���롣
ifeq ($(LATEX), pdflatex)
	#DOGBK2UNI = $(GBK2UNI) $(JOBNAME)
endif

# ������ Windows ���������� UNIX ������
# ����Ǻ��ߣ��� GNU make �����Լ�⵽�Ѿ����� PATH ����������
ifdef PATH
	MAKE = make
	RM = rm -f
else
	MAKE = mingw32-make
	RM = del
endif

all: img doc

img:
	cd img && $(MAKE)

img-clean:
	cd img && $(MAKE) clean

doc:
	$(LATEX) $(JOBNAME)
	$(BIBTEX) $(JOBNAME)
	$(DOGBK2UNI)
	$(LATEX) $(JOBNAME)
	$(LATEX) $(JOBNAME)
	$(DODVIPDF)

clear:
	$(RM) $(JOBNAME).log $(JOBNAME).aux $(JOBNAME).bbl $(JOBNAME).blg\
		$(JOBNAME).toc $(JOBNAME).lof $(JOBNAME).lot $(JOBNAME).out\
		$(JOBNAME).dvi missfont.log
	$(RM) chap/*.aux

clean: clear img-clean
	$(RM) $(JOBNAME).pdf

.PHONY: img img-clean clear clean
