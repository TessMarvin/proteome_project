top_srcdir     = ..
srcdir         = .


SQCLEVEL = 2

ESLDIR = easel

ALIS = 	20aa\
	Caudal_act\
	LuxC\
	M1\
	Patched\
	RRM_1\
	SMC_N\
	XYPPX\
	ecori\
	3box\
	PSE\

# beautification magic stolen from git 
#
QUIET_SUBDIR0 = +${MAKE} -C #space separator after -c
QUIET_SUBDIR1 = 
ifndef V
	QUIET_CC      = @echo '    ' CC $@;
	QUIET_GEN     = @echo '    ' GEN $@;
	QUIET_AR      = @echo '    ' AR $@;
	QUIET_SUBDIR0 = +@subdir=
	QUIET_SUBDIR1 = ; echo '    ' SUBDIR  $$subdir; \
		        ${MAKE} -s -C $$subdir
endif

.PHONY: check hmms clean distclean

check: 
	@echo 
	@echo Running HMMER test suite...
	@echo
	@${srcdir}/../${ESLDIR}/devkit/sqc ${SQCLEVEL} ${srcdir}/testsuite.sqc .. ${srcdir}/..

hmms:
	for ali in ${ALIS}; do\
	   ../src/hmmbuild $$ali.hmm $$ali.sto;\
	done

clean:
	-rm -f *.gcno *.gcda *.gcov
	-rm -f *.o *~ 
ifndef V
	@echo '     ' CLEAN testsuite
endif


distclean: clean
	-rm -f Makefile
	-rm -f esltmp[a-z][a-z][0-9][0-9]*

