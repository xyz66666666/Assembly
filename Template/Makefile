AS = as
LD = ld

CFLAGS = -gstabs

#源码目录
SRCS_DIRS += src/*.s

#编译环境
objs_dir=objs
vpath %.s src
source = $(wildcard *.s $(SRCS_DIRS) $(notdir $(wildcard *.s)))
objs = $(source:%.s=$(objs_dir)/%.o)

TARGET=template
.PHONY: all clean

all: $(TARGET)
$(TARGET) : $(objs)
	@echo -e "\033[31mGenerate the ELF file: $(TARGET) \033[0m"
	ld $(LDFLAGS) -o $@ $^ 
	mv $(TARGET) bin
$(objs): $(objs_dir)/%.o : %.s
	@echo -e "\033[31mCompile the object file: $<\033[0m"
	$(AS) $(CFLAGS) -o $@ $<
clean:
	@echo -e "\033[31mDelete compiled file \033[0m"
	rm -rf objs/src/*.o bin/*
