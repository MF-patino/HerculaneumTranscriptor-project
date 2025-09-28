# Herculaneum Transcriptor project

Herculaneum Transcriptor is a web-based platform for the collaborative transcription of virtually unwrapped Herculaneum scrolls. This repository serves as the central hub for the entire project, containing both the frontend user interface and the backend.

## Try the deployed demo

A working demonstration of this project is available at https://mf-patino.github.io/Zographos.

**IMPORTANT**: the backend instance was deployed via a free Render account. This means that the service will be put to rest after 15 minutes of inactivity and can take up to 4 minutes to wake up once a new request is made. In order to check if the backend is currently running or not, you can visit the page https://herculaneum-transcriptor-latest.onrender.com.

## Architecture overview

This project is structured as a modern web application. Running it involves the use of following services:

*   **Frontend (`Zōgraphos`):** A responsive user interface built with **React**. It handles all user interaction, including viewing scrolls, drawing annotations, and rating transcriptions.
*   **Backend (`HerculaneumTranscriptor`):** A service built with **Java and Spring Boot**, exposing a collection of secured REST APIs. It manages user authentication, scroll and annotation data persistence, as well as image storage either via **Cloudinary** or alternatively in local storage.
*   **Database:** A **PostgreSQL** database for storing all user, scroll, and annotation metadata.
*   **Cloud image storage:** User-uploaded scroll images are securely stored and delivered via **Cloudinary**.

## Repositories

This project is organized into two main repositories, included here as Git submodules:

*   **`/Zographos`**: [Zōgraphos UI repository](https://github.com/MF-patino/Zographos)
    *   The React-based client application.
    *   Deployed via GitHub Actions to GitHub Pages.
*   **`/HerculaneumTranscriptor`**: [Herculaneum Transcriptor API repository](https://github.com/MF-patino/HerculaneumTranscriptor)
    *   The Spring Boot REST API.
    *   Containerized with Docker and deployed to a cloud service.

## Getting started for local development

To get a full local development environment running, you will need Git, Docker, Docker Compose, Java (JDK 21+), and Node.js installed.

**1. Clone the repository**

Clone this meta repository using the `--recurse-submodules` flag to automatically initialize and clone the frontend and backend repositories.

```bash
git clone --recurse-submodules https://github.com/MF-patino/HerculaneumTransciptor-project.git
cd HerculaneumTransciptor-project
```

**2. Configure & run backend environment**

The backend requires some security configuration as well as optional API keys for Cloudinary. At this moment, the needed environment variables have to be set on the `/HerculaneumTransciptor/compose-prod.yaml` file.

To run the backend environment, the following commands can be executed from the root folder of this repository.

```bash
# From the root of HerculaneumTransciptor-project
cd HerculaneumTransciptor
docker-compose -f compose-prod.yaml up --build
```

The backend API will be available on `http://localhost:8080`.

**3. Run the Frontend**

In a separate terminal, navigate to the frontend directory to start the React development server.

```bash
cd Zographos
npm install
npm start
```

The frontend application will now be running and accessible at `http://localhost:3000/Zographos`.