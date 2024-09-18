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
