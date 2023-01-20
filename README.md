# cShare

![Cshare Logo](./cshare.png?raw=true)

A commd-line tool to share sensitive text data across devices owned by you.

## 💡 Inspiration

With my old potato PC, I was converting it into my home server for streaming, remote development, and experimenting with random stuff. For this installation, I decided to go with [Manjaro](https://manjaro.org/) my base OS.

>Manjaro is a free and open-source operating system based on Arch Linux. It uses the same package manager (Pacman) and build system (AUR) as Arch. It is considered a secure operating system as it uses the Linux kernel and a variety of security-focused software and practices. Manjaro also follows the Arch Linux security policy and actively monitors it; overall, it's very secure.

I wasn't able to SSH to my home server because of Manjaro's security. I needed to share some security keys from my Mac with the server. I tried everything I could to copy my key but couldn't.

I needed a simple tool that I could instal just like curl (`pacman -S curl`). I didn't even know about `scp` or maybe I needed to tweak some firewall settings. Ultimately, I decided to build cShare. This is how I was inspired to make this app.

## ⚙ Working

- Like any other CLI app, it can be installed using a single command `go install github.com/JammUtkarsh/cshare`. Behind the scenes, it fetches the source code from the repo temporaryly. Builds and stores it in `$GOROOT/bin`. If this path is added to your shell, then you can access it like any command.
- The data is centerally stored on the [server](https://github.com/JammUtkarsh/cshare-server). cShare makes HTTP requests on the database.
- in `$HOME/.cshare/config.json` stores the JWT token which is required for every subsequent request.

## 🔧 How we built it

- [Cobra](https://github.com/spf13/cobra) is used to create the basic structre app and it's sub commands.
- [Viper](https://github.com/spf13/viper) is the config manager. It performs all the data storage mechanism.
- For other operations like http request and displaying the test, standard library is being used.
