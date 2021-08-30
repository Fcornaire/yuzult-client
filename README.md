# Yuzult client <a href="https://github.com/Fcornaire/yuzult-client/releases/latest"><img alt="GitHub release" src="https://img.shields.io/github/v/release/Fcornaire/yuzult-client"></a> <a href="https://github.com/Fcornaire/yuzult-client/releases"><img src="https://img.shields.io/github/downloads/Fcornaire/yuzult-client/total"></a> <a href="https://twitter.com/DShad66"><img alt="Twitter Follow" src="https://img.shields.io/twitter/follow/DShad66?style=social"></a>

Desktop App making yuzu + parsec Smash Ultimate users to link themselves easier

Yuzult is a service which let you match with people for Smash Ultimate game via Parsec throught a server as a system of lobbies

the name come with the pun Yuzu / ultimate <-> Yuzultimate <-> Yuzult

It composed of 3 main apps :

- [Yuzult](https://github.com/Fcornaire/yuzu) : the yuzu version managing communication with Parsec
- Yuzult-matchmaking : the backend server
- Yuzult-client: the desktop app that use the 2 above for the whole system working

It uses the Parsec capabilities throught the [sdk](https://github.com/parsec-cloud/parsec-sdk) to enable low latency yuzu session ( As a reminder, it's Parsec, not a rollback netcode implementation of Smash Ultimate in yuzu)

[**Read this guide to host / join as client**](./GUIDE.md)

[**Also read this if you have some problems**](./TROUBLESHOOT.md)

# Features
## Present
- Host Smash Ultimate parsec games
- Joining any Smash Ultimate games displayed (You don't need to have yuzu for joining)
- Enjoy less lag overall thanks to Parsec
- Auto update when new version is released

## Planned Features
This feature are planned depending of how people love / use the project. I'm also gonna focus more on bug fix / improve user experience first before moving into the next:
- Private lobby
- Url link for inviting someone to the lobby
- Up to 3 client in the lobby
- Spectate spots
- Some lobbies filter (Country ? Continent ? ping limit ?)
## Known bugs

### Yuzu randomly crash at some points

Not really random since it apparently has to deal with something happening in the memory since the 10.1 version of Smash Ultimate, see this [issue](https://github.com/yuzu-emu/yuzu/issues/5822)

### Yuzu show a black screen while audio and control still working

Not really sure for now if it's related to the bug above or if it's something that need to be fixed in yuzult...

# Quickstart

1. [Download the exe](https://github.com/Fcornaire/yuzult-client/releases/latest)
2. Run the exe `Yuzult-client-Setup-{version}.exe`
3. Enjoy!

# Why ?

People still try to play Smash Ultimate online throught the game. While some people don't have a problem with that, it still really hard to actually enjoy/learn the game properly especially for the competitive player when you have like 5 minimum frames of input delay (Smash Ultimate use delay based netcode, and probably one of the worst one...).

[Yuzu](https://github.com/yuzu-emu/yuzu) is a switch emulator still in developement that run Smash Ultimate good enough. When you combine it throught [Parsec](https://parsec.app/features) (low latency game streaming service), you meet an almost offline environment of play.

Some discord server exist to let yuzu users to connect between themselves to host/join session with parsec and play. It works, but you loose the quick play feel from the game...

The main idea of Yuzult is to let people connect more easily and also to attract more people to it since there is a lot of people that still didn't tried yuzu or at lease joining a parsec session throught parsec.

# How ?

[Yuzult](https://github.com/Fcornaire/yuzu) is a forked version of yuzu that implement the [Parsec SDK](https://github.com/parsec-cloud/parsec-sdk) (check the repo for more details)

Yuzult-matchmaking is an api server that manage all the lobbies and communication between Yuzult and the client (the backend is not destinated to the public ). Communication happen with WebSocket ([SocketIO](https://github.com/socketio/socket.io)) instead of regular Rest Api to take advantage of realtime communication.

The client make everything work together by setting up / send the right data to make all the yuzu + parsec session work. It also responsible for launching the enhanced yuzu, so you don't have to download it
