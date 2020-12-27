## Setting up the Project

### 1. Setup a Python Virtual Environment
> A virtual environment is a tool that helps to keep dependencies required by different projects separate by creating isolated python virtual environments for them.

- Create a Project Folder.


- Run following command to create a new virtual environment inside your project folder:
```
python -m venv myvenv
```

    After running above command, a folder named `myvenv` will get created in your project folder.


- Activate the virtual environment by running following command:
    - For ubuntu and mac users:
        ```
        source myvenv/bin/activate
        ```
    - For windows users:
        ```
        myvenv\Scripts\activate
        ```
---------

### 2. Install required Python Packages:
- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)
    ```
    pip install python-telegram-bot
    ```

--------------

## Polling Program

## Echo Bot

### 1. Enable Logging

```python
import logging

logging.basicConfig(format='%(asctime)s - %(name)s - %(levelname)s - %(message)s', 
                    level=logging.INFO)
logger = logging.getLogger(__name__)
```


### 2. Create Updater

```python
updater = Updater(TOKEN)
```

### 3. Create Dispatcher

```python
dp = updater.dispatcher
```

### 4. Add handlers

```python
dp.add_handler(CommandHandler("start", start))
dp.add_handler(CommandHandler("help", _help))
dp.add_handler(MessageHandler(Filters.text, echo_text))
dp.add_handler(MessageHandler(Filters.sticker, echo_sticker))
dp.add_error_handler(error)
```

### 5. Start Polling and wait for any signal to end the program

```python
updater.start_polling()
updater.idle()
```
