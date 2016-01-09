CXX = g++
CC = g++
CXXFLAGS = -I../chapter05

all:		wc xref grammar

wc.o:		wc.cc

wc:		wc.o

#xref.o:		xref.cc ../chapter05/split.h
xref.o:		xref.cc
#若CXXFLAGS 包含了索引文件目录, 则上面split.h 可以不用写

xref:		xref.o split.o

grammar.o:	grammar.cc ../chapter05/split.h

split.o:	../chapter06/split.cc ../chapter05/split.h
	$(CXX) $(CXXFLAGS) -c ../chapter06/split.cc
#因为split.cc split.h 都不在当前目录,所以要多加一句 $(CXX) $... 

grammar:	grammar.o split.o

test:		all
	./wc < wc.cc
	./xref < wc.cc
	./grammar <../data/grammar_input

clobber:
	rm -f *.o *.exe core wc xref grammar
