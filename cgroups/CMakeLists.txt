IF(CGROUPS)
    LOCATE_LIBRARY(LIBCGROUP "libcgroup.h" "cgroup")

    ADD_LIBRARY(cgroups MODULE
        module
        isolate)

    TARGET_LINK_LIBRARIES(cgroups
        cocaine-core
        cgroup)

    SET_TARGET_PROPERTIES(cgroups PROPERTIES
        PREFIX ""
        SUFFIX ".cocaine-plugin"
        COMPILE_FLAGS "-std=c++0x")

    INSTALL(
        TARGETS cgroups
        LIBRARY DESTINATION lib/cocaine
        COMPONENT runtime)
ENDIF(CGROUPS)
