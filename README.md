# MyMicroservice
# Deploy a microservice to Azure
https://dotnet.microsoft.com/en-us/learn/aspnet/deploy-microservice-tutorial/intro

Step 1 -
1. Create new .net app
   (dotnet new webapi -o MyMicroservice --no-https -f net7.0)
2. Create Dockerfile
3. Build Docker image (docker build -t mymicroservice .) (. -> final parameter tells it which directory to use to find the Dockerfile)

Step 2 -
1. Upload image to Docker Hub (docker tag mymicroservice khintdsoe/mymicroservice)
2. docker push khintdsoe/mymicroservice

Step 3 - Set up Azure tools
1. Create a resource group(az group create --name MyMicroserviceResources --location westus)
2. Create  an aks cluster (az aks create --resource-group MyMicroserviceResources --name MyMicroserviceCluster --node-count 1 --enable-addons http_application_routing --generate-ssh-keys)
3. Download the credentials to deploy to your AKS cluster (az aks get-credentials --resource-group MyMicroserviceResources --name MyMicroserviceCluster)

Step 4 - Deploy to Azure
The AKS tools use a .yaml file to define how to deploy your container.

1. Create .yaml file
2. Deploy your microservice (kubectl apply -f deploy.yaml)
3. Test your deployed service (kubectl get service mymicroservice --watch)
4. Check with http://[YOUR EXTERNAL IP ADDRESS]/WeatherForecast

Step 5 - Clean up resources
1. Delete all resources that you created (az group delete -n MyMicroserviceResources)


   





