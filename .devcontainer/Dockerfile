# Use minimal Debian base image
FROM debian:bookworm-slim

# Install essential dependencies
RUN apt-get update && apt-get install -y \
    wget \
    tar \
    xz-utils \
    ca-certificates \
    git \
    python3 \
    libgomp1 \
    && rm -rf /var/lib/apt/lists/*

# Set up working directory
WORKDIR /workspace

# Download and install OSS CAD Suite from GitHub releases
# Using the latest release for linux-x64
RUN ARCH="linux-x64" && \
    wget -q https://github.com/YosysHQ/oss-cad-suite-build/releases/latest/download/oss-cad-suite-${ARCH}.tgz && \
    mkdir -p /opt/oss-cad-suite && \
    tar -xzf oss-cad-suite-${ARCH}.tgz -C /opt && \
    rm oss-cad-suite-${ARCH}.tgz

# Set up environment variables to source OSS CAD Suite by default
ENV PATH="/opt/oss-cad-suite/bin:${PATH}"
ENV LD_LIBRARY_PATH="/opt/oss-cad-suite/lib:${LD_LIBRARY_PATH}"

# Add the environment setup to bashrc so it's sourced by default
RUN echo 'export PATH="/opt/oss-cad-suite/bin:${PATH}"' >> /etc/bash.bashrc && \
    echo 'export LD_LIBRARY_PATH="/opt/oss-cad-suite/lib:${LD_LIBRARY_PATH}"' >> /etc/bash.bashrc

# Set the default shell to bash
ENV SHELL=/bin/bash

# Default command
CMD ["/bin/bash"]
