THEMES= \
	Atlanta \
	ClearlooksRe \
	Dopple \
	Dopple-Left \
	DustBlue \
	Esco \
	eOS \
	Gorilla \
	Motif \
	Raleigh \
	Spidey \
	Spidey-Left \
	Splint \
	Splint-Left \
	WinMe

THEME_DIR=$(datadir)/themes
THEME_SUBDIR=metacity-1

EXTRA_DIST= \
	meson.build \
	Atlanta/meson.build \
	ClearlooksRe/meson.build \
	Dopple/meson.build \
	Dopple-Left/meson.build \
	DustBlue/meson.build \
	eOS/meson.build \
	Esco/meson.build \
	Gorilla/meson.build \
	Motif/meson.build \
	Raleigh/meson.build \
	Spidey/meson.build \
	Spidey-Left/meson.build \
	Splint/meson.build \
	Splint-Left/meson.build \
	WinMe/meson.build

install-data-local:
	$(mkinstalldirs) $(DESTDIR)$(THEME_DIR); \
	for THEME in $(THEMES); do \
		echo '-- Installing theme '$$THEME; \
		$(mkinstalldirs) $(DESTDIR)$(THEME_DIR)/$$THEME; \
		$(mkinstalldirs) $(DESTDIR)$(THEME_DIR)/$$THEME/$(THEME_SUBDIR); \
		(installfiles=`find $(srcdir)/$$THEME -name "*.png" -o -name "*.xml"`; \
		 for i in $$installfiles; do \
			echo '-- Installing '$$i ; \
		    	$(INSTALL_DATA) $$i $(DESTDIR)$(THEME_DIR)/$$THEME/$(THEME_SUBDIR) ; \
	  	 done) \
	done

uninstall-local:
	for THEME in $(THEMES); do \
		echo '-- Uninstalling theme '$$THEME; \
		(uninstallfiles=`find $(srcdir)/$$THEME -name "*.png" -o -name "*.xml"`; \
		 for i in $$uninstallfiles; do \
					i=`basename $$i`; \
			echo '-- Removing '$$i ; \
				rm -f $(DESTDIR)$(THEME_DIR)/$$THEME/$(THEME_SUBDIR)/$$i ; \
		done); \
		rmdir $(DESTDIR)$(THEME_DIR)/$$THEME/$(THEME_SUBDIR) || :; \
		rmdir $(DESTDIR)$(THEME_DIR)/$$THEME || :; \
	done
	-rmdir $(DESTDIR)$(THEME_DIR)

dist-hook:
	mkdir $(distdir)/themes; \
	for THEME in $(THEMES); do \
		echo '-- Disting theme '$$THEME; \
		mkdir $(distdir)/$$THEME; \
		(installfiles=`find $(srcdir)/$$THEME -name "*.png" -o -name "*.xml"`; \
		 for i in $$installfiles; do \
			echo '-- Disting '$$i ; \
				cp $$i $(distdir)/$$THEME; \
		done) \
	done

-include $(top_srcdir)/git.mk
