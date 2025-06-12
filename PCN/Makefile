CC=g++
DEBUG=-O0 -g
CXX_FLAGS=-std=c++11 -DCPU_ONLY 
#LD_FLAGS=-lopencv_core -lopencv_highgui -lopencv_imgcodecs -lopencv_imgproc -lopencv_video -lopencv_videoio -lcaffe -lglog -lboost_system -lprotobuf
#LD_FLAGS=-lopencv_core -lopencv_imgcodecs -lopencv_imgproc -lcaffe -lglog -lprotobuf
LD_FLAGS=-l:libopencv_core.so.3.2  -l:libopencv_imgproc.so.3.2 -l:libopencv_imgcodecs.so.3.2 -lcaffe -lglog -lprotobuf
TARGETS=video picture fddb pcn_api_test
LIB=libPCN.so
LIB_DIR=/usr/local/lib
SHARE_DIR=/usr/local/share/pcn
CAFFEROOT=/usr/local/lib

all: $(TARGETS)

$(LIB): PCN.cpp
	$(CC) -shared -fPIC -o $@ $^ ${CXX_FLAGS} ${LD_FLAGS} ${DEBUG} -I/usr/include/  -I/usr/lib/aarch64-linux-gnu/

$(TARGETS): $(LIB)
	$(CC) -o $@ $@.cpp $(LIB) ${CXX_FLAGS} ${LD_FLAGS} ${DEBUG} -lboost_system -l:libopencv_highgui.so.3.2 -L/usr/lib/aarch64-linux-gnu/

install:
	mkdir -p $(SHARE_DIR)
	cp model/* $(SHARE_DIR)
	cp $(LIB) $(LIB_DIR)

clean:
	rm -rf $(TARGETS) $(LIB)
