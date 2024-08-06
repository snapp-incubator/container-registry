This repository centralizes all Docker images in one place, simplifying the process of building and pushing Docker images. 

## Purpose

The primary goal of this repository is to streamline Docker image management by:

- **Gathering all Docker images**: Consolidates Dockerfiles into a single repository.
- **Automating the build and push process**: Uses GitHub Actions to build and push Docker images based on commit messages.

## Folder Structure

Organize your repository as follows to ensure compatibility with the workflow:

```
/
  app1/
    Dockerfile
  app2/
    Dockerfile
```

- Each directory (`app1`, `app2`, etc.) should contain a `Dockerfile`.
- The name of each directory corresponds to the Docker image name.

## Commit Message Format

To trigger the Docker build and push process, format your commit messages as follows:

```
build/<image_name>:<version>
```

- `<image_name>`: The directory name containing the `Dockerfile`.
- `<version>`: The version tag for the Docker image.

### Examples

1. **Commit Message for `app1` Docker Image with Version 1.0.0**:
   ```
   build/app1:1.0.0
   ```

2. **Commit Message for `app2` Docker Image with Version 2.1.0**:

   ```
   build/app2:2.1.0
   ```

## Workflow Behavior

- **Valid Commits**: Commits with messages that match the `build/<image_name>:<version>` format will trigger the Docker image build and push process.
- **Invalid Commits**: Commits not following the specified format will be skipped. The CI process will not build or push Docker images for these commits, ensuring that only relevant updates are processed.
- 
## Summary

By following these conventions, you ensure that Docker images are built and pushed automatically whenever a commit with the correct format is made. This approach helps maintain a well-organized repository and simplifies Docker image management.

For more information on GitHub Actions and Docker, check out the [GitHub Actions documentation](https://docs.github.com/en/actions) and [Docker documentation](https://docs.docker.com/).