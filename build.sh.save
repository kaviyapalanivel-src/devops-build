echo "Building Docker Image..."

docker build -t react-app:latest .

echo "Tagging image for DockerHub DEV repo..."

docker tag react-app:latest kaviyapalaniveel/dev:latest

echo "Pushing image to DockerHub DEV repo..."

docker push kaviyapalaniveel/dev:latest
