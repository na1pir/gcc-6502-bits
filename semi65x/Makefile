CXX :=		g++ -DSEMI65X
CFLAGS =	-g -O3 -Wall $(INCLUDE)
CXXFLAGS =	-g -O3 -Wall $(INCLUDE)
INCLUDE :=
LIBPATHS :=
LD :=		$(CXX)

OBJS :=		semi65x.o 6502core.o

TARGET :=	semi65x

.PHONY:	.depend

all:	$(TARGET)

clean:
	rm -f *.o $(TARGET)

cleaner: clean
	rm -f *.d

$(TARGET):	$(OBJS)
	$(CXX) $(LIBPATHS) $(OBJS) -o $@

%.o:	%.cpp
	$(CXX) $(CXXFLAGS) $(INCLUDE) -c $< -o $@

%.o:	%.c
	$(CC) $(CFLAGS) $(INCLUDE) -c $< -o $@

%.d:	%.cpp
	$(CXX) $(CXXFLAGS) $(INCLUDE) -MM $< | ./dirify.sh "$@" > "$@"

%.d:	%.c
	$(CC) $(CFLAGS) $(INCLUDE) -MM $< | ./dirify.sh "$@" > "$@"

ifneq ($(MAKECMDGOALS),clean)
ifneq ($(MAKECMDGOALS),cleaner)
include $(OBJS:.o=.d)
endif
endif
