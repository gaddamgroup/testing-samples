FROM runmymind/docker-android-sdk:latest

# Installing build tools
RUN apt-get update && \
  apt-get install -y \
  build-essential \
  ruby \
  ruby-dev

# Installing bundle
RUN gem install bundle

# Installing fastlane
RUN gem install rake
RUN gem install fastlane -NV
