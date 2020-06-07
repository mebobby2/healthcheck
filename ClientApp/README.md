# HealthCheck

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 6.0.0.

## Development
* Build: ```dotnet build```
* Run: ```dotnet run```
* visit: https://localhost:5001

## Tests
* from ClientApp folder
* ```npm run ng test```

## Run ng commands
```cd ClientApp```

If you have the ng tool installed globally, you can run any of its commands. For example, you can run ng lint, ng test, or any of the other Angular CLI commands. There's no need to run ng serve though, because your ASP.NET Core app deals with serving both server-side and client-side parts of your app. Internally, it uses ng serve in development.

If you don't have the ng tool installed, run npm run ng instead. For example, you can run npm run ng lint or npm run ng test.

## Run "ng serve" independently
The project is configured to start its own instance of the Angular CLI server in the background when the ASP.NET Core app starts in development mode. This is convenient because you don't have to run a separate server manually.

There's a drawback to this default setup. Each time you modify your C# code and your ASP.NET Core app needs to restart, the Angular CLI server restarts. Around 10 seconds is required to start back up. If you're making frequent C# code edits and don't want to wait for Angular CLI to restart, run the Angular CLI server externally, independently of the ASP.NET Core process. To do so:

1. In a command prompt, switch to the ClientApp subdirectory, and launch the Angular CLI development server:
```
cd ClientApp
npm start
```

2. Modify your ASP.NET Core app to use the external Angular CLI instance instead of launching one of its own. In your Startup class, replace the spa.UseAngularCliServer invocation with the following:
```
spa.UseProxyToSpaDevelopmentServer("http://localhost:4200");
```

When you start your ASP.NET Core app, it won't launch an Angular CLI server. The instance you started manually is used instead. This enables it to start and restart faster. It's no longer waiting for Angular CLI to rebuild your client app each time.

# Upto

Page 94

tsconfig.json
