load("//tools:cpplint.bzl", "cpplint")

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "control_lib",
    srcs = [
    ],
    copts = ['-DMODULE_NAME=\\"control\\"'],
    deps = [
        "//cyber",
        "//external:gflags",
        "//modules/canbus/proto:canbus_proto",
        "//modules/common",
        "//modules/common/adapters:adapter_gflags",
        "//modules/common/monitor_log",
        "//modules/common/time",
        "//modules/common/util",
        "//modules/control/common",
        "//modules/control/controller",
        "//modules/control/submodules:preprocessor_submodule_lib",
        "//modules/control/submodules:lat_lon_controller_submodule_lib",
        "//modules/control/submodules:mpc_controller_submodule_lib",
        "//modules/control/submodules:postprocessor_submodule_lib",
        "//modules/control/proto:control_proto",
        "//modules/control/proto:preprocessor_proto",
        "//modules/localization/proto:localization_proto",
        "//modules/perception/proto:perception_proto",
        "//modules/planning/proto:planning_proto",
        "//modules/prediction/proto:prediction_proto"
    ],
)

cc_library(
    name = "control_component_lib",
    srcs = [
        "control_component.cc",
    ],
    hdrs = [
        "control_component.h",
    ],
    copts = ['-DMODULE_NAME=\\"control\\"'],
    deps = [
        ":control_lib",
    ],
)

cc_binary(
    name = "libcontrol_component.so",
    linkshared = True,
    linkstatic = False,
    deps = [":control_component_lib"],
)

cc_test(
    name = "control_component_test",
    size = "small",
    srcs = [
        "control_component_test.cc",
    ],
    data = ["//modules/control:control_testdata"],
    deps = [
        ":control_component_lib",
        "@gtest//:main",
    ],
)

filegroup(
    name = "control_testdata",
    srcs = glob([
        "testdata/**",
    ]),
)

cpplint()
