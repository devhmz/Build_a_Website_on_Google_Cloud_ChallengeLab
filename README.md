# Build_a_Website_on_Google_Cloud_ChallengeLab
   
    Google Cloud Quicklabs : 


    Set the default zone and project configuration :
         gcloud config set compute/zone us-central1 

     
    Clone the the git repo : 
         git clone https://github.com/googlecodelabs/monolith-to-microservices.git

    Run setup.sh : 
         cd monolith-to-microservices
         ./setup.sh 

    Update Node : 
         nvm install --lts

  
    enable Cloud build  api :
         gcloud services enable cloudbuild.googleapis.com

    run Cloud Build to build it, then push it up to GCR. : 
         gcloud builds submit --tag  gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-monolith-584:1.0.0




   Task 2 : 
      
     enable container API : 
     gcloud services enable container.googleapis.com

     Set compute/zone : 
     gcloud config set compute/zone us-central1-a

     Create cluster : 
     gcloud container clusters create fancy-cluster-791 --num-nodes 3 
    
     Create Deployement: 
     kubectl create deployment fancy-monolith-107 --image=gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-monolith-107:1.0.0

     Expose Deployement : 
     kubectl expose deployment fancy-monolith-107 --type=LoadBalancer --port 80 --target-port 8080


   Task 3 : 
     
     Create a containerized version of your microservices
        
     cd ~/microservices/src/orders 
     gcloud builds submit --tag  gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-orders-988:1.0.0

      cd ~/microservices/src/products 
     gcloud builds submit --tag  gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-products-557:1.0.0

   
  Task 4 : 

       Create Deployement: 
     kubectl create deployment fancy-orders-988 --image=gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-orders-988:1.0.0

     Expose Deployement : 
     kubectl expose deployment fancy-orders-988 --type=LoadBalancer --port 80 --target-port 8081
   
     kubectl get svc -w 
    
     Create Deployement: 
     kubectl create deployment fancy-products-557 --image=gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-products-557:1.0.0

     Expose Deployement : 
     kubectl expose deployment fancy-products-557 --type=LoadBalancer --port 80 --target-port 8082

   
  Task 5 : 
    
    Replace the local URL with the IP address of the new Products microservices: 
         cd ~/monolith-to-microservices/react-app
         nano .env


  Task 6 : 

       Create a containerized version of your microservices
        
     cd ~/microservices/src/frontend
     gcloud builds submit --tag  gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-frontend-610:1.0.0
     npm run build


   Task 7 : 

        Create Deployement: 
     kubectl create deployment fancy-frontend-610 --image=gcr.io/${GOOGLE_CLOUD_PROJECT}/fancy-frontend-610:1.0.0

     Expose Deployement : 
     kubectl expose deployment fancy-frontend-610 --type=LoadBalancer --port 80 --target-port 8080
     
     
     
