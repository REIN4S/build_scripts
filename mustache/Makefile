TMPL2HTML=mustache
TMPL=$(wildcard */*.mustache)
DATA=$(TMPL:.mustache=.json)
HTML=$(TMPL:.mustache=.html)
PARTIAL_DIR=../

all: $(HTML)

%.html: %.mustache %.json
	$(TMPL2HTML) $*.json $*.mustache $(PARTIAL_DIR) > $@

%.html: %.mustache
	$(TMPL2HTML) $*.mustache > $@

clean:
	rm -rf $(HTML)
