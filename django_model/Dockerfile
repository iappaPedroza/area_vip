# Dockerfile
FROM python:3.11-slim

# Define variáveis de ambiente para Python
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Define o diretório de trabalho no container
WORKDIR /app

# Instala as dependências do sistema
RUN apt-get update && apt-get install -y \
    gcc \
    sqlite3 \
    libsqlite3-dev \
    && rm -rf /var/lib/apt/lists/*

# Copia os requisitos primeiro para aproveitar o cache do Docker
COPY requirements.txt .

# Instala as dependências Python
RUN pip install --no-cache-dir -r requirements.txt

# Copia o resto do código
COPY . .

# Expõe a porta 8000
EXPOSE 8000

# Comando para executar o servidor de desenvolvimento
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]