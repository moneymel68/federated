load("@rules_python//python:defs.bzl", "py_library", "py_test")

package_group(
    name = "default_visibility",
    includes = ["//tensorflow_federated/python/simulation:simulation_visibility"],
    packages = [
        # Subpackages
        "//tensorflow_federated/python/simulation/datasets/...",

        # TODO(b/182305417): Delete this once the full deprecation period has
        # passed.
        "//tensorflow_federated/python/simulation",
    ],
)

package(default_visibility = [":default_visibility"])

licenses(["notice"])

py_library(
    name = "datasets",
    srcs = ["__init__.py"],
    srcs_version = "PY3",
    visibility = ["//tensorflow_federated/python/simulation:__pkg__"],
    deps = [
        ":cifar100",
        ":client_data",
        ":dataset_utils",
        ":emnist",
        ":file_per_user_client_data",
        ":gldv2",
        ":shakespeare",
        ":sql_client_data",
        ":stackoverflow",
        ":transforming_client_data",
    ],
)

py_library(
    name = "cifar100",
    srcs = ["cifar100.py"],
    srcs_version = "PY3",
    deps = [
        ":download",
        ":sql_client_data",
    ],
)

py_test(
    name = "cifar100_test",
    size = "medium",
    srcs = ["cifar100_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    tags = [
        "external",
        "guitar",
        "manual",
        "nokokoro",
        "notap",
    ],
    deps = [":cifar100"],
)

py_library(
    name = "dataset_utils",
    srcs = ["dataset_utils.py"],
    srcs_version = "PY3",
)

py_test(
    name = "dataset_utils_test",
    size = "small",
    srcs = ["dataset_utils_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":client_data",
        ":dataset_utils",
    ],
)

py_library(
    name = "download",
    srcs = ["download.py"],
    srcs_version = "PY3",
)

py_test(
    name = "download_test",
    size = "small",
    srcs = ["download_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":download"],
)

py_library(
    name = "emnist",
    srcs = ["emnist.py"],
    srcs_version = "PY3",
    deps = [
        ":download",
        ":from_tensor_slices_client_data",
        ":sql_client_data",
        ":transforming_client_data",
        "//tensorflow_federated/python/common_libs:py_typecheck",
    ],
)

py_test(
    name = "emnist_test",
    timeout = "long",
    srcs = ["emnist_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":emnist"],
)

py_library(
    name = "shakespeare",
    srcs = ["shakespeare.py"],
    srcs_version = "PY3",
    deps = [
        ":client_data",
        ":download",
        ":from_tensor_slices_client_data",
        ":sql_client_data",
    ],
)

py_test(
    name = "shakespeare_test",
    size = "small",
    srcs = ["shakespeare_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":shakespeare"],
)

py_library(
    name = "stackoverflow",
    srcs = ["stackoverflow.py"],
    srcs_version = "PY3",
    deps = [
        ":download",
        ":from_tensor_slices_client_data",
        ":sql_client_data",
    ],
)

py_test(
    name = "stackoverflow_test",
    size = "medium",
    srcs = ["stackoverflow_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":stackoverflow"],
)

py_library(
    name = "gldv2",
    srcs = ["gldv2.py"],
    srcs_version = "PY3",
    deps = [
        ":client_data",
        ":file_per_user_client_data",
    ],
)

py_test(
    name = "gldv2_test",
    size = "small",
    srcs = ["gldv2_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":gldv2"],
)

py_library(
    name = "client_data",
    srcs = ["client_data.py"],
    srcs_version = "PY3",
    deps = [
        "//tensorflow_federated/python/common_libs:py_typecheck",
        "//tensorflow_federated/python/core/api:computation_base",
        "//tensorflow_federated/python/core/api:computations",
    ],
)

py_test(
    name = "client_data_test",
    size = "small",
    srcs = ["client_data_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [":client_data"],
)

py_library(
    name = "file_per_user_client_data",
    srcs = ["file_per_user_client_data.py"],
    srcs_version = "PY3",
    deps = [
        ":client_data",
        "//tensorflow_federated/python/common_libs:py_typecheck",
        "//tensorflow_federated/python/core/api:computations",
        "//tensorflow_federated/python/tensorflow_libs:tensor_utils",
    ],
)

py_test(
    name = "file_per_user_client_data_test",
    size = "small",
    srcs = ["file_per_user_client_data_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":file_per_user_client_data",
        "//tensorflow_federated/python/core/api:computation_base",
        "//tensorflow_federated/python/core/backends/native:execution_contexts",
    ],
)

py_library(
    name = "from_tensor_slices_client_data",
    srcs = ["from_tensor_slices_client_data.py"],
    srcs_version = "PY3",
    deps = [
        ":client_data",
        "//tensorflow_federated/python/common_libs:py_typecheck",
        "//tensorflow_federated/python/core/api:computations",
    ],
)

py_test(
    name = "from_tensor_slices_client_data_test",
    size = "small",
    srcs = ["from_tensor_slices_client_data_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":from_tensor_slices_client_data",
        "//tensorflow_federated/python/core/api:computation_base",
        "//tensorflow_federated/python/core/api:computation_types",
        "//tensorflow_federated/python/core/backends/native:execution_contexts",
    ],
)

py_library(
    name = "sql_client_data",
    srcs = ["sql_client_data.py"],
    srcs_version = "PY3",
    deps = [
        ":client_data",
        "//tensorflow_federated/python/common_libs:py_typecheck",
        "//tensorflow_federated/python/core/api:computations",
    ],
)

py_test(
    name = "sql_client_data_test",
    size = "small",
    srcs = ["sql_client_data_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":sql_client_data",
        "//tensorflow_federated/python/core/backends/native:execution_contexts",
    ],
)

py_library(
    name = "transforming_client_data",
    srcs = ["transforming_client_data.py"],
    srcs_version = "PY3",
    deps = [
        ":client_data",
        "//tensorflow_federated/python/common_libs:py_typecheck",
    ],
)

py_test(
    name = "transforming_client_data_test",
    size = "small",
    srcs = ["transforming_client_data_test.py"],
    python_version = "PY3",
    srcs_version = "PY3",
    deps = [
        ":from_tensor_slices_client_data",
        ":transforming_client_data",
    ],
)
