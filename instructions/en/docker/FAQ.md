<h1>FAQ</h1>

<h2>Table of contents</h2>

- [Errors](#errors)
  - [Docker Rancher - Permission Denied when using docker from WSL](#docker-rancher---permission-denied-when-using-docker-from-wsl)

## Errors


###  Docker Rancher - Permission Denied when using docker from WSL

| Relate issue |
|---|
| stackoverflow issue: https://stackoverflow.com/q/72528606/22440363</p><p>github issue: https://github.com/rancher-sandbox/rancher-desktop/issues/1156#issuecomment-1017042882O</p><p> |

```diff
    $ docker ps
    Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json": dial unix /var/run/docker.sock: connect: permission denied
```

<h3>Solution</h3>


```shell
sudo addgroup --system docker
sudo adduser $USER docker
newgrp docker
# And something needs to be done so $USER always runs in group `docker` on the `Ubuntu` WSL
sudo chown root:docker /var/run/docker.sock
sudo chmod g+w /var/run/docker.sock
```

---

Need assistance? Check out my [discussion board](https://github.com/AppleBoiy/cs-wiki101/discussions) or review the [GitHub status page](https://www.githubstatus.com).

&copy; 2023 AppleBoiy &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](LICENSE)

<p align="right"><a href="#top" style=" bottom: 20px; right: 20px;">Back to Top</a></p>
