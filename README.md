# llama.cpp-hosted

This is a personal project for running llama.cpp server on different GPU architectures. It provides Docker images and configurations for CUDA (NVIDIA), ROCm (AMD), and Vulkan (for unsupported cards, including older AMD cards).

## Supported GPU Architectures

- CUDA (NVIDIA GPUs)
- ROCm (AMD GPUs)
- Vulkan (Unsupported cards, including older AMD GPUs)

## Docker Images

These are the pre-built Docker images for each supported GPU architecture:

- CUDA: `ghcr.io/ggerganov/llama.cpp:server-cuda` 
- ROCm: `gjuoun/llama.cpp-hosted:rocm` (maintained by me)
- Vulkan: `ghcr.io/gjuoun/llama.cpp-hosted/vulkan:latest` (maintained by me)

## Usage

### Using Docker Compose

1. Choose the appropriate `docker-compose.yml` file based on your GPU architecture.
2. Run the following command in the same directory as the `docker-compose.yml` file:

```bash
docker-compose up -d
```

This will start the llama.cpp server on port 8080.

### Using Dockerfile
If you want to build the Docker image yourself:

1. Clone this repository.
2. Navigate to the directory containing the Dockerfile for your GPU architecture.
3. Build the Docker image:
  ```bash
  docker build -t llama-cpp-server .
  ```
4. Run the container:
  ```bash
  docker run -p 8080:8080 llama-cpp-server
  ```

## Configuration
You can customize the server behavior by modifying the environment variables in the docker-compose.yml file or by passing them when running the Docker container. Some important variables include:

- `LLAMA_ARG_HOST`: The host to bind the server to (default: 0.0.0.0)
- `LLAMA_ARG_PORT`: The port to run the server on (default: 8080)
- `LLAMA_ARG_N_GPU_LAYERS`: Number of GPU layers to use (default: 99)
- `LLAMA_ARG_CTX_SIZE`: Context size (default: 4096)
- `LLAMA_ARG_MODEL_URL`: URL to download the model from

## Contributing
This is a personal project, but contributions and suggestions are welcome. Please open an issue or submit a pull request if you have any improvements or ideas.

License
This project is open-source and available under the MIT License.

