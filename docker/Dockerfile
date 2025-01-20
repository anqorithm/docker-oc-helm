FROM alpine:3.18

# Install required packages
RUN apk update && \
    apk add --no-cache \
    curl \
    tar \
    gzip \
    bash \
    openssl \
    libstdc++ \
    libc6-compat \
    gcompat

# Install OpenShift CLI (oc)
RUN curl -LO https://mirror.openshift.com/pub/openshift-v4/clients/ocp/latest/openshift-client-linux.tar.gz && \
    tar xzf openshift-client-linux.tar.gz -C /usr/local/bin && \
    rm openshift-client-linux.tar.gz && \
    chmod +x /usr/local/bin/oc && \
    ls -la /usr/local/bin/oc  # Debug: verify file exists and permissions

# Install Helm
ENV VERIFY_CHECKSUM=true
RUN curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 && \
    chmod 700 get_helm.sh && \
    ./get_helm.sh && \
    rm get_helm.sh && \
    which helm  # Debug: verify helm installation path

# Verify installations
RUN which oc && which helm && \
    oc version --client && \
    helm version --client

# Set working directory
WORKDIR /workstation

CMD ["bash"]
