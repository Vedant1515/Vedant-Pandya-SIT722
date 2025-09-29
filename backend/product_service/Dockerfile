# Base image
FROM python:3.11-slim-bookworm

# --- Runtime env (no .pyc, unbuffered logs) ---
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# --- Workdir ---
WORKDIR /app

# --- OS build deps ---
RUN apt-get update \
 && apt-get install -y --no-install-recommends build-essential \
 && rm -rf /var/lib/apt/lists/*

# --- Install Python deps ---
# (copy requirements first to leverage Docker layer caching)
COPY backend/product_service/requirements.txt /tmp/requirements.txt
RUN pip install --no-cache-dir -r /tmp/requirements.txt

# --- Copy application code ---
COPY backend/product_service/ /app

# --- Networking & startup ---
EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
