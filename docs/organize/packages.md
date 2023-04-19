# Packages

To organize your code and make it readable, you can use go packages.

Depending on what you're using, you can create packages for each:

* Slash Commands.
* Events.
* Modals.
* Autocomplete.
* etc.

For example, to move slash commands to packages, create a `SlashCommands` directory and put `ping.go` in it:

<pre><code>DIR | SlashCommands
    File | ping.go
    
<strong>File | main.go
</strong></code></pre>

SlashCommands/ping.go

```go
package SlashCommands

import (
	"github.com/bwmarrin/discordgo"
)

func Ping(s *discordgo.Session, i *discordgo.InteractionCreate) {
	// send ping
}

```

main.go:

```go
package main

import "github.com/bwmarrin/discordgo"
import "MyBot/SlashCommands"

func main() {
	dg, err := discordgo.New("Bot <your-discord-bot-token>")
	if err != nil {
		fmt.Println("error creating Discord session,", err)
		return
	}
	
	// we add interaction create handler and use Ping function from ping.go
	s.AddHandler(func(s *discordgo.Session, i *discordgo.InteractionCreate) {
	SlashCommands.Ping(s,i);
	})	
	
	
	err = dg.Open()
	if err != nil {
		fmt.Println("error opening connection,", err)
		return
	}

	fmt.Println("Bot is now running.  Press CTRL-C to exit.")
	stop := make(chan os.Signal, 1)
	signal.Notify(stop, syscall.SIGINT, syscall.SIGTERM, os.Interrupt)
	<-sc
}
```

The same procedure for all commands, modals, etc.
