
ACLOCAL_AMFLAGS = -I m4

if WANT_JANSSON
JANSSON_INCLUDES= -I$(top_srcdir)/compat/jansson
else
JANSSON_INCLUDES=
endif

EXTRA_DIST	= example-cfg.json nomacro.pl

SUBDIRS		= compat

hodlminer_CPPFLAGS	= $(PTHREAD_FLAGS) -march=native -Ofast -flto -fuse-linker-plugin -std=gnu11 $(JANSSON_INCLUDES)

bin_PROGRAMS	= hodlminer

dist_man_MANS	= hodlminer.1

hodlminer_SOURCES	= elist.h miner.h compat.h \
		  	  sha2.c cpu-miner.c util.c hodl.c aes.c

hodlminer_LDFLAGS	= $(PTHREAD_FLAGS)
hodlminer_LDADD		= @LIBCURL_LIBS@ @OPENSSL_LIBS@ @JANSSON_LIBS@ @PTHREAD_LIBS@ @WS2_LIBS@
hodlminer_CPPFLAGS	+= @LIBCURL_CPPFLAGS@ @LIBCURL_CFLAGS@

if USE_BUILD_NUMBER
hodlminer_CFLAGS	= -DBUILD_NUMBER=\"$(BUILD_NUMBER)\"
endif

if HAVE_WINDOWS
hodlminer_LDFLAGS += -all-static
endif
