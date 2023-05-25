# taski-docker

Сборка и загрузка образов
docker build -t densad/taski_backend:latest backend/
docker build -t densad/taski_frontend:latest frontend/

docker push densad/taski_backend:latest
docker push densad/taski_frontend:latest 

cd backend
docker buildx build --platform=linux/amd64 -t densad/taski_backend .
cd ../frontend
docker buildx build --platform=linux/amd64 -t densad/taski_frontend .
cd ../gateway
docker buildx build --platform=linux/amd64 -t densad/taski_gateway .
docker push densad/taski_backend
docker push densad/taski_frontend
docker push densad/taski_gateway 