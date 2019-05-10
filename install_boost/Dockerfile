FROM my_miniconda3:latest

RUN yum install -y tbb tbb-devel && yum clean all && rm -rf /var/chache/yum

RUN (   cd /tmp \
	&& wget https://dl.bintray.com/boostorg/release/1.70.0/source/boost_1_70_0.tar.gz \
	&& tar -zxvof boost_1_70_0.tar.gz \
	&& cd boost_1_70_0 \
	&& echo "using mpi;" > user-config.jam \
	&& ./bootstrap.sh --with-libraries=all --with-python-root=/opt/conda/ --with-python="/opt/conda/bin/python3.6m" --with-python-version=3.6 \
	&& ./b2 cxxflags="-fPIC -Wno-deprecated-declarations -Wno-strict-overflow" cflags="-fPIC -I/opt/conda/include/python3.6m" -a install \
	&& cd /tmp && rm -rf /tmp/boost_1_70_0 /tmp/boost_1_70_0.tar.gz )

RUN yum install -y swig3 && yum clean all && rm -rf /var/cache/yum

RUN ( cd /tmp \
	&& wget https://github.com/stevengj/nlopt/archive/v2.6.1.tar.gz \
	&& tar -zxvof v2.6.1.tar.gz && rm v2.6.1.tar.gz \
	&& cd nlopt-2.6.1 && mkdir bld && cd bld \
	&& cmake -DNLOPT_CXX=ON .. \
	&& make install \
	&& cd /tmp && rm -rf nlopt-2.6.1 )

RUN conda install -y numpy scipy cloudpickle 

RUN ( cd /tmp \
	&& git clone https://github.com/bryan-lunt-supercomputing/pagmo2.git \
	&& cd pagmo2 \
	&& cmake . && make && make install \
	&& cd /tmp && rm -rf pagmo2 )

RUN conda install -y pygmo
