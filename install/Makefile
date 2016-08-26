VERSION := 9.4.1
WIXBIN := $(shell cygpath "$(WIX)bin/")
WIXEXTENSIONS := -ext WixBalExtension -ext WixUIExtension

install.exe: install.wixobj cs.msi
	"$(WIXBIN)light" -nologo $(WIXEXTENSIONS) install.wixobj -out "$@"

cs.msi: main.wixobj a6nt.wixobj examples.wixobj
	"$(WIXBIN)light" -nologo $(WIXEXTENSIONS) main.wixobj a6nt.wixobj examples.wixobj -out "$@"

%.wixobj: %.wxs
	"$(WIXBIN)candle" -nologo -dVersion="$(VERSION)" $(WIXEXTENSIONS) $<

clean:
	-rm -f install.exe cs.msi *.wixobj *.wixpdb
