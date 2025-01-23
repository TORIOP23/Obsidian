# Overview
- - Docker uses a client-server architecture.
- The Docker client (docker) talks to the Docker daemon (dockerd)
- Docker Registry: Docker Hub is a public registry
- Docker object
    - Image - template for container
        - are composed of layers
    - Containers - a runnable instance of an image
- Docker được viết bằng **Go** & technology called namespace
![[docker.png]]
# Product
**Docker Desktop**
- Containerize your applications
- Docker Desktop bao gồm Docker daemon (dockerd), Docker client (docker), Docker Compose, Docker Content Trust, Kubernetes và Credential Helper.

**Docker Hub**
- Discover and share container images
- Docker Hub provides a variety of Docker-supported and endorsed images known as **Docker Trusted Content**
- 
**Docker Scout**
- Simplify the software supply chain

**Docker Build Cloud**
- Speed up your image builds

**Testcontainers Desktop**
- Local testing with real dependencies

**Testcontainers Cloud**
- Test without limits in the cloud

```c++
docker -v 
// list all running container 
docker ps [-a] 
docker search 
docker pull // pull image 
docker image ls == docker images 
// The docker init command will analyze your project and quickly create a Dockerfile, a compose.yaml, and a .dockerignore 
docker init 

// list image's layers 
docker imageh history imageName 
// start container 
docker run -d -p 8080:80 docker/welcome-to-docker 
// stop container 
docker stop '<the-container-id>' 

// multi continer 
docker compose up 
docker compose down 
docker container 
docker container commit // create new image layer 

docker network create name-network 
docker network ls 
docker stats // monitor
```

# Docker Image & Dockerfile
- Container images are composed of layers
### Layer
1. The first layer adds basic commands and a package manager, such as apt.
2. The second layer installs a Python runtime and pip for dependency management.
3. The third layer copies in an application’s specific requirements.txt file.
4. The fourth layer installs that application’s specific dependencies.
5. The fifth layer copies in the actual source code of the application.
- Layers let you extend images of others by reusing their base layers, allowing you to add only the data that your application needs.

### Dockerfile
- `FROM <image>` - this specifies the base image that the build will extend.
- `WORKDIR <path>` - this instruction specifies the "working directory" or the path in the image where files will be copied and commands will be executed.
- `COPY <host-path> <image-path>` - this instruction tells the builder to copy files from the host and put them into the container image.
- `RUN <command>` - this instruction tells the builder to run the specified command.
- `ENV <name> <value>` - this instruction sets an environment variable that a running container will use.
- `EXPOSE <port-number>` - this instruction sets configuration on the image that indicates a port the image would like to expose.
- `USER <user-or-uid>` - this instruction sets the default user for all subsequent instructions.
- `CMD ["<command>", "<arg1>"]` - this instruction sets the default command a container using this image will run.

### Build image
- `docker build .`

### **Tagging images**
Tagging images is the method to provide an image with a memorable name. However, there is a structure to the name of an image. A full image name has the following structure
<aside> 💡 [HOST[:PORT_NUMBER]/]PATH[:TAG]

</aside>

- HOST: The optional registry hostname where the image is located. If no host is specified, Docker's public registry at [docker.io](http://docker.io) is used by default.
- PORT_NUMBER: The registry port number if a hostname is provided
- PATH: The path of the image, consisting of slash-separated components. For Docker Hub, the format follows [NAMESPACE/]REPOSITORY, where namespace is either a user's or organization's name. If no namespace is specified, library is used, which is the namespace for Docker Official Images.
- TAG: A custom, human-readable identifier that's typically used to identify different versions or variants of an image. If no tag is specified, latest is used by default.
    - Example: `ghcr.io/dockersamples/example-voting-app-vote:pr-311`: this pulls an image from the GitHub Container Registry, the dockersamples namespace, the example-voting-app-vote image repository, and the pr-311 tag

```jsx
// tag image during build
docker build -t my-username/my-image .

// tag already build image 
docker image tag my-username/my-image another-username/another-image:v1
```

