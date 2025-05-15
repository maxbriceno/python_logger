# python_logger

This file contains a custom logger service that is used to log levelling debug prints with python. 
It serves colored and idented logging levels usign colorama.

## Dependencies

```requirements.txtx
colorama
```

 ## 1 - Usage

1. Import init diretive from colorama lib:
```python
from colorama import init
```

2.  In your code import the custom logge class and the custom ColorEnum for styling textual logs:
```python
from my_logger import ColorEnum, MyLogger
```

3. Initialize colorama and istanciate a unique singleton logger to be used in your source code. You can pass a custom message with named parameter `message`,
a level (default level=0) and a Color (default color=ColorEnum.YELLOW):
```python
init(autoreset=True)
logger = MyLogger.get_instance()
logger.log(message="1/4 Initializing...", level=0)
```
