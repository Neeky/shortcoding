## shortcoding
   **简化 python 代码是 shortcoding 是唯一目的，shotcoding: 没有什么是一个 import 解决不了的.** 

   ---


## 让程序以守护进程方式运行
   **start_daemon 让程序以守护进程方式运行**
   ```python
#!/usr/bin/env python3
import time
import argparse
from shortcoding.daemon import start_daemon,stop_daemon


def main():
    """业务逻辑代码
    """
    while True:
        # 假设这是一套非常赚钱的业务
        time.sleep(1)

if __name__ == "__main__":
    parser = argparse.ArgumentParser("daemon")
    parser.add_argument('action',choices=('stop','start'),help="start or stop daemon")
    parser.add_argument('--pid-file',default='/tmp/shortcoding.pid',help='pid file')
    args = parser.parse_args()
    if args.action == 'start':
        start_daemon(args.pid_file) # 一行代码程序就可以以守护进程的方式运行了
        main()
    else:
        stop_daemon(args.pid_file)
            
   ```
