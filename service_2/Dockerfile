FROM python:3.11-slim

WORKDIR /app

# Install uv (fast Python package manager)
RUN pip install --no-cache-dir uv

# Copy project files
COPY . .

# Install dependencies from pyproject.toml using uv
RUN uv pip install -r uv.lock --requires-python "$(uv pip index versions pip | head -n 1 | awk '{print $2}')"

EXPOSE 8002

CMD ["python", "app.py"]
