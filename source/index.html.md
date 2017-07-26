---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

search: true
---

# Introduction

<aside class="notice">
In order to have JavaScript commands you must talk to NovusTheory
</aside>

Welcome to the JavaScript API for Custom Commands in Modulo!

There is three key things you should know while you are programming custom commands for Modulo.

1. All scripts are reviewed before they are allowed to be in use.
2. All scripts must abide by a [strict format](#script-rules).

## FAQ

*Why are all scripts reviewed?*: **Although scripts are enabled by asking for it. All scripts must go under review to prevent malicious actions and follow a set of rules**

*Will reviewing ever be removed?*: **In the future reviewing of scripts might be removed when sandboxing and more restrictions have been put in place**

# Formatting

When programming custom commands, you must program to a specific format

```javascript
// You cannot have code above this line unless they are functions
discord.OnCommand = ...;
// You cannot have code below this line
```

The example code on the shown is how you should structure your code, otherwise it will be rejected for not following the formatting rules

# Discord

## Command Callback

```javascript
discord.OnCommand = function(Message message, Array arguments) {

};
```

You can connect to your command callback by assigning OnCommand to a function which will be called when your command is executed. A custom class [Message](#message) will be returned along with an array of arguments excluding the command itself will be passed.

## Bots

<aside class="warning">
If this option is enabled you must check for messages by bots in your command, otherwise your script will be rejected
</aside>

By default all commands are not allowed to be run by bots. However, you can allow your command to be used by bots when you are setting it up on the dashboard by checking **Allow Bots** to true!

## Interfacing with Modulo

<aside class="warning">
Interfacing with Modulo is a custom feature request and you will need to get in contact with NovusTheory for access to it from your JavaScript API
</aside>
<aside class="notice">
This part of the API has not been finished yet
</aside>

Modulo provides a set of methods that you can use to initiate functions on Modulo's behalf. These functions could include banning a user, muting a user, and etc.

# Message

A message is a class in JavaScript dealing with a commands message. Use this to get information about the message which intitiate your command, such as the [Author](#user).

## Author

```javascript
var author = message.Author;
```

This property returns a [User](#user) class.

## Channel

```javascript
var channel = message.Channel;
```

This property returns a [Channel](#channel-2) class.

## DeleteAsync

> This method can throw errors

```javascript
message.DeleteAsync();
```

Deletes the message

# User

A User is a class in JavaScript dealing with a user on Discord. This class will expose information about a user to you in your script.

## IsBot

```javascript
var bot = user.IsBot;
```

<aside class="notice">
This property will always be false unless bots are allowed to execute your command
</aside>

This property returns a boolean set to true if the user is a bot, likewise it will return false for the opposite.

## Id

```javascript
var id = user.Id;
```

This property returns a ulong value of the users id.

## Game

> This property can return null

```javascript
var game = user.Game;
```

This property returns a string of the users current game.

## Discriminator

```javascript
var discriminator = user.Discriminator;
```

This property returns a ushort value of the users discriminator.

## Username

```javascript
var username = user.Username;
```

This property returns a string value of the users username.

## AvatarId

```javascript
var avatarId = user.AvatarId;
```

This property returns a string of the users avatar id.

## RoleIds

> This property doesn't exist on users not pulled from a guild

```javascript
var roleIDs = user.RoleIds;
```

This property returns an array of ulong values of the users current roles.

It is most common to see this property on users when they derive from guild events. Such as the [Message](#message) class which can contain a user derived from a guild if the message was sent in one.

# Channel

## SendMessageAsync

```javascript
var message = channel.SendMessageAsync("Hello World!");
```

> An alternative to send an embed instead

```javascript
var embed = new Embed();
// Fill in embed
var message = channel.SendMessageAsync(embed)
```

This method has two overloads, one which can send an [Embed](#embed), and the other which is a string.

# Embed

## Title

```javascript
embed.Title = "Embed Title";
```

This property sets or gets the title of an embed.

## Description

```javascript
embed.Description = "Embed Description";
```

This property sets or gets the description of an embed.

## Color

```javascript
embed.Color = new Color(255, 0, 0);
```

This property sets or gets the color of an embed. This property is a [Color](#color-2) class and requires it to be set as one.

## AddField

```javascript
embed.AddField("Key", "Value");
```

This methods adds a field to an embed.

## AddInlineField

```javascript
embed.AddInlineField("Key", "Value");
```

This method adds an inline field to an embed.

# Color

## R

```javascript
var r = color.R;
```

This property returns the red value of a color;

## G

```javascript
var g = color.G;
```

This property returns the green value of a color;

## B

```javascript
var b = color.B;
```

This property returns the blue value of a color;
