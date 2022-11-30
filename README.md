## How to run locally

```zsh
git clone https://github.com/masumahmedeesha/docker-kubernetes-react.git
cd typing-test
npm install
npm start     # to start local server at `localhost:3000`
npm run build # to create production build run
```

version: '3'
services:
  web:
    stdin_open: true
    environment:
      - CHOKIDAR_USEPOLLING=true
    build:
      context: .
      dockerfile: Dockerfile.dev
    ports:
      - '80:3000'
    volumes:
      - /app/node_modules
      - .:/app
  # tests:
  #   stdin_open: true
  #   build:
  #     context: .
  #     dockerfile: Dockerfile.dev
  #   volumes:
  #     - /app/node_modules
  #     - .:/app
  #   command: [ 'npm', 'run', 'test' ]
