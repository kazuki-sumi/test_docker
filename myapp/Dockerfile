# 使用するイメージを指定
FROM ruby:2.6.3
# Linuxコンテナ内で使用する言語形式(locale)を設定
ENV LANG C.UTF-8

# -qq エラー以外は表示しない
# 必要なパッケージをインストール
RUN apt-get update -qq && apt-get install -y \
    build-essential \
    nodejs \
 # aptキャッシュをクリーンにし、 /var/lib/apt/lits を削除することで、イメージのサイズを減らす
 && rm -rf /var/lib/apt/lists/*

RUN gem install bundler

WORKDIR /tmp
ADD Gemfile Gemfile
ADD Gemfile.lock Gemfile.lock
RUN bundle install

ENV APP_HOME /myapp
RUN mkdir -p $APP_HOME
WORKDIR $APP_HOME
ADD . $APP_HOME
