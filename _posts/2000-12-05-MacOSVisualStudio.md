---
layout: post
title: MacOS VisualStudio localhost certificate issue 
published: false
tags: macos blog visual studio certificate
---

## Can't create development certificate on macOS
Been a long time Visual Studio user for .NET Dev work on a Windows workstation. I have recently installed Microsoft Visual Studio on my MacOS. 
I kept getting following error and wasn't able to start the weather project in VS after the installation.

The error was 
_System.InvalidOperationException: "Unable to configure HTTPS endpoint. No server certificate was specified, and the default developer certificate could not be found or is out of date.\nTo generate a developer certificate run 'dotnet dev-certs https'. To trust the certificate (Windows and macOS only) run 'dotnet dev-certs https --trust'.\nFor more information on configuring HTTPS see https://go.microsoft.com/fwlink/?linkid=848054."_

After followed above instructions I still wasn't able to run demo solution with 'dev-certs https' command.
Later I figured out there were more than one localhost certificates in Keychains and the workaround as following:

* Clean up your certificates manually in Keychains.
* Run following commands (use sudo if need be)
 - dotnet dev-certs https --clean
 - dotnet dev-certs https
 - dotnet dev-certs https --trust
