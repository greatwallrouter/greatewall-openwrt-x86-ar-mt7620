.NOTPARALLEL:
APCOM_OBJ=main.o
DEBUG_OBJ=main.o
MD5_OBJ=md5.o
PTHREAD_LIBS = -lpthread
PARAM= -W -g -Wall -Wno-unused-parameter -DUSE_RUNTIME_MODEL_CHECKS=1

.PHONY: all
all: greatwallapp greatwallcmd md5
greatwallapp:$(APCOM_OBJ)
	$(CC) $(CFLAGS) $(LFLAGS) $(PARAM) $(PTHREAD_LIBS) -o $@ $(APCOM_OBJ)
greatwallcmd:$(DEBUG_OBJ) 
	$(CC) $(CFLAGS) $(LFLAGS) $(PARAM) $(PTHREAD_LIBS) -o $@ $(DEBUG_OBJ)
md5:$(MD5_OBJ)
	$(CC) $(CFLAGS) $(LFLAGS) $(PARAM) $(PTHREAD_LIBS) -o $@ $(MD5_OBJ)
	
