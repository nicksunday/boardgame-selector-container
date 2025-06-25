# 🎲 Board Game Selector

**Board Game Selector** is a lightweight, containerized web app that helps you pick the perfect board game from your library based on player count and play time. Built with Python and Flask, it fetches real-time game data from the [BoardGameGeek API](https://boardgamegeek.com/) and runs seamlessly on **Google Cloud Run**.

🌐 Live version: [https://suggest.games](https://suggest.games)

---

## 🧩 Features

- 🔍 Filter games by number of players and maximum play time
- 🎲 Get a random recommendation each time
- 🔗 Pulls data directly from BoardGameGeek's XML API
- 🚀 Deployed to GCP using Cloud Run with a containerized backend

---

## 🛠 Tech Stack

- **Backend:** Python 3, Flask
- **Frontend:** HTML templates (Jinja2)
- **Deployment:** Docker, Google Cloud Run
- **Data Source:** BoardGameGeek XML API

---

## 🐳 Containerized Deployment (Cloud Run or Docker)

### Build the container
```bash
docker build -t boardgame-selector .
```

### Run locally
```bash
docker run -p 80:80 boardgame-selector
```

Then visit [http://localhost](http://localhost)

> To deploy to Google Cloud Run, push the container to Artifact Registry or Docker Hub and follow the Cloud Run setup instructions.

---

## 📜 License

This project is open-source under the [MIT License](LICENSE).

---

## ✨ Future Ideas

- Game complexity filter (e.g., "family", "strategy")
- Visual improvements and mobile responsiveness
- Game cover images and links to BGG pages

---

## ☁️ Continuous Deployment with Google Cloud Build

This project uses **Google Cloud Build** for automated container build and deployment to **Cloud Run**.

A minimal `cloudbuild.yaml` is included in the repo. It performs the following steps:

1. **Build** the Docker image from the repository
2. **Push** the image to Google Container Registry (`us.gcr.io`)
3. **Deploy** the image to **Cloud Run (fully managed)** in `us-central1`

To trigger a build manually:
```bash
gcloud builds submit --config=cloudbuild.yaml .
```

Or set up a **Cloud Build trigger** linked to your repository to deploy on each commit.
