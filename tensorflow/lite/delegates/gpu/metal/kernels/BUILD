load("@build_bazel_rules_apple//apple:ios.bzl", "ios_unit_test")
load(
    "//tensorflow/lite:special_rules.bzl",
    "tflite_ios_lab_runner",
    "tflite_ios_per_kernel_test",
    "tflite_portable_test_suite",
)
load(
    "//tensorflow/core/platform:build_config_root.bzl",
    "tf_gpu_tests_tags",
)

package(
    default_visibility = ["//visibility:public"],
    licenses = ["notice"],  # Apache 2.0
)

cc_library(
    name = "kernels",
    deps = [
        ":conv",
        ":transpose_conv",
        ":winograd",
    ],
)

objc_library(
    name = "add_test_lib",
    testonly = 1,
    srcs = ["add_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:add_test_util",
    ],
)

ios_unit_test(
    name = "add_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":add_test_lib"],
)

objc_library(
    name = "concat_test_lib",
    testonly = 1,
    srcs = ["concat_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:concat_test_util",
    ],
)

ios_unit_test(
    name = "concat_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":concat_test_lib"],
)

cc_library(
    name = "conv",
    srcs = ["conv.cc"],
    hdrs = ["conv.h"],
    deps = [
        ":util",
        "//tensorflow/lite/delegates/gpu/common:data_type",
        "//tensorflow/lite/delegates/gpu/common:gpu_info",
        "//tensorflow/lite/delegates/gpu/common:operations",
        "//tensorflow/lite/delegates/gpu/common:shape",
        "//tensorflow/lite/delegates/gpu/common:types",
        "//tensorflow/lite/delegates/gpu/common:util",
        "//tensorflow/lite/delegates/gpu/common:winograd_util",
        "//tensorflow/lite/delegates/gpu/common/task:gpu_operation",
        "@com_google_absl//absl/strings",
    ],
)

objc_library(
    name = "conv_test_lib",
    testonly = 1,
    srcs = ["conv_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":conv",
        ":test_util",
        ":winograd",
    ],
)

ios_unit_test(
    name = "conv_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":conv_test_lib"],
)

objc_library(
    name = "conv_weights_converter_test_lib",
    testonly = 1,
    srcs = ["conv_weights_converter_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:conv_weights_converter_test_util",
    ],
)

ios_unit_test(
    name = "conv_weights_converter_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":conv_weights_converter_test_lib"],
)

objc_library(
    name = "depthwise_conv_test_lib",
    testonly = 1,
    srcs = ["depthwise_conv_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:depthwise_conv_3x3_stride_h2_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:depthwise_conv_3x3_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:depthwise_conv_test_util",
    ],
)

ios_unit_test(
    name = "depthwise_conv_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":depthwise_conv_test_lib"],
)

objc_library(
    name = "elementwise_test_lib",
    testonly = 1,
    srcs = ["elementwise_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:elementwise_test_util",
    ],
)

ios_unit_test(
    name = "elementwise_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":elementwise_test_lib"],
)

objc_library(
    name = "fully_connected_test_lib",
    testonly = 1,
    srcs = ["fully_connected_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:fully_connected_test_util",
    ],
)

ios_unit_test(
    name = "fully_connected_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":fully_connected_test_lib"],
)

objc_library(
    name = "lstm_test_lib",
    testonly = 1,
    srcs = ["lstm_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:lstm_test_util",
    ],
)

ios_unit_test(
    name = "lstm_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":lstm_test_lib"],
)

objc_library(
    name = "max_unpooling_test_lib",
    testonly = 1,
    srcs = ["max_unpooling_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:max_unpooling_test_util",
    ],
)

ios_unit_test(
    name = "max_unpooling_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":max_unpooling_test_lib"],
)

objc_library(
    name = "mean_stddev_normalization_test_lib",
    testonly = 1,
    srcs = ["mean_stddev_normalization_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:mean_stddev_normalization_test_util",
    ],
)

ios_unit_test(
    name = "mean_stddev_normalization_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":mean_stddev_normalization_test_lib"],
)

objc_library(
    name = "padding_test_lib",
    testonly = 1,
    srcs = ["padding_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:padding_test_util",
    ],
)

ios_unit_test(
    name = "padding_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":padding_test_lib"],
)

objc_library(
    name = "pooling_test_lib",
    testonly = 1,
    srcs = ["pooling_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:pooling_test_util",
    ],
)

