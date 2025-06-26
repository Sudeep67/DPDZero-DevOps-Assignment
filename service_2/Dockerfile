FROM python:3.11-slim

WORKDIR /app


# Copy project files
COPY . .

# Install Flask manually
RUN pip install flask

EXPOSE 8002

CMD ["python", "app.py"]
