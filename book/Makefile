# Makefile for Elementary Category Theory
#
# Requires: pdflatex (TeX Live or MiKTeX) and the packages listed in preamble.tex
# Recommended: latexmk for automatic re-runs

MAIN = main
BUILD = build

.PHONY: all clean view

all: $(BUILD)/$(MAIN).pdf

$(BUILD)/$(MAIN).pdf: $(MAIN).tex preamble.tex chapters/*.tex | $(BUILD)
	latexmk -pdf -output-directory=$(BUILD) -interaction=nonstopmode $(MAIN).tex

$(BUILD):
	mkdir -p $(BUILD)

# Single-pass build (faster, may need re-run for cross-references)
once: | $(BUILD)
	pdflatex -output-directory=$(BUILD) $(MAIN).tex

clean:
	rm -rf $(BUILD)

view: $(BUILD)/$(MAIN).pdf
	xdg-open $(BUILD)/$(MAIN).pdf 2>/dev/null || open $(BUILD)/$(MAIN).pdf
