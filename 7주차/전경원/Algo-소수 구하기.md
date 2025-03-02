  # 소수 구하기
  ### 소수
  1 또는 자기 자신만을 약수로 가지는 수를 의미한다.
  # 소수를 구하는 방법
  ### 직관적인 방법
  2부터 (N - 1)까지 루프를 돌며 나눠보기
  ```python
  def is_prime_num(n):
      for i in range(2, n):
          if n % i == 0:
              return False # i로 나누어 떨어지면 소수가 아니므로 False 리턴

      return True # False가 리턴되지 않고 for문을 빠져나왔다면 소수이므로 True 리턴
  ```
  > 시간 복잡도 O(n) 소요
  ### 효율성을 개선한 방법
  그 어떤 소수도 N의 제곱근보다 큰 수로 나눠지지 않는 다는 점을 이용하는 방법
  ```python
  # 제곱근을 구하기 위해 math 라이브러리 임포트
  import math

  def is_prime_num(n):
      for i in range(2, int(math.sqrt(n))+1): # n의 제곱근을 정수화 시켜준 후 + 1
          if n % i == 0:
              return False

      return True
  ```
  > 시간 복잡도 O(sqrt(n))
  ### 에라토스테네스의 체를 이용한 방법
  - N 이하의 소수인 수 구하기
  ```python
  def is_prime_num(n):
      arr = [True] * (n + 1) # 특정 수가 지워졌는지 아닌지 확인하기 위한 배열
      arr[0] = False
      arr[1] = False

      for i in range(2, n + 1):
          if arr[i] == True: # 특정 수가 지워지지 않았다면 (소수여서)
              j = 2

              while (i * j) <= n:
                  arr[i*j] = False # i의 배수의 값을 False로 지워준다.
                  j += 1

      return arr

  arr = is_prime_num(50) # 0 ~ 50중 소수를 구하기 위한 함수

  for i in range(len(arr)):
      if arr[i] == True:
          print(i, end=' ')
  ```
  > 시간 복잡도 O(n log log n)
