# Don't get the wrong half.h!
set(CMAKE_INCLUDE_CURRENT_DIR OFF)

add_library(gf SHARED
bbox3d.cpp
camera.cpp
frustum.cpp
gamma.cpp
half.cpp
homogeneous.cpp
ilmbase_half.cpp
interval.cpp
line.cpp
line2d.cpp
lineSeg.cpp
lineSeg2d.cpp
math.cpp
matrixData.cpp
matrix2d.cpp
matrix2f.cpp
matrix3f.cpp
matrix3d.cpp
matrix4f.cpp
matrix4d.cpp
multiInterval.cpp
plane.cpp
quatd.cpp
quatf.cpp
quath.cpp
quaternion.cpp
range1d.cpp
range1f.cpp
range2d.cpp
range2f.cpp
range3d.cpp
range3f.cpp
ray.cpp
rect2i.cpp
rotation.cpp
size2.cpp
size3.cpp
transform.cpp
vec2d.cpp
vec2f.cpp
vec2h.cpp
vec2i.cpp
vec3d.cpp
vec3f.cpp
vec3h.cpp
vec3i.cpp
vec4d.cpp
vec4f.cpp
vec4h.cpp
vec4i.cpp
# PYTHON_PUBLIC_CLASSES
pyBufferUtils.cpp
# PRIVATE_CLASSES
ostreamHelpers.cpp
# PYTHON_CPPFILES
moduleDeps.cpp
# PYMODULE_CPPFILES
module.cpp
wrapBBox3d.cpp
wrapCamera.cpp
wrapFrustum.cpp
wrapGamma.cpp
wrapHalf.cpp
wrapHomogeneous.cpp
wrapInterval.cpp
wrapLimits.cpp
wrapLine.cpp
wrapLineSeg.cpp
wrapMath.cpp
wrapMatrix2d.cpp
wrapMatrix2f.cpp
wrapMatrix3f.cpp
wrapMatrix3d.cpp
wrapMatrix4f.cpp
wrapMatrix4d.cpp
wrapMultiInterval.cpp
wrapPlane.cpp
wrapQuaternion.cpp
wrapQuatd.cpp
wrapQuatf.cpp
wrapQuath.cpp
wrapRange1d.cpp
wrapRange1f.cpp
wrapRange2d.cpp
wrapRange2f.cpp
wrapRange3d.cpp
wrapRange3f.cpp
wrapRay.cpp
wrapRect2i.cpp
wrapRotation.cpp
wrapSize2.cpp
wrapSize3.cpp
wrapTransform.cpp
wrapVec2d.cpp
wrapVec2f.cpp
wrapVec2h.cpp
wrapVec2i.cpp
wrapVec3d.cpp
wrapVec3f.cpp
wrapVec3h.cpp
wrapVec3i.cpp
wrapVec4d.cpp
wrapVec4f.cpp
wrapVec4h.cpp
wrapVec4i.cpp
)
# target_include_directories(gf
# PRIVATE
#     )
target_compile_definitions(gf
PRIVATE
    GF_EXPORTS)
target_link_libraries(gf
PUBLIC
    ${PYTHON_LIBRARIES}
    arch
    tf
    )

# set(PXR_PREFIX pxr/base)
# set(PXR_PACKAGE gf)

# pxr_library(gf
#     LIBRARIES
#         arch
#         tf

#     PUBLIC_CLASSES
#         bbox3d
#         camera
#         frustum
#         gamma
#         half
#         homogeneous
#         ilmbase_half
#         interval
#         line
#         line2d
#         lineSeg
#         lineSeg2d
#         math
#         matrixData
#         matrix2d
#         matrix2f
#         matrix3f
#         matrix3d
#         matrix4f
#         matrix4d
#         multiInterval
#         plane
#         quatd
#         quatf
#         quath
#         quaternion
#         range1d
#         range1f
#         range2d
#         range2f
#         range3d
#         range3f
#         ray
#         rect2i
#         rotation
#         size2
#         size3
#         transform
#         vec2d
#         vec2f
#         vec2h
#         vec2i
#         vec3d
#         vec3f
#         vec3h
#         vec3i
#         vec4d
#         vec4f
#         vec4h
#         vec4i

#     PYTHON_PUBLIC_CLASSES
#         pyBufferUtils

#     PUBLIC_HEADERS
#         api.h
#         declare.h
#         ilmbase_halfLimits.h
#         limits.h
#         traits.h

#     PRIVATE_CLASSES
#         ostreamHelpers

#     PRIVATE_HEADERS
#         ilmbase_eLut.h
#         ilmbase_toFloat.h

#     PYTHON_CPPFILES
#         moduleDeps.cpp

