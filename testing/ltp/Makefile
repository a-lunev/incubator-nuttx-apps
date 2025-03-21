############################################################################
# apps/testing/ltp/Makefile
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.  The
# ASF licenses this file to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance with the
# License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
# WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the
# License for the specific language governing permissions and limitations
# under the License.
#
############################################################################

include $(APPDIR)/Make.defs

LTPS_VERSION     = 20230516
LTP_DOWNLOAD_URL = https://github.com/linux-test-project/ltp/archive/refs/tags/
LTP_UNPACK       = ltp
LTP_URL          = https://github.com/linux-test-project/ltp.git

TESTDIR          = $(LTP_UNPACK)/testcases/open_posix_testsuite

ifneq ($(wildcard $(TESTDIR)),)
ifeq ($(CONFIG_FS_AIO),)
BLACKWORDS  += "aio.h"
BLACKWORDS  += "SIGPOLL"
endif
BLACKWORDS  += "SA_RESTART"
BLACKWORDS  += "pthread_atfork"
BLACKWORDS  += "pthread_condattr_setpshared"
BLACKWORDS  += "pthread_condattr_getpshared"
BLACKWORDS  += "pthread_mutex_getprioceiling"
BLACKWORDS  += "pthread_mutexattr_setprioceiling"
BLACKWORDS  += "pthread_mutexattr_getprioceiling"
BLACKWORDS  += "pthread_getattr_np"
BLACKWORDS  += "pthread_getcpuclockid"
BLACKWORDS  += "pthread_rwlockattr_init"
BLACKWORDS  += "pthread_rwlockattr_destroy"
BLACKWORDS  += "pthread_mutex_getprioceiling"
BLACKWORDS  += "clock_getcpuclockid"
BLACKWORDS  += "shm_unlink"
BLACKWORDS  += "shm_open"
BLACKWORDS  += "mlock"
BLACKWORDS  += "munlock"
BLACKWORDS  += "mlockall"
BLACKWORDS  += "msync"
BLACKWORDS  += "getpgrp"
BLACKWORDS  += "lfind"
BLACKWORDS += "killpg"
BLACKWORDS  += "setpwent"
ifeq ($(CONFIG_PTHREAD_SPINLOCKS),)
BLACKWORDS += "pthread_spin_init"
BLACKWORDS += "pthread_spin_destroy"
BLACKWORDS += "pthread_spin_trylock"
endif

BLACKWORDS  += "affinity.h"
BLACKWORDS  += "langinfo.h"
BLACKWORDS  += "ucontext.h"
BLACKWORDS  += "noatime.h"
BLACKWORDS  += "CLOCK_PROCESS_CPUTIME_ID"
BLACKWORDS  += "CLOCK_THREAD_CPUTIME_ID"
BLACKWORDS  += "fork()"
BLACKWORDS  += "pthread_attr_setscope"
BLACKWORDS  += "RLIMIT_MEMLOCK"
BLACKWORDS  += "PTHREAD_SCOPE_PROCESS"
BLACKWORDS  += "SIGABRT"
BLACKWORDS  += "SIGBUS"
BLACKWORDS  += "SIGFPE"
BLACKWORDS  += "SIGHUP"
BLACKWORDS  += "SIGILL"
BLACKWORDS  += "SIGPROF"
BLACKWORDS  += "SIGSEGV"
BLACKWORDS  += "SIGSYS"
BLACKWORDS  += "SIGTRAP"
BLACKWORDS  += "SIGTSTP"
BLACKWORDS  += "SIGTTIN"
BLACKWORDS  += "SIGTTOU"
BLACKWORDS  += "SIGURG"
BLACKWORDS  += "SIGVTALRM"
BLACKWORDS  += "SIGXCPU"
BLACKWORDS  += "SIGXFSZ"
BLACKWORDS  += "SIGSTKSZ"
BLACKWORDS  += "stack_t"
BLACKWORDS  += "siginterrupt"
BLACKWORDS  += "threads_scenarii.c"
BLACKWORDS  += "PTHREAD_PRIO_PROTECT"
BLACKWORDS  += "pthread_mutex_lock"

BLACKWORDS  += "ILL_[A-Z]"
BLACKWORDS  += "FPE_[A-Z]"
BLACKWORDS  += "BUS_[A-Z]"
BLACKWORDS  += "TRAP_[A-Z]"
BLACKWORDS  += "SEGV_[A-Z]"
BLACKWORDS  += "POLL_[A-Z]"
BLACKWORDS  += "SA_ONSTACK"
BLACKWORDS  += "MINSIGSTKSZ"
BLACKWORDS  += "FPE_FLTINV"

