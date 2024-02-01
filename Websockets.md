# Websocket
### defines a full-duplex single socket connection over which messages can be sent between client and server” [websocket.org
- We will be using a c# library
- Client server relationship
## Websocket "Echo" Example

```
class Program	{
		static void	Main(string[]	args)	{
				//	Start	a	websocket	server	at	port	8001
				var	wss	=	new WebSocketServer(8001);	
				//	Add	the	Echo	websocket	service
				wss.AddWebSocketService<Echo>("/echo");	
				//	Start	the	server
				wss.Start();	
				Console.WriteLine("Press	Enter	to	exit.");	
				Console.ReadLine();	
				//	Stop	the	server
				wss.Stop();	
		}
```
```
class Echo	:	WebSocketBehavior	{
		protected override
					void	OnMessage(MessageEventArgs	e)	{
				//	Retrieve	message	from	client
				string	msg	=	e.Data;	
													
				//	Send	the	message	back
				Send("Echo:	"	+	msg);	
		}	
}	
```
# Websocket Client Echo
```
class Program	{
		static void	Main(string[]	args)	{	
				//	Create	a	websocket	connection	to	the	websocket	service	in	
				//	the	local	machine	(127.0.0.1)	at	port	8001	
				using	(var	ws	=	new WebSocket("ws://127.0.0.1:8001/echo"))	{
						
						//	Set	the	client	to	print	messages	from	the	server
						ws.OnMessage	+=	(sender,	e)	=>	Console.WriteLine(e.Data);	
						//	Connect	to	the	server
						ws.Connect();	
						Console.Write("Enter	a	message:	");	
						string	line	=	Console.ReadLine();	
						//	Send	message	to	the	server
						ws.Send(line);	
						Console.ReadLine();	
				}	
		}	
}
```
