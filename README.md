# botbuilder-weatherbot
Echobot with custom WhatsApp and Webex adapter in Botframework Composer

## Features
- Compile and custom adapter installation
- nginx reverse proxy integration
- Linux service installation

## Compile on a Linux hosting with nginx

1. Compile and run on Linux/Windows host
```Shell
$ dotnet build weatherbot.csproj
$ dotnet run --project ./weatherbot.csproj 
```

2. Copy the custom adapter to the nuget folder, then install a custom adapter on the project
```Shell
$ nuget add ".\Bot.Builder.Community.Adapters.Whatsapp.1.0.0.nupkg" -Source "C:\devel\feed"
$ dotnet add weatherbot.csproj package "Bot.Builder.Community.Adapters.Whatsapp" --version="1.0.0" --source="C:\devel\feed"
```

3. Install the service on the Linux systemd
```Shell
$ dotnet publish --configuration Release
$ dotnet publish --configuration Release --project weatherbot.csproj 
$ sudo cp weatherbot.service /etc/systemd/system
$ cd /etc/systemd/system/
$ sudo systemctl enable weatherbot.service
$ sudo systemctl restart weatherbot.service 
$ sudo systemctl status weatherbot.service
```


