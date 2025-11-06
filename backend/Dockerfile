# File: backend/Dockerfile

# 1. Start from an official Python image
FROM python:3.11-slim

# 2. Set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# 3. Set the working directory inside the container
WORKDIR /app

# 4. Install all Python dependencies
# --- FIX: Path is now relative to the root context ---
COPY backend/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 5. Copy your entire backend and the *built* frontend
# --- FIX: Paths are now relative to the root context ---
COPY backend/ .
COPY frontend/dist ./frontend/dist 

# 6. Run collectstatic
# This gathers all your React static files AND your admin CSS
RUN python manage.py collectstatic --no-input