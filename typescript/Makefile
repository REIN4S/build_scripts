SRC= $(wildcard *.ts)
OBJ= $(SRC:.ts=.js)
PACKAGE_NAME=dist.js 

all: $(OBJ)
	@echo "Output is $(OBJ)."
	@rm -f $(PACKAGE_NAME)
	@touch $(PACKAGE_NAME)
	@cat $^ >> $(PACKAGE_NAME)
	
%.js: %.ts
	@echo "[Compling] $< to $@"
	@tsc -outFile $@ $<
	@echo "[Compile End]"

clean:
	@rm -f $(PACKAGE_NAME)
	@rm -f $(OBJ)
