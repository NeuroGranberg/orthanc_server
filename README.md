Check [here]()

**Project Overview**

This project sets up a self-contained environment for medical image management using the Orthanc DICOM server and related components. Here's what the included files do:

* **docker-compose.yml:**  Defines containerized services for smooth deployment:
    * **orthanc_postgres:** A PostgreSQL database for storing Orthanc's index of medical images.
    * **orthanc_server:** The core Orthanc DICOM server, responsible for receiving, storing, and querying medical images.
    * **orthanc_client:**  A separate Orthanc instance configured primarily to send images to the main Orthanc server.
    * **adminer:** Provides a web interface for easy PostgreSQL database management.

* **orthanc_client_config.json:** Configuration for the Orthanc client, specifying how to connect to the main Orthanc server.

* **orthanc_server_config.json:**  Configuration for the main Orthanc server, outlining its settings and the connection to the PostgreSQL database.

**Key Components**

* **Orthanc:** A lightweight, open-source DICOM server designed for ease of use and rapid deployment.
* **PostgreSQL:** A robust database system powering the storage and indexing of image metadata within Orthanc.
* **Adminer:** A web-based database management tool.
* **Docker Compose:** Orchestrates the deployment and relationships between all services.

**How to Use**

1. **Prerequisites:**
   * Docker engine installed ([https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/))
   * Docker Compose installed ([https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/))

2. **Environment Variables:**
   * Create a `.env` file in the project directory. 
   * Define the required environment variables (example provided below).

3. **Run:**
   * From the project directory, execute: `docker-compose up -d`

**Environment Variables (.env)**

```
POSTGRES_DB=orthanc
POSTGRES_USER=orthancuser
POSTGRES_PASSWORD=yoursecurepassword
DICOM_HOST_CLIENT=client
DICOM_HOST_SERVER=server
DICOM_AET_CLIENT=ORTHANC_CLIENT
DICOM_AET_SERVER=ORTHANC_SERVER
DICOM_PORT=4242
```

**Accessing the System**

* **Orthanc Server:** http://localhost:8042
* **Orthanc Client:** http://localhost:8043
* **Adminer (Database Management):** http://localhost:8080

**Additional Notes**

* Persisting image data is achieved through the volumes specified in `docker-compose.yml`. Modify accordingly for your storage needs. 
* You can send DICOM images to the Orthanc client, which will automatically forward them to the primary Orthanc server.
* For production use, ensure robust security measures for image data and network access.

