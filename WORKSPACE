load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

## rules_jvm_external

http_archive(
    name = "rules_jvm_external",
    sha256 = "7e13e48b50f9505e8a99cc5a16c557cbe826e9b68d733050cd1e318d69f94bb5",
    strip_prefix = "rules_jvm_external-fa73b1a8e4846cee88240d0019b8f80d39feb1c3",
    urls = [
        "https://github.com/bazelbuild/rules_jvm_external/archive/fa73b1a8e4846cee88240d0019b8f80d39feb1c3.zip",
    ],
)

load("@rules_jvm_external//:defs.bzl", "maven_install")

maven_install(
    name = "maven",
    artifacts = [
        "androidx.appcompat:appcompat:1.4.2",
        "androidx.constraintlayout:constraintlayout:2.1.4",
    ],
    repositories = [
        "https://maven.google.com",
        "https://repo1.maven.org/maven2",
    ],
)

## Android

# Have to use the add-dummy-sdk branch to avoid missing SDK toolchain errors.
http_archive(
    name = "rules_android",
    sha256 = "708b95dada074961f4996f0e3c6e0d4f48393c7ec55cfa9805ded98210c2a44a",
    strip_prefix = "rules_android-add-dummy-sdk",
    url = "https://github.com/katre/rules_android/archive/refs/heads/add-dummy-sdk.zip",
)

load("@rules_android//:prereqs.bzl", "rules_android_prereqs")

rules_android_prereqs()

load("@rules_android//:defs.bzl", "rules_android_workspace")

rules_android_workspace()

register_toolchains(
    "@rules_android//toolchains/android:android_default_toolchain",
    "@rules_android//toolchains/android_sdk:android_sdk_tools",
)

load("@rules_android//rules/android_sdk_repository:rule.bzl", "android_sdk_repository")

android_sdk_repository(
    name = "androidsdk",
)

## Android NDK

# Use recent head commit.
RULES_ANDROID_NDK_COMMIT = "505b0a5be2507b34a38c7fe0a96ac4a21a8eb2f3"

http_archive(
    name = "rules_android_ndk",
    sha256 = "bc578e1b7cdbe29aef151fb784408a843427253ae95bcc981163452f08fab81c",
    strip_prefix = "rules_android_ndk-%s" % RULES_ANDROID_NDK_COMMIT,
    url = "https://github.com/bazelbuild/rules_android_ndk/archive/%s.zip" % RULES_ANDROID_NDK_COMMIT,
)

load("@rules_android_ndk//:rules.bzl", "android_ndk_repository")

android_ndk_repository(
    name = "androidndk",
)
