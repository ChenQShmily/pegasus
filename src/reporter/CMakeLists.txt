set(MY_PROJ_NAME "pegasus_reporter")
project(${MY_PROJ_NAME} C CXX)

# Source files under CURRENT project directory will be automatically included.
# You can manually set MY_PROJ_SRC to include source files under other directories.
set(MY_PROJ_SRC "../../rdsn/thirdparty/output/include")

# Search mode for source files under CURRENT project directory?
# "GLOB_RECURSE" for recursive search
# "GLOB" for non-recursive search
set(MY_SRC_SEARCH_MODE "GLOB")
include_directories(../../rdsn/thirdparty/output)
link_directories(../../rdsn/thirdparty/output/lib)
link_libraries(
	"libprometheus-cpp-core.so"
	"libprometheus-cpp-push.so"
	"libprometheus-cpp-pull.so")
#add_executable(myrepoter pegasus_counter_reporter.cpp)
set(MY_PROJ_INC_PATH
    "../../rdsn/thirdparty/output/include/prometheus-cpp/core/include"
    "../../rdsn/thirdparty/output/include/prometheus-cpp/push/include")

set(MY_PROJ_LIBS 
	prometheus-cpp-core
	prometheus-cpp-pull
	prometheus-cpp-push
	${MY_PROJ_LIBS}
	)

set(MY_BOOST_PACKAGES system)
set(MY_BOOST_PACKAGES system filesystem)

set(MY_BINPLACES "config.ini")
#SET(CMAKE_INSTALL_RPATH ".")
#SET(CMAKE_BUILD_WITH_INSTALL_RPATH TRUE)

#dsn_add_executable()
#dsn_install_executable()
dsn_add_static_library()