ios_unit_test(
    name = "pooling_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":pooling_test_lib"],
)

objc_library(
    name = "prelu_test_lib",
    testonly = 1,
    srcs = ["prelu_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:prelu_test_util",
    ],
)

ios_unit_test(
    name = "prelu_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":prelu_test_lib"],
)

objc_library(
    name = "quantize_and_dequantize_test_lib",
    testonly = 1,
    srcs = ["quantize_and_dequantize_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common:operations",
        "//tensorflow/lite/delegates/gpu/common:shape",
        "//tensorflow/lite/delegates/gpu/common:status",
        "//tensorflow/lite/delegates/gpu/common:tensor",
        "//tensorflow/lite/delegates/gpu/common:util",
        "//tensorflow/lite/delegates/gpu/common/tasks:quantize_and_dequantize_test_util",
    ],
)

ios_unit_test(
    name = "quantize_and_dequantize_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":quantize_and_dequantize_test_lib"],
)

objc_library(
    name = "reduce_test_lib",
    testonly = 1,
    srcs = ["reduce_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:reduce_test_util",
    ],
)

ios_unit_test(
    name = "reduce_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":reduce_test_lib"],
)

objc_library(
    name = "relu_test_lib",
    testonly = 1,
    srcs = ["relu_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:relu_test_util",
    ],
)

ios_unit_test(
    name = "relu_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":relu_test_lib"],
)

objc_library(
    name = "resize_test_lib",
    testonly = 1,
    srcs = ["resize_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:resize_test_util",
    ],
)

ios_unit_test(
    name = "resize_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":resize_test_lib"],
)

objc_library(
    name = "reshape_test_lib",
    testonly = 1,
    srcs = ["reshape_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:reshape_test_util",
    ],
)

ios_unit_test(
    name = "reshape_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":reshape_test_lib"],
)

objc_library(
    name = "slice_test_lib",
    testonly = 1,
    srcs = ["slice_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:strided_slice_test_util",
    ],
)

ios_unit_test(
    name = "slice_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":slice_test_lib"],
)

objc_library(
    name = "softmax_test_lib",
    testonly = 1,
    srcs = ["softmax_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:softmax_test_util",
    ],
)

ios_unit_test(
    name = "softmax_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":softmax_test_lib"],
)

objc_library(
    name = "space_to_depth_test_lib",
    testonly = 1,
    srcs = ["space_to_depth_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:space_to_depth_test_util",
    ],
)

ios_unit_test(
    name = "space_to_depth_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":space_to_depth_test_lib"],
)

cc_library(
    name = "transpose_conv",
    srcs = ["transpose_conv.cc"],
    hdrs = ["transpose_conv.h"],
    deps = [
        ":util",
        "//tensorflow/lite/delegates/gpu/common:gpu_info",
        "//tensorflow/lite/delegates/gpu/common:operations",
        "//tensorflow/lite/delegates/gpu/common:shape",
        "//tensorflow/lite/delegates/gpu/common:util",
        "//tensorflow/lite/delegates/gpu/common/task:gpu_operation",
        "@com_google_absl//absl/strings",
    ],
)

objc_library(
    name = "transpose_conv_test_lib",
    testonly = 1,
    srcs = ["transpose_conv_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        ":transpose_conv",
        "//tensorflow/lite/delegates/gpu/common/tasks:convolution_transposed_4x4_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:convolution_transposed_test_util",
    ],
)

ios_unit_test(
    name = "transpose_conv_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":transpose_conv_test_lib"],
)

objc_library(
    name = "transpose_test_lib",
    testonly = 1,
    srcs = ["transpose_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:transpose_test_util",
    ],
)

ios_unit_test(
    name = "transpose_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":transpose_test_lib"],
)

objc_library(
    name = "test_util",
    testonly = 1,
    srcs = [
        "test_util.cc",
    ],
    hdrs = ["test_util.h"],
    copts = [
        "-ObjC++",
    ],
    sdk_frameworks = [
        "Metal",
    ],
    deps = [
        "//tensorflow/lite/delegates/gpu/common:convert",
        "//tensorflow/lite/delegates/gpu/common:gpu_info",
        "//tensorflow/lite/delegates/gpu/common:operations",
        "//tensorflow/lite/delegates/gpu/common:precision",
        "//tensorflow/lite/delegates/gpu/common:shape",
        "//tensorflow/lite/delegates/gpu/common:status",
        "//tensorflow/lite/delegates/gpu/common:tensor",
        "//tensorflow/lite/delegates/gpu/common:types",
        "//tensorflow/lite/delegates/gpu/common:util",
        "//tensorflow/lite/delegates/gpu/common/task:gpu_operation",
        "//tensorflow/lite/delegates/gpu/common/task:testing_util",
        "//tensorflow/lite/delegates/gpu/metal:common",
        "//tensorflow/lite/delegates/gpu/metal:compute_task",
        "//tensorflow/lite/delegates/gpu/metal:metal_device",
        "//tensorflow/lite/delegates/gpu/metal:metal_spatial_tensor",
        "@FP16",
        "@com_google_absl//absl/memory",
        "@com_google_absl//absl/strings",
    ],
)

