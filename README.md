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

### Download image and load it. 
```shell
# pull from docker.io
podman pull thisisyuwang/pharmquer-community:latest
## by Docker
docker pull thisisyuwang/pharmquer-community:latest

# or import from on-premise
podman load -i pharmquer-community:0.1.1-sa
## by Docker
docker load -i pharmquer-community:0.1.1-sa
```

### Start container
```shell
# Use command 
podman run -p 31234:1234 35432:5432 pharmquer-community
## by Docker
docker run -p 31234:1234 35432:5432 pharmquer-community

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
  
## Mounting Volume for Data Pipeline
When using Pharmquer, documents uploaded by default are preserved within the container. To facilitate access to the document lake by ETL containers, it is essential to establish a persistent and shareable volume. Given that both **lichens** and **Pharmquer** operate on files using the same path set in the system table, it is imperative to mount the persistent volume to a fixed path in each container.  
### Example 
```shell 
# Create a volume
podman volume create mydatalake;

# Mount the volume to containers
ETL_FILE_PATH=/etl/data
podman run -p 31234:1234 35432:5432 -v mydatalake:$ETL_FILE_PATH -v mypostgrespv:/var/lib/postgresql/data pharmquer-community;  
podman run -v mydatalake:$ETL_FILE_PATH my-lichens-app;  
```
In the example above, a volume named `mydatalake` is created. This volume is then mounted to the Pharmquer container using the specified ETL file path. Adjustments can be made to suit your specific configuration and requirements.

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
   - pharmquer-community_v0.1.0-sa.tar - [download](https://drive.google.com/file/d/1xQYaEt1lA1TcxuIDMq3hWMyvXMHLaXs4/view?usp=sharing)


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
**More Info**
<table style="text-align:left;border-collapse: collapse; background-color: transparent;font-size:12px;">
<tr>
    <th style="padding-right:5px; border: none;">Official Web</th>
    <th style="padding-right:5px; padding-top:8px; border: none;">LinkedIn</th>
    <th style="padding-right:5px; border: none;">Youtube</th>
  </tr>
  <tr>
    <td style="padding-right:5px;border: none;">
      <a href="https://www.colosscious.com" target="_blank">
        <img style="height:27px;" src="assets/img/colosscious-logo_mid.png" />
      </a>
    </td>
    <td style="padding-right:5px;padding-top:8px;border: none;">
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

**Practice Contact**  
bd.info@colosscious.com 

<u>Copyright Ⓒ 2023 Colosscious Co., Ltd. All Rights Reserved.</u>