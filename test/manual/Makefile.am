check_PROGRAMS = client userlist $(OPTIONAL_TESTS_SEARCH) $(OPTIONAL_TESTS_VOICE7) $(OPTIONAL_TESTS_MANUAL_GLIBC)
EXTRA_PROGRAMS = client userlist search voice7 dcc7

CFLAGS = -DGG_IGNORE_DEPRECATED
AM_LDFLAGS = -no-install

dcc7_CFLAGS = -Wall
dcc7_LDADD = $(top_builddir)/src/libgadu.la
dcc7_SOURCES = dcc7.c userconfig.c userconfig.h

client_LDADD = $(top_builddir)/src/libgadu.la
client_SOURCES = client.c userconfig.c userconfig.h

userlist_LDADD = $(top_builddir)/src/libgadu.la
userlist_SOURCES = userlist.c userconfig.c userconfig.h

search_SOURCES = search.c lib/base64.c lib/base64.h ../../config.h lib/hmac.c lib/hmac.h lib/http.c lib/http.h lib/oauth.c lib/oauth.h lib/oauth_parameter.c lib/oauth_parameter.h lib/sha1.c lib/sha1.h lib/urlencode.c lib/urlencode.h lib/xml.c lib/xml.h
search_CFLAGS = -Wall -DHAVE_OPENSSL
search_LDADD = -lcurl -lexpat -lssl -lcrypto

voice7_CFLAGS = -Wall -DHAVE_SPEEX -DHAVE_GSM
voice7_LDADD = $(top_builddir)/src/libgadu.la -lgsm -lspeex

SUBDIRS = lib

clean-local:
	rm -f *.log *-valgrind

check-local:      $(check_PROGRAMS)
	for i in $(check_PROGRAMS); do ln -sf ../valgrind $${i}-valgrind; done

