ifndef KBE_ROOT
export KBE_ROOT := $(subst /kbe/src/lib/dependencies/curl,,$(CURDIR))
endif

all:: kbemake

CONFIG_ARGS =

ifneq ("$(wildcard /usr/lib/x86_64-linux-gnu/libssl.a)", "")
	CONFIG_ARGS = --with-ssl
	
else
	CONFIG_ARGS = --with-ssl=$(KBE_ROOT)/kbe/src/lib/dependencies/openssl
endif

kbemake:
	@chmod -R 755 .
	./buildconf
	./configure $(CONFIG_ARGS) --disable-shared --enable-static --disable-ldap --disable-sspi --without-librtmp --disable-ftp --disable-file --disable-dict --disable-telnet --disable-tftp --disable-rtsp --disable-pop3 --disable-imap --disable-smtp --disable-gopher --disable-smb --without-libidn
	@cp -f "$(KBE_ROOT)/kbe/src/lib/dependencies/curl/kbe/Makefile.kbe" "$(KBE_ROOT)/kbe/src/lib/dependencies/curl/src/Makefile" 
	@make
	@cp -f "$(KBE_ROOT)/kbe/src/lib/dependencies/curl/lib/.libs/libcurl.a" "$(KBE_ROOT)/kbe/src/libs/" 

.PHONY: clean

clean::
	echo "clean"
