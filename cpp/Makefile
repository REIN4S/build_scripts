SRC= $(wildcard *.cpp)
EXE= $(SRC:.cpp=.exe)

TEST_CASE= $(wildcard *.output)
TEST_NUMBER= $(TEST_CASE:.output=)

all: $(EXE)
	@echo "Output is $(EXE)."
	
%.exe: %.cpp
	@echo "[Compling] $< to $@"
	@g++ -o $@ $<
	@echo "[Compile End]"
clean:
	@rm $(EXE)
	
check: $(TEST_NUMBER)
	@echo "Check Done: [$(TEST_NUMBER)]"

$(TEST_NUMBER):
	@echo "[$@.output <--> $@.input]"
	@bash -c "diff --ignore-all-space <(cat $@.output) <(cat $@.input | ./$(word 1,$(EXE))) "

TEST_OUTPUT=aaa.output
TEST_INPUT=aaa.input
test:
	bash -c "diff --ignore-all-space <(cat ${TEST_OUTPUT}) <(cat ${TEST_INPUT} | ./$(word 1,$(EXE))) "
