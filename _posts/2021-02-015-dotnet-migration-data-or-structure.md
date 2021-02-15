---
layout: post
title: dotnet ef migrations - migrate data, structure or both?
summary:
published: true
tags: net .net core ef ef-core migration db database
categories: posts
---

### Hi!

Dotnet ef is a very powerfull tool, that helps a lot whle you are working with DB in your project. I have seen projects that had only ADO.NET, only EF or only Dapper, but very often you merge at least two of this tech. Something wiht EF just to have a way to generate and apply migrations with ease. You may like Dapper for it fastnes, or ADO.NET for it... rawness (rly, someone?) but EF migrations are huge time-saver. But there is also not-so-bright side there.
<br>

<!--more-->
<br>
I usualy use migrations to migrate database structure. You just type
<br>

`dotnet ef migrations add [MigrationName]`
<br>
and done. Dotnet-ef builds your app and generate migrations based on DbContext configuration.
<br>
To apply it just type
<br>
`dotnet ef database update`
<br>
and you are done. Db migrated.
<br>
<br>
But from time to time where is a case that is not so straight forward and easy. You have to write migrations on your own.
<br>
Examples?? Views. Dotnet-ef cannot generate views. Another? **Data migrations**. It sounds as easy as
<br>`generate new migration`
<br>`wirite your own scritp`
<br>and you can be sure that it's so easy, but some things have to be taken into consideration.
<br>
<br>
In my current project I had a situation that I had an enum in my entity model. Just three values and default `enum to db` converter so EF core store it as int in my db. Just 1, 2 and 3. Cool. Works. But later on the requirements changed (as they always do :blink:). From now on we can mix this enum values as it if's a flag. Easy. Add `[Flag]` attribute, rewirte values to 1,2 and 4 and... Oh wait. What about the current data in my db. Now `4 is the new 3`... Ok. Add migration, `update where...` and done. Phew, wasnt so hard :blink:
<br>
<br>
Some time passes and requirements changed again. We do not need this flag any more. Ok. New migration, drop column, done.
<br>
First release passed. And here comes the trobule.
<br>
<br>
While I wrote that migrations that migrate data from enum to flag (change 3 to 4) I had to specify which column should be updated. And now on this column is gone. Each release failed, because my DB validate each script that shoudld be executed. What that means to me? I had a script inside an `IF migration does not exist` that was invalid, as it refers to the column that no longer exists in db and it failed all my release with migrations.
<br>
<br>
To fix that I had to remove that part of script from migration that manipulates the data in the column that was removed. Maybe there is a better solution for that? If you know, give me a tip in comments.
