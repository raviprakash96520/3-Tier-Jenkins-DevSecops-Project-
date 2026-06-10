FROM nginx:mainline-alpine3.20-slim

RUN rm -rf /etc/nginx/nginx.conf && \
    rm -rf /etc/nginx/conf.d/default.conf && \
    mkdir -p /var/cache/nginx/client_temp && \
    mkdir -p /var/cache/nginx/proxy_temp && \
    mkdir -p /var/cache/nginx/fastcgi_temp && \
    mkdir -p /var/cache/nginx/uwsgi_temp && \
    mkdir -p /var/cache/nginx/scgi_temp && \
    chown -R nginx:nginx /var/cache/nginx && \
    chown -R nginx:nginx /etc/nginx/ && \
    chmod -R 755 /etc/nginx/ && \
    chown -R nginx:nginx /var/log/nginx && \
    touch /var/run/nginx.pid && \
    chown -R nginx:nginx /var/run/nginx.pid /run/nginx.pid

COPY nginx.conf /etc/nginx/nginx.conf

# --- ఇక్కడ మార్చండి ---

# 1. మొదట index.html ని డైరెక్ట్ గా html ఫోల్డర్ లోకి కాపీ చేయండి
COPY index.html /usr/share/nginx/html/

# 2. ఆ తర్వాత 'code/static/' లో ఉన్న ఫైల్స్ ని నేరుగా html/static/ లోకి కాపీ చేయండి
COPY code/static/ /usr/share/nginx/html/static/

# ---------------------

# Ensure static files are owned by nginx user so the process can read them
RUN chown -R nginx:nginx /usr/share/nginx/html
USER nginx