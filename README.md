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
docker run -dit --publish=80:80 --publish=3000:3000 --volume=`pwd`:/app --name=react react:latest
```

### Creating a new React App

To start a new React App in the `example/` directory, run the following command:

```
docker exec -it react npx create-react-app example
```

This creates the files both locally and in the docker thanks to the `--volume` command above.

### Test using npm start

The following command lets you start a quick development build/server that you can view on http://localhost:3000.

```
docker exec -it --workdir="/app/example" react npm start
```

After you make changes, just refresh the page to see them!

NOTE: You will only see your app as long as the command is running. I recommend running this command in a separate terminal window and just leaving it to run while you learn :-)

### Test production build

To test building with apache deployment, you will want to run the build command and then symbolically link the built code to the apache directory: `/usr/local/apache2/htdocs`. Here are the commands for an app following the pattern initiated by create-react-app.

```
docker exec -it --workdir="/app/example" react npm run build
```

Note: The first time you do this for a given app, you will want to run the following:

```
docker exec -it --workdir="/usr/local/apache2" react rm -r htdocs
docker exec -it --workdir="/usr/local/apache2" react ln -s /app/example/build htdocs
```

Then you can look at http://localhost in your browser!

## Tutorials Used

*Format is as follows: Tutorial URL (date accessed; commit code) short description including the `directory/the/code/is/stored/in/this/repo`*

- [ReactJs.org Intro to React](https://reactjs.org/tutorial/tutorial.html) (2022Jun11; ip3zQ8) creates a simple tic tac toe game in `tic-tac-toe/`
