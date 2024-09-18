# Jenkins-OKD-CICD-Pipline
<h2>Description</h2>
In this project we will deploy a multi-tier application using a kubernetes cluster, deploy to OKD, and create a Jenkins CICD Pipline integrated with Gitlab and monitored with Nagios 
<p align="center">
<img src="https://github.com/user-attachments/assets/6daaecae-75f4-40b4-ac1e-4ee0d789d18c"/>

<h2>Languages and Utilities Used</h2>



<h2>Environments Used </h2>

- <b>CentOS Linux release 8.5.2111
 10</b>

<h2>Project walk-through:</h2>
<p align="center">
 To begin add the required repositories for Foreman and Katello. Then install their dependencies  <br/>
<img src="https://github.com/user-attachments/assets/3c575f3e-b049-4253-b426-c32414c364cd"/>
 <img src="https://github.com/user-attachments/assets/1dcbe05e-ad71-42ba-b0a6-e898739b276c"/>
<br /> Next run the foreman installer <br/>
 <img src="https://github.com/user-attachments/assets/6897d7f4-1be5-4049-bc6f-c751fc62f3a2"/>
 <br /> 
 <br/> Check to be sure that the hostname matches <br/>
 <img src="https://github.com/user-attachments/assets/8b726cc7-de6d-42e1-8822-74fafd5feca9"/>
 <br />  
<br />
   <br/> Ensure that the yml file is configured properly  <br/> 
<img src="https://github.com/user-attachments/assets/9b72b69c-0fbb-4994-9301-b3e28d5b7422"/>
<br />
<br /> Once configuration is complete check the services <br/>
 <br/>
<img src="https://github.com/user-attachments/assets/83f466ef-e828-4a32-8a7c-834eaf5eaab2"/>
<br /> Now log view webserver ui by either hostname or ip addr specified <br/>
<h2> Kubernetes AKS multi-tier application </h2>
 <br /> Connect to Microsoft Azure from the command line ensure the az-cli package has been installed <br/>
 <img src="https://github.com/user-attachments/assets/4b20ed43-f3ca-406f-aa89-2ebc93fcbd08"/>
 <img src="https://github.com/user-attachments/assets/385d7272-2e53-4de1-b8af-c9d25be4b816"/>
 <img src="https://github.com/user-attachments/assets/56ae6689-94bf-45fa-966d-f2626931bec4"/>
 <br/>
 <br/> Create AKS cluster from the command line <br/> 
 <br/> Make sure the parameters are valid <br/>
 <img src="https://github.com/user-attachments/assets/1e6e60ef-200a-44ed-a54f-a3cf5c5a42ce"/>
 <img src="https://github.com/user-attachments/assets/e84a1931-985a-4b5f-9a22-b99f7dc7cc14"/>
 <img src="https://github.com/user-attachments/assets/23a92a6a-39b9-4661-8dea-cddac03a8a19"/>
<br/>
<br /> Next install OKD on the AKS cluster and confirm with oc version <br/>
 <br/>
<img src="https://github.com/user-attachments/assets/91dbc162-35e5-434e-95ea-2663a9d266c3"/>
 <img src="https://github.com/user-attachments/assets/648c3887-de5d-4386-bb8e-783e11b48459"/>
<br />
<br /> Install the OpenShift installer and select Azure when prompted   <br/> 
 <img src="https://github.com/user-attachments/assets/59d0086a-b972-4fe1-b1ee-933f756bd15a"/>
 <br/> Quick note: OKD can be setup with any of the cloud providers on the list it is not exclusive to Azure <br/>
 <br/>
 <br/>
 <br/> Run the following from the Azure portal or in another screen using the az-cli to access the ID info or view Microsoft Entra ID <br/>
 <img src="https://github.com/user-attachments/assets/12eab14d-9a6e-4e19-8137-86c9214b9bcd"/>
 <img src="https://github.com/user-attachments/assets/7a6e73e6-b889-4372-b656-26dbf03a3464"/>
