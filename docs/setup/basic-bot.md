# Basic bot

Create a `main.go` file and import the package:

```go
package main

import "github.com/bwmarrin/discordgo"

func main() {
	dg, err := discordgo.New("Bot <your-discord-bot-token>")
	if err != nil {
		fmt.Println("error creating Discord session,", err)
		return
	}

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

To run your bot, run the run command in your terminal:

```bash
> go run main.go
Bot is now running.  Press CTRL-C to exit.
```

You should now see the bot going online in discord!
