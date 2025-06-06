FROM eclipse-temurin:21-jdk-jammy
LABEL MAINTAINER="Ronan MOREL <me@3rm.fr>"
USER root

# Install base packages
RUN (userdel -f ubuntu || true ) && groupadd -r flutterdev -g 1000 && useradd -u 1000 -r -g flutterdev flutterdev && \
  mkdir -p /home/flutterdev && chown flutterdev:flutterdev /home/flutterdev && \
  mkdir -p /opt && chmod 777 /opt && \
  apt-get update && apt-get upgrade -y && \
  apt-get install -y nano curl git g++ gcc make build-essential clang cmake unzip ninja-build pkg-config libgtk-3-dev && \
  apt-get clean

ENV GRADLE_VERSION=8.14.1 \
    FLUTTER_VERSION=3.32.1
USER flutterdev

# Install Gradle
RUN cd /opt && curl -L https://downloads.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip -o gradle.zip && \
  unzip gradle.zip && rm gradle.zip

# Environnement variables pour android tools
ENV JAVA_HOME=/opt/java/openjdk \
    GRADLE_HOME=/opt/gradle-${GRADLE_VERSION} \
    ANDROID_SDK_ROOT=/opt/android-sdk \
    FLUTTER_HOME=/opt/flutter-${FLUTTER_VERSION}

# Install android SDK, tools and platforms
RUN mkdir -p ${ANDROID_SDK_ROOT}/cmdline-tools && cd ${ANDROID_SDK_ROOT}/cmdline-tools && \
  curl -L https://dl.google.com/android/repository/commandlinetools-linux-13114758_latest.zip -o commandlinetools.zip && \
  unzip commandlinetools.zip && rm commandlinetools.zip && mv cmdline-tools 19.0

RUN cd ${ANDROID_SDK_ROOT}/cmdline-tools/19.0/bin && \
  yes | ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --licenses && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --update && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-31" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-33" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-34" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-35" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "ndk;27.0.12077973" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "build-tools;34.0.0" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "cmake;3.22.1"

# Install Flutter
RUN cd /opt && \
  curl -L https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_${FLUTTER_VERSION}-stable.tar.xz -o flutter.tar.xz && \
  tar -xvf flutter.tar.xz && rm -f flutter.tar.xz && mv flutter flutter-${FLUTTER_VERSION} && \
  git config --global --add safe.directory $FLUTTER_HOME && ${FLUTTER_HOME}/bin/flutter precache

# Add sdkmanager & android tools in path
ENV PATH=$PATH:${ANDROID_SDK_ROOT}/platform-tools/:${ANDROID_SDK_ROOT}/cmdline-tools/19.0/bin/:${GRADLE_HOME}/bin:${FLUTTER_HOME}/bin

WORKDIR /app
