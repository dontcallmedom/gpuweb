.PHONY: all clean

all: index.html grammar/grammar.js

clean:
	rm -f index.html index.pre.html grammar/grammar.js

index.pre.html: index.bs
	DIE_ON=everything bash ../tools/invoke-bikeshed.sh index.pre.html index.bs

index.html: index.pre.html
	bash ../tools/add-git-head-to-bikeshed-header.sh index.pre.html > index.html

grammar/grammar.js: index.bs extract-grammar.py
	python3 ./extract-grammar.py index.bs grammar/grammar.js
