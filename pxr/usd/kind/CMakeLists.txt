add_library(kind SHARED
        registry.cpp

#     PYTHON_CPPFILES
        moduleDeps.cpp

#     PYMODULE_CPPFILES
        module.cpp
        wrapRegistry.cpp
        wrapTokens.cpp
)
target_compile_definitions(kind
PRIVATE
    KIND_EXPORTS
)
target_link_libraries(kind
PRIVATE
    arch
    tf
    plug
    js
    ${PYTHON_LIBRARIES}
)

# set(PXR_PREFIX pxr/usd)
# set(PXR_PACKAGE kind)

# pxr_library(kind
#     LIBRARIES
#         tf
#         plug

#     PUBLIC_CLASSES
#         registry
        
#     PUBLIC_HEADERS
#         api.h

#     PYTHON_CPPFILES
#         moduleDeps.cpp

#     PYMODULE_CPPFILES
#         module.cpp
#         wrapRegistry.cpp
#         wrapTokens.cpp

#     PYMODULE_FILES 
#         __init__.py
# )

# pxr_test_scripts(
#     testenv/testKindRegistry.py
# )

# pxr_install_test_dir(
#     SRC testenv/testKindRegistry
#     DEST testKindRegistry
# )

# pxr_register_test(testKindRegistry
#     PYTHON
#     COMMAND "${CMAKE_INSTALL_PREFIX}/tests/testKindRegistry"
#     EXPECTED_RETURN_CODE 0
# )
