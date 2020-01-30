## Future 동시성

-   비동기 작업 실행
-   지연시간 (Block) CPU 및 리소스 낭비 방지
-   File, Network I/O 관련 작업 동시성 활용 권장
-   적합한 작업 : 순차 실행보다 효과적
-   부적합 작업 : 순차 실행보다 느려질 수 있음

### 예제 1

```python
# File I/O
from concurrent import futures
import csv
import os
import time

# 파일 읽기
def read_file(name):
    return_list = list()

    with open('{file_path}/{file_name}') as fr:
        reader = csv.DictReader(fr)
        for r in reader:
            if r == name:
                return_list.append(r)
    return return_list



def main():
    # name_list
    name_list = ['Alice', 'Bob']

    # setting worker count
    worker = 5
    # setting start time
    start_time = time.time()

    # use ProcessPoolExecutor : GIL 우회, 변경 후 os.cpu_count()
    with futures.ProcessPoolExecutor() as executor:
        # map > 바로 시작 / 작업 순서 유지
        # result = executor.map(func=read_file, iterables=name_list)
        result = executor.map(read_file, name_list)

    # use TreadPoolExecutor: GIL 종속
    with futures.ThreadPoolExecutor(max_workers=worker) as executor:
        result = executor.map(func=read_file, iterables=name_list)
    # setting end time
    end_time = time.time() - start_time


```