cc_library(
    name = "util",
    srcs = ["util.cc"],
    hdrs = ["util.h"],
    deps = [
        "//tensorflow/lite/delegates/gpu/common:data_type",
        "//tensorflow/lite/delegates/gpu/common:types",
    ],
)

cc_library(
    name = "winograd",
    srcs = ["winograd.cc"],
    hdrs = ["winograd.h"],
    deps = [
        ":util",
        "//tensorflow/lite/delegates/gpu/common:operations",
        "//tensorflow/lite/delegates/gpu/common:shape",
        "//tensorflow/lite/delegates/gpu/common:types",
        "//tensorflow/lite/delegates/gpu/common:util",
        "//tensorflow/lite/delegates/gpu/common:winograd_util",
        "//tensorflow/lite/delegates/gpu/common/task:gpu_operation",
        "@com_google_absl//absl/strings:str_format",
    ],
)

objc_library(
    name = "winograd_test_lib",
    testonly = 1,
    srcs = ["winograd_test.mm"],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":test_util",
        ":winograd",
        "//tensorflow/lite/delegates/gpu/common:winograd_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:winograd_test_util",
    ],
)

ios_unit_test(
    name = "winograd_test",
    testonly = 1,
    minimum_os_version = "11.0",
    runner = tflite_ios_lab_runner("IOS_LATEST"),
    tags = tf_gpu_tests_tags() + [
        "notap",
        "tflite_not_portable_android",
    ],
    deps = [":winograd_test_lib"],
)

objc_library(
    name = "kernel_tests_lib",
    testonly = 1,
    srcs = [
        "add_test.mm",
        "concat_test.mm",
        "conv_test.mm",
        "conv_weights_converter_test.mm",
        "depthwise_conv_test.mm",
        "elementwise_test.mm",
        "fully_connected_test.mm",
        "lstm_test.mm",
        "max_unpooling_test.mm",
        "mean_stddev_normalization_test.mm",
        "padding_test.mm",
        "pooling_test.mm",
        "prelu_test.mm",
        "quantize_and_dequantize_test.mm",
        "reduce_test.mm",
        "relu_test.mm",
        "reshape_test.mm",
        "resize_test.mm",
        "slice_test.mm",
        "softmax_test.mm",
        "space_to_depth_test.mm",
        "transpose_conv_test.mm",
        "transpose_test.mm",
        "winograd_test.mm",
    ],
    hdrs = [
    ],
    sdk_frameworks = ["XCTest"],
    deps = [
        ":conv",
        ":test_util",
        ":transpose_conv",
        ":winograd",
        "//tensorflow/lite/delegates/gpu/common:gpu_info",
        "//tensorflow/lite/delegates/gpu/common:precision",
        "//tensorflow/lite/delegates/gpu/common:shape",
        "//tensorflow/lite/delegates/gpu/common:types",
        "//tensorflow/lite/delegates/gpu/common:util",
        "//tensorflow/lite/delegates/gpu/common/tasks:add_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:concat_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:conv_weights_converter_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:convolution_transposed_4x4_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:convolution_transposed_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:depthwise_conv_3x3_stride_h2_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:depthwise_conv_3x3_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:depthwise_conv_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:elementwise_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:fully_connected_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:lstm_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:max_unpooling_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:mean_stddev_normalization_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:padding_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:pooling_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:prelu_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:quantize_and_dequantize_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:reduce_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:relu_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:reshape_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:resize_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:softmax_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:space_to_depth_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:strided_slice_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:transpose_test_util",
        "//tensorflow/lite/delegates/gpu/common/tasks:winograd_test_util",
        "//tensorflow/lite/delegates/gpu/metal:common",
    ],
)

tflite_portable_test_suite()

tflite_ios_per_kernel_test()
