#Base Image of Python pre-installed
FROM python-3.11

# Install additional system dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        build-essential \
        libgdal-dev \
        libgeos-dev \
        libproj-dev \
        gdal-bin \
        tini \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install JupyterLab and necessary Python packages
RUN pip install --no-cache-dir \
    pandas==2.2.2 \
    geopandas==0.14.4 \
    shapely==2.0.2 \
    fiona==1.9.5 \
    pyproj==3.6.1 \
    geetools==0.6.11 \
    earthengine-api==0.1.272
    
# Set the working directory
WORKDIR /app
