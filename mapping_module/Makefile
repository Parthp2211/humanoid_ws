CC=g++
INC=include
SRC=src
OBJ=obj
LIB=lib

.PHONY: all clean realclean

HDRS=$(shell ls $(INC)/*.hpp)
all: test

test: $(OBJ)/test.o $(LIB)/libgpfmap.so
	$(CC) -o $@ -I$(INC) $< -L$(LIB) -lgpfmap -lm

$(OBJ)/test.o: test.cpp $(HDRS)
	$(CC) -DTR -c -I$(INC) $< -o $@

$(OBJ)/%.o: $(SRC)/%.cpp $(INC)/%.hpp
	$(CC) -fPIC -c -I$(INC) $< -o $@

$(LIB)/libgpfmap.so: $(OBJ)/vect.o $(OBJ)/obstacle.o $(OBJ)/functions.o	$(OBJ)/field.o #Others have to be added similarly before compilation.
	$(CC) -shared -o $@ $^ -lm

clean:
	$(RM) $(OBJ)/*.o $(LIB)/libgpfmap.so

realclean: clean
	$(RM) test


