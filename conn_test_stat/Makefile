# �޸����ɿ�ִ���ļ�������
EXECUTABLE := conn_test_stat
# �޸�LIBS����������Ҫ���ӵĿ⣬�Կո�ָ������� LIBS := pthread rt ssl
LIBS :=# Now alter any implicit rules�� variables if you like, e.g.:
#
# �޸�CC���ı������
CC := g++
# �޸ı���ѡ��
CFLAGS := -O2 -Wall
CXXFLAGS := $(CFLAGS)
RM-F := rm -f
LDFLAGES := 

# You shouldn��t need to change anything below this point.
#
#ƥ����ļ���Ĭ�Ͻ�ƥ�䵱ǰĿ¼�����������޸�
#����������Ҫ������Ŀ¼������$(wildcard test/*.cpp)
#��������֧�ֵĺ�׺�ļ�������$(wildcard *.cc)
SOURCE := $(wildcard *.c) $(wildcard *.cpp)
OBJS := $(patsubst %.c,%.o,$(patsubst %.cpp,%.o,$(SOURCE)))
DEPS := $(patsubst %.o,%.d,$(OBJS))
MISSING_DEPS := $(filter-out $(wildcard $(DEPS)),$(DEPS))
MISSING_DEPS_SOURCES := $(wildcard $(patsubst %.d,%.c,$(MISSING_DEPS)) \
$(patsubst %.d,%.cc,$(MISSING_DEPS)))
CPPFLAGS += -MD
 
.PHONY : all deps objs clean veryclean rebuild

all : $(EXECUTABLE)

deps : $(DEPS)

objs : $(OBJS)

clean :
	@$(RM-F) *.o
	@$(RM-F) *.d
	@$(RM-F) $(EXECUTABLE)

rebuild: clean all

ifneq ($(MISSING_DEPS),)
$(MISSING_DEPS) :
	$(RM-F) $(patsubst %.d,%.o,$@)
endif

$(EXECUTABLE) : $(OBJS)
	$(CC) -o $(EXECUTABLE) $(LDFLAGES) $(OBJS) $(addprefix -l,$(LIBS))