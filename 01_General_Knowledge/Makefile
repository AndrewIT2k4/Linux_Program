CC = gcc
CFLAGS = -fPIC -Iinc
SRC = $(wildcard src/*.c)
OBJ = $(SRC:src/%.c=obj/%.o)

BIN = bin/exam
LIB = lib/shared_lib/libcalc.so

# Tạo thư mục cần thiết
$(shell mkdir -p obj bin lib/shared_lib)

# Mục tiêu chính
all: $(LIB) $(BIN)

# Biên dịch file .c thành .o
obj/%.o: src/%.c inc/*.h
	$(CC) $(CFLAGS) -c $< -o $@

# Tạo thư viện động
$(LIB): $(OBJ)
	$(CC) -shared $^ -o $@

# Liên kết chương trình
$(BIN): obj/main.o $(LIB)
	$(CC) $^ -Llib/shared_lib -lcalc -o $@

# Dọn dẹp
clean:
	rm -rf obj bin lib

.PHONY: all clean
