cmake_minimum_required(VERSION 3.17)

project(rust_cmake_cibuildwheel)

find_package(Python REQUIRED Interpreter Development.Module)

include(FetchContent)

FetchContent_Declare(
        Corrosion
        GIT_REPOSITORY https://github.com/corrosion-rs/corrosion.git
        GIT_TAG v0.4
)

FetchContent_MakeAvailable(Corrosion)

corrosion_import_crate(MANIFEST_PATH Cargo.toml)
# Required to make sure Rust uses the correct path to libpython at runtime.
corrosion_add_target_local_rustflags(rust_cmake_cibuildwheel_example "-Clink-args=-Wl,-rpath,${Python_LIBRARY_DIRS}")
