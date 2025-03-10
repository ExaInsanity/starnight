# Starnight Project Styleguide

This document aims to clarify the parts of Starnight's code style rules that are not already enforced in the
[editorconfig](https://github.com/InsanityBot/starnight/blob/main/.editorconfig) file.

## Introduction

Starnight is a modern, up-to-date, lightweight and fast Discord API wrapper, at this time developed against .NET 6 and Discord API v9. To both allow
fast updating and proper maintenance, Starnight employs very rigorous code style outlined below and enforced in the editorconfig file.

If you plan to contribute to Starnight, make sure to rigorously and unconditionally follow these rules. If you feel like you absolutely have to,
you can ignore some rules. If you decide to do so, make sure to discuss the breach before creating your pull request.

## Code Style

#### Solutions and Projects ####

Starnight does not make extensive use of the dotnet project system. Starnight itself is intended as a lightweight wrapper around Discord API v9,
not an extensive bot framework - extensions can do this job. All extensions developed by the InsanityBot/Starnight team follow
this styleguide too, third party extensions might ignore some or all rules we set forth.

Because of Starnights nature as a direct wrapper, Starnight will rarely need additional Projects as defined by the .NET Project
system. In some cases, it can nonetheless be justified to create a new project: `Starnight.Logging` would be a valid new project,
whereas `Starnight.Commands` would not. Please keep this in mind when thinking about creating new projects.

Additionally, keep in mind Starnight is exclusively a library: the startup code has to be done by the consumer. Console projects
have no reason to exist here.

#### Naming ####

The editorconfig file already handles a great deal of Starlight naming conventions. It leaves the most important part untouched, though,
due to the lack of power of automated tools:

Discord data structures and their direct associates are to be prefixed with `Discord`. For instance, `ApiClient` turns into
`DiscordApiClient` and `EmbedBuilder`, even though not technically required to interact with the Discord API, becomes
`DiscordEmbedBuilder`. This principle is not applied to anything save types.

In general, longer and more descriptive names are preferable to short and thus less descriptive names. There are exceptions,
but - see the Architecture section - those do not really apply to Starnight. As a baseline, 48 characters is a limit that should
not be exceeded.

#### Architecture ####

Starnight mostly wraps Discord API v9 into C#, without much work around that. Starnight does not have any need for factories, builders and the likes.
Please refrain from using any kind of design pattern; a bare API is enough.

#### File Structure ####

Use namespaces where deemed appropriate. Creating a namespace just for two classes is probably not worth it. Put only one type into each file.
Also avoid nested types - where they make sense, split the containing type up into a partial class and use a separate file for the nested type.

Avoid overly long lines. Newlines are easy to use in this language, let's take advantage of that!
