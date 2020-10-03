# BUILD
BE_SRC=$(wildcard ./*.nim)
BE_EXE=$(BE_SRC:.nim=.exe)

FE_SRC=$(wildcard ./module/*.nim)
FE_JS=$(FE_SRC:.nim=.js)

RES_SRC:=$(wildcard ./resource/*.*)
OUT_SRC=$(wildcard ./resource/*.ignore)
RES_SRC:=$(filter-out $(OUT_SRC), $(RES_SRC))

# TEST
BE_UNIT_TEST_SRC=$(wildcard ./tests/UnitTests/BE/*.nim)
BE_UNIT_TEST=$(BE_UNIT_TEST_SRC:.nim=.exe)
FE_UNIT_TESS_SRC=$(wildcard ./tests/UnitTests/FE/*.nim)
FE_UNIT_TEST=$(FE_UNIT_TESS_SRC:.nim=.js)

INT_TEST_SRC=$(wildcard ./tests/Integration/*.nim)
INT_TEST=$(INT_TEST_SRC:.nim=.exe)

all: FE BE
	@mkdir -p ./static
	@cp $(FE_JS) ./static/
	@cp $(RES_SRC) ./static/
	@$(BE_EXE)

BE:
	@nim c -d:ssl --out:./$(BE_EXE) $(BE_SRC)

FE:
	@nim js --out:$(FE_JS) $(FE_SRC)

check: $(BE_UNIT_TEST) $(FE_UNIT_TEST)
	for exe in $(BE_UNIT_TEST); \
	do	\
		$$exe; \
	done;
	@echo "Test Done: [$(BE_UNIT_TEST)]"
	
	for exe in $(FE_UNIT_TEST); \
	do	\
		node $$exe; \
	done;
	@echo "Test Done: [$(FE_UNIT_TEST)]"

tests/UnitTests/BE/%.exe: tests/UnitTests/BE/%.nim
	@nim c --out:$@ $<

tests/UnitTests/FE/%.js: tests/UnitTests/FE/%.nim
	@nim js --out:$@ -d:nodejs $<

check-int: $(INT_TEST)
	for exe in $(INT_TEST); \
	do \
		$$exe; \
	done;
	@echo "Integration Test Done: [$(INT_TEST)]"

tests/Integration/%.exe: tests/Integration/%.nim
	@nim c --out:$@ $<

clean: test-clean
	@rm -rf $(BE_EXE)
	@rm -rf $(FE_JS)
	@rm -rf ./static
	@rm -rf ./nimcache

test-clean:
	@rm -rf $(BE_UNIT_TEST)
	@rm -rf $(FE_UNIT_TEST)
