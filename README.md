## Golang Pretty Logger

![Usage](assets/screencast.gif)

### Install
```bash
go get github.com/happierall/l
```

### Usage
```go
import "github.com/happierall/l"

func main() {
   l.Log(10 + 5)
   l.Print("Without datetime and code line")
   
   people := &People{"Name"}
   l.Debug(people)

   l.Warn("Function is depreceted")
   l.Error("User is not defined")
   l.Logf("%d ms", 10)
   l.Printf("Request %s ms", l.Colorize("53", l.Green))
}

type People struct {
    Name string
}
```

Terminal output:
![Output struct and int](assets/output.png)

### Custom logger
```go
var log = l.New()
log.Prefix = log.Colorize("[APP] ", l.Blue)
log.Level = l.LevelDebug // default
log.DisabledInfo = true  // without date and code line

log.Debug("Message without date and line with prefix")
```

### Production mode
(without colors)
```go
l.Default.Production = true
```

### Subscribe on logs
```go
l.Default.Subscribe(func(text string, lvl l.Level) {
	fmt.Println("New log", text, lvl.String())
})
```
