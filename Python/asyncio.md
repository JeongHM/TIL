## Asyncio
### Generator -> 반복적인 객체 Return (yield)
-  즉 실행, 멈추고, 다른작엄으로 위임 -> 멈춤  재실행 원리


### Block I/O
- 순차실행

```python
import timeit
from urllib.request import urlopen

urls = ['http://daum.net', 'https://google.com', 'https://apple.com', 'https://tistory.com',
        'https://github.com', 'https://gmarket.co.kr']

start = timeit.default_timer()

# 순차 실행
for url in urls:
    print('Start', url)
    urlopen(url=url)
    print('Done', url)

duration = timeit.default_timer() - start
print('total time : ', duration)
```
### Thread
- 쓰레드 개수 및 GIL 문제 염두, 공유 메모리 문제 해결

```python
import timeit
from urllib.request import urlopen
from concurrent.futures import ThreadPoolExecutor
import threading

urls = ['http://daum.net', 'https://google.com', 'https://apple.com', 'https://tistory.com',
        'https://github.com', 'https://gmarket.co.kr']

start = timeit.default_timer()


def fetch(url):
    print('ThreadName: ', threading.current_thread().getName(), 'start', url)
    urlopen(url=url)
    print('ThreadName: ', threading.current_thread().getName(), 'end', url)


def main():
    with ThreadPoolExecutor(max_workers=10) as executer:
        for url in urls:
            executer.submit(fetch, url)


if __name__ == '__main__':
    main()
    duration = timeit.default_timer() - start
    print('total time : ', duration)
```
