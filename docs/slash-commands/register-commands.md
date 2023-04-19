# Register Commands

You can register slash commands so they're available to be ran in the discord client.

```go
// while bot is starting
//..
var Commands = []*discordgo.ApplicationCommand{
	{
		Name:        "ping",
		Description: "Pong!",
		Options: []*discordgo.ApplicationCommandOption{

			{
				Type:         discordgo.ApplicationCommandOptionString,
				Name:         "option",
				Description:  "Test Option!",
				Required:     true
			},
		},
	}
	
_, err := s.ApplicationCommandBulkOverwrite(s.State.User.ID, "", Commands)
	if err != nil {
		panic(err)
		return
	}
```

### Per Guild:

