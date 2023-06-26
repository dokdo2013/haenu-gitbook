# CRA 앱 Dockerize하기

CRA (Create React App) 앱을 Dockerize 해보자. 일반적인 React 앱은 SPA (Single Page Application)로, CSR (Client Side Rendering)을 지원한다. 따라서 JSX로 작성된 코드를 빌드하여 나온 결과물은 Static HTML과 JS/CSS 파일로 구성되고, 이걸 정적으로 서빙하는 것이다. 따라서 먼저 빌드를 하고, 빌드 결과물을 Nginx로 서빙하도록 한다.

## Dockerfile

```docker
# Step 1: Build react application
FROM node:18 as build
WORKDIR /app
COPY package.json yarn.lock ./
RUN yarn install
COPY . ./
RUN yarn build

# Step 2: Serve app with nginx server
FROM nginx:stable-alpine as production
COPY --from=build /app/build /usr/share/nginx/html
# Copy the nginx.conf
COPY nginx.conf /etc/nginx/conf.d/default.conf

# Expose port 80
EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

## nginx.conf

```nginx
server {
    listen 80;
    location / {
        root /usr/share/nginx/html;
        index index.html index.htm;
        try_files $uri $uri/ /index.html;
    }
    error_page 500 502 503 504 /50x.html;
    location = /50x.html {
        root /usr/share/nginx/html;
    }
}
```