<br/> Now that OKD has been established on the AKS its time to create the frontend and backend Dockerfiles for the application <br/>
 <br /> For the Database we create a docker file for sql and use nginx to access our web app UI  <br/>
 <br/> Build images out of the docker files and run them as container to test if they work before we push them to DockerHub <br/>
 <img src="https://github.com/user-attachments/assets/8ebda612-1a2d-4fe2-9e72-c7cc490a0600"/>
 <br/> Make sure to connect to DockerHub by running docker login <br/> 
 <br/> Now tag and push the images to your DockerHub repository 
 <img src="https://github.com/user-attachments/assets/4b8f074c-ff64-44a9-a0b2-41fb3a00fa21"/>
 <br/> Next create Kubernetes manifest and deployments <br/>
<img src="https://github.com/user-attachments/assets/fc199cfe-c191-413f-829d-d7c6553930e6"/>
 <img src="https://github.com/user-attachments/assets/7774c8cc-d2a6-430e-bf20-39eb60c895ba"/>
<br />
<br />  Now apply the manifest to the OKD Cluster <br/> 
 <img src="https://github.com/user-attachments/assets/b49b9345-0e24-43e7-aa6a-31494967354d"/>
 <br/> Confirm <br/>
 <img src="https://github.com/user-attachments/assets/abe082ef-a460-41be-9771-341b330345e9"/>
 <br/> Now lets make sure to set up ingress to expose the front end service<br/>
 <img src="https://github.com/user-attachments/assets/a868c117-9e8c-4cad-b8d8-6659b2c61721"/>
 <img src="https://github.com/user-attachments/assets/1542f177-3b03-454c-a77d-cb61246b5e53"/>
<br/><br /> <br/>
  Lets confirm connectivity to make sure our app can work and is accessible <br/>
<img src="https://github.com/user-attachments/assets/df6de183-ceb0-4690-ad32-0eea171decd4"/>
 <img src="https://github.com/user-attachments/assets/a63cb3af-d558-411c-839c-1de90c81ebea"/>
 <br/> To keep track of logs you can also run oc get events <br/>
 <img src="https://github.com/user-attachments/assets/391f7813-dbee-424c-8c77-3648e12db63e"/>
<br />
<br /> Next lets install Jenkins within our OKD cluster <br/> 
 <br/>
 <img src="https://github.com/user-attachments/assets/518b46c9-66a0-4d34-8cfc-f83f21c87893"/>
<br/> Now confirm <br /> 
 <img src="https://github.com/user-attachments/assets/7eb79b14-45ed-411a-a255-839e7978e69f"/>
 <br/>
 <br/>
 <br/> Now access the Jenkins UI in your browser <br/>
<img src="https://github.com/user-attachments/assets/100bddfe-3486-493c-ad78-4ef75e1142fb"/>
<br /> Navigate to plugins<br/>
 <img src="https://github.com/user-attachments/assets/53e6d9d5-20cc-4956-9fb5-088c1ddfc05f"/>
<br /> Search for Gitlab plugin and install<br/>
 <img src="https://github.com/user-attachments/assets/3cdb3f60-960e-43a4-95fe-5c00af68e32b"/>
 <img src="https://github.com/user-attachments/assets/fd5b8450-deef-47b5-8b23-98e5002d0d86"/>
 <img src="https://github.com/user-attachments/assets/0999d766-3cb0-4c3a-a7bd-a70369609c6c"/>
 <br/> Integrate Jenkins with Gitlab via link address, access tokens, etc... <br/>
 <img src="https://github.com/user-attachments/assets/aab15088-e599-4c31-a3f6-f79e12ebda95"/>
 <img src="https://github.com/user-attachments/assets/7247d0fe-2418-4d86-872d-f3d0ec9b0057"/>
 <img src="https://github.com/user-attachments/assets/9c3a162c-02f4-4fab-9240-15392c5433de"/>
<br/
 ><br /> Now lets test the deployment of docker images <br/>
 <img src="https://github.com/user-attachments/assets/6c9f3b19-00f0-409a-b83e-257419af1124"/>
<br/> Verify pipline and webhook connections to ensure integration <br/>
 <img src="https://github.com/user-attachments/assets/6fc9c79a-da00-4ba6-a7e0-4f22ccd59893"/>
 <br/> <br/>
 <img src=""/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/><br /> <br/>
 <br/>
<img src=""/>
<br />
<br /> <br/> 
 <br/>
 <img src=""/>
<br/>
