add_library(vt SHARED
        array.cpp
        dictionary.cpp
        functions.cpp
        hash.cpp
        streamOut.cpp
        types.cpp
        value.cpp

#     PYTHON_PUBLIC_CLASSES
        arrayPyBuffer.cpp
        valueFromPython.cpp
        wrapArray.cpp

#     PYTHON_CPPFILES
        moduleDeps.cpp

#     PYMODULE_CPPFILES
        module.cpp
        wrapArrayBase.cpp
        wrapArrayFloat.cpp
        wrapArrayIntegral.cpp
        wrapArrayMatrix.cpp
        wrapArrayQuaternion.cpp
        wrapArrayRange.cpp
        wrapArrayString.cpp
        wrapArrayToken.cpp
        wrapArrayVec.cpp
        wrapDictionary.cpp
        wrapValue.cpp
)
# target_link_libraries(vt
# PRIVATE

#     )
target_compile_definitions(vt
PRIVATE
    VT_EXPORTS)
target_link_libraries(vt
PRIVATE
    arch
    tf
    gf
    trace
    ${PYTHON_LIBRARIES}
)

# set(PXR_PREFIX pxr/base)
# set(PXR_PACKAGE vt)

# pxr_library(vt
#     LIBRARIES
#         arch
#         tf
#         gf
#         trace
#         ${Boost_PYTHON_LIBRARY}
#         ${TBB_tbb_LIBRARY}

#     INCLUDE_DIRS
#         ${Boost_INCLUDE_DIRS}
#         ${TBB_INCLUDE_DIRS}

#     PUBLIC_CLASSES
#         array
#         dictionary
#         functions
#         hash
#         streamOut
#         types
#         value

#     PYTHON_PUBLIC_CLASSES
#         arrayPyBuffer
#         valueFromPython
#         wrapArray

#     PUBLIC_HEADERS
#         api.h
#         traits.h
#         operators.h
    
#     PYTHON_PUBLIC_HEADERS
#         pyOperators.h

#     PRIVATE_HEADERS
#         typeHeaders.h

#     PYTHON_CPPFILES
#         moduleDeps.cpp

#     PYMODULE_CPPFILES
#         module.cpp
#         wrapArrayBase.cpp
#         wrapArrayFloat.cpp
#         wrapArrayIntegral.cpp
#         wrapArrayMatrix.cpp
#         wrapArrayQuaternion.cpp
#         wrapArrayRange.cpp
#         wrapArrayString.cpp
#         wrapArrayToken.cpp
#         wrapArrayVec.cpp
#         wrapDictionary.cpp
#         wrapValue.cpp

#     PYMODULE_FILES
#         __init__.py
# )

# pxr_build_test(testVtCpp
#     LIBRARIES
#         tf
#         gf
#         vt
#     CPPFILES
#         testenv/testVtCpp.cpp
# )
# pxr_test_scripts(
#     testenv/testVtArray.py
#     testenv/testVtValue.py
#     testenv/testVtFunctions.py
# )
# pxr_register_test(testVtValue
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testVtValue"
# )
# pxr_register_test(testVtArray
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testVtArray"
# )
# pxr_register_test(testVtFunctions
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testVtFunctions"
# )
# pxr_register_test(testVtCpp
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testVtCpp"
# )
