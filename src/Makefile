DEST = .
CC = gcc
CFLAGS = $(INCLUDE) $(LIB) 

JAVA_HOME = ..

JNI_LAPACK_SRC = $(JAVA_HOME)/src/jni_lapack
JNI_BLAS_SRC = $(JAVA_HOME)/src/jni_blas
JNI_LAPACKE_SRC = $(JAVA_HOME)/src/jni_lapacke
JNI_UTIL = $(JAVA_HOME)/src/util

INCLUDE = -I$(JAVA_HOME)/include

LIB = -L/usr/local/lib #-L/usr/local/lib64 -L/usr/lib 

C_SRC_LAPACK1 = $(JNI_LAPACKE_SRC)/c/LUDecomposition.c 
C_SRC_LAPACK2 = $(JNI_LAPACKE_SRC)/c/CholeskyDecomposition.c
C_SRC_LAPACK3 = $(JNI_LAPACKE_SRC)/c/QRDecomposition.c
C_SRC_LAPACK4 = $(JNI_LAPACKE_SRC)/c/EigenvalueDecomposition.c
C_SRC_LAPACK5 = $(JNI_LAPACKE_SRC)/c/SingularValueDecomposition.c
C_SRC_BLAS = $(JNI_BLAS_SRC)/c/Matrix.c
DYLIB_LAPACK1 = $(JAVA_HOME)/lib/liblapacke_LUDecomposition.dylib
DYLIB_LAPACK2 = $(JAVA_HOME)/lib/liblapacke_CholeskyDecomposition.dylib
DYLIB_LAPACK3 = $(JAVA_HOME)/lib/liblapacke_QRDecomposition.dylib
DYLIB_LAPACK4 = $(JAVA_HOME)/lib/liblapacke_EigenvalueDecomposition.dylib
DYLIB_LAPACK5 = $(JAVA_HOME)/lib/liblapacke_SingularValueDecomposition.dylib
DYLIB_BLAS = $(JAVA_HOME)/lib/libblas_lite.dylib
	

# For package JAMAJni
JC = javac
JFLAGS = -d
JAVA_SRC = $(JNI_UTIL)/Maths.java $(JNI_LAPACKE_SRC)/java/LUDecomposition.java $(JNI_LAPACKE_SRC)/java/CholeskyDecomposition.java $(JNI_LAPACKE_SRC)/java/QRDecomposition.java $(JNI_LAPACKE_SRC)/java/EigenvalueDecomposition.java $(JNI_LAPACKE_SRC)/java/SingularValueDecomposition.java $(JNI_BLAS_SRC)/java/Matrix.java 
PACKAGE = $(JAVA_HOME)/class/*


all: $(PACKAGE) $(DYLIB_LAPACK1) $(DYLIB_LAPACK2) $(DYLIB_LAPACK3) $(DYLIB_LAPACK4) $(DYLIB_LAPACK5) $(DYLIB_BLAS)

$(PACKAGE): $(JAVA_SRC)
	@mkdir -p $(@D)
	$(JC) $(JFLAGS) $(JAVA_HOME)/class $(JAVA_SRC)

$(DYLIB_LAPACK1): $(C_SRC_LAPACK1)
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) -shared -fPIC $(C_SRC_LAPACK1) -llapacke -llapack -lblas -o $(DYLIB_LAPACK1)

$(DYLIB_LAPACK2): $(C_SRC_LAPACK2)
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) -shared -fPIC $(C_SRC_LAPACK2) -llapacke -llapack -lblas -o $(DYLIB_LAPACK2)
$(DYLIB_LAPACK3): $(C_SRC_LAPACK3)
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) -shared -fPIC $(C_SRC_LAPACK3) -llapacke -llapack -lblas -o $(DYLIB_LAPACK3)

$(DYLIB_LAPACK4): $(C_SRC_LAPACK4)
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) -shared -fPIC $(C_SRC_LAPACK4) -llapacke -llapack -lblas -o $(DYLIB_LAPACK4)

$(DYLIB_LAPACK5): $(C_SRC_LAPACK5)
	@mkdir -p $(@D)
	 $(CC) $(CFLAGS) -shared -fPIC $(C_SRC_LAPACK5) -llapacke -llapack -lblas -o $(DYLIB_LAPACK5)

$(DYLIB_BLAS): $(C_SRC_BLAS) 
	@mkdir -p $(@D)
	$(CC) $(CFLAGS) -shared -fPIC $(C_SRC_BLAS) -lblas -o $(DYLIB_BLAS)

clean: 
	rm -fr $(JAVA_HOME)/class
	rm -fr $(JAVA_HOME)/lib
	rm -f $(JAVA_HOME)/lib/*.dylib
	rm -f $(JAVA_HOME)/test/*.class
	rm -f $(JAVA_HOME)/test/*.txt
	rm -f $(JAVA_HOME)/test/*.out
	rm -f $(JAVA_HOME)/test/*.serial
