---
layout: post
title:  "Deploying a Dockerized FastAPI to Cloud Run: My Wild Adventure"
date:   2026-01-14 12:00:00 -0700
categories: [GCP, FastAPI, DevOps]
---

When I first set out to deploy my FastAPI application to Google Cloud Run, I thought it would be straightforward. Little did I know I was about to embark on a wild adventure full of permission errors, API roadblocks, and container quirks. Here's the full story of what happened, and how I finally got everything working.

## Starting with FastAPI

My journey began by building a simple FastAPI application. I made sure to include a health check endpoint and a `smokeTest` router for testing.

```python
@app.get("/")
def health():
    return {"message": "OK 🚀"}
````

Everything ran perfectly locally, but I knew the real test would come when I tried to containerize it and push it to Google Cloud.

### Dockerizing the Application

I created separate Dockerfiles for production and development. Initially, the production Dockerfile exposed the wrong port, which caused Cloud Run to fail health checks. After some trial and error, I corrected it to listen on the `$PORT` environment variable, which Cloud Run requires.

```dockerfile
EXPOSE 8080
CMD ["python", "-m", "src.main"]
```

I also updated the development Dockerfile to include Google Cloud SDK and hot reload capabilities with `uvicorn`.

### The GCP Maze

Once the Docker containers were ready, I faced a barrage of permission errors when trying to push to Artifact Registry and deploy to Cloud Run. I realized I needed a dedicated **service account** with the right roles:

* Artifact Registry Writer
* Cloud Run Admin
* Storage Admin
* Cloud Build Editor

Creating the service account and adding all the IAM roles was tricky, but eventually I scripted everything so it could be replicated.

```bash
gcloud iam service-accounts create fastapi-deploy-sa \
  --display-name "FastAPI CI/CD Service Account"
```

### CI/CD with GitHub Actions

After securing the GCP permissions, I configured a GitHub Actions workflow to automate the build and deployment process. Initially, I struggled with secrets, fork issues, and authentication problems. Once I simplified the workflow to use a service account JSON key, things finally started to work.

```yaml
- name: Authenticate to GCP
  uses: google-github-actions/auth@v2
  with:
    credentials_json: ${{ secrets.GCP_SA_KEY }}
```

### Troubleshooting Containers

Even after everything was set up, my first deployment failed because the container didn't start on the correct port. After adjusting the FastAPI entry point and ensuring the container listens on `$PORT`, Cloud Run accepted it. I also learned that the health endpoint must respond quickly to pass Cloud Run's checks.

### Lessons Learned

* Cloud Run requires containers to listen on `$PORT`.
* Service accounts must have all required roles **before** deploying.
* Enabling APIs like Cloud Run, Artifact Registry, and Cloud Build can require Owner permissions.
* GitHub Actions secrets are tricky when working with forks—be mindful of how they’re passed.
* Dockerfile configuration matters; tiny mistakes can break deployments in subtle ways.

## Conclusion

This deployment adventure was a rollercoaster, full of permission errors, misconfigured Dockerfiles, and API challenges. But by carefully addressing each obstacle—fixing ports, updating IAM roles, and scripting CI/CD—I finally got my FastAPI application running smoothly on Cloud Run.

If you're about to tackle a similar deployment, remember: **patience and step-by-step verification are your best friends.** And always test your container locally before sending it into the cloud.

