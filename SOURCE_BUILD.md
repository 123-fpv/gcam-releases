# Build the V45.96 source snapshot

This is a sanitized snapshot, not the original repository history. Build files and source retain V45.96. Personal CAD projects, machine settings, logs and model fixtures are excluded. Configure BUILD_TESTING=OFF; tests that require those excluded fixtures are not reproducible from this public snapshot. No fresh full build was performed for this publication.

Use a VS 2022 x64 Native Tools developer shell, CMake >=3.20, Ninja, Python 3, Boost 1.85 headers and the official OCCT 8.0.0 Windows x64 SDK. FreeCAD Adaptive2d requires C++20; the application uses C++17. Set paths for your own computer rather than the historical defaults in CMakeLists.txt.

Example (replace paths):

cmake -S SOURCE -B BUILD -G Ninja -DCMAKE_BUILD_TYPE=Release -DBUILD_TESTING=OFF -DGRBL_CAM_EXECUTABLE_NAME=GCam -DOCCT_ROOT=OCCT_SDK -DBOOST_ROOT=BOOST_HEADERS -DFETCHCONTENT_SOURCE_DIR_GLFW=SOURCE/vendor/glfw -DFETCHCONTENT_SOURCE_DIR_IMGUI=SOURCE/vendor/imgui
cmake --build BUILD --parallel 2

OpenCAMLib's included source is research/opencamlib-master/src. Its CMake project can be built separately with BUILD_CXX_LIB=ON and BUILD_DOC=OFF, BUILD_PY_LIB=OFF, BUILD_NODEJS_LIB=OFF; point OCL_INC and OCL_LIB to its headers and resulting libraries. The matching historical prebuilt libraries are retained in research/opencamlib-build for the Windows build. These reconstruction commands have not been revalidated in a fresh environment.

The optional CANDLE_RUNTIME_DIR should point to the complete runtime candle directory. CMake's build steps do not assemble the complete portable Python, OCP/VTK, speech or Candle distribution. Preserve those runtime directories and their licenses from the published Windows package. For application helper integrity:

python tools/runtime_delivery.py verify --source-root SOURCE --runtime-dir RUNTIME

Native OCCT complete source is provided as OCCT-V8_0_0-source.zip beside this release. Its upstream build system and licensing remain unchanged. See LICENSES.md for the separate Python-layer dependencies.