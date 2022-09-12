FROM debian:11.3
LABEL MAINTAINER="Ronan MOREL <ronanmorel@outlook.fr>"
USER root

# Install base packages
RUN apt-get update && apt-get upgrade -y && apt-get install -y nano curl git g++ gcc make build-essential unzip openjdk-11-jdk && \
	mkdir -p /opt && cd /opt && \
	curl -L https://downloads.gradle-dn.com/distributions/gradle-7.4.2-bin.zip -o gradle.zip && \
	unzip gradle.zip && rm gradle.zip

# Environnement variables pour android tools
ENV JAVA_HOME /usr/lib/jvm/java-11-openjdk-amd64
ENV GRADLE_HOME /opt/gradle-7.4.2
ENV ANDROID_SDK_ROOT /opt/android-sdk
ENV FLUTTER_HOME /opt/flutter-2.2.3

# Install android SDK, tools and platforms
RUN mkdir -p ${ANDROID_SDK_ROOT}/cmdline-tools && cd ${ANDROID_SDK_ROOT}/cmdline-tools && \
  curl -L https://dl.google.com/android/repository/commandlinetools-linux-8512546_latest.zip -o commandlinetools.zip && \
  unzip commandlinetools.zip && rm commandlinetools.zip && mv cmdline-tools tools && \
  ln -s ${ANDROID_SDK_ROOT}/cmdline-tools/tools ${ANDROID_SDK_ROOT}/tools

RUN cd ${ANDROID_SDK_ROOT}/cmdline-tools/tools/bin && \
  yes | ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --licenses && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} --update && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "platform-tools" "platforms;android-33" && \
  ./sdkmanager --sdk_root=${ANDROID_SDK_ROOT} "build-tools;33.0.0"

# Install Flutter
RUN cd /opt && \
  curl -L https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_2.2.3-stable.tar.xz -o flutter.tar.xz && \
  tar -xvf flutter.tar.xz && rm -f flutter.tar.xz && mv flutter flutter-2.2.3 && ${FLUTTER_HOME}/bin/flutter precache

# Add sdkmanager & android tools in path
ENV PATH $PATH:${ANDROID_SDK_ROOT}/platform-tools/:${ANDROID_SDK_ROOT}/cmdline-tools/tools/bin/:${GRADLE_HOME}/bin:${FLUTTER_HOME}/bin

WORKDIR /app