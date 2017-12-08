cmake_minimum_required(VERSION 3.2)

project(otus_cpp_01 VERSION 0.0.$ENV{TRAVIS_BUILD_NUMBER})

#find_package(Boost COMPONENTS unit_test_framework REQUIRED)

configure_file(version.h.in version.h)

add_executable(otus_cpp_01_cli main.cpp)

set_target_properties(otus_cpp_01_cli #test_version
	PROPERTIES
		CXX_STANDARD 14
		CXX_STANDARD_REQUIRED ON
		COMPILE_OPTIONS -Wpedantic -Wall -Wextra
)

#set_target_properties(test_version
#	PROPERTIES
#		COMPILE_DEFINITIONS BOOST_TEST_DYN_LINK
#		INCLUDE_DIRECTORIES ${Boost_INCLUDE_DIR}
#)

target_link_libraries(otus_cpp_01_cli)

#target_link_libraries(test_version
#	${Boost_LIBRARIES}
#	otus_cpp_01_cli
#)

install(TARGETS otus_cpp_01_cli RUNTIME DESTINATION bin)

set(CPACK_GENERATOR DEB)

set(CPACK_PACKAGE_VERSION_MAJOR "${PROJECT_VERSION_MAJOR}")
set(CPACK_PACKAGE_VERSION_MINOR "${PROJECT_VERSION_MINOR}")
set(CPACK_PACKAGE_VERSION_PATCH "${PROJECT_VERSION_PATCH}")

set(CPACK_PACKAGE_CONTACT edkolotilov@gmail.com)

include (CPack)

#enable_testing()

#add_test(test_version test_version)