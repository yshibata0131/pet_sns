FROM ruby:2.7

# 必要なパッケージのインストール（基本的に必要になってくるものだと思うので削らないこと）
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update -qq && \
    apt-get install -y build-essential \ 
                       libpq-dev \        
                       nodejs \
                       yarn

# 作業ディレクトリの作成、設定
RUN mkdir /pet_sns 
##作業ディレクトリ名をAPP_ROOTに割り当てて、以下$APP_ROOTで参照
ENV APP_ROOT /pet_sns 
WORKDIR $APP_ROOT

# ホストのGemfileを追加する
ADD ./backend/Gemfile $APP_ROOT/Gemfile
ADD ./backend/Gemfile.lock $APP_ROOT/Gemfile.lock

# Gemfileのbundle install
RUN bundle install
ADD . $APP_ROOT
