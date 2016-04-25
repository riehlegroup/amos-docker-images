#REPO: osrgroup/amos-android-build-image:1.0
#PUSH!
#
# Copyright 2016 The Open Source Research Group,
#                University of Erlangen-Nürnberg
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

FROM osrgroup/amos-java-build-image:1.0

# -------------------------------------- Install Android Studio & SDK

# https://hub.docker.com/r/webratio/android-sdk/~/dockerfile/
ENV ANDROID_SDK_VERSION r24.4.1
ENV ANDROID_BUILD_TOOLS_VERSION 23.0.3

RUN dpkg --add-architecture i386 \
  && apt-get -y update \
  && apt-get -y install \
    libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 \
  && scrub_image

ENV ANDROID_SDK_FILENAME android-sdk_${ANDROID_SDK_VERSION}-linux.tgz
ENV ANDROID_SDK_URL http://dl.google.com/android/${ANDROID_SDK_FILENAME}
ENV ANDROID_API_LEVELS android-15,android-16,android-17,android-18,android-19,android-20,android-21,android-22,android-23
ENV ANDROID_HOME /opt/android-sdk-linux
ENV PATH ${PATH}:${ANDROID_HOME}/tools:${ANDROID_HOME}/platform-tools

RUN cd /opt \
  && wget -q ${ANDROID_SDK_URL} \
  && tar -xzf ${ANDROID_SDK_FILENAME} \
  && rm ${ANDROID_SDK_FILENAME} \
  && echo y | android update sdk --no-ui -a --filter tools,platform-tools,${ANDROID_API_LEVELS},build-tools-${ANDROID_BUILD_TOOLS_VERSION} \
  && scrub_image

# -------------------------------------- Done
