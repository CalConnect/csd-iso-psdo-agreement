SRC  := $(wildcard csd-*.adoc)
XML  := $(patsubst %.adoc,%.xml,$(SRC))
PDF  := $(patsubst %.adoc,%.pdf,$(SRC))
HTML := $(patsubst %.adoc,%.html,$(SRC))
DOC  := $(patsubst %.adoc,%.doc,$(SRC))

SHELL := /bin/bash

all: $(HTML) $(XML) $(PDF)

clean:
	rm -f $(HTML) $(XML) $(PDF) Gemfile Gemfile.lock

bundle:	Gemfile Gemfile.lock
	bundle

Gemfile Gemfile.lock:
	ln -s ../common/$@ .

%.xml %.html %.pdf %.doc: %.adoc bundle
	bundle exec metanorma -t csd -x xml,html,pdf,doc $<

html: $(HTML)

open:
	open $(HTML)

.PHONY: bundle all open
