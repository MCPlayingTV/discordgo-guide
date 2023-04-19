# Configuration

You can put variables that will be changed frequently in a config file (`config.yml)`

Variables include stuff like:

* Bot Token.
* Database Connection.
* URLs.
* API Tokens.
* anything really.

To use config files, create a file called `config.yml`

```yaml
BotToken: "..."
Database: "localhost:..."
Invite: "https://discord.gg/..."
#...
```

To load your files, you can use the `gookit/config` package!

```bash
go get github.com/gookit/config/v2
```

Then load the config variables!

```go
package main

import (
    "github.com/gookit/config/v2"
    "github.com/gookit/config/v2/yaml"
)

func main() {
	config.AddDriver(yaml.Driver)
	err := config.LoadFiles("config.yml")
	if err != nil {
		panic(err)
	}
	BotToken := config.String("BotToken")
	//...
	dg, err := discordgo.New("Bot " + BotToken)
	//...
}
```
