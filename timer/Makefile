objects := $(patsubst %.c, %.o, $(wildcard *.c))
CC := cc

timer: $(objects) memory.a common.a
	$(CC) -o $@ $(objects) memory.a common.a
test.o: test.c test.h timer.h
	$(CC) -c $<
timer_core.o: timer_core.c timer_core.h timer_basic.h
	$(CC) -c $<
timer.o: timer.c timer.h timer_basic.h
	$(CC) -c $<
timer_log.o: timer_log.c timer_log.h
	$(CC) -c $<

.PHONY: clean lib memory.a common.a
memory.a:
	cp ../memory/memory.a .
common.a:
	cp ../common/common.a .
clean:
	rm $(objects)
	rm memory.a
	rm common.a
lib: $(objects)
	ar rvs timer.a $(filter-out test.o,$(objects))
