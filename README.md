# Installing CVAT on Windows: A Comprehensive Guide
CVAT (Computer Vision Annotation Tool) is a powerful open-source tool for image and video annotation, widely used in computer vision projects. This step-by-step guide provides detailed instructions on how to install CVAT on a Windows environment. By following these instructions, you'll set up the necessary dependencies, including Git, Docker, and Google Chrome, and then clone the CVAT source code from its GitHub repository. The guide takes you through the process of running Docker containers, creating a superuser account, and accessing CVAT through Google Chrome. Whether you're a developer, data scientist, or enthusiast in the field of computer vision, this guide equips you with the tools to seamlessly integrate CVAT into your Windows environment for efficient annotation tasks.

## Step 1: Install Git for Windows

1. Download Git for Windows from [https://gitforwindows.org/](https://gitforwindows.org/).
2. Install Git, keeping all options as default.
3. Open the command prompt (`cmd`) and type the following command to check the Git version:
    ```bash
    git --version
    ```

## Step 2: Install Docker Desktop for Windows

1. Download [Docker Desktop for Windows](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe).
2. Double-click the Docker for Windows Installer to run the installer.
3. Follow the instructions for installation, and reboot the system after installation is complete.
4. Open the command prompt and check the Docker version:
    ```bash
    docker --version
    ```
5. Check the Docker Compose version:
    ```bash
    docker compose version
    ```

## Step 3: Install Google Chrome

1. Download and install [Google Chrome](https://www.google.com/chrome/), as it is the only browser supported by CVAT.

## Step 4: Clone CVAT Source Code

1. Clone CVAT source code from the [GitHub repository](https://github.com/opencv/cvat):
    ```bash
    git clone https://github.com/opencv/cvat
    cd cvat
    ```
2. Alternatively, check [alternatives](https://opencv.github.io/cvat/docs/administration/basics/installation/#how-to-get-cvat-source-code) for downloading specific release versions.

## Step 5: Run Docker Containers for CVAT

1. Run the following command to start Docker containers. This will download the latest CVAT release and other required images:
    ```bash
    docker compose up -d
    ```
2. Optionally, specify the CVAT version using the CVAT_VERSION environment variable:
    ```bash
    CVAT_VERSION=dev docker compose up -d
    ```
3. Check the status of the containers:
    ```bash
    docker ps
    ```
4. Wait until the CVAT server is up and running:
    ```bash
    docker logs cvat_server -f
    ```
5. Run the CVAT server:
    ```bash
    docker exec -it cvat_server bash
    ```
6. For the first-time setup, create a superuser account:
    ```bash
    python3 manage.py createsuperuser
    ```
    Choose a username and password for the admin account.

## Step 6: Access CVAT in Google Chrome

1. Open Google Chrome and go to `localhost:8080`.
2. Log in with the superuser credentials created earlier.
3. You should now be able to create a new annotation task.
4. For more details, refer to the [CVAT manual](https://opencv.github.io/cvat/docs/manual/).
