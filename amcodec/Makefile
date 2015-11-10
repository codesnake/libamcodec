M_PREFIX=$(PREFIX)

TARGET=libamcodec.so

TARGET_OBJS=\
        codec/codec_ctrl.c \
	codec/codec_h_ctrl.c \
	codec/codec_msg.c \
	audio_ctl/audio_ctrl.c
#	amsub_ctl/amsub_ctr.c


INSTALL_DIR=${M_PREFIX}/lib

HEADERS_DIR=$(M_PREFIX)/amcodec/include

LDFLAGS += -O2  -L$(PREFIX)/lib -lamadec -lm -lc -shared

CFLAGS+=-O2 -I$(shell pwd)/include -I$(shell pwd)/audio_ctl -I$(shell pwd)/amsub_ctl -I$(shell pwd)/codec -I$(shell pwd)/../amadec/include -I$(shell pwd)/../amavutils/include -fPIC

export CC CFLAGS

all: $(TARGET)

$(TARGET): $(TARGET_OBJS)
	$(CC) $(CFLAGS) $(TARGET_OBJS:%.o=%.c) $(LDFLAGS) -o $@

install:$(TARGET)
	install -m 555 ${TARGET} $(INSTALL_DIR)
	mkdir -p $(HEADERS_DIR)
	cp -rf $(shell pwd)/include/*  $(HEADERS_DIR)/

clean:
	rm -rf *.o
