# Use pre-built base image with all dependencies already installed.
# No network access needed during Coolify builds.
FROM ghcr.io/guiiicd/supoclip/backend-base:latest AS base

# Set working directory
WORKDIR /app

# yt-dlp and its PO-token plugin are installed from uv.lock in the base image.

# Copy source code
COPY src/ ./src/

# Copy fonts and transitions directories
COPY fonts/ ./fonts/
COPY transitions/ ./transitions/

# Create necessary directories for video processing
RUN mkdir -p /app/uploads /app/clips /app/logs /tmp

# Expose the port FastAPI will run on
EXPOSE 8000

# Activate virtual environment and start the application
CMD [".venv/bin/uvicorn", "src.main:app", "--host", "0.0.0.0", "--port", "8000"]
