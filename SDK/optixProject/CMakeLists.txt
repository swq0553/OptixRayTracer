
if(GLUT_FOUND AND OPENGL_FOUND)
  include_directories(${GLUT_INCLUDE_DIR}, cloth-shader/src)
  add_definitions(-DGLUT_FOUND -DGLUT_NO_LIB_PRAGMA)

  # See top level CMakeLists.txt file for documentation of OPTIX_add_sample_executable.
  OPTIX_add_sample_executable( optixProject
    optixProject.cpp
	optixProject.h
    cloth-shader/src/woven_cloth.h
    cloth-shader/src/woven_cloth.cpp
    cudaFile.cu

    
    commonStructs.h
    random.h
    )
else()
  # GLUT or OpenGL not found
  message("Disabling project, which requires glut and opengl.")
endif()
