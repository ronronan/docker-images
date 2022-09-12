# Docker Images

Docker images used for Continious integration.

**Maintained by** : [Ronan M.](https://github.com/ronronan)

**Get Help** :
* [Ionic Docs](https://ionicframework.com/docs)
* [Android Docs](https://developer.android.com/guide)
* [NPM Docs](https://docs.npmjs.com/)

## Alpine SSH

**Role**: To have mini linux to use SSH client commands.

* [Link to Dockerhub](https://hub.docker.com/r/ronronan/alpine-ssh-client)
* [Link to Github](https://github.com/ronronan/docker-images)

|Tag|Alpine|OpenSSH|OpenSSL|
|--|--|--|--|
| `latest`, `3.16.2` | `3.16.2` | `9.0p1` | `1.1.1q` |
| `3.15.0` | `3.15.0` | `8.8p1` | `1.1.1l` |

## Postgresql FR

**Role**: To have database server setup with French Lang.

* [Link to Dockerhub](https://hub.docker.com/r/ronronan/postgresql-fr)
* [Link to Github](https://github.com/ronronan/docker-images)

|Tag|Postgresql|
|--|--|
| `latest`, `14.5` | `14.5` |
| `14.4` | `14.4` |
| `14.3` | `14.3` |
| `14.2` | `14.2` |
| `14.1` | `14.1` |
| `14.0` | `14.0` |
| `13.8` | `13.8` |
| `13.7` | `13.7` |
| `13.6` | `13.6` |
| `13.5` | `13.5` |

## Ionic with Android & Gradle

**Role**: To build Ionic Application for Android Devices.

* [Link to Dockerhub](https://hub.docker.com/r/ronronan/ionic-android)
* [Link to Github](https://github.com/ronronan/docker-images)

|Tag|Node|Android|Java|Gradle|Ionic|Cordova|
|--|--|--|--|--|--|--|
| `latest`, `1.0` | `14.0` | `plateform-tool 28` (Android 9/10) | `8u252` | `6.5` | CLI `6.10.0` | `9.0.0` |

## Kubectl & Helm Client

**Role**: To use easily Kubectl & helm client in CI/CD like Gitlab.

* [Link to Dockerhub](https://hub.docker.com/r/ronronan/kubectl-helm-client)
* [Link to Github](https://github.com/ronronan/docker-images)

|Tag|Kubectl|Helm|
|--|--|--|
| `latest`, `1.0.1` | `1.25.0` | `3.9.4` |
| `1.0.0` | `1.23.5` | `3.8.1` |

## Flutter android

**Role**: To build app flutter for android

* [Link to Dockerhub](https://hub.docker.com/r/ronronan/flutter-android)
* [Link to Github](https://github.com/ronronan/docker-images)

|Tag|Flutter|Gradle|Java|Debian|Android|
|--|--|--|--|--|--|
| `latest`, `1.0.0` | `2.2.3` | `7.4.2` | `11` | `11.3` | `platforms;android-33 - buildtools;33.0.0` |
