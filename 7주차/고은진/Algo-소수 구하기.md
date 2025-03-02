# 소수 구하기

<br />

## 소수란?

**소수**는 1 또는 자기 자신만을 약수로 가지는 수를 의미한다.

<br />

## 소수를 구하는 가장 효율적인 방법

**가장 직관적인 방법**

2부터 (N - 1)까지 루프를 돌며 나눠보며 1 이외의 수로 나누어 떨어지지 않는지 확인한다.

```jsx
function isPrimeNumber(num) {
  for (let i = 2; i < num; i++) {
    if (num % i = 0) {
      return false;
    }
  }

  return true;
}
```

> 시간 복잡도 O(n) 소요

<br />

**효율성을 개선한 방법**

그 어떤 소수도 N의 제곱근보다 큰 수로 나눠지지 않는다는 점을 이용하는 방법

```jsx
function isPrimeNumber(num) {
  for (let i = 2; i * i <= num; i++) {
    if (num % i === 0) {
      return false;
    }
  }

  return true;
}
```

```jsx
function isPrime(num) {
  if (num === 1) return false;
  // Math.sqrt 함수를 사용하여 제곱근까지만 반복하도록 한다.
  for (let i = 2; i <= parseInt(Math.sqrt(num)); i++) {
    if (num % i === 0) return false;
  }
  return true;
}
```

- num의 약수는 짝으로 존재한다. 따라서 쌍을 이루는 약수 중 하나만 찾으면 나머지는 확인하지 않아도 된다.

> 시간 복잡도 O(sqrt(n))

<br />

**에라토스테네스의 체를 이용한 방법**

고대 그리스 수학자 에라토스테네스가 발견한 소수를 찾는 방법

- N이하의 소수인 수 구하기
  ```jsx
  function getPrimeNumbers(num) {
    const numbers = [false, false, ...Array(num - 1).fill(true)];
    const primeNumbers = [];

    for (let i = 2; i * i <= num; i++) {
      if (numbers[i]) {
        for (let j = i * 2; j <= num; j += i) {
          numbers[j] = false;
        }
      }
    }

    numbers.forEach((value, index) => value && primeNumbers.push(index));

    return primeNumbers;
  }
  ```

<br />

- N 이하의 소수 개수 구하기
    
    ```jsx
    function isPrime(num) {
    	let arr = Array(num + 1).fill(true);
        //index 0이 존재하므로 배열을 num + 1로 만든다.
    
        arr[0] = false;
        arr[1] = false;
        //배열의 index 0과 1은 소수가 아니므로 false로 만든다.
    
        for(let i = 2; i * i <= num; i++) { //제곱근까지만 반복
            if(arr[i]) {
                for(let j = i * i; j <= num; j += i) {
                    //반복을 i * i 부터 시작하는 것은 그 이전의 값은 j이전의 수에서 이미 확인했기 때문
                    arr[j] = false; //배수이므로 소수가 아닌것으로 만든다.
                }
            }
        }
        return arr.filter(el => el).length //filter로 arr중 값이 true인 것의 개수를 구한다.
    }
    ```


> 시간 복잡도 O(n log(log n))
