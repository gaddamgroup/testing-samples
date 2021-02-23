FROM openjdk:8

LABEL Vijay <gvreddy579@gmail.com>

ENV ANDROID_SDK_URL https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip
ENV ANDROID_HOME /usr/local/android-sdk-linux
ENV PATH $PATH=$ANDROID_HOME/tools:$ANDROID_HOME/tools/bin:$ANDROID_HOME/platform-tools:$ANDROID_HOME/build-tools:$PATH

USER root

RUN mkdir "$ANDROID_HOME" .android && \
    cd "$ANDROID_HOME" && \
    curl -o sdk.zip $ANDROID_SDK_URL && \
    unzip sdk.zip && \
    rm sdk.zip && \
    # Download Android SDK
    yes | sdkmanager --licenses && \
    sdkmanager --update && \
    sdkmanager "build-tools;29.0.3" && \
    sdkmanager "platforms;android-29" && \
    sdkmanager "platform-tools" && \
    sdkmanager "extras;android;m2repository" && \
    sdkmanager "extras;google;m2repository" && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    apt-get autoremove -y && \
    apt-get clean

# Install Fastlane
RUN apt-get update && \
    apt-get install --no-install-recommends -y --allow-unauthenticated build-essential git ruby-full && \
    # Clean up
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    apt-get autoremove -y && \
    apt-get clean

# Install Fastlane
RUN gem install rake && \
    gem install fastlane -NV && \
    gem install bundler && \
    # Clean up
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    apt-get autoremove -y && \
    apt-get clean