## How to run locally

```zsh
git clone https://github.com/masumahmedeesha/docker-kubernetes-react.git
cd typing-test
npm install
npm start     # to start local server at `localhost:3000`
npm run build # to create production build run
```

## To deploy as Github page
```
- yarn add gh-pages -D
- add following code to scripts
```
        "deploy": "gh-pages -d build",
        "prepare": "husky install"
```
- yarn run deploy
- On package.json, write the correct url, like https://masumahmedeesha.github.io/monogram
- Go to Github Page (in Settings), select gh-pages as repository.
- That's all, now you've a view.
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


travis.yml

script:
  - docker run -e CI=true masumahmedeesha/docker-kubernetes-react npm run test