# 성능 테스트 기준 - T 계열 nano
<ul>
  <li>t2.nano</li>
  <li>t3.nano</li>
  <li>t3a.nano</li>
  <li>t4g.nano</li>
</ul>

# 테스트 코드
```python
import time
import multiprocessing

def cpu_bound_task():
    for _ in range(5000000):
        result = 2 * 2

if __name__ == "__main__":
    start_time = time.time()

    # CPU 코어의 수만큼 프로세스 생성
    num_processes = multiprocessing.cpu_count()
    processes = [multiprocessing.Process(target=cpu_bound_task) for _ in range(num_processes)]

    for process in processes:
        process.start()

    for process in processes:
        process.join()

    end_time = time.time()

    elapsed_time = end_time - start_time
    print(f"Elapsed Time: {elapsed_time} seconds")

```

# 테스트 결과
<ul>
  <li>t2.nano</li><img width="360" alt="t2 nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/f01f115b-b631-404c-ab82-bea496829929">
  <span>평균 시간 : 0.11초</span>
  <li>t3.nano</li><img width="366" alt="t3 nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/c008dc1d-944c-4274-bc62-8fe6ac96974f">
  <span>평균 시간 : 0.22초</span>
  <li>t3a.nano</li><img width="377" alt="t3a nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/6869c4e3-bee4-4144-9f5c-a2856a4d4cdf">
  <span>평균 시간 : 0.2초</span>
  <li>t4g.nano</li><img width="363" alt="t4g nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/3d87de21-120c-4608-bb5f-d14d414e7335">
  <span>평균 시간 : 0.15초</span>
</ul>
