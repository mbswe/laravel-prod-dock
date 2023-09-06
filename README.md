
## Convert Your Entire Laravel App into a docker-image

  

***Note:** This project is currently in an **experimental** phase, driven by my desire to learn. If you choose to use it, please do so at your own risk. I welcome any recommendations or feedback you might have.*

  

***Note:** This guide assumes you have `laravel/horizon` (for scheduler/cron tasks) installed. If not, you can install it with:*

  

```bash

composer  require  laravel/horizon

```

  

### 1. Build the Image

  

-  **Prepare the Files**:

* Copy all files from the **"Image"** folder to the root of your Laravel project.

-  **Adjustments**:

* Make any necessary adjustments as per your project needs.

  

-  **Docker Build Command**:

```bash

docker build --file Dockerfile -t mbswe/laravel .

```

*Note: Replace `mbswe/laravel` with your desired image name.*

-  **Update the Image**:

* Whenever you make changes to the code, repeat the build process.

  

### 2. Deploy Using the Image

  

-  **Set Up Files for Container**:

* Place the contents of the **"App"** folder in your desired location where you intend to start your container.

  

-  **MySQL Requirement**:

* Ensure you have a MySQL server running. *(The reason it's not included in the image is beyond this scope.)*

  

-  **Adjustments**:

* Make necessary modifications to relevant files.

* The `.env.production` file holds details like connection parameters.

  

-  **Start the Container**:

```bash

docker-compose up -d

```