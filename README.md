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
a level (default level=0) and a Color (default color=ColorEnum.YELLOW) -  respectively with `level` and `color` parameters:
```python
init(autoreset=True)
logger = MyLogger.get_instance()
logger.log(message="1/4 Initializing...", level=0)
```

## 2 - Suggestions

1. For improve the debugging across your code, Split up your code in function calls or code blocks wrapped with `try` `except` blocks.

2. Use a global high level `try` `except` block to exit the whole root process . Example:
```python
...

try:
    cwd = str(os.getcwd())
    build_folder_path = os.path.join(cwd, "my_path", "target")
    logger.log(message="✅ Setting paths complete!", level=0, color=ColorEnum.GREEN)
    
    ...

except Exception as e:
    logger.log(message=f"❌ Error Setting paths: {e}", level=0, color=ColorEnum.RED)
    exit(1)
```

3. Use inside single subprocesses or function calls (or code blocks if preferred) to raise Exceltions. Example:

```python
...
    try:
        subprocess.run(...)
        logger.log(message="✅ Subprocess complete!", level=0, color=ColorEnum.GREEN)
    except Exception as e:
        logger.log(message=f"❌ Error in subprocess: {e}", level=0, color=ColorEnum.RED)
        raise e
...
```
 