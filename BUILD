# -*- mode: python -*-
# vi: set ft=python :

#
# BUILD
# AVO2 Library
#
# Copyright 2010 University of North Carolina at Chapel Hill
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# Please send all bug reports to <geom@cs.unc.edu>.
#
# The authors may be contacted via:
#
# Jur van den Berg, Jamie Snape, Stephen J. Guy, and Dinesh Manocha
# Dept. of Computer Science
# 201 S. Columbia St.
# Frederick P. Brooks, Jr. Computer Science Bldg.
# Chapel Hill, N.C. 27599-3175
# United States of America
#
# <http://gamma.cs.unc.edu/AVO/>
#

load("@bazel_tools//tools/build_defs/pkg:pkg.bzl", "pkg_deb", "pkg_tar")

licenses(["notice"])

exports_files(["LICENSE"])

pkg_tar(
    name = "doc",
    srcs = ["LICENSE"],
    mode = "0644",
    package_dir = "/usr/share/doc/AVO",
    visibility = ["//visibility:private"],
)

genrule(
    name = "pc",
    outs = ["AVO.pc"],
    cmd = """
cat << 'EOF' > $@
#
# AVO.pc
# AVO2 Library
#
# Copyright 2010 University of North Carolina at Chapel Hill
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
# Please send all bug reports to <geom@cs.unc.edu>.
#
# The authors may be contacted via:
#
# Jur van den Berg, Jamie Snape, Stephen J. Guy, and Dinesh Manocha
# Dept. of Computer Science
# 201 S. Columbia St.
# Frederick P. Brooks, Jr. Computer Science Bldg.
# Chapel Hill, N.C. 27599-3175
# United States of America
#
# <http://gamma.cs.unc.edu/AVO/>
#

prefix=/usr
exec_prefix=$${prefix}
libdir=$${exec_prefix}/lib
includedir=$${prefix}/include/AVO

Name: AVO2 Library
Description: Reciprocal Collision Avoidance with Acceleration-Velocity Obstacles
URL: http://gamma.cs.unc.edu/AVO/
Version: 1.0.0
Libs: -L$${libdir} -lAVO
Cflags: -I$${includedir}
EOF
""",
    visibility = ["//visibility:private"],
)

pkg_tar(
    name = "pkgconfig",
    srcs = ["AVO.pc"],
    mode = "0644",
    package_dir = "/usr/lib/pkgconfig",
    visibility = ["//visibility:private"],
)

pkg_tar(
    name = "AVO",
    extension = "tar.gz",
    visibility = ["//visibility:public"],
    deps = [
        ":doc",
        ":pkgconfig",
        "//src:include",
        "//src:lib",
    ],
)

pkg_deb(
    name = "deb",
    architecture = "amd64",
    data = ":AVO",
    depends = [
        "libc6",
        "libgcc1",
        "libstdc++6",
    ],
    description = "Reciprocal Collision Avoidance with Acceleration-Velocity Obstacles",
    homepage = "http://gamma.cs.unc.edu/AVO/",
    maintainer = "Jamie Snape",
    package = "avo",
    version = "1.0.0",
    visibility = ["//visibility:public"],
)
