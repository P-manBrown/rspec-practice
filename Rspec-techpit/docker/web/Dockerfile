FROM nginx:1.21.6

ENV USER_NAME=myuser

# インクルード用のディレクトリ内を削除
RUN rm -f /etc/nginx/conf.d/*

# Nginxの設定ファイルをコンテナにコピー
COPY nginx.conf /etc/nginx/conf.d/myapp.conf

RUN adduser ${USER_NAME} && \
    chown -R ${USER_NAME} /var/cache/nginx/ && \
    chown -R ${USER_NAME} /var/run/
USER ${USER_NAME}

# ビルド完了後にNginxを起動
CMD /usr/sbin/nginx -g 'daemon off;' -c /etc/nginx/nginx.conf