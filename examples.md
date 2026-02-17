# Example YAML Files

Here are some practical examples of real-world **YAML files** we can use to revise and understand different use cases.

---

## 1. Docker Compose Example

```yaml
version: '3.8'
services:
  web:
    build: .
    ports:
      - '3000:3000'
    environment:
      - NODE_ENV=development
      - PORT=3000
  database:
    image: mongo:latest
    container_name: my-mongo
    restart: always
    ports:
      - '27017:27017'
    volumes:
      - mongo-data:/data/db

volumes:
  mongo-data:
```

This file defines a simple Node.js + MongoDB setup.

---

## 2. GitHub Actions Workflow

```yaml
name: CI Pipeline

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

This defines a CI workflow that installs dependencies and runs tests on every push or pull request.

---

## 3. Kubernetes Deployment Example

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-node-app
spec:
  replicas: 2
  selector:
    matchLabels:
      app: node-app
  template:
    metadata:
      labels:
        app: node-app
    spec:
      containers:
        - name: node-app
          image: sujal/node-app:latest
          ports:
            - containerPort: 3000
```

This defines a deployment for a Node.js application with 2 replicas.

---

## 4. YAML with Anchors and Aliases

```yaml
defaults: &defaults
  app: myapp
  region: asia
  tier: free

user1:
  <<: *defaults
  username: sujal

user2:
  <<: *defaults
  username: shalini
  tier: pro
```

Here `user1` and `user2` reuse values from `defaults` using YAML anchors and aliases.

---

## 5. Environment Configuration Example

```yaml
development:
  database_url: mongodb://localhost:27017/devdb
  debug: true

production:
  database_url: mongodb+srv://user:pass@cluster.mongodb.net/proddb
  debug: false
```

This can be used for managing environment-based configurations in any app.

---
