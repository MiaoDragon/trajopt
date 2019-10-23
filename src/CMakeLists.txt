include_directories(
  ${CMAKE_SOURCE_DIR}/ext
  ${CMAKE_SOURCE_DIR}/src
)


add_definitions(-DEIGEN_DEFAULT_TO_ROW_MAJOR)

# gcc 4.7 workaround:
# execute_process(COMMAND ${CMAKE_C_COMPILER} -dumpversion
#                 OUTPUT_VARIABLE GCC_VERSION)
# if (GCC_VERSION VERSION_GREATER 4.6)
#   message("GCC > 4.6 detected")
#    add_definitions(-D_GLIBCXX_HAVE_GTHR_DEFAULT)
# endif()

find_package(GUROBI)
if (NOT GUROBI_FOUND)
  message("Gurobi not found. If you want to use Gurobi, set the GUROBI_HOME variable")
else()
  message("Gurobi found")
  include_directories(${GUROBI_INCLUDE_DIRS})
endif()

add_subdirectory(sco)
add_subdirectory(utils)
if(NOT APPLE)
endif()
