#REPO: osrgroup/amos-java-build-image:1.0
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

FROM osrgroup/amos-build-base-image:1.0

# --------------------------------------  Install JDK 8

RUN /usr/bin/add-apt-repository -y "ppa:openjdk-r/ppa" \
  && apt-get -y update \
  && apt-get -y --no-install-recommends install \
    openjdk-8-jdk openjdk-8-jre-headless \
  && scrub_image

ENV JAVA_HOME /usr/lib/jvm/java-8-openjdk-amd64

# -------------------------------------- Install Maven 3

ENV MAVEN_VERSION 3.3.1
ENV M2_HOME /usr/share/maven
ENV MAVEN_OPTS -Xmx1g -XX:+CMSClassUnloadingEnabled -XX:+UseConcMarkSweepGC

RUN wget "http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz" -O - \
    | tar xzf - -C /usr/share \
  && mv /usr/share/apache-maven-$MAVEN_VERSION /usr/share/maven \
  && ln -s /usr/share/maven/bin/mvn /usr/bin/mvn \
  && scrub_image

# -------------------------------------- Install gradle

# http://linuxg.net/how-to-install-gradle-2-1-on-ubuntu-14-10-ubuntu-14-04-ubuntu-12-04-and-derivatives/
RUN add-apt-repository -y ppa:cwchien/gradle \
  && apt-get -y update \
  && apt-get -y install gradle \
  && scrub_image

# -------------------------------------- Done
