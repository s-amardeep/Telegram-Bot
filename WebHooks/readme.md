## Polling vs Webhook

![](images/webhook.png)

### Ports currently supported for Webhooks: 443, 80, 88, 8443.

## Setting up a server

### 1. Install Flask

```
pip install flask
```

### 2. Setup Webhook

```python
# create telegram bot object
bot = Bot(TOKEN)
# set webhook for telegram bot
bot.set_webhook("https://example.com/" + TOKEN)
```

### 2. Create view to handle webhooks

```python
@app.route(f'/{TOKEN}', methods=['GET', 'POST'])
def webhook():
    """webhook view which receives updates from telegram"""
    # create update object from json-format request data
    update = Update.de_json(request.get_json(), bot)
    # process update
    dispatcher.process_update(update)
    return "ok"
```

### 3. Generate Public URL for Webhook using ngrok.io

![](images/ngrok1.png)

> *ngrok is a free tool that allows us to tunnel from a public URL to our application running locally.*

- Download ngrok.
- Unzip it.
- Run ngrok from command line (from the location where executable is stored)
```
  ./ngrok http 8443
```
- Copy the HTTPS Forwarding URL

![](images/ngrok2.png)
