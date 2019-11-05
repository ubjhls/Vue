해당 작업을 하는 함수를 인자로 받아서

나중에 저 함수를 부르자(callback)



우선  Promise object를 리턴한다.

나중에(작업이끝나면) then/catch를 실행한다.

- Promise object 상태
  - pending ->작업 진행중
  - resolved -> resolve 함수 호출(작업 성공)
  - rejected -> reject함수 호출 (작업 실패)
- resolve -> then 에서 처리, reject -> catch에서 처리

```
1. posts/1 요청
2. json userID 값을 얻어서
3. users/${userId} 요청
4. json name 출력
```

