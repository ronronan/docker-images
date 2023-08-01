FROM debian:12.1-slim
LABEL MAINTAINER="Ronan MOREL <me@3rm.fr>"
USER root

ENV GRADLE_VERSION "7.6.2"
ENV FLUTTER_VERSION "3.7.12"

# Install base packages
RUN groupadd -r flutterdev -g 1000 && useradd -u 1000 -r -g flutterdev flutterdev && \
  mkdir -p /home/flutterdev && chown flutterdev:flutterdev /home/flutterdev && \
  mkdir -p /opt && chmod 777 /opt && \
  apt-get update && apt-get upgrade -y && \
  apt-get install -y nano curl git g++ gcc make build-essential clang cmake unzip ninja-build pkg-config libgtk-3-dev && \
  apt-get install -y openjdk-17-jdk && apt-get clean

USER flutterdev

# Install Gradle
RUN cd /opt && curl -L https://downloads.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o gradle.zip && \
  unzip gradle.zip && rm gradle.zip

# Environnement variables pour android tools
ENV JAVA_HOME /usr/lib/jvm/java-17-openjdk-amd64
ENV GRADLE_HOME /opt/gradle-${GRADLE_VERSION}
ENV ANDROID_SDK_ROOT /opt/android-sdk
ENV FLUTTER_HOME /opt/flutter-${FLUTTER_VERSION}

# Install android SDK, tools and platforms
RUN mkdir -p ${ANDROID_SDK_ROOT}/cmdline-tools && cd ${ANDROID_SDK_ROOT}/cmdline-tools && \
  curl -L https://dl.google.com/android/repository/commandlinetools-linux-9477386_latest.zip -o commandlinetools.zip && \
  unzip commandlinetools.zip && rm commandlinetools.zip && mv cmdline-tools 9.0

RUN cd ${ANDROID_SDK_ROOT}/cmdline-tools/9.0/bin && \
  yes | ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --licenses && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --update && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-34" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-28" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-30" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-31" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-33" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "build-tools;34.0.0" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "build-tools;30.0.3"

# Install Flutter
RUN cd /opt && \
  curl -L https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}-stable.tar.xz -o flutter.tar.xz && \
  tar -xvf flutter.tar.xz && rm -f flutter.tar.xz && mv flutter flutter-${FLUTTER_VERSION} && \
  git config --global --add safe.directory $FLUTTER_HOME && ${FLUTTER_HOME}/bin/flutter precache

# Add sdkmanager & android tools in path
ENV PATH $PATH:${ANDROID_SDK_ROOT}/platform-tools/:${ANDROID_SDK_ROOT}/cmdline-tools/9.0/bin/:${GRADLE_HOME}/bin:${FLUTTER_HOME}/bin

WORKDIR /app
