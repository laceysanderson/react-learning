# React Learning

A repo containing various react apps I created while learning and the docker environment I use to learn.

## Learning Environment

**NOTE: You do not need NodeJS installed on your computer. All that's needed is Docker (or Docker Desktop) and your favourite editor.**

First build the image and start a container.

```
docker build ./ --tag=react
```

The run command maps your current directory into the container so you can edit it locally. The current directory should be this repository.

```
docker run -dit --publish=80:80  --volume=`pwd`:/app --name=react react:latest
```

To start a new React App in the `example/` directory, run the following command:

```
docker exec -it react npx create-react-app example
```

This creates the files both locally and in the docker thanks to the `--volume` command above.

## Tutorials Used

- [ReactJs.org Intro to React](https://reactjs.org/tutorial/tutorial.html) (2022Jun11) creates a simple tic tac toe game in `tic-tac-toe/`
