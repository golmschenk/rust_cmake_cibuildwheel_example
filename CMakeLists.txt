cmake_minimum_required(VERSION 3.27)
project(rust_cmake_cibuildwheel)

message(LOG "PATH: $ENV{PATH}")
execute_process(
        COMMAND ls /home/runner/.cargo/bin
)

include(FetchContent)

FetchContent_Declare(
        Corrosion
        GIT_REPOSITORY https://github.com/corrosion-rs/corrosion.git
        GIT_TAG v0.4
)

FetchContent_MakeAvailable(Corrosion)

corrosion_import_crate(MANIFEST_PATH Cargo.toml)