BLACKSRCS += testfrmw.c
BLACKSRCS += 7-3-buildonly.c
BLACKSRCS += 7-4-buildonly.c
BLACKSRCS += 7-5-buildonly.c
BLACKSRCS += 11-1-buildonly.c
BLACKSRCS += 17-1-buildonly.c
BLACKSRCS += 19-1-buildonly.c
BLACKSRCS += 21-1-buildonly.c
BLACKSRCS += 22-31-buildonly.c
BLACKSRCS += 22-32-buildonly.c
BLACKSRCS += 25-1-buildonly.c
BLACKSRCS += 27-1-buildonly.c
BLACKSRCS += 34-1-buildonly.c
BLACKSRCS += 35-1-buildonly.c
BLACKSRCS += 35-2-buildonly.c
BLACKSRCS += 27-2.c
ifeq ($(CONFIG_PTHREAD_SPINLOCKS),)
BLACKSRCS += 3-12-buildonly.c
endif
BLACKSRCS += 35-3-buildonly.c
ifeq ($(CONFIG_SCHED_CHILD_STATUS),)
BLACKSRCS += $(TESTDIR)/conformance/interfaces/pthread_exit/6-1.c
BLACKSRCS += $(TESTDIR)/conformance/behavior/WIFEXITED/1-1.c
BLACKSRCS += $(TESTDIR)/conformance/behavior/WIFEXITED/1-2.c
endif
ifeq ($(CONFIG_FS_TMPFS),)
BLACKWORDS += lio_listio
endif
ifeq ($(CONFIG_SIG_EVTHREAD),)
BLACKWORDS += fork
endif
ifneq ($(shell expr $(CONFIG_MQ_MAXMSGSIZE) \>= 64),1)
BLACKWORDS += mq_close
BLACKWORDS += mq_getattr
BLACKWORDS += mq_notify
BLACKWORDS += mq_open
BLACKWORDS += mq_receive
BLACKWORDS += mq_send
BLACKWORDS += mq_setattr
BLACKWORDS += mq_timedreceive
BLACKWORDS += mq_timedsend
BLACKWORDS += mq_unlink
endif
ifeq ($(CONFIG_PTHREAD_MUTEX_TYPES),)
BLACKWORDS += pthread_mutexattr_settype
endif
ifeq ($(CONFIG_SCHED_SPORADIC),)
BLACKSRCS += $(TESTDIR)/conformance/interfaces/sched_setscheduler/19-2.c
BLACKSRCS += $(TESTDIR)/conformance/interfaces/sched_setscheduler/19-3.c
BLACKSRCS += $(TESTDIR)/conformance/interfaces/sched_setscheduler/19-4.c
endif
ifeq ($(CONFIG_SIG_DEFAULT),)
BLACKWORDS += SIGKILL
BLACKWORDS += SIGSTOP
endif
ifeq ($(CONFIG_RR_INTERVAL),)
BLACKSRCS += $(TESTDIR)/functional/threads/condvar/pthread_cond_wait_1.c
endif
ifeq ($(CONFIG_FS_NAMED_SEMAPHORES),)
BLACKWORDS += sem_open
BLACKWORDS += sem_close
BLACKWORDS += sem_unlink
endif
ifeq ($(CONFIG_PIPES),)
BLACKWORDS += pipe
endif
ifneq ($(shell expr $(CONFIG_LIBC_MAX_EXITFUNS) \>= 32),1)
BLACKSRCS += $(TESTDIR)/conformance/interfaces/pthread_exit/4-1.c
BLACKSRCS += $(TESTDIR)/conformance/interfaces/pthread_exit/5-1.c
endif
ifeq ($(CONFIG_CANCELLATION_POINTS),)
BLACKSRCS += $(TESTDIR)/conformance/interfaces/pthread_exit/3-1.c
endif
ifneq ($(shell expr $(CONFIG_TLS_NELEM) \>= 16),1)
BLACKSRCS += $(TESTDIR)/conformance/interfaces/pthread_setspecific/1-1.c
endif
ifeq ($(CONFIG_PTHREAD_SPINLOCKS),)
BLACKWORDS += pthread_spin_lock
endif
ifeq ($(CONFIG_SCHED_WAITPID),)
BLACKWORDS += waitpid
endif
ifeq ($(CONFIG_SCHED_USER_IDENTITY),)
BLACKWORDS += setuid
BLACKWORDS += setgid
BLACKWORDS += getuid
BLACKWORDS += getgid
BLACKWORDS += seteuid
BLACKWORDS += setegid
BLACKWORDS += geteuid
BLACKWORDS += getegid
endif
ifeq ($(CONFIG_PTHREAD_CLEANUP_STACKSIZE),0)
BLACKWORDS += pthread_cleanup_push
BLACKWORDS += pthread_cleanup_pop
endif
ifeq ($(CONFIG_LIBC_EXECFUNCS),)
BLACKWORDS += execl
BLACKWORDS += execvp
BLACKWORDS += execlp
BLACKWORDS += execvpe
endif
ifeq ($(CONFIG_FS_SHMFS),)
BLACKWORDS += shm_open
BLACKWORDS += shm_unlink
endif
ifeq ($(LIBC_LOCALE_CATALOG),)
BLACKWORDS += catopen
BLACKWORDS += catgets
BLACKWORDS += catclose
endif
ifeq ($(CONFIG_MM_SHM),)
BLACKWORDS += shmget
BLACKWORDS += shmat
endif

