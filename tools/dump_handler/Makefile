builddir = .

override CC := $(abs_top)/support/mtlkfront.sh $(CC)
override AM_CFLAGS = -Wall -Wno-multichar -fno-strict-aliasing -Werror -Wno-error=undef
override CFLAGS += -O2 -Wno-multichar
override CFLAGS += -I$(abs_top)
override CFLAGS += -I$(builddir)/.
override CFLAGS += -I$(abs_top)/tools/mttools/shared
override CFLAGS += -I$(abs_top)/tools/shared/
override CFLAGS += -I$(abs_top)/tools/shared/linux/
override CFLAGS += -I$(abs_top)/wireless/shared/
override CFLAGS += -I$(abs_top)/include/config/
override CFLAGS += -I$(abs_top)/tools/rtlogger/shared/
override CFLAGS += -DMTLK_SOURCE_VERSION="\"1.0\"" -DIWLWAV_RTLOG_MAX_DLEVEL=3 -DCPTCFG_IWLWAV_RT_LOGGER_FUNCTIONS
override CFLAGS += -DLOG_LOCAL_OID=MTLKFRONT_WILL_FILL_IT

LD_LIBS =	-L$(abs_top)/tools/mttools/shared/ -lmttools \
		-L$(abs_top)/tools/shared/linux/ -lmtlkc \
		-L$(abs_top)/wireless/shared/ -lmtlkwls

LINK = $(LDFLAGS) $(LD_LIBS) $(LD_LIBS) $(AM_CFLAGS) $(CFLAGS) -o $@

deps =  $(abs_top)/tools/mttools/shared/libmttools.a \
	$(abs_top)/tools/shared/linux/libmtlkc.a \
	$(abs_top)/wireless/shared/libmtlkwls.a

dump_handler_LDADD  = $(abs_top)/tools/mttools/shared/libmttools.a \
		$(abs_top)/tools/shared/linux/libmtlkc.a \
		$(abs_top)/wireless/shared/libmtlkwls.a

objs =  $(abs_top)/tools/shared/argv_parser.o \
	dump_handler.o \
	logmacro_database.o

dump_handler: $(objs)
	$(CC) $(LINK) $(objs) $(dump_handler_LDADD)

all: dump_handler

clean:
	rm -f $(objs) dump_handler 

export logger_origin_name = dump_handler
export logger_binary_name = dump_handler.o
export logger_origin_id = 6
