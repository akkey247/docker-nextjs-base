FROM node:current-slim

# 各種パッケージをインストール
RUN apt-get update \
  && apt-get install -y curl vim git gh mariadb-client

# pnpm をインストール
RUN npm install -g pnpm@latest

# MailHog でメールを受信できるように設定
RUN curl -sSL https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64 -o mhsendmail \
    && chmod +x mhsendmail \
    && mv mhsendmail /usr/local/bin/mhsendmail

# GitHub 設定
RUN git config --global user.email "temporary_user@example.com" && git config --global user.name "Temporary User"

# 日本語入力できるように設定
ENV LANG C.UTF-8
ENV LANGUAGE en_US:

# 作業ディレクトリ設定
WORKDIR /var/www

# www ディレクトリの中身をクリアするコマンドをコンテナにコピー
COPY clear-www /usr/local/bin/
RUN chmod 755 /usr/local/bin/clear-www

# Next.js をインストール
RUN cd /var && pnpm dlx create-next-app -e https://github.com/vercel/next.js/tree/canary/examples/hello-world www
