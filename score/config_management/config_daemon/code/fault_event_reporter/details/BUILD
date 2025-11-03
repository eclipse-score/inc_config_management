# *******************************************************************************
# Copyright (c) 2025 Contributors to the Eclipse Foundation
#
# See the NOTICE file(s) distributed with this work for additional
# information regarding copyright ownership.
#
# This program and the accompanying materials are made available under the
# terms of the Apache License Version 2.0 which is available at
# https://www.apache.org/licenses/LICENSE-2.0
#
# SPDX-License-Identifier: Apache-2.0
# *******************************************************************************

COMMON_FEATURES = [
    "treat_warnings_as_errors",
    "strict_warnings",
    "additional_warnings",
]

[
    cc_library(
        name = "details_score_impl" + name,
        srcs = [
            "fault_event_reporter_score_impl.cpp",
        ],
        hdrs = [
            "fault_event_reporter_score_impl.h",
        ],
        features = COMMON_FEATURES,
        tags = ["FFI"],
        visibility = [
            "@score-config_management//score/config_management/config_daemon/code:__subpackages__",
        ],
        deps = [
            "@score-config_management//score/config_management/config_daemon/code/fault_event_reporter",
            "@score-config_management//score/config_management/config_daemon/code/fault_event_reporter:fault_event_score_types",
        ] + dependencies,
    )
    for name, dependencies, test_only in [
        (
            "",
            [],
            False,
        ),
        (
            "_for_test",
            ["@googletest//:gtest_main"],
            True,
        ),
    ]
]

cc_test(
    name = "unit_test",
    srcs = ["fault_event_reporter_score_impl_test.cpp"],
    features = [
        "treat_warnings_as_errors",
        "strict_warnings",
        "additional_warnings",
    ],
    tags = ["unit"],
    visibility = [
        "@score-config_management//score/config_management/config_daemon:__subpackages__",
    ],
    deps = [":details_score_impl_for_test"],
)