### Build Cache
- Với mỗi lệnh, Docker sẽ kiểm tra lại xem có thể sử dụng lại lệnh từ bản build trước không, nếu có sử dụng kết quả trong bộ nhớ đệm.
- 1 vài trường hợp khiến bộ đệm bị vô hiệu hoá
    - Bất kì thay đổi nào tới câu lệnh RUN
    - Bất kì sự thay đổi nào tới các file được copy hoặc ADD. Docker sẽ theo dõi thay đổi của tất cả các file kể cả thuộc tính của file như quyền sở hữu, ..
    - 1 layer bị vô hiệu hoá thì các layer tiếp theo cũng bị vô hiệu hoá
- Với các dự án node nên tải dependency trước để cache lại

### Multi-stage build
- Với các ngôn ngữ thông dịch như JS và Python, có thể build trong 1 stage and copy the production-ready files to a smaller runtime image. This optimizes your image for deployment.
- Đối với các ngôn ngữ biên dịch, như C hoặc Go hoặc Rust, các bản dựng nhiều giai đoạn cho phép bạn biên dịch trong một giai đoạn và sao chép các tệp nhị phân đã biên dịch vào một hình ảnh thời gian chạy cuối cùng. Không cần phải đóng gói toàn bộ trình biên dịch trong hình ảnh cuối cùng của bạn.

```python
# Stage 1: Build Environment
FROM builder-image AS build-stage 
# Install build tools (e.g., Maven, Gradle)
# Copy source code
# Build commands (e.g., compile, package)

# Stage 2: Runtime environment
FROM runtime-image AS final-stage  
#  Copy application artifacts from the build stage (e.g., JAR file)
COPY --from=build-stage /path/in/build/stage /path/to/place/in/final/stage
# Define runtime configuration (e.g., CMD, ENTRYPOINT) 
```

- For production use, it's highly recommended that you produce a custom JRE-like runtime using **`jlink`** (create a minimal runtime containing only the necessary Java modules for your application) [Refer to this page](https://hub.docker.com/_/eclipse-temurin?_gl=1*4n5k0x*_gcl_au*MTA0NzcxODg0NS4xNzIzOTYxMzQ0*_ga*MTY3MTg2ODU3Ni4xNzIxNzQ5Njgw*_ga_XJWPQMJYHQ*MTcyNDA0Mjk5NC4xMi4xLjE3MjQwNDMwMDIuNTIuMC4w) for more information.
- In build stage java need open jdk, in final stage java need jre
- In your multi-stage Dockerfile, the final stage (final) is the default target for building.
- This means that if you don't explicitly specify a target stage using the `--target` flag in the `docker build` command, Docker will automatically build the last stage by default.
- You could use `docker build -t spring-helloworld-builder --target builder .` to build only the builder stage with the JDK environment.
# Container
## Overriding the network ports
- Lệnh `docker run` cung cấp một cách mạnh mẽ để ghi đè các mặc định này và điều chỉnh hành vi của container theo ý thích của bạn.

### Setting environment
```python
# setting environment foo = bar 
docker run -e foo=bar postgres env

# use .env file 
docker run --env-file .env postgres env
```

### **Restricting the container to consume the resources**
- Mặc định là không bị giới hạn
This command limits container memory usage to 512 MB and defines the CPU quota of 0.5 for half a core.
```python
docker run -e POSTGRES_PASSWORD=secret --memory="512m" --cpus="0.5" postgres

docker stats # monitor
```

### Network
- Mặc định các container sẽ được kết nối với network mặc định là `bridge`
```python
docker network create mynetwork
docker network ls
docker run -d -e POSTGRES_PASSWORD=secret -p 5434:5432 --network mynetwork postgres

docker network inspect mynetwork
```

### **Override the default CMD and ENTRYPOINT in Docker Compose**
```yaml
services: 
	postgres: 
		image: postgres 
		entrypoint: ["docker-entrypoint.sh", "postgres"] 
		command: ["-h", "localhost", "-p", "5432"] 
		environment: 
			POSTGRES_PASSWORD: secret
```

## Reference
- [Resources](https://www.docker.com/resources/)
- [Manuals](https://docs.docker.com/manuals/)
