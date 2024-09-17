podman build -t tableye-db .
podman build -t tableye-app .

podman network create casino-network

podman run -d --name db --network casino-network tableye-db
podman run -d --name app --network casino-network -p 8080:8080 tableye-app
