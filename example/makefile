CXXFLAGS = -Wall -O3
CFLAGS = -Wall -O3

OBJ_DIR  := obj
CPP_OBJ_DIR  := $(OBJ_DIR)/cpp
C_OBJ_DIR  := $(OBJ_DIR)/c

BIN_DIR  := bin
TARGET = myprog
INCLUDE = -Iinclude/
LDFLAGS = -lm 

CPP_SRC     :=$(wildcard src/*.cpp)
CPP_OBJECTS := $(CPP_SRC:%.cpp=$(CPP_OBJ_DIR)/%.o)

C_SRC     	:=$(wildcard src/*.c)
C_OBJECTS := $(C_SRC:%.c=$(C_OBJ_DIR)/%.o)

all: $(BIN_DIR)/$(TARGET)

$(CPP_OBJ_DIR)/%.o: %.cpp
	@mkdir -p $(@D)
	$(CXX) $(CXXFLAGS) $(INCLUDE) -o $@ -c $<

$(C_OBJ_DIR)/%.o: %.c
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) $(INCLUDE) -o $@ -c $<

$(BIN_DIR)/$(TARGET): $(CPP_OBJECTS) $(C_OBJECTS)
	@mkdir -p $(@D)
	$(CXX) $(CXXFLAGS) $(INCLUDE) $(LDFLAGS) -o $(BIN_DIR)/$(TARGET) $(CPP_OBJECTS) $(C_OBJECTS)

.PHONY: clean  all


clean:
	-@rm -rvf $(CPP_OBJ_DIR)/*
	-@rm -rvf $(C_OBJ_DIR)/*
	-@rm -rvf $(BIN_DIR)/*
