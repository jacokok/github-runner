# Github Runner

This will run my arm64 runners and group them together

## Environment

- RUNNER_NAME
- RUNNER_LABELS
- RUNNER_REPOSITORY_URL
- GITHUB_ACCESS_TOKEN
- RUNNER_TOKEN

## Example Compose

```yaml
version: "3"
services:
    runner1:
      image: doink/github-runner:latest
      environment:
        RUNNER_NAME: "test"
        RUNNER_LABELS: "internal"
        RUNNER_REPOSITORY_URL: ${RUNNER_REPOSITORY_URL}
        GITHUB_ACCESS_TOKEN: ${GITHUB_ACCESS_TOKEN}
      volumes:
        - /var/run/docker.sock:/var/run/docker.sock
```

## Docker Build

```bash
docker build -t github-runner .

docker run -d \
    -e GITHUB_ACCESS_TOKEN=${GITHUB_ACCESS_TOKEN} \
    -e RUNNER_NAME=test \
    -e RUNNER_REPOSITORY_URL=${RUNNER_REPOSITORY_URL} \
    -v /var/run/docker.sock:/var/run/docker.sock \
    github-runner
```

## Test

```bash
docker run --rm -it alpine sh
```
