---
layout: post
title: App.config in MSTest on .NET Core
summary:
published: true
tags: net .net core mstest appconfig
categories: posts
---

### Hi!

Currently, at work, I'm porting the NET472 app into .Net Core 3.1. As it's a kind of enterprise application, there are a lot of NuGet packages (younger and older one) that has some (younger and older) dependencies. One of them is ConfigurationManager...
<br>
<!--more-->
<br>
... which means that I have to provide proper configuration in
<br>

`IConfiguration`
<br>
interface for .Net core things and
<br>

`ConfigurationManager`
<br>
for legacy nuget packages.
<br><br>
Fortunaltey .Net core supports `System.Configuration` namespace, so `ConfigurationManager` is availabel out of the box.
<br>
<br>
Sound easy... keep `app.config` file with old configuration, put new one in `appsettings.json`.
<br>
Done.
<br>
<br>
*Not so easy....*
<br>
<br>
We have quite a lot of `MSTest` tests over here. I found out, that `ConfigurationManager` is not filled with configs from `app.config`.
<br>
<br>
After lots of googling, asking around etc the solution was found in [this Github issue](http://github.com/microsoft/testfx/issues/348)
<br>
<br>
To have it working, I had to add custom target do MSBuild

```xml
<Target Name="CopyAppConfig" AfterTargets="Build" DependsOnTargets="Build">
     <CreateItem Include="$(OutputPath)App.config">
        <Output TaskParameter="Include" ItemName="FilesToCopy"/>
    </CreateItem>
    <Copy SourceFiles="@(FilesToCopy)" DestinationFiles="$(OutputPath)testhost.dll.config" />
  </Target>
```
<br>
to copy "app.config" from my build directory into `testhost.dll.config` to let the `testhost.dll` read my whole configuration and fill `ConfigurationManager` with proper data.
<br>
k.