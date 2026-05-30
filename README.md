This repository centralizes all Docker images in one place, simplifying the process of building and pushing Docker images.

## Purpose

The primary goal of this repository is to streamline Docker image management by:

- **Gathering all Docker images**: Consolidates Dockerfiles into a single repository.
- **Automating the build and push process**: Uses GitHub Actions to build and push Docker images based on code changes and versions stored in the repo.

## Folder Structure

Organize your repository as follows to ensure compatibility with the workflow:

```
/
  app1/
    Dockerfile
    VERSION
  app2/
    Dockerfile
    VERSION
```

- Each directory (`app1`, `app2`, etc.) should contain a `Dockerfile`.
- Each directory must also contain a `VERSION` file holding the tag you want pushed for that image.
- The name of each directory corresponds to the Docker image name.

## Image Versioning

- The content of the `VERSION` file is used as the tag for `ghcr.io/<owner>/<image>:<version>`.
- Update `VERSION` whenever you want to publish a new tag for that image; commit the change alongside any Dockerfile or asset updates.
- The workflow always publishes a `:latest` tag in addition to the version from the file.

## Workflow Behavior

- On pushes to `main`, the workflow compares the previous and current commits and looks for changed top-level folders that contain a `Dockerfile` (including changes to their `VERSION` files).
- Only those folders are built and pushed. If nothing relevant changed, the build job is skipped.
- Image metadata is read from the repository itself; commit messages no longer control which images or versions are built.

## Summary

By following these conventions, Docker images are built and pushed automatically whenever code (or the `VERSION` file) in an image folder changes. This approach keeps image versions in the codebase and simplifies Docker image management.

For more information on GitHub Actions and Docker, check out the [GitHub Actions documentation](https://docs.github.com/en/actions) and [Docker documentation](https://docs.docker.com/).
