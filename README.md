# Colosscious: pharmquer-community
> Pharmquer Community is free version of [Colosscious Pharmquer](https://www.colosscious.com).  
<div align="center">
<img src="assets/img/colosscious-logo.svg" style="width:128px;"/>
<p style="align:center;font-size:20px" align="center">Colosscious</p>
</div> 

**Pharmquer** is a cloud BI platform for pharmaceuticals and bio industry. 
Pharmquer simplifies the process of creating dashboards with its emphasis on speed, flexibility, scalability, and high expandability. The fundamental idea behind Pharmquer involves breaking down tasks into module nodes, each containing operations related to the dataset. Notably, data fetching occurs selectively, only when necessary for generating results such as charts, downloads, or dashboards. This architecture significantly enhances speed compared to traditional Business Intelligence (BI) methods.

Tailored for enterprise applications, particularly in the fields of bio and pharma, Pharmquer prioritizes data integrity by prohibiting direct uploads of Excel or CSV files. Instead, the platform offers a Data Pipeline, enabling IT and advanced users to manage data uploading tasks.

To facilitate efficient ETL (Extract, Transform, Load) processes, **Colosscious** introduces the ETL framework **[lichens](https://github.com/thisishugow/lichens)**. This framework empowers users to swiftly construct data pipelines for tasks such as uploading, validation, and maintaining ALCOA+ standards. For a visual understanding of Pharmquer's Data Pipeline, refer to the [Youtube video](https://youtu.be/5I82Ajo9d8s?feature=shared).



## Quickstart
**Pharmquer** is packaged as a Docker image, bundling the main application along with a PostgreSQL database. We recommend deploying it on Kubernetes (K8S), AWS, GCP, or Azure for optimal performance. If you prefer on-premise deployment, ensure that Docker or Podman is properly set up beforehand.

### Download image ad load it. 
```shell
# Load image
podman load -i pharmquer-community_0.1.0-sa.tar 
```

### Start container
```shell
# Use command 
docker run -p 31234:1234 35432:5432 pharmquer-community:0.1.0-sa

# Use docker-compose.yml (See in example/docker-compose.yml))
docker-compose -f docker-compose.yml up 
```  
Notes: 
- port `:1234` is app's port. 
- port `:5432` is Postgresql's port. Exposing it is for data pipeline which is optionally.

## Deployment on Production 

For deploying in a production environment, robust database management and persistent storage are crucial. We recommend utilizing PostgreSQL on AWS RDS, Cloud SQL, or Azure. If you are operating in an on-premise environment, consider establishing a permanent volume within your Kubernetes (K8S) cluster or Docker.

### Database Management

- **Cloud Environments (AWS RDS, Cloud SQL, Azure):** Opt for PostgreSQL as your database management system on cloud platforms. Leverage services such as AWS RDS, Cloud SQL, or Azure for seamless integration and efficient management.

- **On-Premise Environment:** If deploying on-premise, PostgreSQL remains a solid choice. Ensure proper setup and maintenance for optimal performance.

### Persistent Storage

- **Cloud Environments (AWS, GCP, Azure):** Utilize the native storage solutions provided by your cloud provider. This ensures reliability and scalability for your data storage needs.

- **On-Premise Environment (Kubernetes Cluster or Docker):** In on-premise setups, create a permanent volume within your Kubernetes cluster or Docker environment. This guarantees data persistence and facilitates efficient access.

## Parameters
You can customized the setting by ENV   
- `SYS_DB_TYPE`: The type of the system database. Default value is `postgresql`.  
- `SYS_DB_HOST`: The host of the system database. Default value is `localhost`.  
- `SYS_DB_PORT`: The port number of the system database. Default value is `5432`.  
- `SYS_DB_USER`: The username for accessing the system database. Default value is `demodb01`.  
- `SYS_DB_PASSWORD`: The password for accessing the system database. Default value is `demodb01`.  
- `SYS_DB_NAME`: The name of the system database. Default value is `demodb01`.  
- `DATA_DB_TYPE`: The type of the data database. Default value is `postgresql`.  
- `DATA_DB_HOST`: The host of the data database. Default value is `localhost`.  
- `DATA_DB_PORT`: The port number of the data database. Default value is `5432`.  
- `DATA_DB_USER`: The username for accessing the data database. Default value is `demodb01`.  
- `DATA_DB_PASSWORD`: The password for accessing the data database. Default value is `demodb01`.  
- `DATA_DB_NAME`: The name of the data database. Default value is `demodb01`.  
- `DATA_DB_SCHEMA`: The schema for the data database. Default value is `pharmquer`.  


## Download

1. Docker image
   - pharmquer-community_v0.1.0-sa.tar - [download](www.colosscious.com)


## Powered By
- [FastAPI](https://fastapi.tiangolo.com/)

- [vue-element-admin](https://github.com/PanJiaChen/vue-element-admin)  

- [Antv X6](https://github.com/antvis/X6)  

- [Vue-Grid-Layout](https://jbaysolutions.github.io/vue-grid-layout/)

- [Vue-Data-Board](https://github.com/dongsuo/vue-data-board)  

- [Apache Echarts](https://echarts.apache.org/zh/index.html)
  
## Useful Links
- [Colosscious Official Website](https://www.colosscious.com)
- [Podman](https://podman.io)
- [Docker](https://www.docker.com)
- [Podman Desktop](https://podman-desktop.io)
- [Minikube](https://minikube.sigs.k8s.io)

---
<table style="text-align:left;border-collapse: collapse; background-color: transparent;">
  <tr>
    <td style="padding-right:5px;border: none;">
      <a href="https://www.colosscious.com" target="_blank">
        <img style="height:26px;" src="assets/img/colosscious-logo_mid.png" />
      </a>
    </td>
    <td style="padding-right:5px;border: none;">
      <a href="https://linkedin.com/company/colosscious" target="_blank">
        <img style="height:23px;width:84px;" src="https://content.linkedin.com/content/dam/me/business/en-us/amp/brand-site/v2/bg/LI-Logo.svg.original.svg"/>
      </a>
    </td>
    <td style="padding-right:5px;border: none;">
      <a href="https://www.youtube.com/@ColossciousCoLtd" target="_blank">
        <img style="height:20px;" src="https://www.gstatic.com/youtube/img/branding/youtubelogo/svg/youtubelogo.svg" />
      </a>
    </td>
  </tr>
</table>
