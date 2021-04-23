# codesanook-ef-note

## How to run the project locally
- Fork this project
- Clone the project to your computer.
```sh
git clone git@github.com:{your-github-username}/codesanook-ef-note.git
```
!!! Change **{your-github-username}** to your GitHub username

- CD to to the root folder.
``sh
cd codesanook-ef-note
``

- Launch Docker containers.
```sh
docker-compose down --volumes; docker-compose up --build
```

- Wait for a while until you see dotnet watch messages, e.g.
```sh
web_1  | watch : Process id 384 ran for 579ms
web_1  | watch : Watching 80 file(s) for changes
web_1  | watch : Watch command can be configured to use --no-restore.
web_1  | watch : No restore arguments: run --no-restore --urls http://*:80 --no-launch-profile
web_1  | watch : dotnet-watch is configured to launch a browser on ASP.NET Core application startup.
web_1  | watch : Refresh server running at ws://127.0.0.1:43557.
web_1  | watch : Started '/usr/share/dotnet/dotnet' 'run --urls http://*:80 --no-launch-profile' with process id 431
web_1  | watch : Running dotnet with the following arguments: run --urls http://*:80 --no-launch-profile
web_1  | watch : Started
```
- Open a browser and navigate to http://localhost:8000/
- You will find a simple note app that you can 
  - Add a new notebook which is a group/container of each note  
  - Add a new note.
  - Add a new tag.
  - Update/Delete notebook, note and tag.

## Hot reload
- Edit some C# source code in `app` folder. 
- Code will be compile automatically.
- Refresh a browser and see what you have changed.

## EF Note in a browser 
![ef-note-animated-screenshot.gif](ef-note-animated-screenshot.gif)

## Release compose for testing only
```sh
docker-compose down --volumes; docker-compose -f docker-compose.yml -f docker-compose.release.yml up --build
```

## Production release
- Create Azure App Service with a container mcr.microsoft.com/dotnet/samples:aspnetapp
- Create a public DockerHub repository
- Set up these secrets
  - AZURE_WEBAPP_CONTAINER_PUBLISH_PROFILE
  - AZURE_WEBAPP_NAME
  - DOCKERHUB_REPOSITORY
  - DOCKERHUB_TOKEN
  - DOCKERHUB_USERNAME
- Push the project to the main branch


## Debugging
- CD to `app` folder and launch run with debugging with VS Code `.NET Core launch (web)`
- Start only a database  container
```sh
docker-compose up db
```

## TODO
- [ ] Improve code quality
- [ ] Use async/await
