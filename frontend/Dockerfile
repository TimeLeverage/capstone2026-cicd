# 1단계: 빌드 (Node.js 환경)
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
# 여기서 index.html과 JS 파일들이 build 폴더로 합쳐집니다.
RUN npm run build

# 2단계: 배포 (Nginx 환경)
FROM nginx:stable-alpine
# 핵심: 빌드된 결과물 전체를 Nginx의 기본 웹 서비스 폴더로 복사합니다.
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]