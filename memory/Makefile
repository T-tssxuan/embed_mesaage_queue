objects := $(patsubst %.c, %.o, $(wildcard *.c))
CC := cc

memory: $(objects)
	$(CC) -o $@ $(objects)
test.o: test.c test.h memory_manage.o memory_log.o
	$(CC) -c $<
memory_manage.o: memory_manage.c memory_manage.h memory_basic.h memory_log.o bst.o \
	memory.o
	$(CC) -c $<
memory.o: memory.c memory.h memory_basic.h memory_log.o bst.o
	$(CC) -c $<
bst.o: bst.c bst.h
	$(CC) -c $<
memory_log.o: memory_log.c memory_log.h
	$(CC) -c $<

.PHONY: clean lib
clean:
	rm $(objects)
lib: $(objects)
	ar rvs memory.a $(filter-out test.o,$(objects))
