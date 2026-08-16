# Install python into image
FROM python:3.13.11-slim

# Install uv from ghcr.io/astral-sh/uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /bin/

# Change working directory to /app 
WORKDIR /app

# Create a virtual environment and add it to the PATH
ENV PATH="/app/.venv/bin:$PATH"

# Move the lockfile, pyproject.toml, .python-version, and README.md to the working directory
COPY uv.lock pyproject.toml .python-version README.md ./
COPY src ./src

# Install dependencies from the lockfile
RUN uv sync --locked

# Copy the pipeline.py file to the working directory
COPY pipeline.py ./

# Set the entrypoint to run the pipeline.py script using Python
ENTRYPOINT ["python", "pipeline.py"]