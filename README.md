# Docker Images

Docker images used for Continuous integration.

**Maintained by** : [Ronan M.](https://github.com/ronronan)

**Get Help** :

- [Ionic Docs](https://ionicframework.com/docs)
- [Android Docs](https://developer.android.com/guide)
- [NPM Docs](https://docs.npmjs.com/)

## Alpine SSH

**Role**: To have mini Linux to use SSH client commands.

- [Link to Dockerhub](https://hub.docker.com/r/ronronan/alpine-ssh-client)
- [Link to Github](https://github.com/ronronan/docker-images)

| Tag                | Alpine   | OpenSSH | OpenSSL  |
| ------------------ | -------- | ------- | -------- |
| `latest`, `3.21.3` | `3.21.3` | `9.9p2` | `3.3.3`  |
| `3.21.2`           | `3.21.2` | `9.9p1` | `3.3.2`  |
| `3.19.1`           | `3.19.1` | `9.6p1` | `3.1.5`  |
| `3.18.2`           | `3.18.2` | `9.3p2` | `3.1.1`  |
| `3.15.0`           | `3.15.0` | `8.8p1` | `1.1.1l` |

### Commands

- Test

```bash
docker run --rm -it ronronan/alpine-ssh-client:latest sh
```

- Build

```bash
docker build -t ronronan/alpine-ssh-client:latest -f ./alpine-ssh-client/Dockerfile .
```

- Tag

```bash
docker tag ronronan/alpine-ssh-client:latest ronronan/alpine-ssh-client:3.21.3
```

- Push

```bash
docker push ronronan/alpine-ssh-client:latest
```

## Kubectl & Helm Client

**Role**: To use easily Kubectl & helm client in CI/CD like Gitlab.

- [Link to Dockerhub](https://hub.docker.com/r/ronronan/kubectl-helm-client)
- [Link to Github](https://github.com/ronronan/docker-images)

| Tag               | Kubectl  | Helm          |
| ----------------- | -------- | ------------- |
| `latest`, `1.0.6` | `1.31.0` | `3.17.3`      |
| `1.0.5`           | `1.31.0` | `3.16.4`      |
| `1.0.4`           | `1.30.1` | `3.15.0-rc.2` |
| `1.0.3`           | `1.29.3` | `3.14.4`      |
| `1.0.2`           | `1.27.4` | `3.12.2`      |
| `1.0.1`           | `1.25.0` | `3.9.4`       |
| `1.0.0`           | `1.23.5` | `3.8.1`       |

### Commands

- Test

```bash
docker run --rm -it ronronan/kubectl-helm-client:latest sh
```

- Build

```bash
docker build -t ronronan/kubectl-helm-client:latest -f ./kubectl-helm-client/Dockerfile .
```

- Tag

```bash
docker tag ronronan/kubectl-helm-client:latest ronronan/kubectl-helm-client:1.0.6
```

- Push

```bash
docker push ronronan/kubectl-helm-client:latest
```

## Flutter android

**Role**: To build app flutter for android

- [Link to Dockerhub](https://hub.docker.com/r/ronronan/flutter-android)
- [Link to Github](https://github.com/ronronan/docker-images)

| Tag               | Flutter  | Gradle   | Java | Android                                    |
| ----------------- | -------- | -------- | ---- | ------------------------------------------ |
| `latest`, `1.3.1` | `3.32.1` | `8.14.1` | `21` | `platforms;android-35 - buildtools;34.0.0` |
| `1.3.0`           | `3.29.2` | `8.14`   | `21` | `platforms;android-35 - buildtools;34.0.0` |
| `1.2.0`           | `3.27.2` | `8.12`   | `21` | `platforms;android-35 - buildtools;34.0.0` |
| `1.1.4`           | `3.24.3` | `7.6.4`  | `17` | `platforms;android-34 - buildtools;34.0.0` |
| `1.1.3`           | `3.22.0` | `7.6.4`  | `17` | `platforms;android-34 - buildtools;34.0.0` |
| `1.1.2`           | `3.19.5` | `7.6.4`  | `17` | `platforms;android-34 - buildtools;34.0.0` |
| `1.1.1`           | `3.10.6` | `7.6.2`  | `17` | `platforms;android-34 - buildtools;34.0.0` |
| `1.1.0`           | `3.7.12` | `7.6.2`  | `17` | `platforms;android-34 - buildtools;34.0.0` |
| `1.0.2`           | `3.7.7`  | `7.6.1`  | `17` | `platforms;android-33 - buildtools;33.0.2` |

### Commands

- Test

```bash
docker run --rm -it ronronan/flutter-android:latest bash
```

- Build

```bash
docker build -t ronronan/flutter-android:latest -f ./flutter-android/Dockerfile .
```

- Tag

```bash
docker tag ronronan/flutter-android:latest ronronan/flutter-android:1.3.1
```

- Push

```bash
docker push ronronan/flutter-android:latest
```