MAINWORDS += "main("

LTP_ORIGS := $(shell find $(TESTDIR) -name *.c)
ifneq ($(LTP_ORIGS),)
$(call SPLITVARIABLE,ORIGS_SPILT,$(LTP_ORIGS),200)
$(foreach BATCH, $(ORIGS_SPILT_TOTAL), \
	$(foreach word, $(BLACKWORDS), $(eval BLACKLIST+=$(shell grep -lr $(word) $(ORIGS_SPILT_$(BATCH))))) \
)
endif

$(foreach src, $(BLACKSRCS), $(eval BLACKLIST+=$(filter %$(src),$(LTP_ORIGS))))

LTP_ORIGS := $(filter-out $(BLACKLIST), $(LTP_ORIGS))
ifneq ($(LTP_ORIGS),)
$(call SPLITVARIABLE,ORIGS_SPILT,$(LTP_ORIGS),200)
$(foreach BATCH, $(ORIGS_SPILT_TOTAL), \
	$(foreach word, $(MAINWORDS), $(eval LTP_MAINCSRCS+=$(shell grep -lr $(word) $(ORIGS_SPILT_$(BATCH))))) \
)
endif

LTP_CSRCS := $(filter-out $(LTP_MAINCSRCS), $(LTP_ORIGS))
ifneq ($(LTP_MAINCSRCS),)
$(call SPLITVARIABLE,MAINCSRC_SPILT,$(LTP_MAINCSRCS),50)
$(foreach BATCH, $(MAINCSRC_SPILT_TOTAL), \
	$(eval PROGNAME+=$(basename $(shell echo $(MAINCSRC_SPILT_$(BATCH)) | xargs -n 1 | awk -F "[/]" '{print "ltp_"$$(NF-2)"_"$$(NF-1)"_"$$(NF)}' | sed s/-/_/g))) \
)
endif

MAINSRC       = $(LTP_MAINCSRCS)
PRIORITY      = SCHED_PRIORITY_DEFAULT
STACKSIZE     = $(CONFIG_DEFAULT_TASK_STACKSIZE)
MODULE        = $(CONFIG_TESTING_LTP)

CSRCS        := $(LTP_CSRCS)
CFLAGS       += -I$(CURDIR)
CFLAGS       += -I$(TESTDIR)/include
endif

# Relax warning checks to avoid expected compile errors:
CFLAGS += -Wno-strict-prototypes -Wno-return-type -Wno-format -Wno-uninitialized
CFLAGS += -Wno-unused-variable -Wno-unused-function -Wno-unused-but-set-variable -Wno-unused-value

# Should be removed if possible in the future
CFLAGS += -Wno-incompatible-pointer-types -Wno-overflow -Wno-int-to-pointer-cast

ltp-$(LTPS_VERSION).zip:
	$(call DOWNLOAD,$(LTP_DOWNLOAD_URL),$(LTPS_VERSION).zip, ltp.zip)

$(LTP_UNPACK): ltp-$(LTPS_VERSION).zip
	$(Q) echo "dowload $(LTP_DOWNLOAD_URL)$(LTPS_VERSION).zip"
	$(Q) unzip -o ltp.zip
	$(Q) mv ltp-$(LTPS_VERSION) $(LTP_UNPACK)
	$(Q) patch -p1 < 0001-pthread_rwlock_unlock-follow-linux.patch
	$(Q) patch -p1 < 0002-Use-ifdef-instead-of-if-for-__linux__.patch

# Download and unpack tarball if no git repo found
ifeq ($(wildcard $(LTP_UNPACK)/.git),)
context:: $(LTP_UNPACK)

distclean::
	$(Q) rm -rf $(LTP_UNPACK)
endif

include $(APPDIR)/Application.mk
