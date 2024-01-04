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
# 테스트 코드 설명
<p>
  t 시리즈에서 t2, t3, t4g의 차이를 명확하게 보여주는 코드는 일반적으로 성능 테스트를 통해 비교되는데 CPU 성능 테스트를 수행하는 Python 코드를 통해 차이를 확인할 수 있습니다.
이 코드는 CPU 바운드 작업을 수행하고 걸리는 시간을 측정하는 테스트입니다.
</p>


# 테스트 결과
<ul>
  <li><h3>t2.nano</h3></li><img width="360" alt="t2 nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/f01f115b-b631-404c-ab82-bea496829929">
  <h3>평균 시간 : 0.11초</h3>
  <li><h3>t3.nano</h3></li><img width="366" alt="t3 nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/c008dc1d-944c-4274-bc62-8fe6ac96974f">
  <h3>평균 시간 : 0.22초</h3>
  <li><h3>t3a.nano</h3></li><img width="377" alt="t3a nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/6869c4e3-bee4-4144-9f5c-a2856a4d4cdf">
  <h3>평균 시간 : 0.2초</h3>
  <li><h3>t4g.nano</h3></li><img width="363" alt="t4g nano" src="https://github.com/chanjin1998/chanjin1998/assets/70675133/3d87de21-120c-4608-bb5f-d14d414e7335">
  <h3>평균 시간 : 0.15초</h3>
</ul>

# 결과 분석
**초기 예상 : 숫자가 높은 순서대로 성능이 좋을 것으로 예측**

+ t2.nano는 가장 빠른 처리 시간을 기록하여, 작고 비용 효율적인 작업에 적합(Linux 기준 시간당 0.0072 USD)
+ t3.nano와 t3a.nano는 중간 범위의 성능을 제공하며, 일반적인 용도에 적합(Linux 기준 시간당 0.0065 USD, Linux 기준 시간당 0.0059 USD)
+ t4g.nano는 ARM 기반의 최신 프로세서를 사용하여 좋은 성능을 제공하는 것으로 확인(Linux 기준 시간당 0.0052 USD)
+ t4g.nano는 비용 대비 효율적인 선택으로 나타남

