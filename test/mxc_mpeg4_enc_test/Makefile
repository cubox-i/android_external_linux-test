#
# Setup the proper directories for make.rules to function
#
OBJDIR=$(TOPDIR)/platform/$(PLATFORM)/$(MODULE_NAME)
CFLAGS += -I . -lpthread

# list of platforms which did not want this test case
EXCLUDE_LIST:="IMX21ADS IMX27ADS MXC27530EVB MXC91131EVB MXC30031ADS MXC30020EVB"

ifeq (,$(findstring $(PLATFORM), $(EXCLUDE_LIST)))
ifeq "$(PLATFORM)" "MXC30030EVB"
LIBS = $(TOPDIR)/test/$(MODULE_NAME)/libmpeg4enc_cif.a
EXES = $(OBJDIR)/cam2mpeg4_cif.out
OBJS = $(OBJDIR)/cam2mpeg4_cif.o
SCRIPTS = $(OBJDIR)/autorun-hantro.sh
else
LIBS = $(TOPDIR)/test/$(MODULE_NAME)/libmpeg4enc_vga.a
EXES = $(OBJDIR)/cam2mpeg4_vga.out
OBJS = $(OBJDIR)/cam2mpeg4_vga.o
SCRIPTS = $(OBJDIR)/autorun-hantro.sh
endif
endif

all: $(EXES) $(SCRIPTS)
	@mv $(EXES) $(OBJDIR)/cam2mpeg4.out

.PHONY: clean
clean:
	rm -f $(EXES) $(OBJS) $(SCRIPTS)

$(EXES): $(LIBS)

#
# include the Rules
#
include $(TOPDIR)/test/make.rules

#include $(EXES:.out=.d)