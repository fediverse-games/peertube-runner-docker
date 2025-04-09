# peertube-runner

This docker image provides a simple, easy and declarative way to create simple, stateless peertube-runner instances.

I couldn't quite find an image that did *exactly* what I wanted so I decided to create my own.

## Usage

At a minimum, the image requires a `PEERTUBE_URL` and `PEERTUBE_RUNNER_TOKEN` to successfully execute. All other environment variables have default values to fall back on.

### Docker

```
docker run ghcr.io/fediverse-games/peertube-runner:latest -e PEERTUBE_URL=https://your-peertube-url.example/ -e PEERTUBE_RUNNER_TOKEN=prrt-yourtoken
```

### Docker Compose

Example docker compose to come.

### Kubernetes

Example kubernetes manifest to come.

## Configuration

| Variable                     | Function                                                  | Default |
| -------------                |--------------                                             | - |
| `PEERTUBE_URL`               | **REQUIRED**: The peertube URL the runner will connect to | N/A |
| `PEERTUBE_RUNNER_TOKEN`      | **REQUIRED**: The peertube runner registration token generated in peertube | N/A |
| `FFMPEG_THREADS`             | The number of threads FFMPEG should use for each job. 0 is auto | 0 |
| `FFMPEG_NICE`                | The FFMPEG niceness value                                  | 0 |
| `PEERTUBE_RUNNER_NAME`       | THe name/id to assign to the runner.                      | The `HOSTNAME` value |
| `PEERTUBE_RUNNER_DESCRIPTION`| The description to assign to the runner.                  | Peertube Runner |
| `PEERTUBE_TRANSCRIPTION_ENGINE`| The transcription engine to use. **Changing this value is untested and not supported at this time** | whisper-ctranslate2 |
| `PEERTUBE_TRANSCRIPTION_MODEL`| The model size for the transcription engine **Changing this value is untested and not supported at this time** | small |
| `PEERTUBE_TRANSCRIPTION_ENGINEPATH` | The path in the container the transcription engine is installed in **Changing this value is untested and not supported at this time** | /home/peertube/.local/pipx/venvs/whisper-ctranslate2/bin/whisper-ctranslate2 |

## TO DO:

- Proper documentation.
- Better github build process.
- Publish to dockerhub?
- Try and get hardware acceleration working (may require changes to the peertube-runner package itself).