#     PYMODULE_CPPFILES
#         module.cpp
#         wrapBBox3d.cpp
#         wrapCamera.cpp
#         wrapFrustum.cpp
#         wrapGamma.cpp
#         wrapHalf.cpp
#         wrapHomogeneous.cpp
#         wrapInterval.cpp
#         wrapLimits.cpp
#         wrapLine.cpp
#         wrapLineSeg.cpp
#         wrapMath.cpp
#         wrapMatrix2d.cpp
#         wrapMatrix2f.cpp
#         wrapMatrix3f.cpp
#         wrapMatrix3d.cpp
#         wrapMatrix4f.cpp
#         wrapMatrix4d.cpp
#         wrapMultiInterval.cpp
#         wrapPlane.cpp
#         wrapQuaternion.cpp
#         wrapQuatd.cpp
#         wrapQuatf.cpp
#         wrapQuath.cpp
#         wrapRange1d.cpp
#         wrapRange1f.cpp
#         wrapRange2d.cpp
#         wrapRange2f.cpp
#         wrapRange3d.cpp
#         wrapRange3f.cpp
#         wrapRay.cpp
#         wrapRect2i.cpp
#         wrapRotation.cpp
#         wrapSize2.cpp
#         wrapSize3.cpp
#         wrapTransform.cpp
#         wrapVec2d.cpp
#         wrapVec2f.cpp
#         wrapVec2h.cpp
#         wrapVec2i.cpp
#         wrapVec3d.cpp
#         wrapVec3f.cpp
#         wrapVec3h.cpp
#         wrapVec3i.cpp
#         wrapVec4d.cpp
#         wrapVec4f.cpp
#         wrapVec4h.cpp
#         wrapVec4i.cpp

#     PYMODULE_FILES
#         __init__.py
# )

# # gfGenCode --validate ensures that the generated GfVec, GfMatrix, GfRange, etc.
# # source files are up to date with the contents of the templates used to
# # generate them. If not, a diff displaying the difference will be printed to
# # stdout and the build will fail.
# if (NOT ${PXR_VALIDATE_GENERATED_CODE})
#     message(STATUS "Skipping validation of gf generated code because PXR_VALIDATE_GENERATED_CODE=OFF")
# elseif(NOT JINJA2_FOUND)
#     message(STATUS "Skipping validation of gf generated code because of missing dependency: jinja2")
# else()
#     add_custom_command(
#         TARGET gf 
#         PRE_BUILD 
#         COMMENT "Validating gf generated code..."
#         COMMAND
#             ${PYTHON_EXECUTABLE} ${CMAKE_CURRENT_SOURCE_DIR}/gfGenCode.py 
#                 --srcDir ${CMAKE_CURRENT_SOURCE_DIR}
#                 --validate 
#     )
# endif()
        
# pxr_build_test(testGfHardToReach
#     LIBRARIES
#         gf
#     CPPFILES
#         testenv/testGfHardToReach.cpp
# ) 

# pxr_test_scripts(
#     testenv/testGfBBox3d.py
#     testenv/testGfCamera.py
#     testenv/testGfDecomposeRotation.py
#     testenv/testGfFrustum.py
#     testenv/testGfGamma.py
#     testenv/testGfHomogeneous.py
#     testenv/testGfInterval.py
#     testenv/testGfLine.py
#     testenv/testGfLineSeg.py
#     testenv/testGfMath.py
#     testenv/testGfMatrix.py
#     testenv/testGfMultiInterval.py
#     testenv/testGfPlane.py
#     testenv/testGfQuaternion.py
#     testenv/testGfRange.py
#     testenv/testGfRay.py
#     testenv/testGfRect2i.py
#     testenv/testGfRotation.py
#     testenv/testGfSize.py
#     testenv/testGfTransform.py
#     testenv/testGfVec.py
# )

# pxr_register_test(testGfBBox3d
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfBBox3d"
# )
# pxr_register_test(testGfDecomposeRotation
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfDecomposeRotation"
# )
# if (NOT APPLE)
#     pxr_register_test(testGfFrustum
#         PYTHON
#         COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfFrustum"
#     )
# endif()
# pxr_register_test(testGfGamma
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfGamma"
# )
# pxr_register_test(testGfHardToReach
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfHardToReach"
# )
# pxr_register_test(testGfHomogeneous
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfHomogeneous"
# )
# pxr_register_test(testGfInterval
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfInterval"
# )
# pxr_register_test(testGfMultiInterval
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfMultiInterval"
# )
# pxr_register_test(testGfLine
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfLine"
# )
# pxr_register_test(testGfLineSeg
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfLineSeg"
# )
# pxr_register_test(testGfMath
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfMath"
# )
# pxr_register_test(testGfMatrix
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfMatrix"
# )
# pxr_register_test(testGfPlane
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfPlane"
# )
# pxr_register_test(testGfQuaternion
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfQuaternion"
# )
# pxr_register_test(testGfRange
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfRange"
# )
# pxr_register_test(testGfRay
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfRay"
# )
# pxr_register_test(testGfRect2i
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfRect2i"
# )
# pxr_register_test(testGfRotation
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfRotation"
# )
# pxr_register_test(testGfSize
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfSize"
# )
# pxr_register_test(testGfTransform
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfTransform"
# )
# pxr_register_test(testGfVec
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfVec"
# )
# pxr_register_test(testGfCamera
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testGfCamera"
# )
