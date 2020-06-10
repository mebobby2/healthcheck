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

## C# Notes
### default literal
You can use the default literal to produce the default value of a type when the compiler can infer the expression type.
```
T[] InitializeArray<T>(int length, T initialValue = default)
{
    if (length < 0)
    {
        return default;
    }

    var array = new T[length];
    for (var i = 0; i < length; i++)
    {
        array[i] = initialValue;
    }
    return array;
}
```

### using statement
Provides a convenient syntax that ensures the correct use of IDisposable objects. Beginning in C# 8.0, the using statement ensures the correct use of IAsyncDisposable objects.
```
string manyLines=@"This is line one
This is line two
Here is line three
The penultimate line is line four
This is the final, fifth line.";

using (var reader = new StringReader(manyLines))
{
    string? item;
    do {
        item = reader.ReadLine();
        Console.WriteLine(item);
    } while(item != null);
}
```

## General Notes
### Internet Control Message Protocol (ICMP)
Is a networking protocol.  It is used to send error messages or to send query messages. You must have heard about "Ping". Ping uses ICMP to send echo request to the target host and get echo reply.

Ping works in the following way: the machine that performs the PING sends one or more ICMP echo request packets to the target host and waits for a reply; if it receives it, it reports the round-trip time of the whole task; otherwise, it time outs and reports a ```host not reachable``` error.

The host not reachable error can be due to a number of possible scenarios, as listed here:
* The target host is not available.
* The target host is available, but actively refuses TCP/IP connections of
any kind.
* The target host is available and accepts TCP/IP incoming connections, but it has been configured to explicitly refuse ICMP requests and/or not send ICMP echo replies back.
* The target host is available and properly configured to accept ICMP requests and send echo replies back, but the connection is very slow or hindered by unknown reasons (performance, heavy load, and so on), so the round-trip time takes too long—or even times out.


### WAN
If an enterprise has an office a building in Barcelona, then that is likely a Local Area Network or LAN, as all of the traffic is local and it could be on copper (slow) or fiber (fast).  That same company might have an office in a building in Geneva, and that Geneva traffic would also probably be a LAN, a different LAN than the one in Barcelona.

To go one further, the office in Geneva might be a campus of buildings, and with fiber (fast) as the interconnects, that would, for most people, still be considered a LAN.  Because of the latency and because of the simple routing used.

So LANs tend to be simple,  fairly reliable, and with low latency.  Most applications and users like traffic that is local, because the network component for delay (latency) is low.

Now, if the enterprise wants to link the two offices together in some way, that's where a WAN comes into play.  Because of the distance, WANs
tend to have higher latency, higher delay, and gosh, they get a bit less reliable.  Most users deal with that OK, but some applications do not.

Beacuse you'll be dealing with 3rd parties, you'll have to introduce one or more routing protocol.  Lots of LAN traffic might not route at all.  A company might use various interior routing protocols (static, RIP, OSPF, EIGRP, ISIS, etc) internally, but in order to talk on a WAN, you'll have to use an exterior routing protocol, and that typically means BGP.


# Upto

Page 157

Chapter 4
