# Alternate-Life RageMP.NET

This is the documentation for the Alternate-Life RageMP server bridge to add proper .NET Core support.

## Getting started

To get started with AlternateLife.RageMP.Net, [look into our guide](~/documentation/installation.md) on how to create your first serverside resource.

## FAQ

- **Why should I prefer AlternateLife.RageMP.Net instead of the official RAGE Multiplayer C# bridge?**    
    - *This library represents the native JavaScript RAGE Multiplayer server API as close as possible.* 
    - *Furthermore, this library has improved error and exception handling, so exceptions thrown inside a resource should be caught and logged correctly to prevent crashes.*
    - *Thread-safety is handled by this library, so you do not have to worry about wrong thread calls or crashes due to race-conditions.*
    - *This libary is developed with the [task-based asynchronous pattern (TAP)](https://docs.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) in mind to achieve thread-safety.*
- **Is there a way to drop pure `.cs` files inside a resource folder and let the server compile it?**   
    - *No, you have to compile all projects into assemblies (`.dll`), other ways are not supported.*
- **Does this library offer a command handler to create simple commands?**
    - *Yes, but in a very basic way. There are two ways to create commands: First, with command-handlers and attributes which define commands and a very simple MP.Commands.Add() method that uses a lambda function as handler.*
- **I want to create multiple main-classes which are activated by the server, is that even possible?**   
    - *No, the server looks for the first type that implements the [IResource](api/AlternateLife.RageMP.Net.Scripting.IResource.yml) interface and activates it. You have to manage different types yourself.*


## MIT License

Copyright (c) 2018 Alternate-Life

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.